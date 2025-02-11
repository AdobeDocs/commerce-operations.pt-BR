---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.7
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 9397740c608e4f0521018d6f6c918ca267197c6c
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Notas de versão de patches de segurança do Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p4

A versão de segurança 2.4.7-p4 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.7.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

A versão de segurança 2.4.7-p3 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.7.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfixes incluídos nesta versão

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

A versão de segurança 2.4.7-p2 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes incluídos nesta versão

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

A versão de segurança do Adobe Commerce 2.4.7-p1 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aplicar hotfix para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Destaques

Esta versão inclui os seguintes destaques:

* **Atualizar [configurações de senha única](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para o Google Authenticator**-Esta atualização é necessária para resolver um erro introduzido por uma [alteração incompatível com versões anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) na versão 2.4.7. A descrição do campo **[!UICONTROL OTP Window]** agora fornece uma explicação precisa da configuração e o valor padrão foi alterado de `1` para `29`.

* **Compatibilidade com a versão B2B** — Para compatibilidade com o Commerce versão 2.4.7-p1, os comerciantes que têm a extensão B2B do Adobe Commerce devem atualizar para a versão [B2B versão 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Hotfixes incluídos nesta versão

O Adobe Commerce 2.4.7-p1 resolve um problema introduzido no escopo da migração de integração de UPS do SOAP para a API REST. Esse problema afetou os clientes que enviavam para fora dos EUA e os impediu de usar as medições do Sistema de Métrica/SI de quilogramas e centímetros para que os pacotes criassem remessas com a UPS. Consulte o artigo da base de conhecimento [Migração da integração do método de envio UPS do SOAP para a API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) para obter mais detalhes.
