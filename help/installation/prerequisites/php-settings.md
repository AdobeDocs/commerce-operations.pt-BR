---
title: Configurações do PHP
description: Siga estas etapas para instalar as extensões necessárias do PHP e definir as configurações necessárias do PHP para instalações locais do Adobe Commerce e do Magento Open Source.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 9fe0a27346554bca3cb635b2e7ecf175adcec54a
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 0%

---


# Configurações do PHP

Este tópico discute como definir as opções necessárias do PHP.

>[!NOTE]
>
>A versão mais recente do Adobe Commerce e do Magento Open Source requer no mínimo o PHP 8.1. Consulte [requisitos do sistema](../system-requirements.md) para todas as versões suportadas do PHP.

Para obter orientação sobre a configuração na nuvem, consulte [Configurações do PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) no _Commerce na infraestrutura em nuvem_ guia.

## Verificar se o PHP está instalado

O PHP é instalado por padrão na maioria das distribuições Linux. Este tópico assume que você já instalou o PHP. Para verificar se o PHP está instalado, digite o seguinte na linha de comando:

```bash
php -v
```

Se o PHP estiver instalado, uma mensagem similar à seguinte será exibida:

```terminal
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

Se o PHP não estiver instalado (ou necessitar de uma atualização), instale-o seguindo as instruções para a sua distribuição Linux.

## Verificar extensões instaladas

Adobe Commerce e Magento Open Source requerem determinadas extensões PHP. As listas a seguir especificam as extensões necessárias para cada edição do Commerce. As listas são geradas automaticamente a partir de uma implantação que executa a versão mais recente de cada edição.

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
>Se você estiver usando o PHP 7.4.20, defina `pcre.jit=0` no seu `php.ini` arquivo. Isto se aproxima de um PHP [bug](https://bugs.php.net/bug.php?id=81101) que impede o CSS de carregar.

- Defina o fuso horário do sistema para o PHP; caso contrário, erros como o seguinte durante a instalação e operações relacionadas ao tempo como cron podem não funcionar:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Defina o limite de memória do PHP.

  Adobe recomenda o seguinte:

   - Compilação de código ou implantação de ativos estáticos, `1G`
   - Depuração, `2G`
   - Testes, `~3-4G`

- Aumentar os valores do PHP `realpath_cache_size` e `realpath_cache_ttl` para configurações recomendadas:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Estas configurações permitem que processos PHP armazenem em cache caminhos para arquivos em vez de pesquisá-los no carregamento da página. Consulte [Ajuste de desempenho](https://www.php.net/manual/en/ini.core.php) na documentação do PHP.

- Ativar [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), que é necessário para o Adobe Commerce e o Magento Open Source 2.1 e posteriores.

  O Adobe recomenda ativar o [OPcache do PHP](https://www.php.net/manual/en/book.opcache.php) por motivos de desempenho. O OPcache está habilitado em muitas distribuições PHP.

  Adobe Commerce e Magento Open Source 2.1 e posterior usam comentários de código PHP para geração de código.

>[!NOTE]
>
>Para evitar problemas durante a instalação e o upgrade, o Adobe recomenda que você aplique as mesmas configurações do PHP tanto para a configuração da linha de comando do PHP quanto para a configuração do plug-in do servidor Web PHP. Para obter mais informações, consulte a próxima seção.

## Localizar arquivos de configuração do PHP

Esta seção discute como você encontra os arquivos de configuração necessários para atualizar as configurações necessárias.

### Localizar `php.ini` arquivo de configuração

Para localizar a configuração do servidor Web, execute uma [`phpinfo.php` arquivo](optional-software.md#create-phpinfophp) no navegador da Web e procure a variável `Loaded Configuration File` do seguinte modo:

![Página de informações do PHP](../../assets/installation/config_phpini-webserver.png)

Para localizar a configuração da linha de comando do PHP, digite

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Se você tiver apenas um `php.ini` arquivo, altere esse arquivo. Se você tiver dois `php.ini` arquivos, alterar *ambos* arquivos. Se isso não for feito, o desempenho poderá ser imprevisível.

### Localizar definições de configuração do OPcache

Normalmente, as configurações de OPcache do PHP estão localizadas em `php.ini` ou `opcache.ini`. A localização pode depender do seu sistema operacional e da versão do PHP. O arquivo de configuração do OPcache pode ter um `opcache` seção ou configurações como `opcache.enable`.

Use as diretrizes a seguir para encontrá-la:

- Apache Web Server:

  Para o Ubuntu com Apache, as configurações do OPcache normalmente estão localizadas no `php.ini` arquivo.

  Para CentOS com Apache ou nginx, as configurações de OPcache normalmente estão localizadas em `/etc/php.d/opcache.ini`

  Caso contrário, use o seguinte comando para localizá-lo:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- nginx web server com PHP-FPM: `/etc/php/8.1/fpm/php.ini`

Se tiver mais de um `opcache.ini`, modifique todos eles.

## Como definir opções do PHP

Para definir as opções do PHP:

1. Abra um `php.ini` em um editor de texto.
1. Localize o fuso horário do seu servidor no campo [configurações de fuso horário](https://www.php.net/manual/en/timezones.php)
1. Localize a seguinte configuração e remova o comentário dela se necessário:

   ```conf
   date.timezone =
   ```

1. Adicione a configuração de fuso horário encontrada na etapa 2.

1. Altere o valor de `memory_limit` a um dos valores recomendados no início desta seção.

   Por exemplo,

   ```conf
   memory_limit=2G
   ```

1. Adicionar ou atualizar o `realpath_cache` para corresponder aos seguintes valores:

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

1. Abra o outro `php.ini` (se forem diferentes) e fazer as mesmas alterações nela.

## Definir opções de OPcache

Para definir `opcache.ini` opções:

1. Abra o arquivo de configuração do OPcache em um editor de texto:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (servidor Web nginx (CentOS ou Ubuntu))

1. Localizar `opcache.save_comments` e deixe de comentar, se necessário.
1. Verifique se o valor está definido como `1`.
1. Salve as alterações e saia do editor de texto.
1. Reiniciar o servidor Web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu e CentOS: `service nginx restart`

## Solução de problemas

Consulte os seguintes artigos de suporte do Adobe Commerce para obter ajuda com a solução de problemas do PHP:

- [Erro de versão do PHP ou erro 404 ao acessar o Adobe Commerce em um navegador](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Erros de configurações de PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [Extensão mcrypt do PHP não instalada corretamente](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problemas de verificação de preparação da versão do PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Erros fatais comuns do PHP e suas soluções](https://support.magento.com/hc/en-us/articles/360030568432)
