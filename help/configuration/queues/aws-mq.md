---
title: Configurar a fila de mensagens do Amazon
description: Saiba como configurar o Commerce para usar o serviço AWS MQ.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Configurar a fila de mensagens do Amazon

A partir do Commerce 2.4.3, o Amazon Message Queue (MQ) estará disponível como uma substituição pronta para nuvem para instâncias de fila de mensagens no local.

Para criar uma fila de mensagens no AWS, consulte [Configuração do Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) no _Documentação do AWS_.

## Configurar o Commerce para AWS MQ

Para se conectar ao serviço AWS MQ, configure a variável `queue.amqp` na `env.php` arquivo.
A Fila de mensagens do AWS requer uma conexão SSL/TLS.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

Em que:

- `host`—O url do ponto de extremidade AMQP; disponível clicando no nome do agente no AWS (remova &quot;https://&quot; e o número da porta à direita)
- `user`—O valor do nome de usuário inserido ao criar o AWS MQ broker
- `password`—O valor da senha inserido ao criar o AWS MQ broker

>[!INFO]
>
>O Amazon MQ é compatível somente com conexões TLS. Não há suporte para verificação de mesmo nível.

Depois de editar o `env.php` execute o seguinte comando para concluir a configuração:

```bash
bin/magento setup:upgrade
```

## Como o Commerce usa o serviço AWS MQ

O `async.operations.all` o consumidor da fila de mensagens usa a conexão AMQP.

Esse consumidor encaminha qualquer nome de tópico prefixado com `async` por meio da conexão AWS MQ.

Por exemplo, em `InventoryCatalog` há:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

A configuração padrão para `InventoryCatalog` não publica mensagens no RabbitMQ; o comportamento padrão é executar a ação no mesmo thread do usuário. Para dizer `InventoryCatalog` para publicar mensagens, habilite `cataloginventory/bulk_operations/async`. No administrador, acesse **Lojas** > Configuração > **Catálogo** > **Inventário** > Administração de operações em massa e conjunto  `Run asynchronously`para **Sim**.

## Teste da fila de mensagens

Para testar o envio de mensagens do Commerce para o RabbitMQ:

1. Faça logon no console da Web do RabbitMQ no AWS para monitorar as filas.
1. No Administrador, crie um produto.
1. Crie uma fonte de inventário.
1. Habilitar **Lojas** > Configuração > **Catálogo** > **Inventário** > Operações de administração em massa > Executar de forma assíncrona.
1. Ir para **Catálogo** > Produtos. Na grade, selecione o produto criado acima e clique em **Atribuir Origem de Inventário**.
1. Clique em **Salvar e fechar** para concluir o processo.

   Agora, você deve ver mensagens exibidas no console da Web do RabbitMQ.

1. Inicie o `async.operations.all` consumidor da fila de mensagens.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Agora você deve ver a mensagem na fila ser processada no console da Web do RabbitMQ.
Verifique se as fontes de inventário foram alteradas no produto em Admin.
