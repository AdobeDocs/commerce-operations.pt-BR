---
title: Modificar ponto para melhorar a segurança
description: Impeça o acesso não autorizado baseado em navegador ao Adobe Commerce ou ao sistema de arquivos Magento Open Source no local.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Modificar ponto para melhorar a segurança

Em uma instalação padrão com um servidor Web Apache, o Adobe Commerce e o Magento Open Source são instalados na raiz da Web padrão: `/var/www/html/magento2`.

O `magento2/` O diretório contém o seguinte:

- `pub/`
- `setup/`
- `var/`

O pedido é notificado a partir de `/var/www/html/magento2/pub`. O restante do sistema de arquivos está vulnerável, pois pode ser acessado de um navegador.
Definir o broto para a `pub/` impede que os visitantes do site acessem áreas sensíveis do sistema de arquivos a partir de um navegador.

Este tópico descreve como alterar a raiz do Apache em uma instância existente para servir arquivos do `pub/` , que é mais seguro.

## Uma observação sobre o nginx

Se estiver usando [nginx](../prerequisites/web-server/nginx.md) e [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) arquivo incluído no diretório de instalação, você provavelmente já está disponibilizando arquivos do `pub/` diretório.

Quando usado no bloco de servidor que define seu site, a variável `nginx.conf.sample` a configuração substitui as configurações de ponto do servidor para enviar arquivos do `pub/` diretório. Por exemplo, consulte a última linha na seguinte configuração:

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## Antes de começar

Para concluir este tutorial, você precisa acessar uma instalação em funcionamento em execução em um [LUZ](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) pilha:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) ou OpenSearch (1.2)
- Adobe Commerce ou Magento Open Source (2.4+)

>[!NOTE]
>
>Consulte [Pré-requisitos](../prerequisites/overview.md) e [Guia de instalação](../overview.md) para obter mais informações.

## 1. Editar a configuração do servidor

O nome e o local do arquivo de host virtual dependem da versão do Apache que você está executando. Este exemplo mostra o nome e o local do arquivo de host virtual no Apache v2.4.

1. Faça logon no servidor de aplicativos.
1. Edite o arquivo de host virtual:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Adicione o caminho ao seu `pub/` para `DocumentRoot` diretiva:

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Reinicie o Apache:

   ```bash
   systemctl restart apache2
   ```

## 2. Atualize seu URL base

Se você anexou um nome de diretório ao nome de host ou endereço IP do seu servidor para criar o URL base quando instalou o aplicativo (por exemplo, `http://192.168.33.10/magento2`), é necessário removê-lo.

>[!NOTE]
>
>Substituir `192.168.33.10` com o nome de host do seu servidor.

1. Faça logon no banco de dados:

   ```bash
   mysql -u <user> -p
   ```

1. Especifique o banco de dados que você criou ao instalar o aplicativo:

   ```shell
   use <database-name>
   ```

1. Atualize o URL base:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Atualize o arquivo env.php

Anexe o seguinte nó ao `env.php` arquivo.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Consulte a [referência env.php](../../configuration/reference/config-reference-envphp.md) para obter mais informações.

## 4. Modos de alternância

[Modos de aplicativo](../../configuration/bootstrap/application-modes.md), que incluem `production` e `developer`, são concebidas para melhorar a segurança e facilitar o desenvolvimento. Como os nomes sugerem, você deve mudar para `developer` ao estender ou personalizar o aplicativo e alternar para `production` durante a execução em um ambiente ativo.

A alternância entre modos é uma etapa importante para verificar se a configuração do servidor está funcionando corretamente. Você pode alternar entre modos usando a ferramenta CLI:

1. Vá para o diretório de instalação.
1. Mudar para `production` modo.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Atualize seu navegador e verifique se a loja é exibida corretamente.
1. Mudar para `developer` modo.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Atualize seu navegador e verifique se a loja é exibida corretamente.

## 5. Verifique a loja

Vá para o [vitrine](https://glossary.magento.com/storefront) em um navegador da Web para verificar se tudo está funcionando.

1. Abra um navegador da Web e insira o nome do host ou endereço IP do seu servidor na barra de endereços. Por exemplo, `http://192.168.33.10`.

   A figura a seguir mostra uma página de loja de exemplo. Se for exibido da seguinte maneira, sua instalação foi um sucesso!

   ![Loja que verifica uma instalação bem-sucedida](../../assets/installation/install-success_store.png)

   Consulte a [seção solução de problemas](https://support.magento.com/hc/en-us/articles/360032994352) se a página exibir um erro 404 (Não encontrado) ou não carregar outros ativos, como imagens, CSS e JS.

1. Tente acessar um diretório de aplicativo a partir de um navegador. Anexe o nome do diretório ao nome do host ou endereço IP do seu servidor na barra de endereços:

   Se vir uma mensagem 404 ou &quot;Acesso negado&quot;, você restringiu com êxito o acesso ao sistema de arquivos.

   ![Acesso negado](../../assets/installation/access-denied.png)
