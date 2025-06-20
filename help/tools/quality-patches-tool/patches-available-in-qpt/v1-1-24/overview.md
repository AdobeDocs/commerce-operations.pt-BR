---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.24.
feature: Tools and External Services
role: Admin
exl-id: 7f88a28b-f166-4c5b-8d69-239c57cc4001
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Visão geral da v1.1.24 do [!DNL Quality Patches Tool] (QPT)

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.24.

O QPT v1.1.24 inclui os seguintes patches:

1. **ACSD-45168**: corrige o problema em que URLs amigáveis para SEO não são geradas para produtos que têm atributos de *url_key* substituídos no nível de exibição da loja.
1. **ACSD-46617**: corrige o problema em que o botão **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que o *Valor Mínimo do Pedido* configurado.
1. **ACSD-46770**: corrige o problema em que emails de pedido de administrador são enviados mesmo quando a *Confirmação de pedido de email* está desmarcada.
1. **ACSD-46865**: corrige o problema em que a grade [!UICONTROL Shipment and Credit Memo] não é preenchida quando a indexação assíncrona está habilitada.
1. **ACSD-47004**: corrige o problema em que o IVA não é aplicado a um endereço de cobrança sem uma ID de IVA.
1. **ACSD-47079**: corrige o problema em que o status do estoque de produtos compostos (agrupados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado via REST API POST /rest/V1/inventory/source-items.
1. **ACSD-47137**: melhora a velocidade de carregamento da galeria de imagens quando a pasta pub/media é muito grande.
1. **ACSD-47336**: correções *Algo deu errado.Erro* ao dispensar notificações no Administrador do Commerce.
1. **ACSD-47559**: corrige o problema em que a área Visualizar Modelo de Email não está totalmente visível.
1. **ACSD-47803**: corrige o problema em que amostras de produtos configuráveis e sem estoque são exibidas como disponíveis.
1. **ACSD-47920**: corrige o problema em que os pedidos podem ser feitos por meio da API Rest como um usuário convidado mesmo quando a *Permitir check-out de convidado* está desativada.
1. **ACSD-47955**: corrige o problema em que a GraphQL não exibe o desconto do carrinho corretamente.

Use o menu à esquerda para navegar até uma página de patch específica.
