---
title: Configurar servidor da Web
description: Saiba como configurar o servidor da Web para funcionar com a Varnish.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# Configurar o servidor da Web

Configure seu servidor da Web para escutar em uma porta diferente da padrão 80, pois o Varnish responde diretamente às solicitações HTTP recebidas, não ao servidor da Web.

As seções a seguir usam a porta 8080 como exemplo.

**Para alterar a porta de escuta do Apache 2.4**:

1. Abrir `/etc/httpd/conf/httpd.conf` em um editor de texto.
1. Localize a variável `Listen` diretiva.
1. Altere o valor da porta de escuta para `8080`. (Você pode usar qualquer porta de escuta disponível.)
1. Salve as alterações em `httpd.conf` e saia do editor de texto.

## Modificar a configuração do sistema Varnish

Para modificar a configuração do sistema Varnish:

1. Como um usuário com `root` , abra o arquivo de configuração do Vanish em um editor de texto:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Defina a porta de escuta Varnish como 80:

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

1. Salve as alterações no arquivo de configuração Varnish e saia do editor de texto.

### Modificar a VCL padrão

Esta seção discute como fornecer configuração mínima para que o Varnish retorne cabeçalhos de resposta HTTP. Isso permite verificar se o Varnish funciona antes de configurar a variável [!DNL Commerce] pedido de utilização do Varnish.

Para configurar minimamente o Varnish:

1. Fazer backup `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Abrir `/etc/varnish/default.vcl` em um editor de texto.
1. Localize o seguinte stanza:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Substitua o valor de `.host` com o nome de host ou endereço IP totalmente qualificado e a porta de escuta do Varnish _backend_ ou _servidor de origem_; ou seja, o servidor que fornece o conteúdo em Varnish será acelerado.

   Normalmente, esse é o seu servidor da Web. Consulte [Servidores de backend](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) no _Guia da Varna_.

1. Substitua o valor de `.port` com a porta de escuta do servidor da web (8080 neste exemplo).

   Exemplo: O Apache é instalado no host 192.0.2.55 e o Apache está escutando na porta 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Se Varnish e Apache estiverem em execução no mesmo host, o Adobe recomenda que você use um endereço IP ou nome de host e não `localhost`.

1. Salve as alterações em `default.vcl` e saia do editor de texto.

1. Reinicie o Varnish:

   ```bash
   service varnish restart
   ```

Se o Varnish não iniciar, tente executá-lo a partir da linha de comando da seguinte maneira:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Isso deve exibir mensagens de erro.


>[!INFO]
>
>Se a Varnish não iniciar como um serviço, você deverá configurar as regras do SELinux para permitir sua execução.

## Verificar se o Varnish está funcionando

As seções a seguir discutem como você pode verificar se a Varnish está funcionando, mas _without_ configurando o Commerce para usá-lo. Tente isso antes de configurar o Commerce.

Execute as tarefas discutidas nas seções a seguir na ordem mostrada:

- [Iniciar Verniz](#start-varnish)
- [&quot;netstat&quot;](#netstat)

### Iniciar Verniz

Informe: `service varnish start`

Se a Varnish não iniciar como um serviço, inicie-a a partir da linha de comando da seguinte maneira:

1. Inicie a CLI Varna:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Inicie o processo filho Varnish:

   Quando solicitado, insira `start`

   As mensagens a seguir são exibidas para confirmar um início bem-sucedido:

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Faça logon no servidor Varnish e insira o seguinte comando:

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

O anterior mostra o Varnish sendo executado na porta 80 e o Apache em execução na porta 8080.

Se você não vir saída para `varnishd`, certifique-se de que o Varnish esteja em execução.

Consulte [`netstat` opções](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Instalar o software Commerce

Instale o software Commerce, se ainda não o tiver feito. Quando solicitado para um URL de base, use o host Varnish e a porta 80 (para Varnish), pois Varnish recebe todas as solicitações HTTP recebidas.

Possível erro ao instalar o Commerce:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Se você tiver esse erro, edite `default.vcl` e adicione um tempo limite à `backend` stanza:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verificar cabeçalhos de resposta HTTP

Agora você pode verificar se a Varnish está exibindo páginas observando [HTML](https://glossary.magento.com/html) cabeçalhos de resposta retornados de qualquer página.

Antes de poder ver os cabeçalhos, você deve definir o Commerce para o modo desenvolvedor. Há várias maneiras de fazer isso, a mais simples delas é modificar `.htaccess` na raiz do aplicativo Commerce. Também é possível usar a variável [`magento deploy:mode:set`](../cli/set-mode.md) comando.

### Definir comércio para o modo de desenvolvedor

Para definir o Commerce para o modo de desenvolvedor, use o [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) comando.

### Veja o log Varnish

Certifique-se de que Varnish esteja em execução e insira o seguinte comando no servidor Varnish:

```bash
varnishlog
```

Em um navegador da Web, acesse qualquer página de Comércio.

Uma longa lista de cabeçalhos de resposta é exibida na janela de prompt de comando. Procure cabeçalhos como os seguintes:

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

Se cabeçalhos como esses _not_ exibir, parar Varnish, verifique seu `default.vcl`e tente novamente.

### Examine os cabeçalhos de resposta do HTML

Há várias maneiras de examinar os cabeçalhos de resposta, incluindo o uso de um navegador [plug-in](https://glossary.magento.com/plug-in) ou um inspetor de navegador.

O exemplo a seguir usa `curl`. Você pode inserir este comando em qualquer máquina que possa acessar o servidor do Commerce usando HTTP.

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
