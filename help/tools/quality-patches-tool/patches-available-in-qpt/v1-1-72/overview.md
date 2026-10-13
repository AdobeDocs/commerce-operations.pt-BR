---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.72.
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
source-wordcount: '276'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.72

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.72.

O QPT v1.1.72 inclui os seguintes patches:

1. **ACSD-66807**: a tabela `report_viewed_product_index` mostra uma contagem incorreta de exibições de páginas de produtos.
1. **ACSD-67187**: usuários administradores restritos a sites não padrão veem o erro, *&quot;* Crie pelo menos um catálogo compartilhado público para continuar* e não possam acessar o botão **[!UICONTROL Add New Company]** na grade da Empresa.
1. **ACSD-67383**: erro ao fazer logon como um cliente com duas contas de administrador de empresa na mesma sessão.
1. **ACSD-67424**: o valor `updated_at` na resposta da API `GET /carts/search` [!DNL REST] não corresponde ao valor mostrado em **[!UICONTROL Admin panel]** ao usar Cotações Negociáveis.
1. **ACSD-67518**: os relatórios avançados geram linhas de cabeçalho duplicadas quando a contagem de linhas excede o tamanho do lote.
1. **ACSD-67639**: falha ao criar um memorando de crédito para produtos agrupados com **[!UICONTROL Dynamic Price]** definido como *Não*.
1. **ACSD-67696**: `media_gallery` entradas não retornam no nó de produto GraphQL do carrinho após uma liberação de cache.
1. **ACSD-67941**: solicitações GraphQL com nomes de filtro desconhecidos causam logs de exceção do PHP.
1. **ACSD-67946**: a atualização do carrinho mostra banners de erro duplicados.
1. **ACSD-68011**: SKUs não existentes atribuídas ao catálogo compartilhado via API /V1/sharedCatalog/:id/assignProducts.
1. **ACSD-68040**: a página de pesquisa de front-end desacelera em [!DNL MariaDB] 10.6 com um histórico grande.
1. **ACSD-68064**: entradas duplicadas criadas durante atualizações agendadas em ambientes com categorias profundamente aninhadas.
1. **ACSD-68092**: as opções de pacote de produtos são perdidas após vários salvamentos devido à sincronização imprópria entre as atualizações agendadas e os dados de base do produto.
1. **ACSD-68118**: a consulta `customerCart` [!DNL GraphQL] retorna valores de atributo de produto incorretos para exibição de loja.


Use o menu à esquerda para navegar até uma página de patch específica.
