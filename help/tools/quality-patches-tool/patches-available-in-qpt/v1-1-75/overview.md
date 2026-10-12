---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
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
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.75

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.75.

O QPT v1.1.75 inclui os seguintes patches:
1. **ACSD-68289**: corrige um problema em que a pesquisa de texto completo agora retorna produtos correspondentes se a condição de correspondência mínima for atendida em todos os campos pesquisáveis coletivamente, em vez de exigir que a condição seja atendida por um único campo.
1. **ACSD-68359**: corrige o erro *414* ao selecionar **[!UICONTROL Pick in Store]** com carrinhos grandes.
1. **ACSD-68451**: corrige um problema para vários sites em que um administrador de empresa faz logon em um site, cria uma empresa não relacionada em outro site, mas é erroneamente vinculada a essa empresa não relacionada.
1. **ACSD-68517**: corrige um erro de reenvio de formulário nas páginas **[!UICONTROL Catalog]** e **[!UICONTROL Catalog Search]**.
1. **ACSD-68490**: botão **[!UICONTROL Add New Attribute]** visível para o administrador restrito durante a criação do produto configurável.
1. **ACSD-68573**: as permissões de categoria não foram aplicadas aos itens da lista de desejos do cliente, causando exibição e paginação incorretas na loja da web e em [!DNL GraphQL].
1. **ACSD-68615**: corrige o problema em que a CLI de compensação de reserva de estoque mostrava uma exceção se a combinação processada tivesse uma ID de pedido ausente.
1. **ACSD-68793**: corrige um problema em que produtos válidos eram rejeitados incorretamente ao atribuí-los a um catálogo compartilhado.
1. **ACSD-68925**: corrige um problema em que as respostas das solicitações do GraphQL agora estão alinhadas com as especificações do GraphQL sobre HTTP. Um código de resposta 4XX é retornado quando a solicitação não pode ser analisada, não está autorizada ou encontra um problema geral se a solicitação for analisada.

Use o menu à esquerda para navegar até uma página de patch específica.
