---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.68'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.68.
feature: Tools and External Services
role: Admin, Developer
exl-id: 74094036-cb1b-419f-b287-ca24d351a448
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
source-wordcount: '278'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.68

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.68.

O QPT v1.1.68 inclui os seguintes patches:

1. **ACSD-58131** Falha na galeria de mídia antiga ao carregar imagens devido ao arquivo de imagem de 0 byte.
1. **ACSD-62146**: o endereço de cobrança selecionado desaparece na página de pagamento de check-out quando a pesquisa de endereço está habilitada e o &quot;Limite de Número de Endereços de Cliente&quot; está definido como 1.
1. **ACSD-62415**: o back-end do Adobe Commerce carrega categorias muito lentamente.
1. **ACSD-65938**: emails de cartão-presente foram enviados mesmo quando a criação da fatura falhou.
1. **ACSD-66072**: os produtos relacionados não são retornados via GraphQL na Página de Detalhes do Produto devido a um erro interno do servidor quando o [!UICONTROL Related Products Rule] está configurado.
1. **ACSD-66082**: não é possível atualizar a imagem de amostra de um produto por meio da importação do produto.
1. **ACSD-66179**: cancelar uma fatura com o tipo de pagamento &quot;Não Capturar&quot; resulta em uma página de erro 404.
1. **ACSD-66233**: os usuários administradores não puderam adicionar produtos às categorias porque o pop-up [!UICONTROL Add Product] não está carregando.
1. **ACSD-66506**: ocorre um erro de backend após a exclusão e reatribuição de produtos do Catálogo Compartilhado.
1. **ACSD-66865**: salvar um **[!UICONTROL Catalog Price Rule]** invalida os indexadores e fornece uma alternativa para reindexar somente os produtos afetados.
1. **ACSD-66889**: erro durante a reindexação do inventário na CLI.
1. **ACSD-66963**: a mutação `estimateTotals` retorna *null* para descontos quando um código de desconto é aplicado a um carrinho com produtos virtuais.
1. **ACSD-66965**: a opção Imprimir na página Lista de Requisições causa um erro.
1. **ACSD-66965**: a opção **[!UICONTROL Print]** na página **[!UICONTROL Requisition List]** causa um erro.
1. **ACSD-67039**: os registros do cliente não foram salvos devido à validação do atributo do sistema `rp_token`.

Use o menu à esquerda para navegar até uma página de patch específica.
