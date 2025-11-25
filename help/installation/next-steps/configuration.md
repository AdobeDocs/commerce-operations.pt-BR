---
title: Configurar o aplicativo
description: Saiba mais sobre a configuração pós-instalação necessária para implantações locais do Adobe Commerce.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Configurar o aplicativo

Agora que você terminou de instalar o Adobe Commerce, é necessário configurá-lo. Este tópico fornece algumas definições de configuração recomendadas.

## Configurar cron

O programador de tarefas do UNIX, o cron, é essencial para as operações diárias do aplicativo. Ele agenda itens como reindexação, boletins informativos, emails e mapas de site. Um *crontab* é uma configuração cron.

Você deve instalar os serviços do Adobe Commerce no *crontab* ou algumas funcionalidades principais (e algumas extensões de terceiros) não funcionam corretamente.

Para obter mais informações sobre cron, incluindo como remover um crontab e executar cron a partir da linha de comando, consulte [Configurar e executar cron](../../configuration/cli/configure-cron-jobs.md).

## Configurações e recomendações de segurança

Após a instalação, recomendamos o seguinte:

* Verifique se a propriedade e as permissões do seu arquivo estão definidas [corretamente](../prerequisites/file-system/configure-permissions.md)
* Recomendamos [alterar o URI de Administrador padrão](../tutorials/admin-uri.md) de `admin` para algo diferente
* Verifique se o cabeçalho HTTP [`X-Frame-Option`](../../configuration/security/xframe-options.md) está definido corretamente.
* Tome precauções contra script entre sites (XSS) ao [proteger seus modelos](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting)

Se você instalou o [clonando o repositório GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository), certifique-se de incluir somente os arquivos e pastas necessários para o ambiente de produção ao implantar o aplicativo. Os arquivos e pastas que não forem necessários poderão expor riscos à segurança.

## Habilitar regravações do servidor Apache

Se você usa o servidor Web Apache, deve ativar as regravações de servidor para que as páginas sejam exibidas corretamente. Caso contrário, você verá páginas sem estilos e outros problemas.

[A seção sobre regravações do servidor Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Armazenamento em cache em um ambiente com vários nós da Web

Se você tiver vários nós da Web, *não poderá* usar o cache de arquivos padrão do aplicativo porque não há sincronização entre nós da Web. Em outras palavras, a atividade em um nó da Web é gravada somente no sistema de arquivos desse nó da Web. A atividade subsequente, se executada em outro nó da Web, pode resultar na gravação de arquivos desnecessários ou em erros.

Em vez disso, use [Redis](../../configuration/cache/config-redis.md) para o cache padrão e o cache de páginas.

## Configurações do servidor

Esta seção discute brevemente as configurações que recomendamos considerar para o servidor no qual o aplicativo é executado. Algumas dessas configurações não estão diretamente relacionadas ao aplicativo; elas são fornecidas somente como sugestões.

### Rotação de logs

O utilitário UNIX `logrotate` permite administrar sistemas que geram um grande número de arquivos de log. Ele permite rotação, compactação, remoção e envio automático de arquivos de registro. Cada arquivo de log pode ser manipulado diariamente, semanalmente, mensalmente ou quando o arquivo de log excede um tamanho especificado.

Para obter mais informações, consulte uma das seguintes opções:

* [ComoFazer: o último tutorial do comando de rotação de log com dez exemplos](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Empilhar Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` página do manual](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>As seguintes informações de disponibilidade se aplicam aos projetos do Adobe Commerce na infraestrutura em nuvem:
>
>* Os ambientes iniciais não têm rotação de log.
>
>* Não é possível configurar a rotação de logs em ambientes de Integração Pro. Você deve implementar uma solução/script personalizado e [configurar seu cron](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) para executar o script conforme necessário.

### Configurar regras do iptables para permitir que vários serviços se comuniquem

Se você tiver um servidor ou muitos, deve abrir portas no firewall para habilitar os serviços para se comunicar. Por exemplo, se você usar o mecanismo de pesquisa Solr com o Adobe Commerce, será necessário habilitá-lo para se comunicar com o servidor Web. Se você tiver vários nós da Web, é necessário habilitá-los para se comunicar.

Mais informações:

* Ubuntu: [página da documentação do Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [instruções do CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Regras do SELinux (Security Enhanced Linux)

Não temos uma recomendação para usar ou não o SELinux; no entanto, se você usá-lo, deverá configurar os serviços para que se comuniquem entre si de forma semelhante à configuração do iptables.

Mais informações:

* Ubuntu: [Manual Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [wiki do CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configurar um servidor de email

O Adobe Commerce requer um servidor de e-mail. Não recomendamos um servidor específico, mas você pode tentar qualquer um dos seguintes procedimentos:

* Postfix para CentOS ([Tutorial do Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [Documentação do CentOS](https://www.centos.org))
* Postfix para Ubuntu ([Tutorial do Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Documentação do Ubuntu](https://help.ubuntu.com/community/MailServer))

### Refine o mecanismo de pesquisa para melhorar o desempenho:

O Elasticsearch ou OpenSearch é necessário para todas as instalações a partir da versão 2.4.0.

* [Instalar e configurar o mecanismo de pesquisa](../../configuration/search/overview-search.md)

### Configurar uma fila de mensagens

Desde a versão 2.3.0, o Adobe Commerce inclui a funcionalidade de fila de mensagens. Em versões anteriores, ele está disponível somente para o Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Configurações somente para o Adobe Commerce

Você pode configurar o seguinte somente se usar o Adobe Commerce:

* [Dividir bancos de dados para check-out, gerenciamento de pedidos e outras tabelas de banco de dados](../../configuration/storage/multi-master.md)
