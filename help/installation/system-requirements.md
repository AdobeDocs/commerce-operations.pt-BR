---
title: Requisitos do sistema
description: Use esta referência para identificar as dependências de software necessárias que foram testadas com versões Adobe Commerce e Magento Open Source.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 4087d5f5de0bc11ce120d61a539800a3533893f0
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# Requisitos do sistema

A seguir é apresentado um resumo das dependências de software e dos serviços testados para Adobe Commerce e Magento Open Source.

Existem algumas diferenças nas dependências do Commerce na infraestrutura em nuvem. O suporte à versão do serviço e à compatibilidade do Adobe Commerce na infraestrutura em nuvem é determinado por serviços testados e implantados nos ambientes de nuvem hospedados e, às vezes, difere das versões compatíveis com implantações locais do Adobe Commerce. Por exemplo, o Elasticsearch 7.17 é compatível com o Commerce 2.4.4 para implantações locais, mas o OpenSearch 1.2 é compatível com o Commerce 2.4.4 na infraestrutura em nuvem.

As tabelas a seguir mostram versões de dependências de software de terceiros que o Adobe testou com versões específicas do Adobe Commerce e do Magento Open Source.

O Adobe suporta apenas a combinação dos requisitos de sistema descritos nas tabelas a seguir. Por exemplo, 2.4.5 é totalmente testado com MariaDB 10.4. A Adobe recomenda que você atualize para MariaDB 10.4 antes de atualizar para a versão 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

A variável [Modelo do Commerce na nuvem](https://github.com/magento/magento-cloud) O fornece uma configuração padrão para serviços compatíveis com uma versão específica do Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Os serviços e as versões são definidos em [o `services.yaml` arquivo](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). A seguir está a configuração de serviço padrão para o Commerce 2.4.6 na infraestrutura em nuvem:

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

Consulte [Configurar serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) no _Commerce na infraestrutura em nuvem_ guia.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Configurações do PHP

Há definições específicas de configuração do PHP, como a variável `memory_limit` , que pode ajudá-lo a evitar problemas comuns ao usar o Adobe Commerce e o Magento Open Source. Consulte [Configurações necessárias do PHP](prerequisites/php-settings.md).

Para obter orientação sobre a configuração na nuvem, consulte [Configurações do PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) no _Commerce na infraestrutura em nuvem_ guia.

### OPcache do PHP

É recomendável verificar se [OPcache do PHP](https://www.php.net/manual/en/intro.opcache.php) está ativado por motivos de desempenho. O OPcache está habilitado em muitas distribuições PHP. A variável `opcache` A extensão do é instalada por padrão na infraestrutura do Commerce na nuvem.

Para verificar se o PHP OPcache está instalado, consulte [Configurações do PHP](prerequisites/php-settings.md). Ou, para obter orientação específica sobre configurações de desempenho, consulte as recomendações de software para [Configurações do PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) no _Práticas recomendadas de desempenho_ guia.

Se precisar instalar o OPcache separadamente, consulte a [Documentação do PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Controle do processo PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (como uma ferramenta de linha de comando).

### Extensões PHP

A variável [instruções de instalação do PHP](prerequisites/php-settings.md) inclua uma etapa para instalar essas extensões.

>[!TIP]
>
>Para extensões PHP na infraestrutura da nuvem, consulte [Habilitar extensões PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) no _Commerce na infraestrutura em nuvem_ guia.

>[!BEGINTABS]

>[!TAB Commerce na nuvem]

A tabela a seguir mostra as extensões compatíveis do PHP ao implantar o Adobe Commerce na plataforma na nuvem.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentação oficial do PHP](https://www.php.net/manual/en/extensions.php) para obter detalhes sobre a instalação.

>[!ENDTABS]

## Diversos

Esta seção descreve o suporte e a compatibilidade para todos os outros tipos de software necessário e opcional.

>[!NOTE]
>
>Os requisitos a seguir se aplicam à versão mais recente do patch 2.4.x do Adobe Commerce e Magento Open Source. Quando pertinente, são fornecidas orientações sobre a infraestrutura do Commerce on Cloud.

### Navegadores

Loja e Administrador:

- Microsoft Edge (versão principal mais recente e anterior)
- Firefox (versão principal mais recente e anterior; qualquer sistema operacional)
- Chrome (versão principal mais recente e anterior; qualquer sistema operacional)
- Safari (versão principal mais recente e anterior; somente macOS)
- Safari para iOS (versão principal mais recente e anterior, para loja)
- Chrome para Android (versão principal mais recente e anterior, para loja)

### Servidor de email

Mail Transfer Agent (MTA) ou um servidor SMTP. A infraestrutura do Commerce na nuvem usa o [Serviço de email SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Memória

A atualização dos aplicativos e extensões obtidos do Commerce Marketplace e de outras fontes pode exigir até 2 GB de RAM. Se você estiver usando um sistema com menos de 2 GB de RAM, crie um [trocar arquivo](https://support.magento.com/hc/en-us/articles/360032980432); caso contrário, sua atualização poderá falhar.

### Sistemas operacionais (Linux x86-64)

Distribuições Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e similares. O Microsoft Windows e o macOS não são compatíveis.

O Adobe Commerce e o Magento Open Source exigem as seguintes ferramentas do sistema para algumas operações:

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
- Requisito de Segurança da camada de transporte (TLS) - PayPal e `repo.magento.com` ambos exigem TLS 1.2 ou posterior.

Para a infraestrutura do Commerce na nuvem, consulte [Configuração do Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) no _Commerce na infraestrutura em nuvem_ guia.

### Xdebug

Para Adobe Commerce e Magento Open Source, use [php_xdebug 2.5.x](https://xdebug.org/download) ou posterior (somente ambientes de desenvolvimento; pode ter um efeito adverso no desempenho).

Para o Adobe Commerce na nuvem, consulte [Configurar Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) no _Commerce na infraestrutura em nuvem_ guia.

>[!NOTE]
>
>Há um problema conhecido com o `xdebug` que podem afetar as instalações do Adobe Commerce ou Magento Open Source ou o acesso à loja ou ao Administrador após a instalação. Consulte [Problema conhecido que afeta `xdebug` instalação](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) no _Knowledge base de suporte do Commerce_.
