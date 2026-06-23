---
title: Configurar nginx para cache de verniz
description: Saiba como configurar seu servidor Web para funcionar com o armazenamento em cache do Varnish para o Adobe Commerce. Conheça os requisitos de configuração e configuração de porta.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# Configurar nginx para cache de vernish {#configure-web-server-for-varnish-caching}

Quando o verniz é usado como cache de página inteira na frente do Adobe Commerce, o verniz normalmente escuta a porta HTTP pública e encaminha solicitações para o nginx em uma porta de back-end não padrão, como a 8080. Atualize a configuração do site nginx para que seu servidor de origem Commerce escute na porta de back-end que o Vernish usará.

{{varnish-config-cloud}}

As seções a seguir usam a porta 8080 como exemplo.

**Alterar a porta de escuta nginx do servidor de origem do Commerce**:

1. Abra a configuração do site nginx para seu servidor de origem Adobe Commerce em um editor de texto.

O local depende do sistema operacional e do layout nginx. Por exemplo, o Ubuntu geralmente usa um arquivo em `/etc/nginx/sites-available/`.

1. No bloco `server` do site do Commerce, altere a diretiva `listen` da porta HTTP pública para a porta de back-end que o verniz usará para alcançar nginx.

   Por exemplo, alterar

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   para:

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. Salve o arquivo.

1. Verifique a configuração do nginx:

   ```shell
   nginx -t
   ```

1. Reiniciar o nginx:

   ```shell
   systemctl restart nginx
   ```

## Modificar a configuração do sistema Vernish

Depois de atualizar o nginx para escutar na porta de backend, configure o Varnish para encaminhar solicitações para esse host e porta. Por exemplo:

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### Modificar o VCL padrão

Esta seção discute como fornecer configuração mínima para que o Verniz retorne cabeçalhos de resposta HTTP. Isso permite verificar se o Verniz funciona antes de configurar o aplicativo [!DNL Commerce] para usar o Verniz.

Para configurar minimamente o Verniz:

1. Fazer backup de `default.vcl`:

   ```shell
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Abra `/etc/varnish/default.vcl` em um editor de texto.
1. Localize a seguinte estrofe:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Substitua o valor de `.host` pelo nome de host ou endereço IP totalmente qualificado e a porta de escuta do _back-end_ ou do _servidor de origem_ do Verniz; ou seja, o servidor que fornece o conteúdo O verniz será acelerado.

   Normalmente, esse é o seu servidor Web. Consulte [Servidores backend](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) no _guia de verniz_.

1. Substitua o valor de `.port` pela porta de escuta do servidor Web (8080 neste exemplo).

   Exemplo: nginx está instalado no host 192.0.2.55 e escutando na porta 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Se o Varnish e o nginx estiverem em execução no mesmo host, a Adobe recomenda o uso de um endereço IP ou nome de host, em vez de `localhost`.

1. Salve as alterações em `default.vcl` e saia do editor de texto.

1. Reiniciar o verniz:

   ```shell
   service varnish restart
   ```

Se o Verniz não for iniciado, tente executá-lo a partir da linha de comando da seguinte maneira:

```shell
varnishd -d -f /etc/varnish/default.vcl
```

Isso deve exibir mensagens de erro.


>[!INFO]
>
>Se o Varnish não for iniciado como um serviço, você deverá configurar as regras do SELinux para permitir que ele seja executado.

## Verificar se o verniz está funcionando

As seções a seguir discutem como verificar se o Verniz está funcionando, mas _sem_ configurar o Commerce para usá-lo. Você deve tentar isso antes de configurar o Commerce.

Execute as tarefas discutidas nas seguintes seções na ordem mostrada:

- [Iniciar verniz](#start-varnish)
- [`netstat`](#netstat)

### Iniciar verniz

Digite: `service varnish start`

Se o Varnish falhar ao ser iniciado como um serviço, inicie-o a partir da linha de comando da seguinte maneira:

1. Inicie a CLI do Vernish:

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Inicie o processo filho de Verniz:

   Quando solicitado, insira `start`

   As mensagens a seguir são exibidas para confirmar um início bem-sucedido:

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Faça logon no servidor Vernish e insira o seguinte comando:

```shell
netstat -tulpn
```

Procure a seguinte saída em particular:

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

O anterior mostra o Varnish em execução na porta 80 e nginx em execução na porta 8080.

Se você não vir a saída para `varnishd`, verifique se o Verniz está em execução.

Consulte [`netstat` opções](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Instale o software da Commerce

Instale o software Commerce, se ainda não tiver feito isso. Quando solicitado a fornecer um URL base, use o host verniz e a porta 80 (para verniz) porque verniz recebe todas as solicitações HTTP recebidas.

Possível erro ao instalar o Commerce:

```text
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Se você receber esse erro, edite `default.vcl` e adicione um tempo limite à estrofe `backend` da seguinte maneira:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verificar cabeçalhos de resposta HTTP

Agora é possível verificar se o Verniz está oferecendo páginas observando os cabeçalhos de resposta do HTML retornados de qualquer página.

Antes de visualizar os cabeçalhos, é necessário definir o Commerce para o modo de desenvolvedor. Há várias maneiras de fazer isso, a mais simples delas é modificar `.htaccess` na raiz do aplicativo Commerce. Você também pode usar o comando [`magento deploy:mode:set`](../cli/set-mode.md).

### Definir Commerce para modo de desenvolvedor

Para definir o Commerce para o modo de desenvolvedor, use o comando [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode).

### Veja o log de verniz

Verifique se o Verniz está em execução e digite o seguinte comando no servidor Verniz:

```shell
varnishlog
```

Em um navegador da Web, vá para qualquer página do Commerce.

Uma longa lista de cabeçalhos de resposta é exibida na janela da tela de comandos. Procure cabeçalhos como os seguintes:

```text
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

Se cabeçalhos como estes _não_ forem exibidos, pare de Verniz, verifique seu `default.vcl` e tente novamente.

### Observar cabeçalhos de resposta do HTML

Há várias maneiras de visualizar cabeçalhos de resposta, incluindo o uso de um plug-in de navegador ou um inspetor de navegador.

O exemplo a seguir usa `curl`. Você pode inserir esse comando em qualquer máquina que possa acessar o servidor do Commerce usando HTTP.

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

Por exemplo,

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Procure cabeçalhos como os seguintes:

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
