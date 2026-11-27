---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.86'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.86.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 41f455b05b7afecd8a476188c3b723a8e02235a4
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.86

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.86.

O QPT v1.1.86 inclui os seguintes patches:


1. **[ACP2E-5046](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5046.md)**: corrige o problema em que atualizar a página ao criar um pedido no Administrador adiciona a mesma SKU várias vezes.
1. **[ACP2E-3094](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3094.md)**: Corrige o problema em que visualizar ou editar **[!UICONTROL Category Permissions]** para uma categoria com muitas permissões pode fazer com que o navegador pare de responder.
1. **[ACP2E-5050](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5050.md)**: Corrige o problema em que visualizar ou salvar um RMA no Administrador não exibe o número de RMA no relatório **[!UICONTROL Action Logs]**.
1. **ACP2E-5057**: corrige o problema em que [!DNL GraphQL] consultas de produtos de pacotes retornam preços de opções de pacotes globais em vez de preços específicos de sites quando **[!UICONTROL Catalog Price Scope]** está definido como **[!UICONTROL Website]**.
1. **[ACP2E-5071](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5071.md)**: corrige o problema em que a mensagem de indisponibilidade de estoque nem sempre é exibida na página do produto quando o carrinho do comprador já contém a quantidade total disponível.
1. **[ACP2E-5061](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5061.md)**: corrige o problema em que uma regra de merchandising de categoria não pode combinar condições AND com uma condição que corresponde a qualquer um dos vários valores.
1. **ACP2E-5094**: corrige o problema em que os carregamentos de página são significativamente mais lentos quando uma variável de ambiente `MAGENTO_DC_*` é definida.
1. **[ACP2E-5134](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5134.md)**: corrige o problema em que a remoção de um produto incluído em um pacote do Catálogo Compartilhado de uma empresa deixa o produto do pacote no carrinho de compras e causa um erro no carrinho e durante o check-out.
1. **[ACP2E-5118](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5118.md)**: corrige o problema em que a visualização do [!DNL Page Builder] não é renderizada quando o cache do **[!UICONTROL Translations]** está desabilitado.
1. **ACP2E-5146**: corrige o problema em que um usuário Administrador restrito a sites específicos não pode excluir clientes quando um cliente em outro site tem a mesma ID que o usuário Administrador.
1. **[ACP2E-5176](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5176.md)**: corrige o problema em que eventos de comércio eletrônico enviados para o Google Analytics 4 por meio do Google Tag Manager usam o formato Universal Analytics e omitem vários eventos de check-out.
1. **ACP2E-5185**: corrige o problema em que mover uma categoria na árvore de categorias exibe o erro `There was a category move error` ou demora vários minutos para ser concluído quando o repositório tem muitas regravações de URL.
1. **[ACP2E-4191](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-4191.md)**: corrige o problema em que determinadas solicitações da API REST entram em um loop infinito quando o cache de tipos e atributos de EAV está desabilitado.
1. **[ACP2E-4973](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-4973.md)**: corrige o problema em que a alternância de **[!UICONTROL In-Store Delivery]** para outro método de entrega não limpa o endereço de armazenamento associado do carrinho.
1. **ACP2E-5221**: corrige o problema em que o indexador **[!UICONTROL Catalog Product Permissions]** demora significativamente mais quando o **[!UICONTROL Quick Order]** é habilitado em instalações com muitas lojas e grupos de clientes.
1. **[ACP2E-5248](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5248.md)**: Corrige o problema em que os usuários Administradores sem a permissão **[!UICONTROL Edit Product Status]** veem o erro de substituição *null como matriz* ao abrir a página **[!UICONTROL Add Product]** no PHP 8.5.
1. **[ACP2E-5245](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5245.md)**: corrige o problema em que um cliente recém-registrado que usa o mesmo endereço para remessa e cobrança em seu primeiro pedido vê esse endereço listado duas vezes durante o próximo check-out.
1. **ACP2E-5254**: corrige o problema em que os produtos adicionados a uma lista de requisições não aparecem quando um cliente abre a lista até que o cache seja limpo.
1. **ACP2E-5268**: corrige o problema em que a criação de um produto configurável falha quando **[!UICONTROL Enable Frontend Resize]** está definido como **[!UICONTROL No]**.
1. **[ACP2E-3752](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3752.md)**: corrige o problema em que o processamento de importação de produtos gera o erro *Aviso: Chave de matriz indefinida &quot;apply_to&quot;* quando muitas operações de importação de produtos são criadas.
1. **ACP2E-5280**: corrige o problema em que os clientes encontram um erro ao entrar enquanto o **[!UICONTROL Category Permissions]** está habilitado.
1. **ACP2E-5295**: corrige o problema em que a reindexação paralela de preços de produtos falha com o erro `Fail in child process` quando executada após o indexador **[!UICONTROL Inventory]** no mesmo processo.
1. **ACP2E-5298**: corrige o problema em que os usuários administradores com acesso somente para visualização às regras de preço do carrinho podem gerar ou excluir códigos de cupom.
1. **ACP2E-5333**: Corrige o problema em que a atualização de um segmento de cliente com uma condição **[!UICONTROL Total Number of Orders]** que usa o operador **[!UICONTROL is not]** e um valor de um ou mais falha com o erro `Unknown operator specified`.
1. **[ACP2E-5425](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5425.md)**: corrige o problema em que os clientes recebem emails de confirmação de pedido duplicados para o mesmo pedido.

Use o menu à esquerda para navegar até uma página de patch específica.
