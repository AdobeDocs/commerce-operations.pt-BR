---
title: Agente de mensagem (AtiveMQ Artemis)
description: Siga estas etapas para instalar e configurar o agente de mensagens Apache AtiveMQ Artemis para instalações locais do Adobe Commerce.
source-git-commit: aee02c258acaeb7a248e10b867017ef8f72b544d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Agente de mensagem (AtiveMQ Artemis)

O Adobe Commerce também oferece suporte ao agente de mensagens de código aberto AtiveMQ Artemis por meio do Simple Text Oriented Messaging Protocol (STOMP). Ele oferece um sistema de mensagens confiável e escalável, oferecendo flexibilidade para integrações baseadas em STOMP.


>[!NOTE]
>
>O AtiveMQ Artemis foi introduzido no Adobe Commerce 2.4.6 e versões posteriores. Para obter detalhes sobre como instalar o AtiveMQ Artemis no Adobe Commerce em projetos de infraestrutura em nuvem, consulte [Configurar o serviço AtiveMQ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemq) no *Guia do Commerce na Nuvem*.

As filas de mensagens fornecem um mecanismo de comunicação assíncrono no qual o remetente e o destinatário de uma mensagem não entram em contato entre si. Eles também não precisam se comunicar com a fila de mensagens ao mesmo tempo. Quando um remetente coloca uma mensagem em uma fila, ela é armazenada até que o destinatário a receba.

O sistema de fila de mensagens deve ser estabelecido antes da instalação do Adobe Commerce. A sequência básica é:

1. Instale o Apache AtiveMQ Artemis e todos os pré-requisitos.
1. Conecte o AtiveMQ ao Adobe Commerce.

>[!NOTE]
>
>Você pode usar MySQL, AtiveMQ ou [!DNL RabbitMQ] para processamento de fila de mensagens. Para obter detalhes sobre a configuração do sistema de fila de mensagens, consulte [Visão geral das filas de mensagens](https://developer.adobe.com/commerce/php/development/components/message-queues/). Se você estiver usando a API em massa com o Adobe Commerce, a configuração do sistema de fila de mensagens usa [!DNL RabbitMQ] como o agente de mensagens. Consulte [Iniciar consumidores da fila de mensagens](../../configuration/cli/start-message-queues.md) para obter mais informações.

>[!TIP]
>
>Sempre verifique a [página de download do Apache AtiveMQ Artemis](https://activemq.apache.org/components/artemis/download/) para obter a versão estável mais recente antes da instalação. Os exemplos neste documento usam a versão 2.42.0, que foi a versão estável mais recente em setembro de 2025.


## Instalar o Apache AtiveMQ Artemis

Você pode instalar o AtiveMQ Artemis usando Docker (recomendado para desenvolvimento) ou instalação manual (recomendado para produção).

### Opção 1: Instalação do Docker (recomendada para desenvolvimento)

#### Pré-requisitos

Verifique se o Docker está instalado e em execução no sistema.

>[!TIP]
>
>Para obter mais informações sobre a imagem oficial do AtiveMQ Artemis Docker, consulte a [página Hub do Apache AtiveMQ Artemis Docker](https://hub.docker.com/r/apache/activemq-artemis).

#### Etapas de instalação

1. Execute o AtiveMQ Artemis usando a imagem oficial do Docker:

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. Executar com credenciais personalizadas:

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Comandos de gerenciamento do Docker

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### Acesso aos serviços

Depois que o container do Docker estiver em execução, você poderá acessar:

- **Console da Web**: http://localhost:8161/console (credenciais padrão: artemis/artemis)
- **Porta STOMP**: localhost:61613 (para conexão com o Adobe Commerce)

>[!NOTE]
>
>A instalação do Docker é recomendada para desenvolvimento e teste. Para produção, considere usar a instalação manual com configurações de segurança adequadas.

### Opção 2: instalação manual no Ubuntu/CentOS

#### Pré-requisitos

Verifique se o Java 17 ou superior está instalado (necessário para o AtiveMQ Artemis 2.42.0+).

### Etapas de instalação

1. Baixe e instale a versão mais recente do [site Apache AtiveMQ Artemis](https://activemq.apache.org/components/artemis/download/). A partir de setembro de 2025, a versão estável mais recente é a 2.42.0:

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. Criar o usuário `artemis` e definir a propriedade:

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Criar uma instância de agente:

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Inicie o broker:

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## Configurar AtiveMQ Artemis

Consulte a documentação oficial do AtiveMQ Artemis para configurar e gerenciar o broker. Preste atenção aos seguintes itens:

- Variáveis de ambiente
- Acesso à porta (protocolo STOMP)
- Contas e credenciais de usuário padrão
- Iniciando e interrompendo o agente
- Limites do sistema e ajuste de recursos

### Arquivos de configuração de chave

- `/var/lib/artemis-instance/etc/broker.xml` - Configuração do agente principal
- `/var/lib/artemis-instance/etc/artemis-users.properties` - Autenticação de usuário
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - Funções do usuário
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Configuração do Bootstrap

### Habilitar o protocolo STOMP

Verifique `/var/lib/artemis-instance/etc/broker.xml` para garantir que o aceitador de STOMP esteja configurado:

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

Para habilitar SSL no STOMP, você deve adicionar explicitamente o aceitador `stomp-ssl`.

## Instale com o AtiveMQ Artemis e conecte

Se você instalar o Adobe Commerce _depois_ de instalar o AtiveMQ Artemis, adicione os seguintes parâmetros de linha de comando durante a instalação:

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

Onde:

| Parâmetro | Descrição |
|--- |--- |
| `--stomp-host` | O nome do host onde o AtiveMQ está instalado. |
| `--stomp-port` | A porta a ser usada para conectar ao AtiveMQ. O padrão é `61613`. |
| `--stomp-user` | O nome de usuário para conexão com o AtiveMQ. Não usar o usuário padrão `artemis`. |
| `--stomp-password` | A senha para conexão com o AtiveMQ. Não usar a senha padrão `artemis`. |
| `--stomp-ssl` | Indica se é necessário se conectar ao AtiveMQ. O padrão é `false`. Se você definir o valor como true, consulte Configurar SSL para obter mais informações. |

## Conectar AtiveMQ Artemis

Se você já tiver uma instância do Adobe Commerce com configuração RabbitMQ (AMQP) no arquivo `<install_directory>/app/etc/env.php` e quiser conectá-la ao AtiveMQ, substitua a seção `queue` pelo STOMP para que seja semelhante ao seguinte:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

Você também pode definir valores de configuração do AtiveMQ usando o comando `bin/magento setup:config:set` (remova a configuração AMQP se ela existir no arquivo `app/etc/env.php`):

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

Após executar o comando ou atualizar o arquivo `<install_directory>/app/etc/env.php` com valores de configuração STOMP, execute `bin/magento setup:upgrade` para aplicar as alterações e criar as filas necessárias no AtiveMQ.

## Configurar SSL

Para configurar o suporte para SSL, edite os parâmetros `ssl` e `ssl_options` no arquivo `<install_directory>/app/etc/env.php` para que sejam semelhantes ao seguinte:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### Opções de configuração do SSL

| Opção | Descrição | Padrão |
|--- |--- |--- |
| `verify_peer` | Verificar o certificado SSL do agente | `true` |
| `verify_peer_name` | Verifique se o nome de host do agente corresponde ao certificado | `true` |
| `allow_self_signed` | Permitir certificados autoassinados | `false` |
| `cafile` | Caminho para o arquivo de certificado de autoridade de certificação para verificação do agente | Obrigatório para SSL |
| `certfile` | Caminho para o arquivo de certificado do cliente (para SSL mútuo) | Opcional |
| `keyfile` | Caminho para o arquivo de chave privada do cliente (para SSL mútuo) | Opcional |
| `passphrase` | Senha da chave privada do cliente | Opcional |

### Configuração do SSL de desenvolvimento

Para ambientes de desenvolvimento, é possível usar configurações SSL relaxadas:

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## Ajuste de desempenho

O AtiveMQ Artemis oferece várias opções de ajuste de desempenho:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## Monitoramento e gerenciamento

### Console da Web

O AtiveMQ Artemis fornece um console de gerenciamento baseado na Web acessível em:
- URL: `http://localhost:8161/console`
- Credenciais padrão: `artemis/artemis`

## Solução de problemas

### Problemas comuns

1. **Conexão recusada**: verifique se a AtiveMQ Artemis está em execução e se o aceitador STOMP está configurado.
1. **Falha de autenticação**: verifique o nome de usuário/senha tanto na configuração do agente quanto no arquivo `env.php`.
1. **Falha no handshake de SSL**: verifique a configuração e os certificados SSL.




### Verificar conexão STOMP

Testar conexão STOMP usando telnet:

```bash
telnet localhost 61613
```

Você deve ver uma conexão estabelecida. Para testar com um comando STOMP:

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

A saída esperada deve mostrar a conexão estabelecida e a resposta do protocolo STOMP.

## Iniciar os consumidores da fila de mensagens

Depois de conectar o Adobe Commerce e o AtiveMQ Artemis, você deve iniciar os consumidores da fila de mensagens. Consulte [Configurar filas de mensagens](../../configuration/cli/start-message-queues.md) para obter detalhes.

