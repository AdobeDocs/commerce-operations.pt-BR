---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.7
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.7.
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Notas de versão de patches de segurança do Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

A versão de segurança do Adobe Commerce 2.4.7-p1 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Realce de segurança

Esta versão inclui uma atualização da [configurações de senha ocasional (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para que o Google Authenticator resolva um erro introduzido por um [alteração incompatível com versões anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) em 2.4.7. A descrição do **[!UICONTROL OTP Window]** agora fornece uma explicação precisa da configuração e o valor padrão foi alterado de `1` para `29`.

### Hotfixes incluídos nesta versão

O Adobe Commerce 2.4.7-p1 resolve um problema introduzido no escopo da migração de integração de UPS da API SOAP para REST. Esse problema afetou os clientes que enviavam para fora dos EUA e os impediu de usar as medições do Sistema de Métrica/SI de quilogramas e centímetros para que os pacotes criassem remessas com a UPS. Consulte a [Migração de integração do método de envio UPS de SOAP para API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) artigo da knowledge base para obter detalhes.
