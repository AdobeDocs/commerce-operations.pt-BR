---
title: Instale o [!DNL Upgrade Compatibility Tool]
description: Siga estas etapas para instalar o [!DNL Upgrade Compatibility Tool] para seu projeto do Adobe Commerce.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# Instale o [!DNL Upgrade Compatibility Tool]

O [!DNL Upgrade Compatibility Tool] é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos instalados nela. Retorna uma lista de erros e avisos que devem ser endereçados antes de atualizar para a versão mais recente do Adobe Commerce.

## Fluxo de trabalho

O diagrama a seguir mostra o fluxo de trabalho esperado ao executar o [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Quem é o [!DNL Upgrade Compatibility Tool] para?

O caso de uso a seguir descreve o processo típico de um parceiro da Adobe Commerce para atualizar a instância de um cliente:

1. Um engenheiro de software de um parceiro baixa o [!DNL Upgrade Compatibility Tool] do [Repositório Adobe Commerce](https://repo.magento.com/) O e o executa durante a fase beta da versão mais recente do Adobe Commerce. Consulte a [Baixe o [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) para obter mais informações.
1. O Engenheiro de Software gera uma instância baunilha para a versão específica do Adobe Commerce que está instalada no momento. Consulte a [Guia do colaborador](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obter mais informações sobre como usar o `instance` para gerar uma instalação baunilha.
1. O Engenheiro de Software vê que há várias áreas personalizadas quebradas nos módulos de inventário e catálogo e elas também obtêm uma pontuação de complexidade de X. Consulte o [Desenvolvedor](../upgrade-compatibility-tool/developer.md) para obter mais informações sobre o índice de complexidade.
1. Com essas informações, o engenheiro de software é capaz de entender a complexidade da atualização e pode retransmitir essas informações para o gerente de conta do parceiro.
1. O Gerente de conta cria uma linha do tempo e um custo para a atualização do Adobe Commerce, o que permite que o gerente obtenha a aprovação.
1. Com a aprovação do gerente, o engenheiro de software trabalha com as modificações de código necessárias para corrigir os módulos quebrados.
1. O Engenheiro de Software executa o [!DNL Upgrade Compatibility Tool] mais uma vez com um pré-lançamento do Adobe Commerce para garantir que não há novos problemas e que suas alterações de código corrigiram os problemas encontrados durante a fase beta.
1. Tudo é verificado e o engenheiro de software envia o código para um ambiente de preparo, onde os testes de regressão confirmam que todos os testes são verdes, o que permite que ele libere a versão mais recente do Adobe Commerce para produção no mesmo dia em que o pré-lançamento do Adobe Commerce foi lançado.

   ![[!DNL Upgrade Compatibility Tool] público](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Uma instância baunilha é uma instalação limpa de uma tag ou ramificação de versão especificada para uma versão específica.

## Pré-requisitos

Consulte [pré-requisitos](../upgrade-compatibility-tool/prerequisites.md) para obter mais informações.

>[!NOTE]
>
>Você pode executar o [!DNL Upgrade Compatibility Tool] em qualquer sistema operacional. Não há necessidade de executar o [!DNL Upgrade Compatibility Tool] onde a instância do Adobe Commerce está localizada. É necessário [!DNL Upgrade Compatibility Tool] para ter acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalar a ferramenta em um servidor e apontá-la para a instalação do Adobe Commerce em outro servidor.

Se você estiver executando o [!DNL Upgrade Compatibility Tool] em relação a uma instância do Adobe Commerce com módulos e arquivos grandes, a ferramenta pode exigir uma quantidade alta de RAM, pelo menos 2 GB de RAM.

### Ações recomendadas

As práticas recomendadas da Adobe Commerce recomendam evitar dois módulos com o mesmo nome. Se isso acontecer, a variável [!DNL Upgrade Compatibility Tool] mostra um erro de falha de segmentação.

Para evitar esse erro, é recomendável executar a variável `bin` com a opção adicionada `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>O `<dir>` é o diretório onde sua instância do Adobe Commerce está localizada.

O `-m` permite [!DNL Upgrade Compatibility Tool] para analisar cada módulo específico independentemente para evitar encontrar dois módulos com o mesmo nome na instância do Adobe Commerce.

Essa opção de comando também permite [!DNL Upgrade Compatibility Tool] para analisar uma pasta contendo vários módulos:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Essa recomendação também ajuda com problemas de memória que podem ocorrer ao executar o [!DNL Upgrade Compatibility Tool].

## Baixe o [!DNL Upgrade Compatibility Tool]

Para baixar o [!DNL Upgrade Compatibility Tool], execute o seguinte comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Instalar

Para instalar o [!DNL Upgrade Compatibility Tool], instale os pré-requisitos necessários:

* Chaves de acesso do Adobe Commerce
* Composer
* Node.js

### Chaves de acesso do Adobe Commerce

Você deve ter [Chaves de acesso do Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) para baixar e usar o [!DNL Upgrade Compatibility Tool]. Adicione as chaves de acesso do Adobe Commerce à `auth.json` arquivo , localizado em `~/.composer` por padrão.

>[!WARNING]
>
>Verifique sua **COMPOSER_HOME** variável de ambiente para ver onde a variável `auth.json` está localizado.

O **chave pública** corresponde a _username_ Considerando que **chave privada** é _senha_:

### Exemplo de chaves de acesso do Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Composer

Clonar o [!DNL Upgrade Compatibility Tool] repositório e execução `composer install` no terminal para instalar dependências.

>[!WARNING]
>
>Se a variável **Chaves de acesso do Adobe Commerce** não estão configuradas corretamente, a variável [!DNL Upgrade Compatibility Tool] não será instalado e ocorrerão erros ao executar o `composer install` comando.

### Node.js

Para instalar o Node.js, consulte Node.js [documentação](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensões de terceiros

O Adobe recomenda que você entre em contato com o fornecedor da extensão para determinar se a extensão é totalmente compatível com o Adobe Commerce 2.4.x.

Consulte [Executar a ferramenta](../upgrade-compatibility-tool/run.md) para obter informações sobre como executar o [!DNL Upgrade Compatibility Tool].
