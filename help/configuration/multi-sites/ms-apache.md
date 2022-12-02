---
title: Configurar vários sites com o Apache
description: Siga este tutorial para configurar vários sites com o Apache.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---


# Configurar vários sites com o Apache

Presumimos que:

Se necessário, copie os `index.php` script do ponto de entrada para o site ou [exibição de loja](https://glossary.magento.com/store-view) e adicione o seguinte:

- Você está trabalhando em uma máquina de desenvolvimento (laptop, máquina virtual e assim por diante)

   Podem ser necessárias tarefas adicionais para implantar vários sites em um ambiente hospedado; consulte seu provedor de hospedagem para obter mais informações.

   Tarefas adicionais são necessárias para configurar o Adobe Commerce na infraestrutura de nuvem. Após concluir as tarefas discutidas neste tópico, consulte [Configurar vários sites da Web ou lojas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) no _Guia do Commerce on Cloud Infrastructure_.

- Você usa um host virtual por site; o arquivo de configuração do host virtual é `/etc/httpd/httpd.conf`

   Diferentes versões do Apache em diferentes sistemas operacionais configuram hosts virtuais de forma diferente. Consulte o [Documentação do Apache](https://httpd.apache.org/docs/2.4/vhosts) ou um administrador de rede, caso não tenha certeza de como configurar um host virtual.

- O software Commerce está instalado em `/var/www/html/magento2`
- Você tem dois sites diferentes do padrão:

   - `french.mysite.mg` com código de site `french` e armazenar código de exibição `fr`
   - `german.mysite.mg` com código de site `german` e armazenar código de exibição `de`

## Roteiro para configurar vários sites com o Apache

Configurar vários armazenamentos consiste nas seguintes tarefas:

1. [Configurar sites, lojas e visualizações de loja](ms-admin.md) em Admin.
1. Criar um [Host virtual do Apache](#step-2-create-apache-virtual-hosts) por site do Commerce.

## Etapa 1: Criar sites, lojas e visualizações de loja no Administrador

Consulte [Configurar vários sites, lojas e visualizações de loja no Administrador](ms-admin.md).

## Etapa 2: Criar hosts virtuais Apache

Esta seção discute como definir valores para `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` uso da variável do servidor Apache `SetEnvIf` em um host virtual.

Para obter mais informações sobre `SetEnvIf`, consulte:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Para criar hosts virtuais Apache**:

1. Como um usuário com `root` , abra o arquivo de configuração do host virtual em um editor de texto.

   Por exemplo, abra `/etc/httpd/conf/httpd.conf`

1. Localize a seção que começa com `<VirtualHost *:80>`.
1. Crie os seguintes hosts virtuais após qualquer host virtual existente:

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. Salve as alterações em `httpd.conf` e saia do editor de texto.
1. Reinicie o Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Verificar o site

A menos que você tenha o DNS configurado para os URLs das suas lojas, é necessário adicionar uma rota estática ao host em seu `hosts` arquivo:

1. Localize seu sistema operacional `hosts` arquivo.
1. Adicione a rota estática no formato :

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
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
>- Tarefas adicionais são necessárias para configurar o Adobe Commerce na infraestrutura em nuvem; see [Configurar vários sites da nuvem ou armazenamentos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) no _Guia do Commerce on Cloud Infrastructure_.


### Solução de problemas

- Se seus sites em francês e alemão retornarem 404s, mas seu administrador carregar, certifique-se de concluir [Etapa 6: Adicionar o código de armazenamento ao URL base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se todos os URLs retornarem 404s, certifique-se de reiniciar seu servidor da Web.
- Se o Administrador não funcionar corretamente, certifique-se de configurar seus hosts virtuais corretamente.
