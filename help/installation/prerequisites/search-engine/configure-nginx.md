---
title: Configurar o Nginx para seu mecanismo de pesquisa
description: Siga estas etapas para configurar um mecanismo de pesquisa com o servidor Web Nginx para instalações locais do Adobe Commerce.
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Configurar o Nginx para seu mecanismo de pesquisa

{{$include /help/_includes/web-server-communication.md}}

## Configurar um proxy

>[!NOTE]
>
>O suporte ao OpenSearch foi adicionado na versão 2.4.4. O OpenSearch é uma bifurcação de Elasticsearch compatível. Consulte [Migrar o Elasticsearch para o OpenSearch](../../../upgrade/prepare/opensearch-migration.md) para obter mais informações.

Esta seção discute como configurar o nginx como um *inseguro* para que o Adobe Commerce possa usar um mecanismo de pesquisa em execução neste servidor. Esta seção não discute a configuração da autenticação básica de HTTP; isso é discutido em [Comunicação segura com nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>O motivo pelo qual o proxy não é seguro neste exemplo é que é mais fácil de configurar e verificar. Você pode usar o TLS com esse proxy se desejar; para isso, adicione as informações do proxy à configuração de bloqueio do servidor seguro.

### Especifique arquivos de configuração adicionais na sua configuração global

Certifique-se de que seu `/etc/nginx/nginx.conf` contém a seguinte linha para carregar os outros arquivos de configuração discutidos nas seguintes seções:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Configurar o nginx como proxy

Esta seção discute como especificar quem pode acessar o servidor nginx.

1. Usar um editor de texto para criar um arquivo `/etc/nginx/conf.d/magento_es_auth.conf` com o seguinte conteúdo:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Reiniciar o nginx:

   ```bash
   service nginx restart
   ```

1. Verifique se o proxy funciona digitando o seguinte comando:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Por exemplo, se seu proxy usar a porta 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Mensagens semelhantes ao seguinte são exibidas para indicar sucesso:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Comunicação segura com nginx

Esta seção discute como configurar [Autenticação básica de HTTP](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) com seu proxy seguro. O uso conjunto da autenticação TLS e HTTP Básica impede que qualquer pessoa intercepte a comunicação com o Elasticsearch ou OpenSearch ou com o servidor de aplicativos.

Como o nginx suporta nativamente a autenticação básica HTTP, recomendamos fazê-lo, por exemplo, [Autenticação Digest](https://www.nginx.com/resources/wiki/modules/auth_digest/), que não é recomendado na produção.

Recursos adicionais:

* [Como configurar a autenticação de senha com o Nginx no Ubuntu 14.04 (Digital Ocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Autenticação HTTP básica com Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Exemplo de configurações Nginx para Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Consulte as seguintes seções para obter mais informações:

* [Criar senhas](#create-a-password)
* [Configurar acesso ao nginx](#set-up-access-to-nginx)
* [Configurar um contexto restrito para o mecanismo de pesquisa](#set-up-a-restricted-context-for-the-search-engine)
* [Verificar se a comunicação é segura](#secure-communication-with-nginx)

### Criar uma senha

Recomendamos que você use o Apache `htpasswd` comando para codificar senhas para um usuário com acesso ao Elasticsearch ou OpenSearch (denominado `magento_elasticsearch` neste exemplo).

Para criar uma senha:

1. Digite o seguinte comando para determinar se `htpasswd` já está instalado:

   ```bash
   which htpasswd
   ```

   Se um caminho for exibido, ele será instalado; se o comando não retornar nenhuma saída, `htpasswd` não está instalado.

1. Se necessário, instale `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Criar um `/etc/nginx/passwd` diretório para armazenar senhas:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Por motivos de segurança, `<filename>` deve ser oculto; ou seja, deve começar com um ponto.

1. *(Opcional).* Para adicionar outro usuário ao seu arquivo de senhas, digite o mesmo comando sem a `-c` Opção (criar):

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Verifique se o conteúdo de `/etc/nginx/passwd` está correto.

### Configurar acesso ao nginx

Esta seção discute como especificar quem pode acessar o servidor nginx.

>[!WARNING]
>
>O exemplo mostrado é para um *inseguro* proxy. Para usar um proxy seguro, adicione o seguinte conteúdo (exceto a porta de escuta) ao bloco do servidor seguro.

Use um editor de texto para modificar `/etc/nginx/conf.d/magento_es_auth.conf` (não seguro) ou o bloco do servidor seguro com o seguinte conteúdo:

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>A porta de escuta do mecanismo de pesquisa mostrada no exemplo anterior é apenas para exemplos. Por motivos de segurança, recomendamos que você use uma porta de escuta não padrão.

### Configurar um contexto restrito para o mecanismo de pesquisa

Esta seção discute como especificar quem pode acessar o servidor do mecanismo de pesquisa.

1. Digite o seguinte comando para criar um diretório para armazenar a configuração de autenticação:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Usar um editor de texto para criar um arquivo `/etc/nginx/auth/magento_elasticsearch.conf` com o seguinte conteúdo:

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. Se você configurar um proxy seguro, exclua `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Reinicie o nginx e continue com a próxima seção:

   ```bash
   service nginx restart
   ```

#### Verificar

{{$include /help/_includes/verify-secure-communication.md}}
