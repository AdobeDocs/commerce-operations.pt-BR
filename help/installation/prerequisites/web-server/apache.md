---
title: Instalar o Apache para implantações locais
description: Saiba como instalar e configurar o Apache para implantações locais do Adobe Commerce. Ative os módulos, as substituições e as configurações ".htaccess" necessários.
feature: Install, Configuration
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# Instalar o Apache para implantações locais {#apache}

Este guia aborda a instalação do Apache para implantações locais do Adobe Commerce e a definição das configurações do Apache exigidas pelo Commerce. Ele inclui requisitos compartilhados do Apache e procedimentos específicos do sistema operacional para Ubuntu e CentOS. A Adobe recomenda seguir as instruções de configuração fornecidas neste guia para preservar a funcionalidade e a segurança do aplicativo do Commerce.

O Adobe oferece suporte às versões do Apache listadas nos [requisitos do sistema](../../system-requirements.md) da sua versão do Adobe Commerce. As versões compatíveis variam de acordo com a versão. O Apache também requer uma configuração PHP compatível. Para obter os requisitos do PHP relacionados, consulte [configurações do PHP](../php-settings.md).

Comece com a seção que corresponde ao seu ambiente:

- Se o Apache já estiver instalado, comece com [Examine os requisitos do Apache](#review-apache-requirements).
- Se precisar instalar ou atualizar o Apache no Ubuntu, acesse [Instalar ou atualizar o Apache no Ubuntu](#installing-or-upgrading-apache-on-ubuntu).
- Se precisar instalar o Apache no CentOS, acesse [Instalar o Apache no CentOS](#installing-apache-on-centos).

## Revisar requisitos do Apache

Conclua esses requisitos em qualquer servidor Apache que hospede o Adobe Commerce.

### Configurar as diretivas necessárias

Defina `AllowEncodedSlashes` na configuração do servidor (globalmente) ou nas configurações do host virtual para evitar a decodificação das barras codificadas que podem causar problemas para URLs. Por exemplo, ao recuperar produtos com uma barra na SKU por meio da API, você não deseja converter a barra. O bloco de exemplo a seguir não está completo e outras diretivas são necessárias.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### Configurar regravações e .htaccess {#apache-rewrites-and-htaccess}

Use esta seção para habilitar regravações do Apache e configurar o [arquivo `.htaccess` distribuído](https://httpd.apache.org/docs/current/howto/htaccess.html). O Adobe Commerce usa substituições de servidor e `.htaccess` para fornecer instruções no nível do diretório para o Apache.

>[!IMPORTANT]
>
>A falha em ativar essas configurações normalmente resulta na exibição de estilos na vitrine eletrônica ou no Administrador. Também pode impedir que o Apache aplique as proteções de segurança do Adobe Commerce definidas em `.htaccess`.

1. Habilite o módulo de regravação do Apache:

   ```bash
   a2enmod rewrite
   ```

1. Habilite o aplicativo para usar o arquivo de configuração `.htaccess` distribuído.

   1. No Ubuntu, edite `/etc/apache2/sites-available/000-default.conf`. Para outros layouts do Apache ou se forem necessários parâmetros adicionais, consulte a [documentação do Apache](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) e a [documentação de controle de acesso do Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

   1. Adicione ou atualize a diretiva `AllowOverride` para o diretório onde você planeja instalar o Adobe Commerce.

   Por exemplo, se você instalar o Adobe Commerce no `docroot` padrão, adicione o seguinte bloco ao `000-default.conf`:

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Se você atualizou de uma versão anterior do Apache, primeiro procure um bloco existente `<Directory "/var/www/html">` ou `<Directory "/var/www">` em `000-default.conf`. Se você instalar o Adobe Commerce em um `docroot` diferente, atualize o bloco `<Directory>` correspondente para esse caminho.

1. Reinicie o Apache para aplicar as alterações:

   ```bash
   service apache2 restart
   ```

### Instalar os módulos necessários

O Adobe Commerce requer que os seguintes módulos do Apache sejam instalados:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verificar se o Apache está instalado

Para verificar se o Apache está instalado e visualizar a versão atual, insira:

```bash
apache2 -v
```

O resultado exibe informações semelhantes às seguintes:

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Se o Apache *não* estiver instalado, consulte:
   - [Instalar ou atualizar o Apache no Ubuntu](#installing-or-upgrading-apache-on-ubuntu)
   - [Instalar o Apache no CentOS](#installing-apache-on-centos)

## Instalar ou atualizar o Apache no Ubuntu {#installing-or-upgrading-apache-on-ubuntu}

A instalação e a configuração do Apache no Ubuntu são um processo de três etapas:

1. Instale o software.
1. Habilitar regravações.
1. Especifique as diretivas `.htaccess`.

Ao configurar regravações do servidor Apache, você deve especificar o tipo de diretivas que podem ser usadas em `.htaccess`, que o aplicativo usa para especificar regras de regravação e proteções de segurança.

### Instalar o Apache no Ubuntu

1. Instale o Apache se ainda não tiver feito isso:

   ```bash
   apt-get -y install apache2
   ```

1. Verifique a instalação:

   ```bash
   apache2 -v
   ```

   Mensagens semelhantes às seguintes são exibidas para confirmar que a instalação foi bem-sucedida:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Prossiga para a próxima seção.

   >[!NOTE]
   >
   >Mesmo que o Apache seja fornecido por padrão com o Ubuntu, consulte a seção a seguir para configurá-lo.

### Atualização do Apache no Ubuntu

Se o Apache já estiver instalado e você estiver usando uma versão anterior ao `2.4`, atualize para o Apache `2.4` ou para a versão mais recente com suporte da versão do Adobe Commerce que você implantou. Consulte [requisitos de sistema](../../system-requirements.md).

1. Atualizar informações do pacote:

   ```bash
   apt-get -y update
   ```

1. Adicione um repositório que forneça uma versão do Apache compatível com seu ambiente, se necessário.

1. Instalar ou atualizar o Apache:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Se o comando `apt-get install` falhar devido a dependências não atendidas, consulte a documentação do pacote do sistema operacional ou os recursos de suporte à distribuição.

1. Verifique a instalação:

   ```bash
   apache2 -v
   ```

1. Confirme se a versão instalada corresponde à versão com suporte para sua versão do Adobe Commerce em [requisitos do sistema](../../system-requirements.md).

1. Habilitar [regravações e `.htaccess` para Ubuntu](#enable-rewrites-and-htaccess-for-ubuntu).

### Habilite regravações e .htaccess para Ubuntu

1. Abra o arquivo `/etc/apache2/sites-available/000-default.conf` para edição:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Localize o bloco que começa com:

   ```conf
   <Directory "/var/www/html">
   ```

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

1. Configure o Apache para usar o módulo `mod_rewrite`:

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

>[!IMPORTANT]
>
>A falha em ativar essas configurações normalmente resulta na exibição de estilos na vitrine eletrônica ou no Administrador. Também pode impedir que o Apache aplique as proteções de segurança do Adobe Commerce definidas em `.htaccess`.

## Instalar o Apache no CentOS {#installing-apache-on-centos}

A instalação e configuração do Apache no CentOS é um processo de três etapas:

1. Instalar o software
2. Habilitar regravações
3. Especifique as diretivas `.htaccess`.

Ao configurar regravações do servidor Apache, você deve especificar o tipo de diretivas que podem ser usadas em `.htaccess`, que o aplicativo usa para especificar regras de regravação e proteções de segurança.

### Instalação do Apache

1. Instale o Apache se ainda não tiver feito isso.

   ```bash
   yum -y install httpd
   ```

1. Verifique a instalação:

   ```bash
   httpd -v
   ```

   Mensagens semelhantes às seguintes são exibidas para confirmar que a instalação foi bem-sucedida:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Prossiga para a próxima seção.

   >[!NOTE]
   >
   >Mesmo que o Apache seja fornecido por padrão com o CentOS, consulte a seção a seguir para configurá-lo.

### Habilitar regravações e .htaccess para CentOS

1. Abra o arquivo `/etc/httpd/conf/httpd.conf` para edição:

   ```bash
   vim /etc/httpd/conf/httpd.conf
   ```

1. Localize o bloco que começa com:

   ```conf
   <Directory "/var/www/html">
   ```

1. Altere o valor de `AllowOverride` para `All`.

   Por exemplo:

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
   >Os valores anteriores para `Order` podem não funcionar em todos os casos. Para obter mais informações, consulte a [documentação do Apache](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Salve o arquivo e saia do editor de texto.

1. Para aplicar as configurações do Apache, reinicie o Apache.

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>A falha em ativar essas configurações normalmente resulta na exibição de estilos na vitrine eletrônica ou no Administrador. Também pode impedir que o Apache aplique as proteções de segurança do Adobe Commerce definidas em `.htaccess`.

## Resolvendo erros 403 (Proibido)

Se você encontrar erros 403 Proibido ao tentar acessar o site, poderá atualizar sua configuração do Apache ou a configuração do host virtual para permitir que os visitantes do site:

### Resolver erros 403 proibidos do Apache

Para permitir que visitantes do site acessem seu site, use uma das [Diretivas necessárias](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>Os valores anteriores para `Order` podem não funcionar em todos os casos. Para obter mais informações, consulte a [documentação do Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
