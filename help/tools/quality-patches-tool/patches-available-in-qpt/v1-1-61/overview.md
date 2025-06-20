---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.61'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.61.
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.61

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.61.

O QPT v1.1.61 inclui os seguintes patches:

1. **ACP2E-3689**: corrige vários problemas com a exibição da árvore de categoria em níveis mais profundos e refletindo relações de âncora/não âncora.
1. **ACP2E-3705**: corrige um problema em que a execução do cron `indexer_update_all_views` falha quando `MAGE_INDEXER_THREADS_COUNT` é definido.
1. **ACSD-63883**: corrige o problema em que [!UICONTROL Requisition List] retorna um `items_count` incorreto na resposta [!DNL GraphQL].
1. **ACSD-63974**: corrige o problema em que a página [!UICONTROL Requisition List] leva muito tempo para carregar quando há muitos itens, adicionando um recurso de paginação à grade [!UICONTROL Requisition List] na vitrine, que exibe somente partes dos registros limitadas ao número de registros por página, em vez de todos os registros de uma só vez.
1. **ACSD-64178**: corrige o problema em que a página de edição [!UICONTROL Attribute Set] é carregada lentamente se houver milhares de atributos de produto.
1. **ACSD-64209**: corrige o problema em que o agendador cron recupera todas as cotações negociáveis sem excluir aquelas com o status **[!UICONTROL ordered]**, fazendo com que um email ou emails sejam acionados.
1. **ACSD-64431**: a mutação `placeOrder` que contém as informações de código do cupom na solicitação não lança mais um erro interno, mas mostra que o pedido foi feito com êxito.
1. **ACSD-64467**: corrige o problema em que o editor do WYSIWYG aparece vazio após salvar uma descrição de categoria no nível de exibição de repositório.
1. **ACSD-64546**: corrige o problema em que uma mensagem de erro genérica ocorre na interface e uma exceção *Matriz para conversão de cadeia de caracteres* é armazenada nos logs durante a criação do rótulo de remessa UPS, garantindo que o erro real seja exibido na interface e que a mensagem de erro correta seja armazenada nos logs.
1. **ACSD-64684**: corrige o problema em que ocorre um erro de validação ao editar e salvar um cartão-presente com um valor maior que *999* devido à vírgula (separador de milhares) no número *mil (1.000)*.

Use o menu à esquerda para navegar até uma página de patch específica.
