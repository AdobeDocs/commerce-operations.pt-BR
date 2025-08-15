---
title: Opções de modo de manutenção para atualização
description: Crie uma página de modo de manutenção personalizada que seus clientes verão na loja da Adobe Commerce enquanto você executa uma atualização.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Opções de modo de manutenção para atualização

Este tópico discute como criar uma página de manutenção personalizada para exibir aos usuários enquanto seu aplicativo do Magento está sendo atualizado. A criação de uma página personalizada é opcional, mas recomendada, pois seu site está acessível durante parte da atualização.

Criar uma página personalizada para redirecionar usuários impede qualquer acesso ao site e também informa aos usuários que o site está em manutenção.

>[!NOTE]
>
>Você deve executar as tarefas desta seção como um usuário com privilégios de `root`. Páginas de manutenção personalizadas não podem ser definidas enquanto estiverem no modo de desenvolvedor.

## Criar a página de manutenção personalizada

Para criar uma página de manutenção e redirecioná-la, primeiro crie uma página de manutenção chamada:

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

Adicione o seguinte conteúdo:

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Página de manutenção personalizada do Apache

Esta seção discute como criar uma página de manutenção personalizada e como redirecionar o tráfego para ela.

O exemplo nesta seção mostra como modificar os seguintes arquivos, o que é uma maneira de configurar sua página de manutenção:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

Para redirecionar o tráfego para uma página de manutenção personalizada:

1. Atualize sua configuração do Apache para fazer o seguinte:

   - Redirecionar todo o tráfego para a página de manutenção
   - Incluir na lista de permissões determinados IPs para que um administrador possa atualizar o software Magento.

   Incluir na lista de permissões O exemplo a seguir apresenta 192.0.2.110.

   Adicione o seguinte ao final do arquivo de configuração do Apache:

   ```
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Reiniciar o Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. Digite o seguinte comando:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [Atualize seu sistema](../implementation/perform-upgrade.md).
1. Teste o site para verificar se ele funciona corretamente.
1. Após a atualização, exclua `maintenance.enable`.

## Página de manutenção personalizada para nginx

Esta seção discute como criar uma página de manutenção personalizada e como redirecionar o tráfego para ela.

Para redirecionar o tráfego para uma página de manutenção personalizada:

1. Use um editor de texto para abrir o arquivo de configuração nginx que contém o bloco do servidor.
1. Adicionar o seguinte ao bloco de servidor (`server` é mostrado apenas para maior clareza; não adicione um segundo bloco de servidor).

   Incluir na lista de permissões O seguinte capítulo exibe o endereço IP 192.0.2.110 e 192.0.2.115 em um sistema em que o Magento está instalado em `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Digite o seguinte comando:

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Recarregue a configuração do nginx:

   ```bash
   service nginx reload
   ```

1. [Atualize seu sistema](../implementation/perform-upgrade.md).
1. Teste o site para verificar se ele funciona corretamente.
1. Após a atualização, exclua ou renomeie `maintenance.enable`
1. Recarregue a configuração do nginx:

   ```bash
   service nginx reload
   ```
