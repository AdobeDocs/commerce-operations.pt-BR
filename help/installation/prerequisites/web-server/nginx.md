---
title: Instalar o Nginx para implantações locais
description: Saiba como instalar e configurar o servidor Web Nginx para implantações locais do Adobe Commerce. Configure o PHP-FPM e seu host virtual.
feature: Install, Configuration
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Instalar o Nginx para implantações locais {#nginx}

Este guia aborda a instalação de Nginx para implantações locais do Adobe Commerce e a definição das configurações de Nginx exigidas pelo Commerce. Ele inclui procedimentos específicos do sistema operacional para Ubuntu e CentOS, juntamente com orientações para a configuração do PHP-FPM. A Adobe recomenda seguir as instruções de configuração fornecidas neste guia para preservar a funcionalidade e a segurança do aplicativo do Commerce.

O Adobe oferece suporte às versões do Nginx listadas nos [requisitos do sistema](../../system-requirements.md) da sua versão do Adobe Commerce. As versões compatíveis variam de acordo com a versão. O Nginx também requer uma configuração PHP-FPM compatível. Para requisitos relacionados do PHP, consulte [PHP](../php-settings.md).

## Instalar no Ubuntu

Use esta seção para instalar o Adobe Commerce no Ubuntu com Nginx, PHP e MySQL.

### Instalar Nginx

```bash
sudo apt -y install nginx
```

Você também pode [compilar Nginx a partir da origem](https://www.armanism.com/blog/install-nginx-on-ubuntu).

Após concluir as seções a seguir e instalar o aplicativo, use o arquivo de configuração de exemplo para [configurar o Nginx](#configure-nginx). Essa configuração recomendada preserva a funcionalidade e a segurança do aplicativo do Commerce.

### Instalar e configurar o PHP-FPM

O Adobe Commerce requer várias [extensões PHP](../php-settings.md) para funcionar corretamente. Além dessas extensões, você também deve instalar e configurar a extensão `php-fpm` se estiver usando o Nginx.

Para instalar e configurar o `php-fpm`:

1. Instale os pacotes `php-fpm` e `php-cli` para a versão do PHP suportada pela sua versão do Adobe Commerce. No Ubuntu, os nomes dos pacotes normalmente seguem esse padrão:

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >Substitua `<php-version>` pela versão secundária do PHP com suporte listada em [requisitos do sistema](../../system-requirements.md) para a versão do Adobe Commerce que você está instalando. Use o mesmo valor nos caminhos de arquivo, nome de serviço e caminho de soquete nas etapas a seguir.

1. Abrir os arquivos `php.ini` em um editor:

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. Edite ambos os arquivos para corresponder às seguintes linhas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >A Adobe recomenda definir o limite de memória para 2 GB ao testar o Adobe Commerce. Consulte [Configurações PHP necessárias](../php-settings.md) para obter mais informações.

1. Salve e saia do editor.

1. Reiniciar o serviço `php-fpm`:

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### Instalar e configurar o MySQL

Consulte [MySQL](../database/mysql.md) para obter mais informações.

### Instalar o Adobe Commerce

É possível baixar o Adobe Commerce de várias maneiras:

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

1. Instalar da [linha de comando](../../advanced.md). Este exemplo pressupõe que o diretório de instalação seja nomeado como `magento2ee` e que o host do banco de dados esteja na mesma máquina (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >Use o valor `--search-engine` e as opções de host/porta correspondentes exigidas pela versão do Adobe Commerce que você está instalando. Para versões anteriores à 2.4.6, use o `elasticsearch7` com as opções `--elasticsearch-*` para o Elasticsearch 7 ou OpenSearch. Para a versão 2.4.6 e posterior, use o valor do mecanismo de pesquisa e as opções correspondentes da CLI compatíveis com essa versão.

1. Alternar para modo de desenvolvedor:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar Nginx

A Adobe recomenda configurar o Nginx usando o arquivo de configuração `nginx.conf.sample` fornecido no diretório de instalação e a configuração do host virtual Nginx para preservar a funcionalidade e a segurança do aplicativo Commerce.

>[!IMPORTANT]
>
>O arquivo `nginx.conf.sample` fornece o roteamento de aplicativo necessário, bem como regras de proteção de segurança. Por exemplo, ela restringe a execução de scripts mal-intencionados carregados no servidor. Se você não usar esse arquivo ou modificar suas regras, será responsável pela implementação de controles de segurança equivalentes na sua configuração personalizada do nginx.

Essas instruções supõem que você esteja usando o local padrão do Ubuntu para o host virtual Nginx, como `/etc/nginx/sites-available`, e o docroot padrão do Ubuntu, como `/var/www/html`. Você pode alterar esses locais para se adequar ao seu ambiente.

1. Crie um novo host virtual para seu site:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Adicione a seguinte configuração:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
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

1. Reiniciar O Nginx:

   ```bash
   systemctl restart nginx
   ```

### Verificar a instalação

Para verificar a instalação, abra um navegador da Web e navegue até o URL base do site. Para obter mais informações, consulte [Verificar a instalação](../../next-steps/verify.md).

## Instalação no CentOS 7

Use esta seção para instalar o Adobe Commerce no CentOS 7 com Nginx, PHP e MySQL.

### Instalar Nginx

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

Depois de concluir as seções a seguir e instalar o aplicativo, use um arquivo de configuração de exemplo para configurar o Nginx.

### Instalar e configurar o PHP-FPM

O Adobe Commerce requer várias extensões [PHP](../php-settings.md) para funcionar corretamente. Além dessas extensões, você também deve instalar e configurar a extensão `php-fpm` se estiver usando o Nginx.

1. Instalar `php-fpm`:

   ```bash
   yum -y install <php-fpm-package>
   ```

1. Abra o arquivo `/etc/php.ini` em um editor.

   >[!NOTE]
   >
   >Instale o pacote que fornece `php-fpm` para a versão do PHP suportada pela versão do Adobe Commerce que você está instalando. Os nomes dos pacotes variam de acordo com o repositório e sistema operacional. Consulte [requisitos de sistema](../../system-requirements.md).

1. Descomente a linha `cgi.fix_pathinfo` e altere o valor para `0`.

1. Edite o arquivo para corresponder às seguintes linhas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >A Adobe recomenda definir o limite de memória para 2 GB ao testar o Adobe Commerce. Consulte [Configurações PHP necessárias](../php-settings.md) para obter mais informações.

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

1. Crie um diretório para o caminho da sessão PHP e altere o proprietário para o usuário e grupo `nginx`:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. Crie um diretório para o soquete PHP-FPM e altere o proprietário para o usuário e grupo `nginx`:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
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

Consulte [MySQL](../database/mysql.md) para obter mais informações.

### Instalar o Adobe Commerce

É possível baixar o Adobe Commerce de várias maneiras:

* [Obtenha o metapackage do Composer](../../composer.md)

* [Clonar o repositório Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Este exemplo mostra uma instalação baseada no Composer usando a linha de comando.

1. Como o [proprietário do sistema de arquivos](../file-system/overview.md), faça logon no servidor de aplicativos.

1. Altere para o diretório docroot do servidor Web ou um diretório que você configurou como docroot do host virtual. Para este exemplo, use o padrão CentOS `/usr/share/nginx/html`.

   ```bash
   cd /usr/share/nginx/html
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
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Instalar da [linha de comando](../../advanced.md). Este exemplo pressupõe que o diretório de instalação seja nomeado como `magento2ee` e que o host do banco de dados esteja na mesma máquina (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Alternar para modo de desenvolvedor:

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar Nginx

Recomendamos configurar o Nginx usando o arquivo `nginx.conf.sample` no diretório de instalação e sua configuração de host virtual Nginx.

>[!IMPORTANT]
>
>O arquivo `nginx.conf.sample` fornece o roteamento de aplicativo necessário, bem como regras de proteção de segurança. Por exemplo, ela restringe a execução de scripts mal-intencionados carregados no servidor. Se você não usar esse arquivo ou modificar suas regras, será responsável pela implementação de controles de segurança equivalentes na sua configuração personalizada do nginx.

Essas instruções supõem que você esteja usando o local padrão do CentOS para o host virtual Nginx, como `/etc/nginx/conf.d`, e o docroot padrão, como `/usr/share/nginx/html`. Você pode alterar esses locais para se adequar ao seu ambiente.

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

1. Reiniciar O Nginx:

   ```bash
   systemctl restart nginx
   ```

### Configurar SELinux e firewalld

O SELinux é ativado por padrão no CentOS 7. Use o seguinte comando para confirmar se está em execução:

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

Para verificar a instalação, abra um navegador da Web e navegue até o URL base do site. Para obter mais informações, consulte [Verificar a instalação](../../next-steps/verify.md).
