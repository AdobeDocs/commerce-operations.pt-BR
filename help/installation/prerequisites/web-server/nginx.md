---
title: Nginx
description: Siga estas etapas para instalar e configurar o servidor Web Nginx para instalações locais do Adobe Commerce.
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Nginx

O Adobe Commerce oferece suporte ao nginx 1.x (ou à [versão principal mais recente](https://nginx.org/en/linux_packages.html#mainline)). Você também deve instalar a versão mais recente do `php-fpm`.

As instruções de instalação variam de acordo com o sistema operacional que você está usando. Consulte [PHP](../php-settings.md) para obter informações.

## Ubuntu

A seção a seguir descreve como instalar o Adobe Commerce 2.x no Ubuntu usando nginx, PHP e MySQL.

### Instalar o nginx

```bash
sudo apt -y install nginx
```

Você também pode [compilar nginx a partir da origem](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Depois de concluir as seções a seguir e instalar o aplicativo, usaremos um exemplo de arquivo de configuração para [configurar nginx](#configure-nginx).

### Instalar e configurar o php-fpm

O Adobe Commerce requer várias [extensões PHP](../php-settings.md) para funcionar corretamente. Além dessas extensões, você também deve instalar e configurar a extensão `php-fpm` se estiver usando nginx.

Para instalar e configurar o `php-fpm`:

1. Instalar `php-fpm` e `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Este comando instala a última versão disponível do PHP 7.2.X. Consulte [requisitos do sistema](../../system-requirements.md) para ver as versões do PHP suportadas.

1. Abrir os arquivos `php.ini` em um editor:

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
   >Recomendamos definir o limite de memória para 2 G ao testar o Adobe Commerce. Consulte [Configurações PHP necessárias](../php-settings.md) para obter mais informações.

1. Salve e saia do editor.

1. Reiniciar o serviço `php-fpm`:

   ```bash
   systemctl restart php7.2-fpm
   ```

### Instalar e configurar o MySQL

Consulte [MySQL](../database/mysql.md) para obter mais informações.

### Instalar e configurar

Há várias maneiras de baixar o Adobe Commerce, incluindo:

* [Obtenha o metapackage do Composer](../../composer.md)

* [Clonar o repositório Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Este exemplo mostra uma instalação baseada no Composer usando a linha de comando.

1. Como o [proprietário do sistema de arquivos](../file-system/overview.md), faça logon no servidor de aplicativos.

1. Altere para o diretório docroot do servidor Web ou um diretório que você configurou como docroot do host virtual. Para este exemplo, estamos usando o padrão Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Instale o Composer globalmente. O Composer é necessário para atualizar dependências antes de instalar o Adobe Commerce:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crie um projeto do Composer usando o metapackage do Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando solicitado, insira suas [chaves de autenticação](../authentication-keys.md). Sua _chave pública_ é seu nome de usuário; sua _chave privada_ é sua senha.

1. Defina permissões de leitura e gravação para o grupo de servidores Web antes de instalar o aplicativo. Isso é necessário para que a linha de comando possa gravar arquivos no sistema de arquivos.

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

1. Instalar da [linha de comando](../../advanced.md). Este exemplo supõe que o diretório de instalação seja nomeado como `magento2ee`, o `db-host` esteja na mesma máquina (`localhost`) e que o `db-name`, `db-user` e `db-password` sejam todos `magento`:

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

1. Alternar para modo de desenvolvedor:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar nginx

Recomendamos configurar o nginx usando o arquivo de configuração `nginx.conf.sample` fornecido no diretório de instalação e no host virtual nginx.

Essas instruções supõem que você esteja usando o local padrão do Ubuntu para o host virtual nginx (por exemplo, `/etc/nginx/sites-available`) e o docroot padrão do Ubuntu (por exemplo, `/var/www/html`). No entanto, você pode alterar esses locais para atender ao seu ambiente.

1. Crie um novo host virtual para seu site:

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
   >A diretiva `include` deve apontar para a amostra do arquivo de configuração nginx no diretório de instalação.

1. Substitua `www.magento-dev.com` pelo nome de domínio. Deve corresponder ao URL de base especificado ao instalar o Adobe Commerce.

1. Salve e saia do editor.

1. Ative o host virtual recém-criado criando um link simbólico para ele no diretório `/etc/nginx/sites-enabled`:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Verifique se a sintaxe está correta:

   ```bash
   nginx -t
   ```

1. Reiniciar o nginx:

   ```bash
   systemctl restart nginx
   ```

### Verificar a instalação

Abra um navegador e navegue até a URL base do site para [verificar a instalação](../../next-steps/verify.md).

## CentOS 7

A seção a seguir descreve como instalar o Adobe Commerce 2.x no CentOS 7 usando nginx, PHP e MySQL.

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

Depois de concluir as seções a seguir e instalar o aplicativo, usaremos um arquivo de configuração de exemplo para configurar o nginx.

### Instalar e configurar o php-fpm

O Adobe Commerce requer várias extensões [PHP](../php-settings.md) para funcionar corretamente. Além dessas extensões, você também deve instalar e configurar a extensão `php-fpm` se estiver usando nginx.

1. Instalar `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Abra o arquivo `/etc/php.ini` em um editor.

1. Descomente a linha `cgi.fix_pathinfo` e altere o valor para `0`.

1. Edite o arquivo para corresponder às seguintes linhas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Recomendamos definir o limite de memória para 2 G ao testar o Adobe Commerce. Consulte [Configurações PHP necessárias](../php-settings.md) para obter mais informações.

1. Remova o comentário do diretório de caminho da sessão e defina o caminho:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Salve e saia do editor.

1. Abra `/etc/php-fpm.d/www.conf` em um editor.

1. Edite o arquivo para corresponder às seguintes linhas:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Remova o comentário das linhas de ambiente:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Salve e saia do editor.

1. Crie um diretório para o caminho da sessão PHP e altere o proprietário para o usuário e grupo `apache`:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Crie um diretório para o caminho da sessão PHP e altere o proprietário para o usuário e grupo `apache`:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Inicie o serviço `php-fpm` e configure-o para iniciar no momento da inicialização:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Verifique se o serviço `php-fpm` está em execução:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Instalar e configurar o MySQL

Consulte [MySQL](..//database/mysql.md) para obter mais informações.

### Instalar e configurar

Há várias maneiras de baixar o Adobe Commerce, incluindo:

* [Obtenha o metapackage do Composer](../../composer.md)

* [Clonar o repositório Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Este exemplo mostra uma instalação baseada no Composer usando a linha de comando.

1. Como o [proprietário do sistema de arquivos](../file-system/overview.md), faça logon no servidor de aplicativos.

1. Altere para o diretório docroot do servidor Web ou um diretório que você configurou como docroot do host virtual. Para este exemplo, estamos usando o padrão Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Instale o Composer globalmente. O Composer é necessário para atualizar dependências antes de instalar o Adobe Commerce:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crie um projeto do Composer usando o metapackage do Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando solicitado, insira suas [chaves de autenticação](../authentication-keys.md). Sua _chave pública_ é seu nome de usuário; sua _chave privada_ é sua senha.

1. Defina permissões de leitura e gravação para o grupo de servidores Web antes de instalar o aplicativo. Isso é necessário para que a linha de comando possa gravar arquivos no sistema de arquivos.

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

1. Instalar da [linha de comando](../../advanced.md). Este exemplo supõe que o diretório de instalação seja nomeado como `magento2ee`, o `db-host` esteja na mesma máquina (`localhost`) e que o `db-name`, `db-user` e `db-password` sejam todos `magento`:

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

1. Alternar para modo de desenvolvedor:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar nginx

Recomendamos configurar o nginx usando o arquivo de configuração `nginx.conf.sample` fornecido no diretório de instalação e no host virtual nginx.

Essas instruções supõem que você esteja usando o local padrão do CentOS para o host virtual nginx (por exemplo, `/etc/nginx/conf.d`) e o docroot padrão (por exemplo, `/usr/share/nginx/html`). No entanto, você pode alterar esses locais para atender ao seu ambiente.

1. Crie um novo host virtual para seu site:

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
   >A diretiva `include` deve apontar para a amostra do arquivo de configuração nginx no diretório de instalação.

1. Substitua `www.magento-dev.com` pelo nome de domínio.

1. Salve e saia do editor.

1. Verifique se a sintaxe está correta:

   ```bash
   nginx -t
   ```

1. Reiniciar o nginx:

   ```bash
   systemctl restart nginx
   ```

### Configurar SELinux e Fireworld

O SELinux é ativado por padrão no CentOS 7. Use o seguinte comando para ver se está em execução:

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

1. Execute os seguintes comandos para abrir portas para HTTP e HTTPS para poder acessar o URL base de um navegador da Web:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Verificar a instalação

Abra um navegador e navegue até a URL base do site para [verificar a instalação](../../next-steps/verify.md).
