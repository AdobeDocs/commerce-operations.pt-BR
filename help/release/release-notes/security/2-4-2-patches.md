---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.2
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
last-update: 2026-08-19
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%
---

# Notas de versão de patches de segurança do Adobe Commerce 2.4.2

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

A versão de segurança 2.4.2-p2 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.2.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html).

## Aplique o AC-3022.patch para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar o `AC-3022.patch` o mais rápido possível para continuarem oferecendo a DHL como transportadora. Consulte o artigo da Base de conhecimento [Aplicar um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) para obter informações sobre como baixar e instalar o patch.

<!-- Last updated from includes: 2026-08-19 13:31:55 -->
