---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.7
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 5f0914e92e5d1f1a27640a12a36c73ce878687a0
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Notas de versão de patches de segurança do Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p8

A versão de segurança do Adobe Commerce 2.4.7-p8 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.7.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB25-94](https://helpx.adobe.com/br/security/products/magento/apsb25-94.html).

{{b2b-patches}}

Esta versão inclui os seguintes destaques:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### Problemas conhecidos

#### A página de check-out não carrega static.min.js e mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.7-p7

A versão de segurança do Adobe Commerce 2.4.7-p7 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-71](https://helpx.adobe.com/br/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.7-p6

A versão de segurança 2.4.7-p6 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-50](https://helpx.adobe.com/br/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Destaques

Esta versão inclui os seguintes destaques:

* **Suporte a MariaDB**—Suporte a MariaDB 10.11 adicionado.

* **Aprimoramento de desempenho da API**—Resolve a degradação de desempenho em pontos de extremidade de API da Web assíncronos em massa que foram introduzidos após o patch de segurança anterior.<!-- AC-14078 -->

* **Correção de acesso de Bloqueios do CMS** — Resolve um problema em que os usuários administradores com permissões restritas (como acesso somente de merchandising) não conseguiam exibir a página de listagem [!UICONTROL CMS Blocks].

  Anteriormente, esses usuários encontravam um erro devido a parâmetros de configuração ausentes após a instalação de patches de segurança anteriores.<!-- AC-14087 -->

* **Compatibilidade com limite de cookies** — Resolve uma alteração incompatível com versões anteriores envolvendo a constante `MAX_NUM_COOKIES` na estrutura. Esta atualização restaura o comportamento esperado e garante a compatibilidade para extensões ou personalizações que interagem com limites de cookies.<!-- AC-14475 -->

* **Operações assíncronas** — Operações assíncronas restritas para substituir pedidos de clientes anteriores.<!-- AC-13917 -->

## 2.4.7-p5

A versão de segurança do Adobe Commerce 2.4.7-p5 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-26](https://helpx.adobe.com/br/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Esta versão também apresenta suporte para a [extensão pronta para HIPAA do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/start/compliance/hipaa-ready-service/overview).

>[!ENDSHADEBOX]

### Problemas conhecidos

**Problema**: ao instalar o 2.4.7-p5 com o PHP 8.2 ou superior, o sistema instala o `paypal/module-braintree` versão 4.7.0, que se destina ao 2.4.8 e mais recente. Para o PHP 8.1, é usada a versão correta 4.6.1-p5 do Braintree. Esta incompatibilidade se deve à dependência flexível em `adobe-commerce/extensions-metapackage: ~2.0` no metapackage. Isso afeta a compatibilidade e o conjunto de recursos suportados para implantações do PHP 8.2+.<!-- ACPLTSRV-6276) -->

Além disso, para as versões 2.4.7-p3, 2.4.7-p4 e 2.4.7-p5, a extensão do Braintree versão 4.6.1-p5 pode ser instalada, enquanto alguns usuários esperam 4.6.1-p3 ou p4, devido a dependências mais rigorosas anteriores terem sido relaxadas para permitir atualizações de extensão em uma linha de versão. <!-- AC-14430 -->

**Solução alternativa**: para garantir que você tenha a versão correta do Braintree para a sua versão do PHP, execute `composer update` para instalar a versão apropriada conforme determinado pela dependência `adobe-commerce/extensions-metapackage:2.0.0`.

## 2.4.7-p4

A versão de segurança 2.4.7-p4 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.7.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB25-08](https://helpx.adobe.com/br/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

A versão de segurança 2.4.7-p3 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.7.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB24-73](https://helpx.adobe.com/br/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfixes incluídos nesta versão

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

A versão de segurança 2.4.7-p2 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-61](https://helpx.adobe.com/br/security/products/magento/apsb24-61.html).

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes incluídos nesta versão

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

A versão de segurança do Adobe Commerce 2.4.7-p1 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-40](https://helpx.adobe.com/br/security/products/magento/apsb24-40.html).

### Aplicar hotfix para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Destaques

Esta versão inclui os seguintes destaques:

* **Atualizar [configurações de senha única](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para o Google Authenticator**-Esta atualização é necessária para resolver um erro introduzido por uma [alteração incompatível com versões anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) na versão 2.4.7. A descrição do campo **[!UICONTROL OTP Window]** agora fornece uma explicação precisa da configuração e o valor padrão foi alterado de `1` para `29`.

* **Compatibilidade com a versão B2B** — Para compatibilidade com o Commerce versão 2.4.7-p1, os comerciantes que têm a extensão B2B do Adobe Commerce devem atualizar para a versão [B2B versão 1.4.2-p1](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Hotfixes incluídos nesta versão

O Adobe Commerce 2.4.7-p1 resolve um problema introduzido no escopo da migração de integração de UPS do SOAP para a API REST. Esse problema afetou os clientes que enviavam para fora dos EUA e os impediu de usar as medições do Sistema de Métrica/SI de quilogramas e centímetros para que os pacotes criassem remessas com a UPS. Consulte o artigo da base de conhecimento [Migração da integração do método de envio UPS do SOAP para a API RESTful](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) para obter mais detalhes.

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
