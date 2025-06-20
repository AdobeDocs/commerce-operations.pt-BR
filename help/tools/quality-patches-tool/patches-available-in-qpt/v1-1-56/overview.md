---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.56'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.56.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.56

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.56.

O QPT v1.1.56 inclui os seguintes patches:

1. **ACSD-63244**: corrige os problemas em que um erro de JavaScript impede que o [!DNL Google Maps] seja renderizado corretamente e em que há muitos *TypeError Não Capturados: este._each não é uma função* erros no console no painel [!UICONTROL Admin].
1. **ACSD-63242**: corrige o problema de lentidão de importação ao adicionar produtos de catálogo com mais de 10.000 entradas.
1. **ACSD-63062**: corrige o problema em que cálculos incorretos de desconto do carrinho ocorrem quando várias regras de sobreposição são aplicadas.
1. **ACSD-62979**: corrige o problema em que o uso do [!UICONTROL Store ID] incorreto no cabeçalho do GraphQL causa um erro fatal de memória.
1. **ACSD-62971**: corrige o problema em que importar fontes de estoque com valores não numéricos na coluna *[!UICONTROL Quantity]* resulta na *quantidade* sendo definida como *0*.
1. **ACSD-62872**: corrige o problema na validação de atributo exclusivo, em que as atualizações de agendamento são validadas incorretamente.
1. **ACSD-62755**: corrige o problema em que o [!DNL TinyMCE] 7 requer que o tamanho e a fonte da fonte sejam adicionados especificamente às configurações de inicialização do editor.
1. **ACSD-62670**: corrige o problema em que a exportação de relatórios [!UICONTROL Products Ordered] para CSV e XML retorna um erro.
1. **ACSD-62577**: corrige o problema de desempenho lento de consultas de pesquisa de vitrine otimizando índices de consulta e de tabela.
1. **ACSD-62475**: corrige o problema em que os produtos [!UICONTROL Gift Card] são mesclados incorretamente no carrinho.
1. **ACSD-62428**: corrige o problema em que `is_out_of_stock` está definido como um valor incorreto no índice de pesquisa do catálogo quando [!DNL SKU] não está definido como um atributo pesquisável.
1. **ACSD-62355**: melhora o tempo de carregamento da página de edição do produto configurável quando o produto configurável é baseado em muitos atributos com muitos valores.
1. **ACSD-61805**: corrige o problema em que os produtos permanecem sem estoque na loja após a atualização do status do pedido pendente via [!DNL REST API].
1. **ACSD-60811**: corrige o problema em que a atualização do status da ordem com um valor ou comentário personalizado só é possível se o status atual for *[!UICONTROL Processing]* ou *[!UICONTROL Fraud]*.
1. **ACSD-62952**: corrige o problema em que a data [!UICONTROL Gift Registry] é exibida de forma imprecisa na vitrine.
1. **ACSD-55339**: corrige o problema em que um produto [!DNL SKU] iniciando com *0* (zero) remove o *0*, impedindo que a cotação seja atualizada.

Use o menu à esquerda para navegar até uma página de patch específica.
