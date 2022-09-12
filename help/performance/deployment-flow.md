---
title: Fluxo de implantação
description: Saiba mais sobre as etapas necessárias para implantar o Adobe Commerce ou o Magento Open Source em um ambiente de produção.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Fluxo de implantação

O [!DNL Commerce] o fluxo de implantação de produção ajuda uma loja a alcançar o desempenho máximo.

## Instalar dependências

O `composer.json` e `composer.lock` gerenciamento de arquivos [!DNL Commerce] dependências e instale a versão apropriada para cada pacote. Você deve instalar as dependências antes de [instruções de injeção de dependência de pré-processamento](#preprocess-dependency-injection-instructions) se você planeja atualizar a variável [carregador automático](#update-the-autoloader).

Para instalar [!DNL Commerce] dependências:

```bash
composer install --no-dev
```

## Instruções de injeção de dependência de pré-processamento

Ao pré-processar e compilar as instruções de injeção de dependência (ID), Magento:

* Lê e processa todas as configurações presentes
* Analisa dependências entre classes
* Cria arquivos gerados automaticamente (incluindo proxies, fábricas, etc.)
* Armazena dados e configurações compilados em um cache que economiza até 25% do tempo no processamento de solicitações

Para pré-processar e compilar instruções de ID:

```bash
bin/magento setup:di:compile
```

## Atualizar o carregador automático

Depois que a compilação for concluída, confirme se [APCu está ativado](../performance/software.md#php-settings) e atualize o carregador automático:

Para atualizar o carregador automático:

>[!INFO]
>
>O `-o` converte o carregamento automático PSR-0/4 em classmap para obter um carregador automático mais rápido. O `--apcu` A opção usa o APCu para armazenar em cache as classes encontradas/não encontradas.

```bash
composer dump-autoload -o --apcu
```

Se você planeja atualizar o carregador automático, é necessário executar os seguintes comandos em ordem:

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## Implantar conteúdo estático

A implantação de conteúdo estático causa [!DNL Commerce] para executar as seguintes ações:

* Analisar todos os recursos estáticos
* Fazer mesclagem, minimização e empacotamento de conteúdo
* Ler e processar dados de temas
* Analisar fallback de tema
* Armazenar todo o conteúdo processado e materializado em uma pasta específica para uso adicional

Se o conteúdo estático não for implantado, [!DNL Commerce] realiza todas as operações listadas em tempo real, levando a um aumento significativo no tempo de resposta.

Você pode usar uma variedade de opções para personalizar as operações de implantação com base no tamanho da loja e nas necessidades de atendimento. A estratégia de implantação compacta é a mais comum. Consulte [Estratégias de implantação de arquivos estáticos](../configuration/cli/static-view-file-strategy.md)

Para implantar conteúdo estático:

```bash
bin/magento setup:static-content:deploy
```

Esse comando permite que o Composer recrie o mapeamento para arquivos de projeto para que eles sejam carregados mais rápido.

## Definir modo de produção

>[!INFO]
>
>A configuração do modo para produção é executada automaticamente `setup:di:compile` e `setup:static-content:deploy`.

Por fim, você precisa colocar sua loja no modo Produção. O modo de produção é especificamente otimizado para obter o máximo desempenho de sua loja. Ela também desativa todos os recursos específicos do desenvolvedor. Isso pode ser feito em `.htaccess` ou `nginx.conf` arquivo:

`SetEnv MAGE_MODE production`

Você também pode implantar conteúdo estático, compilar o conteúdo e definir o modo em um comando da CLI:

```bash
bin/magento deploy:mode:set production
```

O comando é executado em segundo plano e não permite que você defina opções adicionais em cada etapa específica.

## Ações adicionais de pré-lançamento

Essas etapas são recomendadas, mas não são obrigatórias. Você pode executá-los imediatamente antes de iniciar sua loja no modo de produção. A lista inclui:

* Reindexe os dados para evitar a presença de dados inconsistentes em seus índices.
* Limpe o cache para ter certeza de que nenhum dado antigo ou incorreto será deixado no cache.
* Aqueça o cache, que chama as páginas de armazenamento mais populares ou críticas antecipadamente, para que o cache para elas seja gerado e armazenado. Essa operação pode ser executada com qualquer rastreador de Internet ou manualmente, se você tiver uma loja pequena.
