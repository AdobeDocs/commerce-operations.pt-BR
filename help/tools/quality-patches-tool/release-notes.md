---
title: Notas de versão
description: Saiba mais sobre os patches disponíveis para Adobe Systems Comércio e os problemas que eles resolvem.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: d870d98caf2b2576f3bf179e860e711d1cea9afc
workflow-type: tm+mt
source-wordcount: '21346'
ht-degree: 0%

---

# Notas de versão

O [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fornece patches individuais desenvolvidos pelo Adobe e pela comunidade Magento Open Source. Ela permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce. Você pode aplicar patches a projetos Adobe Commerce e Magento Open Source, independentemente de quem os desenvolveu. Por exemplo, você pode aplicar uma correção desenvolvida pela comunidade para projetos do Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) para obter instruções sobre como aplicar patches aos seus projetos do Adobe Commerce. See [[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in the Software Update Guide to review a full list of released patches.

>[!INFO]
>
>Para obter informações sobre [!DNL quality patches] criado pela Comunidade para o Magento Open Source, consulte as [notas de versão](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o erro *Chamada para método indefinido RefletionUnionType::getName()* que ocorre ao instalar as versões 2.4.4-pX.
* **ACSD-45049** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6) - Corrige o problema em que a configuração de atributo *[!UICONTROL Is required]* de um cliente não funciona corretamente de acordo com o escopo do site no Administrador.
* **ACSD-46938** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema no desempenho da recriação de gatilhos de BD durante `setup:upgrade`.
* **ACSD-48210** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a atualização de um atributo *[!UICONTROL Website Scope]* em uma exibição de repositório específica substitui os valores de atributo no escopo global.
* **ACSD-54887** (for Adobe Commerce and Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Fixes the issue where the customer shopping cart gets cleared after the customer session has expired with [!UICONTROL Persistent Shopping Cart] enabled.
* **ACSD-58141** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.8) - Fixes the issue where PHPSESSID regenerates on POST requests on the storefront area for a logged-in customer if the [!DNL L2 Redis cache] is enabled and the customer is updated from Admin.
* **ACSD-58352** (for Adobe Commerce >=2.4.4 &lt;2.4.7) - Fixes the issue where return attribute labels for the default store view are returned via GraphQL API when a non-default store view is specified in the request header.
* **ACSD-58442** (for Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - Fixes the issue where devices with a width of 768px are treated as mobile, causing the menu and header to load in a mobile view instead of desktop.
* **ACSD-58790** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige a funcionalidade de pinçar para zoom nas imagens da página de detalhes do produto na exibição móvel no [!DNL Chrome].
* **ACSD-59036** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige uma exceção que ocorre ao carregar preços de produtos com limites inferiores e superiores iguais a $0.
* **ACSD-59229** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que as informações relacionadas ao grupo de clientes são salvas no segmento errado devido ao valor antigo do X-Magento-Vary na solicitação.
* **ACSD-59378** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que as substituições de URL de nível de repositório são atualizadas incorretamente durante a importação.
* **ACSD-59514** (para Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - Corrige o problema em que os formulários na área de Administração com [!DNL Page Builder] exibem o erro *[!DNL Page Builder]que foi renderizado por 5 segundos sem liberar bloqueios.* no console de navegador após o envio do formulário, e as alterações não podem ser salvas.
* **ACSD-60303** (para Adobe Commerce >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Corrige o problema em que um pedido do administrador não pode ser feito se a minificação de HTML estiver ativada.
* **ACSD-60441** (para Adobe Commerce e Magento Open Source 2.4.4-p9 || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Corrige o problema com a atualização de clientes por meio do ponto de extremidade `V1/customers` [!DNL REST API] ao usar o token de acesso de integração gerado do back-end.
* Patches atualizados: ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que as imagens de produtos são removidas após a exclusão de uma atualização de preparo.
* **ACSD-57086** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que os pedidos feitos em sites não padrão com termos e condições habilitados não são processados corretamente.
* **ACSD-57588** (para Adobe Systems Comércio e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where shipping an order to multiple addresses triggers an error during region ID processing.
* **ACSD-57643** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que produtos com opções personalizadas são adicionados incorretamente ao carrinho de compras por meio do GraphQL.
* **ACSD-57846** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a pesquisa de produtos da GraphQL com um filtro de preço zero não retorna resultados devido a uma exceção.
* **ACSD-57941** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que as opções do produto são atribuídas incorretamente à loja do administrador em vez de suas respectivas lojas.
* **A configuração ACSD-58375** (para configuração Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the wrong *[!DNL YouTube API Key]* causa um erro ao adicionar um [!DNL YouTube] vídeo no nível de armazenamento visualização.
* **ACSD-58739** (para Adobe Systems Comércio e Magento Open Source >=2.4.7 &lt;2.4.8) - Fixes the issue where partial reindexing throws an error.
* **ACSD-58446** (para Adobe Systems Comércio >=2.4.6 &lt;2.4.7) - Fixes the issue where when deleting a team with child users or teams irrespective of their status (inactive), the system provides an uninformative error message not consistent with the UI.
* **ACSD-58054** (para Adobe Systems Comércio >=2.4.4 &lt;2.4.6) - Fixes the issue where it is possible to generate customer tokens for inactive customers via API.
* **ACSD-58163** (para Adobe Systems Comércio >=2.4.3 &lt;2.4.7) - Fixes the issue where a *[!UICONTROL Cart Price Rule]* não aplica um desconto para um cliente convidado no carrinho correspondente *[!UICONTROL Customer Segment]* sem um código cupom.
* **ACSD-57045** (para Adobe Systems Comércio >=2.4.5 &lt;2.4.7) - Fixes the issue where URL rewrites cause infinite page looping after *[!UICONTROL Website Root]* está desmarcado de *[!UICONTROL Hierarchy]*.
* Patches atualizados: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a mutação `mergeCart` falha com um &quot;*Erro Interno do Servidor*&quot; na resposta [!DNL GraphQL] ao mesclar carrinhos de origem e destino que têm os mesmos itens de pacote.
* **ACSD-56546** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que os produtos configuráveis e agrupados são exibidos como **Sem Estoque** na loja quando a **exibição da configuração do produto** está *Desabilitada*.
* **ACSD-56635** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que o cliente importado é duplicado com o mesmo endereço de email quando uma importação é usada com **compartilhamento de conta** definido como *Global*.
* **ACSD-56741** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige a mensagem de erro &quot;*Tentando acessar o deslocamento da matriz no valor do tipo nulo*&quot; que é exibida durante `setup:upgrade` quando o banco de dados contém um gatilho [!DNL MySQL] personalizado não relacionado ao mecanismo de indexação e [!DNL MView].
* **ACSD-57315** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue when a new transaction is created in [!DNL PayPal Payflow Pro] each time the [!UICONTROL Fetch] button is clicked on the **[!UICONTROL View transaction]** screen in the Admin.
* **ACSD-57337** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige o problema em que um usuário administrador com restrições de acesso a sites específicos pode ver empresas de todos os sites na grade **[!UICONTROL Companies]**.
* **ACSD-57394** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue of incorrect product sorting by multiple sort fields in [!DNL GraphQL].
* **ACSD-57565** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o painel **[!UICONTROL Order]** exibe informações de pedido incorretas até que o período seja atualizado. A painel agora exibe as estatísticas corretas de solicitar na primeira carga.
* **ACSD-57854** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema quando as solicitações do produto [!DNL GraphQL] retornavam categorias desabilitadas nas agregações de categoria.
* **ACSD-58008** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que a atualização de uma atualização agendada removia a versão anterior de um item preparado, se nenhuma data final fosse especificada.
* Patches atualizados: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que os atributos *[!UICONTROL Used]* e *[!UICONTROL Times Used]* exibem valores incorretos para cupons gerados quando usados durante o check-out com vários endereços.
* **ACSD-56760** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que um usuário administrador restrito a um site específico não pode classificar ou adicionar novos produtos dentro de uma categoria, caso o repositório Web tenha sua própria categoria raiz.
* **ACSD-56858** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que as permissões da função de empresa B2B são exibidas incorretamente para um administrador de empresa restrita.
* **ACSD-57074** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where the *Yes/No* custom attribute with `attrbute_code` starting with `price_` does not work properly with indexing, and products with such attributes are not available on the front end.
* Patches atualizados: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the category page caches invalidate when the stock quantity changes, even if the product is still in stock.
* **ACSD-54656** (para Adobe Systems Comércio >=2.4.5 &lt;2.4.6) - Fixes the issue where the invisible Recaptcha fails during checkout, preventing an order from being placed.
* **ACSD-55100** (for Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where GraphQL does not return more than 10k products in the search results.
* **ACSD-56621** (for Adobe Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where the updated first name and last name are not reflected in the greetings header section for the company admin user.
* **ACSD-56842** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the deferred proxies and the deferred proxy factories are missing after running `setup:di:compile`.
* **ACSD-57003** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where the order status is changed to *[!UICONTROL Complete]* instead of being changed to *[!UICONTROL Processing]* when an order is partially refunded and partially shipped.
* Updated patches: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where a configurable product becomes out of stock when one of two child products is disabled by a scheduled update.
* **ACSD-56616** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where bundled products display as in stock on the storefront when their simple products are out of stock.
* **ACSD-56515** (para Adobe Systems Comércio >=2.4.2 &lt;2.4.7) - Fixes the issue where admin with website level permissions cannot add or edit a dynamic block.
* **ACSD-56447** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where adding the same product to the cart via parallel REST web API requests results in two separate items in the cart.
* **ACSD-56415** (para Adobe Systems Comércio e Magento Open Source >=2,4,5 &lt;2.4.7) - Fixes the issue where the performance of the partial price indexing is slowed down due to a `DELETE` query quando o banco de dados tem muitos dados parciais de preços para indexar.
* **ACSD-54965** (for Adobe Commerce >=2.4.5 &lt;2.4.6) - Fixes the issue where the Visual Merchandising grid does not display the correct stock when a product is assigned to custom stock only.
* **ACSD-52824** (for Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where PayPal Express, Google Pay, and Apple Pay buttons are displayed for company customers when such payment methods are disabled in company settings.
* Updated patches: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a user is redirected to the Admin Dashboard when sorting category products using the **Move out of Stock to bottom** option and the `Invalid security or form key. Please refresh the page` error appears on top of the screen.
* **ACSD-56280** (for Adobe Commerce >=2.4.4 &lt;2.4.7) - Fixes the issue where ordering items from a gift registry leads to an exception.
* **ACSD-56246** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que os dados são removidos do atributo de seleção múltipla personalizado quando uma atualização agendada para um produto se torna ativa.
* **ACSD-56193** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Corrige o problema em que o cache Verniz/Fastly não é atualizado quando um bloco agendado é usado na descrição da categoria usando o Page Builder.
* **ACSD-56158** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que a consulta de &quot;carrinho&quot; retorna o valor de imposto total para cada regra de imposto.
* **ACSD-56023** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o conteúdo do widget não é atualizado na página CMS quando o cache está habilitado.
* **ACSD-55427** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que o usuário administrador não pode desatribuir um produto de um catálogo compartilhado da página de produto no Administrador.
* **ACSD-55352** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que, após criar um memorando de crédito parcial com pontos de premiação do cliente, o status do pedido muda para Fechado, e as opções de memorando de crédito desaparecem da página Pedido de administrador.
* **ACSD-55231** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que não é possível adicionar produtos a um carrinho usando a funcionalidade de pedido rápido.
* **ACSD-54283** (para Adobe Commerce >=2.4.3 &lt;2.4.4) - Corrige o problema em que os Produtos/Categorias não atribuídos ao Catálogo Compartilhado para o Padrão (Grupo Geral) ainda estão incluídos no Mapa de Site XML.
* Patches atualizados: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a URL de categoria canônica não é atualizada após a alteração da URL da categoria.
* **ACSD-53636** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5) - Corrige o problema em que o preço normal não é exibido nas páginas de listagem de produtos para produtos configuráveis que têm produtos filho com preços especiais.
* **ACSD-54885** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema no check-out de vários endereços quando o usuário administrador está usando a funcionalidade *Fazer logon como cliente*.
* **ACSD-55610** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que um pedido parcialmente cancelado tem um valor de desconto incorreto.
* **ACSD-55334** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige as traduções de rótulos por meio de dicionários de Tradução na resposta do GraphQL.
* **ACSD-54739** (for Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the product stock status condition is not applied for related product rules.
* **ACSD-53925** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o administrador não pode salvar o bloco CMS com o carrossel do produto quando o modo `catalog_product_price` dimensions está definido como *site*.
* **ACSD-52714** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o filtro de data não está funcionando na grade do administrador quando o formato de data está definido como *Y-m-d*.
* **ACSD-55055** (para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.7) - Improves performance of loading product attributes in cart price rules in the shopping cart.
* **ACSD-53790** (para Adobe Systems Comércio >=2.4.6 &lt;2.4.7) - Fixes the issue where Multiple RMAs for a single product can be created via REST API.
* **ACSD-56090** (para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.5) - Fixes the issue where the GraphQL request is responding with all stores&#39; data rather than the specifically requested store data.
* **ACSD-54983** (para Adobe Systems Comércio >=2.4.2 &lt;2.4.7) - Fixes the issue where getting the company user UID with GraphQL request is not possible when the user status is set to *[!UICONTROL Inactive]*.
* **ACSD-53309** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o imposto não é totalmente aplicado no rótulo *[!UICONTROL Regular Price]* quando a opção personalizável é selecionada.
* **ACSD-55305** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Corrige o problema em que o pop-up *[!UICONTROL Edit Company User]* da página **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** congela com um carregador na tela.
* Patches atualizados: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que os dados do produto *[!UICONTROL Recently Viewed]* não são atualizados corretamente na exibição da loja.
* **ACSD-54626** (para Adobe Systems Comércio >=2.4.6 &lt;2.4.7) - Fixes the issue where you can&#39;t create a new purchase order rule (`createPurchaseOrderApprovalRule`) com o `NUMBER_OF_SKUS` atributo via [!DNL GraphQL].
* **ACSD-53845** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the [!DNL MySQL] problema de tempo limite de conexão quando `consumer max_messages` = 0.
* **ACSD-54890** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where `aggregate_sales_report_bestsellers_data` causa [!DNL MySQL] erros devido ao `/tmp` disco estar fora do espaço.
* **ACSD-55112** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the *[!UICONTROL Submit review]* botão pode ser clicado várias vezes sem [!DNL Google reCAPTCHA v3] validação.
* **ACSD-54264** (para Adobe Systems Comércio >=2.4.4-p5 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p4 &lt;2.4.6 ||=&quot;&quot;>=2.4.6-p2 &lt;2.4.7) - Fixes the issue where the error message *&quot;Você não pode atualizar o atributo solicitado. &lt;/2.4.6>&lt;/2.4.5> ID da linha: armazenamento_id&quot;* aparece quando um cliente tenta sair com uma cotação negociável de outra armazenamento visualização.
* **ACSD-54418** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a fixed amount of discount is incorrectly applied to each child product of the dynamically priced bundle.
* **ACSD-55238** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes saving the empty product *[!UICONTROL Meta Description]*.
* **ACSD-54966** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where a coupon code with a limited-use per customer can&#39;t be reused if the previous order failed.
* **ACSD-54060** (para Adobe Systems Comércio e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a restricted admin can&#39;t save a product if it&#39;s a child of another product assigned to a different scope.
* **ACSD-48910** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixed the issue where a bundle product assigned to multiple sources goes out-of-stock after an order is invoiced and shipped, even if it still has a non-zero quantity.
* **ACSD-55381** (para Adobe Systems Comércio >=2.4.2 &lt;2.4.7) - Fixes an internal server error when querying `configurable_product_option_uid` e `configurable_product_option_value_uid` campos de um [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (para Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - Corrige o upload de um arquivo no formulário de registro da empresa e substitui um arquivo para um atributo do cliente na loja.
* Patches atualizados: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema que ocorre no carrinho de compras quando um produto é removido do catálogo compartilhado depois de já ter sido adicionado ao carrinho.
* **ACSD-53722** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Corrige o problema em que o preço das opções de produto agrupadas muda para $0 quando atualizações agendadas para escopos diferentes se tornam ativas.
* **ACSD-53643** (para Adobe Systems Comércio >=2.4.3 &lt;2.4.7) - Fixes the issue where the order has an incorrect total when placing a purchase order with disabled or out-of-stock products. Ele é corrigido ocultando o *[!UICONTROL Place Order]* botão de tais pedidos de compra.
* **ACSD-54067** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um vídeo de produto não é reproduzido em um dispositivo móvel.
* **ACSD-55414** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Melhora o desempenho quando o MariaDB tenta converter a entity_id EAV de uma cadeia de caracteres em um inteiro.
* **ACSD-51819** (para Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Corrige o problema em que vários pedidos podem ser feitos com a mesma ID de cotação.
* **ACSD-53118** (para Adobe Commerce >=2.4.0 &lt;2.4.7) - Corrige o problema em que o *[!UICONTROL Cart Price Rule]* é aplicado usando o código de cupom enquanto o produto tem um atributo vazio.
* **ACSD-54324** (for Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the GraphQL requisition_lists request does not consider pagination settings and returns all results.
* Patches atualizados: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (para Adobe Commerce >=2.4.0 &lt;2.4.6) - Corrige o problema em que não é possível processar uma Cotação B2B enviada para um produto com Várias Fontes Atribuídas.
* **ACSD-54040** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Corrige o problema em que o campo *[!UICONTROL Created]* está em branco para exibir detalhes quando os módulos B2B estão habilitados.
* **ACSD-54319** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema no qual o preço do produto mostra zero no relatório *[!UICONTROL Product in Cart]*.
* **ACSD-53378** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Improves checkout page load time for customers who have large address books.
* **ACSD-52657** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the minicart is not updated on the secondary storeview, which uses a subdomain.
* **ACSD-53414** (for Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where a restricted admin user can see CMS pages outside of their permissions scope.
* **ACSD-54472** (for Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where customers of a rejected company can still authenticate, and customers of a blocked and a rejected company can still place orders. The patch adds additional validation for GraphQL endpoints.
* **ACSD-52801** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Adds the option to do a partial match when searching for products in GraphQL.
* **ACSD-55004** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o validador falha ao carregar um arquivo de importação maior do que o valor configurado em `php.ini`.
* **ACSD-54989** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Corrige o problema em que um administrador de empresa não pode fazer um pedido quando *[!UICONTROL Enable Purchase Orders]* está definido como *[!UICONTROL Yes]* e *[!UICONTROL Purchase Order]* está definido como *[!UICONTROL No]*.
* **ACSD-54007** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o erro *&quot;Chave de matriz indefinida &quot;_scope&quot;&quot;* sobre a importação de dados do cliente.
* **ACSD-55031** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o erro *Tipo &quot;misto&quot; não pode ser anulável* durante a compilação.
* **ACSD-54961** (para status de Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a restricted admin user cannot mass update the *Revisão* do Produto.
* **ACSD-55256** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que somente a primeira imagem é exibida com êxito no controle deslizante de imagem.
* Patches atualizados: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (para Adobe Commerce >=2.4.0 &lt;2.4.7) - Corrige o problema em que o histórico de saldo de pontos de recompensa é calculado incorretamente após a expiração dos pontos de recompensa.
* **ACSD-53583** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Melhora o desempenho da reindexação parcial de *Produtos de Categoria* e *Categorias de Produto* indexadores.
* **ACSD-54026** (para Adobe Systems Comércio >=2.4.6 &lt;2.4.7) - Fixes an incorrect error message for an `updateCompanyRole` GraphQL solicitação para um usuário não autorizado.
* **ACSD-54106** (para Adobe Systems Comércio e Magento Open Source >=2.4.1 &lt;2.4.5) - Fixes the issue where category product sorting by name for Turkish accented characters is incorrect.
* **ACSD-52219** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que os filtros salvos nas grades de administrador não funcionam como esperado ao alternar frequentemente entre exibições de marcadores.
* **ACSD-54342** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige uma mensagem de erro incorreta *Erro na estrutura de dados: os valores são misturados* ao importar um arquivo CSV sem dados válidos.
* **ACSD-54660** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Um novo atributo de entrada *sort* foi adicionado para classificar pedidos de clientes no GraphQL por `sort_field` e `sort_direction`.
* **ACSD-54776** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que os valores de campo de produto desmarcados *[!UICONTROL Use Default Value]* e não padrão não são salvos no segundo modo de exibição de site, loja e loja.
* **ACSD-53998** (para Adobe Commerce e Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Corrige o problema em que um **[!UICONTROL Dynamic Block]** baseado em um **[!UICONTROL Customer Segment]** não funciona corretamente depois de sair de uma conta de cliente.
* **ACSD-53204** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Correções *O produto não pode ser salvo.* erro ao fazer solicitações simultâneas para adicionar imagens à galeria de produtos usando o ponto de extremidade `rest/V1/products/<sku>/media`.
* **ACSD-47657** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Adição de um mecanismo de cache para credenciais AWS. Um provedor de credenciais agora usa o cache de Magento para armazenar em cache credenciais recuperadas do AWS para configuração EC2.
* Patches atualizados: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corrige o problema em que os produtos atribuídos a um catálogo compartilhado não aparecem na loja quando um índice parcial é executado.
* **ACSD-54018** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige os problemas de desempenho com o widget [!UICONTROL Product List] que usa um atributo não global na condição do widget.
* **ACSD-54111** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que as imagens em miniatura do produto não são exibidas na loja quando a proporção da imagem da marca d&#39;água não corresponde à imagem do produto.
* **ACSD-47669** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Correções *Violação de restrição de integridade: 1452 Não é possível adicionar ou atualizar uma linha secundária: uma restrição de chave estrangeira falha* erro ao importar CSV de produtos.
* **ACSD-53347** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a indexação de preços leva muito tempo para ser executada.
* **ACSD-52287** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema com o status de ordem incorreto na grade de ordem arquivada quando a indexação de grade assíncrona está habilitada.
* **ACSD-52929** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue with redundant requests to reindex default source items when the inventory indexer is configured in async mode.
* **ACSD-53824** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where `UpdateMultiselectAttributesBackendTypes` correção excede o limite de tamanho da transação do banco de dados durante `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que caches e índices são atualizados mesmo quando não são feitas atualizações para `Inventory_source` itens pela API REST.
* **ACSD-51884** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o caminho do cache de imagem do produto se torna incorreto após a execução do comando resize.
* **ACSD-53628** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o relatório de ordem de venda CSV mostra caracteres especiais incorretos.
* **ACSD-53148** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável ao carrinho resultavam em dois itens separados no carrinho com o mesmo SKU de produto.
* **ACSD-52606** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que a mensagem de erro *Seu pedido não está pronto para retirada* é exibida quando o usuário clica em **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a imagem não é atualizada no front-end depois de substituí-la por outra imagem com o mesmo nome.
* **ACSD-53728** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o indexador EAV do produto está demorando mais para ser concluído.
* **ACSD-53979** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the JS issue that occurs on the homepage if the welcome message contains a single quote.
* **ACSD-52085** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where a configurable product with a special price is not visible in the product&#39;s carousel.
* **ACSD-53795** (para trabalhos de Adobe Systems Comércio e Magento Open Source >=2,4,2 &lt;2.4.7) - Fixes the issue with invalid data type in `indexer_update_all_views` cron.
* **ACSD-52143** (para Adobe Systems Comércio e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where custom options are removed after product import.
* **ACSD-53750** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the *Erro de conexão* quebrado ou fechado durante a reindexação multi encadeada `catalog_product_price` .
* **ACSD-49843** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.0 ||=&quot;&quot;>=2.4.1 &lt;2.4.7) - Fixes the issue where the link on product download is not available after the ordered item is auto-invoiced by online payment method with the **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** configuração ativada.&lt;/2.4.0>
* **ACSD-47054** (for Adobe Commerce >=2.4.2 &lt;2.4.6) - Fixes the issue where the preview reindex runs reindex for all stores, causing slowness.
* Added new versions for ACSD-46541, ACSD-47079.
* ACSD-49970-v3 replaced with ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt; 2.4.6) - Fixes the issue where the inventory indexer cleans all caches in the Update on Schedule mode.
* **ACSD-50887** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the product attribute property *[!UICONTROL Use in Search Results Layered Navigation]* can be set to *Yes* without the *[!UICONTROL Use in search]* option set to *Yes*.
* **ACSD-51846** (para Adobe Systems Comércio e Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Fixes the *Problema de Erro* interno que acontece porque nem todos os níveis de carga da API REST são validados.
* **ACSD-52906** (para Adobe Systems Comércio >=2.3.7 &lt;2.4.7) - Fixes the issue where the X-Magento-Vary cookie is set incorrectly for logged-in customers that belong to the same customer segment causing improper caching for some pages.
* **ACSD-52736** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where a *Cart Price Rule* that includes requirements for configurable product quantity does not work as expected.
* **ACSD-47875** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where admin users are not able to add a product to a customer cart from the Admin for a particular store view scope with inventory management.
* **ACSD-53176** (para Adobe Systems Comércio >=2.3.7 *&lt;2.4.5) - Fixes the issue where  Regra* de produto relacionado com *é uma das* condições que não corresponde aos produtos.
* **ACSD-51666** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the error *A sessão expirou, fazer logon novamente.* that happens after a customer tries to log in.
* Adição de novas versões para MDVA-39305-v2.
* Atualização dos requisitos para o ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que o endereço de remessa padrão na etapa de remessa do check-out é preenchido automaticamente com um endereço de remessa na loja selecionado anteriormente.
* **ACSD-52041** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a mensagem de erro: *[ERRO] [!DNL Page Builder] foi renderizada por 5 segundos sem liberar bloqueios.* aparece no navegador Chrome ao salvar o conteúdo editado com [!DNL Page Builder].
* **ACSD-52095** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que o valor `manage_stock` era definido incorretamente como 0 no arquivo CSV após a exportação do produto.
* **ACSD-51358** (para Adobe Systems Comércio >=2.4.5 &lt;2.4.7) - Fixes the issue where removing a scheduled update without an end date leads to removing other scheduled updates for the same entity.
* **ACSD-48070** (para Adobe Systems Comércio >=2.3.7 &lt;2.4.7) - Fixes the issue where editing a scheduled update triggers an exception.
* **ACSD-51890** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que o botão [!UICONTROL Submit review] pode ser clicado várias vezes sem a validação do [!DNL Google reCAPTCHA] v3.
* **ACSD-51984** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que os valores *[!UICONTROL Use Default Value]* e *[!UICONTROL non-default product field]* desmarcados não são salvos no segundo modo de exibição de site, repositório e repositório.
* **ACSD-52398** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o erro *A quantidade solicitada não está disponível* que ocorre ao tentar atualizar a quantidade de um produto agrupado no carrinho na loja.
* **ACSD-52786** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que uma condição de regra de catálogo *SKU* se aplica a todos os produtos que começam com a SKU fornecida.
* **ACSD-52921** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que ocorre um erro interno ao solicitar detalhes do carrinho da GraphQL quando há um produto configurável indisponível no carrinho.
* **ACSD-51683** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que uma opção personalizável não pode ser adicionada ao carrinho usando o GraphQL.
* **ACSD-52133** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que uma conta de cliente não pode ser salva após uma atualização.
* **ACSD-52202** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a quantidade vendável do estoque padrão muda incorretamente para 0 quando um estoque não padrão é alterado para 0 na execução do pedido.
* **ACSD-51265** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema com o desempenho de reindexação do `catalog_product_price` quando há muitos produtos agrupados no sistema.
* **ACSD-52831** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que os clientes não podem fazer pedidos de cotação negociáveis quando o [!DNL Google reCAPTCHA v3 Invisible] está habilitado.
* **ACSD-51845** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que os produtos subsequentes com preços de camada e conjuntos de atributos diferentes não podem ser atualizados por meio da API REST em massa assíncrona.
* **ACSD-52815** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a entrada do campo de quantidade de uma fonte não padrão suporta apenas até 6 dígitos, ao contrário de 8 para um estoque padrão.
* **ACSD-51149** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que a Exportação de Importação Agendada com Permissões de Catálogo habilitadas invalida os indexadores e libera o cache pelo cron.
* **ACSD-50815** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que a quantidade decimal de um produto simples não pode ser usada para uma nova opção de Produto agrupado.
* Atualizadas versões para ACSD-47803.
* Título atualizado para ACSD-51892.
* Atualização do ACSD-51379.
* Atualização do ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um usuário administrador não é redirecionado corretamente após selecionar uma exibição de loja ao criar uma nova ordem no Administrador.
* **ACSD-50813** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que o Administrador não podia adicionar produtos agrupados contendo uma barra na SKU com a funcionalidade [!UICONTROL Add Products by SKU] à ordem do administrador.
* **ACSD-51630** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que uma grande quantidade de mensagens do sistema atrasa o download de páginas de administração.
* **ACSD-51853** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corrige o problema em que os estilos de texto copiados não são aplicados ao usar o [!UICONTROL Page Builder].
* **ACSD-52160** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where the product validation result against the cart price rule was not properly evaluated based on the rule condition &#39;If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true&#39;.
* **ACSD-51636** (para Adobe Systems Comércio >=2.4.5 &lt;2.4.7) - Fixes the issue where the company admin cannot add new users from the customer account section despite having all necessary roles and permissions.
* **ACSD-51739** (para Adobe Systems Comércio >=2.4.6 &lt;2.4.7) - Fixes the issue where an error is returned when the `structure_id` é solicitado em um solicitação CompanyTeam GraphQL.
* **ACSD-51857** (para Adobe Systems Comércio e Magento Open Source >=2,4,0 &lt;2.4.7) - Fixes the issue where the slow performance of the `aggregate_sales_report_bestsellers_data` cron relatório sobre grandes sales_solicitar e `sales_order_item` tabelas de banco de dados deveu-se à forma como os principais query de dados foram gravados.
* **ACSD-48448** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que há um problema de condição de corrida ocorrendo durante os cancelamentos de pedidos, o que causa uma entrada duplicada na tabela `inventory_reservation`.
* **ACSD-52689** (para Adobe Systems Comércio e Magento Open Source >=2.4.3 &lt;2.4.6) - Fixes the issue where images cannot be uploaded to Amazon S3 storage using REST API.
* **B2B-2674** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.7) - Add caching capability to the 1customAttributeMetadata1 GraphQL query.
* Adição de novas versões para ACSD-44938.
* Requisitos adicionados para ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.5) - Fixes the database rollback command for a case when the DB dump contains triggers and a *delimitador* SQL.
* **ACSD-50512** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o *Erro: o link disponível para download não está relacionado ao produto. Verifique o link e tente novamente.Erro* que ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável.
* **ACSD-50949** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o filtro de preço na pesquisa avançada não retorna resultados adequados quando usado com o filtro SKU.
* **ACSD-51645** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o erro lançado ao salvar uma nova Regra de Preço do Carrinho se a extensão `Magento_OfflineShipping` estiver desabilitada.
* **ACSD-50895** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que [!DNL Google Analytics] 3 marcas GTM não são acionadas se [!DNL Google Analytics] 4 GTM não estiver configurado.
* **ACSD-51102** (para Adobe Systems Comércio >=2.4.2 &lt;2.4.7) - Fixes the issue where a catalog rule that is applied to a large number of products is not correctly indexed when the rule is enabled by a scheduled update.
* **ACSD-50368** (para Adobe Commerce e Magento Open Source >= 2.4.3 &lt;2.4.5) - Corrige o problema em que o `group_id` do cliente é ignorado quando um cliente é criado por meio da API REST assíncrona ou da API REST em massa assíncrona.
* **ACSD-51497** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corrige o problema em que um cliente não pode classificar uma página de catálogo por Atributo personalizado do tipo de lista suspensa.
* **ACSD-51408** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt; 2.4.7) - Fixes the issue where the order item status is incorrectly set to *[!UICONTROL Backordered]*.
* **ACSD-51735** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que o status do item do pedido é definido incorretamente como *[!UICONTROL Ordered]* quando o estoque do produto é *0*.
* **ACSD-51792** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que uma página não tem o evento de impressão quando o [!DNL Google Tag Manager] 4 está habilitado.
* **ACSD-51471** (para Adobe Commerce >=2.4.3 &lt;2.4.7) - Corrige o problema em que um usuário administrador não pode salvar uma atualização agendada para um produto agrupado que usa um produto simples que tem uma atualização agendada.
* **ACSD-51700** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o erro que ocorre ao alternar exibições da loja em uma página de edição de produto baixável no administrador.
* **ACSD-51120** (para Adobe Systems Comércio >=2.3.7 &lt;2.4.3) - Fixes the issue where GraphQL GET requests cache is not cleared for CMS pages that contain CMS blocks that are updated via a staging update.
* **ACSD-51240** (for Adobe Commerce >=2.4.4 &lt;2.4.6) - Fixes the issue where the uploaded file is missing if the registration is done via the company registration form.
* **ACSD-51907** (for Adobe Commerce >=2.4.2 &lt;2.4.3) - Fixes the issue where a restricted admin user cannot create a credit memo with an offline refund.
* **ACSD-52148** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where the [!DNL Google V3 reCAPTCHA] Admin login fails occasionally.
* **ACSD-51431** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where an indexer status is *working* even if there are no new entries in the changelog.
* **ACSD-51892** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema de desempenho em que os arquivos de configuração são carregados várias vezes.
* ACSD-51114 obsoleto.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que os vários erros [!UICONTROL Page Builder's] impedem que o administrador salve um produto sem permissões de conteúdo.
* **ACSD-51305** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que os produtos derivados configuráveis esgotados não estão disponíveis na resposta do GraphQL.
* **ACSD-50621** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que [!UICONTROL Tier Prices] de sites diferentes no catálogo compartilhado não ficam visíveis ao tentar editá-los em um ambiente de vários sites.
* **ACSD-51041** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Melhora o desempenho do indexador de preços.
* **ACSD-51379** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que as alterações feitas no conteúdo do texto da página via [!UICONTROL Page Builder] não são salvas.
* **ACSD-49480** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que apenas uma regra de preço de carrinho é aplicada ao carrinho.
* **ACSD-51230** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que a conta do cartão-presente é excluída quando um reembolso parcial de um produto simples é processado a partir de um pedido.
* **ACSD-51238** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a origem de estoque é removida ao atualizar produtos configuráveis e editar o preço.
* **ACSD-50794** (para Adobe Commerce >=2.4.1 &lt;2.4.7) - Corrige o problema em que a mensagem de presente ou os detalhes de invólucro do presente não são atualizados no banco de dados ao removê-los por meio do GraphQL.
* **ACSD-51528** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que a coluna *x_forwarded_for* tem valores nulos na tabela *sales_order*.
* **ACSD-50849** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige o problema em que a adição de um novo produto à categoria após a limpeza do cache resulta em uma incompatibilidade de posições e seleções dos produtos existentes.
* **ACSD-51294** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where GTM/GA price, quantity, tax, shipping, and revenue are sent as a string to [!DNL Google Analytics] e GTM.
* **ACSD-51204** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um produto totalmente vendido não é retornado ao estoque após a criação de um memorando de crédito.
* **ACSD-51291** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Corrige o problema em que o administrador restrito com acesso a um site pode adicionar imagens/vídeos ao produto atribuído a vários sites.
* Adição de novas versões para ACSD-50336.
* Substituídos os patches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Corrige o problema em que o Recaptcha v2 não é recarregado após o envio de um pagamento com falha.
* **ACSD-50817** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Otimiza o trabalho Cron `sales_clean_quotes` para ser executado mais rápido.
* **ACSD-49392** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corrige o problema no qual o status do pedido muda para fechado após um reembolso parcial para um produto agrupado.
* **ACSD-51036** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que as condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição das informações de status de remessa na tabela [!UICONTROL Items Ordered].
* **ACSD-50858** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Melhora o desempenho para carregar conteúdo de banners.
* Adição de novas versões para MDVA-39305-v2, ACSD-45169.
* Atualização dos patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (para Adobe Commerce e Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Corrige o problema em que os emails de alerta do produto não são enviados quando um produto está de volta ao estoque ou o preço é alterado.
* **ACSD-50367** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a exportação de endereço do cliente não funciona quando um atributo de endereço do cliente de seleção múltipla sem valores é criado.
* **ACSD-49877** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a reprodução automática de vídeo não funciona no [!DNL Safari] móvel quando o vídeo é vinculado diretamente a um arquivo de vídeo remoto e não a um serviço de streaming.
* **ACSD-50165** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o erro *O arquivo não pode ser excluído. Aviso!unlink: esse arquivo ou diretório* não existe ao limpar o cache de JS/CSS do Administrador.
* **ACSD-49737** (para Adobe Commerce e Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Corrige o problema em que um cupom é marcado incorretamente como usado após uma falha no pagamento por cartão.
* **ACSD-50814** (para Adobe Systems Comércio e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where an admin user is not able to create a credit memo.
* **ACSD-50116** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que um usuário administrador não consegue criar uma regravação de URL para subcategorias de nível 3 ou inferior.
* **ACSD-49513** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5) - Corrige o problema em que a sincronização do armazenamento remoto falha devido a arquivos de 0 bytes.
* **ACSD-46683** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema no qual o preço de envio mostra *Ainda não calculado*.
* **ACSD-49129** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que o atributo *[!UICONTROL content]* (código de imagem base64) não é retornado nas respostas da API de mídia do produto `rest/V1/products/sku/media`.
* **ACSD-50276** (para Adobe Commerce >=2.4.0 &lt;2.4.7) - Corrige o problema em que o formulário de registro do cliente não funciona na loja se um atributo de cliente de seleção múltipla for criado.
* **ACSD-50527** (para Adobe Systems Comércio >=2.3.7 &lt;2.4.7) - Fixes the error that occurs when saving a page with an empty dynamic block.
* **ACSD-49973** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.5) - Improves performance of fetching bundled products through GraphQL.
* **ACSD-51114** (para Adobe Systems Comércio e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a random product disappears from large catalogs when asynchronous indexing is enabled. Melhora o desempenho da reindexação assíncrona para catálogos grandes.
* **B2B-2598** (para Adobe Systems Comércio e Magento Open Source >=2.4.4[!UICONTROL availableStores]&lt;2.4.7) - Add caching capability to the  , [!UICONTROL countries], [!UICONTROL country], , [!UICONTROL currency]e [!UICONTROL storeConfig] queries GraphQL.
* Adição de novas versões para MDVA-42806, ACSD-48627, ACSD-46815.
* Atualização de patches metadados para ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a ready-to-pick-up email is sent by API when the order is not ready for pickup.
* **ACSD-49822** (para Adobe Systems Comércio >=2.3.7 &lt;2.4.7) - Fixes the issue where updates in the [!UICONTROL Requisition List] página não se refletem na [!UICONTROL Print Requisition List].
* **ACSD-48771** (para versões Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue with upgrading the column-block content type from older [!DNL Page Builder] .
* **ACSD-49464** (para Adobe Systems Comércio >=2.3.7 &lt;2.4.7) - Fixes the issue where invoices, shipments, and credit memos are not moved back from the archive when the orderId is different.
* **ACSD-49773** (para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where product export fails when AWS S3 is used as remote storage.
* **ACSD-49748** (para Adobe Systems Comércio >=2.3.7 &lt;2.4.7) - Fixes the issue where invitations cannot be sent.
* **ACSD-49502** (para Adobe Systems Comércio >=2.4.3 &lt;2.4.7) - Fixes the issue where the downloadable link is not updated properly after a staging update is applied to the downloadable product.
* **ACSD-49527** (para Adobe Systems Comércio >=2.4.2 &lt;2.4.7) - Fixes the issue where GraphQL company roles don&#39;t display pagination correctly.
* **ACSD-49706** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the default value is saved for a visual swatch attribute when no value is selected.
* **ACSD-49835** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the Use default checkbox value is not saved correctly on a store level for a multi-select attribute.
* **ACSD-49898** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the products grid throws an exception when a bundled product has a special price that exceeds 1000.
* **ACSD-50234** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.5) - Fixes the issue with the wrong customer name in the confirmation email if placing an order with [!DNL PayPal].
* **ACSD-49960** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where filtering by date does not work for the customer order grid.
* **ACSD-49849** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que o email do cliente foi substituído pelo email [!DNL PayPal] ao fazer um pedido com [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que a estrutura e a Precificação do Catálogo Compartilhado lançam um erro no Administrador quando os produtos têm aspas simples ou duplas no SKU.
* **ACSD-49970** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige a manipulação incorreta de erros de GraphQL quando os relatórios do [!DNL New Relic] estão ativados.
* **ACSD-50260** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que os resultados da pesquisa de produtos da GraphQL estão limitados a apenas 10.000 resultados.
* **ACSD-48813** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a pesquisa não mostra resultados relevantes com base no peso da pesquisa dos atributos.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.3) - Corrige o problema em que uma regra de preço de catálogo criada com base no atributo Sim/Não não considera o escopo selecionado.
* **ACSD-47704** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the bundled product shows the price of in stock products only.
* **ACSD-49370** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the *O atributo de produto Date Time* tem um *tipo FilterMatchTypeInput* no GraphQL schema.
* **ACSD-48807** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corrige o problema em que as Avaliações de Produtos do cliente não são filtradas por storeview via GraphQL.
* **ACSD-49433** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que o valor padrão é mostrado como subtotal no carrinho para cartão-presente com um valor em aberto.
* **ACSD-48866** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que ocorre um erro ao solicitar o feed RSS para categorias.
* **ACSD-48784** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que os preços do segmento de cliente são armazenados incorretamente em cache entre os grupos de clientes.
* **ACSD-48857** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um usuário não pode salvar alterações após a edição com o Page Builder.
* **ACSD-49065** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que os itens de cotação não estão visíveis no Admin se atribuídos apenas ao estoque personalizado.
* **ACSD-49179** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o Relatório de Pedidos mostra valores incorretos em caso de moedas diferentes para lojas diferentes.
* **ACSD-49286** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um produto é adicionado duas vezes a um carrinho quando vários widgets de produto estão presentes na página.
* **ACSD-49574** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Adiciona funcionalidade para oferecer suporte a atualizações de produto de Cartão Presente em um carrinho via GraphQL.
* Correção atualizada: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (para Adobe Commerce >=2.4.1 &lt;2.4.7) - Corrige o problema em que o endereço de entrega padrão é usado em vez de um novo ao fazer um pedido usando uma cotação negociável.
* **ACSD-48059** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que os comerciantes não podem salvar o &quot;[!UICONTROL Match product by rule]&quot; na categoria.
* **ACSD-48216** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corrige o problema em que [!UICONTROL AUTO_INCREMENT] da tabela [!UICONTROL inventory_source_item] aumenta na operação [!UICONTROL UPDATE].
* **ACSD-47908** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.0 &lt;2.4.7) - Fixes the error &quot;A value less than or equal to 0 is expected&quot; when selecting the source and qty on the shipping step during checkout.&lt;/2.3.8>
* **ACSD-49497** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where an order remains in the processing state after shipment and a partial refund is applied.
* **ACSD-48694** (para Adobe Systems Comércio e Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.1 &lt;2.4.7) - Fixes the issue where the error &quot;Invalid state change requested&quot; prevents a customer from placing an order.&lt;/2.3.8>
* **ACSD-49013** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a confirmação de email não é traduzida para a localidade do site ao criar clientes usando a API em massa.
* **ACSD-48164** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que um administrador restrito não pode salvar um valor no nível do site.
* **ACSD-48404** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que &quot;Lembrar Paginação de Categoria = Sim&quot; causa um erro ao pressionar o botão Voltar do navegador.
* **ACSD-48634** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige erros de JS em uma página de atualização de preparo quando &quot;[!UICONTROL Google Analytics Content Experiments]&quot; está habilitado.
* **ACSD-49042** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que um produto com uma ordem pendente infinita não pode ser encomendado à Loja.
* Patches atualizados: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (para Adobe Commerce e Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Corrige o problema em que as notificações de queda de preço nem sempre são enviadas devido ao armazenamento em cache no nível do aplicativo.
* **ACSD-48661** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que, se o limite de crédito da empresa for maior que 999, o separador de vírgulas impedirá o salvamento da empresa devido a um erro de validação.
* **ACSD-48773** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o modelo de email de pontos de premiação é retirado do armazenamento errado.
* **ACSD-48587** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que os caracteres especiais de HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes.
* **ACSD-48212** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que a importação de produtos atribui o produto à origem errada.
* **ACSD-47988** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que a exportação de produtos elimina as marcas HTML da descrição do produto do page builder.
* **ACSD-48366** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a imagem do produto não é exibida no modelo de email Voltar para o Stock.
* **ACSD-48417** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where an SQL error appears after creating a schedule change for a product and saving another product.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where product price reindex is not working if the bundle product is not assigned to any website.
* **ACSD-48262** (para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where products are not visible on the frontend when &quot;Allow All Products Per Page&quot; setting is set to Yes.
* **ACSD-48293** (para Adobe Systems Comércio e Magento Open Source >=2.4.3 &lt;2.4.4) - Fixes the issue where the composite products go out of stock when the child products that were sold out are returned to stock.
* **ACSD-47520** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where customers lose reward points when a credit memo is created.
* **ACSD-48044** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where applying multiple gift cards to a single order with multi-shipping prevents orders from being placed.
* **ACSD-48300** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where a return cannot be created if the configurable product is removed.
* **ACSD-47910** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue of missing orders, invoices, shipments, and credit memos in respective entity grids.
* **ACSD-47292** (para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where out-of-stock bundled products are not available in the GraphQL response if the &quot;show out-of-stock products&quot; is set to Yes.
* **ACSD-48234** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the catalog search result shows an incorrect category item count when the &quot;show out of stock&quot; option is enabled.
* **ACSD-48313** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.5) - Fixes the issue where the &quot;configurable_variations&quot; column is not parsed if the attribute value contains a comma. The same parsing algorithm is used for &quot;additional_attributes.
* **ACSD-48627** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que o produto configurável sem estoque causa um erro ao enviar uma solicitação GraphQL para obter detalhes do carrinho.
* Patch atualizado: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where SEO-friendly URLs are not generated for products that have *url_key* attributes overridden on the store-view level.
* **ACSD-46865** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the Shipment and Credit Memo grid is not populated when asynchronous indexing is enabled.
* **ACSD-47004** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where VAT is not applied to a billing address without a VAT ID.
* **ACSD-47803** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where out-of-stock configurable product swatches are displayed as available.
* **ACSD-47137** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Melhora a velocidade de carregamento da galeria de imagens quando a pasta pub/media é muito grande.
* **ACSD-46770** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que emails de pedido de administrador são enviados mesmo quando a *Confirmação de pedido de email* está desmarcada.
* **ACSD-47955** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que o GraphQL não exibe o desconto do carrinho corretamente.
* **ACSD-46617** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o botão *Continuar para o Check-out* fica esmaecido mesmo se o subtotal for maior que o *Valor Mínimo do Pedido* configurado.
* **ACSD-47079** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que o status do estoque de produtos compostos (agrupados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado por meio da API REST POST /rest/V1/inventory/source-items.
* **ACSD-47336** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Correções *Algo deu errado.Erro* ao dispensar notificações no Administrador do Commerce.
* **ACSD-47559** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a área Visualizar Modelo de email não estava totalmente visível.
* **ACSD-47920** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que os pedidos podem ser feitos por meio da API Rest como um usuário convidado, mesmo quando a opção *Permitir check-out de convidado* está desativada.
* Patches substituídos: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que um administrador com acesso restrito a um escopo específico não pode excluir análises de produtos.
* **ACSD-47107** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Corrige o problema em que o desconto de Regra de Preço de Catálogo é aplicado às opções de produto personalizadas.
* **ACSD-47232** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que os cupons com condições de peso total não podem ser aplicados no Admin.
* **ACSD-46519** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6) - Corrige o problema em que a solicitação categoryList do GraphQL retorna uma product_count incorreta para uma categoria âncora.
* **ACSD-47027** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige uma solicitação lenta de GraphQL updateCompanyRole.
* **ACSD-47666** (para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.6) -=&quot;&quot; fixes=&quot;&quot; the=&quot;&quot; issue=&quot;&quot; where=&quot;&quot; the=&quot;&quot; filter=&quot;&quot; function=&quot;&quot; does=&quot;&quot; not=&quot;&quot; work=&quot;&quot; in=&quot;&quot; the=&quot;&quot; admin=&quot;&quot;> Permissões > do sistema > funções do usuário > uma grade função > de Usuários de função.&lt;/2.4.6)>
* **ACSD-47497** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a guia Serviços não estava visível na Configuração sob o Administrador.
* Correção atualizada: ACSD-47743.
* Patches substituídos: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3) - Corrige o erro _Tentando acessar deslocamento de matriz no valor do tipo bool_ ao acessar determinados caminhos de categoria não existentes para produtos conhecidos no PHP 7.4.
* **ACSD-47332** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o cron falha com um erro que só é relatado na execução entre 00:00 e 00:59 UTC.
* **ACSD-47280** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a desabilitação do recurso de catálogo compartilhado em um escopo específico não funciona corretamente.
* **ACSD-47106** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que um valor não pode ser salvo em um novo atributo personalizado em uma página de criação de empresa.
* Correção atualizada: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que um usuário recebe um erro ao atribuir um grande número de fontes de produtos.
* **ACSD-46856** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Melhora os preços da camada de atualização de desempenho por meio de Sistema > Configuração > Importação > Advanced Pricing.
* **ACSD-46541** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que um usuário administrador não pode criar um memorando de crédito se um item de pedido for excluído.
* **ACSD-46581** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o total de impostos estimado não é atualizado após selecionar um país no carrinho de compras.
* **ACSD-46618** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o widget lista de produtos mostra preços em cache incorretos para um cliente conectado.
* **ACSD-46674** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que as opções personalizadas de um tipo de imagem são exibidas como HTML nos emails do cliente.
* **ACSD-46988** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a Solicitação de API &#39;currency&#39; do GraphQL retorna valores NULL para uma moeda personalizada.
* **ACSD-47076** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) - Corrige o problema em que os vídeos do Vimeo não podem ser reproduzidos na loja.
* **ACSD-45071** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Corrige o problema em que a origem padrão é adicionada ao produto durante a importação.
* **AC-3023** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Atualize o esquema DHL para a versão 10.0 mais recente.
* Patches atualizados: MDVA-42584.
* Patches substituídos: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que um usuário recebe um status de pedido incorreto quando reembolsado usando o crédito da loja.
* **ACSD-46703** (*para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige o problema em que não é possível arrastar e soltar opções personalizadas em uma página de edição de produto.
* **ACSD-44851** (*para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema em que um categoria com subcategorias não consegue abrir ou expandir.
* **ACSD-46815** (*para Adobe Systems Comércio e Magento Open Source >=2.4.5 &lt;2.4.6*) - Corrige o problema em que categoria árvore solicitação é limitada a 20 categorias.
* **ACSD-45675** (*para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema em que a exportação de produtos usa categoria nomes da *Loja padrão Exibir* escopo.
* **ACSD-46869** (*para Adobe Systems Comércio e Magento Open Source >=2.4.4*&lt;2.4.6 ) - Corrige o problema em que um produto configurável em um carrinho não é atualizado por meio de um *PUT solicitação de API* REST sem alterar o quantidade do produto.
* **MDVA-42768-V2** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o produto configurável exibe o preço regular como *0* quando *Exibir Fora de Stock* é *Sim*.
* Patches atualizados: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* correção obsoleta: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que categoria solicitação de árvore está limitada a 20 categorias.
* **ACSD-45781** (*para Adobe Systems Comércio e Magento Open Source >=2.4.1 &lt;2.4.2*) - Corrige o problema em que o campo armazenamento frente pesquisa não é exibido em dispositivos móveis.
* **ACSD-46192** (*para Adobe Systems Comércio e Magento Open Source >=2.3.6*&lt;2.4.5 ) - Corrige o problema com o uso do `async/bulk/V1/configurable-products/bySku/options` endpoint.
* **ACSD-46404** (*para Adobe Systems Comércio e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige o problema em que um administrador usuário não pode fazer logon após atualizar para a versão 2.4.4.
* Patches atualizados: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que uma mutação de produto GraphQL para uma armazenamento específica retorna todas as variantes configuráveis, incluindo aquelas não atribuídas ao armazenamento solicitado.
* **ACSD-46146** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que dois emails de confirmação solicitar são enviados após colocar uma solicitar do Administrador.
* **ACSD-45255** (*para Adobe Systems Comércio >=2.4.3 &lt;2.4.6*) - Corrige uma exceção no página de Relatório de Baixa Stock para uma administrador usuário restrita.
* **ACSD-45488** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.6*) - Corrige o problema no qual um produto configurável com várias fontes não é retornado na Stock automaticamente.
* **ACSD-45754** (*para Adobe Systems Comércio e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema em que os pontos de recompensa não são adicionados após aplicar uma cupom ao carrinho.
* **ACSD-45849** (*para Adobe Commerce >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo.
* **ACSD-45257** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema em que o GraphQL não exibe um desconto de carrinho corretamente.
* **ACSD-44938** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que `VAT_ID` não pode ser aplicado em uma solicitação GraphQL para um usuário convidado.
* Patches atualizados: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige o problema em que a quantidade em estoque de um produto virtual é calculada incorretamente após a criação de um memorando de crédito.
* **ACSD-43887** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando os Pedidos de compra para empresas estão habilitados.
* **ACSD-45143** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que a mutação `setShippingAddressesOnCart` não permite definir o código de região numérica como *região*.
* **ACSD-44591** (*para Adobe Systems Comércio e Magento Open Source >=2.4.3 &lt;2.4.6*) - Corrige o erro que ocorre quando uma solicitar é colocada sem confirmação CAPTCHA.
* **ACSD-45520** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que as opções de amostra não são pré-selecionadas nos detalhes do produto página quando um usuário edita produtos configuráveis do carrinho de compras.
* **ACSD-45169** (*para Adobe Systems Comércio e Magento Open Source >=2.4.1*&lt;2.4.6 ) - Corrige o problema em [!DNL Visual Merchandiser] que não exibe o estoque e o preço corretos de um produto configurável após a aplicação de uma atualização de preparo.
* **ACSD-45424** (*para Adobe Systems Comércio e Magento Open Source >=2.3.4 &lt;2.4.6*) - Corrige a questão em que uma compensação incorreta de reserva é criada após um reembolso parcial (memorando de crédito).
* **MDVA-42807** (*para Adobe Systems Comércio e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema em que o sinal de moeda personalizada não é exibido no armazenamento frente.
* Patches atualizados: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os totais de pedidos no relatório de Pedidos são calculados incorretamente para o usuário administrador restrito.
* **MDVA-44940** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o erro SQL que ocorre ao salvar a categoria do Administrador.
* **MDVA-44562** (*para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Corrige o problema no qual a ID de armazenamento não padrão para itens de aspas é substituída pelo id de armazenamento padrão, apesar do GraphQL solicitação originário do armazenamento visualização não padrão.
* **MDVA-43167** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que administrador solicitar ação em massa de grade não se aplica a várias página quando administrador usuário seleciona todos os pedidos.
* **MDVA-44044** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Corrige o problema em que um produto não é exibido no categoria página depois de ser atribuído a um novo site.
* **MDVA-42509** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.4*) - Corrige o problema em que não foi possível carregar um CSV para uma ordem rápida, resultando em um erro *Não é possível enviar o cookie*.
* Patches atualizados: MDVA-41061, MDVA-42584.
* O prefixo dos novos patches [!DNL Quality Patches Tool] será alterado de *MDVA* para *ACSD* devido a alterações internas no processo.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que um item adicional não pode ser adicionado ao carrinho quando a quantidade mínima do item já está no carrinho.
* **MDVA-44887** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige o erro *Uncaught SyntaxError: Unexpected token &#39;const&#39;* no painel de Administração.
* **MDVA-43718** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Correções *O consumidor não está autorizado a acessar %resources.Erro* que aparece ao acessar um catálogo compartilhado de uma integração personalizada.
* **MDVA-44660** (*para Adobe Commerce e Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Corrige o problema em que o caractere de acento grave ``` ` ``` não pode ser usado para o nome e sobrenome de um cliente.
* **MDVA-40896** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o *Erro: TypeError: Argumento 3 transmitido para o erro Magento* na API assíncrona de produto em massa.
* **MDVA-38559** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige o erro */V1/customers/search API* para clientes com mais de uma assinatura.
* **MDVA-44533** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.4*) - Corrige o problema em que o desconto é aplicado incorretamente a um produto filho do pacote.
* Patches atualizados: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que os produtos *Não Visível Individualmente* ainda aparecem nos Resultados da Pesquisa Avançada do Catálogo.
* **MDVA-44100** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que todos os FPTs são atribuídos ao último produto no carrinho de compras e redefinidos para outros produtos.
* **MDVA-43605** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corrige o problema em que os dados de pedido retornam valores negativos para totais de linha ao usar a API Rest.
* **MDVA-43102** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corrige o problema em que a quantidade comercializável não é atualizada corretamente quando um reembolso é feito por meio da API REST.
* **MDVA-43178** (*para Adobe Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Corrige o problema em que um token de cliente para um armazenamento personalizado não pode ser recuperado no GraphQL.
* **MDVA-43859** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o erro *Nenhuma entidade com customerId =* é registrada quando um cliente excluído tenta fazer logon.
* **MDVA-44147** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que um GraphQL solicitação não retorna Listas de requisição.
* **MDVA-44505** (*para Adobe Systems Comércio e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige os problemas em que o GraphQL Aplicando Pontos de Recompensa não atualiza o Total Geral e onde armazenamento crédito é aplicado várias vezes durante o solicitar posicionamento.
* Patches atualizados: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*para Adobe Systems Comércio e Magento Open Source >=2.4.1*&lt;2.4.3 ) - Corrige o problema em que a Regra de Produto Relacionada funciona somente quando o Segmento do Cliente é definido como *Todos*.
* **MDVA-39605** (*para Adobe Systems Comércio e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que o TTL do cache Redis (data de expiração) tem um valor errado.
* **MDVA-43862** (*para Adobe Systems Comércio e Magento Open Source >=2.3.3*&lt;2.4.5 ) - Corrige o problema em que o cliente não pode atualizar carrinho itens devido a um erro de mutação *GraphQL* UpdateCartItems.
* **MDVA-43824** (*para Adobe Systems Comércio e Magento Open Source >=2.3.6 &lt;=2.3.7-p3 ||=&quot;&quot;>=2.4.1 &lt;2.4.5*) - Corrige o problema em que um erro aparece ao cancelar pedidos com desconto.&lt;/=2.3.7-p3>
* **MDVA-43451** (*para Adobe Systems Comércio e Magento Open Source >=2.4.3*&lt;2.4.5 ) - Corrige o problema em que o erro em que o armazenamento *solicitado não foi encontrado. Verifique o armazenamento e tente novamente.* aparece ao configurar um catálogo compartilhado para um site específico.
* **MDVA-43491** (*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;2.4.5*) - Fixes the issue where the base image label doesn&#39;t update when importing products for a multi-store website.
* **MDVA-43601** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*) - Fixes the issue with missing triggers after full reindex.
* **MDVA-42046** (*for Adobe Commerce and Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Fixes the issue where an incorrect value is assigned to a product attribute with a date input field while updating a product.
* **MDVA-43935** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.5*) - Fixes the issue where Upsell product is shown twice.
* **MDVA-44188** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que os emails emitidos pelo sistema com `.-` em endereços não são enviados.
* **MDVA-42283** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que o formato de data e hora na grade de administrador solicitar da localidade Francês é inválido.
* Patches atualizados: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Added patches metadata for the [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.3.6*) - Fixes the issue where the user is able to edit the start time for an active scheduled update.
* **MDVA-42410** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que relatórios de cupom exibem apenas a moeda base padrão.
* **MDVA-41136** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*) - Fixes the issue where the expiration date of the `mage-cache-sessid` is not extended, resulting in customer data cleanup.
* **MDVA-39993** (*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Fixes the issue where inventory changes done through API do not reflect on the product page on the frontend.
* **MDVA-42855** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.5*) - Fixes the issue where a new customer address is not saved to the address book during checkout.
* **MDVA-42645** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.5*) - Fixes the issue where the Admin cannot refund reward points if store credit functionality is disabled.
* **MDVA-43414** (*for Adobe Commerce and Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Fixes the PHP fatal error that occurs when running the `inventory.reservations.updateSalabilityStatus` queue consumer on numerical SKUs.
* **MDVA-41628** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que usuários administradores restritos existentes obtêm acesso aos novos recursos quando novos módulos são adicionados.
* **MDVA-43348** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que a solicitação de cartão-presente GraphQL mostra um erro se `gift_card_options` contiver *uid*.
* **MDVA-39546** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que a data de início da atualização de preparo podia ser definida como uma data anterior à data atual durante a edição.
* **MDVA-42950** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os vídeos não são reproduzidos na página do produto.
* **MDVA-42689** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que o Adobe Commerce lança um erro *Violação de Restrição de Integridade* ao atualizar categorias de produto durante a importação.
* **MDVA-41229** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que as imagens disponíveis no back-end não são exibidas no front-end após a importação de produtos configuráveis.
* **MDVA-43731 (para Adobe Systems Comércio e Magento Open Source >=2.4.3 *&lt;2.4.4 ) - Corrige o problema em*que Search sinônimos *não funcionam mais quando o valor é adicionado em*Termos mínimos para correspondência *.***
* **MDVA-43232** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que a classificação de produtos em [!DNL Visual Merchandiser] por Preço Especial para Baixo/Cima causa um erro ao salvar a categoria.
* **MDVA-43726** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.3*) - Corrige o problema em que a regra de preço de catálogo baseada na correspondência de atributo de nível de repositório falha ao ser aplicada após a reindexação parcial.
* Patches atualizados: MDVA-36464, MDVA-37478, MDVA-38608.
* Adicionados metadados de patches para o [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que os atributos de preço do produto não podem ser atualizados para um site específico por meio da API REST.
* **MDVA-41350** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que uma exceção é lançada quando um usuário administrador com acesso restrito adiciona um produto fora do escopo de sua função por SKU em um pedido.
* **MDVA-42269** (*para Adobe Commerce e Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Corrige o problema em que um usuário administrador não consegue fazer logon no Admin devido ao *TypeError: strtotime() espera que o parâmetro 1 seja uma cadeia de caracteres, nulo dado* erro.
* **MDVA-40830** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que o crédito de armazenamento é aplicado várias vezes durante o posicionamento do pedido.
* **MDVA-42237** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que um preço especial de produto configurável não é atualizado após alterações no preço do subproduto.
* **MDVA-42520** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que a alíquota de imposto é aplicada duas vezes se *Habilitar Comércio Entre Fronteiras* for usado.
* Patches atualizados: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Patch obsoleto: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.5*) - Corrige o problema em que a atualização de atributos em massa cria regravação de URL para o Repositório Padrão somente após alterar *Visibilidade do produto*.
* **MDVA-43091** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que a solicitação de um produto do pacote do Administrador no back-end resulta no erro *Você não pode usar a quantidade decimal para este produto*.
* **MDVA-40816** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que as regras de produto relacionadas mostram produtos de categorias não definidas nas condições de regra.
* **MDVA-41305** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que o GraphQL mutation não retorna opções de produto configuráveis depois de adicioná-lo à lista de desejos.
* **MDVA-39181** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que as regras de produto relacionadas mostram produtos de categorias não definidas nas condições de regra.
* **MDVA-42584** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque configurável no back-end não é atualizado após a alteração do status de quantidade e estoque por meio da Importação ou da API.
* **MDVA-40175** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige o problema em que *Clicar para alterar o método de envio* não mostra botões de opção para selecionar métodos de envio no Administrador durante a reorganização.
* **MDVA-42768** (*para Adobe Systems Comércio e Magento Open Source >=2.3.4*&lt;2.4.5 ) - Corrige o problema em que o produto configurável exibe o preço regular como 0 quando *a Exibição Fora de Stock* é Sim.
* **MDVA-43201** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que ocorre um erro no fazer logon do cliente ao usar atributo DOB com determinados locais.
* Patches atualizados: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os filtros de data não estão funcionando corretamente quando o fuso horário do Adobe Commerce é diferente do fuso horário do ambiente local.
* **MDVA-42657** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não consegue selecionar categorias nas condições do segmento do cliente.
* **MDVA-42806** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que um email *Novo registro de empresa* é enviado sempre que uma empresa existente é atualizada por meio da API REST.
* **MDVA-37984** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que a funcionalidade [!DNL Visual Merchandiser] *Corresponder produto por regra* não filtra corretamente os produtos com atualizações de preparo.
* **MDVA-40488** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que os produtos configuráveis com produtos derivados indisponíveis não são mostrados em seu intervalo de preços correto.
* **MDVA-42507** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho.
* **MDVA-39163** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corrige o problema em que os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão de convidado.
* **MDVA-38626** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não consegue fazer um pedido no back-end usando o pagamento [!DNL PayPal Payflow Pro].
* **MDVA-38666** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.3.6*) - Corrige o problema em que o usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente.
* **MDVA-38526** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o usuário administrador não consegue acessar o [!DNL Site-Wide Analysis tool].
* Patches atualizados: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que os usuários recebem o erro 500 após definirem as *mensagens* mage-cookie se ela já existir, mas não há novas mensagens.
* **MDVA-41139** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os produtos configuráveis ficam Fora do Estoque após a importação do produto quando a quantidade=0 de um produto simples para uma de suas origens.
* **MDVA-42326** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os clientes recebem um erro no check-out após um tempo limite de sessão, mesmo se o carrinho de compras persistente estiver habilitado.
* **MDVA-42341** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que a consulta do GraphQL `categoryList` não filtra os resultados se uma solicitação tiver o cabeçalho Store.
* **MDVA-38393** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras do Catálogo param de funcionar para um produto configurável se seu produto simples for renomeado.
* **MDVA-39153** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que um valor de desconto é calculado incorretamente durante um novo pedido no Administrador.
* Updated patches: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os usuários administradores não podem acessar a grade do cliente após excluir o site.
* **MDVA-40311** (*para Adobe Commerce e Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Corrige o problema em que os usuários administradores recebem a mensagem de erro *Chave de formulário ou segurança inválida. Atualize a página* após fazer logon no Administrador se o caminho Admin personalizado estiver configurado e a chave secreta estiver habilitada.
* **MDVA-41631** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao tentar recuperar informações de pedidos sem um valor *telefone* opcional por meio do GraphQL.
* **MDVA-27239** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.3.6*) - Fixes the issue where cross-sell products are not displayed.
* Updated patches: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;2.4.4*) - Fixes the issue with missing products on the frontend during reindexing.
* **MDVA-40120** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.4*) - Fixes the issue where GraphQL sorting by DESC/ASC doesn&#39;t work with products having the same relevance or price.
* **MDVA-41399** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.2*) - Corrige o problema em que os usuários administradores não conseguem acessar a página *Gerenciar Carrinho de Compras* se um cliente adicionar um produto à lista de desejos.
* **MDVA-40609** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que os dados de produtos desabilitados estão ausentes na tabela de índice `cataloginventory_stock_status`, exibindo quantidades incorretas de produtos desabilitados.
* **MDVA-39031** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que é possível adicionar um produto ao carrinho por meio do GraphQL, mesmo que ele não esteja atribuído ao site de destino.
* **MDVA-41597** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao adicionar mais de um produto configurável ao carrinho usando o GraphQL.
* **MDVA-27456** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.3.7*) - Corrige o problema em que os usuários recebem um erro ao tentar carregar o [!DNL Swagger].
* **MDVA-32776** (*para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.2*) - Corrige o problema em que o status do estoque não é atualizado quando um solicitar é colocado, mas não enviado.
* **MDVA-30862** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.0*) - Corrige o problema com a data de pedido incorreta na fatura PDF impressa.
* Página de índice aprimorada para [!DNL Quality Patch Tool]. Adição de pesquisa e filtragem convenientes para [!DNL quality patches] na versão mais recente da ferramenta.
* Patches atualizados: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que é impossível criar uma atualização agendada nova ou editar uma existente para um produto se a Data de Término tiver sido removida anteriormente.
* **MDVA-41046** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que produtos simples com opções personalizadas estão disponíveis para atribuição a produtos configuráveis/agrupados.
* **MDVA-40545** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que somente o primeiro nó de uma página foi recuperado, mesmo que houvesse mais de um nó para a mesma página.
* **MDVA-41164** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Corrige o problema em que um usuário administrador não pode salvar ou editar uma Empresa com um atributo de cliente personalizado do tipo arquivo ou imagem.
* **MDVA-39229** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0*&lt;2.4.4 ) - Corrige o problema que faz com que o seguinte erro apareça após atualizar o Catálogo regra Atualização start tempo: *o Cron Job staging_synchronize_entities_period tem um erro: a atualização ativa não pode ser excluída.*
* **MDVA-40619** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que alterações no CMS página hierarquia causam um erro 500 ao tentar fazer edição em linha em um página CMS.
* **MDVA-41061** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque é redefinido para salável quando um produto é salvo do Administrador.
* **MDVA-31763** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras de preço do catálogo são revertidas (ou não aplicadas) até a reindexação manual.
* **MDVA-37748** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que uma query GraphQL retorna produtos não atribuídos a um catálogo compartilhado.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que faturas parciais para a mesma solicitar não podem ser criadas simultaneamente por meio da API REST.
* **MDVA-40101** (*para Adobe Systems Comércio e Magento Open Source >=2.3.2*&lt;2.4.0 ) - Corrige o problema em que os itens não são removidos do mini-carrinho após uma solicitar posicionamento bem-sucedida usando [!DNL PayPal Express] o Checkout.
* **MDVA-40401** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o valor de uso do cupom muda mesmo se um pedido falhar.
* **MDVA-40537** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Corrige o problema em que os usuários obtêm um erro ao criar uma exibição de repositório se existirem várias páginas do CMS com a mesma chave de URL.
* **MDVA-37725** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Corrige o problema em que emails de ordem assíncrona enviados de sites não padrão contêm URLs de logotipo do site padrão.
* **MDVA-39482** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que um produto sai do estoque se importado com a quantidade &quot;0&quot; quando ordens pendentes são habilitadas.
* **MDVA-40435** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema com um desconto incorreto em produtos de pacote com preços dinâmicos quando aplicados via GraphQL.
* **MC-42528** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Fixes the issue where the `categoryList` GraphQL query returns both assigned and unassigned categories.
* **MDVA-29400** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Fixes the issue with duplicated orders placed with [!DNL PayPal Express Checkout].
* **MDVA-26005** (*for Adobe Commerce and Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Fixes the issue where it is impossible to select a category in a category tree for Cart Price rule conditions.
* **MDVA-25631** (*for Adobe Commerce and Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Improves performance for editing and saving customer segments that contain a large number of customers.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.4*) - Fixes the issue where GraphQL search queries are not shown in popular search terms in the Admin.
* **MDVA-40601** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários obtêm um erro ao tentar obter informações sobre a categoria alteradas por meio da atualização agendada no GraphQL.
* **MDVA-37234** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que adicionar um item ao carrinho várias vezes (solicitação paralela) para o mesmo SKU cria um item de linha duplicado para a mesma ID do carrinho.
* **MDVA-33606** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários recebem um erro *Violação de restrição exclusiva* ao salvar uma página do CMS atribuída a uma hierarquia.
* **MDVA-31590** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que os usuários não podem atualizar atributos em massa usando filas assíncronas MySQL.
* **MDVA-36309** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que a pesquisa de produto por atributos está lenta nas grades de administração.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*para Adobe Systems Comércio e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que a fatura com FPT mostra um Total Geral errado quando o solicitar é pago do crédito armazenamento.
* **MDVA-37364** (*para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;=2.4.3*) - Corrige o problema em que o atributo personalizado do cliente do tipo de data quebra a grade do interface do cliente.
* **MDVA-39195** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2*&lt;=2.4.2-p2 ) - Corrige o problema *em que Adicionar ao* carrinho de botão estava inativo na categoria página quando redirecionar para carrinho habilitado.
* **MDVA-37115** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema no qual um aviso desnecessário *somente 0 é* mostrado na página do produto configurável.
* **MDVA-39521** (*para Adobe Systems Comércio e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que o usuário não consegue definir endereços de envio no carrinho com um número de telefone vazio via GraphQL.
* **MDVA-39384** (*for Adobe Commerce and Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Fixes the issue where the custom customer attribute for a company user is not saved.
* **MDVA-39043** (*for Adobe Commerce and Magento Open Source >=2.3.4 &lt;=2.4.3*) - Fixes the issue where the admin user with limited access gets an error when trying to add the *Products* widget to the CMS page.
* **MDVA-39966** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Fixes the issue with deploying incorrect locales.
* **MDVA-38852** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Fixes the issue where the catalog inventory by design locks tables for updates that significantly decrease performance in cases with several parallel orders.
* **MDVA-39986** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.3*) - Fixes the issue where the user is not able to place an order in the Admin on MacOS using the Safari browser.
* **MDVA-38447** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.4*) - Fixes two issues: where the *Not visible individually* configurable child products are returned in GraphQL response and optimize MySQL query for GraphQL products query with category filter.
* **MDVA-40134** (*para Adobe Systems Comércio e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o GraphQL não retorna produtos relacionados quando o Catálogo compartilhado está habilitado.
* **MDVA-39935** (*para Adobe Systems Comércio e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o GraphQL retorna produtos secundários configuráveis desativados no nível do site.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.4*) - Fixes the issue where the *Call to a member function getId()* error is displayed on the order details page in the Admin.
* **MDVA-34948 (para Adobe Systems Comércio e Magento Open Source >=2.3.6 &lt;=2.3.6-p1 ||=&quot;&quot;>=2.4.0 &lt;=2.4.0-p1 *) - Corrige o problema com consultas de longa duração, curtir `GET_LOCK`.&lt;/=2.3.6-p1>***
* **MDVA-39305** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Fixes the issue where registered customers are not able to log in with enabled Google ReCaptcha.
* **MDVA-37897** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.4*) - Fixes the issue with an incorrect redirect when a customer tries to add products with options from the Recently Viewed widget.

## v1.1.0 {#v1-1-0}

* Patch categories were introduced in order to improve the user experience and make searching for required patches easier for customers.
* The `patches.json` file has been renamed to `support-patches.json`.
* **MDVA-38799** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os produtos baixáveis não eram salvos após a criação de uma atualização de preparo.
* **MDVA-37592** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige o problema quando a classificação por preço não funciona corretamente para produtos com preço zero atribuído ao catálogo compartilhado.
* **MDVA-38827** (*para Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Corrige o problema em que os clientes recebem um email de remessa de pedido contendo uma mensagem de erro.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*para Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Corrige o erro ao salvar páginas do CMS: *Já existe um item com a mesma ID PAGE_ID*.
* **MDVA-34680** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Corrige o problema em que o tempo de criação da conta do cliente não é filtrado corretamente na grade de clientes.
* **MDVA-37068** (*para Adobe Systems Comércio >=2.3.1 &lt;2.4.4*) - Corrige a questão em que a taxa de imposto incorreta é exibida quando o carrinho de compras tem apenas produtos virtuais.
* **MDVA-38608** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que tabelas temporárias não são excluídas quando a reindexação não é concluída com êxito.
* **MDVA-38308** (*para Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Corrige os problemas relacionados à adição de vídeos [!DNL Vimeo] aos produtos.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige o problema em que o cliente não é levado para a página Confirmação de Pagamento ao usar o método [!DNL Paypal Payment Advanced].
* **MDVA-37082** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao salvar o estoque personalizado de produtos agrupados, fazendo com que o produto fique sem estoque no front-end.
* **MDVA-36572** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corrige o problema quando as atualizações do Aviso de Crédito não causam mais atualizações de reserva de produtos duplicadas no banco de dados.
* **MDVA-38132** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige o problema quando o painel Admin está inacessível devido a um erro de *muitos redirecionamentos*.
* **MDVA-38270** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema de informações de cartão-presente ausentes no total de pedidos no GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*for Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Fixes the issue with adding a configurable product to the cart via GraphQL when the website ID does not coincide with the store ID.
* **MDVA-36832** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corrige o problema em que as imagens são duplicadas em páginas com largura de exibição de 768px.
* **MDVA-37874** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Corrige o problema em que o *Valor de desconto fixo para o carrinho inteiro* é aplicado incorretamente a um produto de pacote que contém mais de uma opção.
* **MDVA-37913** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Corrige o problema em que os links baixáveis desaparecem se o produto baixável for atualizado via API.
* **MDVA-34330** (*para Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Corrige o problema em que os pedidos na grade Pedidos não são filtrados de acordo com o fuso horário do Administrador.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*para Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Corrige o problema em que o Adobe Commerce lança um erro ao criar uma fatura parcial para pedidos feitos com o método de pagamento *Pagamento na Conta* por meio da API REST.
* **MDVA-37362** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corrige o problema em que os valores de opção de produto e os valores de atributo de variante configuráveis estavam vazios na resposta do GraphQL.
* **MDVA-37288** (*para Adobe Commerce 2.4.2*) - Corrige o problema em que preços de camada incorretos foram retornados após a solicitação do GraphQL.
* **MDVA-37225** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Corrige o problema em que o processo de carregamento fica preso durante a criação rápida de pedido quando há um valor inteiro nas SKUs importadas.
* **MDVA-37224** (*para Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Corrige o problema em que os clientes não podem pagar pela cotação negociável com [!DNL PayFlow Pro] com outro produto no carrinho.
* **MDVA-36286** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige o problema em que a visualização do widget Produtos do Page Builder é interrompida se o mesmo SKU tiver uma posição diferente em subcategorias.
* **MDVA-30186** (*para Adobe Systems Comércio >=2.3.4 &lt;=2.3.5-p2,>=2.4.0 &lt;=2.4.0-p1,>=2.4.2 &lt;=2.4.2-p1*) - Corrige o problema em que as opções de atributo são classificadas por valor de opção em vez da contagem de itens do atributo na resposta do GraphQL.&lt;/=2.4.0-p1,>&lt;/=2.3.5-p2,>

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*para Adobe Systems Comércio >=2.3.0 &lt;=2.4.2*) - Corrige o problema em que as opções personalizadas antigas permanecem após serem alteradas via API.
* **MDVA-35773** (*para Adobe Systems Comércio >=2.3.6 &lt;=2.3.6-p1 ||=&quot;&quot;>=2.4.1 &lt;=2.4.2*) - Corrige o problema com o Total Geral não sendo mostrado como zero na Fatura para pedidos com desconto de 100%.&lt;/=2.3.6-p1>
* **MDVA-36833** (*para Adobe Systems Comércio 2.4.2*) - Corrige o problema com os resultados pesquisa mostrando números aleatórios de produtos por página depois de excluir alguns produtos do catálogo compartilhado.
* **MDVA-37182** (*para Adobe Systems Comércio >=2.4.1*&lt;=2.4.2) - Corrige o problema ao obter resultados incorretos pesquisa na [!DNL Elasticsearch] versão 6 e 7.
* **MDVA-36253** (*para Adobe Systems Comércio >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que o subtotal errado é exibido no mini carrinho após a exclusão do item.
* **MDVA-36853** (*para Adobe Systems Comércio 2.4.2*) - Corrige o problema sem que imagens apareçam ao carregar grandes galerias de mídia.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*para Adobe Systems Comércio >=2.3.4 &lt;=2.3.4-p2*) - Corrige o problema com a falta de produtos empacotados em categoria páginas.
* **MDVA-36615** (*para Adobe Systems Comércio 2.4.2*) - Corrige o problema com a contagem incorreta de produtos na grade de produtos administradores.
* **MDVA-36464** (*para Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Corrige o problema em que a configuração de notificação por email não está funcionando no nível de exibição de loja.
* **MDVA-36138** (*para Adobe Commerce ^2.3.2*) - Corrige o problema em que o preço de envio não é ajustado e o preço total de envio é mostrado aos clientes se nem todos os itens no carrinho se qualificarem para a regra de carrinho de remessa gratuita.
* **MDVA-36424** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Corrige o problema em que as imagens de mídia anexadas a elementos do page builder desaparecem quando o conteúdo está sendo editado repetidamente se o URL de base do backend for diferente do URL de base da loja.
* **MDVA-35984** (*para Adobe Commerce ^2.4.0*) - Corrige o problema com a quantidade incorreta do produto e a quantidade comercializável após criar várias remessas simultâneas para o mesmo produto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Isso corrige o problema em que a consulta do GraphQL não é armazenada em cache usando a marca de cache de categoria.
* **MDVA-33168** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema ao atualizar um atributo de produto via API. Todos os outros atributos são alterados para um valor vazio.
* **MDVA-19640** (*para Adobe Commerce >=2.3.0*) - Corrige o problema em que [!DNL Advanced Reporting] não está mostrando dados.
* **MDVA-11189** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema ao importar um arquivo CSV para atualizar o estoque de produtos; as linhas da tabela `cataloginventory_stock` são excluídas.
* **MDVA-26639** (*para Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Corrige o problema em que, se um novo modelo de email de confirmação de pedido for criado, os itens de pedido estarão ausentes na mensagem de pedido.
* **MDVA-15546** (*para Adobe Commerce >=2.3.0*) - Corrige o problema em que, após a criação de um pedido, uma *Coluna entity_id onde a cláusula é ambígua* erro é exibido no log de exceção.
* **MDVA-21095** (*for Adobe Commerce >=2.3.0 &lt;2.3.5*) - Fixes the issue when a query `INSERT INTO search_tmp` will not end after mass attribute value update.
* **MDVA-23845** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema em que os modelos de email não podem ser visualizados depois que a minificação do JavaScript é habilitada.
* **MDVA-22026** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que a importação de produtos do arquivo CSV, incluindo imagens de URLs externas, falha.
* **MDVA-22383** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema em que salvar um produto leva muito tempo e a página é quebrada.
* **MC-41359** (*para Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Corrige o problema das configurações incorretas de parâmetros de cookies do SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*for Adobe Commerce 2.4.1*) - Fixes the issue where Page Builder throws the following error: *An error has occurred while initiating Page Builder. Please consult with your technical support contact.*
* **MDVA-35356** (*for Adobe Commerce >=2.3.0 &lt;2.4.3*) - Fixes the issue with incorrect store credit return after partially invoiced order cancellation.
* **MDVA-33289** (*for Adobe Commerce >=2.4.0 &lt;2.4.3*) - Fixes the issue where raw JavaScript code is displayed in the billing address UI during checkout if [!DNL Google Tag Manager] is enabled.
* **MDVA-35982** (*for Adobe Commerce >=2.3.0 &lt;2.4.3*) - Fixes the issue where admin users restricted to a specific website cannot create a shipment for the order placed on same website.
* **MDVA-35155** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que é impossível comprar um pacote de produto se o título da opção foi alterado.
* **MDVA-35910** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema em que é impossível criar uma nova conta de cliente depois de desabilitar o Logon como funcionalidade do Cliente.
* **MDVA-34474** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao adicionar um produto à lista de requisições usando a API.
* **MDVA-34591** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema com um cálculo de desconto de regra de carrinho incorreto para *O Desconto de Quantidade Máxima é Aplicado a* e *Etapa de Quantidade de Desconto (Compre X)*.
* **MDVA-33704** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige o problema em que a opção de remessa *Coleta na loja* não é exibida, embora esteja configurada para estar disponível.
* **MDVA-34928** (*para Adobe Systems Comércio >=2.3.5 &lt;2.3.5-p2*) - Corrige o problema em que o carregador de página é exibido indefinidamente após a armazenamento crédito ser removido do pagamento.
* **MDVA-35254** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige os problemas com CAPTCHA durante o check-out.
* **MDVA-35569** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que o campo *impostos fixos de produto* não está sendo preenchido na resposta da GraphQL quando o estado é especificado.
* **MDVA-35847** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema B2B em que os Formulários de Usuários da Empresa são interrompidos se um atributo de cliente personalizado for usado.
* **MDVA-31307** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que há *memória insuficiente* erros em determinadas categorias devido a problemas com a lista de permissões de CSP dinâmica para blocos em cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o status de mensagem incorreto *em andamento* para a mensagem *concluída* correta para o consumidor `quoteItemCleaner` após excluir vários produtos.
* **MDVA-34102** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige a quantidade de Estoque Padrão igual a zero para produtos desabilitados nas páginas Grade de Produtos e Editar Produtos na área de Administrador.
* **MDVA-35286** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que há um erro se um cliente tiver agrupado produtos no carrinho e alternar do check-out Vários Endereços para o check-out Onepage.
* **MDVA-35312** (*para Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Corrige o código de resposta 500 quando uma solicitação GraphQL está vazia.
* **MDVA-34189** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige o tempo limite de 503 primeiros bytes em consultas [!DNL Visual Merchandiser] ao carregar a página Categoria de Administrador.
* **MDVA-34695** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correções negativas `children_count` após a exclusão de categorias.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige o problema em que a caixa de seleção *Usar valor padrão* é desmarcada após a aplicação das alterações agendadas. O problema aparece quando as alterações agendadas não estão mais em vigor.
* **MDVA-35064** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige o problema em que regravações de URL não são geradas para produtos configuráveis criados por meio da API.
* **MDVA-34943** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o pedido rápido armazena em cache as SKUs inseridas anteriormente.
* **MDVA-35197** (*para Adobe Commerce >=2.3.5 &lt;2.4.0*) - Corrige o problema em que há um erro ao adicionar ao carrinho usando o GraphQL se os produtos adicionados anteriormente ficarem indisponíveis.
* **MDVA-34850** (*para Adobe Commerce >=2.3.1 &lt;2.4.0*) - Corrige o problema em que as opções indisponíveis de um produto configurável não são exibidas, em vez de serem exibidas como tachadas.
* **MDVA-34867** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os valores de um campo de condição definidos para uma atualização agendada não são salvos.
* **MDVA-35092** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corrige o problema em que os usuários não podem adicionar vídeos do [!DNL Vimeo] devido à API [!DNL Vimeo] obsoleta.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige o problema em que a visualização do tipo de conteúdo Produtos do Page Builder é interrompida se os produtos correspondentes tiverem preços diferentes para cada site.
* **MDVA-32634** (*para Adobe Commerce ^2.3.1*) - Corrige o problema em que o `url_path` da categoria atribuída a todos os armazenamentos permanece inalterado após mover a categoria na hierarquia.
* **MDVA-33344** (*para Adobe Systems Comércio ^2.3.0*) - Corrige o problema em que de codificação rígida `rma_item` ID de conjunto de atributos padrão da entidade é usada em vez do valor do banco de dados.
* **MDVA-34192** (*para Adobe Systems Comércio >=2.3.4 &lt;2.4.3*) - Corrige o problema em que é impossível modificar/especificar a data de nascimento do cliente usando o formato dd/mm/aaaa.
* **MDVA-34847** (*para Adobe Commerce ^2.3.0*) - Corrige a conversão do tipo de IDs de repositório em número inteiro para a condição SQL em coleções de administradores para Usuário Admin com permissões personalizadas.
* **MDVA-34886** (*para Adobe Commerce ^2.3.2*) - Corrige o problema em que a pesquisa não retorna resultados se o atributo de produto *weight* estiver configurado como pesquisável.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema de falha no pagamento [!DNL PayPal Payflow Pro] com o erro de formato da lista de parâmetros de redirecionamento.
* **MDVA-34023** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que o erro *Nenhuma entidade com addressId* é exibida aleatoriamente nos navegadores dos visitantes.
* **MDVA-32759** (*para Adobe Commerce >=2.3.1 &lt;2.4.3 com extensão B2B*) - Corrige o problema em que os Catálogos Compartilhados estão excluindo os preços de camada existentes.
* **MDVA-33482** (*para Adobe Commerce ^2.3.5*) - Corrige o problema em que a geração de um Aviso de Crédito contra uma fatura parcial resulta em imposto para a ordem total em vez de imposto para essa fatura parcial.
* **MDVA-33393** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o erro *Desde que countryId não exista*.
* **MDVA-33632** (*para Adobe Systems Comércio >=2.3.0 &lt;2.3.7*) - Fornece uma correção em que a mensagem *de exceção Este produto está sem estoque* agora é exibida em uma administrador usuário ao tentar re-solicitar um produto fora de estoque.
* **MDVA-34469** (*para Adobe Systems Comércio >=2.4.1 &lt;2.4.2*) - Corrige o problema em que mutações de GraphQL na carrinho do cliente falham ao usar várias visualizações armazenamento.
* **MDVA-33976** (*para Adobe Systems Comércio >=2.3.0 &lt;2.3.7*) - Corrige o problema em que o produto pacote é mostrado De Stock na vitrine depois de remover a segunda opção do produto pacote.
* **MDVA-33894** (*para Adobe Systems Comércio >=2.4.0 &lt;2.4.1 with B2B extension*) - Corrige vários problemas para funcionalidade de ordem rápida, incluindo a adição e remoção de vários produtos e SKU distinção entre maiúsculas e minúsculas.
* **MDVA-27664** (*para Adobe Systems Comércio >=2.3.4*&lt;2.3.6 ) - Corrige o problema no formulário de registro do cliente causando um erro ao exibir: *ERROR - A data de nascimento não deve ser maior do que hoje.*
* **MDVA-33970** (*para Adobe Systems Comércio >=2.3.4 &lt;2.4.2*) - Corrige a questão em que há o sinal de moeda errada no Memorando de Crédito quando o escopo do atributo de preço é definido para o site.
* **MDVA-33992** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue of B2B special pricing displaying incorrectly during checkout.
* **MDVA-34100** (*for Adobe Commerce >=2.3.4 &lt;2.4.2 with B2B extension*) - Fixes the issue where a company account cannot be created from the company structure page.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*for Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Fixes the issue with duplicated images after product import from a CSV file.
* **MDVA-33382** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issues with indexers invalidation after products removal from a category.
* **MDVA-28511** (*para Adobe Systems Comércio >=2.3.5*&lt;2.3.6 ) - Corrige o problema em que não é possível concluir [!DNL PayPal] o check-out se o campo Nome contiver certos caracteres (curtir letras maiúsculas acentuadas).
* **MDVA-31519** (*para Adobe Systems Comércio >=2.3.5 &lt;2.3.6*) - Corrige o problema com tempos de espera limites no check-out de hóspedes quando um regra de vendas em todo o site está em uso.
* **MDVA-33281** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) - Fixes the issue where there is a fatal error in `inventory:reservation:list-inconsistencies` because of wrong SKU parameter type.
* **MDVA-24201** (*for Adobe Commerce >=2.3.0 &lt;2.3.5*) - Fixes the issue where prices do not reflect the scheduled cart price rule until manually re-indexed.
* **MDVA-32694** (*for Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Fixes the issue where an admin user cannot add a product to a negotiable quote if it is related to a not default store.
* **MDVA-33516** (*para Adobe Systems Comércio >=2.3.0 &lt;2.3.6*) - Corrige o problema em que editar um produto pacote em uma requisição lista resulta em um erro.
* **MDVA-33975** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) - Fixes multiple issues related to price calculation in GraphQL requests.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue with [!DNL PayPal] Settlement reports not being available under **Reports** > **Sales** > **[!DNL PayPal]** Settlement as expected.
* **MCP-87** (*for Adobe Commerce >=2.3.1 &lt;2.4.2*) - Improved indexation time for category product and stock indexers for large profiles.
* **MDVA-33106** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue where the rescheduled product changes are erased after the cron `run` command is executed.
* **MDVA-19391** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema em que `analytics_collect_data` está gerando um erro devido a registros de descrição NULL na tabela `catalog_category_entity_text`.
* **MDVA-20376** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema com a *Nenhuma entidade com customerId = 1* erro no `exception.log` para clientes conectados após o posicionamento do pedido.
* **MDVA-23764** (*para Adobe Systems Comércio >=2.3.2*&lt;2.3.5 ) - Corrige o bug `JsFooterPlugin.php` que afeta a exibição de blocos dinâmicos.
* **MDVA-13203** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.2*) - Corrige o problema em que a *violação de restringir integridade pesquisa_tmp_* aparece após uma reindexação completa.
* **MDVA-23426** (*para Adobe Systems Comércio >=2.3.3 &lt;2.3.5*) - Corrige o problema em que notificação emails enviados por Adobe Systems Comércio contêm um corpo em branco com conteúdo sendo adicionados como anexo.
* **MDVA-22150** (*para Adobe Commerce >=2.3.1 &lt;2.3.4*) - Corrige o problema em que os clientes com um produto configurável no carrinho e um cupom aplicado não podem fazer logon se esse produto configurável estiver desabilitado no Administrador.
* **MDVA-32545** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que as faturas não são enviadas automaticamente ao criar pedidos do Administrador.
* **MDVA-32714** (*para Adobe Commerce >=2.3.4 &lt;2.4.1*) - Corrige o problema em que o preço de grupo de clientes não está funcionando na consulta de produtos do GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Adiciona o *Subtotal (Incl. Imposto)* opção para condições de regra de preço.
* **MDVA-31236** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que os Administradores com acesso a recurso personalizado não podem configurar 2FA ou fazer logon.
* **MDVA-30845** (*para Adobe Commerce >=2.3.5 &lt;2.3.7*) - Corrige o problema em que o erro *Desculpe, nenhuma cotação está disponível para este pedido no momento* é exibido ao não se conectar ao UPS XML/USPS/DHL e nenhum outro método de envio está disponível.
* **MDVA-32133** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema em que a galeria de mídia não está carregando do Page Builder em determinados casos.
* **MDVA-12304** (*para Adobe Commerce >=2.3.0*) - Aumenta o número máximo de cookies de 50 para 200.
* **MDVA-32632** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige o problema em que os pedidos aparecem no sistema de pagamento, mas não no Adobe Commerce.
* **MDVA-32449** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que o histórico de pedidos carrega muito lentamente ou não carrega.
* **MDVA-32739** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que habilitar Notificações por Email Assíncronas envia emails de vendas antigos.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*para Adobe Systems Comércio 2.3.6, 2.4.1*) - Corrige o problema em que o *Criar uma Conta* botão permanece desativado após a correção inválido dados no *formulário Criar Novo conta* do cliente.
* **MDVA-31006** (*para Adobe Systems Comércio 2.3.0, 2.3.1*) - Corrige o problema em que pedidos duplicados aparecem após colocar uma solicitar usando [!DNL Paypal Express] o pagamento.
* **MDVA-25602** (*para Adobe Systems Comércio 2.3.0*) - Corrige o problema com [!DNL PayPal Payflow Pro] o método de pagamento e o tratamento de cookies como `SameSite=Lax` padrão na Cromo 80 navegador e na resposta da API redirecionar ao fazer logon página do cliente.

## v1.0.10 {#v1-0-10}

Correções secundárias para versões de patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema em que a Regra de Preço do Carrinho com o cupom não se aplica via GraphQL quando a ação *Desconto de valor fixo para carrinho inteiro* é usada.
* **MDVA-30889** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que ocorre um erro após faturar um pacote com produtos virtuais e simples como opções.
* **MDVA-31791** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Melhora o desempenho da página do produto nos casos em que as regras de destino ou os produtos vinculados são usados.
* **MDVA-31168** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.2*) - Corrige o problema em que a exportação de CSV arquivo do produto não aparece e há uma memória alocação erro.
* **MDVA-32313** (*para Adobe Systems Comércio >=2.3.0 &lt;2.3.4*) - Corrige o problema em que produtos configuráveis poderiam ser adicionados à lista de desejos com as opções de configuração erradas.
* **MDVA-31759** (*para Adobe Systems Comércio >=2.3.0*&lt;2.4.2 ) - Corrige o problema em que os produtos não são atualizados com *valores de* atributos suspensos e *de área* de texto durante CSV importação.
* **MDVA-32012** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os CEP da Coreia e da Argentina não podem ser validados.
* **MDVA-31640** (*para Adobe Systems Comércio >=2.3.1 &lt;2.3.6 ||=&quot;&quot;>=2.4.0 &lt;2.4.1*) - Corrige o problema em que um preço especial não pode ser atualizado via API REST.&lt;/2.3.6>
* **MDVA-28651** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 com extensão B2B*) - Corrige o problema em que há problemas de desempenho ao carregar cotações negociáveis por meio da API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.1 with B2B extension*) - Corrige o problema em que um sinal de moeda errada é exibido na grade do Credit Memo.
* **MDVA-31295** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os pontos de recompensa não são calculados quando uma solicitar parcial é concluída e os itens são tributados.
* **MDVA-30112** (*para Adobe Systems Comércio >=2.3.4*&lt;2.4.2 ) - Corrige o problema em que, se o número de pedidos exceder o *valor de tamanho* fixo, Adobe Systems Comércio considera os pedidos com *status pendente* como inconsistências.
* **MDVA-31150** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.2*) - Corrige a questão em que os saldos de cartão de crédito e presente armazenamento não são retornados pela chamada GET API Rest Da Fatura, quando a fatura foi postada por uma chamada de Rest API e o solicitar foi parcialmente pago pela armazenamento contas de crédito e cartão do presente.
* **MDVA-30963** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema em que os resultados da filtragem de produtos definem para conter apenas valores especificados para o escopo *Todas as exibições de loja* no Admin, incluir produtos com valores substituídos no nível de exibição de loja.
* **MDVA-29954** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 com extensão B2B*) - Corrige o problema no qual os emails *Nova Solicitação de Registro de Empresa* e *Você foi vinculado a uma empresa* são enviados do endereço errado.
* **MDVA-28357** (*para Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Substitui o analisador padrão por um analisador personalizado com tokenizador de palavra-chave para o campo SKU no índice [!DNL ElasticSearch] para fazer com que as consultas de pesquisa curinga funcionem com SKUs que contenham um hífen (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o status de pedido personalizado foi alterado para *Processando* após a criação de remessa parcial usando WebApi.
* **MDVA-30428** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se esse produto estiver atribuído a uma fonte de estoque personalizada.
* **MDVA-30594** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.2*) - Corrige o problema em que um solicitar com vários endereços não podia ser salvo durante o check-out quando o FPT é configurado.
* **MDVA-29148** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema ao criar um produto por meio de uma chamada de API. O atributo personalizado de produto do tipo `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multisseleção) não usará seu valor padrão se nenhum valor for fornecido na carga.
* **MDVA-30837** (*para Adobe Commerce >=2.3.1 &lt;2.3.5*) - Adição de uma definição de configuração *Incluir Imposto no Valor: Sim/Não* na configuração do método de Envio Gratuito. Quando *Incluir Imposto no Valor* estiver definido como *Sim*, o Valor Mínimo do Pedido será calculado como Subtotal + Imposto. Quando *Incluir Imposto no Valor* estiver definido como *Não*, o Valor Mínimo da Ordem será calculado como Subtotal
* **MDVA-25028** (*para Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Corrige o problema quando os pedidos feitos usando o [!DNL PayPal Payflow Pro] não são definidos como status de Suspeita de Fraude quando os filtros de fraude são acionados.
* **MDVA-31224** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*) - Melhora o desempenho da operação de reindexação `catalog_product_price` para produtos agrupados.
* **MDVA-31321** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige uma página em branco (erro) quando *Mostrar tudo* está selecionado. [!DNL Elasticsearch] retorna uma grande lista de ids de produtos. Nesse cenário, a cláusula order by é convertida em um formato SQL incorreto.
* **MDVA-30815** (*for Adobe Commerce >=2.3.2 &lt;2.3.4*) - Fixes the issue where when you change how many search results should be displayed on the search results page, Adobe Commerce displays a blank page. [!DNL Elasticsearch] now correctly displays results from category pages when you change the number of search results viewed per page.
* **MDVA-30782** (*for Adobe Commerce >=2.3.5 &lt;2.4.2*) - Fixes the issue where Dynamic Block is displayed regardless of cart rule.
* **MDVA-31021** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue where performance issues exists in `module-catalog-import-export/Model/Import/Product/Option.php`. If there are more than ~100k records in `catalog_product_option` table, a new CSV with single product takes less than 10 sec to validate.
* **MDVA-31007** (*for Adobe Commerce >=2.4.0 &lt;2.4.1*) - Fixes the issue where custom address attributes are not correctly displayed in the order details page in the my account area and in the backend.
* **MDVA-29389** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema no Relatório Avançado em que o `analytics_collect_data` cronjob diz: *A porta deve ser configurada dentro do parâmetro de host (como localhost:3306)*.
* **MDVA-31343** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema com a classe de corpo removida `page-layout-category-full-width` quando uma categoria é agendada.
* **MDVA-30945** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que você recebe uma mensagem de erro fatal ao atualizar os carrinhos `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*para Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementa a funcionalidade *Mínimo deve corresponder* e a pesquisa parcial para o mecanismo [!DNL Elasticsearch]. Soluciona problemas com hifens em consultas de pesquisa.
* **MDVA-30102** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corrige o problema em que o cache Redis cresce rapidamente, pois os caches de layout não têm TTL.
* **MDVA-30599** (*para Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Corrige o problema em que as cotações de convidado criadas usando a API são marcadas incorretamente como cotações para clientes conectados.
* **MDVA-29446** (*para Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Corrige o problema em que o preço do método de envio não aplicável é mostrado como zero durante o check-out.
* **MDVA-30357** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corrige o problema em que URLs de imagem incorretas são criadas ao gerar um mapa de site pelo cron.
* **MDVA-30565** (*para Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Corrige o problema em que *Nenhuma entidade com o erro cartid = 0* é exibida para o cliente convidado na verificação da loja se o carrinho de compras persistente estiver habilitado.
* **MDVA-29787** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Corrige o problema em que a regra de destino para produtos relacionados não funciona quando *é uma das* condições são usadas para definir os produtos a serem exibidos.
* **MDVA-30977** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Corrige o problema de produtos aleatórios ausentes das categorias após a reindexação.
* **MDVA-28202** (*para Adobe Systems Comércio >=2.3.4 &lt;=2.4.2*) - Corrige o problema em que a Navegação em camadas não filtra produtos configuráveis corretamente quando o MSI é usado.
* **MDVA-28300** (*para Adobe Systems Comércio >=2.3.0 &lt;2.3.6*) - Corrige o problema em que a GQL solicitação não reflete as mudanças de preço das regras de preço do catálogo.
* **MDVA-31006** (*para Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Corrige o problema em que pedidos duplicados aparecem após fazer um pedido usando o pagamento [!DNL Paypal Express].

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema na navegação em camadas, em que o valor *No* para atributos de produto do tipo booleano não era incluído na navegação em camadas se [!DNL Elasticsearch] fosse usado como um mecanismo de pesquisa.
* **MDVA-28191** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que nenhum método de pagamento é carregado durante a criação do pedido por meio do Administrador.
* **MDVA-29959** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 com extensão B2B*) - Corrige o problema em que o usuário administrador restrito com permissões de *Empresas* não tem permissão para excluir a conta da empresa.
* **MDVA-30265** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que o link de rastreamento de remessa para de funcionar após a criação da fatura.
* **MDVA-28409** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema em que o trabalho `sales_clean_quotes` do cron falha com o erro *memória insuficiente* quando o número de aspas expiradas no banco de dados é enorme.
* **MDVA-30593** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema em que as cotações expiradas de acordo com a configuração Tempo de Vida da Cotação não são limpas.
* **MDVA-30107** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que o alternador de repositório não funciona como esperado se forem usadas diferentes URLs base para exibições de repositório.
* **MDVA-28763** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que a imagem do produto está sendo duplicada após a atualização das informações do produto usando a API REST mais de uma vez.
* **MDVA-30284** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o indexador da Pesquisa de Catálogo falha devido ao seguinte erro *[!DNL Elasticsearch]: o limite do total de campos no índice foi excedido.*
* **MDVA-29042** (*para Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 com extensão B2B*) - Corrige o problema em que as permissões de Catálogo foram alteradas para *Permitir* automaticamente depois que o novo produto foi adicionado ao catálogo compartilhado.
* **MDVA-30428** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se esse produto estiver atribuído a uma fonte de estoque personalizada.
* **MDVA-28661** (*para Adobe Commerce >=2.3.0 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que um erro é lançado na seção de conta da empresa Usuários da Empresa depois que o administrador da empresa é alterado.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*para Adobe Commerce 2.3.1 - 2.3.4-p2*) - Corrige o problema em que os trabalhos cron falham se o nome do banco de dados for muito longo, resultando na não atualização de categorias no front-end.
* **MDVA-30106** (*para Adobe Commerce ^2.3.0*) - Corrige um problema em que, durante pagamentos de check-out, não é carregado com *Não é possível ler a propriedade &#39;length&#39; de erro nulo* no console JS.
* **MDVA-28656** (*para Adobe Systems Comércio >=2.3.1 &lt;2.3.6 ||=&quot;&quot;>=2.4.0 &lt;2.4.2*) - Corrige o problema em que se um solicitar foi colocado sem informações de pagamento necessárias (por exemplo, com 100% de desconto) e uma fatura foi criada para o solicitar, o status solicitar muda para *Fechado* em vez de Todos os Apps.&lt;/2.3.6>
* **MDVA-30209** (*para Adobe Systems Comércio 2.3.0 - 2.3.3-p1*) - Corrige o problema em que o grupo do cliente foi alterado para padrão se o cliente atualizasse suas informações conta.
* **MDVA-30123** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que os rótulos de opção de atributo não são traduzidos corretamente para consultas do GraphQL.
* **MDVA-29996** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que, após habilitar a permissão de categoria, a página de categoria não é armazenada em cache pelo Cache de Página Inteira.
* **MDVA-30164** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Corrige o problema em que os registros de clientes não podem ser exportados da grade Clientes se existirem atributos de clientes personalizados.
* **MDVA-30444** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige o problema em que nenhum email de confirmação é enviado para pedidos feitos usando o GraphQL.
* **MDVA-30490** (*para Adobe Commerce 2.3.4 - 2.3.5-p2*) - Corrige o problema em que a comparação de produtos lança a página de erro 500 se um dos produtos tiver uma descrição curta vazia.
* **MDVA-30232** (*para Adobe Commerce >=2.3.1 &lt;2.4.1*) - Corrige o problema em que não é possível reordenar se o pedido original contiver um cartão-presente.
* **MDVA-29965** (*for Adobe Commerce >=2.3.3 &lt;2.4.0*) - Corrige o problema em que os clientes obtêm o erro Chave de Formulário Inválida ao adicionar um produto ao carrinho.
* **MDVA-30008** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema B2B em que não é possível fazer pedidos por meio da API de Administração para um produto que está em um catálogo público.
* **MDVA-22469** (*para Adobe Systems Comércio 2.3.2-p2 - 2.3.3-p1*) - Corrige o problema em que, após atualizar para o Adobe Systems Comércio 2.3.3, Page Builder não está funcionando no painel Admin e alguns arquivos JS e CSS não estão sendo carregados.
* **MC-35984** (*para Adobe Systems Comércio >=2.4.0 &lt;2.4.1*) - Corrige o problema em que os comerciantes não conseguiam interagir com nenhum elemento página no página de Devoluções após criar um rótulo de envio para uma Autorização de Mercadoria de Retorno (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*para Adobe Systems Comércio 2.3.0 - 2.3.4*) - Corrige o problema com [!DNL PayPal Payflow Pro] o método de pagamento e o tratamento de cookies como `SameSite=Lax` padrão na Cromo 80 navegador e na resposta da API redirecionar ao fazer logon página do cliente.
* **MDVA-26694** (*para Adobe Systems Comércio >=2.3.0 &lt;2.3.6 || 2.4.0*) - Corrige o problema com caches de produtos e catálogos expirando diariamente, embora esteja programado para expirar de forma diferente.
* **MDVA-27825** (*para Adobe Systems Comércio >=2.3.0 &lt;2.4.1*) - Corrige o problema em que a exportação de grandes quantidades de dados falhou por causa de vazamento de memória.
* **MDVA-29085** (*para Adobe Systems Comércio >=2.3.0 &lt;=2.3.5-p1*) - Corrige o problema B2B em que novos empresa emails obrigatórios são enviados se um empresa for criado pela API.
* **MDVA-29344** (*para Adobe Systems Comércio >=2.3.5 &lt;=2.4.0-p1*) - Corrige o problema em que Page Builder fica preso após copiar o texto de um elemento de cabeçalho para um elemento de texto.
* **MDVA-29835** (*para Adobe Systems Comércio >2.3.1 &lt;2.4.2*) - Corrige o problema em que pedidos de cartão de presente continham dois códigos em vez de um.
* **MDVA-30052** (*para Adobe Systems Comércio >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema com conteúdo privados (armazenamento locais) não sendo preenchidos corretamente, o que resultou em problemas de desempenho.
* **MDVA-30131** (*para Adobe Systems Comércio >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema com navegação em camadas, onde o *valor Não* para atributos de produtos do tipo booleano não era incluído em camadas navegação se [!DNL Elasticsearch] fosse usado como mecanismo de pesquisa.
* **MDVA-35514** (*para Adobe Systems Comércio >=2.4.0 &lt;2.4.1*) - Corrige o problema com a criação de um rótulo de envio e a adição de produtos solicitados a um pacote na janela modal Criar Pacotes.
