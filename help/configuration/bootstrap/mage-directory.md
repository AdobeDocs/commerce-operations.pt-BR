---
title: Personalizar caminhos de diretório base
description: Use a variável MAGE_DIRS para definir uma matriz de caminhos absolutos.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 02c69e890b40643781ab8f48c3133527dd79386a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Caminhos de diretório base

A variável de ambiente `MAGE_DIRS` permite que você especifique caminhos de diretório base personalizados e fragmentos de URLs base que são usados pelo aplicativo Commerce para construir caminhos absolutos para vários arquivos ou para gerar URLs.

## Definir MAGE_DIRS

Especifique uma matriz associativa em que as chaves sejam constantes de [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] e os valores sejam caminhos absolutos de diretórios ou seus caminhos de URL, respectivamente.

Você pode definir `MAGE_DIRS` de qualquer uma das seguintes maneiras:

- [Definir o valor dos parâmetros de inicialização](../bootstrap/set-parameters.md)
- Use um script de ponto de entrada personalizado como o seguinte:

  ```php
  <?php
  /**
   * Copyright Adobe
   * All Rights Reserved.
   */
  
  use Magento\Framework\App\Bootstrap;
  use Magento\Framework\App\Filesystem\DirectoryList;
  use Magento\Framework\App\Http;
  
  require __DIR__ . '/app/bootstrap.php';
  $params = $_SERVER;
  $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
       DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
       DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
       DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
       DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
       DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
  ];
  $bootstrap = Bootstrap::create(BP, $params);
  /** @var Http $app */
  $app = $bootstrap->createApplication(Http::class);
  $bootstrap->run($app);
  ```

O exemplo anterior define os caminhos dos diretórios `[cache]` e `[media]` como `/mnt/nfs/cache` e `/mnt/nfs/media`, respectivamente.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
