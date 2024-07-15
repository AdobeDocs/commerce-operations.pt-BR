---
title: Configurar vários sites com o Nginx
description: Siga este tutorial para configurar vários sites com o Nginx.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Configurar vários sites com o Nginx

Presumimos que:

- Você está trabalhando em uma máquina de desenvolvimento (laptop, máquina virtual ou similar).

  Tarefas adicionais podem ser necessárias para implantar vários sites em um ambiente hospedado; verifique com seu provedor de hospedagem para obter mais informações.

  Tarefas adicionais são necessárias para configurar a Adobe Commerce na infraestrutura em nuvem. Após concluir as tarefas discutidas neste tópico, consulte [Configurar vários sites ou lojas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) no _guia do Commerce na Infraestrutura da Nuvem_.

- Você aceita vários domínios em um arquivo de host virtual ou usa um host virtual por site; os arquivos de configuração de host virtual estão localizados em `/etc/nginx/sites-available`.
- Você usa o `nginx.conf.sample` fornecido pelo Commerce somente com as modificações discutidas neste tutorial.
- O software Commerce está instalado em `/var/www/html/magento2`.
- Você tem dois sites diferentes do padrão:

   - `french.mysite.mg` com código de site `french` e código de exibição de armazenamento `fr`
   - `german.mysite.mg` com código de site `german` e código de exibição de armazenamento `de`
   - `mysite.mg` é o site padrão e a exibição de armazenamento padrão

>[!TIP]
>
>Consulte [Criar sites](ms-admin.md#step-2-create-websites) e [Criar exibições de loja](ms-admin.md#step-4-create-store-views) para obter ajuda sobre como localizar esses valores.

Este é um roteiro para configurar vários sites com nginx:

1. [Configurar sites, lojas e exibições de loja](ms-admin.md) no Administrador.
1. Crie um [Host virtual Nginx](#step-2-create-nginx-virtual-hosts)) para mapear vários sites ou um host virtual Nginx por site da Commerce (etapas detalhadas abaixo).
1. Passe os valores das [variáveis MAGE](ms-overview.md) `$MAGE_RUN_TYPE` e `$MAGE_RUN_CODE` para nginx usando o `nginx.conf.sample` fornecido por Magento (etapas detalhadas abaixo).

   - `$MAGE_RUN_TYPE` pode ser `store` ou `website`:

      - Use o `website` para carregar seu site na vitrine eletrônica.
      - Use `store` para carregar qualquer exibição de loja em sua vitrine eletrônica.

   - `$MAGE_RUN_CODE` é o código de exibição de site ou loja exclusivo que corresponde a `$MAGE_RUN_TYPE`.

1. Atualize a configuração de URL base no administrador do Commerce.

## Etapa 1: criar sites, lojas e visualizações de loja no Administrador

Consulte [Configurar vários sites, lojas e exibições de loja no Administrador](ms-admin.md).

## Etapa 2: Criar hosts virtuais nginx

Esta etapa explica como carregar sites na loja. É possível usar as visualizações de sites ou de loja; se você usar as visualizações de loja, deverá ajustar os valores do parâmetro de acordo. Você deve concluir as tarefas desta seção como um usuário com privilégios `sudo`.

Usando apenas um [arquivo de host virtual nginx](#step-2-create-nginx-virtual-hosts), você pode manter sua configuração nginx simples e limpa. Ao usar vários arquivos de host virtual, você pode personalizar cada armazenamento (para usar um local personalizado para `french.mysite.mg` por instância).

**Para criar um host virtual** (simplificado):

Esta configuração se expande na [nginx](../../installation/prerequisites/web-server/nginx.md).

1. Abra um editor de texto e adicione o seguinte conteúdo a um novo arquivo chamado `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Salve as alterações nos arquivos e saia do editor de texto.
1. Verifique a configuração do servidor:

   ```bash
   nginx -t
   ```

1. Se for bem-sucedido, a seguinte mensagem será exibida:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se forem exibidos erros, verifique a sintaxe dos arquivos de configuração do host virtual.

1. Criar link simbólico no diretório `/etc/nginx/sites-enabled`:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Para obter mais detalhes sobre a diretiva de mapa, consulte a documentação de [nginx na diretiva de mapa](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Para criar vários hosts virtuais**:

1. Abra um editor de texto e adicione o seguinte conteúdo a um novo arquivo chamado `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Crie outro arquivo chamado `german.mysite.mg` no mesmo diretório com o seguinte conteúdo:

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Salve as alterações nos arquivos e saia do editor de texto.
1. Verifique a configuração do servidor:

   ```bash
   nginx -t
   ```

1. Se for bem-sucedido, a seguinte mensagem será exibida:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se forem exibidos erros, verifique a sintaxe dos arquivos de configuração do host virtual.

1. Criar links simbólicos no diretório `/etc/nginx/sites-enabled`:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Etapa 3: Modificar nginx.conf.sample

>[!TIP]
>
>Não edite o arquivo `nginx.conf.sample`; ele é um arquivo Commerce principal que pode ser atualizado com cada nova versão. Em vez disso, copie o arquivo `nginx.conf.sample`, renomeie-o e edite o arquivo copiado.

**Para editar o ponto de entrada do PHP para o aplicativo principal**:

Para modificar o arquivo `nginx.conf.sample`**:

1. Abra um editor de texto e revise o `nginx.conf.sample` arquivo ,`<magento2_installation_directory>/nginx.conf.sample`. Procure a seguinte seção:

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. Atualize o arquivo `nginx.conf.sample` com as duas linhas a seguir antes da instrução include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Um exemplo de ponto de entrada do PHP atualizado para o aplicativo principal se parece com:

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## Etapa 4: atualizar a configuração de URL base

Você deve atualizar a URL base dos sites `french` e `german` no administrador do Commerce.

### Atualizar o URL Base do Site em Francês

1. Faça logon no administrador do Commerce e navegue até **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. Altere o _escopo de configuração_ para o site `french`.
1. Expanda a seção **URLs de Base** e atualize o valor de **URL de Base** e **URL de Link de Base** para `http://french.magento24.com/`.
1. Expanda a seção **URLs de Base (Seguro)** e atualize o valor de **URL de Base Segura** e **URL de Link de Base Segura** para `https://french.magento24.com/`.
1. Clique em **Salvar configuração** e salve as alterações de configuração.

### Atualizar URL Base do Site Alemão

1. Faça logon no administrador do Commerce e navegue até **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. Altere o _escopo de configuração_ para o site `german`.
1. Expanda a seção **URLs de Base** e atualize o valor de **URL de Base** e **URL de Link de Base** para `http://german.magento24.com/`.
1. Expanda a seção **URLs de Base (Seguro)** e atualize o valor de **URL de Base Segura** e **URL de Link de Base Segura** para `https://german.magento24.com/`.
1. Clique em **Salvar configuração** e salve as alterações de configuração.

### Limpe o cache

Execute o seguinte comando para limpar os caches `config` e `full_page`.

```bash
bin/magento cache:clean config full_page
```

## Verifique seu site

A menos que você tenha um DNS configurado para as URLs dos armazenamentos, é necessário adicionar uma rota estática ao host no arquivo `hosts`:

1. Localize o arquivo `hosts` do sistema operacional.
1. Adicione a rota estática no formato:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Vá para um dos seguintes URLs no seu navegador:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Tarefas adicionais podem ser necessárias para implantar vários sites em um ambiente hospedado; verifique com seu provedor de hospedagem para obter mais informações.
>- Tarefas adicionais são necessárias para configurar o Adobe Commerce na infraestrutura em nuvem; consulte [Configurar vários sites ou lojas na nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) no _guia do Commerce na Infraestrutura em Nuvem_.

### Solução de problemas

- Se os sites em francês e alemão retornarem 404s, mas o Administrador carregar, verifique se você concluiu a [Etapa 6: adicionar o código da loja à URL de base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se todos os URLs retornarem 404s, reinicie o servidor da Web.
- Se o Admin não funcionar corretamente, certifique-se de configurar os hosts virtuais corretamente.
