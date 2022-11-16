---
title: Configurar o aplicativo
description: Saiba mais sobre a configuração pós-instalação necessária para implantações locais do Adobe Commerce e Magento Open Source.
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---


# Configurar o aplicativo

Agora que você terminou de instalar o Adobe Commerce ou o Magento Open Source, é necessário configurá-lo. Este tópico fornece algumas configurações recomendadas.

## Configurar o cron

O UNIX task scheduler, cron, é essencial para as operações diárias do aplicativo. Ele programa coisas como reindexação, boletins informativos, e-mails e mapas de sites. A *crontab* é uma configuração cron.

Você deve instalar os serviços Adobe Commerce e Magento Open Source no *crontab* ou algumas funcionalidades principais (e algumas extensões de terceiros) não funcionam corretamente.

Para obter mais informações sobre o cron, incluindo como remover um crontab e executar o cron a partir da linha de comando, consulte [Configurar e executar o cron](../../configuration/cli/configure-cron-jobs.md).

## Configurações e recomendações de segurança

Após a instalação, recomendamos o seguinte:

* Certifique-se de que a propriedade e as permissões do arquivo estejam definidas corretamente
* Recomendamos [alteração do URI de administrador padrão](../tutorials/admin-uri.md) from `admin` para outra coisa
* Certifique-se de que o [`X-Frame-Option` Cabeçalho HTTP](../../configuration/security/xframe-options.md) for definida corretamente.
* Tome precauções contra script entre sites (XSS) ao [como proteger seus modelos](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Se você tiver instalado o [clonagem do repositório GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), certifique-se de incluir somente arquivos e pastas necessários para o ambiente de produção ao implantar o aplicativo. Arquivos e pastas que não são necessários podem expor riscos de segurança.

## Ativar regravações do servidor Apache

Se você usar o servidor da Web Apache, precisará ativar as substituições de servidor para as páginas para serem exibidas corretamente. Caso contrário, você verá páginas sem estilos e outros problemas.

[Seção sobre regravações do servidor Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Armazenamento em cache em um ambiente com vários nós da Web

Se você tiver vários nós da Web, *cannot* use o armazenamento em cache de arquivos padrão do aplicativo porque não há sincronização entre nós da Web. Em outras palavras, a atividade em um nó da Web é gravada somente no sistema de arquivos desse nó da Web. A atividade subsequente, se executada em outro nó da Web, pode resultar na gravação de arquivos desnecessários ou resultar em erros.

Em vez disso, use [Redis](../../configuration/cache/config-redis.md) para ambas as [cache](https://glossary.magento.com/cache) e o cache da página.

## Configurações do servidor

Esta seção discute brevemente as configurações que recomendamos considerar para o servidor no qual o aplicativo é executado. Algumas dessas configurações não estão diretamente relacionadas ao aplicativo; são fornecidas somente como sugestões.

### Rotação de log

O UNIX `logrotate` O utilitário permite administrar sistemas que geram um grande número de arquivos de log. Ele permite a rotação, compactação, remoção e envio automático de arquivos de log. Cada arquivo de log pode ser manipulado diariamente, semanalmente, mensalmente ou quando o arquivo de log excede um tamanho especificado.

Para obter mais informações, consulte um dos seguintes:

* [Como: O tutorial de comando de rotação de log mais avançado com dez exemplos](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Troca de Pilhas](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` página principal](https://linuxconfig.org/logrotate-8-manual-page)

### Configurar regras de iptables para permitir que vários serviços se comuniquem

Caso tenha um ou vários servidores, você deve abrir portas no firewall para permitir que os serviços se comuniquem. Por exemplo, se você usar o mecanismo de pesquisa Solr com o Adobe Commerce, deverá habilitá-lo para se comunicar com o servidor da Web. Se você tiver vários nós da Web, você deverá habilitá-los para se comunicar uns com os outros.

Mais informações:

* Ubuntu: [Página de documentação do Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [Tutorial do CentOS](https://wiki.centos.org/HowTos/Network/IPTables).

### Regras de segurança aprimoradas para Linux (SELinux)

Não temos uma recomendação para você usar o SELinux; no entanto, se você usá-lo, deverá configurar os serviços para se comunicar entre si de forma semelhante à configuração de iptables.

Mais informações:

* Ubuntu: [Manual do Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [Wiki do CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configurar um servidor de e-mail

O Adobe Commerce e o Magento Open Source exigem um servidor de e-mail. Não recomendamos um determinado servidor, mas você pode tentar qualquer um dos seguintes procedimentos:

* Postfix do CentOS ([Tutorial para Oceano digital](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [Documentação do CentOS](https://www.centos.org))
* Postfix do Ubuntu ([Tutorial para Oceano digital](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Documentação do Ubuntu](https://help.ubuntu.com/community/MailServer))

### Refine o mecanismo de pesquisa para melhorar o desempenho:

Elasticsearch ou OpenSearch é necessário para todas as instalações a partir da versão 2.4.0.

* [Instalar e configurar o mecanismo de pesquisa](../../configuration/search/overview-search.md)

### Configurar uma fila de mensagens

Desde a versão 2.3.0, o Adobe Commerce e o Magento Open Source incluem a funcionalidade de fila de mensagens. Em versões anteriores, está disponível somente para o Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Configurações somente para Adobe Commerce

Você pode configurar o seguinte somente se usar o Adobe Commerce:

* [Dividir bancos de dados para check-out, gerenciamento de pedidos e outras tabelas de banco de dados](../../configuration/storage/multi-master.md)
