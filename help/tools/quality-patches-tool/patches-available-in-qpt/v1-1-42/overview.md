---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 40db5196-0ba3-49c4-97b7-32f146c67f95
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
source-wordcount: '324'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.42

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.42.

O QPT v1.1.42 inclui os seguintes patches:

1. **ACSD-53658**: corrige o problema em que os dados do produto *[!UICONTROL Recently Viewed]* não são atualizados corretamente na exibição da loja.
1. **ACSD-54626**: corrige o problema em que você não pode criar uma nova regra de ordem de compra (`createPurchaseOrderApprovalRule`) com o atributo `NUMBER_OF_SKUS` via GraphQL.
1. **ACSD-53845**: corrige o problema de tempo limite de conexão do MySQL quando `consumer max_messages` = 0.
1. **ACSD-54890**: corrige o problema em que `aggregate_sales_report_bestsellers_data` causa erros de MySQL devido à falta de espaço no disco `/tmp`.
1. **ACSD-55112**: corrige o problema em que o botão *[!UICONTROL Submit review]* pode ser clicado várias vezes sem validação de [!DNL Google reCAPTCHA v3].
1. **ACSD-54264**: corrige o problema em que a mensagem de erro *Você não pode atualizar o atributo solicitado. A ID da linha: store_id* aparece quando um cliente tenta fazer check-out com uma cotação negociável de outra exibição de loja.
1. **ACSD-54418**: corrige o problema em que uma quantidade fixa de desconto é aplicada incorretamente a cada produto filho do pacote com preço dinâmico.
1. **ACSD-55238**: corrige o problema ao salvar a metadescrição de produto vazia.
1. **ACSD-54966**: corrige o problema em que um código de cupom com uso limitado por cliente não pode ser reutilizado se o pedido anterior falhar.
1. **ACSD-54060**: corrige o problema em que um administrador restrito não pode salvar um produto se ele for filho de outro produto atribuído a um escopo diferente.
1. **ACSD-48910**: corrige o problema em que um produto agrupado atribuído a várias origens fica indisponível depois que um pedido é faturado e enviado, mesmo que tenha uma quantidade diferente de zero.
1. **ACSD-55381**: corrige um erro interno do servidor ao consultar campos `configurable_product_option_uid` e `configurable_product_option_value_uid` de um B2B *[!UICONTROL Requisition list]* via GraphQL.
1. **ACSD-55628**: corrige o carregamento de um arquivo no formulário de registro da empresa e substitui um arquivo para um atributo de cliente na loja.

Use o menu à esquerda para navegar até uma página de patch específica.
