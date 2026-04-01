---
title: Requisitos do sistema
description: Saiba mais sobre dependências de software e requisitos de sistema para o Adobe Commerce. Descubra as configurações testadas para garantir compatibilidade com seu ambiente de implantação.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 2657c83d5467e603a681521886e80592e3b335aa
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# Requisitos do sistema

A seguir é apresentado um resumo das dependências de software e dos serviços testados para Adobe Commerce.

Existem algumas diferenças nas dependências do Commerce na nuvem. O suporte à versão do serviço e à compatibilidade do Adobe Commerce na nuvem é determinado pelos serviços testados e implantados nos ambientes de nuvem hospedados e, às vezes, difere das versões compatíveis com implantações locais do Adobe Commerce. Por exemplo, o Elasticsearch 7.17 é compatível com o Commerce 2.4.4 para implantações locais, mas o OpenSearch 1 é compatível com o 2.4.4 Adobe Commerce na nuvem.

>[!NOTE]
>
>As tabelas de requisitos do sistema identificam as versões específicas do Adobe Commerce cobertas, incluindo quaisquer versões beta ou de acesso antecipado explicitamente rotuladas. Consulte as [notas de versão](../release/release-notes/overview.md) para saber mais sobre as versões mais recentes publicadas do Adobe Commerce.

As tabelas a seguir mostram versões de dependências de software de terceiros que a Adobe testou com versões específicas do Adobe Commerce.

O Adobe só oferece suporte à combinação dos requisitos de sistema descritos nas tabelas a seguir. Por exemplo, 2.4.5 é totalmente testado com MariaDB 10.4. A Adobe recomenda atualizar para MariaDB 10.4 antes de atualizar para a versão 2.4.5.

Para garantir um processo de atualização tranquilo e evitar falhas de implantação, a Adobe recomenda atualizar as versões do RabbitMQ de forma incremental. Por exemplo, ao atualizar da versão 3.8 para a 4.1, você deve primeiro atualizar da 3.8 para a 3.9, depois da 3.9 para a 3.10 e assim por diante. Somente depois de atingir a versão 3.13 é que você deve prosseguir com a atualização para a versão 4.1.

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

Consulte [Configurar serviços](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) no guia do *Commerce on Cloud Infrastructure*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Configurações do PHP

Há configurações específicas do PHP, como a configuração `memory_limit`, que podem ajudá-lo a evitar problemas comuns ao usar o Adobe Commerce. Consulte [Configurações PHP necessárias](prerequisites/php-settings.md).

Para obter orientações sobre a configuração da nuvem, consulte [configurações do PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) no guia *Commerce na Infraestrutura da Nuvem*.

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

PHPUnit v9 (como uma ferramenta de linha de comando).

### Extensões PHP

As [instruções de instalação do PHP](prerequisites/php-settings.md) incluem uma etapa para instalar essas extensões.

>[!TIP]
>
>Para extensões PHP na infraestrutura da nuvem, consulte [Habilitar extensões PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) no guia _Commerce na infraestrutura da nuvem_.

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

Mail Transfer Agent (MTA) ou um servidor SMTP. A infraestrutura do Commerce na nuvem usa o [serviço de email SendGrid](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memória

A atualização dos aplicativos e extensões obtidos da Commerce Marketplace e de outras fontes pode exigir até 2 GB de RAM. Se você estiver usando um sistema com menos de 2 GB de RAM, crie um [arquivo de troca](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Caso contrário, a atualização poderá falhar.

### Sistemas operacionais (Linux x86-64)

Distribuições Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e similares.

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

Para obter a infraestrutura do Commerce na nuvem, consulte a [Configuração do Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) no guia do *Commerce na Infraestrutura da Nuvem*.

### Xdebug

Para o Adobe Commerce, use o [php_xdebug 2.5.x](https://xdebug.org/download) ou posterior (somente ambientes de desenvolvimento; pode ter um efeito adverso no desempenho).

Para o Adobe Commerce na nuvem, consulte [Configurar Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) no guia do *Commerce na infraestrutura da nuvem*.

>[!NOTE]
>
>Há um problema conhecido com o `xdebug` que pode afetar as instalações do Adobe Commerce ou o acesso à loja ou ao Administrador após a instalação. Consulte [Problema conhecido que afeta a instalação de `xdebug`](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) na _Base de Dados de Conhecimento de Suporte da Commerce_.


<!-- Last updated from includes: 2026-03-13 12:40:18 -->
