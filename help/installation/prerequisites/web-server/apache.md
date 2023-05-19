---
title: Apache
description: Siga estas etapas para instalar e configurar o Apache Web Server para instalações locais do Adobe Commerce e do Magento Open Source.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---

# Apache

O Adobe Commerce é compatível com o Apache 2.4.x.

## Diretivas necessárias do Apache

1. Definir `AllowEncodedSlashes` na configuração do servidor (globalmente) ou nas configurações do host virtual para evitar a decodificação das barras codificadas que podem causar problemas para URLs. Por exemplo, ao recuperar produtos com uma barra na SKU por meio da API, você não deseja convertê-los. O bloco de amostra não está completo e outras diretivas são necessárias.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Regravações do Apache e htaccess

Este tópico discute como habilitar substituições no Apache 2.4 e especificar uma configuração para o [arquivo de configuração distribuído, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

O Adobe Commerce e o Magento Open Source usam regravações e `.htaccess` para fornecer instruções no nível do diretório para o Apache. As instruções a seguir também estão incluídas em todas as outras seções deste tópico.

Use esta seção para habilitar substituições no Apache 2.4 e especificar uma configuração para o [arquivo de configuração distribuído, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

O Adobe Commerce e o Magento Open Source usam regravações e `.htaccess` para fornecer instruções no nível do diretório para o Apache.

>[!NOTE]
>
>A falha em ativar essas configurações normalmente resulta na exibição de estilos na vitrine eletrônica ou no Administrador.

1. Habilite o módulo de regravação do Apache:

   ```bash
   a2enmod rewrite
   ```

1. Para permitir que o aplicativo use o método distribuído `.htaccess` arquivo de configuração, consulte as diretrizes na seção [Documentação do Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >No Apache 2.4, o arquivo de configuração do site padrão do servidor é `/etc/apache2/sites-available/000-default.conf`.

   Por exemplo, você pode adicionar o seguinte ao final de `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Às vezes, podem ser necessários parâmetros adicionais. Para obter mais informações, consulte [Documentação do Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Se você alterou as configurações do Apache, reinicie o Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Se você atualizou de uma versão anterior do Apache, primeiro procure `<Directory "/var/www/html">` ou `<Directory "/var/www">` in `000-default.conf`.
   >- Você deve alterar o valor de `AllowOverride` na diretiva para o diretório no qual você espera instalar o software Adobe Commerce ou Magento Open Source. Por exemplo, para instalar no docroot do servidor Web, edite a diretiva em `<Directory /var/www>`.


>[!NOTE]
>
>A falha em ativar essas configurações normalmente resulta na não exibição de estilos na loja ou no Administrador.

## Módulos necessários do Apache

O Adobe Commerce e o Magento Open Source exigem a instalação dos seguintes módulos Apache:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verificar a versão do Apache

Para verificar a versão do Apache que você está executando no momento, insira:

```bash
apache2 -v
```

O resultado é semelhante ao seguinte:

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Se o Apache estiver *não* instalado, consulte:
   - [Instalação ou atualização do Apache no Ubuntu](#installing-apache-on-ubuntu)
   - [Instalação do Apache no CentOS](#installing-apache-on-centos)

## Instalação ou atualização do Apache no Ubuntu

As seções a seguir discutem como instalar ou atualizar o Apache:

- Instalar o Apache
- Atualize para o Apache 2.4 no Ubuntu para usar o PHP 7.4.

### Instalação do Apache no Ubuntu

Para instalar a versão padrão do Apache:

1. Instalar o Apache

   ```bash
   apt-get -y install apache2
   ```

1. Verifique a instalação.

   ```bash
   apache2 -v
   ```

   O resultado é semelhante ao seguinte:

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Ativar [substituições e `.htaccess`](#apache-rewrites-and-htaccess).

### Atualização do Apache no Ubuntu

Para atualizar para o Apache 2.4:

1. Adicione o `ppa:ondrej` repositório, que tem o Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Instalar o Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Se o comando &#39;apt-get install&#39; falhar devido a dependências não atendidas, consulte um recurso como [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Verifique a instalação.

   ```bash
   apache2 -v
   ```

   Mensagens semelhantes às seguintes devem ser exibidas:

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Ativar [substituições e `.htaccess`](#apache-rewrites-and-htaccess).

## Instalação do Apache no CentOS

O Adobe Commerce e o Magento Open Source exigem regravações de servidor do Apache. Você também deve especificar o tipo de diretivas que podem ser usadas na `.htaccess`, que o aplicativo usa para especificar regras de regravação.

A instalação e configuração do Apache é basicamente um processo de três etapas: instalar o software, habilitar as regravações e especificar `.htaccess` diretivas.

### Instalação do Apache

1. Instale o Apache 2.4 se ainda não tiver feito isso.

   ```bash
   yum -y install httpd
   ```

1. Verifique a instalação:

   ```bash
   httpd -v
   ```

   Mensagens semelhantes às seguintes são exibidas para confirmar que a instalação foi bem-sucedida:

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Prossiga para a próxima seção.

   >[!NOTE]
   >
   >Mesmo que o Apache 2.4 seja fornecido por padrão com o CentOS, consulte a seção a seguir para configurá-lo.

### Habilitar regravações e .htaccess para CentOS

1. Abertura `/etc/httpd/conf/httpd.conf` arquivo para edição:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Localize o bloco que começa com:

   ```conf
   <Directory "/var/www/html">
   ```

1. Altere o valor de `AllowOverride` para `All`.

   Por exemplo,

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >Os valores anteriores para `Order` pode não funcionar em todos os casos. Para obter mais informações, consulte a documentação do Apache ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Salve o arquivo e saia do editor de texto.

1. Para aplicar as configurações do Apache, reinicie o Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>A falha em ativar essas configurações normalmente resulta na exibição de estilos na vitrine eletrônica ou no Administrador.

### Habilite regravações e .htaccess para Ubuntu

1. Abertura `/etc/apache2/sites-available/default` arquivo para edição:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Localize o bloco que começa com:

   `<Directory "/var/www/html">`

1. Altere o valor de `AllowOverride` para `All`.

   Por exemplo:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Salve o arquivo e saia do editor de texto.

1. Configurar o Apache para usar o `mod_rewrite` módulo:

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Reinicie o Apache para aplicar as alterações:

   ```bash
   service apache2 restart
   ```

## Resolvendo erros 403 (Proibido)

Se você encontrar erros 403 Proibido ao tentar acessar o site, poderá atualizar sua configuração do Apache ou a configuração do host virtual para permitir que os visitantes do site:

### Resolução de erros 403 proibidos para o Apache 2.4

Para permitir que os visitantes do site acessem seu site, use uma das opções [Exigir diretivas](https://httpd.apache.org/docs/2.4/howto/access.html).

Por exemplo:

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>Os valores anteriores para `Order` pode não funcionar em todos os casos. Para obter mais informações, consulte [Documentação do Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
