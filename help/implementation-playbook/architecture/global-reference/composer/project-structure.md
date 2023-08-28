---
title: Estrutura de projeto do compositor
description: Saiba como configurar e manter a opção de pacotes separados descrita nos exemplos de arquitetura de referência global.
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Estrutura de projeto do compositor

Este guia descreve como configurar e manter o [opção separar pacotes](../examples.md#option-1-separate-packages) descritos nos exemplos de arquitetura de referência global (GRA).

## Pré-requisitos

Antes de começar, verifique o seguinte:

- Você tem um repositório Git
- Você tem um repositório do Composer (este tópico destaca a Lista de pacotes privados)
- Você configurou o repositório do Composer para espelhar o `repo.magento.com` e `packagist.org` repositórios

## Repositório de projeto Git principal

O repositório principal do projeto Git deve conter apenas um projeto do Composer. Você pode gerenciar tudo mais com os pacotes do Composer. O projeto principal nunca deve conter nada além da seguinte estrutura de arquivo, pois o Composer instala todos os outros pacotes por meio de dependências:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Adicione o seguinte conteúdo à `.gitignore` arquivo:

```tree
/*
!/composer.json
!/composer.lock
```

## Inicializar o projeto principal

1. Crie um repositório Git chamado `project-<region/country/brand>`.

1. Criar `composer.json` e `composer.lock` arquivos:

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## Salvar arquivos que não são do módulo

1. Adicione o `app/etc/config.xml` para o repositório Git.

   Você pode usar o módulo que vai criar para instalar outros arquivos de região ou específicos da marca, como `.htaccess`, arquivos de texto de autenticação do Google ou Bing, executáveis ou outros arquivos estáticos que não são gerenciados por módulos do Adobe Commerce.

   Uso `magento2-component` Digite pacotes para criar um mapeamento de arquivo e copiar arquivos para o repositório Git principal durante `composer install` e `composer update` operações.

1. Crie um repositório Git que siga a convenção de nomenclatura `component-environment-<region/country/brand>`:

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. Adicione o `app/etc/config.php` arquivo como um mapeamento na variável `extra.map` atributo do seu `composer.json` arquivo:

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. Valide seu `composer.json` e confirme-o no repositório Git:

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## Configurar metapackages

1. Crie os seguintes repositórios Git:

   - `meta-gra`
   - `meta-<region/country/brand>`

1. Configure a seguinte árvore de dependência:

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. Crie o metapacote GRA:

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Crie o metapackage da marca:

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Exigir a coleção por meio do gerenciamento de dependências no projeto principal:

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Verifique se o Composer copiou o `app/etc/config.php` arquivo de `<client>/component-environment-<region/country/brand>`.

## Implantar código

No servidor Web, é possível implantar o código usando o Composer, mas não é possível atualizar o projeto principal. Reinstale o projeto usando o Composer com cada nova implantação, o que elimina o requisito para que os servidores de produção e teste tenham acesso ao Git.

## Adicionar outras instâncias e pacotes

Cada instância (região, marca ou instalação exclusiva do Adobe Commerce) deve obter sua própria **projeto principal** instância, **metapackage específico**, e **pacote de componente do ambiente**. A variável **Metapackage de GRA** deve ser **compartilhado** em todas as instâncias.

Pacotes funcionais (como módulos do Adobe Commerce, temas, pacotes de idiomas e bibliotecas) e pacotes de terceiros devem ser exigidos pelo:

- **Metapackage de GRA**—Para instalação em _all_ instâncias
- **metappackage específico da instância**—Para instalação em uma única marca ou região

>[!IMPORTANT]
>
>Não exigir pacotes no do projeto principal `composer.json` arquivo no `main` ou `release` filiais.

## Preparação para o desenvolvimento

Para desenvolvimento, instale `develop` de todos os módulos que você mantém.

Dependendo da sua estratégia de ramificação, você pode ter `develop`, `qa`, `uat`, e `main` filiais. Cada ramificação existe no Composer com um `dev-` prefixo. Assim, o `develop` A ramificação pode ser exigida por meio do Composer como versão `dev-develop`.

1. Criar `develop` ramificações em todos os módulos e repositórios do projeto.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   A etapa anterior gera as seguintes linhas no `composer.json` arquivo:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Não mesclar** estes `composer.json` alterações no arquivo da sua ramificação de produção. Instalar somente versões estáveis de pacotes no `release` e `main` filiais. É possível definir essas dependências para `qa` e outras sucursais não principais.
