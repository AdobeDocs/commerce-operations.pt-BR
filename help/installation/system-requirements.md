---
title: Requisitos do sistema
description: Saiba mais sobre dependências de software e requisitos de sistema para o Adobe Commerce. Consulte as configurações testadas para compatibilidade com seu ambiente de implantação.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
last-update: 2026-09-18
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1614'
ht-degree: 0%
---
# Requisitos do sistema

As informações a seguir resumem as dependências de software e os serviços testados para Adobe Commerce.

As dependências de software da infraestrutura Adobe Commerce na nuvem são diferentes daquelas para implantações locais. O Adobe determina as versões de serviço compatíveis e a compatibilidade com base nos serviços testados e implantados em ambientes de nuvem hospedados. Essas versões às vezes diferem das compatíveis com implantações locais.

>[!IMPORTANT]
>
>As tabelas de requisitos do sistema listam as versões do Adobe Commerce às quais se aplicam, incluindo versões rotuladas como beta ou acesso antecipado.
>Consulte as [notas de versão](../release/release-notes/overview.md) para obter as versões mais recentes do Commerce publicadas.
>
>Quando as versões do serviço não correspondem à configuração compatível com a versão do Commerce, o comportamento pode ser diferente do que o Adobe pode reproduzir no teste. O Suporte da Adobe pode solicitar que você alinhe seu ambiente com uma configuração com suporte antes de investigar, solucionar problemas ou validar o comportamento relatado. Depois de alinhar o ambiente, o Suporte da Adobe pode continuar a investigação.

As tabelas a seguir mostram versões de dependências de software de terceiros que a Adobe testou com versões específicas do Adobe Commerce.

O Adobe oferece suporte apenas às combinações de requisitos do sistema listadas nas tabelas a seguir. O Adobe não valida ou aceita configurações que não correspondem a uma combinação listada. Por exemplo, o Adobe Commerce 2.4.9 é testado com MariaDB 12.3. Atualize para MariaDB 12.3 antes de atualizar para 2.4.9.

## Requisitos do sistema para as versões mais recentes do Commerce

As tabelas a seguir resumem os requisitos de sistema para a versão mais recente de todas as versões compatíveis do Commerce. A Adobe recomenda que todos os clientes atualizem para essas versões.

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

O [modelo do Commerce na Nuvem](https://github.com/magento/magento-cloud) fornece uma configuração padrão para serviços compatíveis com a versão mais recente do Commerce para cada linha de versão.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

O [`services.yaml` arquivo](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) define os serviços e as versões padrão.
Consulte [Configurar serviços](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) no guia do *Commerce on Cloud Infrastructure*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

**O MySQL 8.0 chegou ao fim do suporte (EOS) em 30 de abril de 2026.**
Após essa data, o Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou suporte para versões do MySQL lançadas após o MySQL 8.0.
A Adobe não valida ou oferece suporte a versões principais mais recentes do MySQL para essas versões do Commerce.
Se você executar as versões 2.4.7, 2.4.6, 2.4.5 ou 2.4.4 do Adobe Commerce no local, a Adobe recomenda que você migre seus servidores de banco de dados para uma versão compatível do MariaDB.

Os clientes do Adobe Commerce na nuvem devem manter as dependências da plataforma nas versões compatíveis. Consulte [Dependências da plataforma](../release/lifecycle-policy.md#platform-dependencies) na política de ciclo de vida.

O **Elasticsearch 7.17 chegou ao Fim do Suporte (EOS) em 15 de janeiro de 2026.**
Após essa data, o Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou suporte para versões do Elasticsearch lançadas após o Elasticsearch 7.
A Adobe não valida ou oferece suporte a versões mais recentes da Elasticsearch para essas versões do Commerce.
Se você executar as versões 2.4.6, 2.4.5 ou 2.4.4 do Adobe Commerce no local, a Adobe recomenda que você migre sua infraestrutura de pesquisa para uma versão compatível do OpenSearch.

>[!ENDTABS]

## Requisitos do sistema para a versão 2.4.10-alpha do Commerce

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

{{$include /help/_includes/templated/cloud-requirements-table-alpha.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-alpha.md}}

>[!ENDTABS]

## Requisitos do sistema para versões anteriores do Commerce

As tabelas a seguir listam os requisitos de sistema para versões do Adobe Commerce, incluindo aqueles em suporte estendido. Use essas tabelas somente para referência. A Adobe não recomenda usar versões não compatíveis de dependências de software. Antes que o Suporte da Adobe investigue, solucione problemas ou valide o comportamento relatado, você deve alinhar seu ambiente a uma configuração compatível.

>[!NOTE]
>
>O Adobe Commerce 2.4.6 está no [suporte estendido](../release/lifecycle-policy.md#extended-support) até **30 de agosto de 2027**, seguido por um [período de transição somente de segurança](../release/lifecycle-policy.md#security-only-transitional-period) até **31 de maio de 2028**. Essas provisões estão disponíveis somente para clientes do Adobe Commerce. Eles não estendem o suporte para dependências de terceiros, como MySQL.
>
>Se você executar o Adobe Commerce na Nuvem, deverá atualizar para uma versão com suporte ou migrar para o [!DNL Adobe Commerce as a Cloud Service] antes dos **requisitos e prazos de segurança do [&#x200B; do** de 1 de junho de 2028](../release/security-enforcement-policy.md). Consulte a tabela [fim das datas de suporte](../release/lifecycle-policy.md#end-of-support-dates) para obter as datas do ciclo de vida completo.
>
>A tabela é recolhida para minimizar o comprimento deste artigo. Selecione o cabeçalho para expandi-lo.

+++Requisitos para versões anteriores

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

O [modelo do Commerce na Nuvem](https://github.com/magento/magento-cloud) fornece uma configuração padrão para serviços compatíveis com uma versão específica do Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

O [`services.yaml` arquivo](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) define os serviços e as versões padrão.
Consulte [Configurar serviços](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) no guia do *Commerce on Cloud Infrastructure*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**O MySQL 8.0 chegou ao fim do suporte (EOS) em 30 de abril de 2026.**
Após essa data, o Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou suporte para versões do MySQL lançadas após o MySQL 8.0.
A Adobe não valida ou oferece suporte a versões principais mais recentes do MySQL para essas versões do Commerce.
Se você executar as versões 2.4.7, 2.4.6, 2.4.5 ou 2.4.4 do Adobe Commerce no local, a Adobe recomenda que você migre seus servidores de banco de dados para uma versão compatível do MariaDB.

Os clientes do Adobe Commerce na nuvem devem manter as dependências da plataforma nas versões compatíveis. Consulte [Dependências da plataforma](../release/lifecycle-policy.md#platform-dependencies) na política de ciclo de vida.

O **Elasticsearch 7.17 chegou ao Fim do Suporte (EOS) em 15 de janeiro de 2026.**
Após essa data, o Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou suporte para versões do Elasticsearch lançadas após o Elasticsearch 7.
A Adobe não valida ou oferece suporte a versões mais recentes da Elasticsearch para essas versões do Commerce.
Se você executar as versões 2.4.6, 2.4.5 ou 2.4.4 do Adobe Commerce no local, a Adobe recomenda que você migre sua infraestrutura de pesquisa para uma versão compatível do OpenSearch.

>[!ENDTABS]

+++

## Configurações do PHP

Defina as configurações do PHP, como `memory_limit`, para ajudar a evitar problemas comuns ao usar o Adobe Commerce. Consulte [Configurações PHP necessárias](prerequisites/php-settings.md).

Para obter orientações sobre a configuração da nuvem, consulte [configurações do PHP](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/app/php-settings) no guia *Commerce na Infraestrutura da Nuvem*.

### OPcache do PHP

A Adobe recomenda verificar se o [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) está habilitado para melhorar o desempenho. Muitas distribuições PHP habilitam o OPcache.

- **Para o Adobe Commerce em implantações de infraestrutura na nuvem**, a extensão `opcache` é instalada por padrão.
- **Para implantações locais do Adobe Commerce:**
  - [Verifique se a extensão OPcache do PHP está instalada](prerequisites/php-settings.md#verify-php-is-installed).
  - Para obter orientações específicas sobre configurações de desempenho, consulte as recomendações de software para [configurações de PHP](../performance/software.md#php-settings) no guia *Práticas recomendadas de desempenho*.


Se você precisar instalar o OPcache separadamente, consulte a [documentação do OPcache do PHP](https://www.php.net/manual/en/opcache.setup.php).

### Controle do processo PHP

{{php-process-control}}

### PHPUnit

A versão principal PHPUnit compatível depende da versão do Adobe Commerce. O Adobe testa 2.4.9 com PHPUnit 12, 2.4.8-p5 com PHPUnit 10 e 2.4.7-p10 até 2.4.4-p18 com PHPUnit 9. Instale o PHPUnit como uma ferramenta de linha de comando na versão principal que corresponde às configurações testadas pela Adobe para o seu lançamento.

### Extensões PHP

As [instruções de instalação do PHP](prerequisites/php-settings.md) incluem uma etapa para instalar essas extensões.

>[!TIP]
>
>Para extensões PHP na infraestrutura da nuvem, consulte [Habilitar extensões PHP](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) no guia _Commerce na infraestrutura da nuvem_.

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

A tabela a seguir mostra as extensões compatíveis do PHP ao implantar o Adobe Commerce na plataforma na nuvem.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Consulte a [documentação oficial do PHP](https://www.php.net/manual/en/extensions.php) para obter detalhes sobre a instalação.

>[!ENDTABS]

## Outros requisitos de software

Esta seção descreve o suporte e a compatibilidade para todos os outros tipos de software necessário e opcional.

>[!NOTE]
>
>Os seguintes requisitos se aplicam à versão de patch 2.4.x mais recente do Adobe Commerce. Quando pertinente, são fornecidas orientações sobre a infraestrutura do Commerce na nuvem.

### Navegadores

O Adobe Commerce é compatível com as versões principais mais recentes e anteriores dos seguintes navegadores para a loja e o administrador, exceto quando observado:

- Microsoft Edge
- Firefox (qualquer sistema operacional)
- Chrome (qualquer sistema operacional)
- Safari (somente macOS)
- Safari para iOS (somente loja)
- Chrome for Android (somente vitrine)

### Servidor de email

Mail Transfer Agent (MTA) ou um servidor SMTP. A infraestrutura do Commerce na nuvem usa o [serviço de email SendGrid](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memória

A atualização de aplicativos e extensões da Commerce Marketplace e de outras fontes pode exigir até 2 GB de RAM. Se o sistema tiver menos de 2 GB de RAM, crie um [arquivo de troca](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Sem um arquivo de troca, a atualização poderá falhar.

### Sistemas operacionais (Linux x86-64)

Distribuições Linux, como Red Hat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e similares.

O Microsoft Windows e o macOS **não** são suportados.

O Adobe Commerce requer as seguintes ferramentas do sistema para algumas operações:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- Um certificado de segurança válido é necessário para HTTPS.
- Certificados SSL autoassinados não são compatíveis.
- Requisito de Segurança da Camada de Transporte (TLS) - PayPal e `repo.magento.com` exigem TLS 1.2 ou posterior.

Para obter a infraestrutura do Commerce na nuvem, consulte a [Configuração do Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) no guia do *Commerce na Infraestrutura da Nuvem*.

### Xdebug

Somente para ambientes de desenvolvimento do Adobe Commerce, use o [php_xdebug 2.5.x](https://xdebug.org/download) ou posterior. O Xdebug pode afetar negativamente o desempenho.

Para o Adobe Commerce na nuvem, consulte [Configurar Xdebug](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/test/debug) no guia do *Commerce na infraestrutura da nuvem*.

>[!NOTE]
>
>Um problema conhecido com o Xdebug pode afetar as instalações do Adobe Commerce ou o acesso à loja ou ao administrador após a instalação. Consulte [Problema conhecido que afeta a instalação de `xdebug`](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) na _Base de Dados de Conhecimento de Suporte da Commerce_.

<!-- Last updated from includes: 2026-10-07 13:03:29 -->
