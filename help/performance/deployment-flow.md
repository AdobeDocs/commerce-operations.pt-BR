---
title: Fluxo de implantação
description: Saiba mais sobre as etapas necessárias para implantar o Adobe Commerce em um ambiente de produção.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Fluxo de implantação

A variável [!DNL Commerce] o fluxo de implantação de produção ajuda uma loja a alcançar o desempenho máximo.

## Instalar dependências

A variável `composer.json` e `composer.lock` arquivos gerenciar [!DNL Commerce] e instale a versão apropriada para cada pacote. Você deve instalar as dependências antes de [instruções de injeção de dependência de pré-processamento](#preprocess-dependency-injection-instructions) se você planeja atualizar a variável [carregador automático](#update-the-autoloader).

Para instalar [!DNL Commerce] dependências:

```bash
composer install --no-dev
```

## Pré-processar instruções de injeção de dependência

Ao pré-processar e compilar instruções de injeção de dependência (DI), Magento:

* Lê e processa todas as configurações presentes
* Analisa dependências entre classes
* Cria arquivos gerados automaticamente (incluindo proxies, fábricas, etc.)
* Armazena dados e configurações compilados em um cache que economiza até 25% do tempo no processamento de solicitações

Para pré-processar e compilar instruções de ID:

```bash
bin/magento setup:di:compile
```

## Atualizar o carregador automático

Após a conclusão da compilação, confirme se [APCu habilitado](../performance/software.md#php-settings) e atualize o carregador automático:

Para atualizar o carregador automático:

>[!INFO]
>
>A variável `-o` A opção converte o carregamento automático PSR-0/4 em classmap para obter um carregador automático mais rápido. A variável `--apcu` A opção usa APCu para armazenar em cache classes encontradas/não encontradas.

```bash
composer dump-autoload -o --apcu
```

Se você planeja atualizar o carregador automático, é necessário executar os seguintes comandos na ordem:

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
* Realizar mesclagem, minimização e agrupamento de conteúdo
* Ler e processar dados de tema
* Analisar fallback do tema
* Armazenar todo o conteúdo processado e materializado na pasta específica para uso adicional

Se o conteúdo estático não for implantado, [!DNL Commerce] O executa todas as operações listadas em tempo real, resultando em um aumento significativo no tempo de resposta.

Você pode usar várias opções para personalizar as operações de implantação com base no tamanho da loja e nas necessidades de atendimento. O mais comum é a estratégia de implantação compacta. Consulte [Estratégias de implantação de arquivos estáticos](../configuration/cli/static-view-file-strategy.md)

Para implantar conteúdo estático:

```bash
bin/magento setup:static-content:deploy
```

Esse comando permite que o Composer recrie o mapeamento para arquivos de projeto, para que eles sejam carregados mais rapidamente.

## Definir modo de produção

>[!INFO]
>
>A definição do modo para produção é executada automaticamente `setup:di:compile` e `setup:static-content:deploy`.

Por fim, é necessário colocar a loja no modo de Produção. O modo de produção é otimizado especificamente para o desempenho máximo de sua loja. Também desativa todos os recursos específicos do desenvolvedor. Isso pode ser feito em seu `.htaccess` ou `nginx.conf` arquivo:

`SetEnv MAGE_MODE production`

Você também pode implantar conteúdo estático, compilar o conteúdo e definir o modo em um comando da CLI:

```bash
bin/magento deploy:mode:set production
```

O comando é executado em segundo plano e não permite definir opções adicionais em cada etapa específica.

## Ações adicionais de pré-lançamento

Essas etapas são recomendadas, mas não são obrigatórias. É possível executá-las imediatamente antes de iniciar o armazenamento no modo de produção. A lista inclui:

* Reindexe os dados para evitar a presença de dados inconsistentes em seus índices.
* Limpe o cache para garantir que nenhum dado antigo ou incorreto seja deixado no cache.
* Aqueça o cache, que chama as páginas de armazenamento mais populares ou críticas antecipadamente, para que o cache para elas seja gerado e armazenado. Esta operação pode ser executada com qualquer rastreador da Internet ou manualmente, se você tiver um pequeno armazenamento.
