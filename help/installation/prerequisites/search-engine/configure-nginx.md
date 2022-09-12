---
title: Configurar o Nginx para o mecanismo de pesquisa
description: Siga estas etapas para configurar um mecanismo de pesquisa com o servidor da Web Nginx para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: a0f2c6480edcda5540ca83835580d18f401de72f
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# Configurar o Nginx para o mecanismo de pesquisa

{{$include /help/_includes/web-server-communication.md}}

## Configurar um proxy

>[!NOTE]
>
>O suporte ao OpenSearch foi adicionado em 2.4.4. O OpenSearch é uma bifurcação compatível do Elasticsearch. Todas as instruções para configurar o Elasticsearch 7 se aplicam ao OpenSearch. Consulte [Migrar Elasticsearch para OpenSearch](../../../upgrade/prepare/opensearch-migration.md) para obter mais informações.

Esta seção discute como configurar o nginx como um *inseguro* para que o Adobe Commerce ou o Magento Open Source possa usar um mecanismo de pesquisa em execução neste servidor. Esta seção não discute a configuração da autenticação HTTP Basic; que é discutido no [Comunicação segura com o nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>O motivo pelo qual o proxy não está protegido neste exemplo é que é mais fácil configurar e verificar. Você pode usar o TLS com esse proxy, se desejar; para fazer isso, adicione as informações de proxy à configuração de bloco de servidor seguro.

### Especificar arquivos de configuração adicionais na sua configuração global

Certifique-se de que seu `/etc/nginx/nginx.conf` contém a linha a seguir para carregar os outros arquivos de configuração discutidos nas seguintes seções:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Configurar o nó como proxy

Esta seção discute como especificar quem pode acessar a variável [nginx](https://glossary.magento.com/nginx) servidor.

1. Usar um editor de texto para criar um arquivo `/etc/nginx/conf.d/magento_es_auth.conf` com o seguinte conteúdo:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Reinicie o nginx:

   ```bash
   service nginx restart
   ```

1. Verifique se o proxy funciona inserindo o seguinte comando:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Por exemplo, se seu proxy usa a porta 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Mensagens semelhantes ao seguinte são exibidas para indicar o sucesso:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Comunicação segura com o nginx

Esta seção discute como configurar [Autenticação HTTP Basic](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) com seu proxy seguro. O uso conjunto da autenticação TLS e HTTP Basic impede qualquer pessoa de interceptar a comunicação com o Elasticsearch ou com seu servidor Adobe Commerce ou Magento Open Source.

Como o nginx suporta nativamente a autenticação HTTP Basic, a recomendamos, por exemplo, [Autenticação Digest](https://www.nginx.com/resources/wiki/modules/auth_digest/), que não é recomendado na produção.

Recursos adicionais:

* [Como configurar a autenticação de senha com o Nginx no Ubuntu 14.04 (Oceano digital)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Autenticação HTTP básica com Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Exemplo de configurações de próximo trimestre para Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Consulte as seguintes seções para obter mais informações:

* [Criar senhas](#create-a-password)
* [Configurar acesso ao nginx](#set-up-access-to-nginx)
* [Configurar um contexto restrito para o mecanismo de pesquisa](#set-up-a-restricted-context-for-the-search-engine)
* [Verifique se a comunicação está segura](#secure-communication-with-nginx)

### Criar uma senha

Recomendamos que você use o Apache `htpasswd` comando para codificar senhas para um usuário com acesso ao Elasticsearch ou OpenSearch (nomeado `magento_elasticsearch` neste exemplo).

Para criar uma senha:

1. Digite o seguinte comando para determinar se `htpasswd` já está instalado:

   ```bash
   which htpasswd
   ```

   Se um caminho for exibido, ele será instalado; se o comando não retornar nenhuma saída, `htpasswd` não estiver instalado.

1. Se necessário, instale `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Crie um `/etc/nginx/passwd` diretório para armazenar senhas:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Por razões de segurança, `<filename>` deve estar oculto; ou seja, deve começar com um período.

1. *(Opcional).* Para adicionar outro usuário ao arquivo de senha, digite o mesmo comando sem a `-c` opção (criar):

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Verifique se o conteúdo de `/etc/nginx/passwd` está correto.

### Configurar acesso ao nginx

Esta seção discute como especificar quem pode acessar o servidor de nó.

>[!WARNING]
>
>O exemplo mostrado é para um *inseguro* proxy. Para usar um proxy seguro, adicione o seguinte conteúdo (exceto a porta de escuta) ao bloco de servidor seguro.

Use um editor de texto para modificar `/etc/nginx/conf.d/magento_es_auth.conf` (não seguro) ou seu bloco de servidor seguro com o seguinte conteúdo:

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
>A porta de escuta do mecanismo de pesquisa mostrada no exemplo anterior são apenas exemplos. Por motivos de segurança, recomendamos que você use uma porta de escuta não padrão.

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
