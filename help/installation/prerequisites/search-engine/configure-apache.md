---
title: Configurar o Apache para seu mecanismo de pesquisa
description: Siga estas etapas para configurar um mecanismo de pesquisa com o servidor Web Apache para instalações locais do Adobe Commerce.
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Configurar o Apache para seu mecanismo de pesquisa

{{$include /help/_includes/web-server-communication.md}}

## Configurar um proxy

>[!NOTE]
>
>O suporte ao OpenSearch foi adicionado na versão 2.4.4. O OpenSearch é uma bifurcação compatível do Elasticsearch. Consulte [Migrar Elasticsearch para OpenSearch](../../../upgrade/prepare/opensearch-migration.md) para obter mais informações.

Esta seção discute como configurar o Apache como um proxy *não seguro* para que o Adobe Commerce possa usar um mecanismo de pesquisa em execução neste servidor. Esta seção não discute a configuração da autenticação básica de HTTP; ela é discutida em [Comunicação segura com o Apache](#secure-communication-with-apache).

>[!NOTE]
>
>O motivo pelo qual o proxy não é seguro neste exemplo é que é mais fácil de configurar e verificar. Você pode usar o TLS com esse proxy. Se desejar fazer isso, certifique-se de adicionar as informações do proxy à configuração do host virtual seguro.

### Configurar um proxy para o Apache 2.4

Esta seção discute como configurar um proxy usando um host virtual.

1. Habilite `mod_proxy` da seguinte maneira:

   ```bash
   a2enmod proxy_http
   ```

1. Usar um editor de texto para abrir `/etc/apache2/sites-available/000-default.conf`
1. Adicione a seguinte diretiva na parte superior do arquivo:

   ```conf
   Listen 8080
   ```

1. Adicione o seguinte na parte inferior do arquivo:

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Reiniciar o Apache:

   ```bash
   service apache2 restart
   ```

1. Verifique se o proxy funciona digitando o seguinte comando:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Por exemplo, se você estiver usando o Elasticsearch e seu proxy usar a porta 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Mensagens semelhantes ao seguinte são exibidas para indicar sucesso:

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Comunicação segura com o Apache

Esta seção discute como proteger a comunicação entre o Apache e o mecanismo de pesquisa usando a autenticação [HTTP Básica](https://datatracker.ietf.org/doc/html/rfc2617) com o Apache. Para obter mais opções, consulte um dos seguintes recursos:

* [Tutorial de autenticação e autorização do Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Consulte uma das seguintes seções:

* [Criar um arquivo de senha](#create-a-password)
* [Configurar o host virtual seguro](#secure-communication-with-apache)

### Criar uma senha

Por motivos de segurança, você pode localizar o arquivo de senha em qualquer lugar, exceto no docroot do servidor Web. Neste exemplo, mostramos como armazenar o arquivo de senha em um novo diretório.

#### Instale o htpasswd, se necessário

Primeiro, veja se o utilitário Apache `htpasswd` está instalado da seguinte maneira:

1. Digite o seguinte comando para determinar se `htpasswd` já está instalado:

   ```bash
   which htpasswd
   ```

   Se um caminho for exibido, ele será instalado; se o comando não retornar nenhuma saída, `htpasswd` não será instalado.

1. Se necessário, instale o `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### Criar um arquivo de senha

Digite os seguintes comandos como um usuário com privilégios de `root`:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Onde

* `<username>` pode ser:

   * Configuração do cron: o usuário do servidor Web ou outro usuário.

  Neste exemplo, usamos o usuário do servidor Web, mas a escolha do usuário depende de você.

   * Configurando o Elasticsearch: o usuário é nomeado como `magento_elasticsearch` neste exemplo

* `<password file name>` deve ser um arquivo oculto (começa com `.`) e deve refletir o nome do usuário. Consulte os exemplos posteriormente nesta seção para obter detalhes.

Siga as instruções na tela para criar uma senha para o usuário.

#### Exemplos

**Exemplo 1: cron**
Você deve configurar a autenticação para apenas um usuário para cron; neste exemplo, usamos o usuário do servidor Web. Para criar um arquivo de senha para o usuário do servidor Web, digite os seguintes comandos:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Exemplo 2: Elasticsearch**
Você deve configurar a autenticação para dois usuários: um com acesso ao nginx e outro com acesso ao Elasticsearch. Para criar arquivos de senha para esses usuários, digite os seguintes comandos:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Adicionar mais usuários

Para adicionar outro usuário ao seu arquivo de senhas, digite o seguinte comando como um usuário com privilégios `root`:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Comunicação segura com o Apache

Esta seção discute como configurar a [autenticação básica de HTTP](https://httpd.apache.org/docs/2.2/howto/auth.html). O uso conjunto da autenticação TLS e HTTP Básica impede que qualquer pessoa intercepte comunicações com o Elasticsearch, OpenSearch ou com o servidor de aplicativos.

Esta seção discute como especificar quem pode acessar o servidor Apache.

1. Use um editor de texto para adicionar o seguinte conteúdo ao host virtual seguro.

   * Apache 2.4: editar `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Se você tiver adicionado o anterior ao host virtual seguro, remova `Listen 8080` e as diretivas `<VirtualHost *:8080>` adicionadas anteriormente ao host virtual não seguro.

1. Salve as alterações, saia do editor de texto e reinicie o Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Verificar

{{$include /help/_includes/verify-secure-communication.md}}

<!-- Last updated from includes: 2024-07-18 15:50:54 -->
