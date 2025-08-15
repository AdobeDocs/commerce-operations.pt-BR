---
title: Configurar vários sites com o Apache
description: Siga este tutorial para configurar vários sites com o Apache.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Configurar vários sites com o Apache

Presumimos que:

Se necessário, copie o script de ponto de entrada `index.php` existente para a exibição do site ou da loja e adicione o seguinte a ele:

- Você está trabalhando em uma máquina de desenvolvimento (laptop, máquina virtual etc.)

  Tarefas adicionais podem ser necessárias para implantar vários sites em um ambiente hospedado; verifique com seu provedor de hospedagem para obter mais informações.

  Tarefas adicionais são necessárias para configurar a Adobe Commerce na infraestrutura em nuvem. Após concluir as tarefas discutidas neste tópico, consulte [Configurar vários sites ou lojas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) no _guia do Commerce na Infraestrutura da Nuvem_.

- Você usa um host virtual por site; o arquivo de configuração do host virtual é `/etc/httpd/httpd.conf`

  Diferentes versões do Apache em diferentes sistemas operacionais configuram hosts virtuais de forma diferente. Consulte a [Documentação do Apache](https://httpd.apache.org/docs/2.4/vhosts) ou um administrador de rede se não tiver certeza de como configurar um host virtual.

- O software Commerce está instalado em `/var/www/html/magento2`
- Você tem dois sites diferentes do padrão:

   - `french.mysite.mg` com código de site `french` e código de exibição de armazenamento `fr`
   - `german.mysite.mg` com código de site `german` e código de exibição de armazenamento `de`

## Roteiro para configurar vários sites com o Apache

A configuração de vários armazenamentos consiste nas seguintes tarefas:

1. [Configurar sites, lojas e exibições de loja](ms-admin.md) no Administrador.
1. Crie um [host virtual Apache](#step-2-create-apache-virtual-hosts) por site do Commerce.

## Etapa 1: criar sites, lojas e visualizações de loja no Administrador

Consulte [Configurar vários sites, lojas e exibições de loja no Administrador](ms-admin.md).

## Etapa 2: Criar hosts virtuais do Apache

Esta seção discute como definir valores para `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` usando a variável de servidor Apache `SetEnvIf` em um host virtual.

Para obter mais informações sobre `SetEnvIf`, consulte:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Para criar hosts virtuais Apache**:

1. Como um usuário com privilégios `root`, abra o arquivo de configuração do host virtual em um editor de texto.

   Por exemplo, abrir `/etc/httpd/conf/httpd.conf`

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
1. Reiniciar o Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

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
