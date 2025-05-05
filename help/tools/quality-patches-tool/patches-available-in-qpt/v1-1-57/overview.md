---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.57'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.57.
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
source-git-commit: fc5c790108a3c62d4591631128743259824c4c6b
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.57

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.57.

O QPT v1.1.57 inclui os seguintes patches:

1. **ACSD-57570**: corrige o problema em que um usuário administrador restrito com acesso a uma determinada loja nem sempre consegue ver todos os catálogos compartilhados aos quais os produtos estão atribuídos ou os clientes que não podem ser salvos, resultando em inconsistências no sistema.
1. **ACSD-58325**: corrige o problema em que o botão [!UICONTROL Import] fica disponível mesmo após um erro de validação.
1. **ACSD-59083**: corrige o problema em que algumas operações de atualização do banco de dados resultam em erro de _Tabela base ou exibição não encontrada_ se a atualização [!DNL mview] estiver sendo executada ao mesmo tempo.
1. **ACSD-61622**: corrige o problema em que [!DNL FedEx] taxas específicas da conta estão ausentes na resposta. ACSD-61622 substitui a correção documentada na migração de integração do método de envio [[!DNL FedEx] de [!DNL SOAP] para [!DNL RESTful API]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api).
1. **ACSD-61895**: corrige o problema em que a consulta de categorias [!DNL GraphQL] retorna categorias com a permissão *permitir*, mesmo que a categoria raiz não tenha a permissão *permitir*.
1. **ACSD-62212**: corrige o problema em que o conteúdo de email [!UICONTROL Forgot Password] não é traduzido para o idioma do modo de exibição de armazenamento.
1. **ACSD-62481**: corrige o problema em que o carrinho de compras do cliente fica vazio mesmo se [!UICONTROL Persistence] estiver habilitado.
1. **ACSD-62629**: corrige o problema em que uma lista de produtos usada em [!UICONTROL Widgets] não respeita a condição de categoria.
1. **ACSD-62635**: corrige o problema em que os produtos relacionados a várias lojas não são exibidos corretamente na consulta de produto do [!DNL GraphQL].
1. **ACSD-62671**: corrige o problema em que a solicitação [!DNL GraphQL] não retorna informações de endereço atualizadas na primeira tentativa.
1. **ACSD-62689**: corrige o problema em que o cliente não pode adicionar Categorias em [!UICONTROL Related Product Rules] e [!UICONTROL Widgets] após a profundidade 4.
1. **ACSD-62708**: corrige o problema em que o tamanho da fonte do editor do [!DNL TinyMCE] 7 no administrador mostra [!UICONTROL pt] e não [!UICONTROL px] após aplicar a correção de [!UICONTROL ACP2E-3430]. Agora, você também pode definir o tamanho da fonte em [!UICONTROL px] em vez de [!UICONTROL pt].
1. **ACSD-62758**: corrige o problema em que os vídeos de produtos não são renderizados corretamente na página de detalhes do [!UICONTROL Configurable Product] se a URL contiver opções selecionadas.
1. **ACSD-62951**: corrige o problema para onde o email [!UICONTROL Credit Memo] é enviado sem incluir itens e totais.
1. **ACSD-62965**: corrige o problema em que uma mensagem *LocalizedException* não é incluída no posicionamento do pedido [!DNL GraphQL response].
1. **ACSD-63286**: corrige o problema em que os produtos atribuídos a um catálogo compartilhado via API não aparecem na loja até que uma reindexação manual seja executada.
1. **ACSD-63326**: corrige o problema em que o administrador é redirecionado para uma página interrompida após fazer um pedido no back-end.


Use o menu à esquerda para navegar até uma página de patch específica.
