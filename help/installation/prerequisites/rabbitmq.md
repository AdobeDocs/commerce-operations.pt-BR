---
title: Agente de mensagens
description: Siga estas etapas para instalar e configurar o software do mediador de mensagens necessário (como [!DNL RabbitMQ]) para instalações no local da Adobe Commerce e do Magento Open Source.
source-git-commit: 1233d2e1d80a3228626be3e20f1bd826b1283523
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Agente de mensagens

A Adobe Commerce usa a variável [!DNL RabbitMQ] agente de mensagens de código aberto. Ele oferece um sistema de mensagens confiável, altamente disponível, escalável e portátil.

As filas de mensagens fornecem um mecanismo de comunicação assíncrono no qual o remetente e o destinatário de uma mensagem não se conectam. Nem precisam se comunicar com a fila de mensagens ao mesmo tempo. Quando um remetente coloca uma mensagem em uma fila, ela é armazenada até que o recipient a receba.

O sistema de fila de mensagens deve ser estabelecido antes de instalar o Adobe Commerce ou o Magento Open Source. A sequência básica é:

1. Instalar [!DNL RabbitMQ] e quaisquer pré-requisitos.
1. Connect [!DNL RabbitMQ] para Adobe Commerce ou Magento Open Source.

>[!NOTE]
>
>Você pode usar o MySQL ou [!DNL RabbitMQ] para processamento de fila de mensagens. Para obter detalhes sobre como configurar o sistema de fila de mensagens, consulte [Visão geral das filas de mensagens](https://developer.adobe.com/commerce/php/development/components/message-queues/). Se estiver usando a API em massa com o Adobe Commerce, a configuração do sistema da fila de mensagens assumirá como padrão o uso de [!DNL RabbitMQ] como o mediador de mensagens. Consulte [Iniciar consumidores de fila de mensagens](../../configuration/cli/start-message-queues.md) para obter mais informações.

## Instalar [!DNL RabbitMQ] no Ubuntu

Para instalar [!DNL RabbitMQ] no Ubuntu 16, digite o seguinte comando:

```bash
sudo apt install -y rabbitmq-server
```

Este comando também instala os pacotes Erlang necessários.

Se você tiver uma versão mais antiga do Ubuntu, [!DNL RabbitMQ] A recomenda instalar o pacote do site.

1. Baixe o pacote .deb de [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Instale o pacote com `dpkg`.

Consulte [Instalação no Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) para obter mais informações.

## Instalar [!DNL RabbitMQ] no CentOS

### Instalar o Erlang

[!DNL RabbitMQ] foi escrito usando a linguagem de programação Erlang, que deve ser instalada no mesmo sistema que [!DNL RabbitMQ].

Consulte [Instalação manual](https://www.erlang-solutions.com/downloads/) para obter mais informações.

Consulte a [[!DNL RabbitMQ]Matriz de versão do /Erlang](https://www.rabbitmq.com/which-erlang.html) para instalar a versão correta.

### Instalar [!DNL RabbitMQ]

O [!DNL RabbitMQ] está incluído no CentOS, mas a versão geralmente é antiga. [!DNL RabbitMQ] A recomenda instalar o pacote do site.

Consulte a [!DNL RabbitMQ] instale a página para obter a versão mais recente compatível. Suporte para Adobe Commerce e Magento Open Source 2.3 e 2.4 [!DNL RabbitMQ] 3.8.x

Consulte [Instalação no Linux baseado em RPM](https://www.rabbitmq.com/install-rpm.html) para obter mais informações.

## Configurar [!DNL RabbitMQ]

Revise o [!DNL RabbitMQ] documentação para configurar e gerenciar [!DNL RabbitMQ]. Preste atenção aos seguintes itens:

* Variáveis de ambiente
* Acesso à porta
* Contas de usuário padrão
* Iniciar e parar o corretor
* Limites do sistema

## Instalar com [!DNL RabbitMQ] e conectar

Se você instalar o Adobe Commerce ou o Magento Open Source _after_ você instala [!DNL RabbitMQ], adicione os seguintes parâmetros de linha de comando durante a instalação:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Em que:

| Parâmetro | Descrição |
|--- |--- |
| `--amqp-host` | O nome do host onde [!DNL RabbitMQ] está instalado. |
| `--amqp-port` | A porta a ser usada para conexão [!DNL RabbitMQ]. O padrão é `5672`. |
| `--amqp-user` | O nome de usuário para conexão com o [!DNL RabbitMQ]. Não usar o usuário padrão `guest`. |
| `--amqp-password` | A senha para conexão com o [!DNL RabbitMQ]. Não use a senha padrão `guest`. |
| `--amqp-virtualhost` | O host virtual para conexão com o [!DNL RabbitMQ]. O padrão é `/`. |
| `--amqp-ssl` | Indica se deseja se conectar ao [!DNL RabbitMQ]. O padrão é `false`. Se você definir o valor como true, consulte Configurar SSL para obter mais informações. |

## Connect [!DNL RabbitMQ]

Se você já tiver o Adobe Commerce ou o Magento Open Source instalado e deseja conectá-lo [!DNL RabbitMQ], adicione um `queue` na seção `<install_directory>/app/etc/env.php` para que seja semelhante ao seguinte:

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

Você também pode definir [!DNL RabbitMQ] valores de configuração usando o `bin/magento setup:config:set` comando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Após executar o comando ou atualizar o `<install_directory>/app/etc/env.php` arquivo com valores de configuração AMQP, execute `bin/magento setup:upgrade` para aplicar as alterações e criar as filas e trocas necessárias no [!DNL RabbitMQ].

## Configurar SSL

Para configurar o suporte para SSL, edite o `ssl` e `ssl_options` na `<install_directory>/app/etc/env.php` para que sejam semelhantes ao seguinte:

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

Depois de conectar o Adobe Commerce e [!DNL RabbitMQ], você deve iniciar os consumidores da fila de mensagens. Consulte [Configurar filas de mensagem](../../configuration/cli/start-message-queues.md) para obter detalhes.
