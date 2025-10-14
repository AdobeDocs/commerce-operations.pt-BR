---
title: Programação de lançamento de patches
description: Saiba quando a Adobe planeja anunciar o lançamento de novos patches e correções de segurança para o Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 5f9f0e1dab7f5e4580f077693039ea387df23880
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Programação de lançamento de patches

A Adobe se esforça continuamente para encontrar o equilíbrio certo entre tornar as atualizações de produtos simples e previsíveis e, ao mesmo tempo, fornecer melhorias aos participantes iniciais mais rapidamente (consulte [política de controle de versão](versioning-policy.md)).

O objetivo deste cronograma é fornecer datas para quando a Adobe planeja anunciar o lançamento de [patches](versioning-policy.md#patch-release) para cada linha de lançamento com suporte do aplicativo Adobe Commerce PHP principal. As versões de correção são oportunidades de atualizar a base de código principal para manter sua plataforma segura, confiável e eficiente.

>[!NOTE]
>
>Para saber mais sobre novos recursos, infraestrutura em nuvem e versões de extensibilidade, consulte a documentação da versão dos [Serviços da Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Além dos patches de qualidade, segurança e beta agendados listados nesta página, a Adobe fornece acesso a [patches individuais](versioning-policy.md#individual-patch) por meio da [Ferramenta de Patches de Qualidade](../tools/quality-patches-tool/usage.md). A ferramenta permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce.

A partir de janeiro de 2026, a Adobe Commerce migrará para um cronograma mensal de lançamento de patches com a seguinte estratégia:

- **Correções de segurança isoladas** — As [correções de segurança](versioning-policy.md#isolated-patch) individuais e não cumulativas podem ser lançadas mensalmente e incluir correções de segurança para todas as [linhas de versão ](lifecycle-policy.md) com suporte (inclui suporte regular e estendido).

- **Patches de segurança**—No mínimo, [patches de segurança](versioning-policy.md#security-patch-release) são lançados anualmente (maio) para todas as linhas de versão [com suporte](lifecycle-policy.md). Esses patches incluem todas as correções de segurança isoladas lançadas anteriormente. A Adobe pode lançar patches de segurança adicionais em novembro, se necessário, mas isso não é garantido.

- **Patch** — Um [patch](versioning-policy.md#patch-release) completo para a linha de versão LTS 2.4.x do Adobe Commerce (período de suporte de 3 anos) é lançado anualmente (maio).

- **Patches do Beta**—Dois [patches beta](versioning-policy.md#beta-patch-release) para a linha de lançamento do Adobe Commerce 2.4.x LTS são lançados duas vezes por ano (março e novembro).

Consulte a imagem a seguir para obter detalhes:

![Calendário de lançamento do Adobe Commerce de 2026](../assets/release/release-calendar.drawio.svg)
