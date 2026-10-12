---
title: Práticas recomendadas para extensões
description: Saiba como evitar problemas de desempenho causados por extensões de terceiros do Adobe Commerce.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%
---
# Práticas recomendadas para extensões

As extensões de terceiros (módulos) do Adobe Commerce têm o potencial de causar vários problemas que podem afetar negativamente o desempenho da loja. Você pode evitar esses problemas seguindo estas práticas recomendadas:

- Desenvolva suas integrações e personalizações do Commerce usando a [extensibilidade fora do processo](https://developer.adobe.com/commerce/extensibility/) sempre que possível para facilitar a manutenção e a atualização.
- Baixe e compre extensões de terceiros de uma fonte confiável, como o [Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html).
- Atualize todas as extensões de terceiros para a versão mais recente.
- Se não conseguir manter suas extensões de terceiros atualizadas, considere usar extensões diferentes.
- Ao planejar uma atualização para uma nova versão do Adobe Commerce, verifique se as extensões de terceiros instaladas são compatíveis com a nova versão e atualize as extensões, se necessário.

>[!NOTE]
>
> Todas as extensões disponíveis no Adobe Commerce Marketplace são necessárias para manter a compatibilidade com as novas versões do Commerce. Consulte [Compatibilidade de versão](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases).

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Informações adicionais

- [Práticas recomendadas para o planejamento de atualizações](../../../upgrade/prepare/best-practices.md)
- Uso de extensões de terceiros com o Adobe Commerce na infraestrutura em nuvem
  - [Tecnologias e requisitos - Desenvolvimento e teste](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/overview#cloud-req-devtest)
  - [Por que testar totalmente a integração e o preparo?](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
