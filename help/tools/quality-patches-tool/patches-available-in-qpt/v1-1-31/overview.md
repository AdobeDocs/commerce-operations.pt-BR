---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.31.
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
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
source-wordcount: '173'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.31

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.31.

O QPT v1.1.31 inclui os seguintes patches:

1. **ACSD-50817**: otimiza o trabalho cron `sales_clean_quotes` para ser executado mais rápido adicionando um índice composto em `store_id` e `updated_at` colunas na tabela de aspas.
1. **ACSD-50345**: corrige o problema em que: [!DNL Google reCAPTCHA v2] não é recarregado após o envio de um pagamento com falha, [!DNL Google reCAPTCHA v3 Invisible] não está trabalhando no check-out e o pedido não pode ser feito e o evento [!UICONTROL PlaceOrder] não foi disparado.
1. **ACSD-49392**: corrige o problema em que o status do pedido muda para fechado após um reembolso parcial para um produto agrupado.
1. **ACSD-51036**: corrige o problema em que as condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição das informações de status de remessa na tabela [!UICONTROL Items Ordered].
1. **ACSD-50858**: corrige o problema em que um cupom é marcado incorretamente como usado após uma falha no pagamento por cartão.

Use o menu à esquerda para navegar até uma página de patch específica.
