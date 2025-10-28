---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.72.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3493a89d40e3dee377be715e71e2f977a3afd382
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.72

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.72.

O QPT v1.1.72 inclui os seguintes patches:
1. **ACSD-68040**: a página de pesquisa de front-end desacelera em [!DNL MariaDB] 10.6 com um histórico grande.
1. **ACSD-67941**: solicitações GraphQL com nomes de filtro desconhecidos causam logs de exceção do PHP.
1. **ACSD-68064**: a criação de atualizações agendadas resulta em entradas duplicadas em ambientes com um alto número de categorias aninhadas.
1. **ACSD-66807**: a tabela `report_viewed_product_index` mostra uma contagem incorreta de exibições de páginas de produtos.
1. **ACSD-67383**: faça logon como Cliente com duas contas de administrador de empresa na mesma sessão, causando um erro *Nenhuma entidade com cartId*.
1. **ACSD-67518**: os relatórios avançados geram linhas de cabeçalho duplicadas quando a contagem de linhas excede o tamanho do lote.
1. **ACSD-67639**: falha ao criar um memorando de crédito para produtos agrupados com **[!UICONTROL Dynamic Price]** definido como *Não*.
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)**: `media_gallery` entradas não retornam no nó de produto GraphQL do carrinho após uma liberação de cache.
1. **ACSD-67946**: as atualizações do carrinho mostram banners de erro duplicados.
1. **ACSD-68011**: SKUs não existentes atribuídas ao catálogo compartilhado via API /V1/sharedCatalog/:id/assignProducts.
1. **ACSD-68118**: a consulta `customerCart` [!DNL GraphQL] retorna valores de atributo de produto incorretos para exibição de loja.
1. **ACSD-68092**: as opções de pacote de produtos são perdidas após vários salvamentos devido à sincronização imprópria entre as atualizações agendadas e os dados de base do produto.
1. **ACSD-67424**: o valor `updated_at` na resposta da API `GET /carts/search` [!DNL REST] não corresponde ao valor mostrado em **[!UICONTROL Admin panel]** ao usar Cotações Negociáveis.
1. **ACSD-67187**: usuários administradores restritos a sites não padrão veem o erro, *&quot;*Crie pelo menos um catálogo compartilhado público para continuar* e não possam acessar o botão **[!UICONTROL Add New Company]** na grade da Empresa.

Use o menu à esquerda para navegar até uma página de patch específica.
