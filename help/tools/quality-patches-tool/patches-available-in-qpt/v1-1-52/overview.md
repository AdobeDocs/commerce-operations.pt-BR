---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.52'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.52.
feature: Tools and External Services
role: Admin, Developer
exl-id: e6fc655e-0809-4b47-8be1-1fc36ae30753
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.52

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.52.

O QPT v1.1.52 inclui os seguintes patches:

1. **ACSD-59366**: corrige o problema em que ocorre um erro ao excluir uma equipe que contém usuários desativados que não estão visíveis na lista de equipes.
1. **ACSD-59865**: corrige o problema em que um [!UICONTROL Cart Price Rule] não cancela regras aplicadas anteriormente se a quantidade do produto no carrinho não for suficiente para que as regras sejam aplicadas.
1. **ACSD-59925**: corrige o problema de classificação de itens na galeria de mídia por posição no GraphQL.
1. **ACSD-59952**: corrige o problema em que ocorre um erro ao criar um catálogo compartilhado com uma ID de grupo atribuída a um catálogo compartilhado existente.
1. **ACSD-60590**: melhora o desempenho de geração de *[!UICONTROL Bestsellers Aggregated Daily Reports]* para um grande volume de pedidos feitos.
1. **ACSD-60673**: corrige o problema em que o [!UICONTROL Cart Price Rule] para vários métodos de pagamento no check-out não se aplica adequadamente ao método de pagamento específico.
1. **ACSD-60684**: corrige o problema em que a classificação de produto do GraphQL por vários campos não funciona conforme esperado.
1. **ACSD-60788**: corrige o problema em que scripts personalizados para [!DNL Google Tag Manager] não são executados devido a erros da Política de Segurança de Conteúdo (CSP).
1. **ACSD-61322**: corrige o problema em que Produtos/Categorias não atribuídos ao [!UICONTROL Shared Catalog] para o Padrão (Grupo Geral) ainda estão incluídos no Mapa do Site XML.
1. **ACSD-61366**: corrige o problema em que o comando `setup:static-content:deploy --jobs 4` é executado com vários trabalhos com falha na *Porta deve ser configurada no erro de parâmetro de host* quando a porta é especificada para a conexão de BD.

Use o menu à esquerda para navegar até uma página de patch específica.
