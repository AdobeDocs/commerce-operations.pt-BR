---
title: Configurar vários sites com o Nginx
description: Siga este tutorial para configurar vários sites com o Nginx.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---


# Configurar vários sites com o Nginx

Presumimos que:

- Você está trabalhando em uma máquina de desenvolvimento (laptop, máquina virtual ou semelhante).

   Podem ser necessárias tarefas adicionais para implantar vários sites em um ambiente hospedado; consulte seu provedor de hospedagem para obter mais informações.

   Tarefas adicionais são necessárias para configurar o Adobe Commerce na infraestrutura de nuvem. Após concluir as tarefas discutidas neste tópico, consulte [Configurar vários sites da Web ou lojas](https://devdocs.magento.com/cloud/project/project-multi-sites.html) no _guia Commerce Cloud_.

- Você aceita vários domínios em um arquivo de host virtual ou usa um host virtual por site; os arquivos de configuração do host virtual estão localizados em `/etc/nginx/sites-available`.
- Você usa a variável `nginx.conf.sample` fornecido pelo Commerce com apenas as modificações discutidas neste tutorial.
- O software Commerce está instalado em `/var/www/html/magento2`.
- Você tem dois sites diferentes do padrão:

   - `french.mysite.mg` com código de site `french` e armazenar código de exibição `fr`
   - `german.mysite.mg` com código de site `german` e armazenar código de exibição `de`
   - `mysite.mg` é o site padrão e a exibição de loja padrão

>[!TIP]
>
>Consulte [Criar sites](ms-admin.md#step-2-create-websites) e [Criar visualizações de loja](ms-admin.md#step-4-create-store-views) para obter ajuda sobre como localizar esses valores.

Veja a seguir um roteiro para a configuração de vários sites com o nginx:

1. [Configurar sites, lojas e visualizações de loja](ms-admin.md) em Admin.
1. Crie um [Nginx host virtual](#step-2-create-nginx-virtual-hosts)) para mapear vários sites ou um host virtual Nginx por site do Commerce (etapas detalhadas abaixo).
1. Passe os valores da variável [Variáveis de MAGE](ms-overview.md) `$MAGE_RUN_TYPE` e `$MAGE_RUN_CODE` para identificar usando o Magento fornecido `nginx.conf.sample` (etapas detalhadas abaixo).

   - `$MAGE_RUN_TYPE` pode ser `store` ou `website`:

      - Use `website` para carregar seu site na loja.
      - Use `store` para carregar qualquer visualização de loja em sua loja.
   - `$MAGE_RUN_CODE` é o único código de visualização de site ou loja que corresponde a `$MAGE_RUN_TYPE`.


1. Atualize a configuração do URL básico no administrador do Commerce.

## Etapa 1: Criar sites, lojas e visualizações de loja no Administrador

Consulte [Configurar vários sites, lojas e visualizações de loja no Administrador](ms-admin.md).

## Etapa 2: Criar novos hosts virtuais

Esta etapa discute como carregar sites na [vitrine](https://glossary.magento.com/storefront). Você pode usar sites ou exibições de armazenamento; se você usar exibições de loja, ajustará os valores do parâmetro de acordo. Você deve concluir as tarefas desta seção como um usuário com `sudo` privilégios.

Utilizando apenas uma [nginx arquivo de host virtual](#step-2-create-nginx-virtual-hosts), você pode manter a configuração do nginx simples e limpa. Ao usar vários arquivos de host virtual, você pode personalizar cada loja (para usar um local personalizado para `french.mysite.mg` por exemplo).

**Para criar um host virtual** (simplificado):

Essa configuração é expandida em [Configuração Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html).

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

1. Se bem-sucedido, a seguinte mensagem será exibida:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se os erros forem exibidos, verifique a sintaxe dos arquivos de configuração do host virtual.

1. Criar link simbólico no `/etc/nginx/sites-enabled` diretório:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Para obter mais detalhes sobre a diretiva de mapa, consulte [nginx documentações sobre a diretiva do mapa](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


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

1. Se bem-sucedido, a seguinte mensagem será exibida:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se os erros forem exibidos, verifique a sintaxe dos arquivos de configuração do host virtual.

1. Crie links simbólicos no `/etc/nginx/sites-enabled` diretório:

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
>Não edite o `nginx.conf.sample` ficheiro; é um arquivo principal do Commerce que pode ser atualizado a cada nova versão. Em vez disso, copie o `nginx.conf.sample` , renomeie-o e edite o arquivo copiado.

**Para editar o ponto de entrada PHP para o aplicativo principal**:

Para modificar o `nginx.conf.sample` ficheiro**:

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

1. Atualize o `nginx.conf.sample` arquivo com as duas linhas a seguir antes da instrução include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Um exemplo de ponto de entrada PHP atualizado para o aplicativo principal tem a seguinte aparência:

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

## Etapa 4: Atualize a configuração do URL básico

Você deve atualizar o URL básico da variável `french` e `german` sites na administração do Commerce.

### Atualizar URL básico do site em francês

1. Faça logon no administrador do Commerce e navegue até **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. Altere o _escopo de configuração_ para `french` site.
1. Expandir **URLs básicos** e atualize a seção **URL básica** e **URL do link básico** para `http://french.magento24.com/`.
1. Expandir **URLs básicos (seguros)** e atualize a seção **URL de base segura** e **URL do Link Base Seguro** para `https://french.magento24.com/`.
1. Clique em **Salvar configuração** e salve as alterações de configuração.

### Atualizar URL base do site alemão

1. Faça logon no administrador do Commerce e navegue até **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. Altere o _escopo de configuração_ para `german` site.
1. Expandir **URLs básicos** e atualize a seção **URL básica** e **URL do link básico** para `http://german.magento24.com/`.
1. Expandir **URLs básicos (seguros)** e atualize a seção **URL de base segura** e **URL do Link Base Seguro** para `https://german.magento24.com/`.
1. Clique em **Salvar configuração** e salve as alterações de configuração.

### Limpe o cache

Execute o seguinte comando para limpar o `config` e `full_page` caches.

```bash
bin/magento cache:clean config full_page
```

## Verificar o site

A menos que você tenha o DNS configurado para os URLs das suas lojas, é necessário adicionar uma rota estática ao host em seu `hosts` arquivo:

1. Localize seu sistema operacional `hosts` arquivo.
1. Adicione a rota estática no formato :

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. Vá para um dos seguintes URLs em seu navegador:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Podem ser necessárias tarefas adicionais para implantar vários sites em um ambiente hospedado; consulte seu provedor de hospedagem para obter mais informações.
>- Tarefas adicionais são necessárias para configurar o Adobe Commerce na infraestrutura em nuvem; see [Configurar vários sites da nuvem ou armazenamentos](https://devdocs.magento.com/cloud/project/project-multi-sites.html) no _guia Commerce Cloud_.


### Solução de problemas

- Se seus sites em francês e alemão retornarem 404s, mas seu administrador carregar, certifique-se de concluir [Etapa 6: Adicionar o código de armazenamento ao URL base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se todos os URLs retornarem 404s, certifique-se de reiniciar seu servidor da Web.
- Se o Administrador não funcionar corretamente, certifique-se de configurar seus hosts virtuais corretamente.
