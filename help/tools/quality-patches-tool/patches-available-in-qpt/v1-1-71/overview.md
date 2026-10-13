---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '185'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.71

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.71.

O QPT v1.1.71 inclui os seguintes patches:


* **ACSD-60624**: falha ao carregar Imagem para conteúdo vazio nas seções Imagem, Banner e Controle Deslizante em [!DNL Page Builder]
* **ACSD-67089**: problema de paginação na API `inventory/export-stock-salable-qty`, que limita incorretamente `total_count` ao tamanho da página.
* **ACSD-67093**: recuperar pedidos até [!DNL GraphQL] usando o filtro de intervalo de datas retorna resultados incorretos.
* **ACSD-67459**: não é possível importar produtos com descrições maiores que 65.536 caracteres.
* **ACSD-67603**: tempos de processamento longos de geração de mapas do site para produtos com inclusão de imagem habilitada
* **ACSD-67643**: entradas duplicadas são criadas durante atualizações agendadas em ambientes com um alto número de categorias aninhadas.
* **ACSD-67652**: o status do produto do pacote é retornado como indisponível em chamadas [!DNL GraphQL] mesmo com produtos filho e pai em estoque.
* **ACSD-67904**: os pedidos não podem ser feitos se o nome da cidade contiver dígitos (0-9), E comercial (&amp;), ponto (.) ou parênteses ().

Use o menu à esquerda para navegar até uma página de patch específica.
