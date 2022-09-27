---
title: Configurar Varnish para comércio
description: Saiba como atualizar e gerenciar o arquivo de configuração Varnish para o aplicativo Commerce.
source-git-commit: d451ea025a6f4fc8a4a9f15ca83896a63058a3a0
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Configure o aplicativo Commerce para usar o Varnish

Para configurar o Commerce para usar o Varnish:

1. Faça logon em Admin como administrador.
1. Clique em **[!UICONTROL Stores]** > Configurações > **Configuração** > **Avançado** > **Sistema** > **Cache de página inteira**.
1. No **[!UICONTROL Caching Application]** listar, clique em **Armazenamento em cache na Varna**.
1. Insira um valor no **[!UICONTROL TTL for public content]** campo.
1. Expandir **[!UICONTROL Varnish Configuration]** e insira as seguintes informações:

   | Campo | Descrição |
   | ----- | ----------- |
   | Lista de acesso | Insira o nome do host totalmente qualificado, o endereço IP ou [Roteamento entre domínios sem classe (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) intervalo de endereços IP de notação para o qual invalidar o conteúdo. Consulte [Limpeza de cache variável](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host back-end | Insira o nome do host ou endereço IP totalmente qualificado e escute a porta do Varnish _backend_ ou _servidor de origem_; ou seja, o servidor que fornece o conteúdo Varnish acelera. Normalmente, esse é o seu servidor da Web. Consulte [Servidores Backend de cache variável](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Porta de backend | Porta de escuta do servidor de origem. |
   | Período de carência | O período de carência determina por quanto tempo a Varnish fornecerá conteúdo obsoleto se o back-end não for responsivo. O valor padrão é de 300 segundos. |

1. Clique em **Salvar configuração**.

Você também pode ativar o Varnish na linha de comando, em vez de fazer logon no Admin, usando a ferramenta C command-line interface:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportar um arquivo de configuração Varnish

Para exportar um arquivo de configuração Varnish do Administrador:

1. Clique em um dos botões de exportação para criar um `varnish.vcl` você pode usar com o Varnish.

   Por exemplo, se você tiver o Varnish 4, clique em **Exportar VCL para o Varnish 4**

   A figura a seguir mostra um exemplo:

   ![Configure o Commerce para usar o Varnish no Admin](../../assets/configuration/varnish-admin-22.png)

1. Faça o backup do `default.vcl`. Em seguida, renomeie o `varnish.vcl` arquivo para o qual você acabou de exportar `default.vcl`. Em seguida, copie o arquivo para a `/etc/varnish/` diretório.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe recomende que você abra `default.vcl` e alterar o valor de `acl purge` ao endereço IP do host Varnish. (Você pode especificar vários hosts em linhas separadas ou também pode usar a notação CIDR.)

   Por exemplo,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Se desejar personalizar as verificações de integridade do Vagrant ou a configuração do modo de carência ou do modo saint, consulte [Configuração Varnish avançada](config-varnish-advanced.md).

1. Reinicie o Varnish e o servidor da Web:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Arquivos estáticos de cache

Os arquivos estáticos não devem ser armazenados em cache por padrão, mas se você quiser armazená-los em cache, edite a seção `Static files caching` no VCL, para ter o seguinte teor:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

É necessário fazer essas alterações antes de configurar o Commerce para usar o Varnish.
