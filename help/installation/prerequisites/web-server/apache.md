---
title: Apache
description: Siga estas etapas para instalar e configurar o servidor da Web Apache para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---


# Apache

O Adobe Commerce é compatível com o Apache 2.4.x.

## Apache requer diretivas

1. Definir `AllowEncodedSlashes` na configuração do servidor (globalmente) ou nas configurações do host virtual para evitar a decodificação de barras codificadas que podem causar problemas para URLs. Por exemplo, ao recuperar produtos com uma barra no SKU por meio da API, você não quer que isso seja convertido. O bloco de amostra não está completo e outras diretivas são necessárias.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Regravações do Apache e htaccess

Este tópico discute como ativar as regravações do Apache 2.4 e especificar uma configuração para a variável [arquivo de configuração distribuído, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce e Magento Open Source usam regravações e `.htaccess` para fornecer instruções no nível do diretório para o Apache. As instruções a seguir também estão incluídas em todas as outras seções deste tópico.

Use esta seção para ativar as regravações do Apache 2.4 e especificar uma configuração para a variável [arquivo de configuração distribuído, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce e Magento Open Source usam regravações e `.htaccess` para fornecer instruções no nível do diretório para o Apache.

>[!NOTE]
>
>A falha ao ativar essas configurações normalmente resulta na não exibição de estilos na loja ou no Administrador.

1. Ative o módulo de reescrita do Apache:

   ```bash
   a2enmod rewrite
   ```

1. Para permitir que o aplicativo use o `.htaccess` consulte as diretrizes no arquivo de configuração do [Documentação do Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >No Apache 2.4, o arquivo de configuração de site padrão do servidor é `/etc/apache2/sites-available/000-default.conf`.

   Por exemplo, você pode adicionar o seguinte ao final de `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Às vezes, podem ser necessários parâmetros adicionais. Para obter mais informações, consulte o [Documentação do Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Se você alterou as configurações do Apache, reinicie o Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Se você atualizou de uma versão anterior do Apache, procure primeiro por `<Directory "/var/www/html">` ou `<Directory "/var/www">` em `000-default.conf`.
   >- Você deve alterar o valor de `AllowOverride` na diretiva para o diretório no qual você espera instalar o software Adobe Commerce ou Magento Open Source. Por exemplo, para instalar no docroot do servidor da Web, edite a diretiva em `<Directory /var/www>`.


>[!NOTE]
>
>A não ativação dessas configurações normalmente resulta em estilos que não são exibidos na loja ou no Administrador.

## Módulos necessários do Apache

Adobe Commerce e Magento Open Source exigem que os seguintes módulos Apache sejam instalados:

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

O resultado é exibido de forma semelhante ao seguinte:

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Se o Apache estiver *not* instalado, consulte:
   - [Instalação ou atualização do Apache no Ubuntu](#installing-apache-on-ubuntu)
   - [Instalação do Apache no CentOS](#installing-apache-on-centos)

## Instalação ou atualização do Apache no Ubuntu

As seguintes seções discutem como instalar ou atualizar o Apache:

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

   O resultado é exibido de forma semelhante ao seguinte:

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Habilitar [regrava e `.htaccess`](#apache-rewrites-and-htaccess).

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

1. Instale o Apache 2.4:

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

   Mensagens semelhantes ao seguinte devem ser exibidas:

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Habilitar [regrava e `.htaccess`](#apache-rewrites-and-htaccess).

## Instalação do Apache no CentOS

O Adobe Commerce e o Magento Open Source exigem que o Apache use regravações do servidor. Você também deve especificar o tipo de diretivas que pode ser usado em `.htaccess`, que o aplicativo usa para especificar regras de regravação.

A instalação e configuração do Apache é basicamente um processo de três etapas: instale o software, ative regravações e especifique `.htaccess` diretivas.

### Instalação do Apache

1. Instale o Apache 2.4 se ainda não tiver feito isso.

   ```bash
   yum -y install httpd
   ```

1. Verifique a instalação:

   ```bash
   httpd -v
   ```

   Mensagens semelhantes à seguinte exibição para confirmar que a instalação foi bem-sucedida:

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Continue com a próxima seção.

   >[!NOTE]
   >
   >Mesmo que o Apache 2.4 seja fornecido por padrão com o CentOS, consulte a seguinte seção para configurá-lo.

### Habilitar regravações e .htaccess para CentOS

1. Abrir `/etc/httpd/conf/httpd.conf` arquivo para edição:

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
   >Os valores anteriores para `Order` pode não funcionar em todos os casos. Para obter mais informações, consulte a documentação do Apache ([2.4.](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Salve o arquivo e saia do editor de texto.

1. Para aplicar as configurações do Apache, reinicie o Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>A falha ao ativar essas configurações normalmente resulta na não exibição de estilos na loja ou no Administrador.

### Habilitar regravações e .htaccess para Ubuntu

1. Abrir `/etc/apache2/sites-available/default` arquivo para edição:

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

1. Configure o Apache para usar o `mod_rewrite` módulo:

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

## Resolução de erros 403 (Proibido)

Se encontrar 403 erros proibidos ao tentar acessar o site, você pode atualizar a configuração do Apache ou a configuração do host virtual para permitir que os visitantes do site:

### Resolvendo erros 403 proibidos para o Apache 2.4

Para permitir que os visitantes do site acessem seu site, use uma das [Exigir diretivas](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>Os valores anteriores para `Order` pode não funcionar em todos os casos. Para obter mais informações, consulte o [Documentação do Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
