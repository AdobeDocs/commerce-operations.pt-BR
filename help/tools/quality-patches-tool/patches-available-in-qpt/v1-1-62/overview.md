---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.62'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.62.
feature: Tools and External Services
role: Admin, Developer
exl-id: be8ffedc-b589-4a30-ba9a-eed705696825
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
source-wordcount: '238'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.62

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.62.

O QPT v1.1.62 inclui os seguintes patches:

1. **ACSD-63406**: corrige o problema em que as aspas persistentes expiradas não são apagadas por nenhum trabalho cron quando o trabalho `persistent_clear_expired` cron é executado.
1. **ACSD-63520**: corrige o problema em que imagens adicionadas através do **[!UICONTROL Configurations]** no painel de administração não aderem ao limite de tamanho máximo do upload.
1. **ACSD-64523**: corrige o problema em que novos produtos podem ser criados sem um nome por meio do processo de importação (via administrador ou API), fazendo com que a interface do administrador seja interrompida e resultando em produtos inválidos.
1. **ACSD-64532**: corrige o problema em que uma variável ENV definida como *false* é tratada como uma cadeia de caracteres *false*, em vez de um booleano false.
1. **ACSD-64592**: corrige o problema em que o link de declaração do email para um cartão-presente em lojas não padrão sempre redireciona a declaração do cartão-presente para o site padrão.
1. **ACSD-65164**: corrige o problema em que a mensagem de erro *Algumas das opções de item selecionadas não estão disponíveis no momento* ocorre ao reordenar um produto configurável com uma única opção personalizada de caixa de seleção selecionada.
1. **ACSD-64732**: corrige o problema em que controladores de terceiros não eram armazenados em cache corretamente com segmentos de clientes.

Use o menu à esquerda para navegar até uma página de patch específica.
