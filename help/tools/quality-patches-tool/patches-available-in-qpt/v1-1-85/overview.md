---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-11-18T22:14:27.542Z'
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a1cc81ee1a8d0bbcbea322558da75a31e65d66a4
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%
---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.85

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.85.

O QPT v1.1.85 inclui os seguintes patches:

1. **[ACP2E-4929](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-4929.md)**: Corrige o problema em que os rótulos de atributo na página Comparar Produtos exibem traduções de uma exibição de repositório diferente em vez da exibição de repositório atual.
1. **ACP2E-5075**: corrige o problema em que uma regra de preço de carrinho de valor fixo com uma condição de categoria aplicava incorretamente um desconto a todos os filhos de um produto de pacote de preço dinâmico quando a regra correspondia somente ao produto pai do pacote.
1. **ACP2E-5077**: corrige o problema em que `customerCart` consultas simultâneas do GraphQL ou `POST /V1/carts/mine` solicitações REST criam carrinhos ativos duplicados para clientes que ainda não têm um carrinho ativo.
1. **ACP2E-5088**: corrige o problema em que o carrinho de compras persistente de um cliente é limpo quando a sessão expira.
1. **[ACP2E-3991](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-3991.md)**: corrige o problema em que o endereço IP do cliente não é determinado corretamente.
1. **ACP2E-5092**: corrige o problema em que a página **[!UICONTROL Company Profile]** e a página Editar Cliente Admin exibem um erro quando um endereço de empresa salvo sem uma região posteriormente tem uma região adicionada ao seu país.
1. **ACP2E-5124**: Corrige o problema em que o botão **[!UICONTROL Import]** permanece disponível nos resultados da validação após a falha da validação quando o **[!UICONTROL Validation Strategy]** está definido como **[!UICONTROL Stop on Error]**.
1. **AC-17456**: corrige o problema em que a edição do escopo **[!UICONTROL Global]** na página **[!UICONTROL Design Configuration]** do Painel de Administração retorna um erro *HTTP 500* no PHP 8.4 e 8.5.
1. **ACP2E-5212**: corrige o problema em que **[!UICONTROL Quick Order]** aceita arquivos não CSV renomeados com uma extensão `.csv`.
1. **ACP2E-5300**: Corrige o problema em que pesquisas por palavras-chave para vários números de ordem separados por espaços ou vírgulas na grade do Painel de Administração **[!UICONTROL Orders]** não retornam ordens correspondentes.
1. **ACP2E-5354**: corrige o problema em que atualizar um cliente por meio da API REST faz com que um cliente associado a uma conta da empresa apareça várias vezes na grade Admin **[!UICONTROL Customers]**.
1. **ACP2E-5208**: corrige o problema em que a seção **[!UICONTROL Requisition List]** é recarregada em cada navegação de página da Storefront, mesmo quando nenhuma alteração é feita.

Use o menu à esquerda para navegar até uma página de patch específica.
