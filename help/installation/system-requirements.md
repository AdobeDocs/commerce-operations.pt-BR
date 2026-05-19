---
title: Requisitos do sistema
description: Saiba mais sobre dependências de software e requisitos de sistema para o Adobe Commerce. Consulte as configurações testadas para compatibilidade com seu ambiente de implantação.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: f5d0b6943b1b5ca41967c61842b73734ed41f26f
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 0%

---

# Requisitos do sistema

As informações a seguir resumem as dependências de software e os serviços testados para Adobe Commerce.

Existem algumas diferenças nas dependências do Commerce na nuvem. O suporte à versão do serviço e à compatibilidade do Adobe Commerce na nuvem é determinado pelos serviços testados e implantados nos ambientes de nuvem hospedados e, às vezes, difere das versões compatíveis com implantações locais do Adobe Commerce.

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

O [modelo do Commerce na Nuvem](https://github.com/magento/magento-cloud) fornece uma configuração padrão para serviços compatíveis com uma versão específica do Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Para a configuração padrão, os serviços e as versões são definidos no [arquivo `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Para obter mais detalhes, consulte [Configurar serviços](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) no guia *Commerce na Infraestrutura de Nuvem*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

**O MySQL 8.0 chegou ao fim do suporte (EOS) em 30 de abril de 2026.**
Após essa data, o Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou
suporte para qualquer versão do MySQL lançada após o MySQL 8.0. O Adobe não
validar ou fornecer suporte para versões principais mais recentes do MySQL neste Adobe
Linha de versão do Commerce.
Todos os clientes locais do Adobe Commerce que executam as versões 2.4.7, 2.4.6, 2.4.5, 2.4.4 são altamente
aconselhados a migrar seus servidores de banco de dados para uma versão compatível do MariaDB.

O **Elasticsearch 7.17 chegou ao Fim do Suporte (EOS) em 15 de janeiro de 2026.**
Após essa data, o Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou
suporte para qualquer versão do Elasticsearch lançada após o Elasticsearch 7. O Adobe não
validar ou fornecer suporte para versões principais mais recentes do Elasticsearch neste Adobe
Linha de versão do Commerce.
Todos os clientes locais do Adobe Commerce que executam as versões 2.4.6, 2.4.5, 2.4.4 são altamente
aconselhamos a migrar sua infraestrutura de pesquisa para uma versão compatível do OpenSearch.

>[!ENDTABS]

>[!AVAILABILITY]
>
><sup>1</sup> A compatibilidade entre o MariaDB 12.3 e o Adobe Commerce 2.4.9 será confirmada após o lançamento oficial do MariaDB 12.3, previsto para maio-junho.

## Requisitos do sistema para versões anteriores do Commerce

As tabelas a seguir listam os requisitos de sistema para versões do Adobe Commerce, incluindo aquelas em suporte estendido. Estas tabelas são fornecidas apenas para fins de referência. A Adobe não recomenda o uso de versões não compatíveis de dependências de software, e o Suporte exige que você alinhe seu ambiente a uma configuração compatível antes que possamos investigar, solucionar problemas ou validar o comportamento relatado.

>[!NOTE]
>
>A tabela é recolhida para minimizar o comprimento deste artigo. Selecione o cabeçalho para expandi-lo.

+++Requisitos para versões anteriores

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

O [modelo do Commerce na Nuvem](https://github.com/magento/magento-cloud) fornece uma configuração padrão para serviços compatíveis com uma versão específica do Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Para a configuração padrão, os serviços e as versões são definidos no [arquivo `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Para obter mais detalhes, consulte [Configurar serviços](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) no guia *Commerce na Infraestrutura de Nuvem*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**O MySQL 8.0 chegou ao fim do suporte (EOS) em 30 de abril de 2026.**
Após essa data, o Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou
suporte para qualquer versão do MySQL lançada após o MySQL 8.0. O Adobe não
validar ou fornecer suporte para versões principais mais recentes do MySQL neste Adobe
Linha de versão do Commerce.
Todos os clientes locais do Adobe Commerce que executam as versões 2.4.7, 2.4.6, 2.4.5, 2.4.4 são altamente
aconselhados a migrar seus servidores de banco de dados para uma versão compatível do MariaDB.

O **Elasticsearch 7.17 chegou ao Fim do Suporte (EOS) em 15 de janeiro de 2026.**
Após essa data, o Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 não fornecerá compatibilidade ou
suporte para qualquer versão do Elasticsearch lançada após o Elasticsearch 7. O Adobe não
validar ou fornecer suporte para versões principais mais recentes do Elasticsearch neste Adobe
Linha de versão do Commerce.
Todos os clientes locais do Adobe Commerce que executam as versões 2.4.6, 2.4.5, 2.4.4 são altamente
aconselhamos a migrar sua infraestrutura de pesquisa para uma versão compatível do OpenSearch.

>[!ENDTABS]

+++

## Configurações do PHP

Há configurações específicas do PHP, como a configuração `memory_limit`, que podem ajudá-lo a evitar problemas comuns ao usar o Adobe Commerce. Consulte [Configurações PHP necessárias](prerequisites/php-settings.md).

Para obter orientações sobre a configuração da nuvem, consulte [configurações do PHP](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/app/php-settings) no guia *Commerce na Infraestrutura da Nuvem*.

### OPcache do PHP

A Adobe recomenda verificar se o [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) está habilitado por motivos de desempenho. O OPcache está habilitado em muitas distribuições PHP.

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

Loja e Administrador:

- Microsoft Edge (versão principal mais recente e anterior)
- Firefox (versão principal mais recente e anterior em qualquer sistema operacional)
- Chrome (versão principal mais recente e anterior em qualquer sistema operacional)
- Safari (versão principal mais recente e anterior somente no macOS)
- Safari para iOS (versão principal mais recente e anterior da loja)
- Chrome para Android (versão principal mais recente e anterior da loja)

### Servidor de email

Mail Transfer Agent (MTA) ou um servidor SMTP. A infraestrutura do Commerce na nuvem usa o [serviço de email SendGrid](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memória

A atualização dos aplicativos e extensões obtidos da Commerce Marketplace e de outras fontes pode exigir até 2 GB de RAM. Se você estiver usando um sistema com menos de 2 GB de RAM, crie um [arquivo de troca](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Caso contrário, a atualização poderá falhar.

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

Para o Adobe Commerce, use o [php_xdebug 2.5.x](https://xdebug.org/download) ou posterior (somente ambientes de desenvolvimento; pode ter um efeito adverso no desempenho).

Para o Adobe Commerce na nuvem, consulte [Configurar Xdebug](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/test/debug) no guia do *Commerce na infraestrutura da nuvem*.

>[!NOTE]
>
>Há um problema conhecido com o `xdebug` que pode afetar as instalações do Adobe Commerce ou o acesso à loja ou ao Administrador após a instalação. Consulte [Problema conhecido que afeta a instalação de `xdebug`](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) na _Base de Dados de Conhecimento de Suporte da Commerce_.

<!-- Last updated from includes: 2026-05-13 16:20:40 -->
