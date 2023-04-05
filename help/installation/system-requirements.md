---
title: Requisitos do sistema
description: Use essa referência para identificar as dependências de software necessárias que foram testadas com versões de Adobe Commerce e Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Requisitos do sistema

Esta tabela mostra versões de dependências de software de terceiros que o Adobe testou com versões específicas do Adobe Commerce e do Magento Open Source. O Adobe suporta apenas a combinação de requisitos de sistema descritos na tabela a seguir.

Por exemplo, o 2.4.5 é totalmente testado com o MariaDB 10.4. O Adobe recomenda que você atualize para o MariaDB 10.4 antes de atualizar para o 2.4.5.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Diversos

Esta seção descreve o suporte e a compatibilidade para todos os outros tipos de software necessários e opcionais.

>[!NOTE]
>
>Os requisitos a seguir se aplicam à versão mais recente do patch 2.4.x do Adobe Commerce e do Magento Open Source.

### Servidor de correio

Mail Transfer Agent (MTA) ou um servidor SMTP

### Sistemas operacionais (Linux x86-64)

Distribuição do Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e semelhante. Não há suporte para Microsoft Windows e macOS.

### extensões PHP

>[!NOTE]
>
>O [instruções de instalação do PHP](prerequisites/php-settings.md) inclua uma etapa para instalar essas extensões.

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentação oficial do PHP](https://php.net/manual/en/extensions.php) para obter detalhes sobre a instalação.

### PHP OPcache

Recomendamos que você verifique se [PHP OPcache](https://php.net/manual/en/intro.opcache.php) está ativada por motivos de desempenho. O OPcache é ativado em muitas distribuições PHP. Para verificar se ele está instalado, consulte nosso [documentação PHP](prerequisites/php-settings.md).

Se precisar instalá-lo separadamente, consulte o [Documentação do PHP OPcache](https://php.net/manual/en/opcache.setup.php).

### configurações PHP

Recomendamos configurações específicas do PHP, como `memory_limit`, que pode evitar problemas comuns ao usar o Adobe Commerce e o Magento Open Source.

Para obter mais informações, consulte [Configurações PHP necessárias](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (como uma ferramenta de linha de comando) 9.0.0

### RAM

A atualização dos aplicativos e extensões que você obtém do Commerce Marketplace e de outras fontes pode exigir até 2 GB de RAM. Se você estiver usando um sistema com menos de 2 GB de RAM, recomendamos que você crie um [troca de arquivo](https://support.magento.com/hc/en-us/articles/360032980432); caso contrário, sua atualização pode falhar.

### Dependências do sistema

O Adobe Commerce e o Magento Open Source exigem as seguintes ferramentas de sistema para algumas operações:

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

- É necessário um certificado de segurança válido para HTTPS.
- Certificados SSL autoassinados não são suportados.
- Requisito de TLS (Transport Layer Security) - PayPal e `repo.magento.com` ambos exigem TLS 1.2 ou posterior.

### Navegadores compatíveis

Loja e Administrador:

- Microsoft Edge (versão principal mais recente e anterior)
- Firefox (versão principal mais recente e anterior; qualquer sistema operacional)
- Chrome (versão principal mais recente e anterior; qualquer sistema operacional)
- Safari (versão principal mais recente e anterior; Somente macOS)
- Safari Mobile para iPad 2, iPad Mini, iPad com Retina Display (iOS 12 ou posterior), para vitrine de desktop
- Safari Mobile para iPhone 6 ou posterior; iOS 12 ou posterior, para vitrine móvel
- Chrome para dispositivos móveis (versão principal mais recente e anterior) [Android 4 ou posterior] para loja móvel)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) ou posterior (apenas ambientes de desenvolvimento; pode ter um efeito adverso no desempenho)

>[!NOTE]
>
>Há um problema conhecido com `xdebug` que podem afetar as instalações do Adobe Commerce ou Magento Open Source ou o acesso à loja ou ao Administrador após a instalação. Para obter detalhes, consulte [Problema conhecido com xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
