---
title: Configurar verniz para o Commerce
description: Saiba como atualizar e gerenciar o arquivo de configuração de verniz para o aplicativo Commerce.
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Configurar o aplicativo do Commerce para usar o verniz

Para configurar o Commerce para usar o verniz:

1. Faça logon no Admin como administrador.
1. Clique em **[!UICONTROL Stores]** > Configurações > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira**.
1. No **[!UICONTROL Caching Application]** clique em **Armazenamento em cache de verniz**.
1. Insira um valor no campo **[!UICONTROL TTL for public content]** campo.
1. Expandir **[!UICONTROL Varnish Configuration]** e insira as seguintes informações:

   | Campo | Descrição |
   | ----- | ----------- |
   | Lista de acesso | Insira o nome do host, endereço IP ou [Roteamento interdomínio sem classe (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) intervalo de endereços IP da notação para o qual o conteúdo será invalidado. Consulte [Limpeza do cache de verniz](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host de back-end | Insira o nome do host ou endereço IP totalmente qualificado e a porta de escuta do Verniz _back-end_ ou _servidor de origem_; ou seja, o servidor que fornece o conteúdo Verniz acelera. Normalmente, esse é o seu servidor Web. Consulte [Servidores de back-end com cache verniz](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Porta de back-end | Porta de escuta do servidor de origem. |
   | Período de carência | O período de carência determina por quanto tempo o verniz fornecerá conteúdo obsoleto se o back-end não for responsivo. O valor padrão é de 300 segundos. |

1. Clique em **Salvar configuração**.

Você também pode ativar o Verniz na linha de comando, em vez de fazer logon no Administrador, usando a ferramenta de interface de linha de comando C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportar um arquivo de configuração de verniz

Para exportar um arquivo de configuração de verniz do Admin:

1. Clique em um dos botões de exportação para `varnish.vcl` você pode usar com verniz.

   Por exemplo, se você tiver Verniz 4, clique em **Exportar VCL para Verniz 4**

   A figura a seguir mostra um exemplo:

   ![Configurar o Commerce para usar o verniz no Admin](../../assets/configuration/varnish-admin-22.png)

1. Fazer backup do seu existente `default.vcl`. Em seguida, renomeie o `varnish.vcl` arquivo para o qual você acabou de exportar `default.vcl`. Em seguida, copie o arquivo para o `/etc/varnish/` diretório.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe recomenda abrir `default.vcl` e altere o valor de `acl purge` ao endereço IP do host verniz. (Você pode especificar vários hosts em linhas separadas ou também pode usar a notação CIDR.)

   Por exemplo,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Se você quiser personalizar as verificações de integridade do Vagrant ou a configuração do modo de carência ou do modo santo, consulte [Configuração avançada de verniz](config-varnish-advanced.md).

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
