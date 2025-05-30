---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.2
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Notas de versão de patches de segurança do Adobe Commerce 2.4.2

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

A versão de segurança 2.4.2-p2 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.2.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB21-64](https://helpx.adobe.com/br/security/products/magento/apsb21-64.html).

## Aplique o `AC-3022.patch` para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar o `AC-3022.patch` o mais rápido possível para continuarem oferecendo a DHL como transportadora. Consulte o artigo da Base de conhecimento [Aplicar um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) para obter informações sobre como baixar e instalar o patch.
