---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.54.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
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
source-wordcount: '300'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.54

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.54.

O QPT v1.1.54 inclui os seguintes patches:

1. **ACSD-60267**: corrige o problema em que o FPT (Imposto Fixo do Produto) se aplica corretamente ao adicionar produtos simples com FPT diretamente ao carrinho, mas falha ao selecionar esses produtos por meio de opções de produto configuráveis.
1. **ACSD-61103**: corrige o problema em que a contagem de falhas na tabela `customer_entity` não é redefinida para zero depois que um cliente faz logon por meio de pontos de extremidade de API.
1. **ACSD-61134**: corrige o problema em que o método de pagamento [!DNL Braintree Vault] é automaticamente desmarcado no fluxo de trabalho de check-out quando um comprador atualiza seu endereço de cobrança ao desmarcar a caixa de seleção *[!UICONTROL My billing and shipping address are the same]*.
1. **ACSD-61199**: corrige o problema em que a guia de hierarquia de página do CMS não exibe uma estrutura de árvore adequada ao editar uma página do CMS com uma hierarquia existente.
1. **ACSD-61200**: corrige o problema em que os cálculos para *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]* em vendas estão sem o *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]*, causando discrepâncias nos dados da ordem de venda.
1. **ACSD-61522**: corrige o problema em que é possível inserir endereços de email nos campos *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* do cliente convidado e enviar emails de confirmação de pedido inválidos.
1. **ACSD-61756**: melhora o desempenho de `AdvancedSalesRule` filtros.
1. **ACSD-61799**: corrige o problema em que o desconto total é calculado incorretamente quando várias regras de carrinho com descontos fixos são aplicadas à cotação.
1. **ACSD-61845**: corrige o erro que ocorre quando uma solicitação é enviada somente com o cabeçalho de aceitação *text/html*.
1. **ACSD-62056**: corrige o problema em que o carregamento de imagens para um produto configurável falha se o MSI estiver instalado.
1. **ACSD-62485**: corrige o problema em que o consumidor `async.operations.all` para de funcionar quando uma empresa é criada.

Use o menu à esquerda para navegar até uma página de patch específica.
