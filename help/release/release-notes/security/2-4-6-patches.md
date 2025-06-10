---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.6
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 9ec53ae90e400a6dad98c77c6ae55c70c19e0a40
workflow-type: tm+mt
source-wordcount: '1354'
ht-degree: 0%

---


# Notas de versão de patches de segurança do Adobe Commerce 2.4.6

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p11

A versão de segurança do Adobe Commerce 2.4.6-p11 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.6.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-06.md}}

## 2.4.6-p10

A versão de segurança do Adobe Commerce 2.4.6-p10 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.6.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-26](https://helpx.adobe.com/br/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

A versão de segurança 2.4.6-p9 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.6.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB25-08](https://helpx.adobe.com/br/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

A versão de segurança do Adobe Commerce 2.4.6-p8 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.6.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB24-73](https://helpx.adobe.com/br/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfixes incluídos nesta versão

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

A versão de segurança do Adobe Commerce 2.4.6-p7 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.6.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-61](https://helpx.adobe.com/br/security/products/magento/apsb24-61.html).

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes incluídos nesta versão

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

A versão de segurança 2.4.6-p6 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.6.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-40](https://helpx.adobe.com/br/security/products/magento/apsb24-40.html).

Para compatibilidade com a versão 2.4.6-p6 do Commerce, os comerciantes que têm a extensão B2B do Adobe Commerce devem atualizar para a versão 1.4.2-p1[&#128279;](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) do B2B2B.

### Aplicar hotfix para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Para compatibilidade com a versão 2.4.6-p6 do Commerce, os comerciantes que têm a extensão B2B do Adobe Commerce devem atualizar para a versão 1.4.2-p1[&#128279;](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) do B2B2B.

### Destaques

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

A versão de segurança 2.4.6-p5 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores da 2.4.6.

Para obter as informações mais recentes sobre essas correções, consulte o [Boletim de Segurança do Adobe APSB24-18](https://helpx.adobe.com/br/security/products/magento/apsb24-18.html).

## 2.4.6-p4

A versão de segurança 2.4.6-p4 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB24-03](https://helpx.adobe.com/br/security/products/magento/apsb24-03.html).

### Destaques

Esta versão apresenta dois aprimoramentos significativos de segurança:

* **Alterações no comportamento de chaves de cache não geradas**:

   * As chaves de cache não geradas para blocos agora incluem prefixos que diferem dos prefixos para chaves geradas automaticamente. (As chaves de cache não geradas são chaves definidas por meio da sintaxe de diretiva de modelo ou pelos métodos `setCacheKey` ou `setData`.)
   * As chaves de cache não geradas para blocos agora devem conter apenas letras, dígitos, hifens (-) e caracteres de sublinhado (_). <!-- AC-9831 -->

* **Limitações sobre o número de códigos de cupom gerados automaticamente**. O Commerce agora limita o número de códigos de cupom gerados automaticamente. O máximo padrão é 250.000. Os comerciantes podem usar a nova opção de configuração **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar esse novo limite. <!-- AC-8753 -->

## 2.4.6-p3

A versão de segurança 2.4.6-p3 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de segurança, consulte o [Boletim de Segurança do Adobe APSB23-50](https://helpx.adobe.com/br/security/products/magento/apsb23-50.html).

### Destaques

Esta versão introduz uma nova definição de configuração de cache de página inteira que ajuda a reduzir os riscos associados ao ponto de extremidade `{BASE-URL}/page_cache/block/esi HTTP`. Esse endpoint oferece suporte a fragmentos de conteúdo irrestritos e carregados dinamicamente de manipuladores de layout e estruturas de bloco do Commerce. A nova definição de configuração **[!UICONTROL Handles Param]** define o valor do parâmetro `handles` desse ponto de extremidade, que determina o número máximo permitido de identificadores por API. O valor padrão dessa propriedade é 100. Os comerciantes podem alterar este valor de Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Hotfixes incluídos nesta versão

O Adobe Commerce 2.4.6-p3 inclui a resolução da degradação de desempenho corrigida pelo patch ACSD-51892. Os comerciantes não são afetados pelo problema tratado por esse patch, que é descrito no [ACSD-51892: problema de desempenho em que os arquivos de configuração são carregados várias vezes](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=pt-BR) artigo da Base de Dados de Conhecimento.

### Problemas conhecidos

**Problema**: o Adobe Commerce exibe um erro `wrong checksum` durante o download pelo Composer a partir de `repo.magento.com`, e o download do pacote é interrompido. Esse problema pode ocorrer durante o download de pacotes de lançamento disponibilizados durante o período de pré-lançamento e é causado por um reempacotamento do pacote `magento/module-page-cache`.

**Solução alternativa**: os comerciantes que visualizarem este erro durante o download podem executar estas etapas:

1) Exclua o diretório `/vendor` dentro do projeto, se existir.
2) Execute o comando `bin/magento composer update magento/module-page-cache`. Este comando atualiza somente o pacote `page cache`.

Se o problema de soma de verificação persistir, remova o arquivo `composer.lock` antes de executar novamente o comando `bin/magento composer update` para atualizar cada pacote.

## 2.4.6-p2

A versão de segurança 2.4.6-p2 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também oferece aprimoramentos de segurança para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB23-42](https://helpx.adobe.com/br/security/products/magento/apsb23-42.html).

### Aplicar hotfix para CVE-2022-31160

A biblioteca do `jQuery-UI` versão 1.13.1 tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no artigo da Base de Dados de Conhecimento [vulnerabilidade de segurança da interface do usuário do jQuery CVE-2022-31160 para 2.4.4, 2.4.5 e 2.4.6 versões](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=pt-BR).

### Destaques

O valor de `fastcgi_pass` no arquivo `nginx.sample` foi retornado ao seu valor anterior (pré-2.4.6-p1) de `fastcgi_backend`. Este valor foi alterado inadvertidamente para `php-fpm:9000` no Adobe Commerce 2.4.6-p1.

### Hotfixes incluídos nesta versão

O Adobe Commerce 2.4.6-p2 inclui a resolução da degradação do desempenho que foi abordada pelo patch ACSD-51892. Os comerciantes não são afetados pelo problema tratado por esse patch, que é descrito no [ACSD-51892: problema de desempenho em que os arquivos de configuração são carregados várias vezes](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=pt-BR) artigo da Base de Dados de Conhecimento.

## 2.4.6-p1

A versão de segurança 2.4.6-p1 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança e atualizações de plataforma para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB23-35](https://helpx.adobe.com/br/security/products/magento/apsb23-35.html).

### Aplicar hotfix para CVE-2022-31160

A biblioteca do `jQuery-UI` versão 1.13.1 tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no artigo da Base de Dados de Conhecimento [vulnerabilidade de segurança da interface de consulta CVE-2022-31160 para as versões 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=pt-BR).

#### Realce

O comportamento padrão da consulta GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) e do ponto de extremidade REST [`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable) foi alterado. Por padrão, a API agora sempre retorna `true`. Os comerciantes podem habilitar o comportamento original, que é retornar `true` se o email não existir no banco de dados e `false` se ele existir. <!-- AC-6695 -->

### Atualizações da plataforma

As atualizações de plataforma para esta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

* **Suporte ao cache de verniz 7.3**. Esta versão é compatível com a versão mais recente do Varnish Cache 7.3. A compatibilidade permanece com as versões 6.0.x e 7.2.x, mas a Adobe recomendou usar o Adobe Commerce 2.4.6-p1 somente com o Cache do Varnish versão 7.3 ou versão 6.0 LTS.

* **Suporte a RabbitMQ 3.11**. Esta versão é compatível com a versão mais recente do RabbitMQ 3.11. A compatibilidade permanece com o RabbitMQ 3.9, que é compatível até agosto de 2023, mas a Adobe recomendou usar o Adobe Commerce 2.4.6-p1 somente com o RabbitMQ 3.11.

* **Bibliotecas JavaScript**. As bibliotecas JavaScript desatualizadas foram atualizadas para as versões secundárias ou de patch mais recentes, incluindo a biblioteca `moment.js` (v2.29.4), a biblioteca `jQuery UI` (v1.13.2) e a biblioteca de plug-in de validação `jQuery` (v1.19.5).

### Problemas conhecidos

* O arquivo `nginx.sample` foi atualizado inadvertidamente com uma alteração que modifica o valor de `fastcgi_pass` de `fastcgi_backend` para `php-fpm:9000`. Essa alteração pode ser revertida ou ignorada com segurança. <!-- AC-8992 -->

* Dependências ausentes para o pacote de segurança B2B causam o seguinte erro de instalação ao instalar ou atualizar a extensão B2B para 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Esse problema pode ser resolvido adicionando dependências manuais para o pacote de segurança B2B com uma [marca de estabilidade](https://getcomposer.org/doc/04-schema.md#package-links). Para obter detalhes, consulte as [notas de versão B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html?lang=pt-BR#known-issue).
