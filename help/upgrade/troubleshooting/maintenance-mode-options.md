---
title: Opções de modo de manutenção para atualização
description: Crie uma página de modo de manutenção personalizada que seus clientes verão em sua loja Adobe Commerce ou Magento Open Source enquanto você executa uma atualização.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Opções de modo de manutenção para atualização

Este tópico discute como criar uma página de manutenção personalizada para exibir aos usuários enquanto seu aplicativo Magento está sendo atualizado. A criação de uma página personalizada é opcional, mas recomendada, pois seu site está acessível durante parte da atualização.

Criar uma página personalizada para redirecionar usuários impede qualquer acesso ao site e também informa aos usuários que o site está em manutenção.

>[!NOTE]
>
>Você deve executar as tarefas desta seção como um usuário com `root` privilégios. Páginas de manutenção personalizadas não podem ser definidas enquanto estiverem no modo de desenvolvedor.

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
   - executar a Inclui na lista de permissões de determinados IPs para que um administrador possa atualizar o software Magento.

   O exemplo a seguir inclui na lista de permissões 192.0.2.110.

   Adicione o seguinte ao final do arquivo de configuração do Apache:

   ```terminal
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

1. [Atualizar o sistema](../implementation/perform-upgrade.md).
1. Teste o site para verificar se ele funciona corretamente.
1. Depois que a atualização estiver concluída, exclua `maintenance.enable`.

## Página de manutenção personalizada para nginx

Esta seção discute como criar uma página de manutenção personalizada e como redirecionar o tráfego para ela.

Para redirecionar o tráfego para uma página de manutenção personalizada:

1. Use um editor de texto para abrir o arquivo de configuração nginx que contém o bloco do servidor.
1. Adicione o seguinte ao bloco do servidor (`server` é exibido apenas para maior clareza; não adicione um segundo bloco de servidor).

   Lista de permissões A seguinte mensagem exibe o endereço IP 192.0.2.110 e 192.0.2.115 em um sistema no qual o Magento está instalado `/var/www/html/magento2`:

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

1. [Atualizar o sistema](../implementation/perform-upgrade.md).
1. Teste o site para verificar se ele funciona corretamente.
1. Depois que a atualização estiver concluída, exclua ou renomeie `maintenance.enable`
1. Recarregue a configuração do nginx:

   ```bash
   service nginx reload
   ```
