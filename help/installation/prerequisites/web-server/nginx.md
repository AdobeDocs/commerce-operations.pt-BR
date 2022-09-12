---
title: Nginx
description: Siga estas etapas para instalar e configurar o servidor da Web Nginx para instalações locais do Adobe Commerce e Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---


# Nginx

O Adobe Commerce é compatível com o ngx 1.18 (ou a variável [versão principal mais recente](https://nginx.org/en/linux_packages.html#mainline)). Você também deve instalar a versão mais recente de `php-fpm`.

As instruções de instalação variam de acordo com o sistema operacional que você está usando. Consulte [PHP](../php-settings.md) para obter informações.

## Ubuntu

A seção a seguir descreve como instalar o Adobe Commerce e o Magento Open Source 2.x no Ubuntu usando nginx, PHP e MySQL.

### Instalar o nginx

```bash
sudo apt -y install nginx
```

Você também pode [criar nginx a partir da origem](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Após concluir as seções a seguir e instalar o aplicativo, usaremos um arquivo de configuração de amostra para [configurar nginx](#configure-nginx).

### Instalar e configurar o php-fpm

Adobe Commerce e Magento Open Source exigem várias [extensões PHP](../php-settings.md) para funcionar adequadamente. Além dessas extensões, você também deve instalar e configurar o `php-fpm` se estiver usando nginx.

Para instalar e configurar `php-fpm`:

1. Instalar `php-fpm` e `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Este comando instala a versão mais recente disponível do PHP 7.2.X. Consulte [requisitos do sistema](../../system-requirements.md) para versões PHP compatíveis.

1. Abra o `php.ini` arquivos em um editor:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Edite ambos os arquivos para corresponder às seguintes linhas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Recomendamos definir o limite de memória como 2 G ao testar o Adobe Commerce e o Magento Open Source. Consulte [Configurações PHP necessárias](../php-settings.md) para obter mais informações.

1. Salve e saia do editor.

1. Reinicie o `php-fpm` serviço:

   ```bash
   systemctl restart php7.2-fpm
   ```

### Instalar e configurar o MySQL

Consulte [MySQL](../database/mysql.md) para obter mais informações.

### Instalar e configurar

Há várias maneiras de baixar o Adobe Commerce e o Magento Open Source, incluindo:

* [Obter a metapackage do Composer](../../composer.md)

* [Clonar o repositório Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Este exemplo mostra uma instalação baseada em Composer usando a linha de comando.

1. Como [proprietário do sistema de arquivos](../file-system/overview.md), faça logon no servidor de aplicativos.

1. Altere para o diretório raiz do servidor da Web ou um diretório que você configurou como um ponto de raiz do host virtual. Neste exemplo, estamos usando o padrão Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Instale o Composer globalmente. O Composer é necessário atualizar as dependências antes de instalar o Adobe Commerce ou o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crie um projeto do Composer usando o metapackage do Magento Open Source ou Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando solicitado, insira [chaves de autenticação](../authentication-keys.md). Seu _chave pública_ é seu nome de usuário; your _chave privada_ é sua senha.

1. Defina permissões de leitura/gravação para o grupo de servidores da Web antes de instalar o aplicativo. Isso é necessário para que a linha de comando possa gravar arquivos no sistema de arquivos.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Instalar a partir do [linha de comando](../../advanced.md). Este exemplo supõe que o diretório de instalação tenha o nome `magento2ee`, o `db-host` está na mesma máquina (`localhost`) e que a `db-name`, `db-user`e `db-password` são todas `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. Alterne para o modo desenvolvedor:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar nó

Recomendamos configurar o nginx usando o `nginx.conf.sample` arquivo de configuração fornecido no diretório de instalação e nginx host virtual.

Essas instruções consideram que você está usando o local padrão do Ubuntu para o host virtual nginx (por exemplo, `/etc/nginx/sites-available`) e o docroot padrão Ubuntu (por exemplo, `/var/www/html`), no entanto, é possível alterar esses locais para atender ao seu ambiente.

1. Crie um novo host virtual para o seu site:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Adicione a seguinte configuração:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >O `include` deve apontar para o arquivo de configuração do nó de amostra no diretório de instalação.

1. Substituir `www.magento-dev.com` com seu nome de domínio. Deve corresponder ao URL básico especificado ao instalar o Adobe Commerce ou o Magento Open Source.

1. Salve e saia do editor.

1. Ative o host virtual recém-criado criando um link simbólico para ele no `/etc/nginx/sites-enabled` diretório:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Verifique se a sintaxe está correta:

   ```bash
   nginx -t
   ```

1. Reinicie o nginx:

   ```bash
   systemctl restart nginx
   ```

### Verifique a instalação

Abra um navegador da Web e navegue até o URL base do site para [verifique a instalação](../../next-steps/verify.md).

## CentOS 7

A seção a seguir descreve como instalar o Adobe Commerce e o Magento Open Source 2.x no CentOS 7 usando nginx, PHP e MySQL.

### Instalar o nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

Após a conclusão da instalação, inicie o nginx e configure-o para iniciar no momento da inicialização:

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

Após concluir as seções a seguir e instalar o aplicativo, usaremos um arquivo de configuração de amostra para configurar o nginx.

### Instalar e configurar o php-fpm

Adobe Commerce e Magento Open Source exigem várias [PHP](../php-settings.md) extensões para funcionarem corretamente. Além dessas extensões, você também deve instalar e configurar o `php-fpm` se estiver usando nginx.

1. Instalar `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Abra o `/etc/php.ini` em um editor.

1. Exclua o comentário da `cgi.fix_pathinfo` e altere o valor para `0`.

1. Edite o arquivo para corresponder às seguintes linhas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Recomendamos definir o limite de memória como 2 G ao testar o Adobe Commerce ou o Magento Open Source. Consulte [Configurações PHP necessárias](../php-settings.md) para obter mais informações.

1. Exclua o comentário do diretório do caminho da sessão e defina o caminho:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Salve e saia do editor.

1. Abrir `/etc/php-fpm.d/www.conf` em um editor.

1. Edite o arquivo para corresponder às seguintes linhas:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Exclua as linhas de ambiente:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Salve e saia do editor.

1. Crie um diretório para o caminho da sessão PHP e altere o proprietário para o `apache` usuário e grupo:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Crie um diretório para o caminho da sessão PHP e altere o proprietário para o `apache` usuário e grupo:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Inicie o `php-fpm` e configure-o para iniciar no momento da inicialização:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Verifique se a variável `php-fpm` O serviço está em execução:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Instalar e configurar o MySQL

Consulte [MySQL](..//database/mysql.md) para obter mais informações.

### Instalar e configurar

Há várias maneiras de baixar o Adobe Commerce e o Magento Open Source, incluindo:

* [Obter a metapackage do Composer](../../composer.md)

* [Clonar o repositório Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Este exemplo mostra uma instalação baseada em Composer usando a linha de comando.

1. Como [proprietário do sistema de arquivos](../file-system/overview.md), faça logon no servidor de aplicativos.

1. Altere para o diretório raiz do servidor da Web ou um diretório que você configurou como um ponto de raiz do host virtual. Neste exemplo, estamos usando o padrão Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Instale o Composer globalmente. O Composer é necessário atualizar as dependências antes de instalar o Adobe Commerce ou o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crie um projeto do Composer usando o metapackage do Magento Open Source ou Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando solicitado, insira [chaves de autenticação](../authentication-keys.md). Seu _chave pública_ é seu nome de usuário; your _chave privada_ é sua senha.

1. Defina permissões de leitura/gravação para o grupo de servidores da Web antes de instalar o aplicativo. Isso é necessário para que a linha de comando possa gravar arquivos no sistema de arquivos.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Instalar a partir do [linha de comando](../../advanced.md). Este exemplo supõe que o diretório de instalação tenha o nome `magento2ee`, o `db-host` está na mesma máquina (`localhost`) e que a `db-name`, `db-user`e `db-password` são todas `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Alterne para o modo desenvolvedor:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar nó

Recomendamos configurar o nginx usando o `nginx.conf.sample` arquivo de configuração fornecido no diretório de instalação e nginx host virtual.

Essas instruções presumem que você está usando o local padrão do CentOS para o host virtual do nó (por exemplo, `/etc/nginx/conf.d`) e o docroot padrão (por exemplo, `/usr/share/nginx/html`), no entanto, é possível alterar esses locais para atender ao seu ambiente.

1. Crie um novo host virtual para o seu site:

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. Adicione a seguinte configuração:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >O `include` deve apontar para o arquivo de configuração do nó de amostra no diretório de instalação.

1. Substituir `www.magento-dev.com` com seu nome de domínio.

1. Salve e saia do editor.

1. Verifique se a sintaxe está correta:

   ```bash
   nginx -t
   ```

1. Reinicie o nginx:

   ```bash
   systemctl restart nginx
   ```

### Configurar SELinux e Firewalld

O SELinux é ativado por padrão no CentOS 7. Use o seguinte comando para ver se ele está em execução:

```bash
sestatus
```

Para configurar o SELinux e o firewalld:

1. Instale as ferramentas de gerenciamento do SELinux:

   ```bash
   yum -y install policycoreutils-python
   ```

1. Execute os seguintes comandos para alterar o contexto de segurança do diretório de instalação:

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Instale o pacote firewalld:

   ```bash
   yum -y install firewalld
   ```

1. Inicie o serviço de firewall e configure-o para iniciar no momento da inicialização:

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Execute os seguintes comandos para abrir portas para HTTP e HTTPS, para que você possa acessar o URL base de um navegador da Web:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Verifique a instalação

Abra um navegador da Web e navegue até o URL base do site para [verifique a instalação](../../next-steps/verify.md).
