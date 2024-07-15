---
title: Modifique docroot para melhorar a segurança
description: Impeça o acesso não autorizado baseado em navegador ao sistema de arquivos local da Adobe Commerce.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Modifique docroot para melhorar a segurança

Em uma instalação padrão com um servidor Web Apache, o Adobe Commerce é instalado na raiz da Web padrão: `/var/www/html/magento2`.

O diretório `magento2/` contém o seguinte:

- `pub/`
- `setup/`
- `var/`

O aplicativo é fornecido de `/var/www/html/magento2/pub`. O restante do sistema de arquivos é vulnerável porque pode ser acessado de um navegador.
Definir a webroot para o diretório `pub/` impede que os visitantes do site acessem áreas confidenciais do sistema de arquivos por meio de um navegador.

Este tópico descreve como alterar o docroot do Apache em uma instância existente para servir arquivos do diretório `pub/`, que é mais seguro.

## Uma observação sobre o nginx

Se você estiver usando o arquivo [nginx](../prerequisites/web-server/nginx.md) e o arquivo [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) incluído no diretório de instalação, provavelmente já está disponibilizando arquivos do diretório `pub/`.

Quando usada no bloco de servidor que define o site, a configuração `nginx.conf.sample` substitui as configurações docroot do servidor para fornecer arquivos do diretório `pub/`. Por exemplo, consulte a última linha na seguinte configuração:

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

Para concluir este tutorial, você precisa acessar uma instalação em funcionamento em uma pilha de LAMP:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) ou OpenSearch (1.2)
- Adobe Commerce (2.4+)

>[!NOTE]
>
>Consulte os [Pré-requisitos](../prerequisites/overview.md) e o [Guia de Instalação](../overview.md) para obter mais informações.

## 1. Editar a configuração do servidor

O nome e o local do arquivo de host virtual dependem da versão do Apache que você está executando. Este exemplo mostra o nome e o local do arquivo de host virtual no Apache v2.4.

1. Faça logon no servidor de aplicativos.
1. Edite seu arquivo de host virtual:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Adicione o caminho ao diretório `pub/` à diretiva `DocumentRoot`:

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

1. Reiniciar o Apache:

   ```bash
   systemctl restart apache2
   ```

## 2. Atualize seu URL base

Se você anexou um nome de diretório ao nome de host ou endereço IP do servidor para criar a URL base quando instalou o aplicativo (por exemplo, `http://192.168.33.10/magento2`), é necessário removê-la.

>[!NOTE]
>
>Substitua `192.168.33.10` pelo nome de host do seu servidor.

1. Fazer logon no banco de dados:

   ```bash
   mysql -u <user> -p
   ```

1. Especifique o banco de dados criado quando você instalou o aplicativo:

   ```shell
   use <database-name>
   ```

1. Atualize o URL de base:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Atualize o arquivo env.php

Anexe o seguinte nó ao arquivo `env.php`.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Consulte a [referência do arquivo env.php](../../configuration/reference/config-reference-envphp.md) para obter mais informações.

## 4. Alternar modos

Os [modos de aplicativo](../../configuration/bootstrap/application-modes.md), que incluem o `production` e o `developer`, foram projetados para melhorar a segurança e facilitar o desenvolvimento. Como os nomes sugerem, você deve alternar para o modo `developer` ao estender ou personalizar o aplicativo e alternar para o modo `production` ao executar em um ambiente ativo.

Alternar entre os modos é uma etapa importante para verificar se a configuração do servidor está funcionando corretamente. Você pode alternar entre os modos usando a ferramenta da CLI:

1. Vá para o diretório de instalação.
1. Alternar para o modo `production`.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Atualize o navegador e verifique se a loja é exibida corretamente.
1. Alternar para o modo `developer`.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Atualize o navegador e verifique se a loja é exibida corretamente.

## 5. Verifique a vitrine

Acesse a loja em um navegador da Web para verificar se tudo está funcionando.

1. Abra um navegador da Web e digite o nome de host ou endereço IP do servidor na barra de endereços. Por exemplo, `http://192.168.33.10`.

   A figura a seguir mostra um exemplo de página da loja. Se for exibido da seguinte maneira, sua instalação foi um sucesso!

   ![Loja que verifica uma instalação bem-sucedida](../../assets/installation/install-success_store.png)

   Consulte a [seção de solução de problemas](https://support.magento.com/hc/en-us/articles/360032994352) se a página exibir um 404 (Não encontrado) ou se falhar ao carregar outros ativos, como imagens, CSS e JS.

1. Tente acessar um diretório de aplicativo de um navegador. Anexe o nome do diretório ao nome de host ou endereço IP do servidor na barra de endereços:

   Se aparecer a mensagem 404 ou &quot;Acesso negado&quot;, você restringiu com êxito o acesso ao sistema de arquivos.

   ![Acesso negado](../../assets/installation/access-denied.png)
