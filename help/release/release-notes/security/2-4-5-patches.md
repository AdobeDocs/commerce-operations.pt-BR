---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.5
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---


# Notas de versão de patches de segurança do Adobe Commerce 2.4.5

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

A versão de segurança 2.4.5-p7 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.5.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Atualizações da plataforma

* **Suporte ao MariaDB 10.5**. Esta versão de patch apresenta compatibilidade com o MariaDB versão 10.5. O Adobe Commerce ainda é compatível com a versão 10.4 do MariaDB, mas o Adobe recomenda o uso do Adobe Commerce 2.4.5-p8 e de todas as próximas versões de patch somente de segurança 2.4.5 somente com a versão 10.5 do MariaDB, pois a manutenção do MariaDB 10.4 termina em 18 de junho de 2024. <!--AC-11530-->

### Aprimoramentos adicionais de segurança

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

A versão de segurança 2.4.5-p7 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

A versão de segurança 2.4.5-p6 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Destaques da segurança

Esta versão apresenta dois aprimoramentos significativos de segurança:

* **Alterações no comportamento de chaves de cache não geradas**:

   * As chaves de cache não geradas para blocos agora incluem prefixos que diferem dos prefixos para chaves geradas automaticamente. (As chaves de cache não geradas são chaves definidas por meio da sintaxe de diretiva de modelo ou pelos métodos `setCacheKey` ou `setData`.)
   * As chaves de cache não geradas para blocos agora devem conter apenas letras, dígitos, hifens (-) e caracteres de sublinhado (_). <!-- AC-9831 -->

* **Limitações sobre o número de códigos de cupom gerados automaticamente**. O Commerce agora limita o número de códigos de cupom gerados automaticamente. O máximo padrão é 250.000. Os comerciantes podem usar a nova opção de configuração **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar esse novo limite. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

A versão de segurança 2.4.5-p5 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Realce de segurança

Esta versão introduz uma nova definição de configuração de cache de página inteira que ajuda a reduzir os riscos associados ao ponto de extremidade `{BASE-URL}/page_cache/block/esi HTTP`. Esse endpoint oferece suporte a fragmentos de conteúdo irrestritos e carregados dinamicamente de manipuladores de layout e estruturas de bloco do Commerce. A nova definição de configuração **[!UICONTROL Handles Param]** define o valor do parâmetro `handles` desse ponto de extremidade, que determina o número máximo permitido de identificadores por API. O valor padrão dessa propriedade é 100. Os comerciantes podem alterar este valor de Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problema conhecido

**Problema**: o Adobe Commerce exibe um erro de **soma de verificação incorreta** durante o download pelo Composer de `repo.magento.com`, e o download do pacote foi interrompido. Esse problema pode ocorrer durante o download de pacotes de lançamento que foram disponibilizados durante o pré-lançamento e é causado por um reempacotamento do pacote `magento/module-page-cache`.

**Solução alternativa**: os comerciantes que visualizarem este erro durante o download podem executar estas etapas:

1) Exclua o diretório `/vendor` dentro do projeto, se existir.
2) Execute o comando `bin/magento composer update magento/module-page-cache`. Este comando atualiza somente o pacote `page cache`.

Se o problema de soma de verificação persistir, remova o arquivo `composer.lock` antes de executar novamente o comando `bin/magento composer update` para atualizar cada pacote.

## Adobe Commerce 2.4.5-p4

A versão de segurança 2.4.5-p4 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Aplicar patch para resolver a vulnerabilidade de segurança CVE-2022-31160 na biblioteca jQuery-UI

A biblioteca `jQuery-UI` versão 1.13.1 tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no artigo da Base de Dados de Conhecimento [vulnerabilidade de segurança da interface do usuário do jQuery CVE-2022-31160 para 2.4.4, 2.4.5 e 2.4.6 versões](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html).

## Adobe Commerce 2.4.5-p3

A versão de segurança 2.4.5-p3 do Adobe Commerce fornece correções de segurança para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Aplicar patch para resolver a vulnerabilidade de segurança CVE-2022-31160 na biblioteca jQuery-UI

A biblioteca `jQuery-UI` versão 1.13.1 tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no artigo da Base de Dados de Conhecimento [vulnerabilidade de segurança da interface de consulta CVE-2022-31160 para as versões 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html).

### Realce de segurança

O comportamento padrão da consulta GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) e do ponto de extremidade REST [`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable) foi alterado. Por padrão, a API agora sempre retorna `true`. Os comerciantes podem habilitar o comportamento original, que é retornar `true` se o email não existir no banco de dados e `false` se ele existir. <!-- AC-6695 -->

### Atualizações da plataforma

As atualizações de plataforma para esta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

* **Suporte ao cache de verniz 7.3**. Esta versão é compatível com a versão mais recente do Varnish Cache 7.3. A compatibilidade permanece com as versões 6.0.x e 7.2.x, mas recomendamos usar o Adobe Commerce 2.4.5-p3 somente com o Varnish Cache versão 7.3 ou versão 6.0 LTS.

* **Suporte ao RabbitMQ 3.11**. Esta versão é compatível com a versão mais recente do RabbitMQ 3.11. A compatibilidade permanece com o RabbitMQ 3.9, compatível até agosto de 2023, mas recomendamos usar o Adobe Commerce 2.4.5-p3 somente com o RabbitMQ 3.11.

* **Bibliotecas JavaScript**. As bibliotecas JavaScript desatualizadas foram atualizadas para as versões secundárias ou de patch mais recentes, incluindo a biblioteca `moment.js` (v2.29.4), a biblioteca `jQuery UI` (v1.13.2) e a biblioteca de plug-in de validação `jQuery` (v1.19.5).

## Notas de versão do Adobe Commerce 2.4.5-p2

A versão de segurança 2.4.5-p2 do Adobe Commerce fornece três correções de segurança para vulnerabilidades identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

A versão de segurança 2.4.5-p1 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas na versão anterior (Adobe Commerce 2.4.5 e Magento Open Source 2.4.5).

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

Uma das correções de bugs de segurança incluiu a criação de uma nova configuração. A configuração **Exigir confirmação por email se o email tiver sido alterado** permite que os administradores exijam confirmação por email quando um usuário administrador alterar seu endereço de email. <!-- AC-6292-->
