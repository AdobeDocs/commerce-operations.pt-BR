---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.7
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 2269c99908c0f8292ad62bd5837b1b8cebd50cb3
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Notas de versão de patches de segurança do Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

A versão de segurança do Adobe Commerce 2.4.7-p1 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.7.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aplicar hotfix para CVE-2024-34102

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Destaques da segurança

* **Atualizar [configurações de senha única](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para o Google Authenticator**-Esta atualização é necessária para resolver um erro introduzido por uma [alteração incompatível com versões anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) na versão 2.4.7. A descrição do campo **[!UICONTROL OTP Window]** agora fornece uma explicação precisa da configuração e o valor padrão foi alterado de `1` para `29`.

* **Compatibilidade com a versão B2B** — Para compatibilidade com o Commerce versão 2.4.7-p1, os comerciantes que têm a extensão B2B do Adobe Commerce devem atualizar para a versão [B2B versão 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Hotfixes incluídos nesta versão

O Adobe Commerce 2.4.7-p1 resolve um problema introduzido no escopo da migração da integração do UPS do SOAP para a API REST. Esse problema afetou os clientes que enviavam para fora dos EUA e os impediu de usar as medições do Sistema de Métrica/SI de quilogramas e centímetros para que os pacotes criassem remessas com a UPS. Consulte o artigo da base de conhecimento [Migração da integração do método de envio UPS do SOAP para a API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) para obter mais detalhes.
