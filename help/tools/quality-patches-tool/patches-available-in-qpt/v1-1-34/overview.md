---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
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
source-wordcount: '285'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.34

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.34.

O QPT v1.1.34 inclui os seguintes patches:

1. **ACSD-52277**: corrige o problema em que um usuário administrador não é redirecionado corretamente após selecionar a exibição da loja ao criar uma nova ordem no administrador.
1. **ACSD-50813**: corrige o problema em que um administrador não pode adicionar produtos agrupados contendo uma barra na SKU com a funcionalidade [!UICONTROL Add Products by SKU] à ordem do administrador.
1. **ACSD-51630**: corrige o problema em que uma grande quantidade de mensagens do sistema atrasa o download de páginas de administração.
1. **ACSD-51853**: corrige o problema em que os estilos de texto copiados não são aplicados quando se usa [!DNL Page Builder].
1. **ACSD-52160**: corrige o problema em que um resultado de validação de produto em relação à regra de preço do carrinho não é avaliado corretamente, com base na condição de regra *Se um item for ENCONTRADO/NÃO ENCONTRADO no carrinho com Todas/Qualquer uma dessas condições true*.
1. **ACSD-51636**: corrige o problema em que um administrador não pode adicionar novos usuários da seção de conta do cliente apesar de ter todas as funções e permissões necessárias.
1. **ACSD-51739**: corrige o problema em que um erro é retornado quando o `structure_id` é solicitado em uma solicitação GraphQL `CompanyTeam`.
1. **ACSD-51857**: corrige o problema em que o desempenho lento do relatório cron do `aggregate_sales_report_bestsellers_data` afeta tabelas de banco de dados `sales_order` e `sales_order_item` grandes.
1. **ACSD-48448**: corrige o problema em que há um problema de condição de corrida ocorrendo durante cancelamentos de pedidos, o que causa entrada duplicada na tabela *inventory_reservation*.
1. **ACSD-52689**: corrige o problema em que as imagens não podem ser carregadas no armazenamento do [!DNL Amazon S3] usando a API REST.

Use o menu à esquerda para navegar até uma página de patch específica.
