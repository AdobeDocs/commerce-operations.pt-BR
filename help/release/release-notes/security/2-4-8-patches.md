---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.8
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.7.
source-git-commit: 33debd1c742698e8242faaef1ff83bb2a9e5ee58
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Notas de versão de patches de segurança do Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p1

A versão de segurança 2.4.8-p1 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.8.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Destaques

Esta versão inclui os seguintes destaques:

* **Aprimoramento de desempenho da API**—Resolve a degradação de desempenho em pontos de extremidade de API da Web assíncronos em massa que foram introduzidos após o patch de segurança anterior.<!-- AC-14078 -->

* **Correção de acesso de Bloqueios do CMS** — Resolve um problema em que os usuários administradores com permissões restritas (como acesso somente de merchandising) não conseguiam exibir a página de listagem [!UICONTROL CMS Blocks].

  Anteriormente, esses usuários encontravam um erro devido a parâmetros de configuração ausentes após a instalação de patches de segurança anteriores.<!-- AC-14087 -->

* **Compatibilidade com limite de cookies** — Resolve uma alteração incompatível com versões anteriores envolvendo a constante `MAX_NUM_COOKIES` na estrutura. Esta atualização restaura o comportamento esperado e garante a compatibilidade para extensões ou personalizações que interagem com limites de cookies.<!-- AC-14475 -->

* **Operações assíncronas** — Operações assíncronas restritas para substituir pedidos de clientes anteriores.<!-- AC-13917 -->

* **Correção para CVE-2025-47110**—Resolve uma vulnerabilidade de modelos de email.<!-- AC-14695 -->

* **Correção para VULN-31547**—Resolve uma vulnerabilidade de link canônico de categoria.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

As correções para CVE-2025-47110 e VULN-31547 também estão disponíveis como um patch isolado. Consulte o [artigo da Base de Dados de Conhecimento](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) para obter detalhes.

>[!ENDSHADEBOX]
