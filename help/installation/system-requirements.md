---
title: Requisitos do sistema
description: Use esta referência para identificar as dependências de software necessárias que foram testadas com versões Adobe Commerce e Magento Open Source.
source-git-commit: 61a477ec6118e4a228ddbb956e613fa3bec9c91c
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# Requisitos do sistema

Esta tabela mostra versões de dependências de software de terceiros que o Adobe testou com versões específicas do Adobe Commerce e do Magento Open Source. O Adobe suporta apenas a combinação dos requisitos de sistema descritos na tabela a seguir.

Por exemplo, 2.4.5 é totalmente testado com MariaDB 10.4. A Adobe recomenda que você atualize para MariaDB 10.4 antes de atualizar para a versão 2.4.5.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Diversos

Esta seção descreve o suporte e a compatibilidade para todos os outros tipos de software necessário e opcional.

>[!NOTE]
>
>Os requisitos a seguir se aplicam à versão mais recente do patch 2.4.x do Adobe Commerce e Magento Open Source.

### Servidor de email

Mail Transfer Agent (MTA) ou um servidor SMTP

### Sistemas operacionais (Linux x86-64)

Distribuições Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e similares. O Microsoft Windows e o macOS não são compatíveis.

### Extensões PHP

>[!NOTE]
>
>A variável [instruções de instalação do PHP](prerequisites/php-settings.md) inclua uma etapa para instalar essas extensões.

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentação oficial do PHP](https://php.net/manual/en/extensions.php) para obter detalhes sobre a instalação.

### OPcache do PHP

Recomendamos que você verifique se [OPcache do PHP](https://php.net/manual/en/intro.opcache.php) está ativado por motivos de desempenho. O OPcache está habilitado em muitas distribuições PHP. Para verificar se ele está instalado, consulte nossa [Documentação do PHP](prerequisites/php-settings.md).

Se precisar instalá-lo separadamente, consulte a seção [Documentação do PHP OPcache](https://php.net/manual/en/opcache.setup.php).

### Configurações do PHP

Recomendamos definições específicas de configuração do PHP, como `memory_limit`, que podem evitar problemas comuns ao usar o Adobe Commerce e o Magento Open Source.

Para obter mais informações, consulte [Configurações necessárias do PHP](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (como uma ferramenta de linha de comando) 9.0.0

### RAM

A atualização dos aplicativos e extensões obtidos do Commerce Marketplace e de outras fontes pode exigir até 2 GB de RAM. Se você estiver usando um sistema com menos de 2 GB de RAM, recomendamos criar um [trocar arquivo](https://support.magento.com/hc/en-us/articles/360032980432); caso contrário, sua atualização poderá falhar.

### Dependências do sistema

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

- Um válido [certificado de segurança](https://glossary.magento.com/security-certificate) é necessário para HTTPS.
- Certificados SSL autoassinados não são compatíveis.
- Requisito de Segurança da camada de transporte (TLS) - PayPal e `repo.magento.com` ambos exigem TLS 1.2 ou posterior.

### Navegadores compatíveis

Loja e Administrador:

- Microsoft Edge (versão principal mais recente e anterior)
- Firefox (versão principal mais recente e anterior; qualquer sistema operacional)
- Chrome (versão principal mais recente e anterior; qualquer sistema operacional)
- Safari (versão principal mais recente e anterior; somente macOS)
- Safari Mobile para iPad 2, iPad Mini, iPad com Retina Display (iOS 12 ou posterior), para vitrine de desktop
- Safari Mobile para iPhone 6 ou posterior; iOS 12 ou posterior, para loja de dispositivos móveis
- Chrome para dispositivos móveis (versão principal mais recente e anterior) [Android 4 ou posterior] para loja de dispositivos móveis)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) ou posterior (somente ambientes de desenvolvimento; pode ter um efeito adverso no desempenho)

>[!NOTE]
>
>Há um problema conhecido com o `xdebug` que podem afetar as instalações do Adobe Commerce ou Magento Open Source ou o acesso à loja ou ao Administrador após a instalação. Para obter detalhes, consulte [Problema conhecido com xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
