---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.25'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.25.
feature: Tools and External Services
role: Admin
exl-id: a9953394-b2dd-4e07-a280-378bef2b9b0f
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
source-wordcount: '304'
ht-degree: 0%
---
# Visão geral do [!DNL Quality Patches Tool] (QPT) v1.1.25

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.25.

O QPT v1.1.25 inclui os seguintes patches:

1. **ACSD-47292**: corrige o problema em que os produtos empacotados esgotados não estão disponíveis na resposta da GraphQL se o *mostrar produtos esgotados* estiver definido como *Sim*.
1. **ACSD-47520**: corrige o problema em que os clientes perdem pontos de premiação quando um memorando de crédito é criado.
1. **ACSD-47910**: corrige o problema de pedidos, faturas, remessas e avisos de crédito ausentes nas respectivas grades de entidade.
1. **ACSD-48044**: corrige o problema em que a aplicação de vários cartões-presente a um único pedido com remessa múltipla impede que os pedidos sejam feitos.
1. **ACSD-48058**: corrige o problema em que a reindexação de preço do produto não funciona se o produto do pacote não estiver atribuído a nenhum site.
1. **ACSD-48234**: corrige o problema em que o resultado da pesquisa no catálogo mostra uma contagem de itens de categoria incorreta quando a opção *mostrar indisponível* está habilitada.
1. **ACSD-48262**: corrige o problema em que os produtos não estão visíveis no front-end quando a configuração *[!UICONTROL Allow All Products Per Page]* está definida como *Sim*.
1. **ACSD-48293**: corrige o problema em que os produtos compostos ficam sem estoque quando os produtos secundários que foram vendidos são devolvidos ao estoque.
1. **ACSD-48300**: corrige o problema em que um retorno não pode ser criado se o produto configurável for removido.
1. **ACSD-48313**: corrige o problema em que a coluna *configurable_variation* não é analisada se o valor do atributo contiver uma vírgula. O mesmo algoritmo de análise é usado para *additional_attributes*.
1. **ACSD-48627**: corrige o problema em que o produto configurável indisponível causa um erro ao enviar uma solicitação do GraphQL para obter detalhes do carrinho.

Use o menu à esquerda para navegar até uma página de patch específica.
