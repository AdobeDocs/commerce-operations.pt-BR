---
title: Notas de versão
description: Saiba mais sobre os patches disponíveis para o Adobe Commerce e os problemas que eles resolvem.
source-git-commit: 6d0b5515792afe33eab440290413b84d251796cc
workflow-type: tm+mt
source-wordcount: '9752'
ht-degree: 0%

---

# Notas de versão

O [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) O fornece patches individuais desenvolvidos pelo Adobe e pela comunidade do Magento Open Source. Ele permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce ou do Magento Open Source. Você pode aplicar patches a projetos do Adobe Commerce e do Magento Open Source, independentemente de quem desenvolveu o patch. Por exemplo, você pode aplicar um patch desenvolvido pela comunidade a projetos da Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) para obter instruções sobre como aplicar patches a seus projetos do Adobe Commerce ou Magento Open Source. Consulte [Patches disponíveis](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no Guia de atualização de software para consultar uma lista completa dos patches lançados.

>[!INFO]
>
>Para obter informações sobre [!DNL quality patches] criado pela Comunidade para o Magento Open Source, consulte a [notas de versão](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que um administrador com acesso restrito a um escopo específico não pode excluir revisões de produtos.
* **ACSD-47107** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Corrige o problema em que o desconto de Regra de Preço de Catálogo é aplicado às opções de produto personalizadas.
* **ACSD-47232** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema no qual cupons com condições de peso total não podem ser aplicados no Admin.
* **ACSD-46519** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6) - Corrige o problema no qual a solicitação GraphQL categoryList retorna uma product_count incorreta para uma categoria de âncora.
* **ACSD-47027** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige uma solicitação de UpdateCompanyRole GraphQL lenta.
* **ACSD-47666** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema no qual a função de filtro não funciona na grade Admin > Sistema > Permissões > Funções de usuário > uma função > Usuários de função .
* **ACSD-47497** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema no qual a guia Serviços não está visível na Configuração em Admin.
* Correção atualizada: ACSD-47743.
* Correções substituídas: MDVA-42807

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3) - Corrige o _Tentando acessar o deslocamento da matriz no valor do bool de tipo_ ao acessar determinados caminhos de categoria não existentes para produtos conhecidos no PHP 7.4.
* **ACSD-47332** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o cron falha com um erro que só é reportado ao executar entre 00:00 e 00:59 UTC.
* **ACSD-47280** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema que fazia com que a desativação do recurso de catálogo compartilhado em um escopo específico não funcionasse corretamente.
* **ACSD-47106** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema no qual um valor não pode ser salvo em um novo atributo personalizado em uma página de criação de empresa.
* Correção atualizada: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que um usuário recebe um erro ao atribuir um grande número de fontes de produtos.
* **ACSD-46856** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Melhora o desempenho ao atualizar os preços da camada por meio de Sistema > Configuração > Importar > Preços Avançados.
* **ACSD-46541** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que um usuário administrador não pode criar um aviso de crédito se um item de pedido for excluído.
* **ACSD-46581** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema no qual o total estimado de imposto não é atualizado após selecionar um país no carrinho de compras.
* **ACSD-46618** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o widget de lista de produtos mostra preços em cache incorretos para um cliente conectado.
* **ACSD-46674** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema no qual as opções personalizadas de um tipo de imagem são exibidas como HTML nos emails do cliente.
* **ACSD-46988** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a Solicitação de API de &quot;moeda&quot; GraphQL retorna valores NULL para uma moeda personalizada.
* **ACSD-47076** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) - Corrige o problema no qual os vídeos do Vimeo não podem ser reproduzidos na loja.
* **ACSD-45071** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Corrige o problema em que a fonte padrão é adicionada ao produto durante a importação.
* **AC-3023** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Atualize o esquema da DHL para a versão mais recente 10.0.
* Correções atualizadas: MDVA-42584.
* Correções substituídas: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que um usuário obtém um status de pedido incorreto quando reembolsado usando o crédito da loja.
* **ACSD-46703** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige o problema que impedia arrastar e soltar opções personalizadas em uma página de edição de produto.
* **ACSD-44851** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema que impedia que uma categoria com subcategorias fosse aberta ou expandida.
* **ACSD-46815** (*para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6*) - Corrige o problema onde a solicitação de árvore de categoria é limitada a 20 categorias.
* **ACSD-45675** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema em que a exportação do produto usa nomes de categoria da *Exibição de armazenamento padrão* escopo.
* **ACSD-46869** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige o problema em que um produto configurável em um carrinho não é atualizado por meio de um *API PUT REST* sem alterar a quantidade do produto.
* **MDVA-42768-V2** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema no qual o Produto configurável exibe o preço normal como *0* when *Exibir esgotado* é *Sim*.
* Correções atualizadas: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Patch obsoleto: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema onde a solicitação de árvore de categoria é limitada a 20 categorias.
* **ACSD-45781** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.2*) - Corrige o problema no qual o campo de pesquisa frontal da loja não é exibido em dispositivos móveis.
* **ACSD-46192** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;2.4.5*) - Corrige o problema com o uso da variável `async/bulk/V1/configurable-products/bySku/options` endpoint .
* **ACSD-46404** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige o problema em que um usuário administrador não consegue fazer logon após a atualização para a versão 2.4.4.
* Correções atualizadas: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que uma mutação de produto GraphQL para uma loja específica retorna todas as variantes configuráveis, incluindo aquelas não atribuídas à loja solicitada.
* **ACSD-46146** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que dois e-mails de confirmação de pedido são enviados após fazer um pedido pelo Administrador.
* **ACSD-45255** (*para Adobe Commerce >=2.4.3 &lt;2.4.6*) - Corrige uma exceção na página Relatório de Estoque Baixo para um usuário administrador restrito.
* **ACSD-45488** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6*) - Corrige o problema em que um produto configurável com várias fontes não é retornado automaticamente para o In Stock.
* **ACSD-45754** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema no qual os Pontos de recompensa não são adicionados após aplicar um cupom ao carrinho.
* **ACSD-45849** (*para Adobe Commerce >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo.
* **ACSD-45257** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema em que GraphQL não exibe um desconto ao carrinho corretamente.
* **ACSD-44938** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que `VAT_ID` não pode ser aplicado em uma solicitação GraphQL para um usuário convidado.
* Correções atualizadas: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige o problema em que a quantidade de estoque de um produto virtual é calculada incorretamente após a criação de um aviso de crédito.
* **ACSD-43887** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando Pedidos de compra para empresas são ativados.
* **ACSD-45143** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que a variável `setShippingAddressesOnCart` não permite definir o código de região numérica como *região*.
* **ACSD-44591** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6*) - Corrige o erro que ocorre quando um pedido é feito sem a confirmação CAPTCHA.
* **ACSD-45520** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que as opções de amostra não são pré-selecionadas na página de detalhes do produto quando um usuário edita produtos configuráveis do carrinho de compras.
* **ACSD-45169** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6*) - Corrige o problema em que [!DNL Visual Merchandiser] não exibe o estoque e o preço corretos de um produto configurável após a aplicação de uma atualização de preparo.
* **ACSD-45424** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.6*) - Corrige o problema em que uma compensação de reserva incorreta é criada após um reembolso parcial (aviso de crédito).
* **MDVA-42807** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema no qual o sinal de moeda personalizado não é exibido na frente da loja.
* Correções atualizadas: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os totais de pedidos no relatório de Pedidos são calculados incorretamente para o usuário administrador restrito.
* **MDVA-44940** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o erro SQL que ocorre ao salvar a categoria do Administrador.
* **MDVA-44562** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Corrige o problema em que a ID de armazenamento não padrão para itens de cotação é substituída pela ID de armazenamento padrão, apesar da solicitação GraphQL originada da exibição de armazenamento não padrão.
* **MDVA-43167** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que a ação em massa da grade de ordem de administrador não se aplica a várias páginas quando o usuário administrador seleciona todos os pedidos.
* **MDVA-44044** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Corrige o problema em que um produto não é exibido na página de categoria depois de ser atribuído a um novo site da Web.
* **MDVA-42509** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.4*) - Corrige o problema em que um CSV não podia ser carregado para uma ordem rápida, resultando em um *Não é possível enviar o cookie* erro.
* Correções atualizadas: MDVA-41061, MDVA-42584.
* O prefixo do novo [!DNL Quality Patches Tool] os patches serão alterados em *MDVA* para *ACSD* devido a alterações no processo interno.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que um item adicional não pode ser adicionado ao carrinho quando a quantidade mínima do item já está no carrinho.
* **MDVA-44887** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige o *SyntaxError não captado: Token inesperado &#39;const&#39;* no painel Administração.
* **MDVA-43718** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Correções *O consumidor não está autorizado a acessar %resources.* que aparece ao acessar um catálogo compartilhado de uma integração personalizada.
* **MDVA-44660** (*para Adobe Commerce e Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Corrige o problema em que o caractere de acento grave ``` ` ``` não pôde ser usado para o nome e sobrenome de um cliente.
* **MDVA-40896** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o *Erro: TypeError: Argumento 3 passado para Magento* erro na API em massa de produto assíncrona.
* **MDVA-38559** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige o */V1/customers/API de pesquisa* para clientes com mais de uma assinatura.
* **MDVA-44533** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.4*) - Corrige o problema em que o desconto é aplicado incorretamente a um produto filho de pacote.
* Correções atualizadas: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que os produtos *Não visível individualmente* ainda é exibido em Resultados de pesquisa avançada do catálogo.
* **MDVA-44100** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que todos os FPTs são atribuídos ao último produto no carrinho de compras e são redefinidos para outros produtos.
* **MDVA-43605** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corrige o problema em que os dados do pedido retornam valores negativos para os totais das linhas ao usar a API Restante.
* **MDVA-43102** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corrige o problema em que a quantidade comercializável não é atualizada corretamente quando um reembolso é feito por meio da REST API.
* **MDVA-43178** (*para Adobe Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Corrige o problema em que um token de cliente para uma loja personalizada não pode ser recuperado em GraphQL.
* **MDVA-43859** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema no qual o erro *Nenhuma entidade com customerId =* é registrado quando um cliente excluído tenta fazer logon.
* **MDVA-44147** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que uma solicitação GraphQL não retorna Listas de Requisições.
* **MDVA-44505** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige os problemas em que GraphQL Aplicando Pontos de Recompensa não atualiza o Total Geral e em que o crédito da loja é aplicado várias vezes durante o posicionamento do pedido.
* Correções atualizadas: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige o problema em que a Regra de produto relacionada funciona somente quando o Segmento do cliente está definido como *Todos*.
* **MDVA-39605** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema no qual o TTL de cache do Redis (data de expiração) tem um valor errado.
* **MDVA-43862** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige o problema em que o cliente não pode atualizar itens do carrinho devido a um GraphQL *Mudança UpdateCartItems* erro.
* **MDVA-43824** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Corrige o problema em que um erro aparece ao cancelar pedidos com um desconto.
* **MDVA-43451** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema no qual o erro *A loja que foi solicitada não foi encontrada. Verifique a loja e tente novamente.* é exibido ao configurar um catálogo compartilhado para um site específico.
* **MDVA-43491** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corrige o problema em que o rótulo da imagem base não é atualizado ao importar produtos para um site de várias lojas.
* **MDVA-43601** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema com acionadores ausentes após a reindexação completa.
* **MDVA-42046** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Corrige o problema em que um valor incorreto é atribuído a um atributo de produto com um campo de entrada de data ao atualizar um produto.
* **MDVA-43935** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema no qual o produto da venda adicional é exibido duas vezes.
* **MDVA-44188** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que emails emitidos pelo sistema com `.-` os endereços em não são enviados.
* **MDVA-42283** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que o formato de data e hora na grade de pedido de administrador para a localidade francesa é inválido.
* Correções atualizadas: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Adição de metadados de patches para o [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corrige o problema em que o usuário pode editar a hora de início de uma atualização agendada ativa.
* **MDVA-42410** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os relatórios de cupom exibem apenas a moeda base padrão.
* **MDVA-41136** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que a data de expiração da variável `mage-cache-sessid` não é estendida, resultando na limpeza dos dados do cliente.
* **MDVA-39993** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Corrige o problema que fazia com que as alterações de inventário feitas por meio da API não refletissem na página do produto no front-end.
* **MDVA-42855** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que um novo endereço do cliente não é salvo no catálogo de endereços durante o check-out.
* **MDVA-42645** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o Administrador não pode reembolsar os pontos de recompensa se a funcionalidade de crédito de loja estiver desativada.
* **MDVA-43414** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Corrige o erro fatal do PHP que ocorre ao executar o `inventory.reservations.updateSalabilityStatus` consumidor da fila em SKUs numéricas.
* **MDVA-41628** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que usuários de administradores restritos existentes obtêm acesso aos novos recursos quando novos módulos são adicionados.
* **MDVA-43348** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema no qual a solicitação GraphQL do cartão-presente mostra um erro se `gift_card_options` contain *uid*.
* **MDVA-39546** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema no qual a data de início da atualização de preparo podia ser definida como uma data anterior à data atual durante a edição.
* **MDVA-42950** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema no qual os vídeos não são reproduzidos na página do produto.
* **MDVA-42689** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema no qual o Adobe Commerce lança um *Violação de restrição de integridade* erro ao atualizar categorias de produto durante a importação.
* **MDVA-41229** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que as imagens disponíveis no backend não são exibidas no front-end após a importação de produtos configuráveis.
* **MDVA-43731** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que *Sinônimos de pesquisa* não funciona mais quando o valor é adicionado em *Mínimo de termos para correspondência*.
* **MDVA-43232** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que a classificação de produtos no [!DNL Visual Merchandiser] por Preço Especial Até a Parte Inferior/Superior causa um erro ao salvar a categoria.
* **MDVA-43726** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.3*) - Corrige o problema em que a regra de preço do Catálogo baseada na correspondência de atributos de nível de loja não é aplicada após a reindexação parcial.
* Correções atualizadas: MDVA-36464, MDVA-37478, MDVA-38608.
* Adição de metadados de patches para o [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema no qual os atributos de preço do produto não podem ser atualizados para um site específico por meio da REST API.
* **MDVA-41350** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que uma exceção é lançada quando um usuário administrador com acesso restrito adiciona um produto fora do escopo da função pelo SKU em um pedido.
* **MDVA-42269** (*para Adobe Commerce e Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Corrige o problema em que um usuário administrador não consegue fazer logon no Administrador devido ao *TypeError: strtotime() espera que o parâmetro 1 seja uma string, null given* erro.
* **MDVA-40830** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que o crédito da loja é aplicado várias vezes durante o posicionamento do pedido.
* **MDVA-42237** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que um preço especial de produto configurável não é atualizado após alterações no preço do subproduto.
* **MDVA-42520** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que a taxa de imposto é aplicada duas vezes se *Habilitar comércio transfronteiriço* é usada.
* Correções atualizadas: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Patch obsoleto: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.5*) - Corrige o problema em que a atualização de atributo em massa cria a reescrita de URL para o armazenamento padrão somente após a alteração *Visibilidade do produto*.
* **MDVA-43091** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema no qual solicitar um produto de pacote do Administrador no back-end gera o erro *Não é possível usar a quantidade decimal para este produto*.
* **MDVA-40816** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema no qual as regras de produto relacionadas mostram produtos de categorias não definidas nas condições da regra.
* **MDVA-41305** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que a mutação GraphQL não retorna opções de produto configuráveis após adicioná-la à lista de desejos.
* **MDVA-39181** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema no qual as regras de produto relacionadas mostram produtos de categorias não definidas nas condições da regra.
* **MDVA-42584** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque configurável no backend não é atualizado após alterar a quantidade e o status do estoque por meio de Importar ou API.
* **MDVA-40175** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige o problema em que *Clique para alterar o método de envio* não mostra botões de opção para selecionar métodos de envio em Admin durante o repedido.
* **MDVA-42768** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que o Produto configurável exibe o preço normal como 0 quando *Exibir esgotado* é Sim.
* **MDVA-43201** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que ocorre um erro no logon do cliente ao usar o atributo DOB com determinadas localidades.
* Correções atualizadas: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os filtros de data não estão funcionando corretamente quando o fuso horário do Adobe Commerce é diferente do fuso horário do ambiente local.
* **MDVA-42657** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não consegue selecionar categorias nas condições do segmento do cliente.
* **MDVA-42806** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que uma *Registro de nova empresa* O email é enviado sempre que uma empresa existente é atualizada por meio da REST API.
* **MDVA-37984** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que a variável [!DNL Visual Merchandiser] *Corresponder produto por regra* A funcionalidade não filtra corretamente produtos com atualizações de preparo.
* **MDVA-40488** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema no qual os produtos configuráveis com produtos filhos indisponíveis não são mostrados no intervalo de preço correto.
* **MDVA-42507** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema no qual o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra do carrinho.
* **MDVA-39163** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corrige o problema no qual os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão do convidado.
* **MDVA-38626** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não é capaz de fazer um pedido no back-end usando o [!DNL PayPal Payflow Pro] pagamento.
* **MDVA-38666** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.3.6*) - Corrige o problema em que o usuário administrador não é capaz de alterar as opções de produto configuráveis no carrinho do cliente.
* **MDVA-38526** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o usuário administrador não consegue acessar o [!DNL Site-Wide Analysis tool].
* Correções atualizadas: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que os usuários recebem o erro 500 após definir a variável *mensagens* se já existir, mas não há novas mensagens.
* **MDVA-41139** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os produtos configuráveis ficavam fora do estoque após a importação do produto quando uma quantidade de produto simples=0 para uma de suas fontes.
* **MDVA-42326** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os clientes obtêm um erro no check-out após o tempo limite de uma sessão, mesmo se o carrinho de compras persistente estiver ativado.
* **MDVA-42341** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que a variável `categoryList` A consulta GraphQL não filtra resultados se uma solicitação tiver o cabeçalho Loja.
* **MDVA-38393** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras do catálogo param de funcionar para um produto configurável se o seu produto simples for renomeado.
* **MDVA-39153** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige a emissão em que um valor de desconto é calculado incorretamente durante o repedido no Administrador.
* Correções atualizadas: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os usuários administradores não podem acessar a grade do cliente após excluir o site.
* **MDVA-40311** (*para Adobe Commerce e Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Corrige o problema em que os usuários administradores recebem a mensagem de erro *Segurança ou chave de formulário inválida. Atualize a página* depois de fazer logon no Admin, se o caminho de Admin personalizado estiver configurado e a chave secreta estiver ativada.
* **MDVA-41631** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao tentar recuperar informações de pedido sem uma opção opcional *telefone* por meio de GraphQL.
* **MDVA-27239** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corrige o problema no qual os produtos de venda cruzada não são exibidos.
* Correções atualizadas: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige o problema com os produtos ausentes na frente durante a reindexação.
* **MDVA-40120** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que a classificação GraphQL por DESC/ASC não funciona com produtos com a mesma relevância ou preço.
* **MDVA-41399** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.2*) - Corrige o problema em que os usuários administradores não conseguem acessar o *Gerenciar carrinho de compras* se um cliente adicionar um produto à lista de desejos.
* **MDVA-40609** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que os dados de produtos desativados estão ausentes no `cataloginventory_stock_status` tabela de índice, exibindo quantidades incorretas de produtos desativados.
* **MDVA-39031** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema que fazia com que a adição de um produto ao carrinho por meio do GraphQL fosse possível mesmo se não estivesse atribuído ao site de destino.
* **MDVA-41597** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao adicionar mais de um produto configurável ao carrinho usando GraphQL.
* **MDVA-27456** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.3.7*) - Corrige o problema em que os usuários recebem um erro ao tentar carregar [!DNL Swagger].
* **MDVA-32776** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2*) - Corrige o problema em que o status do estoque não é atualizado quando um pedido é feito, mas não é enviado.
* **MDVA-30862** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.0*) - Corrige o problema com a data incorreta de pedido na fatura de PDF impressa.
* Melhoria na página de índice do [!DNL Quality Patch Tool]. Foi adicionada uma pesquisa e filtragem conveniente para [!DNL quality patches] na versão mais recente da ferramenta.
* Correções atualizadas: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema onde é impossível criar uma atualização nova ou editar uma atualização programada existente para um produto se a Data final tiver sido removida anteriormente.
* **MDVA-41046** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que produtos simples com opções personalizadas estão disponíveis para atribuição a produtos configuráveis/agrupados.
* **MDVA-40545** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que somente o primeiro nó de uma página foi recuperado, mesmo se houvesse mais de um nó para a mesma página.
* **MDVA-41164** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Corrige o problema em que um usuário administrador não é capaz de salvar ou editar uma Empresa com um atributo personalizado de cliente do tipo arquivo ou imagem.
* **MDVA-39229** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema que fazia com que o seguinte erro fosse exibido após a atualização da regra do catálogo e a hora de início da Atualização de preparo: *O Cron Job staging_synchronize_entities_period tem um erro: A atualização ativa não pode ser excluída.*
* **MDVA-40619** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as alterações na hierarquia da página do CMS causam um erro 500 ao tentar fazer a edição em linha em uma página do CMS.
* **MDVA-41061** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque é redefinido para venível quando um produto é salvo em Administrador.
* **MDVA-31763** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras de preço do catálogo são revertidas (ou não aplicadas) até a reindexação manual.
* **MDVA-37748** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que uma consulta GraphQL retorna produtos não atribuídos a um catálogo compartilhado.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema no qual faturas parciais para o mesmo pedido não podem ser criadas simultaneamente via REST API.
* **MDVA-40101** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.0*) - Corrige o problema em que os itens não são removidos do minicarrinho após um posicionamento de pedido bem-sucedido usando [!DNL PayPal Express] Check-out.
* **MDVA-40401** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o valor de uso do cupom muda mesmo se um pedido falhar.
* **MDVA-40537** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Corrige o problema em que os usuários recebem um erro ao criar uma visualização de loja se várias páginas CMS com a mesma chave de URL existirem.
* **MDVA-37725** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Corrige o problema no qual emails de pedido assíncronos enviados de sites não padrão contêm URLs de logotipo do site padrão.
* **MDVA-39482** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que um produto sai do estoque se for importado com a quantidade &quot;0&quot; quando os backorders eram ativados.
* **MDVA-40435** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema com um desconto incorreto em produtos de pacote com preços dinâmicos quando aplicado via GraphQL.
* **MC-42528** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Corrige o problema em que a variável `categoryList` A consulta GraphQL retorna as categorias atribuídas e não atribuídas.
* **MDVA-29400** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com pedidos duplicados colocados com [!DNL PayPal Express Checkout].
* **MDVA-26005** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Corrige o problema onde é impossível selecionar uma categoria em uma árvore de categoria para as condições da regra de Preço do carrinho.
* **MDVA-25631** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Melhora o desempenho para editar e salvar segmentos de clientes que contêm um grande número de clientes.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema no qual as consultas de pesquisa GraphQL não são mostradas em termos de pesquisa populares no Administrador.
* **MDVA-40601** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários recebem um erro ao tentar obter informações sobre a categoria alteradas por atualização agendada por GraphQL.
* **MDVA-37234** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que a adição de um item ao carrinho várias vezes (solicitação paralela) para o mesmo SKU cria um item de linha duplicado para a mesma ID do carrinho.
* **MDVA-33606** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários obtêm um *Violação de restrição exclusiva* ao salvar uma página CMS atribuída a uma hierarquia.
* **MDVA-31590** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que os usuários não conseguem atualizar atributos em massa usando as filas assíncronas do MySQL.
* **MDVA-36309** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que a pesquisa do produto por atributos está lenta nas grades do administrador.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que a fatura com FPT mostra um Total Geral incorreto quando o pedido é pago do crédito da loja.
* **MDVA-37364** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.3*) - Corrige o problema em que o atributo personalizado do cliente de tipo de data quebra a interface do usuário de grade do cliente.
* **MDVA-39195** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que *Adicionar ao carrinho* estava inativo na página categoria quando o redirecionamento para o carrinho estava ativado.
* **MDVA-37115** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que uma *Somente 0 restantes* o aviso é mostrado na página do produto configurável.
* **MDVA-39521** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que o usuário não é capaz de definir endereços de envio no carrinho com um número de telefone vazio via GraphQL.
* **MDVA-39384** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Corrige o problema no qual o atributo personalizado do cliente para um usuário da empresa não é salvo.
* **MDVA-39043** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.3*) - Corrige o problema em que o usuário administrador com acesso limitado recebe um erro ao tentar adicionar o *Produtos* para a página CMS.
* **MDVA-39966** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com a implantação de localidades incorretas.
* **MDVA-38852** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Corrige o problema em que o inventário de catálogo por design bloqueia tabelas para atualizações que diminuem significativamente o desempenho em casos com várias ordens paralelas.
* **MDVA-39986** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige o problema em que o usuário não é capaz de fazer um pedido no Admin no MacOS usando o navegador Safari.
* **MDVA-38447** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige dois problemas: em que *Não visível individualmente* produtos filho configuráveis são retornados na resposta GraphQL e otimizam a consulta MySQL para produtos GraphQL com filtro de categoria.
* **MDVA-40134** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que GraphQL não retorna produtos relacionados quando o Catálogo compartilhado é ativado.
* **MDVA-39935** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o GraphQL retorna produtos filhos configuráveis desativados no nível do site.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que a variável *Chame para uma função membro getId()* é exibido na página de detalhes do pedido, em Admin.
* **MDVA-34948** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com consultas de longa duração, como `GET_LOCK`.
* **MDVA-39305** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Corrige o problema em que os clientes registrados não conseguem fazer logon com o Google ReCaptcha habilitado.
* **MDVA-37897** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema com um redirecionamento incorreto quando um cliente tenta adicionar produtos com opções do widget Visualizado recentemente.

## v1.1.0 {#v1-1-0}

* As categorias de patches foram introduzidas para melhorar a experiência do usuário e facilitar a pesquisa por patches necessários para os clientes.
* O `patches.json` arquivo foi renomeado para `support-patches.json`.
* **MDVA-38799** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os produtos baixáveis não eram salvos após criar uma atualização de preparo.
* **MDVA-37592** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige o problema quando a classificação por preço não funciona corretamente para produtos com um preço zero atribuído ao catálogo compartilhado.
* **MDVA-38827** (*para Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Corrige o problema em que os clientes recebem um email de remessa de pedido contendo uma mensagem de erro.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*para Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Corrige o erro ao salvar páginas CMS: *O item com a mesma ID PAGE_ID já existe*.
* **MDVA-34680** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Corrige o problema no qual a hora de criação da conta do cliente não é filtrada corretamente na grade de clientes.
* **MDVA-37068** (*para Adobe Commerce >=2.3.1 &lt;2.4.4*) - Corrige o problema em que a taxa de imposto incorreta era exibida quando o carrinho de compras tinha apenas produtos virtuais.
* **MDVA-38608** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que tabelas temporárias não são excluídas quando a reindexação não é concluída com êxito.
* **MDVA-38308** (*para Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Corrige os problemas relacionados à adição [!DNL Vimeo] vídeos para produtos.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige o problema em que o cliente não é levado para a página Confirmação de pagamento ao usar o [!DNL Paypal Payment Advanced] método .
* **MDVA-37082** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao salvar o estoque personalizado de produtos agrupados faz com que o produto apareça fora do estoque na frente.
* **MDVA-36572** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corrige o problema quando as atualizações de Aviso de Crédito não causam mais atualizações duplicadas de reservas de produtos no banco de dados.
* **MDVA-38132** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige o problema quando o painel de Administração está inacessível devido a um erro *muitos redirecionamentos* erro.
* **MDVA-38270** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema de falta de informações do cartão Gift no total do pedido em GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*para Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Corrige o problema ao adicionar um produto configurável ao carrinho via GraphQL quando a ID do site não coincide com a ID da loja.
* **MDVA-36832** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corrige o problema em que as imagens duplicam nas páginas quando a largura da visualização é de 768px.
* **MDVA-37874** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Corrige o problema em que *Valor de desconto fixo para o carrinho inteiro* for aplicada incorretamente a um produto de pacote contendo mais de uma opção.
* **MDVA-37913** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Corrige o problema que fazia com que os links baixáveis desaparecessem se o produto baixável fosse atualizado via API.
* **MDVA-34330** (*para Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Corrige o problema em que os pedidos na grade Pedidos não são filtrados de acordo com o fuso horário de Admin.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*para Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Corrige o problema em que o Adobe Commerce lança um erro ao criar uma fatura parcial para pedidos feitos com o *Pagamento por Conta* método de pagamento por meio da REST API.
* **MDVA-37362** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corrige o problema em que os valores de opções de produto configuráveis e os valores de atributos de variante estavam vazios na resposta GraphQL.
* **MDVA-37288** (*para Adobe Commerce 2.4.2*) - Corrige o problema no qual os preços incorretos da camada eram retornados após a solicitação GraphQL.
* **MDVA-37225** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Corrige o problema em que o processo de upload está travado durante a criação rápida de pedidos quando há um valor inteiro em SKUs importadas.
* **MDVA-37224** (*para Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Corrige o problema que impedia que os clientes pagassem uma cotação negociável com [!DNL PayFlow Pro] com outro produto no carrinho.
* **MDVA-36286** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige o problema em que a visualização de widget de produtos do Page Builder é interrompida se o mesmo SKU tiver uma posição diferente nas subcategorias.
* **MDVA-30186** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Corrige o problema em que as opções de atributo são classificadas por valor de opção em vez de contagem de item de atributo na resposta GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*para Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Corrige o problema em que as opções personalizadas antigas permanecem depois de serem alteradas via API.
* **MDVA-35773** (*para Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Corrige o problema em que o Total geral não era exibido como zero na NFF para pedidos com desconto de 100%.
* **MDVA-36833** (*para Adobe Commerce 2.4.2*) - Corrige o problema onde os resultados de pesquisa mostram números aleatórios de produtos por página após excluir alguns produtos do catálogo compartilhado.
* **MDVA-37182** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Corrige o problema ao obter resultados de pesquisa incorretos em ambos [!DNL Elasticsearch] versão 6 e versão 7.
* **MDVA-36253** (*para Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que o subtotal incorreto é exibido no minicarrinho após a exclusão do item.
* **MDVA-36853** (*para Adobe Commerce 2.4.2*) - Corrige o problema de que nenhuma imagem é exibida ao carregar galerias de mídia grandes.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*para Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Corrige o problema com produtos empacotados ausentes nas páginas da categoria.
* **MDVA-36615** (*para Adobe Commerce 2.4.2*) - Corrige o problema com uma contagem de produtos incorreta na grade de produtos Admin .
* **MDVA-36464** (*para Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Corrige o problema no qual a configuração da notificação por email não está funcionando no nível de visualização da loja.
* **MDVA-36138** (*para Adobe Commerce ^2.3.2*) - Corrige o problema em que o preço de frete não é ajustado e o preço de frete total é mostrado aos clientes, se nem todos os itens no carrinho estão qualificados para a regra do carrinho de entrega gratuito.
* **MDVA-36424** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Corrige o problema em que imagens de mídia anexadas a elementos do construtor de página desaparecem quando o conteúdo é editado repetidamente se o URL de base do back-end é diferente do URL de base da loja.
* **MDVA-35984** (*para Adobe Commerce ^2.4.0*) - Corrige o problema com quantidade incorreta do produto e quantidade que pode ser vendida após a criação de várias entregas simultâneas para o mesmo produto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Isso corrige o problema em que a consulta GraphQL não está sendo armazenada em cache usando a tag de cache de categoria.
* **MDVA-33168** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema ao atualizar um atributo de produto via API, quando todos os outros atributos mudam para um valor vazio.
* **MDVA-19640** (*para Adobe Commerce >=2.3.0*) - Corrige o problema em que [!DNL Advanced Reporting] não está mostrando dados.
* **MDVA-11189** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema ao importar um arquivo CSV para atualizar o estoque de produtos, linhas do `cataloginventory_stock` são excluídas.
* **MDVA-26639** (*para Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Corrige o problema em que, se um novo modelo de email de confirmação de pedido for criado, os itens do pedido estarão ausentes no email do pedido.
* **MDVA-15546** (*para Adobe Commerce >=2.3.0*) - Corrige o problema em que, depois de criar um pedido, um *Coluna entity_id onde a cláusula é ambígua* é exibido no log de exceções.
* **MDVA-21095** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema quando um query `INSERT INTO search_tmp` não terminará após a atualização do valor do atributo de massa.
* **MDVA-23845** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema que impedia que modelos de email fossem visualizados após a minificação do JavaScript ser ativada.
* **MDVA-22026** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema no qual a importação de produtos do arquivo CSV, incluindo imagens de URLs externos, falha.
* **MDVA-22383** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema que fazia com que o salvamento de um produto demorasse muito tempo e a página fosse interrompida.
* **MC-41359** (*para Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Corrige o problema das configurações incorretas de parâmetros do cookie SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*para Adobe Commerce 2.4.1*) - Corrige o problema no qual o Page Builder aciona o seguinte erro: *Ocorreu um erro ao iniciar o Page Builder. Consulte seu contato com o suporte técnico.*
* **MDVA-35356** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema com a devolução de crédito de armazenamento incorreta após o cancelamento de pedido parcialmente faturado.
* **MDVA-33289** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige o problema em que o código JavaScript bruto é exibido na interface do usuário do endereço de cobrança durante o check-out se [!DNL Google Tag Manager] estiver ativado.
* **MDVA-35982** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os usuários administradores restritos a um site específico não podem criar uma remessa para o pedido colocado no mesmo site.
* **MDVA-35155** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que é impossível comprar um produto de pacote se o título da opção foi alterado.
* **MDVA-35910** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema em que é impossível criar uma nova conta de cliente após desativar a funcionalidade Logon como cliente .
* **MDVA-34474** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao adicionar um produto à lista de requisições usando a API.
* **MDVA-34591** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema com um cálculo incorreto de desconto de regra de carrinho para *Desconto de Quantidade Máxima é Aplicado a* e *Etapa Qtd. Desconto (Comprar X)*.
* **MDVA-33704** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige o problema em que a variável *Na retirada da loja* a opção de envio não é exibida, embora esteja sendo configurada para estar disponível.
* **MDVA-34928** (*para Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Corrige o problema em que o carregador de página é exibido indefinidamente após o crédito da loja ser removido do pagamento.
* **MDVA-35254** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige os problemas com CAPTCHA durante o check-out.
* **MDVA-35569** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que a variável *impostos fixos sobre produtos* não está sendo preenchido na resposta GraphQL quando o estado é especificado.
* **MDVA-35847** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema B2B em que o formulário Usuários da empresa é interrompido se um atributo do cliente personalizado for usado.
* **MDVA-31307** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que há *Memória insuficiente* erros em determinadas categorias devido a problemas com a lista de permissões de CSP dinâmica para blocos em cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o erro *em andamento* status da mensagem para correto *complete* mensagem para o consumidor `quoteItemCleaner` após excluir vários produtos.
* **MDVA-34102** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige a quantidade de Estoque Padrão que é zero para produtos desativados na Grade de Produto e nas páginas Editar Produto na área de Administração.
* **MDVA-35286** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que há um erro se um cliente tiver empacotado produtos no carrinho e alternar do check-out de Vários endereços para o check-out de página única.
* **MDVA-35312** (*para Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Corrige o código de resposta 500 quando uma solicitação GraphQL vazia.
* **MDVA-34189** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige o tempo limite do primeiro byte em 503 [!DNL Visual Merchandiser] consulta ao carregar a página de Categoria do administrador.
* **MDVA-34695** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correções negativas `children_count` após excluir categorias.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige o problema em que a variável *Usar valor padrão* a caixa de seleção é apagada depois que as alterações agendadas são aplicadas. O problema aparece assim que as alterações programadas não estão mais em vigor.
* **MDVA-35064** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige o problema em que as regravações de URL não são geradas para produtos configuráveis criados por meio da API.
* **MDVA-34943** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema no qual o pedido rápido armazena em cache as SKUs inseridas anteriormente.
* **MDVA-35197** (*para Adobe Commerce >=2.3.5 &lt;2.4.0*) - Corrige o problema em que há um erro ao adicionar ao carrinho usando GraphQL se os produtos adicionados anteriormente ficarem fora do estoque.
* **MDVA-34850** (*para Adobe Commerce >=2.3.1 &lt;2.4.0*) - Corrige o problema em que as opções esgotadas de um produto configurável não são exibidas em vez de serem aprovadas.
* **MDVA-34867** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema no qual os valores de um campo de condição definido para uma atualização programada não são salvos.
* **MDVA-35092** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corrige o problema em que os usuários não conseguem adicionar [!DNL Vimeo] vídeos devido a [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige o problema em que a visualização do tipo de conteúdo de Produtos do Page Builder é interrompida se os produtos correspondentes tiverem preços diferentes para cada site.
* **MDVA-32634** (*para Adobe Commerce ^2.3.1*) - Corrige o problema em que a variável `url_path` da categoria atribuída a todas as lojas permanece inalterada após mover a categoria na hierarquia.
* **MDVA-33344** (*para Adobe Commerce ^2.3.0*) - Corrige o problema em que o código fixo `rma_item` a ID do conjunto de atributos padrão da entidade é usada em vez do valor do banco de dados.
* **MDVA-34192** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige o problema onde é impossível modificar/especificar a data de nascimento do cliente usando o formato dd/mm/aaaa.
* **MDVA-34847** (*para Adobe Commerce ^2.3.0*) - Corrige a conversão do tipo de IDs de armazenamento para um número inteiro para a condição SQL nas Coleções de administração para o Usuário administrador com permissões personalizadas.
* **MDVA-34886** (*para Adobe Commerce ^2.3.2*) - Corrige o problema no qual a pesquisa não retorna resultados se *peso* o atributo do produto é configurado como pesquisável.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema de [!DNL PayPal Payflow Pro] falha no pagamento com erro de formato da lista de parâmetros de redirecionamento.
* **MDVA-34023** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema no qual o erro *Nenhuma entidade com addressId* é exibido aleatoriamente nos navegadores dos visitantes.
* **MDVA-32759** (*para Adobe Commerce >=2.3.1 &lt;2.4.3 com extensão B2B*) - Corrige o problema em que os Catálogos compartilhados estão excluindo os preços de camada existentes.
* **MDVA-33482** (*para Adobe Commerce ^2.3.5*) - Corrige o problema em que gerar um Aviso de Crédito em relação a uma NFF parcial resulta em imposto para o pedido total em vez de imposto para essa NFF parcial.
* **MDVA-33393** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o erro *O countryId fornecido não existe*.
* **MDVA-33632** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fornece uma correção onde a mensagem de exceção *Este produto está indisponível* O agora é exibido a um usuário administrador ao tentar reordenar um produto indisponível.
* **MDVA-34469** (*para Adobe Commerce >=2.4.1 &lt;2.4.2*) - Corrige o problema em que as mutações GraphQL no carrinho de um cliente falham ao usar várias visualizações de loja.
* **MDVA-33976** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*) - Corrige o problema em que o produto do pacote é exibido em Ausência de estoque na loja após remover a segunda opção do produto do pacote.
* **MDVA-33894** (*para Adobe Commerce >=2.4.0 &lt;2.4.1 com extensão B2B*) - Corrige vários problemas para a funcionalidade de Pedido Rápido, incluindo a adição e remoção de vários produtos e a sensibilidade a maiúsculas e minúsculas de SKU.
* **MDVA-27664** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema no formulário de registro do cliente, causando um erro de exibição: *ERRO - A Data de nascimento não deve ser maior do que hoje.*
* **MDVA-33970** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que há o sinal de moeda incorreto no Aviso de crédito quando o escopo do atributo de preço é definido como site.
* **MDVA-33992** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema de exibição incorreta de preços especiais B2B durante o check-out.
* **MDVA-34100** (*para Adobe Commerce >=2.3.4 &lt;2.4.2 com extensão B2B*) - Corrige o problema no qual uma conta de empresa não pode ser criada a partir da página de estrutura da empresa.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*para Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Corrige o problema com imagens duplicadas após a importação do produto de um arquivo CSV.
* **MDVA-33382** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige os problemas com a invalidação de indexadores depois que os produtos são removidos de uma categoria.
* **MDVA-28511** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige o problema onde não é possível concluir [!DNL PayPal] verifique se o campo Nome contém determinados caracteres (como letras maiúsculas acentuadas).
* **MDVA-31519** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige o problema com tempos limite de espera no check-out de convidado quando uma regra de vendas do site inteiro está em uso.
* **MDVA-33281** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema em que há um erro fatal no `inventory:reservation:list-inconsistencies` devido ao tipo de parâmetro SKU incorreto.
* **MDVA-24201** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema em que os preços não refletem a regra de preço agendada do carrinho até que sejam reindexados manualmente.
* **MDVA-32694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Corrige o problema em que um usuário administrador não pode adicionar um produto a uma cotação negociável se ele estiver relacionado a uma loja não padrão.
* **MDVA-33516** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema no qual editar um produto de pacote em uma lista de requisições leva a um erro.
* **MDVA-33975** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige vários problemas relacionados ao cálculo de preços em solicitações GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema com [!DNL PayPal] Relatórios de liquidação não disponíveis ao abrigo do **Relatórios** > **Vendas** > **[!DNL PayPal]** Liquidação conforme esperado.
* **MCP-87** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Tempo de indexação aprimorado para produtos de categoria e indexadores de estoque para perfis grandes.
* **MDVA-33106** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que as alterações de produto reagendadas são apagadas após a cron `run` é executado.
* **MDVA-19391** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema em que `analytics_collect_data` O está gerando um erro devido aos registros de descrição NULL no `catalog_category_entity_text` tabela.
* **MDVA-20376** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema com a variável *Nenhuma entidade com customerId = 1* no `exception.log` para clientes conectados após o posicionamento do pedido.
* **MDVA-23764** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige o erro em `JsFooterPlugin.php` que afeta a exibição de blocos dinâmicos.
* **MDVA-13203** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que a variável *Violação de restrição de integridade search_tmp_ table* aparece após uma reindexação completa.
* **MDVA-23426** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*) - Corrige o problema no qual os emails de notificação enviados pelo Adobe Commerce contêm um corpo em branco com o conteúdo sendo adicionado como anexo.
* **MDVA-22150** (*para Adobe Commerce >=2.3.1 &lt;2.3.4*) - Corrige o problema em que os clientes com um produto configurável no carrinho e um cupom aplicado não conseguem fazer logon se esse produto configurável estiver desativado no Administrador.
* **MDVA-32545** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que as faturas não são enviadas automaticamente ao criar pedidos com o Administrador.
* **MDVA-32714** (*para Adobe Commerce >=2.3.4 &lt;2.4.1*) - Corrige o problema no qual o preço do grupo de clientes não está funcionando na consulta de produto GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Adiciona o *Subtotal (Incl. Imposto)* opção para as condições da regra de preço.
* **MDVA-31236** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que os Administradores com acesso a recursos personalizados não conseguem configurar o 2FA ou fazer logon.
* **MDVA-30845** (*para Adobe Commerce >=2.3.5 &lt;2.3.7*) - Corrige o problema em que a variável *Não há aspas disponíveis para este pedido neste momento* é exibido ao não se conectar ao UPS XML/USPS/DHL, e nenhum outro método de envio está disponível.
* **MDVA-32133** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema que fazia com que a galeria de mídia não fosse carregada no Page Builder em determinados casos.
* **MDVA-12304** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Aumenta o número máximo de cookies de 50 para 200.
* **MDVA-32632** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige o problema em que as ordens são exibidas no sistema de pagamento, mas não no Adobe Commerce.
* **MDVA-32449** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que o histórico de pedidos é carregado muito lentamente ou não é carregado.
* **MDVA-32739** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema no qual a ativação de Notificações por email assíncronas envia emails de vendas antigos.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*para Adobe Commerce 2.3.6, 2.4.1*) - Corrige o problema em que a variável *Criar uma conta* O botão permanece desativado após a correção de dados inválidos no *Criar nova conta do cliente* formulário.
* **MDVA-31006** (*para Adobe Commerce 2.3.0, 2.3.1*) - Corrige o problema em que pedidos duplicados são exibidos após fazer um pedido usando [!DNL Paypal Express] pagamento.
* **MDVA-25602** (*para Adobe Commerce 2.3.0*) - Corrige o problema com [!DNL PayPal Payflow Pro] método de pagamento e tratamento de cookies como `SameSite=Lax` por padrão, no navegador Chrome 80 e na resposta da API, redirecione para a página de logon do cliente.

## v1.0.10 {#v1-0-10}

Correções secundárias para versões de patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema em que a Regra de preço do carrinho com cupom não se aplica via GraphQL quando *Desconto de valor fixo para o carrinho inteiro* é usada.
* **MDVA-30889** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que um erro ocorre após faturar um pacote com produtos virtuais e simples como opções.
* **MDVA-31791** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Melhora o desempenho da página do produto nos casos em que regras de direcionamento ou produtos vinculados são usados.
* **MDVA-31168** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema no qual o arquivo CSV de exportação do produto não é exibido e ocorre um erro de alocação de memória.
* **MDVA-32313** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema no qual os produtos configuráveis podiam ser adicionados à lista de desejos com as opções de configuração erradas.
* **MDVA-31759** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema que fazia com que os produtos não fossem atualizados com *lista suspensa* e *textarea* durante a importação do CSV.
* **MDVA-32012** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema que impedia a validação de códigos postais na Coreia e na Argentina.
* **MDVA-31640** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Corrige o problema no qual um preço especial não pode ser atualizado por meio da API REST.
* **MDVA-28651** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 com extensão B2B*) - Corrige o problema em que há problemas de desempenho ao carregar aspas negociáveis por meio da REST API.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*para Adobe Commerce >=2.3.0 &lt;2.4.1 com extensão B2B*) - Corrige o problema em que um sinal de moeda incorreto é exibido na grade Aviso de crédito .
* **MDVA-31295** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os pontos de recompensa não são calculados quando um pedido parcial é concluído e os itens são tributados.
* **MDVA-30112** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema se o número de pedidos exceder o valor de *tamanho de grupo* , a Adobe Commerce considera os pedidos com *pendente* status como inconsistências.
* **MDVA-31150** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os saldos do cartão-presente e do crédito da loja não são retornados pela chamada à API de Rest da fatura do GET, quando a fatura foi lançada pela chamada à API Rest e o pedido foi parcialmente pago por contas de cartão-presente e crédito da loja.
* **MDVA-30963** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema no qual os resultados da filtragem de produtos configurados para conter apenas os valores especificados para *Todas as visualizações da loja* no Admin, inclua produtos com valores substituídos no nível de exibição de loja.
* **MDVA-29954** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 com extensão B2B*) - Corrige o problema em que a variável *Nova Solicitação de Registro de Empresa* e *Você foi vinculado a uma empresa* os emails são enviados do endereço errado.
* **MDVA-28357** (*para Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Substitui o analisador padrão por um analisador personalizado por um token de palavra-chave para o campo SKU no [!DNL ElasticSearch] índice para fazer consultas de pesquisa curinga funcionarem com SKUs contendo um hífen (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o status do pedido personalizado foi alterado para *Processamento* após a criação de remessa parcial usando a WebApi.
* **MDVA-30428** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se este produto estiver atribuído a uma fonte de inventário personalizada.
* **MDVA-30594** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que um pedido com vários endereços não podia ser salvo durante o check-out quando o FPT estava configurado.
* **MDVA-29148** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema ao criar um produto por meio de uma chamada de API, o atributo personalizado do produto de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multiselect) O tipo não usará seu valor padrão se nenhum valor for fornecido na carga útil.
* **MDVA-30837** (*para Adobe Commerce >=2.3.1 &lt;2.3.5*) - Adição de uma configuração *Incluir Imposto para Quantia: Sim/Não* na configuração do método Free Shipping. When *Incluir Imposto para Quantia* está definida como *Sim*, Valor Mínimo da Ordem é calculado como Subtotal + Imposto. When *Incluir Imposto para Quantia* está definida como *Não*, Valor Mínimo da Ordem é calculado como Subtotal
* **MDVA-25028** (*para Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Corrige o problema quando os pedidos são feitos usando [!DNL PayPal Payflow Pro] não estão definidas como Status de fraude suspeita quando filtros de fraude são acionados.
* **MDVA-31224** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*) - Melhora o desempenho da `catalog_product_price` operação de reindexação para produtos do pacote.
* **MDVA-31321** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige uma página em branco (erro) ao *Mostrar tudo* está selecionada. [!DNL Elasticsearch] retorna uma lista grande de ids de produto. Nesse cenário, a cláusula order by é convertida em um formato SQL incorreto.
* **MDVA-30815** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que, ao alterar quantos resultados de pesquisa devem ser exibidos na página de resultados da pesquisa, o Adobe Commerce exibe uma página em branco. [!DNL Elasticsearch] agora exibe corretamente os resultados de páginas de categoria quando você altera o número de resultados de pesquisa exibidos por página.
* **MDVA-30782** (*para Adobe Commerce >=2.3.5 &lt;2.4.2*) - Corrige o problema no qual o Bloco dinâmico é exibido, independentemente da regra do carrinho.
* **MDVA-31021** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que há problemas de desempenho em `module-catalog-import-export/Model/Import/Product/Option.php`. Se houver mais de ~100k registros em `catalog_product_option` tabela, um novo CSV com um único produto leva menos de 10 segundos para ser validado.
* **MDVA-31007** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema no qual os atributos de endereço personalizados não são exibidos corretamente na página de detalhes do pedido, na área da minha conta e no back-end.
* **MDVA-29389** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema com os Relatórios avançados, onde a função `analytics_collect_data` cronjob diz: *A porta deve ser configurada no parâmetro de host (como localhost:3306)*.
* **MDVA-31343** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema com a classe de corpo removida `page-layout-category-full-width` quando uma categoria é agendada.
* **MDVA-30945** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que você recebe uma mensagem de erro fatal ao atualizar carrinhos `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*para Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementa o *O mínimo deve corresponder* funcionalidade e pesquisa parcial por [!DNL Elasticsearch] motor. Resolve problemas com hífens em consultas de pesquisa.
* **MDVA-30102** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corrige o problema em que o cache de Redis cresce rapidamente, pois os caches de layout não têm TTL.
* **MDVA-30599** (*para Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Corrige o problema em que as aspas de convidado criadas usando a API são marcadas incorretamente como aspas para clientes conectados.
* **MDVA-29446** (*para Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Corrige o problema no qual o preço do método de envio não aplicável é mostrado como zero durante o check-out.
* **MDVA-30357** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corrige o problema com URLs de imagem incorretas que são criadas ao gerar um mapa do site por cron.
* **MDVA-30565** (*para Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Corrige o problema em que *Nenhuma entidade com cartid = 0* é exibido para cliente convidado no check-out da loja se o carrinho de compras persistente estiver ativado.
* **MDVA-29787** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Corrige o problema em que a regra de direcionamento para produtos relacionados não funciona quando *é um de* é usada para definir produtos a serem exibidos.
* **MDVA-30977** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Corrige o problema com produtos aleatórios ausentes das categorias após a reindexação.
* **MDVA-28202** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Corrige o problema em que a Navegação em camadas não filtra corretamente os produtos configuráveis quando o MSI é usado.
* **MDVA-28300** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que a solicitação GQL não reflete as alterações de preço das regras de preço do catálogo.
* **MDVA-31006** (*para Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Corrige o problema em que pedidos duplicados são exibidos após fazer um pedido usando [!DNL Paypal Express] pagamento.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema com a navegação em camadas, onde a variável *Não* o valor para atributos de produto do tipo booleano não foi incluído na navegação em camadas se [!DNL Elasticsearch] foi usado como um mecanismo de pesquisa.
* **MDVA-28191** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema no qual nenhum método de pagamento é carregado durante a criação do pedido por meio do Administrador.
* **MDVA-29959** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 com extensão B2B*) - Corrige o problema em que o usuário administrador restrito com *Empresas* não é permitido excluir a conta da empresa.
* **MDVA-30265** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que o link de rastreamento de entrega para de funcionar após a criação da fatura.
* **MDVA-28409** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema em que a variável `sales_clean_quotes` o trabalho cron falha com *memória insuficiente* erro quando o número de aspas expiradas no banco de dados é enorme.
* **MDVA-30593** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema no qual as aspas que expiraram de acordo com a configuração Tempo de vida da cotação não são removidas.
* **MDVA-30107** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que o alternador de loja não funciona conforme o esperado se URLs base diferentes forem usados para exibições de loja.
* **MDVA-28763** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que a imagem do produto está sendo duplicada após a atualização das informações do produto usando a REST API mais de uma vez.
* **MDVA-30284** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o indexador de Pesquisa no catálogo falha devido ao seguinte *[!DNL Elasticsearch]erro: o limite do total de campos no índice foi excedido.*
* **MDVA-29042** (*para Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 com extensão B2B*) - Corrige o problema no qual as permissões do Catálogo foram alteradas para *Permitir* automaticamente após a adição de um novo produto ao catálogo compartilhado.
* **MDVA-30428** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se este produto estiver atribuído a uma fonte de inventário personalizada.
* **MDVA-28661** (*para Adobe Commerce >=2.3.0 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que um erro é lançado na seção da conta da empresa Usuários da empresa depois que o administrador da empresa é alterado.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*para Adobe Commerce 2.3.1 - 2.3.4-p2*) - Corrige o problema em que os trabalhos do cron falham se o nome do banco de dados for muito longo, resultando em categorias não atualizadas no front-end.
* **MDVA-30106** (*para Adobe Commerce ^2.3.0*) - Corrige um problema em que durante os pagamentos de check-out não são carregados com *Não é possível ler a propriedade &#39;length&#39; de null* no console JS.
* **MDVA-28656** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Corrige o problema em que, se um pedido foi feito sem nenhuma informação de pagamento necessária (por exemplo, com 100% de desconto) e uma fatura foi criada para o pedido, o status do pedido muda para *Fechado* em vez de Complete.
* **MDVA-30209** (*para Adobe Commerce 2.3.0 - 2.3.3-p1*) - Corrige o problema em que o grupo de clientes foi alterado para o padrão se o cliente atualizou suas informações de conta.
* **MDVA-30123** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que os rótulos de opções de atributo não são traduzidos corretamente para consultas GraphQL.
* **MDVA-29996** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que, depois de habilitar a permissão da categoria, a página da categoria não está sendo armazenada em cache pelo Cache de página inteira.
* **MDVA-30164** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Corrige o problema em que os registros dos clientes não podem ser exportados da grade Clientes se existirem atributos personalizados do cliente.
* **MDVA-30444** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige o problema no qual nenhum email de confirmação é enviado para pedidos feitos com GraphQL.
* **MDVA-30490** (*para Adobe Commerce 2.3.4 - 2.3.5-p2*) - Corrige o problema no qual a comparação de produtos lança a página de erro 500 se um dos produtos tiver uma descrição curta vazia.
* **MDVA-30232** (*para Adobe Commerce >=2.3.1 &lt;2.4.1*) - Corrige o problema onde não é possível reordenar se o pedido original contiver um cartão-presente.
* **MDVA-29965** (*para Adobe Commerce >=2.3.3 &lt;2.4.0*) - Corrige o problema em que os clientes recebem um erro de Chave de formulário inválida ao adicionar um produto ao carrinho.
* **MDVA-30008** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema B2B, onde não é possível colocar pedidos por meio da API de administração para um produto que está em um catálogo público.
* **MDVA-22469** (*para Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Corrige o problema no qual, após a atualização para o Adobe Commerce 2.3.3, o Page Builder não está funcionando no painel de Administração e alguns arquivos JS e CSS não estão carregando.
* **MC-35984** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema em que os comerciantes não podiam interagir com nenhum elemento de página na página Devoluções depois de criar um rótulo de envio para uma Autorização de devolução de produto (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*para Adobe Commerce 2.3.0 - 2.3.4*) - Corrige o problema com [!DNL PayPal Payflow Pro] método de pagamento e tratamento de cookies como `SameSite=Lax` por padrão, no navegador Chrome 80 e na resposta da API, redirecione para a página de logon do cliente.
* **MDVA-26694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Corrige o problema que fazia com que os caches de produtos e catálogos expirassem diariamente, embora estivesse sendo agendados para expirar de forma diferente.
* **MDVA-27825** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige o problema no qual a exportação de grandes quantidades de dados falhou devido a um vazamento de memória.
* **MDVA-29085** (*para Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Corrige o problema B2B, onde nenhum email de nova empresa é enviado se uma empresa for criada pela API.
* **MDVA-29344** (*para Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Corrige o problema em que o Page Builder fica preso após copiar o texto de um elemento de cabeçalho para um elemento de texto.
* **MDVA-29835** (*para Adobe Commerce > 2.3.1 &lt;2.4.2*) - Corrige o problema em que os pedidos de cartão-presente continham dois códigos em vez de um.
* **MDVA-30052** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema em que o conteúdo privado (armazenamento local) não era preenchido corretamente, o que resultava em problemas de desempenho.
* **MDVA-30131** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema com a navegação em camadas, onde a variável *Não* o valor para atributos de produto do tipo booleano não foi incluído na navegação em camadas se [!DNL Elasticsearch] foi usado como um mecanismo de pesquisa.
* **MDVA-35514** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema ao criar um rótulo de envio e adicionar produtos solicitados a um pacote na janela modal Criar pacotes .
