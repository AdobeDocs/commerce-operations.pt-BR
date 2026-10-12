---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.51'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.51.
feature: Tools and External Services
role: Admin, Developer
exl-id: 277b6301-944b-4913-84a3-bbcca2c92ce1
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
source-wordcount: '267'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.51

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.51.

O QPT v1.1.51 inclui os seguintes patches:

1. **ACSD-59786**: corrige o problema em que o GraphQL retorna um erro interno do servidor ao tentar obter uma ID de cotação para uma cotação expirada.
1. **ACSD-60234**: corrige o problema em que um valor incorreto é exibido em [!DNL PayPal] quando o desconto é aplicado por meio do método de pagamento.
1. **ACSD-59967**: corrige o problema em que um erro de JavaScript impede que o [!DNL Google Maps] seja renderizado corretamente.
1. **ACSD-60326**: corrige o problema em que ocorre um erro na consulta do GraphQL para o status de retorno do cliente.
1. **ACSD-60538**: corrige o problema em que, se um produto for desabilitado no *[!UICONTROL All Store Views]* e habilitado somente em escopos de exibição de loja específicos, os atributos do produto não serão exibidos corretamente na resposta do GraphQL, fazendo com que o produto não seja exibido corretamente.
1. **ACSD-60631**: corrige o problema em que o GraphQL retorna um erro quando o mesmo produto simples é atribuído a vários produtos configuráveis.
1. **ACSD-60632**: corrige o problema em que um novo endereço é salvo sempre que uma tentativa de posicionamento de pedido é feita, independentemente de o pedido ser criado com êxito ou não.
1. **ACSD-60816**: corrige o problema em que os scripts [!DNL New Relic Browser Monitoring] inseridos pelo agente APM não são compatíveis com a CSP (Política de Segurança de Conteúdo), impedindo sua execução.
1. **ACSD-61195**: corrige o problema em que nenhum item do carrinho é retornado na última página da solicitação GraphQL do carrinho.

Use o menu à esquerda para navegar até uma página de patch específica.
