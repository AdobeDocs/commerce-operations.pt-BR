---
title: Configurar servidor Web
description: Saiba como configurar o servidor Web para funcionar com o Verniz.
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Configurar o servidor Web

Configure seu servidor Web para escutar em uma porta diferente da porta padrão 80, pois o Varnish responde diretamente às solicitações HTTP recebidas, não ao servidor Web.

As seções a seguir usam a porta 8080 como exemplo.

**Para alterar a porta de escuta do Apache 2.4**:

1. Abertura `/etc/httpd/conf/httpd.conf` em um editor de texto.
1. Localize o `Listen` diretiva.
1. Altere o valor da porta de escuta para `8080`. (Você pode usar qualquer porta de escuta disponível.)
1. Salvar as alterações em `httpd.conf` e saia do editor de texto.

## Modificar a configuração do sistema Vernish

Para modificar a configuração do sistema Vernish:

1. Como usuário com `root` abra o arquivo de configuração do Vanish em um editor de texto:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Defina a porta de escuta do verniz como 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Para o Varnish 4.x, verifique se DAEMON_OPTS contém a porta de escuta correta para o `-a` (mesmo se VARNISH_LISTEN_PORT estiver definido com o valor correto):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Salve as alterações no arquivo de configuração de verniz e saia do editor de texto.

### Modificar o VCL padrão

Esta seção discute como fornecer configuração mínima para que o Verniz retorne cabeçalhos de resposta HTTP. Isso permite verificar se o Verniz funciona antes de configurar o [!DNL Commerce] aplicativo para usar o verniz.

Para configurar minimamente o Verniz:

1. Fazer backup `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Abertura `/etc/varnish/default.vcl` em um editor de texto.
1. Localize a seguinte estrofe:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Substitua o valor de `.host` com o nome do host ou endereço IP totalmente qualificado e a porta de escuta do Verniz _back-end_ ou _servidor de origem_; ou seja, o servidor que fornece o conteúdo Verniz será acelerado.

   Normalmente, esse é o seu servidor Web. Consulte [Servidores de back-end](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) no _Guia de verniz_.

1. Substitua o valor de `.port` com a porta de escuta do servidor Web (8080 neste exemplo).

   Exemplo: o Apache está instalado no host 192.0.2.55 e o Apache está escutando na porta 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Se o Varnish e o Apache estiverem em execução no mesmo host, a Adobe recomenda o uso de um endereço IP ou nome de host, em vez de `localhost`.

1. Salvar as alterações em `default.vcl` e saia do editor de texto.

1. Reiniciar o verniz:

   ```bash
   service varnish restart
   ```

Se o Verniz não for iniciado, tente executá-lo a partir da linha de comando da seguinte maneira:

```bash
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
- [&quot;netstat&quot;](#netstat)

### Iniciar verniz

Digite: `service varnish start`

Se o Varnish falhar ao ser iniciado como um serviço, inicie-o a partir da linha de comando da seguinte maneira:

1. Inicie a CLI do Vernish:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Inicie o processo filho de Verniz:

   Quando solicitado, insira `start`

   As mensagens a seguir são exibidas para confirmar um início bem-sucedido:

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Faça logon no servidor Vernish e insira o seguinte comando:

```bash
netstat -tulpn
```

Procure a seguinte saída em particular:

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

O anterior mostra o Varnish em execução na porta 80 e o Apache em execução na porta 8080.

Se você não vir saída para `varnishd`, verifique se o Verniz está em execução.

Consulte [`netstat` opções](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Instalar o software Commerce

Instale o software Commerce, se ainda não tiver instalado. Quando solicitado a fornecer um URL base, use o host verniz e a porta 80 (para verniz) porque verniz recebe todas as solicitações HTTP recebidas.

Possível erro ao instalar o Commerce:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Se você receber esse erro, edite `default.vcl` e adicione um tempo limite à variável `backend` estrofe do seguinte modo:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verificar cabeçalhos de resposta HTTP

Agora é possível verificar se o Verniz está servindo páginas observando os cabeçalhos de resposta de HTML retornados de qualquer página.

Antes de visualizar os cabeçalhos, é necessário definir o Commerce para o modo de desenvolvedor. Há várias maneiras de fazê-lo, a mais simples delas é modificar `.htaccess` na raiz do aplicativo Commerce. Você também pode usar a variável [`magento deploy:mode:set`](../cli/set-mode.md) comando.

### Definir comércio para modo de desenvolvedor

Para definir o Commerce para o modo de desenvolvedor, use o [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) comando.

### Veja o log de verniz

Verifique se o Verniz está em execução e digite o seguinte comando no servidor Verniz:

```bash
varnishlog
```

Em um navegador da Web, vá para qualquer página do Commerce.

Uma longa lista de cabeçalhos de resposta é exibida na janela da tela de comandos. Procure cabeçalhos como os seguintes:

```terminal
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

Se cabeçalhos como esses _não_ exibir, parar Verniz, verificar o `default.vcl`e tente novamente.

### Observar cabeçalhos de resposta de HTML

Há várias maneiras de visualizar cabeçalhos de resposta, incluindo o uso de um plug-in de navegador ou um inspetor de navegador.

O exemplo a seguir usa `curl`. Você pode inserir esse comando em qualquer máquina que possa acessar o servidor do Commerce usando HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Por exemplo,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Procure cabeçalhos como os seguintes:

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
