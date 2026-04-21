---
title: Programação de lançamento de patches
description: Saiba quando a Adobe planeja anunciar o lançamento de novos patches e correções de segurança para o Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 4%

---


# Programação de lançamento de patches

A Adobe se esforça continuamente para encontrar o equilíbrio certo entre tornar as atualizações de produtos simples e previsíveis e, ao mesmo tempo, fornecer melhorias aos participantes iniciais mais rapidamente (consulte [política de controle de versão](versioning-policy.md)).

O objetivo deste cronograma é fornecer datas para quando a Adobe planeja anunciar o lançamento de [patches](versioning-policy.md#patch-release) para cada linha de lançamento com suporte do aplicativo Adobe Commerce PHP principal. As versões de correção são oportunidades de atualizar a base de código principal para manter sua plataforma segura, confiável e eficiente.

>[!NOTE]
>
>Para saber mais sobre novos recursos, infraestrutura em nuvem e versões de extensibilidade, consulte a documentação da versão dos [Serviços da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/release-information/release-notes-all).

Além dos patches de qualidade, segurança e beta agendados listados nesta página, a Adobe fornece acesso a [patches individuais](versioning-policy.md#individual-patch) por meio da [Ferramenta de Patches de Qualidade](../tools/quality-patches-tool/usage.md). A ferramenta permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce.

As versões de patch do Adobe Commerce são lançadas com base nas seguintes diretrizes:

- **Arquivo de patch de segurança isolado** — Os [arquivos de patch de segurança](versioning-policy.md#isolated-security-patch-file) individuais e não cumulativos são lançados separadamente para permitir uma correção mais rápida e são incorporados ao próximo patch de segurança completo. Para aplicar um arquivo de patch de segurança isolado, os clientes devem estar na versão de patch de segurança mais recente (a versão mais recente -p) para a linha de lançamento compatível, já que as correções de segurança isoladas são testadas exclusivamente em relação a essa versão.

- **Patches de segurança**—No mínimo, [patches de segurança](versioning-policy.md#security-patch-release) são lançados anualmente para todas as linhas de versão [com suporte](lifecycle-policy.md). Esses patches incluem todos os hotfixes de segurança, conformidade e qualidade lançados anteriormente.  A Adobe pode lançar patches de segurança adicionais, se necessário, mas isso não é garantido.

- **Patch** — Um [patch](versioning-policy.md#patch-release) completo para a linha de versão LTS 2.4.x do Adobe Commerce (período de suporte de 3 anos) é lançado anualmente (maio).

- Os **patches do Alpha**-One [patch alpha](versioning-policy.md#alpha-patch-release) para a linha de lançamento do Adobe Commerce 2.4.x LTS são lançados anualmente.

- **Patches do Beta**—Um [patch beta](versioning-policy.md#beta-patch-release) para a linha de lançamento do Adobe Commerce 2.4.x LTS é lançado anualmente.

Consulte a imagem a seguir para obter detalhes:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![Calendário de lançamento do Adobe Commerce de 2026](../assets/release/release-calendar.png)


## Canais de notificação de versão

A Adobe notifica os clientes sobre novas versões de patches pelos seguintes canais:

- [Boletins e conselhos de segurança do Adobe](https://helpx.adobe.com/br/security/security-bulletin.html#magento)
- Email
- Alertas no produto

>[!NOTE]
>
> Para obter as datas de lançamento de cada versão secundária, patch e segurança, e as datas para o fim do suporte regular, consulte [Versões lançadas](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/versions).
