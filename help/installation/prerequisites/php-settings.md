---
title: configurações PHP
description: Siga estas etapas para instalar as extensões PHP necessárias e definir as configurações PHP necessárias para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---


# configurações PHP

Este tópico discute como definir as opções PHP necessárias.

>[!NOTE]
>
>Consulte [requisitos do sistema](../system-requirements.md) para versões compatíveis do PHP.

## Verificar se o PHP está instalado

A maioria das opções de Linux tem o PHP instalado por padrão. Este tópico assume que você já instalou o PHP. Para verificar se o PHP já está instalado, na linha de comando, digite:

```bash
php -v
```

Se o PHP estiver instalado, uma mensagem semelhante a esta é exibida:

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

O Adobe Commerce e o Magento Open Source 2.4 são compatíveis com o PHP 7.3, mas testamos e recomendamos o uso do PHP 7.4.

Se o PHP não estiver instalado ou for necessário um upgrade de versão, instale-o seguindo as instruções para seu sabor Linux específico.
No CentOS, [podem ser necessárias etapas adicionais](https://wiki.centos.org/HowTos/php7).

## Verificar extensões instaladas

O Adobe Commerce e o Magento Open Source exigem que um conjunto de extensões seja instalado.

{{$include /help/_includes/templated/php-extensions.md}}

Para verificar as extensões instaladas:

1. Listar os módulos instalados.

   ```bash
   php -m
   ```

1. Verifique se todas as extensões necessárias estão instaladas.
1. Adicione os módulos ausentes usando o mesmo workflow usado para instalar o PHP. Por exemplo, se você usar `yum` para instalar o PHP, os módulos PHP 7.4 podem ser adicionados com:

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## Verificar configurações PHP

>[!WARNING]
>
>Se estiver usando o PHP 7.4.20, defina `pcre.jit=0` em seu `php.ini` arquivo. Isso dá a volta a um PHP [bug](https://bugs.php.net/bug.php?id=81101) que impede o carregamento de CSS.

- Defina o fuso horário do sistema para PHP; caso contrário, erros como o seguinte são exibidos durante a instalação e operações relacionadas ao tempo, como o cron, podem não funcionar:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Defina o limite de memória PHP.

   Nossas recomendações detalhadas são:

   - Compilação de código ou implantação de ativos estáticos, `1G`
   - Depuração, `2G`
   - Testes, `~3-4G`

- Aumente os valores para o PHP `realpath_cache_size` e `realpath_cache_ttl` para as configurações recomendadas:

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   Essas configurações permitem que processos PHP armazenem em cache caminhos em arquivos em vez de pesquisá-los sempre que uma página é carregada. Consulte [Ajuste de desempenho](https://www.php.net/manual/en/ini.core.php) na documentação do PHP.

- Habilitar [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), que é necessário para Adobe Commerce e Magento Open Source 2.1 e posterior.

   Recomendamos que você ative a [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) por motivos de desempenho. O OPcache é ativado em muitas distribuições PHP.

   Adobe Commerce e Magento Open Source 2.1 e posterior usam comentários de código PHP para geração de código.

>[!NOTE]
>
>Para evitar problemas durante a instalação e a atualização, recomendamos que você aplique as mesmas configurações PHP tanto à configuração da linha de comando PHP quanto à configuração do plug-in do servidor Web PHP. Para obter mais informações, consulte a próxima seção.

## Localizar arquivos de configuração PHP

Esta seção discute como você encontra os arquivos de configuração necessários para atualizar as configurações necessárias.

### Localizar `php.ini` arquivo de configuração

Para localizar a configuração do servidor da Web, execute um [`phpinfo.php` arquivo](optional-software.md#create-phpinfophp) em seu navegador da Web e procure por `Loaded Configuration File` como se segue:

![página de informações PHP](../../assets/installation/config_phpini-webserver.png)

Para localizar a configuração da linha de comando PHP, insira

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Se você tiver apenas um `php.ini` , faça as alterações nesse arquivo. Se você tiver dois `php.ini` , faça as alterações em *all* arquivos. Se isso não for feito, o desempenho poderá ser imprevisível.

### Encontrar configurações do OPcache

As configurações do PHP OPcache geralmente estão localizadas em `php.ini` ou `opcache.ini`. A localização pode depender do sistema operacional e da versão PHP. O arquivo de configuração OPcache pode ter um `opcache` seção ou configurações como `opcache.enable`.

Use as diretrizes a seguir para encontrá-lo:

- Servidor Web Apache:

   Para Ubuntu com Apache, as configurações de OPcache geralmente estão localizadas na variável `php.ini` arquivo.

   Para CentOS com Apache ou nginx, as configurações de OPcache geralmente estão localizadas em `/etc/php.d/opcache.ini`

   Caso contrário, use o seguinte comando para localizá-lo:

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- nginx web server com PHP-FPM: `/etc/php/7.2/fpm/php.ini`

Se você tiver mais de um `opcache.ini`, modifique todos eles.

## Como definir opções PHP

Para definir as opções PHP:

1. Abra um `php.ini` em um editor de texto.
1. Localize o fuso horário do seu servidor na variável [configurações de fuso horário](https://www.php.net/manual/en/timezones.php)
1. Localize a seguinte configuração e exclua o comentário se necessário:

   ```conf
   date.timezone =
   ```

1. Adicione a configuração de fuso horário encontrada na etapa 2.

1. Altere o valor de `memory_limit` para um dos valores recomendados no início desta seção.

   Por exemplo,

   ```conf
   memory_limit=2G
   ```

1. Adicione ou atualize o `realpath_cache` configuração para corresponder aos seguintes valores:

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

1. Abra o outro `php.ini` (se forem diferentes) e fazer as mesmas alterações nele.

## Definir opções do OPcache

Para definir `opcache.ini` opções:

1. Abra o arquivo de configuração do OPcache em um editor de texto:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/7.2/fpm/php.ini` (nginx web server (CentOS ou Ubuntu)

1. Localizar `opcache.save_comments` e exclua o comentário, se necessário.
1. Certifique-se de que seu valor esteja definido como `1`.
1. Salve as alterações e saia do editor de texto.
1. Reinicie o servidor Web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu e CentOS: `service nginx restart`

## Solução de problemas

Consulte os seguintes artigos de suporte do Adobe Commerce para obter ajuda com a solução de problemas do PHP:

- [Erro de versão PHP ou erro 404 ao acessar o Adobe Commerce no navegador](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Erros de configurações PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [Extensão mcrypt do PHP não instalada corretamente](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problemas de verificação de disponibilidade da versão PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Erros e soluções fatais PHP comuns](https://support.magento.com/hc/en-us/articles/360030568432)
