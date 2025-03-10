---
title: Requisitos do sistema
description: Use esta referência para identificar as dependências de software necessárias que foram testadas com as versões do Adobe Commerce.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 0d8dcfd7064488787ddd0ff54c82c77f3e4d1cfb
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# Requisitos do sistema

A seguir é apresentado um resumo das dependências de software e dos serviços testados para Adobe Commerce.

Existem algumas diferenças nas dependências do Commerce na nuvem. O suporte à versão do serviço e à compatibilidade do Adobe Commerce na nuvem é determinado pelos serviços testados e implantados nos ambientes de nuvem hospedados e, às vezes, difere das versões compatíveis com implantações locais do Adobe Commerce. Por exemplo, o Elasticsearch 7.17 é compatível com o Commerce 2.4.4 para implantações locais, mas o OpenSearch 1 é compatível com o 2.4.4 Adobe Commerce na nuvem.

>[!NOTE]
>
>Os requisitos do sistema se aplicam apenas às versões lançadas do Adobe Commerce. As versões do Beta ou de acesso antecipado não estão incluídas. Consulte as [notas de versão](../release/release-notes/overview.md) para saber mais sobre as versões mais recentes do Adobe Commerce.

As tabelas a seguir mostram versões de dependências de software de terceiros que a Adobe testou com versões específicas do Adobe Commerce.

O Adobe só oferece suporte à combinação dos requisitos de sistema descritos nas tabelas a seguir. Por exemplo, 2.4.5 é totalmente testado com MariaDB 10.4. A Adobe recomenda atualizar para MariaDB 10.4 antes de atualizar para a versão 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

O [modelo do Commerce na Nuvem](https://github.com/magento/magento-cloud) fornece uma configuração padrão para serviços compatíveis com uma versão específica do Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Os serviços e as versões estão definidos no [arquivo `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). A seguir está a configuração de serviço padrão para o Commerce 2.4.6 na infraestrutura em nuvem:

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

Consulte [Configurar serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) no guia do _Commerce on Cloud Infrastructure_.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Configurações do PHP

Há configurações específicas do PHP, como a configuração `memory_limit`, que podem ajudá-lo a evitar problemas comuns ao usar o Adobe Commerce. Consulte [Configurações PHP necessárias](prerequisites/php-settings.md).

Para obter orientações sobre a configuração da nuvem, consulte [configurações do PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) no guia _Commerce na Infraestrutura da Nuvem_.

### OPcache do PHP

É recomendável verificar se o [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) está habilitado por motivos de desempenho. O OPcache está habilitado em muitas distribuições PHP. A extensão `opcache` é instalada por padrão na infraestrutura do Commerce na nuvem.

Para configurações no local, verifique se o PHP OPcache está instalado, consulte [configurações do PHP](prerequisites/php-settings.md). Ou, para obter orientação específica sobre configurações de desempenho, consulte as recomendações de software para [configurações de PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) no guia _Práticas recomendadas de desempenho_.

Se você precisar instalar o OPcache separadamente, consulte a [documentação do OPcache do PHP](https://www.php.net/manual/en/opcache.setup.php).

### Controle do processo PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (como uma ferramenta de linha de comando).

### Extensões PHP

As [instruções de instalação do PHP](prerequisites/php-settings.md) incluem uma etapa para instalar essas extensões.

>[!TIP]
>
>Para extensões PHP na infraestrutura da nuvem, consulte [Habilitar extensões PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) no guia _Commerce na infraestrutura da nuvem_.

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

A tabela a seguir mostra as extensões compatíveis do PHP ao implantar o Adobe Commerce na plataforma na nuvem.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Consulte a [documentação oficial do PHP](https://www.php.net/manual/en/extensions.php) para obter detalhes sobre a instalação.

>[!ENDTABS]

## Diversos

Esta seção descreve o suporte e a compatibilidade para todos os outros tipos de software necessário e opcional.

>[!NOTE]
>
>Os seguintes requisitos se aplicam à versão de patch 2.4.x mais recente do Adobe Commerce. Quando pertinente, são fornecidas orientações sobre a infraestrutura do Commerce na nuvem.

### Navegadores

Loja e Administrador:

- Microsoft Edge (versão principal mais recente e anterior)
- Firefox (versão principal mais recente e anterior; qualquer sistema operacional)
- Chrome (versão principal mais recente e anterior; qualquer sistema operacional)
- Safari (versão principal mais recente e anterior; somente macOS)
- Safari para iOS (versão principal mais recente e anterior, para loja)
- Chrome para Android (versão principal mais recente e anterior, para loja)

### Servidor de email

Mail Transfer Agent (MTA) ou um servidor SMTP. A infraestrutura do Commerce na nuvem usa o [serviço de email SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Memória

A atualização dos aplicativos e extensões obtidos da Commerce Marketplace e de outras fontes pode exigir até 2 GB de RAM. Se você estiver usando um sistema com menos de 2 GB de RAM, crie um [arquivo de troca](https://support.magento.com/hc/en-us/articles/360032980432); caso contrário, a atualização poderá falhar.

### Sistemas operacionais (Linux x86-64)

Distribuições Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e similares. O Microsoft Windows e o macOS não são compatíveis.

O Adobe Commerce requer as seguintes ferramentas do sistema para algumas operações:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- Um certificado de segurança válido é necessário para HTTPS.
- Certificados SSL autoassinados não são compatíveis.
- Requisito de Segurança da Camada de Transporte (TLS) - PayPal e `repo.magento.com` exigem TLS 1.2 ou posterior.

Para obter a infraestrutura do Commerce na nuvem, consulte a [Configuração do Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) no guia do _Commerce na Infraestrutura da Nuvem_.

### Xdebug

Para o Adobe Commerce, use o [php_xdebug 2.5.x](https://xdebug.org/download) ou posterior (somente ambientes de desenvolvimento; pode ter um efeito adverso no desempenho).

Para o Adobe Commerce na nuvem, consulte [Configurar Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) no guia do _Commerce na infraestrutura da nuvem_.

>[!NOTE]
>
>Há um problema conhecido com o `xdebug` que pode afetar as instalações do Adobe Commerce ou o acesso à loja ou ao Administrador após a instalação. Consulte [Problema conhecido que afeta a instalação de `xdebug`](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) na _Base de Dados de Conhecimento de Suporte da Commerce_.
