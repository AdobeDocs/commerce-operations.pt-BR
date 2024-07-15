---
title: Configurar verniz para Commerce
description: Saiba como atualizar e gerenciar o arquivo de configuração do Vernish para o aplicativo da Commerce.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Configurar o aplicativo do Commerce para usar o verniz

Para configurar o Commerce para usar o verniz:

1. Faça logon no Admin como administrador.
1. Clique em **[!UICONTROL Stores]** > Configurações > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira**.
1. Na lista **[!UICONTROL Caching Application]**, clique em **Cache de Verniz**.
1. Insira um valor no campo **[!UICONTROL TTL for public content]**.
1. Expanda **[!UICONTROL Varnish Configuration]** e insira as seguintes informações:

   | Campo | Descrição |
   | ----- | ----------- |
   | Lista de acesso | Insira o nome de host totalmente qualificado, o endereço IP ou o intervalo de endereços IP da notação [Roteamento entre Domínios sem Classe (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) para o qual o conteúdo será invalidado. Consulte [Limpeza de cache de verniz](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host de back-end | Insira o nome de host ou endereço IP totalmente qualificado e a porta de escuta do _back-end_ ou do _servidor de origem_ do verniz; ou seja, o servidor que fornece o conteúdo do verniz é acelerado. Normalmente, esse é o seu servidor Web. Consulte [Servidores de back-end do cache de verniz](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Porta de back-end | Porta de escuta do servidor de origem. |
   | Período de carência | Determina por quanto tempo o Verniz fornecerá conteúdo obsoleto se o back-end não for responsivo. O valor padrão é de 300 segundos. |
   | Gerencia o tamanho dos parâmetros | Especifica o número máximo de [identificadores de layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) a serem processados no ponto de extremidade HTTP [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) para cache de página inteira. Restringir o tamanho pode melhorar a segurança e o desempenho. O padrão é 100. |

1. Clique em **Salvar configuração**.

Você também pode ativar o Verniz na linha de comando, em vez de fazer logon no Administrador, usando a ferramenta de interface de linha de comando C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportar um arquivo de configuração de verniz

Para exportar um arquivo de configuração de verniz do Admin:

1. Clique em um dos botões de exportação para criar um `varnish.vcl` que você possa usar com Verniz.

   Por exemplo, se você tiver o Verniz 4, clique em **Exportar VCL para o Verniz 4**

   A figura a seguir mostra um exemplo:

   ![Configurar o Commerce para usar o verniz no Administrador](../../assets/configuration/varnish-admin-22.png)

1. Faça backup do `default.vcl` existente. Em seguida, renomeie o arquivo `varnish.vcl` que você acabou de exportar para `default.vcl`. Em seguida, copie o arquivo para o diretório `/etc/varnish/`.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe recomendamos que você abra `default.vcl` e altere o valor de `acl purge` para o endereço IP do host Vernish. (Você pode especificar vários hosts em linhas separadas ou também pode usar a notação CIDR.)

   Por exemplo,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Se você quiser personalizar as verificações de integridade do Vagrant ou a configuração do modo de carência ou do modo de santo, consulte [Configuração avançada de verniz](config-varnish-advanced.md).

1. Reinicie o Varnish e seu servidor Web:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Armazenar arquivos estáticos em cache

Os arquivos estáticos não devem ser armazenados em cache por padrão, mas se você quiser armazená-los em cache, edite a seção `Static files caching` no VCL para ter o seguinte conteúdo:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Você deve fazer essas alterações antes de configurar o Commerce para usar o verniz.
