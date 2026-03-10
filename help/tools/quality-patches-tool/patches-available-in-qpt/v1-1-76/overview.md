---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.76.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: f56050886f28692286c42102222dfb580e52aef1
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.76

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.76.

O QPT v1.1.76 inclui os seguintes patches:
1. **[ACSD-67370](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370.md)**: corrige vários problemas em que os preços incorretos eram mostrados para os produtos do Pacote em PDP/PLP e na página do carrinho para lojas de várias moedas.
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)**: corrige o erro de tamanho máximo do conjunto de gravação para garantir a limpeza do índice de produto da regra de catálogo implementando duas estratégias de exclusão com base no volume de dados.
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)**: corrige um problema em que colocar um pedido para uma cotação negociável adiciona ou mescla incorretamente linhas de carrinho adicionais à cotação. Agora os produtos são adicionados corretamente ao carrinho de compras depois de sair da última etapa da finalização da cotação negociável.
1. **ACSD-69086**: corrige o problema em que o trabalho cron falha ao limpar as tabelas de log de alterações, causando [!DNL Galera Cluster] falhas ao manipular grandes quantidades de dados.
1. **ACSD-69115**: corrige um problema em que os erros do carrinho de compras não eram exibidos para o usuário administrador ao gerenciar o carrinho de compras de um cliente atribuído a um site não padrão.
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)**: corrige um problema em que a exclusão do site básico padrão e o uso do site secundário como padrão resulta em um erro ao tentar atualizar o preço da camada para o site secundário por meio da API [!DNL REST].
1. **ACSD-69203**: corrige um problema em que o widget **[!UICONTROL Products List]** retorna resultados incorretos quando várias categorias são listadas na condição de categoria.
1. **[ACSD-69261](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261.md)**: corrige um problema em que um cupom da regra de preço do carrinho configurado para uso único por cliente era reutilizado várias vezes devido ao tratamento incorreto do atributo `times_used` em cenários de cancelamento de fatura parcial e quantidade restante.
1. **ACSD-69308**: corrige um problema em que as regras de preço do catálogo não se aplicavam quando `special_price` era definido somente no nível do site (não em **[!UICONTROL All Store Views]**). Após a correção, as regras de preço do catálogo são aplicadas corretamente verificando primeiro a loja padrão do site.
1. **ACSD-69261**: corrige um problema em que um cupom da regra de preço do carrinho configurado para uso único por cliente era reutilizado várias vezes devido ao tratamento incorreto do atributo `times_used` em cenários de cancelamento de fatura parcial e quantidade restante.
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)**: corrige um problema em que as regras de preço do catálogo não se aplicavam quando `special_price` era definido somente no nível do site (não em **[!UICONTROL All Store Views]**).
1. **ACSD-69319**: corrige um problema em que os preços de pacote não eram indexados corretamente quando produtos derivados tinham estoque em fontes personalizadas.
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)**: corrige um problema em que modificar o caso do SKU faz com que o produto pareça estar esgotado no estoque da loja.
1. **ACSD-69331**: corrige um problema em que os criadores de conteúdo na galeria de mídia não podiam criar pastas com apenas a permissão `create_folder`. Após a correção, eles podem criar pastas conforme esperado.
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)**: corrige um problema em que a redução da quantidade de um produto no [!UICONTROL Admin] para menos do que a quantidade anterior em um carrinho interrompeu a capacidade de editar a quantidade de produtos nesse carrinho por meio do GraphQL.
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)**: corrige um problema em que alterações de SKU eram permitidas em produtos com uma atualização agendada ativa. Após a correção, as alterações do SKU são proibidas durante as atualizações ativas; os salvamentos falham com um erro claro e o campo SKU do administrador é desativado. Isso evita inconsistências de Inventário MSI causadas por alterações de SKU durante reversões de preparo.

Use o menu à esquerda para navegar até uma página de patch específica.
