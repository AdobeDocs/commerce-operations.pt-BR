---
title: Personalizar caminhos de diretório base
description: Use a variável MAGE_DIRS para definir uma matriz de caminhos absolutos.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Caminhos de diretório base

A variável `MAGE_DIRS` A variável de ambiente permite especificar caminhos de diretório base personalizados e fragmentos de URLs base que são usados pelo aplicativo Commerce para construir caminhos absolutos para vários arquivos ou para gerar URLs.

## Definir MAGE_DIRS

Especificar uma matriz associativa de onde as chaves são constantes [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] Os valores e são caminhos absolutos de diretórios ou seus caminhos de URL, respectivamente.

Você pode definir `MAGE_DIRS` de qualquer uma das seguintes formas:

- [Definir o valor dos parâmetros de inicialização](../bootstrap/set-parameters.md)
- Use um script de ponto de entrada personalizado como o seguinte:

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
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

O exemplo anterior define caminhos para `[cache]` e `[media]` diretórios para `/mnt/nfs/cache` e `/mnt/nfs/media`, respectivamente.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
