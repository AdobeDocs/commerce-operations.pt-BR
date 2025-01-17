---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.58'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.58.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f8473bbdedef26b291547d828e47a9ba08a5d142
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.58

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.58.

O QPT v1.1.58 inclui os seguintes patches:

1. **ACSD-48570**: corrige o problema em que a página de redefinição de senha não podia ser acessada clicando no link de [!UICONTROL Admin] redefinição de senha quando **Adicionar Código de Repositório a URLs** estava *habilitado*, o que anteriormente resultava na exibição da página de logon ou de uma página 404.
1. **ACSD-62118**: corrige o problema em que a tabela `sales_order_tax_item` não é totalmente atualizada quando [!DNL B2B] pedidos são feitos usando o método Ordem de Compra.
1. **ACSD-63067**: corrige o problema em que todas as quantidades de produtos são realçadas incorretamente e a mensagem *[!DNL Please specify the quantity of product(s).]* é exibida para todos os produtos em um produto agrupado quando apenas uma quantidade está incorreta.
1. **ACSD-63090**: corrige o problema em que os itens do carrinho de compras são removidos quando um produto é excluído depois de ser adicionado ao carrinho.
1. **ACSD-63182**: corrige o problema em que ocorre um erro ao salvar um produto de pacote duplicado com o **[!DNL MSI]** *habilitado*.
1. **ACSD-63283**: corrige o problema em que a solicitação de itens do registro de presentes causa uma exceção e em que as atualizações do registro de presentes incluem itens que não pertencem ao registro.
1. **ACSD-63299**: corrige o problema em que o preço especial de um produto configurável não é exibido na loja.
1. **ACSD-63325**: corrige o problema em que ocorre um erro `Syntax Error: Unexpected <EOF>` ao enviar uma solicitação [!DNL GraphQL] vazia.
1. **ACSD-63329**: corrige o problema em que os valores padrão para atributos com tipos de entrada **[!UICONTROL Date]** ou **[!UICONTROL Date and Time]** não são definidos ao criar produtos por meio do [!DNL REST API].
1. **ACSD-63572**: corrige o problema em que as tabelas temporárias do indexador `CatalogRule` não são limpas se o processo do indexador for encerrado.
1. **ACSD-63578**: corrige o problema em que clicar no botão **[!UICONTROL Delete]** em **[!UICONTROL Add to Order by SKU]** no [!UICONTROL Admin] não remove o [!DNL SKU].

Use o menu à esquerda para navegar até uma página de patch específica.

