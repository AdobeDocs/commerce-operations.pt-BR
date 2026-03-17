---
title: Configurações do PHP
description: Siga estas etapas para instalar as extensões necessárias do PHP e definir as configurações necessárias do PHP para instalações locais do Adobe Commerce.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 766226dc998aafe54bc84d77cabee6fb0a969e6c
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 0%

---


# Configurações do PHP

Este tópico discute como definir as opções necessárias do PHP.

>[!NOTE]
>
>As versões do PHP suportadas variam de acordo com a versão do Adobe Commerce. Consulte [requisitos do sistema](../system-requirements.md) para obter as versões exatas do PHP suportadas pela versão que você está instalando.

Para obter orientações sobre a configuração da nuvem, consulte [configurações do PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) no guia _Commerce na Infraestrutura da Nuvem_.

## Controle do processo PHP

{{php-process-control}}

## Verificar se o PHP está instalado

O PHP é instalado por padrão na maioria das distribuições Linux. Este tópico assume que você já instalou o PHP. Para verificar se o PHP está instalado, digite o seguinte na linha de comando:

```bash
php -v
```

Se o PHP estiver instalado, uma mensagem similar à seguinte será exibida:

```
PHP <supported-version> (cli) (built: <build-date>) (NTS)
Copyright (c) The PHP Group
Zend Engine v<matching-version>, Copyright (c) Zend Technologies
    with Zend OPcache v<matching-version>, Copyright (c), by Zend Technologies
```

Se o PHP não estiver instalado (ou necessitar de uma atualização), instale-o seguindo as instruções para a sua distribuição Linux.

## Verificar extensões instaladas

O Adobe Commerce requer determinadas extensões do PHP. As listas a seguir especificam as extensões necessárias para cada edição do Commerce. As listas são geradas automaticamente a partir de uma implantação que executa a versão mais recente de cada edição.

{{$include /help/_includes/templated/php-extensions.md}}

Para verificar as extensões instaladas:

1. Listar módulos instalados.

   ```bash
   php -m
   ```

1. Verifique se todas as extensões necessárias estão instaladas.
1. Adicione quaisquer módulos ausentes usando o mesmo workflow usado para instalar o PHP.

## Verificar configurações do PHP

>[!WARNING]
>
>Se você estiver solucionando problemas em um ambiente herdado afetado pelo PHP [bug 81101](https://bugs.php.net/bug.php?id=81101), defina `pcre.jit=0` em seu arquivo `php.ini` para contornar o problema no qual o CSS não carrega.

- Defina o fuso horário do sistema para o PHP; caso contrário, erros como o seguinte durante a instalação e operações relacionadas ao tempo como cron podem não funcionar:

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Defina o limite de memória do PHP.

  A Adobe recomenda o seguinte:

   - Compilando código ou implantando ativos estáticos, `1G`
   - Depurando, `2G`
   - Testando, `~3-4G`

- Aumente os valores do PHP `realpath_cache_size` e `realpath_cache_ttl` para as configurações recomendadas:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Estas configurações permitem que processos PHP armazenem em cache caminhos para arquivos em vez de pesquisá-los no carregamento da página. Consulte [Ajuste de desempenho](https://www.php.net/manual/en/ini.core.php) na documentação do PHP.

- Habilitar [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), que é necessário para o Adobe Commerce 2.1 e posterior.

  A Adobe recomenda habilitar o [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) por motivos de desempenho. O OPcache está habilitado em muitas distribuições PHP.

  Adobe Commerce 2.1 e posteriores usam comentários de código PHP para geração de código.

>[!NOTE]
>
>Para evitar problemas durante a instalação e o upgrade, a Adobe recomenda que você aplique as mesmas configurações do PHP tanto para a configuração da linha de comando do PHP quanto para a configuração do plug-in do servidor Web PHP. Para obter mais informações, consulte a próxima seção.

## Localizar arquivos de configuração do PHP

Esta seção discute como você encontra os arquivos de configuração necessários para atualizar as configurações necessárias.

### Localizar o arquivo de configuração `php.ini`

Para localizar a configuração do servidor Web, execute um [`phpinfo.php` arquivo](optional-software.md#create-phpinfophp) em seu navegador da Web e procure o `Loaded Configuration File` da seguinte maneira:

![Página de informações do PHP](../../assets/installation/config_phpini-webserver.png)

Para localizar a configuração da linha de comando do PHP, digite

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Se você tiver apenas um arquivo `php.ini`, altere esse arquivo. Se você tiver dois arquivos `php.ini`, altere *ambos* arquivos. Se isso não for feito, o desempenho poderá ser imprevisível.

### Localizar definições de configuração do OPcache

Normalmente, as configurações de OPcache do PHP estão localizadas em `php.ini` ou `opcache.ini`. A localização pode depender do seu sistema operacional e da versão do PHP. O arquivo de configuração OPcache pode ter uma seção `opcache` ou configurações como `opcache.enable`.

Use as diretrizes a seguir para encontrá-la:

- Apache Web Server:

  Para o Ubuntu com Apache, as configurações do OPcache normalmente estão localizadas no arquivo `php.ini`.

  Para CentOS com Apache ou nginx, as configurações de OPcache normalmente estão localizadas em `/etc/php.d/opcache.ini`

  Caso contrário, use o seguinte comando para localizá-lo:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- servidor Web nginx com PHP-FPM: `/etc/php/<supported-php-version>/fpm/php.ini`

Se você tiver mais de um `opcache.ini`, modifique todos eles.

## Como definir opções do PHP

Para definir as opções do PHP:

1. Abra um `php.ini` em um editor de texto.
1. Localize o fuso horário do seu servidor nas [configurações de fuso horário](https://www.php.net/manual/en/timezones.php) disponíveis
1. Localize a seguinte configuração e remova o comentário dela se necessário:

   ```conf
   date.timezone =
   ```

1. Adicione a configuração de fuso horário encontrada na etapa 2.

1. Altere o valor de `memory_limit` para um dos valores recomendados no início desta seção.

   Por exemplo,

   ```conf
   memory_limit=2G
   ```

1. Adicione ou atualize a configuração `realpath_cache` para corresponder aos seguintes valores:

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. Salve as alterações e saia do editor de texto.

1. Abra o outro `php.ini` (se forem diferentes) e faça as mesmas alterações nele.

## Definir opções de OPcache

Para definir opções de `opcache.ini`:

1. Abra o arquivo de configuração do OPcache em um editor de texto:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/<supported-php-version>/fpm/php.ini` (servidor Web nginx (CentOS ou Ubuntu))

1. Localize `opcache.save_comments` e remova o comentário, se necessário.
1. Verifique se o valor está definido como `1`.
1. Salve as alterações e saia do editor de texto.
1. Reiniciar o servidor Web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu e CentOS: `service nginx restart`

## Solução de problemas

Consulte os seguintes artigos de suporte do Adobe Commerce para obter ajuda com a solução de problemas do PHP:

- [Erro de versão do PHP ou erro 404 ao acessar o Adobe Commerce em um navegador](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [erros de configurações do PHP](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/php-settings-errors)
- [Extensão mcrypt do PHP não instalada corretamente](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/php-mcrypt-extension-not-installed-properly)
- [Problemas de verificação de preparação da versão do PHP](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues)
- [Erros Fatais Comuns do PHP e soluções](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions)

<!-- Last updated from includes: 2025-04-04 22:27:22 -->
