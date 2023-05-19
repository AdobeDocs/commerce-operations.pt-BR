---
title: Configurar Fila de Mensagens do Amazon
description: Saiba como configurar o Commerce para usar o serviço AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Configurar Fila de Mensagens do Amazon

A partir do Commerce 2.4.3, o Amazon Message Queue (MQ) está disponível como uma substituição pronta para nuvem para instâncias de fila de mensagens locais.

Para criar uma fila de mensagens no AWS, consulte [Configuração do Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) no _Documentação do AWS_.

## Configurar o Commerce para o AWS MQ

Para se conectar ao serviço AWS MQ, configure o `queue.amqp` objeto no `env.php` arquivo.
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

Onde:

- `host`—O url para o endpoint AMQP; disponível ao clicar no nome do broker no AWS (remova &quot;https://&quot; e o número da porta à direita)
- `user`—O valor do nome de usuário inserido ao criar o broker do AWS MQ
- `password`—O valor de senha inserido ao criar o AWS MQ Broker

>[!INFO]
>
>O Amazon MQ oferece suporte somente a conexões TLS. A verificação de mesmo nível não é suportada.

Após editar o `env.php` execute o seguinte comando para concluir a configuração:

```bash
bin/magento setup:upgrade
```

## Como o Commerce usa o serviço AWS MQ

A variável `async.operations.all` O consumidor da fila de mensagens usa a conexão AMQP.

Esse consumidor encaminha qualquer nome de tópico com o prefixo `async` por meio da conexão AWS MQ.

Por exemplo, em `InventoryCatalog` há:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

A configuração padrão para `InventoryCatalog` não publica mensagens no [!DNL RabbitMQ]; o comportamento padrão é executar a ação no mesmo thread do usuário. Para saber `InventoryCatalog` para publicar mensagens, ative `cataloginventory/bulk_operations/async`. No admin, acesse **Lojas** > Configuração > **Catálogo** > **Inventário** > Administração de operações em massa e definir  `Run asynchronously`para **Sim**.

## Teste da fila de mensagens

Para testar o envio de mensagens do Commerce para o [!DNL RabbitMQ]:

1. Faça logon no [!DNL RabbitMQ] console da web no AWS para monitorar filas.
1. Em Admin, crie um produto.
1. Criar uma origem de Inventário.
1. Ativar **Lojas** > Configuração > **Catálogo** > **Inventário** > Administração de operações em massa > Executar de forma assíncrona.
1. Ir para **Catálogo** > Produtos. Na grade, selecione o produto criado acima e clique em **Atribuir Origem do Inventário**.
1. Clique em **Salvar e fechar** para concluir o processo.

   Agora você deverá ver mensagens aparecendo no [!DNL RabbitMQ] console da web.

1. Inicie o `async.operations.all` consumidor da fila de mensagens.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Agora você deve ver a mensagem em fila ser processada no [!DNL RabbitMQ] console da web.
Verifique se as origens do inventário foram alteradas no produto na Admin.
