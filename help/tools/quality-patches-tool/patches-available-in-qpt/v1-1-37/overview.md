---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
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
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.37

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.37.

O QPT v1.1.37 inclui os seguintes patches:

1. **ACSD-52613**: corrige o problema em que caches e índices são atualizados mesmo quando não são feitas atualizações para `Inventory_source` itens pela API rest.
1. **ACSD-51884**: corrige o problema em que o caminho do cache de imagem do produto se torna incorreto após a execução do comando resize.
1. **ACSD-53628**: corrige o problema em que o relatório de ordem de venda CSV mostra caracteres especiais incorretos.
1. **ACSD-49843**: corrige o problema em que o link no download do produto não fica disponível depois que o item solicitado é faturado automaticamente pela forma de pagamento online com a configuração *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* habilitada.
1. **ACSD-53148**: corrige o problema em que duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável ao carrinho resultavam em dois itens separados no carrinho com o mesmo SKU de produto.
1. **ACSD-47054**: corrige o problema em que a pré-visualização de reindexação executa a reindexação para todos os armazenamentos, causando lentidão.
1. **ACSD-52606**: corrige o problema em que a mensagem de erro *Seu pedido não está pronto para retirada* é exibida quando o usuário clica em **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**: corrige o problema em que a imagem não é atualizada no front-end depois de substituí-la por outra imagem com o mesmo nome.
1. **ACSD-53728**: corrige o problema em que o indexador EAV do produto está demorando mais para ser concluído.
1. **ACSD-53979**: corrige o problema de JS que ocorre na página inicial se a mensagem de boas-vindas contiver aspas simples.
1. **ACSD-52143**: corrige o problema em que as opções personalizadas são removidas após a importação do produto.
1. **ACSD-53750**: corrige o erro de *pipe interrompido ou conexão fechada* durante a reindexação de `catalog_product_price` multithread.

Use o menu à esquerda para navegar até uma página de patch específica.
