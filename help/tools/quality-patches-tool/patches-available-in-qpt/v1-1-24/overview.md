---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.24.
feature: Tools and External Services
role: Admin
exl-id: 7f88a28b-f166-4c5b-8d69-239c57cc4001
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%
---
# Visão geral da v1.1.24 do [!DNL Quality Patches Tool] (QPT)

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.24.

O QPT v1.1.24 inclui os seguintes patches:

1. **ACSD-45168**: corrige o problema em que URLs amigáveis para SEO não são geradas para produtos que têm atributos de *url_key* substituídos no nível de exibição da loja.
1. **ACSD-46617**: corrige o problema em que o botão **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que o *Valor Mínimo do Pedido* configurado.
1. **ACSD-46770**: corrige o problema em que emails de pedido de administrador são enviados mesmo quando a *Confirmação de pedido de email* está desmarcada.
1. **ACSD-46865**: corrige o problema em que a grade [!UICONTROL Shipment and Credit Memo] não é preenchida quando a indexação assíncrona está habilitada.
1. **ACSD-47004**: corrige o problema em que o IVA não é aplicado a um endereço de cobrança sem uma ID de IVA.
1. **ACSD-47079**: corrige o problema em que o status do estoque de produtos compostos (agrupados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado via REST API POST /rest/V1/inventory/source-items.
1. **ACSD-47137**: melhora a velocidade de carregamento da galeria de imagens quando a pasta pub/media é muito grande.
1. **ACSD-47336**: correções *Algo deu errado.* erro ao dispensar notificações no Commerce Admin.
1. **ACSD-47559**: corrige o problema em que a área Visualizar Modelo de Email não está totalmente visível.
1. **ACSD-47803**: corrige o problema em que amostras de produtos configuráveis e sem estoque são exibidas como disponíveis.
1. **ACSD-47920**: corrige o problema em que os pedidos podem ser feitos por meio da API Rest como um usuário convidado mesmo quando a *Permitir check-out de convidado* está desativada.
1. **ACSD-47955**: corrige o problema em que a GraphQL não exibe o desconto do carrinho corretamente.

Use o menu à esquerda para navegar até uma página de patch específica.
