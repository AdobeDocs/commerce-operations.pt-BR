---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.41'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.41.
feature: Tools and External Services
role: Admin, Developer
exl-id: 10e1f4f9-8c6b-45b2-b6ed-0758c8019c8c
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
source-wordcount: '233'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.41

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.41.

O QPT v1.1.41 inclui os seguintes patches:

1. **ACSD-54376**: corrige o problema que ocorre no carrinho de compras quando um produto é removido do catálogo compartilhado depois de já ter sido adicionado ao carrinho.
1. **ACSD-53722**: corrige o problema em que o preço das opções de produto agrupadas muda para $0 quando atualizações agendadas para escopos diferentes se tornam ativas.
1. **ACSD-53643**: corrige o problema em que o pedido tem um total incorreto ao fazer um pedido de compra com produtos desabilitados ou indisponíveis. Isso é corrigido ocultando o botão *[!UICONTROL Place Order]* para essas ordens de compra.
1. **ACSD-54067**: corrige o problema em que um vídeo de produto não é reproduzido em um dispositivo móvel.
1. **ACSD-55414**: melhora o desempenho quando o MariaDB tenta converter a entity_id EAV de string em inteiro.
1. **ACSD-51819**: corrige o problema em que vários pedidos podem ser feitos com a mesma ID de cotação.
1. **ACSD-53118**: corrige o problema em que o *[!UICONTROL Cart Price Rule]* é aplicado usando o código de cupom enquanto o produto tem um atributo vazio.
1. **ACSD-54324**: corrige o problema em que a solicitação requisition_lists do GraphQL não considera configurações de paginação e retorna todos os resultados.

Use o menu à esquerda para navegar até uma página de patch específica.
