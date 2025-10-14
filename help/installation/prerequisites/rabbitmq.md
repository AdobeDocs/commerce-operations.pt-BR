---
title: Agente de mensagem (RabbitMQ)
description: Siga estas etapas para instalar e configurar o software agente de mensagens necessário (como o  [!DNL RabbitMQ]) para instalações locais do Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 73faaa2a3b9ce773e9a381d103735403966f568b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Agente de mensagem (RabbitMQ)

O Adobe Commerce usa o agente de mensagens de código aberto [!DNL RabbitMQ]. Ele oferece um sistema de mensagens confiável, altamente disponível, escalável e portátil.

As filas de mensagens fornecem um mecanismo de comunicação assíncrono no qual o remetente e o destinatário de uma mensagem não entram em contato entre si. Eles também não precisam se comunicar com a fila de mensagens ao mesmo tempo. Quando um remetente coloca uma mensagem em uma fila, ela é armazenada até que o destinatário a receba.

O sistema de fila de mensagens deve ser estabelecido antes da instalação do Adobe Commerce. A sequência básica é:

1. Instale o [!DNL RabbitMQ] e qualquer pré-requisito.
1. Conectar [!DNL RabbitMQ] ao Adobe Commerce.

>[!NOTE]
>
>Você pode usar MySQL ou [!DNL RabbitMQ] para processamento de fila de mensagens. Para obter detalhes sobre a configuração do sistema de fila de mensagens, consulte [Visão geral das filas de mensagens](https://developer.adobe.com/commerce/php/development/components/message-queues/). Se você estiver usando a API em massa com o Adobe Commerce, a configuração do sistema de fila de mensagens usa [!DNL RabbitMQ] como o agente de mensagens. Consulte [Iniciar consumidores da fila de mensagens](../../configuration/cli/start-message-queues.md) para obter mais informações.

## Instalar o [!DNL RabbitMQ] no Ubuntu

Para instalar o [!DNL RabbitMQ] no Ubuntu 16, digite o seguinte comando:

```bash
sudo apt install -y rabbitmq-server
```

Este comando também instala os pacotes Erlang necessários.

Se você tiver uma versão mais antiga do Ubuntu, a [!DNL RabbitMQ] recomenda instalar o pacote de seu site.

1. Baixe o pacote .deb de [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Instalar o pacote com `dpkg`.

Consulte [Instalando no Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) para obter mais informações.

## Instalar [!DNL RabbitMQ] no CentOS

### Instalar Erlang

[!DNL RabbitMQ] foi gravado usando a linguagem de programação Erlang, que deve ser instalada no mesmo sistema que [!DNL RabbitMQ].

Consulte [Instalação manual](https://www.erlang-solutions.com/downloads/) para obter mais informações.

Consulte a [[!DNL RabbitMQ]/Erlang version matrix](https://www.rabbitmq.com/which-erlang.html) para instalar a versão correta.

### Instalar [!DNL RabbitMQ]

O servidor [!DNL RabbitMQ] está incluído no CentOS, mas a versão é frequentemente antiga. O [!DNL RabbitMQ] recomenda instalar o pacote de seu site.

Consulte a página de instalação [!DNL RabbitMQ] para obter a versão mais recente com suporte. O Adobe Commerce 2.3 e 2.4 são compatíveis com [!DNL RabbitMQ] 3.8.x.

Consulte [Instalando no Linux baseado em RPM](https://www.rabbitmq.com/install-rpm.html) para obter mais informações.

## Configurar [!DNL RabbitMQ]

Consulte a documentação oficial [!DNL RabbitMQ] para configurar e gerenciar [!DNL RabbitMQ]. Preste atenção aos seguintes itens:

* Variáveis de ambiente
* Acesso à porta
* Contas de usuário padrão
* Iniciando e interrompendo o agente
* Limites do sistema

## Instalar com [!DNL RabbitMQ] e conectar

Se você instalar o Adobe Commerce _depois_ de instalar o [!DNL RabbitMQ], adicione os seguintes parâmetros de linha de comando durante a instalação:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Onde:

| Parâmetro | Descrição |
|--- |--- |
| `--amqp-host` | O nome do host em que [!DNL RabbitMQ] está instalado. |
| `--amqp-port` | A porta a ser usada para conexão com [!DNL RabbitMQ]. O padrão é `5672`. |
| `--amqp-user` | O nome de usuário para conexão com [!DNL RabbitMQ]. Não usar o usuário padrão `guest`. |
| `--amqp-password` | A senha para conexão com [!DNL RabbitMQ]. Não usar a senha padrão `guest`. |
| `--amqp-virtualhost` | O host virtual para conexão com [!DNL RabbitMQ]. O padrão é `/`. |
| `--amqp-ssl` | Indica se é necessário conectar a [!DNL RabbitMQ]. O padrão é `false`. Se você definir o valor como true, consulte Configurar SSL para obter mais informações. |

## Conectar [!DNL RabbitMQ]

Se você já tiver o Adobe Commerce instalado e quiser conectá-lo ao [!DNL RabbitMQ], adicione uma seção `queue` no arquivo `<install_directory>/app/etc/env.php` para que ela seja semelhante ao seguinte:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

Você também pode definir valores de configuração [!DNL RabbitMQ] usando o comando `bin/magento setup:config:set`:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Após executar o comando ou atualizar o arquivo `<install_directory>/app/etc/env.php` com valores de configuração AMQP, execute `bin/magento setup:upgrade` para aplicar as alterações e criar as filas e trocas necessárias em [!DNL RabbitMQ].

## Configurar SSL

Para configurar o suporte para SSL, edite os parâmetros `ssl` e `ssl_options` no arquivo `<install_directory>/app/etc/env.php` para que sejam semelhantes ao seguinte:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## Iniciar os consumidores da fila de mensagens

Depois de conectar o Adobe Commerce e o [!DNL RabbitMQ], você deve iniciar os consumidores da fila de mensagens. Consulte [Configurar filas de mensagens](../../configuration/cli/start-message-queues.md) para obter detalhes.
