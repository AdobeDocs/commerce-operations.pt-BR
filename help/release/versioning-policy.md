---
title: Política de lançamento
description: Saiba mais sobre os diferentes tipos de versões do Adobe Commerce.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: e0905f357c5ab84b30304eeaad00d9ae4ec0c168
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Política de versão do Adobe Commerce

O Adobe Commerce usa [controle de versão semântico](https://semver.org/) no nível de módulo individual (por exemplo, `magento/framework 101.1.1`), mas não para o número de versão de marketing. Por exemplo:

- **VERSÃO PRINCIPAL**—2
- **VERSÃO SECUNDÁRIA**—2.4
- **PATCH release**—2.4.8
   - **Versão de correção de segurança**—2.4.8-p1
      - Correção de erro de segurança
      - Aprimoramento de segurança
- **Versão de patch do ALPHA**—2.4.8-alpha1
- **Versão de patch do BETA**—2.4.8-beta1
- **Extensibility, Infrastructure, and Services release**
- **Hotfix**
- **Patch individual**
- **Patch personalizado**

## Versão SECUNDÁRIA

As seguintes diretrizes se aplicam a versões secundárias:

- É possível que ocorram alterações importantes; o código escrito para o Adobe Commerce 2.2.x pode não funcionar mais com o Adobe Commerce 2.3.x. Por exemplo, versões secundárias podem apresentar suporte para os principais requisitos e dependências do sistema, como o PHP.
- As versões dos módulos podem variar. Por exemplo, algumas alterações de módulo são introduzidas em um novo patch, enquanto outras são introduzidas em uma versão secundária.
- Minor releases can include new features that may require additional work by you or your solution partner during an upgrade to ensure compatibility.
- Minor releases can include fixes for security and quality issues.

## PATCH release

Patch releases are primarily focused on delivering security, performance, compliance, and high-priority quality fixes to help you keep your sites performing at their peak.

The following guidelines apply to patch releases:

- The latest-supported minor release receives full functional quality fixes and enhancements.
- Changes that could break extensions or code compatibility are avoided. For example, code written for version 2.2.0 should still work on version 2.2.7.
- On an exceptional basis, breaking changes or additional patches or hotfixes may be released to address security or compliance issues and high-impact quality issues. On the module level, these changes are mostly PATCH-level; sometimes MINOR-level.

### SECURITY patch release

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## ALPHA patch release

Pre-Beta releases of Adobe Commerce features are made publicly available to all Adobe Commerce customers and Adobe partners. Alpha releases are intended for early feedback and evaluation of features that are still in active development. These releases provide an opportunity for early testing and integration planning ahead of Beta and General Availability releases.

Alpha releases may be incomplete, and are likely to contain defects. They are provided &quot;AS IS&quot; without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify, or otherwise support (via Adobe Support Services or otherwise) Alpha releases. Customers should not rely on the correct functioning or performance of Alpha releases or any accompanying documentation or materials. Use of Alpha releases is entirely at the customer&#39;s own risk.

## BETA patch release

Pre-General Availability releases of Adobe Commerce features are made publicly available to all Adobe Commerce customers and Adobe partners. It allows for extra time before General Availability to review code and affected components.

Beta releases may contain defects and are provided &quot;AS IS&quot; without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify, or otherwise support (via Adobe Support Services or otherwise) Beta releases. Customers should not rely on the correct functioning or performance of Beta releases or any accompanying documentation or materials. Portanto, qualquer uso das versões do Beta é de inteira responsabilidade do cliente.

## Hotfix

Hotfixes são patches que contêm correções de segurança ou qualidade de alto impacto, como correções para vulnerabilidades &quot;zero-day&quot;, que afetam muitos comerciantes. O Adobe lança hotfixes (conforme necessário) para versões do Adobe Commerce compatíveis quando problemas críticos de segurança ou qualidade os afetam. Os hotfixes são entregues por meio da [Ferramenta de correção de qualidade](../tools/quality-patches-tool/usage.md). Essas correções estão incluídas na próxima versão de patch planejada.

>[!NOTE]
>
>Hotfixes podem conter alterações incompatíveis com versões anteriores.

## Patch individual

Patches individuais contêm correções de qualidade de baixo impacto para um problema específico. Essas correções são aplicadas às versões secundárias compatíveis do Adobe Commerce. A Adobe lança patches individuais conforme necessário para o Adobe Commerce de acordo com a [Política de ciclo de vida do software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf). Eles são entregues por meio da [Ferramenta de Patches de Qualidade](../tools/quality-patches-tool/usage.md).

>[!NOTE]
>
>Os patches individuais não contêm alterações incompatíveis com versões anteriores.

## Correção personalizada

Criado por pessoas que não são da Adobe para corrigir um problema ou modificar o código do Adobe Commerce por vários motivos.

<!-- Last updated from includes: 2026-04-20 10:12:04 -->
