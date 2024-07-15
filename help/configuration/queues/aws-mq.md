---
title: Configurar Fila de Mensagens do Amazon
description: Saiba como configurar o Commerce para usar o serviço AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Configurar Fila de Mensagens do Amazon

A partir do Commerce 2.4.3, o Amazon Message Queue (MQ) está disponível como uma substituição pronta para nuvem para instâncias de fila de mensagens locais.

Para criar uma fila de mensagens no AWS, consulte [Configuração do Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) na _documentação do AWS_.

## Configuração do Commerce para AWS MQ

Para se conectar ao serviço AWS MQ, configure o objeto `queue.amqp` no arquivo `env.php`.
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

- `host`—A url do ponto de extremidade AMQP; disponível ao clicar no nome do agente no AWS (remova &quot;https://&quot; e o número da porta à direita)
- `user` — O valor de nome de usuário inserido ao criar o agente do AWS MQ
- `password` — O valor de senha inserido ao criar o agente do AWS MQ

>[!INFO]
>
>O Amazon MQ oferece suporte somente a conexões TLS. A verificação de mesmo nível não é suportada.

Após editar o arquivo `env.php`, execute o seguinte comando para concluir a instalação:

```bash
bin/magento setup:upgrade
```

## Como o Commerce usa o serviço AWS MQ

O consumidor da fila de mensagens `async.operations.all` usa a conexão AMQP.

Esse consumidor roteia qualquer nome de tópico com o prefixo `async` pela conexão do AWS MQ.

Por exemplo, em `InventoryCatalog` há:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

A configuração padrão para `InventoryCatalog` não publica mensagens em [!DNL RabbitMQ]; o comportamento padrão é executar a ação no mesmo thread de usuário. Para instruir `InventoryCatalog` a publicar mensagens, habilite `cataloginventory/bulk_operations/async`. No administrador, vá para **Lojas** > Configuração > **Catálogo** > **Inventário** > Operações em massa do administrador e defina `Run asynchronously`como **Sim**.

## Teste da fila de mensagens

Para testar o envio de mensagens do Commerce para [!DNL RabbitMQ]:

1. Faça logon no console da Web [!DNL RabbitMQ] no AWS para monitorar filas.
1. Em Admin, crie um produto.
1. Criar uma origem de Inventário.
1. Habilitar **Lojas** > Configuração > **Catálogo** > **Inventário** > Operações de administração em massa > Executar de forma assíncrona.
1. Vá para **Catálogo** > Produtos. Na grade, selecione o produto criado acima e clique em **Atribuir Source de Inventário**.
1. Clique em **Salvar e fechar** para concluir o processo.

   Agora você deve ver as mensagens aparecendo no console da Web [!DNL RabbitMQ].

1. Iniciar o consumidor da fila de mensagens `async.operations.all`.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Agora você deve ver a mensagem na fila ser processada no console da Web [!DNL RabbitMQ].
Verifique se as origens do inventário foram alteradas no produto na Admin.
