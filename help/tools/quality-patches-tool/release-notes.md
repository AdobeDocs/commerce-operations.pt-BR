---
title: Notas de versão
description: Saiba mais sobre os patches disponíveis para o Adobe Commerce e os problemas que eles resolvem.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
type: Troubleshooting
source-git-commit: a233f39557ef1cc4f27f3e4ce015de554941d676
workflow-type: tm+mt
source-wordcount: '30379'
ht-degree: 0%

---

# Notas de versão

O [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fornece patches individuais desenvolvidos pela Adobe e pela comunidade Magento Open Source. Ela permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce. Você pode aplicar patches a projetos do Adobe Commerce e do Magento Open Source, independentemente de quem os desenvolveu. Por exemplo, você pode aplicar uma correção desenvolvida pela comunidade para projetos do Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) para obter instruções sobre como aplicar patches aos seus projetos do Adobe Commerce. Consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no Guia de Atualização de Software para verificar uma lista completa de patches lançados.

>[!INFO]
>
>Para obter informações sobre [!DNL quality patches] criado pela Comunidade para o Magento Open Source, consulte as [notas de versão](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.76 {#v1-1-76}

* **ACSD-67091** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o erro de tamanho máximo do conjunto de gravação para garantir a limpeza do índice de produto da regra de catálogo implementando duas estratégias de exclusão com base no volume de dados.
* **ACSD-67370** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.9) - Corrige vários problemas em que preços incorretos eram mostrados para produtos do pacote em PDP/PLP e na página do carrinho para lojas de várias moedas.
* **ACSD-68410** (para Adobe Commerce, B2B >=1.3.3 &lt;1.5.3) - Corrige um problema em que colocar um pedido para uma cotação negociável adiciona ou mescla incorretamente linhas adicionais do carrinho à cotação. Agora os produtos são adicionados corretamente ao carrinho de compras depois de sair da última etapa da finalização da cotação negociável.
* **ACSD-69086** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que o trabalho cron falha ao limpar as tabelas de log de alterações, causando falhas no Cluster Galera ao manipular grandes quantidades de dados.
* **ACSD-69115** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige um problema em que os erros do carrinho de compras não eram exibidos para o usuário administrador ao gerenciar o carrinho de compras de um cliente atribuído a um site não padrão.
* **ACSD-69129** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7 || >=2.4.8 &lt;2.4.9) - Corrige um problema em que a exclusão do site base padrão e o uso do site secundário como padrão resultavam em um erro ao tentar atualizar o preço da camada para o site secundário por meio da API REST.
* **ACSD-69203** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige um problema em que o widget Lista de produtos retornava resultados incorretos quando várias categorias eram listadas na condição de categoria.
* **ACSD-69261** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige um problema em que um cupom de regra de preço de carrinho configurado para uso único por cliente era reutilizado várias vezes devido à manipulação incorreta do atributo `times_used` em cenários de cancelamento de fatura parcial e quantidade restante.
* **ACSD-69308** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige um problema no qual as regras de preço de catálogo não se aplicavam quando `special_price` era definido somente no nível do site (não em &quot;Todas as Exibições de Loja&quot;). Após a correção, as regras de preço do catálogo são aplicadas corretamente verificando primeiro a loja padrão do site.
* **ACSD-69319** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.9) - Corrige um problema em que os preços de pacote não eram indexados corretamente quando os produtos derivados tinham estoque em fontes personalizadas.
* **ACSD-69325** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.9) - Corrige um problema em que a modificação do caso de SKU fazia com que o produto parecesse indisponível na loja.
* **ACSD-69331** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.9) - Corrige um problema em que os criadores de conteúdo na galeria de mídia não podiam criar pastas com apenas a permissão `create_folder`. Após a correção, eles podem criar pastas conforme esperado.
* **ACSD-69333** (para Adobe Commerce >=2.4.7 &lt;2.4.9) - Corrige um problema no qual alterações de SKU eram permitidas em produtos com uma Atualização Agendada ativa. Após a correção, as alterações do SKU são proibidas durante as atualizações ativas; os salvamentos falham com um erro claro e o campo SKU do administrador é desativado. Isso evita inconsistências de inventário MSI causadas por alterações de SKU durante reversões de preparo.
* **ACSD-69541** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige um problema em que a redução da quantidade de um produto no administrador para menos do que o valor já existente em um carrinho impossibilitava a edição da quantidade de produtos nesse carrinho por meio do GraphQL.
* Versões atualizadas: **ACSD-46541**, **ACSD-53750**, **ACSD-66404**
* Patches substituídos: **ACSD-66404**, **ACSD-68499**

## v1.1.75 {#v1-1-75}

* **ACSD-68289** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige um problema em que a pesquisa de texto completo agora retorna produtos correspondentes se a condição de correspondência mínima for atendida em todos os campos pesquisáveis coletivamente, em vez de exigir que a condição seja atendida por um único campo.
* **ACSD-68359** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige um problema em que a seleção de um armazenamento durante o check-out usando o [!UICONTROL Pick in Store] não falha mais devido a URLs longas quando muitos produtos estão no carrinho. Anteriormente, isso acionava um *erro de 414* causado por URLs excessivamente longas geradas durante a seleção do armazenamento, impedindo que os clientes concluíssem o check-out.
* **ACSD-68451** (para Adobe Commerce, B2B >=1.5.2-p1 &lt;1.5.3) - Corrige um problema para vários sites em que um administrador de empresa faz logon em um site, cria uma empresa não relacionada em outro site, mas é erroneamente vinculada a essa empresa não relacionada.
* **ACSD-68490** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que o botão [!UICONTROL Add New Attribute] está visível para um usuário administrador restrito durante a criação do produto configurável.
* **ACSD-68517** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige um erro de reenvio de formulário nas páginas de Pesquisa no catálogo e no catálogo.
* **ACSD-68573** (para Adobe Commerce >=2.4.5 &lt;2.4.9) - Corrige o problema em que as permissões de categoria não eram aplicadas corretamente aos itens da lista de desejos do cliente. Após a correção, os itens da lista de desejos são exibidos e paginados corretamente na Web e no GraphQL.
* **ACSD-68615** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que a CLI de compensação de reserva de estoque mostrava uma exceção se a combinação processada tivesse uma ID de pedido ausente.
* **ACSD-68793** (para Adobe Commerce, B2B >=1.5.1 &lt;1.5.3) - Corrige um problema em que produtos válidos eram rejeitados incorretamente ao atribuí-los a um catálogo compartilhado.
* **ACSD-68925** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige um problema no qual as respostas para solicitações do GraphQL agora estão alinhadas com as especificações do GraphQL sobre HTTP. Um código de resposta 4XX é retornado quando a solicitação não pode ser analisada, não está autorizada ou encontra um problema geral. Se a solicitação for analisada e puder ser processada, um código de resposta 200 será retornado.
* Versões atualizadas: **MDVA-19640**, **ACSD-47910**, **ACSD-68040**, **ACSD-62965**
* Patches substituídos: **ACSD-62577**, **ACSD-68011**

## v1.1.74 {#v1-1-74}

* **ACSD-68636** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige um problema em que o nome do proprietário da loja não é exibido corretamente nos cabeçalhos de email de cartão-presente quando a fatura é criada de outra loja.
* **ACSD-68430** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.8) - Corrige um problema em que falha ao salvar um cliente ou endereço de cliente se o registro incluir várias opções de atributo que foram excluídas da configuração de atributo.
* **ACSD-68499** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige um problema em que a mutação `updateCartItems` do GraphQL retorna uma resposta bem-sucedida incorreta ao atualizar quantidades que excedem o estoque disponível, causando quantidades e totais inflados.
* **ACSD-68810** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige um problema no qual um pedido é atribuído a um cliente criado em um site diferente, apesar da configuração **[!UICONTROL Customer Account Sharing]**.
* Versões atualizadas: **ACSD-49737**, **ACSD-57003-V2**
* Patches substituídos: **ACSD-61969**

## v1.1.73 {#v1-1-73}

* **ACSD-67171** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige o problema em que os usuários B2B veem uma página *[!UICONTROL Access Denied]* quando a sessão expirou ou foi removida durante o check-out.
* **ACSD-67908** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que os arquivos JS não são mesclados corretamente em configurações de vários armazenamentos.
* **ACSD-68190** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Corrige o problema em que os descontos não se aplicam, os descontos aplicados não são exibidos corretamente na resposta de exibição do carrinho do GraphQL e os descontos que não são de cupom são removidos ao remover um desconto de cupom.
* **ACSD-68206** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.9) - Corrige o erro ao usar o servidor de Aplicativos GraphQL com o recurso **[!UICONTROL Rate Limiting]** com a extensão [!DNL PHP Redis] instalada.
* **ACSD-68356** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que uma consulta de carrinho do GraphQL retornava um valor de desconto incorreto para cotações virtuais.
* **ACSD-68391** (para Adobe Commerce >=2.4.6-p10 &lt;2.4.9) - Corrige o problema em que as permissões relacionadas à categoria não eram aplicadas corretamente em **[!UICONTROL Quick Order]** e **[!UICONTROL Requisition Lists]**.
* **ACSD-68400** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a quantidade de cartão-presente virtual não era refletida com precisão na tabela de reserva de estoque.

## v1.1.72 {#v1-1-72}

* **ACSD-68040** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que o desempenho da página de pesquisa de front-end é degradado em [!DNL MariaDB] 10.6 e 11.4 com muitas solicitações de pesquisa históricas.
* **ACSD-67941** (para Adobe Commerce e Magento Open Source >=2.4.7-p1 &lt;2.4.8) - Corrige o problema em que solicitações GraphQL com nomes de filtro desconhecidos causam logs de exceção PHP.
* **ACSD-68064** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que a criação de atualizações agendadas resulta em entradas duplicadas em ambientes com um alto número de categorias aninhadas.
* **ACSD-66807** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que a tabela `report_viewed_product_index` mostra uma contagem incorreta de exibições de página de produtos.
* **ACSD-67383** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o uso de **[!UICONTROL Login as Customer]** com duas contas de administrador de empresa na mesma sessão causa um erro *Nenhuma dessas entidades com cartId*.
* **ACSD-67518** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que os relatórios avançados geram linhas de cabeçalho duplicadas quando a contagem de linhas excede o tamanho do lote.
* **ACSD-67639** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que a criação de um memorando de crédito falha para produtos de pacote com o **[!UICONTROL Dynamic Price]** definido como *Não*.
* **ACSD-67696** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que `media_gallery` entradas não retornam no nó de produto do Cart GraphQL após uma liberação de cache.
* **ACSD-67946** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.9) - Corrige o problema em que as atualizações do carrinho mostram banners de erro duplicados.
* **ACSD-68011** (para Adobe Commerce, B2B >=1.5.1 &lt;1.5.3) - Corrige o problema em que SKUs inexistentes podem ser atribuídas a um catálogo compartilhado por meio da API `/V1/sharedCatalog/:id/assignProducts` [!DNL REST].
* **ACSD-68118** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.9) - Corrige o problema em que a consulta do GraphQL `customerCart` retorna valores de atributo de produto que não refletem o cabeçalho da loja, causando localização inconsistente.
* **ACSD-68092** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que as opções de pacote de produtos são perdidas após vários salvamentos, devido à sincronização inadequada entre as atualizações agendadas e os dados de produto base.
* **ACSD-67424** (para Adobe Commerce, B2B >=1.5.0 &lt;1.5.3) - Corrige o problema em que o valor `updated_at` na resposta da API `GET /carts/search` [!DNL REST] não corresponde ao valor mostrado em **[!UICONTROL Admin panel]** ao usar Aspas Negociáveis.
* **ACSD-67187** (para Adobe Commerce, B2B >=1.5.1 &lt;1.5.3) - Corrige o problema em que os usuários administradores restritos a sites não padrão veem o erro, *Crie pelo menos um catálogo compartilhado público para continuar* e não possa acessar o botão **[!UICONTROL Add New Company]** na grade Empresa.
* Versões atualizadas: **ACSD-49737**, **ACSD-53750**, **ACSD-51819**, **ACSD-55566**, **ACSD-62965**, **ACSD-63323**, **ACSD-63406**, **ACSD-66139**, **ACSD-66404**, **ACSD-67659**, **ACSD-66301**
* Patches substituídos: **ACSD-62577**, **ACSD-63325**, **ACSD-67102**

## v1.1.71 {#v1-1-71}

* **ACSD-60624** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o **[!UICONTROL Upload Image]** não funciona para conteúdo vazio nas seções [!UICONTROL Image], [!UICONTROL Banner] e [!UICONTROL Slider] do Page Builder.
* **ACSD-67089** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema de paginação na API `inventory/export-stock-salable-qty`, que limita incorretamente `total_count` ao tamanho da página.
* **ACSD-67093** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que a recuperação de pedidos por meio do GraphQL usando o filtro de intervalo de datas retorna resultados incorretos.
* **ACSD-67459** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.9) - Corrige o problema em que produtos com descrições com mais de 65.536 caracteres não podem ser importados.
* **ACSD-67603** (para Adobe Commerce >=2.4.6 &lt;2.4.8) - Corrige o problema em que a geração de mapa de site para produtos com inclusão de imagem habilitada experimenta tempos de processamento longos.
* **ACSD-67643** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que entradas duplicadas são criadas durante atualizações agendadas em ambientes com um alto número de categorias aninhadas.
* **ACSD-67652** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que o status do produto agrupado é retornado como indisponível em chamadas do GraphQL, mesmo com produtos filho e pai em estoque.
* **ACSD-67904** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que os pedidos não podem ser feitos se o nome da cidade contiver dígitos (0-9), E comercial (&amp;), ponto (.) ou parênteses ().
* Patches substituídos: **ACSD-61322**, **ACSD-65848**

## v1.1.70 {#v1-1-70}

* **AC-15210** (para Adobe Commerce e Magento Open Source >=2.4.6-p3 &lt;2.4.9) - Migra a integração de USPS das APIs de Ferramentas da Web desatualizadas para as novas APIs RESTful USPS.
* **ACSD-67102** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que o back-end do Adobe Commerce carrega **[!UICONTROL Categories]** muito lentamente.
* **ACSD-66120** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que [!DNL GraphQL] exibe incorretamente porcentagens de desconto e preços base quando os preços de catálogo estão configurados para incluir imposto.
* **ACSD-66157** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.9) - Corrige o problema em que o preço especial não entra em vigor para sites criados em fusos horários diferentes.
* **ACSD-67659** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige um problema no qual as mensagens de erro traduzidas retornam um código de erro INDEFINIDO.
* **ACSD-67166** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que a consulta `cataloginventory_stock_status` é executada várias vezes ao carregar uma cotação na loja, causando chamadas redundantes de banco de dados.
* **ACSD-67289** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que o preço normal não é exibido quando um preço especial é aplicado.
* **ACSD-67686** (para Adobe Commerce e Magento Open Source >=2.4.4-p15 &lt;2.4.5 || >=2,4,5-p14 &lt;2,4,6 || >=2.4.6-p12 &lt;2.4.7) - Corrige o problema em que ocorre um erro `Syntax Error: Unexpected <EOF>` ao enviar uma solicitação [!DNL GraphQL] vazia.
* **ACSD-67250** (para Adobe Commerce >=2.4.7-p4 &lt;2.4.8) - Corrige o problema em que a operação de salvamento **[!UICONTROL Shared Catalog]** atualiza todos os itens em vez de apenas os afetados, melhorando o desempenho com a eliminação de operações desnecessárias.
* **ACSD-67030** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige o problema em que produtos simples não são atribuídos de um produto configurável quando editados por um administrador de função limitada.
* Versões atualizadas: **ACSD-54095**, **ACSD-51636**, **ACSD-51739**, **ACSD-66093**
* Patches substituídos: **ACSD-62415**

## v1.1.69 {#v1-1-69}

* **AC-15223** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige um problema na versão 2.4.8 da loja em que, após alternar as lojas, a página é distribuída do cache e não reflete o armazenamento selecionado.
* **ACP2E-3731** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que as exportações de produtos com visibilidade **[!UICONTROL Catalog, Search]** incluem incorretamente registros de outras exibições de loja em ambientes de várias lojas.
* **ACP2E-3767** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que a última opção de pacote em um produto de pacote não pode ser removida.
* **ACP2E-3964** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrigido o problema em que produtos derivados de produtos configuráveis não podiam ser listados por meio da API REST quando um vídeo era definido na galeria.
* **ACP2E-3977** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige o problema em que o campo **[!UICONTROL Cap Reward Points Balance At]** não pode estar vazio quando [!UICONTROL Rewards Points Balance Redemption Threshold] está definido, causando um erro de validação.
* **ACP2E-4050** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.8) - Corrige o problema em que as regras de preço do carrinho não são aplicadas corretamente a produtos de vários envios quando o produto agrupado é usado e as condições de subseleção são usadas com o frete gratuito habilitado.
* **ACSD-56226** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que as consultas READ no nó subordinado retornam dados desatualizados quando o sinalizador `synchronous_replication` está habilitado.
* **ACSD-57477** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o processamento de regras de vendas causa desempenho lento em solicitações relacionadas ao carrinho.
* **ACSD-58108** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.8) - Corrige o problema em que o nome da tabela de ligação ausente na tabela de busca original causava erros com o SQL de extensão de módulo personalizado na grade de ordem.
* **ACSD-65983** (para Adobe Commerce >=2.4.6-p10 &lt;2.4.9) - Corrige o problema em que a reconfiguração de uma cotação de produto agrupada no back-end de Administração gera um erro.
* **ACSD-66149** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o manipulador IPN retorna um erro *500* para tipos IPN desconhecidos ou sem suporte.
* **ACSD-66153** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que uma página retorna um erro *500* devido a uma estrutura de layout incorreta sendo armazenada em cache.
* **ACSD-66302** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que os itens da lista de desejos são filtrados incorretamente pela ID do armazenamento em vez de serem filtrados pelo site.
* **ACSD-66311** (para Adobe Commerce >=2.4.6-p9 &lt;2.4.9) - Corrige o problema em que a grade Empresas carrega lentamente para usuários administradores com acesso restrito a sites.
* **ACSD-66404** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que o trabalho cron falha ao limpar as tabelas de log de alterações, causando [!DNL Galera Cluster] falhas ao manipular grandes quantidades de dados.
* **ACSD-66952** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige o problema em que o cache é limpo em cada visita de PLP ou carrinho, causando sobrecarga de desempenho quando uma regra de destino é definida.
* **ACSD-67264** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os layouts de página de produto agrupados e baixáveis são inconsistentes entre os dispositivos.
* **ACSD-67347** (para Adobe Commerce e Magento Open Source >=2.4.5-p11 &lt;2.4.6) - Corrige o problema em que o pedido falha com *Não é possível adquirir um erro de bloqueio* quando são usados cupons com caracteres especiais e o bloqueio de arquivos está habilitado.
* Patches substituídos: **ACP2E-3841**

## v1.1.68 {#v1-1-68}

* **ACSD-58131** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a presença de uma imagem de 0 byte na galeria de mídia impedia que todas as imagens do diretório fossem exibidas ou selecionadas.
* **ACSD-62415** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema quando o back-end do Adobe Commerce carrega categorias muito lentamente.
* **ACSD-66082** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.9) - Corrige o problema em que não era possível atualizar a imagem de amostra de um produto por meio da importação do produto.
* **ACSD-66179** (para Adobe Commerce e Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.9) - Corrige o problema em que cancelar uma NFF criada com o tipo de pagamento &quot;Não Capturar&quot; resultava em uma página de erro 404.
* **ACSD-66865** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que salvar regras de preço de catálogo invalidava indexadores e fornece uma alternativa para reindexar somente os produtos afetados.
* **ACSD-66963** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que a mutação `estimateTotals` retornava nulo para descontos quando um código de desconto era aplicado a um carrinho contendo produtos virtuais.
* **ACSD-67039** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os registros do cliente não foram salvos devido à validação do atributo do sistema `rp_token` e a validação de diacríticos agora é aplicada somente ao email do cliente resultante.
* **ACSD-62146** (para Adobe Commerce >=2.4.7 &lt;2.4.8) - Corrige o problema em que o endereço de cobrança selecionado desaparece na página de pagamento de check-out quando a pesquisa de endereço está habilitada e o &quot;Limite de Número de Endereços de Cliente&quot; está definido como 1.
* **ACSD-65938** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige o problema no qual emails de cartão-presente eram enviados mesmo quando a criação da fatura falhava.
* **ACSD-66072** (para Adobe Commerce >=2.4.6 &lt;2.4.9) - Corrige o problema em que os produtos relacionados não eram retornados via GraphQL na Página de Detalhes do Produto devido a um erro interno do servidor quando &quot;Regras de Produto Relacionadas&quot; eram configuradas.
* **ACSD-66233** (para Adobe Commerce >=2.4.8 &lt;2.4.9) - Corrige o problema em que os usuários administradores não conseguiam adicionar produtos a uma categoria devido à falha no carregamento do pop-up Adicionar produto.
* **ACSD-66889** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige a linha de código obsoleta com estrutura adequada para garantir a conclusão com êxito do processo indexador de inventário.
* **ACSD-66965** (para Adobe Commerce B2B >=1.5.0 &lt;1.5.3) - Corrige o problema com a Opção de Impressão da Página de Lista de Requisições que causou um erro.
* **ACSD-66506** (para Adobe Commerce B2B >=1.5.0 &lt;1.5.3) - Corrige o erro de back-end que ocorria quando produtos anteriormente atribuídos de um Catálogo Compartilhado eram excluídos e novos produtos eram atribuídos.
* **ACSD-66417** (para Braintree 4.6.1) - Corrige um problema em que a grade da ordem de venda emite um erro ao tentar filtrar pedidos por data.
* Versões atualizadas: **ACSD-60590**, **ACP2E-3705**
* Patches substituídos: **ACSD-57003**, **ACSD-66434**

## v1.1.67 {#v1-1-67}

* **ACSD-65935** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a consulta do GraphQL `customerOrders` retornava um erro interno do servidor quando um produto era excluído.
* **ACSD-66049** (para Adobe Commerce e Magento Open Source >=2.4.5-p3 &lt;2.4.6 || >=2.4.7 &lt;2.4.9) - Corrige o problema em que as vitrines que não estão em inglês exibem preços incorretos devido à versão da biblioteca ICU.
* **ACSD-66084** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.9) - Corrige o problema em que `row_total_incl_tax` é retornado como um valor residual quase zero na resposta da API do pedido em vez de 0,00 para itens totalmente descontados.
* **ACSD-66118** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que a atualização do código de exibição de repositório limpa as configurações [!UICONTROL Design Configuration] se o cache de configuração não for atualizado.
* **ACSD-66139** (para Adobe Commerce >=2.4.7 &lt;2.4.8) - Corrige o problema em que as chamadas GraphQL para fazer um pedido de um carrinho inexistente ou inativo retornavam um código de erro *INDEFINIDO*.
* **ACSD-66301** (para Adobe Commerce e Magento Open Source >=2.4.6-p9 &lt;2.4.7 || >=2.4.7-p4 &lt;2.4.8) - Corrige o problema em que mover os produtos de um pedido de volta para o carrinho no Administrador resulta em incompatibilidade de quantidade.
* **ACSD-66434** (para Adobe Commerce >=2.4.6-p8 &lt;2.4.9) - Corrige o problema em que a ID do cliente estava ausente das consultas da GraphQL da empresa.
* **ACSD-66441** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.8) - Corrige o problema em que a loja exibe dados de índice incorretos em navegação em camadas ao indexar produtos configuráveis para uma configuração de várias lojas.
* **AC-14984** (para Adobe Commerce e Magento Open Source >=2.4.6-p10 &lt;2.4.7 || >=2.4.8 &lt;2.4.9) - Corrige o erro *Tipo de quadro inválido 21* na conexão RabbitMQ SSL.
* **AC-14985** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que os emails não são enviados ao usar o servidor `smtp` externo com TLS habilitado.
* Versões atualizadas: **MDVA-12304**, **ACSD-47920**, **ACSD-56447**, **ACSD-61845**, **ACSD-64118**

## v1.1.66 {#v1-1-66}

* **ACP2E-3789** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.9) - Corrige o problema em que atualiza um produto por meio de [!DNL WebAPI] arquivos de mídia duplicados quando uma ID de mídia é fornecida.
* **ACP2E-3918** (para Adobe Commerce >=2.4.5 &lt;2.4.9) - Corrige o problema em que o check-out falhava para clientes da empresa que fizeram logon usando a coleta na loja sem um endereço de cobrança padrão.
* **ACSD-65750** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.9) - Corrige o problema em que a consulta do GraphQL `route` retornava produtos fora de ordem nos tipos de conteúdo Produtos do Page Builder.
* **ACSD-65775** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que os detalhes do pedido de API [!DNL REST] retornavam valores `base_row_total` e `row_total` incorretos quando várias quantidades do mesmo item eram solicitadas.
* **ACSD-65777** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que o campo `types` estava ausente para tipos de imagem de produto na solicitação do GraphQL `MediaGallery`.
* **ACSD-65848** (para Adobe Commerce e Magento Open Source >=2.4.8 &lt;2.4.9) - Corrige o problema em que a contagem total de produtos em uma categoria era calculada usando uma subseleção, refatorando o método para usar uma associação.
* **ACSD-65913** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.9) - Corrige o problema em que [!DNL OpenSearch] gerou um erro *invalid_argument_exception* para categorias com produtos com o mesmo preço.
* **ACSD-66041** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que os códigos postais da Irlanda (IE) não eram pesquisáveis para locais de retirada devido a um `CountryID` ausente.
* **ACSD-66212** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.9) - Corrige o problema em que a importação de um arquivo CSV do cliente causou falhas na segunda tentativa e nas subsequentes.
* Versões atualizadas: **MDVA-12304**, **MDVA-19640**, **ACP2E-3841**, **ACSD-65100**, **ACSD-65787**, **ACP2E-3753**, **ACSD-65202**, **ACSD-65331**, **ACSD-65822**

## v1.1.65 {#v1-1-65}

* **ACP2E-3753** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os emails de alerta do produto em uma configuração de várias lojas sempre eram enviados usando o tema padrão, independentemente da configuração de loja ou tema.
* **ACSD-64118** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que solicitações simultâneas para salvar e atualizar o mesmo produto resultam em inconsistência de dados ou produtos duplicados.
* **ACSD-64813** (para Adobe Commerce >=2.4.4 &lt;2.4.9) - Corrige o problema em que o cancelamento da atribuição de categorias de um catálogo compartilhado [!DNL B2B] via API [!DNL REST] demora muito ou atinge um tempo limite com catálogos grandes.
* **ACSD-65202** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a página &quot;Minha Conta&quot; não exibe pedidos recentes de outras exibições de loja na mesma loja.
* **ACSD-65254** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema no qual as notificações por email não eram enviadas aos clientes após a atualização dos endereços de email em suas contas usando a mutação `updateCustomerEmail` [!DNL GraphQL].
* **ACSD-65331** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o armazenamento selecionado em [!UICONTROL Pick in Store] era limpo após navegar repetidamente de volta para a página de check-out.
* **ACSD-65822** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que as quantidades de produtos agrupadas e configuráveis não são exibidas corretamente no painel do carrinho de compras em [!UICONTROL Customer's Activities].
* **ACSD-66093** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que endereços de email podiam ser inseridos nos campos [!UICONTROL First Name] e [!UICONTROL Last Name] do cliente convidado, resultando em emails de confirmação de pedido inválidos.
* Versões atualizadas: **ACSD-51291**
* Patches substituídos: **ACSD-61522**

## v1.1.64 {#v1-1-64}

* **ACP2E-3838** (para Adobe Commerce e Magento Open Source >=2.4.4-p9 &lt;2.4.4-p13 || >=2.4.5-p8 &lt;2.4.5-p12 || >=2.4.6-p6 &lt;2.4.6-p10 || >=2.4.7 &lt;2.4.7-p5) - Corrige o problema em que os erros do CORS [!DNL Page Builder] impedem que as alterações sejam salvas no painel de Administração no modo de produção.
* **ACP2E-3841** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.8) - Corrige o problema em que as regras de preço do carrinho para produtos de remessa múltipla não se aplicam corretamente quando as condições de subseleção são usadas e a remessa gratuita é habilitada.
* **ACSD-63139** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que a exportação de produtos falha quando os atributos do produto contêm milhares de valores de opção.
* **ACSD-65100** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a remoção dos valores de [!UICONTROL Maximum Width] e [!UICONTROL Maximum Height] na configuração [!UICONTROL Media Gallery Image Optimization] causa um erro durante o processo de otimização da imagem.
* **ACSD-65127** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a habilitação da minificação do JavaScript no modo de produção faz com que o [!DNL TinyMCE] 6 gere erros no console do navegador, afetando a funcionalidade e a experiência do usuário.
* **ACSD-65787** (para Adobe Commerce e Magento Open Source >=2.4.7-p5 &lt;2.4.8) - Corrige o problema em que a classe SchemaBuilder falha durante a criação ou as atualizações do esquema devido a uma &#39;coluna&#39; de chave de matriz indefinida ao processar dados da tabela.
* **ACSD-65223** (para Adobe Commerce, B2B 1.5.1) - Corrige o problema em que os termos e contratos selecionados manualmente para [!DNL B2B] ordens de compra resultam em um erro.
* **ACSD-65540** (para Adobe Commerce, B2B 1.5.2) - Corrige o problema em que ocorre um erro de sintaxe SQL devido à ausência da função `REGEXP_LIKE` ao atualizar a tabela `company_structure`.
* **ACSD-65684** (para Adobe Commerce, B2B 1.5.2) - Corrige o problema de desempenho em que a atualização do módulo `Magento_Company` após a atualização para o [!DNL B2B] 1.5.2 demorava muito para processar um grande número de registros (~100.000+) na tabela `company_structure`.
* Versões atualizadas: **ACSD-48234**, **ACSD-51819**, **ACSD-57570**, **ACSD-56415**

## v1.1.63 {#v1-1-63}

* **ACSD-64627** (para Adobe Commerce >=2.4.6-p8 &lt;2.4.8) - Corrige o problema em que os atributos personalizados do cliente não podem ser salvos ao adicionar ou editar usuários na Estrutura da empresa.
* **ACSD-64753** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o armazenamento pré-selecionado na &quot;Coleta no Repositório&quot; não é atualizado quando o endereço de entrega é alterado, mesmo que esteja fora do raio do armazenamento.
* **ACSD-65195** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a mutação do GraphQL `createCompany` lança um erro para um país sem uma região necessária.
* **LYNX-839** (para Adobe Commerce 2.4.8) - Remoção da exposição de informações de grupos de clientes, segmentos e regras promocionais por meio do GraphQL.
* Versões atualizadas: **MDVA-12304**, **ACSD-48234**, **ACSD-58054**

## v1.1.62 {#v1-1-62}

* **ACSD-63406** (para Adobe Commerce e Magento Open Source >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Corrige o problema em que as aspas persistentes expiradas não são apagadas por nenhum trabalho cron quando o trabalho `persistent_clear_expired` cron é executado.
* **ACSD-63520** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que imagens adicionadas por meio do **[!UICONTROL Configurations]** no painel de administração não aderem ao limite de tamanho máximo do upload.
* **ACSD-64523** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que era possível criar novos produtos sem um nome por meio do processo de importação (admin ou API), o que danificaria a interface do administrador e resultaria em produtos inválidos.
* **ACSD-64532** (para Adobe Commerce e Magento Open Source >=2.4.6-p2 &lt;2.4.8) - Corrige o problema em que uma variável ENV definida como &quot;false&quot; é tratada como uma cadeia de caracteres &quot;false&quot; em vez de um booleano false.
* **ACSD-64592** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que o link de declaração do email para um cartão-presente em lojas não padrão sempre redirecionava a declaração do cartão-presente para o site padrão.
* **ACSD-65164** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.8) - Corrige o problema em que a mensagem de erro *Algumas das opções de item selecionadas não estão disponíveis no momento* ocorre ao reordenar um produto configurável com uma única opção personalizada de caixa de seleção selecionada.
* **ACSD-64732** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que controladores de terceiros não eram armazenados em cache corretamente com segmentos de clientes.

## v1.1.61 {#v1-1-61}

* **ACP2E-3689** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige vários problemas com a exibição da árvore de categoria em níveis mais profundos e refletindo relações de âncora/não âncora.
* **ACP2E-3705** (para Adobe Commerce >=2.4.7 &lt;2.4.8) - Corrige um problema em que a execução do cron `indexer_update_all_views` falha ao definir `MAGE_INDEXER_THREADS_COUNT`.
* **ACSD-63883** (para Adobe Commerce >=2.4.4 &lt;2.4.7-p4) - Corrige o problema em que a Lista de Requisições retorna um `items_count` incorreto na resposta do GraphQL.
* **ACSD-63974** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a página de lista Requisição leva muito tempo para carregar quando há muitos itens, adicionando um recurso de paginação à grade da lista Requisição na Loja, que exibe somente partes de registros limitadas ao número de registros por página, em vez de todos os registros de uma só vez.
* **ACSD-64178** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que a página de edição do Conjunto de atributos carrega lentamente se houver milhares de atributos de produto.
* **ACSD-64209** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que o agendador cron recupera todas as cotações negociáveis sem excluir aquelas com o status **[!UICONTROL ordered]**, fazendo com que um email ou emails sejam acionados.
* **ACSD-64431** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - A mutação `placeOrder` que contém as informações de código do cupom na solicitação não lança mais um erro interno, mas mostra que o pedido foi feito com êxito.
* **ACSD-64467** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que o editor do WYSIWYG aparece vazio após salvar uma descrição de categoria no nível de exibição da loja.
* **ACSD-64546** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que uma mensagem de erro genérica ocorre na interface do usuário e uma exceção *Array para conversão de cadeia de caracteres* é armazenada nos logs durante a criação do rótulo de remessa UPS, garantindo que o erro real seja exibido na interface do usuário e que a mensagem de erro correta seja armazenada nos logs.
* **ACSD-64684** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que ocorre um erro de validação ao editar e salvar um cartão-presente com um valor maior que *999* devido à vírgula (separador de milhares) no número *mil (1.000)*.
* Versões atualizadas: **ACSD-49392**, **ACSD-50368**, **ACSD-51819**, **ACSD-54966-V2**, **ACSD-57003**, **ACSD-62979**, **ACSD-64112**
* Patches substituídos: **ACSD-49392**, **ACSD-58739**, **ACSD-62689**, **ACSD-64112**
* Patches obsoletos: **ACSD-46192**, **ACSD-52133**

## v1.1.60 {#v1-1-60}

* **ACSD-63323** (para Adobe Commerce >=2.4.7 &lt;2.4.8) - Corrige o problema em que a opção **[!UICONTROL Select All]** não funciona ao adicionar produtos a uma categoria. Além disso, garante que a paginação e o rótulo de contagem de registros funcionem corretamente ao adicionar produtos a uma categoria por meio da grade pop-up.
* **ACSD-63992** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige um problema em que uma regra de preço de carrinho com um cupom e uma condição baseada em um método de envio não pode ser aplicada corretamente por meio da interface do Administrador.
* **ACSD-64111** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que ocorre um erro ao definir condições aninhadas para um componente de Produto no [!DNL Page Builder].
* **ACSD-64137** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a pesquisa de locais de retirada por código postal não funciona corretamente na localização holandesa.
* **ACSD-64149** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que um segmento de cliente com uma condição de intervalo de datas pode ser salvo quando apenas uma das datas é editada.
* Versões atualizadas: **MDVA-12304**, **ACSD-45049**, **MDVA-43824**, **ACSD-46192**, **ACSD-50368**, **ACSD-52133**, **ACSD-47657**, **ACSD-51819**, **ACSD-54966-V2**, **ACSD-55628**, **ACSD-45049**, **ACSD-63242**

## v1.1.59 {#v1-1-59}

* **ACSD-63454** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que o valor padrão de atributos suspensos e de seleção múltipla não é salvo corretamente no banco de dados.
* **ACSD-63574** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que a adição de uma Lista de produtos do pacote a um bloco por meio do Page Builder resultava em um erro.
* **ACSD-63793** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.8) - Corrige o problema quando os processos de Importação interferem entre si em diferentes guias do navegador.
* **ACSD-64113** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.8) - Corrige o problema que causava erros no administrador ao carregar imagens com uma largura relativamente pequena em comparação à sua altura (ou vice-versa) por meio da galeria de mídia.
* **ACSD-64212** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.8) - Corrige o problema em que um pedido não está associado a uma conta de cliente quando a conta é criada via GraphQL após o pedido ser feito.
* **ACSD-63469** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que os descontos de valor fixo para todo o carrinho não eram aplicados corretamente quando mais de uma regra era aplicada.
* **ACSD-63870** (para Adobe Commerce >=2.4.4 &lt;2.4.4-p11) - Corrige o problema em que um cliente da empresa não era desconectado corretamente quando o status da empresa é alterado durante a sessão ativa do cliente.
* **ACSD-64112** (para Adobe Commerce >=2.4.5 &lt;2.4.8) - Corrige um problema em que a execução do cron `indexer_update_all_views` falha ao definir `MAGE_INDEXER_THREADS_COUNT`.
* Versões atualizadas: **ACSD-61622**
* Patches substituídos: **ACSD-61553**
* Patches obsoletos: **ACSD-61199**

## v1.1.58 {#v1-1-58}

* **ACSD-48570** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a página de redefinição de senha não podia ser acessada clicando no link [!UICONTROL Admin] de redefinição de senha quando **Adicionar Código de Armazenamento a URLs** estava *habilitado*, o que anteriormente resultava na exibição de uma página de logon ou 404.
* **ACSD-62118** (para Adobe Commerce >=2.4.6 &lt;2.4.8) - Corrige o problema em que a tabela `sales_order_tax_item` não é totalmente atualizada quando [!DNL B2B] pedidos são feitos usando o método de Ordem de Compra.
* **ACSD-63067** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que todas as quantidades de produtos são realçadas incorretamente e a mensagem *[!DNL Please specify the quantity of product(s).]* é exibida para todos os produtos em um produto agrupado quando apenas uma quantidade está incorreta.
* **ACSD-63090** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os itens do carrinho de compras são removidos quando um produto é excluído depois de ser adicionado ao carrinho.
* **ACSD-63182** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que ocorre um erro ao salvar um produto de pacote duplicado com o **[!DNL MSI]** *habilitado*.
* **ACSD-63283** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a solicitação de itens do registro de presentes causa uma exceção e em que as atualizações do registro de presentes incluem itens que não pertencem ao registro.
* **ACSD-63299** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o preço especial de um produto configurável não é exibido na loja.
* **ACSD-63325** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que um erro `Syntax Error: Unexpected <EOF>` ocorre ao enviar uma solicitação [!DNL GraphQL] vazia.
* **ACSD-63329** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os valores padrão para atributos com tipos de entrada **[!UICONTROL Date]** ou **[!UICONTROL Date and Time]** não são definidos ao criar produtos por meio do [!DNL REST API].
* **ACSD-63572** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.8) - Corrige o problema em que as tabelas temporárias do indexador `CatalogRule` não são limpas se o processo do indexador for encerrado.
* **ACSD-63578** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que clicar no botão **[!UICONTROL Delete]** em **[!UICONTROL Add to Order by SKU]** no [!UICONTROL Admin] não remove o [!DNL SKU].
* Versões atualizadas: **MDVA-39305-V3**
* Patches substituídos: **ACSD-56280**
* Patches obsoletos: **ACSD-62872**

## v1.1.57 {#v1-1-57}

* **ACSD-57570** (para Adobe Commerce >=2.4.4 &lt;2.4.4-p10) - Corrige o problema em que um usuário administrador restrito com acesso a uma determinada loja nem sempre consegue ver todos os catálogos compartilhados aos quais os produtos estão atribuídos, nem os clientes que não podem ser salvos, resultando em inconsistências no sistema.
* **ACSD-58325** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que o botão **[!UICONTROL Import]** está disponível mesmo após um erro de validação.
* **ACSD-59083** (para Adobe Commerce >=2.4.4 &lt;2.5.0) - Corrige o problema em que algumas operações de atualização do banco de dados resultam em um erro de *Tabela base ou exibição não encontrada* se a atualização [!DNL mview] estiver em execução ao mesmo tempo.
* **ACSD-61622** (para Adobe Commerce e Magento Open Source >=2.4.6-p1 &lt;2.4.7) - Corrige o problema em que as taxas específicas de conta de [!DNL FedEx] estão ausentes na resposta.
* **ACSD-61895** (para Adobe Commerce >=2.4.4 &lt;2.5.0) - Corrige o problema em que a consulta de categorias [!DNL GraphQL] retorna categorias com a permissão **permitir**, mesmo que a categoria raiz não tenha a permissão **permitir**.
* **ACSD-62212** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.5.0) - Corrige o problema em que o conteúdo de email **Esqueceu a senha** não é traduzido para o idioma do modo de exibição de loja.
* **ACSD-62481** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.5.0) - Corrige o problema em que o carrinho de compras do cliente fica vazio mesmo se **[!UICONTROL Persistence]** estiver habilitado.
* **ACSD-62629** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.5.0) - Corrige o problema em que uma lista de produtos usada em **[!UICONTROL Widgets]** não reflete a condição de categoria.
* **ACSD-62635** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.5.0) - Corrige o problema em que os produtos relacionados a várias lojas não são exibidos corretamente na consulta de produto do [!DNL GraphQL].
* **ACSD-62671** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.5.0) - Corrige o problema em que a solicitação [!DNL GraphQL] não retorna informações de endereço atualizadas na primeira tentativa.
* **ACSD-62689** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.5.0) - Corrige o problema em que o cliente não consegue adicionar Categorias em **[!UICONTROL Related Product Rules and Widgets]** após *profundidade 4*.
* **ACSD-62708** (para Adobe Commerce e Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6-p2 || >=2.4.6-p8 &lt;2.4.7-p1) - Corrige o problema em que o tamanho da fonte do editor do [!DNL TinyMCE] 7 no administrador mostra *PT* e não *PX*. Você também pode definir o tamanho da fonte em *PX* em vez de *PT*.
* **ACSD-62758** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.5.0) - Corrige o problema em que os vídeos de produtos não são renderizados corretamente na página de detalhes do **[!UICONTROL Configurable Product]** se o [!DNL URL] contiver opções selecionadas.
* **ACSD-62951** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.5.0) - Corrige o problema em que o email de Aviso de Crédito é enviado sem incluir itens e totais.
* **ACSD-62965** (para Adobe Commerce >=2.4.7 &lt;2.5.0) - Corrige o problema em que uma mensagem `LocalizedException` não é incluída na resposta [!DNL GraphQL] de posicionamento de pedido.
* **ACSD-63286** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que os produtos atribuídos a um catálogo compartilhado via [!DNL API] não aparecem na loja até que uma reindexação manual seja executada.
* **ACSD-63326** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.5.0) - Corrige o problema em que [!UICONTROL Admin] é redirecionado para uma página interrompida após fazer um pedido no back-end.
* Versões atualizadas: **ACSD-51739**
* Patches substituídos: **MDVA-43451**, **ACSD-62755**

## v1.1.56 {#v1-1-56}

* **ACSD-63244** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que um erro [!DNL JavaScript] impede que o [!DNL Google Maps] seja renderizado corretamente. Corrige o problema em que há muitos *TypeError não detectados: isso._each não é uma função* erros no console no painel [!UICONTROL Admin].
* **ACSD-63242** (para Adobe Commerce e Magento Open Source >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Corrige o problema de lentidão de importação ao adicionar produtos de catálogo com mais de 10.000 entradas.
* **ACSD-63062** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que cálculos incorretos de desconto do carrinho ocorrem quando várias regras de sobreposição são aplicadas.
* **ACSD-62979** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que o uso do [!UICONTROL Store ID] incorreto no cabeçalho [!DNL GraphQL] causa um erro fatal de memória.
* **ACSD-62971** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a importação de fontes de estoque com valores não numéricos na coluna **quantidade** resulta na **quantidade** sendo definida como *0*.
* **ACSD-62872** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema de validação de atributo exclusivo em que as atualizações de agendamento são validadas incorretamente.
* **ACSD-62755** (para Adobe Commerce e Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Corrige o problema em que o [!DNL TinyMCE] 7 requer que o tamanho e a fonte da fonte sejam adicionados especificamente às configurações de inicialização do editor.
* **ACSD-62670** (para Adobe Commerce e Magento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2,4,5-p10 &lt;2,4,6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Corrige o problema em que o relatório [!UICONTROL Products Ordered] é exportado para [!DNL CSV] e [!DNL XML] retorna um erro.
* **ACSD-62577** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema de desempenho lento de consultas de pesquisa de vitrine otimizando os índices de consulta e de tabela.
* **ACSD-62475** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que os produtos [!UICONTROL Gift Card] são mesclados incorretamente no carrinho.
* **ACSD-62428** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que `is_out_of_stock` está definido como um valor incorreto no índice de pesquisa de catálogo quando [!DNL SKU] não está definido como um atributo pesquisável.
* **ACSD-62355** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.8) - Melhora o tempo de carregamento da página de edição do produto configurável quando o produto configurável se baseia em muitos atributos com muitos valores.
* **ACSD-61805** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os produtos permanecem sem estoque na loja após a atualização do status do backorder por meio do [!DNL REST API].
* **ACSD-60811** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que a atualização do status do pedido com um valor ou comentário personalizado só é possível se o status atual for *processando* ou *fraude*.
* **ACSD-62952** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a data [!UICONTROL Gift Registry] é exibida de forma imprecisa na loja.
* **ACSD-55339** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que um produto [!DNL SKU] que começa com &quot;0&quot; (zero) remove o &quot;0&quot;, impedindo que a cotação seja atualizada.
**
* Patches atualizados: **ACSD-59514**
* Versões atualizadas: **ACSD-60816**
* Patches substituídos: **ACSD-59967**

## v1.1.55 {#v1-1-55}

* **ACSD-58383** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que a emissão de um reembolso via [!DNL REST API] com duas solicitações idênticas executadas simultaneamente cria avisos de crédito duplicados.
* **ACSD-58471** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que o conteúdo dinâmico não é carregado na página de detalhes do produto quando as regras de preço de catálogo associadas foram agendadas.
* **ACSD-58566** (para Adobe Commerce >=2.4.6 &lt;2.4.8) - Corrige o problema em que [!DNL GraphQL] retorna um erro de servidor interno ao consultar o campo `created_at` na mutação `addPurchaseOrderComment`.
* **ACSD-58685** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os emails de vendas iniciados enquanto a comunicação por email estava desabilitada ainda eram enviados depois que a comunicação por email fosse habilitada novamente.
* **ACSD-58735** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que um administrador restrito não conseguia visualizar os carrinhos de compras abandonados na página da conta do cliente no [!UICONTROL Admin] para um site associado.
* **ACSD-58828** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.8) - Corrige o problema em que a mensagem de validação do lado do servidor *endereço é obrigatório* é exibida se qualquer campo obrigatório estiver vazio, junto com a mensagem de validação do lado do cliente. A validação do lado do servidor não exibirá a mensagem para campos obrigatórios vazios, e a validação do lado do cliente lidará com a notificação de erro, informando: *Este campo é obrigatório.*
* **ACSD-60344** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema no qual emails de confirmação de pedido duplicados são enviados ao usar um **[!UICONTROL Purchase Order]** com aprovação automática.
* **ACSD-61348** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os itens da lista de desejos ficam visíveis via [!DNL GraphQL], mas não na loja quando estão em um ambiente com vários sites.
* **ACSD-61534** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que a configuração de design não podia ser definida usando o comando `bin/magento config:set` e os valores bloqueados podiam ser alterados por meio da manipulação de formulários. Agora, os valores bloqueados definidos de [!DNL CLI] com `--lock-env` ou `--lock-conf` não podem ser atualizados.
* **ACSD-61785** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a atualização do atributo `reward_warning_notification` não era possível por meio da mutação [!DNL GraphQL] e das chamadas [!DNL REST API], alinhando seu comportamento com `reward_update_notification`.
* **ACSD-62591** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrigindo o problema em que o tema não é alternado corretamente quando o **[!UICONTROL User Agent Rules]** é configurado.
* **ACSD-62793** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que os atributos `datetime` nos dados exportados não incluem o componente de tempo. Além disso, se **[!UICONTROL Fields Enclosure]** estiver *habilitado*, os valores de atributo na coluna `additional_attributes` serão colocados entre aspas duplas.
* **ACSD-62332** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema no qual a consulta da lista de produtos [!DNL GraphQL] estava limitada a um `total_count` de 10.000 produtos. Corrige o problema em que [!DNL Live Search] define a página atual como *1* em vez da página *2* nos critérios de pesquisa quando consultado via [!DNL GraphQL].
* Versões atualizadas: **ACSD-46581**, **ACSD-49513**, **ACSD-52801**, **ACSD-59514**
* Patches substituídos: **ACSD-52801**, **ACSD-55100**
* Patches obsoletos: **ACSD-52085**, **ACSD-57854**

## v1.1.54 {#v1-1-54}

* **AC-13283** (para Adobe Commerce e Magento Open Source 2.4.6-p8) - Reverte alterações incompatíveis com versões anteriores de Inserir Pedido incluídas em 2.4.6-p8.
* **ACSD-60267** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o Imposto Fixo de Produto (FPT) se aplica corretamente ao adicionar produtos simples com FPT diretamente ao carrinho, mas falha ao selecionar esses produtos por meio de opções de produto configuráveis.
* **ACSD-61103** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que a contagem de falhas na tabela `customer_entity` não é redefinida para zero depois que um cliente faz logon por meio de pontos de extremidade de API.
* **ACSD-61134** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que o método de pagamento [!DNL Braintree Vault] é automaticamente desmarcado no fluxo de trabalho de check-out quando um comprador atualiza seu endereço de cobrança ao desmarcar a caixa de seleção *[!UICONTROL My billing and shipping address are the same]*.
* **ACSD-61199** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a guia de hierarquia de páginas do CMS não exibe uma estrutura de árvore adequada ao editar uma página do CMS com uma hierarquia existente.
* **ACSD-61200** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que os cálculos de *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]* em vendas estão sem o *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]*, causando discrepâncias nos dados da ordem de venda.
* **ACSD-61522** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que é possível inserir endereços de email nos campos *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* do cliente convidado e enviar emails de confirmação de pedido inválidos.
* **ACSD-61756** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Melhora o desempenho de `AdvancedSalesRule` filtros.
* **ACSD-61799** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que o desconto total é calculado incorretamente quando várias regras de carrinho com descontos fixos são aplicadas à cotação.
* **ACSD-61845** (para Adobe Commerce e Magento Open Source >=2.4.7-p1 &lt;2.4.8) - Corrige o erro que ocorre quando uma solicitação é enviada com apenas *text/html* para aceitar o cabeçalho.
* **ACSD-62056** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que o carregamento de imagens para um produto configurável falha se o MSI estiver instalado.
* **ACSD-62485** (para Adobe Commerce >=2.4.4 &lt;2.4.6-p8 || >=2.4.7 &lt;2.4.8) - Corrige o problema em que o consumidor `async.operations.all` para de funcionar quando uma empresa é criada.
* Versões atualizadas: **ACSD-48661**, **ACSD-55100**, **ACSD-61553**
* Patches obsoletos: **ACSD-51846**

## v1.1.53 {#v1-1-53}

* **ACSD-48318** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que o aninhamento de emulação de ambiente não é permitido. Agora, a emulação é iniciada durante a chamada `send()` assim que a emulação é interrompida durante a chamada `getInfoBlockHtml()`.
* **ACSD-59930** (para Adobe Commerce >=2.4.6 &lt;2.4.8) - Melhora o desempenho dos fluxos **[!UICONTROL Create]**, **[!UICONTROL Save]** e **[!UICONTROL Delete]** da empresa.
* **ACSD-60584** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que um token de acesso criado para o usuário em um site tem permissão para acessar ou alterar informações do cliente em outros sites.
* **ACSD-60804** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que a edição de um cliente vinculado a uma empresa excluída causa o erro *Chamada para uma função membro `getSuperUserId()` em null*.
* **ACSD-61133** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.8) - Corrige o problema em que o `sales_clean_quotes` [!DNL cron] exclui cotações de ordens de compra não aprovadas.
* **ACSD-61528** (para Adobe Commerce >=2.4.6 &lt;2.4.8) - Corrige o problema em que a recuperação de funções de [!UICONTROL Admin] usando [!DNL GraphQL] não retorna resultados.
* **ACSD-61553** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que os descontos de **[!UICONTROL Cart Price Rule]** são calculados incorretamente quando vários descontos com prioridades diferentes e **[!UICONTROL Maximum Qty Discount is Applied To]** são aplicados ao produto.
* **ACSD-61667** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Melhora o desempenho do inventário ao criar entregas no caso de muitas fontes com coleta na loja.
* **ACSD-61969** (para Adobe Commerce >=2.4.7 &lt;2.4.8) - Corrige o problema em que o usuário precisa digitar um código de cupom que diferencie maiúsculas e minúsculas para corresponder exatamente como o código de cupom foi configurado.
* Versões atualizadas: **ACSD-54989**, **ACSD-60632**

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** (para Adobe Commerce e Magento Open Source) - Adiciona todos os campos necessários para atender aos requisitos de carta de ordem 3DS VISA ao usar [!DNL Braintree] como um gateway de pagamento.
* **ACSD-59366** (para Adobe Commerce >=2.4.6 &lt;2.4.8) - Corrige o problema em que ocorre um erro ao tentar excluir uma equipe que contém usuários desativados que não estão visíveis na lista de equipes.
* **ACSD-59865** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que um [!UICONTROL Cart Price Rule] não cancela as regras aplicadas anteriormente se a quantidade do produto no carrinho não for suficiente para que as regras sejam aplicadas.
* **ACSD-59925** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema com a classificação de itens no [!UICONTROL Media Gallery] por posição no GraphQL.
* **ACSD-59952** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que ocorre um erro ao criar um [!UICONTROL Shared Catalog] com uma ID de grupo atribuída a um [!UICONTROL Shared Catalog] existente.
* **ACSD-60590** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Melhora o desempenho da geração de [!UICONTROL Bestsellers Aggregated Daily Reports] para um grande volume de pedidos feitos.
* **ACSD-60673** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que o [!UICONTROL Cart Price Rule] para vários métodos de pagamento no check-out não se aplica adequadamente ao método de pagamento específico.
* **ACSD-60684** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que a classificação de produto do GraphQL por vários campos não funciona conforme esperado.
* **ACSD-60788** (para Adobe Commerce >=2.4.7 &lt;2.4.8) - Corrige o problema em que scripts personalizados para [!DNL Google Tag Manager] não são executados devido a erros de Política de Segurança de Conteúdo (CSP).
* **ACSD-61322** (para Adobe Commerce >=2.4.6 &lt;2.4.8) - Corrige o problema em que [!UICONTROL Products/Categories] não atribuído ao [!UICONTROL Shared Catalog] para o Padrão (Grupo Geral) ainda estão incluídos no Mapa do Site XML.
* **ACSD-61366** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que o comando `setup:static-content:deploy --jobs 4` é executado com vários trabalhos com falha com o erro *A porta deve ser configurada no parâmetro de host* quando a porta é especificada para a conexão de BD.
* Patches atualizados: ACSD-51857, ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.8) - Corrige o problema em que o GraphQL retorna um erro interno do servidor ao tentar obter uma ID de cotação para uma cotação expirada.
* **ACSD-60234** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que um valor incorreto é exibido em [!DNL PayPal] quando o desconto é aplicado pelo método de pagamento.
* **ACSD-59967** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7-p2) - Corrige o problema em que um erro de JavaScript impede que o [!DNL Google Maps] seja renderizado corretamente.
* **ACSD-60326** (para Adobe Commerce >=2.4.4 &lt;2.4.8) - Corrige o problema em que ocorre um erro na consulta do GraphQL para o status de retorno do cliente.
* **ACSD-60538** (para Adobe Commerce >=2.4.7 &lt;2.4.8) - Corrige o problema em que, se um produto estiver desabilitado no *[!UICONTROL All Store Views]* e habilitado somente em escopos de exibição de loja específicos, os atributos do produto não serão exibidos corretamente na resposta do GraphQL, fazendo com que o produto não seja exibido corretamente.
* **ACSD-60631** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que o GraphQL retorna um erro quando o mesmo produto simples é atribuído a vários produtos configuráveis.
* **ACSD-60632** (para Adobe Commerce e Magento Open Source >=2.4.5-p8 &lt;2.4.8) - Corrige o problema em que um novo endereço é salvo sempre que uma tentativa de posicionamento de pedido é feita, independentemente do pedido ser criado com êxito ou não.
* **ACSD-60816** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que os scripts [!DNL New Relic Browser Monitoring] inseridos pelo agente APM não são compatíveis com a CSP (Política de Segurança de Conteúdo), impedindo sua execução.
* **ACSD-61195** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que nenhum item do carrinho é retornado na última página da solicitação do GraphQL do carrinho.
* Patches atualizados: ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o erro *Chamada para método indefinido RefletionUnionType::getName()* que ocorre ao instalar as versões 2.4.4-pX.
* **ACSD-45049** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6) - Corrige o problema em que a configuração de atributo *[!UICONTROL Is required]* de um cliente não funciona corretamente de acordo com o escopo do site no Administrador.
* **ACSD-46938** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema no desempenho da recriação de gatilhos de BD durante `setup:upgrade`.
* **ACSD-48210** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a atualização de um atributo *[!UICONTROL Website Scope]* em uma exibição de repositório específica substitui os valores de atributo no escopo global.
* **ACSD-54887** (para Adobe Commerce e Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2,4,5-p3 &lt;2,4,5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Corrige o problema em que o carrinho de compras do cliente é limpo após a expiração da sessão do cliente com o [!UICONTROL Persistent Shopping Cart] ativado.
* **ACSD-58141** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige o problema em que PHPSESSID é regenerado em solicitações POST na área de vitrine de um cliente conectado se o [!DNL L2 Redis cache] estiver habilitado e o cliente for atualizado do Administrador.
* **ACSD-58352** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Corrige o problema em que os rótulos de atributo de retorno para a exibição de repositório padrão são retornados por meio da API do GraphQL quando uma exibição de repositório não padrão é especificada no cabeçalho da solicitação.
* **ACSD-58442** (para Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - Corrige o problema em que dispositivos com uma largura de 768px são tratados como móveis, fazendo com que o menu e o cabeçalho sejam carregados em uma exibição móvel em vez de na área de trabalho.
* **ACSD-58790** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corrige a funcionalidade de pinçar para zoom nas imagens da página de detalhes do produto na exibição móvel no [!DNL Chrome].
* **ACSD-59036** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige uma exceção que ocorre ao carregar preços de produtos com limites inferiores e superiores iguais a $0.
* **ACSD-59229** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que as informações relacionadas ao grupo de clientes são salvas no segmento errado devido ao valor antigo do X-Magento-Vary na solicitação.
* **ACSD-59378** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que substituições de URL no nível do repositório são atualizadas incorretamente durante a importação.
* **ACSD-59514** (para Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - Corrige o problema em que os formulários na área de Administração com [!DNL Page Builder] exibem o erro *[!DNL Page Builder]que foi renderizado por 5 segundos sem liberar bloqueios.* no console do navegador após o envio do formulário, e as alterações não podem ser salvas.
* **ACSD-60303** (para Adobe Commerce >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Corrige o problema em que um pedido do administrador não pode ser feito se a minificação do HTML estiver ativada.
* **ACSD-60441** (para Adobe Commerce e Magento Open Source 2.4.4-p9 || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Corrige o problema com a atualização de clientes por meio do ponto de extremidade `V1/customers` [!DNL REST API] ao usar o token de acesso de integração gerado do back-end.
* Patches atualizados: ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que as imagens do produto são removidas após a exclusão de uma atualização de preparo.
* **ACSD-57086** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que os pedidos feitos em sites não padrão com termos e condições habilitados não são processados corretamente.
* **ACSD-57588** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o envio de um pedido para vários endereços dispara um erro durante o processamento da ID da região.
* **ACSD-57643** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que os produtos com opções personalizadas são adicionados incorretamente ao carrinho de compras por meio do GraphQL.
* **ACSD-57846** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a pesquisa de produtos da GraphQL com um filtro de preço zero não retorna resultados devido a uma exceção.
* **ACSD-57941** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que as opções do produto são atribuídas incorretamente à loja do administrador em vez de suas respectivas lojas.
* **ACSD-58375** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a configuração incorreta do *[!DNL YouTube API Key]* causa um erro ao adicionar um vídeo [!DNL YouTube] no nível de exibição da loja.
* **ACSD-58739** (para Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corrige o problema em que a reindexação parcial gera um erro.
* **ACSD-58446** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que, ao excluir uma equipe com usuários ou equipes filhos independentemente de seu status (inativo), o sistema fornece uma mensagem de erro não informativa não consistente com a interface.
* **ACSD-58054** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige o problema em que é possível gerar tokens de cliente para clientes inativos via API.
* **ACSD-58163** (para Adobe Commerce >=2.4.3 &lt;2.4.7) - Corrige o problema em que um *[!UICONTROL Cart Price Rule]* não aplica um desconto a um cliente convidado do carrinho *[!UICONTROL Customer Segment]* correspondente sem um código de cupom.
* **ACSD-57045** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que regravações de URL causam looping de página infinito depois que *[!UICONTROL Website Root]* é desmarcado de *[!UICONTROL Hierarchy]*.
* Patches atualizados: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a mutação `mergeCart` falha com um &quot;*Erro Interno do Servidor*&quot; na resposta [!DNL GraphQL] ao mesclar carrinhos de origem e de destino que têm os mesmos itens do pacote.
* **ACSD-56546** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que os produtos configuráveis e agrupados são exibidos como **Fora de Estoque** na loja quando a **exibição fora da configuração do produto** é *Desabilitada*.
* **ACSD-56635** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que o cliente importado é duplicado com o mesmo endereço de email quando uma importação é usada com **compartilhamento de conta** definido como *Global*.
* **ACSD-56741** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige a mensagem de erro &quot;*Tentando acessar o deslocamento da matriz no valor do tipo nulo*&quot; que é exibida durante `setup:upgrade` quando o banco de dados contém um gatilho [!DNL MySQL] personalizado não relacionado ao mecanismo de indexação e [!DNL MView].
* **ACSD-57315** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema quando uma nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão [!UICONTROL Fetch] é clicado na tela **[!UICONTROL View transaction]** no Administrador.
* **ACSD-57337** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige o problema em que um usuário administrador com restrições de acesso a sites específicos pode ver empresas de todos os sites na grade **[!UICONTROL Companies]**.
* **ACSD-57394** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema de classificação de produto incorreta por campos de classificação múltipla em [!DNL GraphQL].
* **ACSD-57565** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o painel **[!UICONTROL Order]** exibe informações de pedido incorretas até que o período seja atualizado. O painel agora exibe as estatísticas de ordem corretas na primeira carga.
* **ACSD-57854** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema quando as solicitações do produto [!DNL GraphQL] retornavam categorias desabilitadas nas agregações de categorias.
* **ACSD-58008** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que a atualização de uma atualização agendada removia a versão anterior de um item preparado, se nenhuma data final fosse especificada.
* Patches atualizados: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que os atributos *[!UICONTROL Used]* e *[!UICONTROL Times Used]* exibem valores incorretos para cupons gerados quando usados durante o check-out com vários endereços.
* **ACSD-56760** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que um usuário administrador restrito a um site específico não pode classificar ou adicionar novos produtos dentro de uma categoria, caso o repositório Web tenha sua própria categoria raiz.
* **ACSD-56858** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que as permissões da função de empresa B2B são exibidas incorretamente para um administrador de empresa restrita.
* **ACSD-57074** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o atributo personalizado *Sim/Não* com `attrbute_code` começando com `price_` não funciona corretamente com a indexação e os produtos com esses atributos não estão disponíveis no front-end.
* Patches atualizados: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que os caches da página de categoria são invalidados quando a quantidade em estoque é alterada, mesmo que o produto ainda esteja em estoque.
* **ACSD-54656** (para Adobe Commerce >=2.4.5 &lt;2.4.6) - Corrige o problema em que o Recaptcha invisível falha durante o check-out, impedindo que um pedido seja feito.
* **ACSD-55100** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que o GraphQL não retorna mais de 10.000 produtos nos resultados da pesquisa.
* **ACSD-56621** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que o nome e o sobrenome atualizados não são refletidos na seção de cabeçalho de saudações do usuário administrador da empresa.
* **ACSD-56842** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que os proxies adiados e as fábricas de proxy adiadas estão ausentes após a execução de `setup:di:compile`.
* **ACSD-57003** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o status do pedido é alterado para *[!UICONTROL Complete]* em vez de ser alterado para *[!UICONTROL Processing]* quando um pedido é parcialmente reembolsado e parcialmente enviado.
* Patches atualizados: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que um produto configurável fica indisponível quando um de dois produtos secundários é desabilitado por uma atualização agendada.
* **ACSD-56616** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que os produtos agrupados são exibidos como em estoque na loja quando os produtos simples estão indisponíveis.
* **ACSD-56515** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que o administrador com permissões no nível do site não pode adicionar ou editar um bloco dinâmico.
* **ACSD-56447** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a adição do mesmo produto ao carrinho por meio de solicitações paralelas de API da Web REST resulta em dois itens separados no carrinho.
* **ACSD-56415** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que o desempenho da indexação de preço parcial é retardado devido a uma consulta `DELETE` quando o banco de dados tem muitos dados de preço parciais a serem indexados.
* **ACSD-54965** (para Adobe Commerce >=2.4.5 &lt;2.4.6) - Corrige o problema em que a grade do Visual Merchandising não exibe o estoque correto quando um produto é atribuído somente ao estoque personalizado.
* **ACSD-52824** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que os botões PayPal Express, Google Pay e Apple Pay são exibidos para clientes da empresa quando esses métodos de pagamento estão desabilitados nas configurações da empresa.
* Patches atualizados: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que um usuário é redirecionado para o Painel de Administração ao classificar produtos de categoria usando a opção **Mover do Estoque para o fim** e o erro `Invalid security or form key. Please refresh the page` aparece na parte superior da tela.
* **ACSD-56280** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Corrige o problema em que a solicitação de itens de um Registro de presente leva a uma exceção.
* **ACSD-56246** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que os dados são removidos do atributo de seleção múltipla personalizado quando uma atualização agendada para um produto se torna ativa.
* **ACSD-56193** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Corrige o problema em que o cache Verniz/Fastly não é atualizado quando um bloco agendado é usado na descrição da categoria usando o Page Builder.
* **ACSD-56158** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que a consulta de &quot;carrinho&quot; retorna o valor de imposto total para cada regra de imposto.
* **ACSD-56023** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o conteúdo do widget não é atualizado na página do CMS quando o cache está habilitado.
* **ACSD-55427** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que o usuário administrador não pode desatribuir um produto de um catálogo compartilhado da página de produto no Administrador.
* **ACSD-55352** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que, após criar um memorando de crédito parcial com pontos de premiação do cliente, o status do pedido muda para Fechado, e as opções de memorando de crédito desaparecem da página Pedido de administrador.
* **ACSD-55231** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que não é possível adicionar produtos a um carrinho usando a funcionalidade de pedido rápido.
* **ACSD-54283** (para Adobe Commerce >=2.4.3 &lt;2.4.4) - Corrige o problema em que os Produtos/Categorias não atribuídos ao Catálogo Compartilhado para o Padrão (Grupo Geral) ainda estão incluídos no Mapa de Site XML.
* Patches atualizados: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a URL de categoria canônica não é atualizada após a alteração da URL da categoria.
* **ACSD-53636** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5) - Corrige o problema em que o preço normal não é exibido nas páginas de listagem de produtos para produtos configuráveis que têm produtos filho com preços especiais.
* **ACSD-54885** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema no check-out de vários endereços quando o usuário administrador está usando a funcionalidade *Fazer logon como Cliente*.
* **ACSD-55610** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que um pedido parcialmente cancelado tem um valor de desconto incorreto.
* **ACSD-55334** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige as traduções de rótulos por meio de dicionários de Tradução na resposta do GraphQL.
* **ACSD-54739** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que a condição de status de estoque do produto não é aplicada às regras de produto relacionadas.
* **ACSD-53925** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o administrador não pode salvar o bloco CMS com o carrossel do produto quando o modo de dimensões `catalog_product_price` está definido como *site*.
* **ACSD-52714** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o filtro de data não está funcionando na grade do administrador quando o formato de data está definido como *Y-m-d*.
* **ACSD-55055** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Melhora o desempenho do carregamento de atributos de produto nas regras de preço do carrinho no carrinho de compras.
* **ACSD-53790** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que vários RMAs para um único produto podem ser criados por meio da API REST.
* **ACSD-56090** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Corrige o problema em que a solicitação do GraphQL responde com os dados de todos os armazenamentos em vez dos dados de armazenamento solicitados especificamente.
* **ACSD-54983** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que não é possível obter o UID do usuário da empresa com a solicitação GraphQL quando o status do usuário está definido como *[!UICONTROL Inactive]*.
* **ACSD-53309** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o imposto não é totalmente aplicado no rótulo *[!UICONTROL Regular Price]* quando a opção personalizável é selecionada.
* **ACSD-55305** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Corrige o problema em que o pop-up *[!UICONTROL Edit Company User]* da página **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** congela com um carregador na tela.
* Patches atualizados: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que os dados do produto *[!UICONTROL Recently Viewed]* não são atualizados corretamente na exibição da loja.
* **ACSD-54626** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que não é possível criar uma nova regra de ordem de compra (`createPurchaseOrderApprovalRule`) com o atributo `NUMBER_OF_SKUS` via [!DNL GraphQL].
* **ACSD-53845** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema de tempo limite de conexão [!DNL MySQL] quando `consumer max_messages` = 0.
* **ACSD-54890** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que `aggregate_sales_report_bestsellers_data` causa erros [!DNL MySQL] devido à falta de espaço no disco `/tmp`.
* **ACSD-55112** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que o botão *[!UICONTROL Submit review]* pode ser clicado várias vezes sem a validação de [!DNL Google reCAPTCHA v3].
* **ACSD-54264** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Corrige o problema em que a mensagem de erro *&quot;Você não pode atualizar o atributo solicitado. A ID da linha: store_id&quot;* aparece quando um cliente tenta fazer check-out com uma cotação negociável de outra exibição de loja.
* **ACSD-54418** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que uma quantidade fixa de desconto é aplicada incorretamente a cada produto filho do pacote com preço dinâmico.
* **ACSD-55238** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Correções que salvam o produto vazio *[!UICONTROL Meta Description]*.
* **ACSD-54966** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que um código de cupom com uso limitado por cliente não pode ser reutilizado se o pedido anterior falhar.
* **ACSD-54060** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um administrador restrito não pode salvar um produto se for filho de outro produto atribuído a um escopo diferente.
* **ACSD-48910** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrigido o problema em que um produto de pacote atribuído a várias origens fica indisponível depois que um pedido é faturado e enviado, mesmo que ainda tenha uma quantidade diferente de zero.
* **ACSD-55381** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige um erro interno de servidor ao consultar campos `configurable_product_option_uid` e `configurable_product_option_value_uid` de um [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (para Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - Corrige o upload de um arquivo no formulário de registro da empresa e substitui um arquivo para um atributo do cliente na loja.
* Patches atualizados: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema que ocorre no carrinho de compras quando um produto é removido do catálogo compartilhado depois de já ter sido adicionado ao carrinho.
* **ACSD-53722** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Corrige o problema em que o preço das opções de produto agrupadas muda para $0 quando atualizações agendadas para escopos diferentes se tornam ativas.
* **ACSD-53643** (para Adobe Commerce >=2.4.3 &lt;2.4.7) - Corrige o problema em que o pedido tem um total incorreto ao fazer um pedido de compra com produtos desabilitados ou esgotados. Isso é corrigido ocultando o botão *[!UICONTROL Place Order]* para essas ordens de compra.
* **ACSD-54067** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um vídeo de produto não é reproduzido em um dispositivo móvel.
* **ACSD-55414** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Melhora o desempenho quando o MariaDB tenta converter a entity_id EAV de uma cadeia de caracteres em um inteiro.
* **ACSD-51819** (para Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Corrige o problema em que vários pedidos podem ser feitos com a mesma ID de cotação.
* **ACSD-53118** (para Adobe Commerce >=2.4.0 &lt;2.4.7) - Corrige o problema em que *[!UICONTROL Cart Price Rule]* é aplicado usando o código de cupom enquanto o produto tem um atributo vazio, o que deveria ter invalidado a regra.
* **ACSD-54324** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que a solicitação requisition_lists do GraphQL não considera configurações de paginação e retorna todos os resultados.
* Patches atualizados: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (para Adobe Commerce >=2.4.0 &lt;2.4.6) - Corrige o problema em que não é possível processar uma Cotação B2B enviada para um produto com Várias Fontes Atribuídas.
* **ACSD-54040** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Corrige o problema em que o campo *[!UICONTROL Created]* está em branco para exibir detalhes quando os módulos B2B estão habilitados.
* **ACSD-54319** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema no qual o preço do produto mostra zero no relatório *[!UICONTROL Product in Cart]*.
* **ACSD-53378** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Melhora o tempo de carregamento da página de check-out para clientes com catálogos de endereços grandes.
* **ACSD-52657** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que o minicart não é atualizado na loja secundária, que usa um subdomínio.
* **ACSD-53414** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que um usuário administrador restrito pode ver páginas do CMS fora do escopo de suas permissões.
* **ACSD-54472** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que os clientes de uma empresa rejeitada ainda podem realizar a autenticação e os clientes de uma empresa bloqueada e rejeitada ainda podem fazer pedidos. O patch adiciona validação adicional para endpoints do GraphQL.
* **ACSD-52801** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Adiciona a opção de fazer uma correspondência parcial ao pesquisar produtos no GraphQL.
* **ACSD-55004** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que o validador falha ao carregar um arquivo de importação maior do que o valor configurado em `php.ini`.
* **ACSD-54989** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Corrige o problema em que um administrador de empresa não pode fazer um pedido quando *[!UICONTROL Enable Purchase Orders]* está definido como *[!UICONTROL Yes]* e *[!UICONTROL Purchase Order]* está definido como *[!UICONTROL No]*.
* **ACSD-54007** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o erro *&quot;Chave de matriz indefinida &quot;_scope&quot;* sobre a importação de dados do cliente.
* **ACSD-55031** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o erro *Tipo &quot;misto&quot; não pode ser anulável* durante a compilação.
* **ACSD-54961** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um usuário administrador restrito não pode atualizar o status de *Análise do Produto* em massa.
* **ACSD-55256** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que somente a primeira imagem é exibida com êxito no controle deslizante de imagem.
* Patches atualizados: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (para Adobe Commerce >=2.4.0 &lt;2.4.7) - Corrige o problema em que o histórico de saldo de pontos de recompensa é calculado incorretamente após a expiração dos pontos de recompensa.
* **ACSD-53583** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Melhora o desempenho da reindexação parcial de *Produtos de Categoria* e *Categorias de Produto* indexadores.
* **ACSD-54026** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige uma mensagem de erro incorreta para uma solicitação do GraphQL `updateCompanyRole` para um usuário não autorizado.
* **ACSD-54106** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) - Corrige o problema em que a classificação de produto de categoria por nome para caracteres com acento turco está incorreta.
* **ACSD-52219** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que os filtros salvos de grades de administração não funcionam como esperado ao alternar frequentemente entre exibições de marcadores.
* **ACSD-54342** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige uma mensagem de erro incorreta *Erro na estrutura de dados: os valores são misturados* ao importar um arquivo CSV sem dados válidos.
* **ACSD-54660** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Um novo atributo de entrada *sort* foi adicionado para classificar pedidos de clientes no GraphQL por `sort_field` e `sort_direction`.
* **ACSD-54776** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que os valores de campo de produto desmarcados *[!UICONTROL Use Default Value]* e não padrão não são salvos no segundo modo de exibição de site, loja e loja.
* **ACSD-53998** (para Adobe Commerce e Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Corrige o problema em que um **[!UICONTROL Dynamic Block]** baseado em um **[!UICONTROL Customer Segment]** não funciona corretamente depois de sair de uma conta de cliente.
* **ACSD-53204** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Correções *O produto não pode ser salvo.* erro ao fazer solicitações simultâneas para adicionar imagens à galeria de produtos usando o ponto de extremidade `rest/V1/products/<sku>/media`.
* **ACSD-47657** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Adição de um mecanismo de cache para credenciais AWS. Um provedor de credenciais agora usa o cache do Magento para armazenar em cache credenciais recuperadas do AWS para configuração EC2.
* Patches atualizados: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corrige o problema em que os produtos atribuídos a um catálogo compartilhado não aparecem na loja quando um índice parcial é executado.
* **ACSD-54018** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige os problemas de desempenho com o widget [!UICONTROL Product List] que usa um atributo não global na condição do widget.
* **ACSD-54111** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que as imagens em miniatura do produto não são exibidas na loja quando a proporção da imagem da marca d&#39;água não corresponde à imagem do produto.
* **ACSD-47669** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Correções *Violação de restrição de integridade: 1452 Não é possível adicionar ou atualizar uma linha secundária: uma restrição de chave estrangeira falha* erro ao importar CSV de produtos.
* **ACSD-53347** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a indexação de preços leva muito tempo para ser executada.
* **ACSD-52287** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema com o status de ordem incorreto na grade de ordem arquivada quando a indexação de grade assíncrona está habilitada.
* **ACSD-52929** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema com solicitações redundantes para reindexar itens de origem padrão quando o indexador de inventário é configurado no modo assíncrono.
* **ACSD-53824** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que o patch de dados de migração `UpdateMultiselectAttributesBackendTypes` excede o limite de tamanho de transação do banco de dados durante `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que caches e índices são atualizados mesmo quando não são feitas atualizações para `Inventory_source` itens pela API REST.
* **ACSD-51884** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o caminho do cache de imagem do produto se torna incorreto após a execução do comando resize.
* **ACSD-53628** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o relatório de ordem de venda CSV mostra caracteres especiais incorretos.
* **ACSD-53148** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável ao carrinho resultavam em dois itens separados no carrinho com o mesmo SKU de produto.
* **ACSD-52606** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que a mensagem de erro *Seu pedido não está pronto para retirada* é exibida quando o usuário clica em **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a imagem não é atualizada no front-end depois de substituí-la por outra imagem com o mesmo nome.
* **ACSD-53728** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o indexador EAV do produto está demorando mais para ser concluído.
* **ACSD-53979** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema de JS que ocorre na página inicial se a mensagem de boas-vindas contiver uma aspa simples.
* **ACSD-52085** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que um produto configurável com preço especial não é visível no carrossel do produto.
* **ACSD-53795** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema com o tipo de dados inválido no trabalho do cron `indexer_update_all_views`.
* **ACSD-52143** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que as opções personalizadas são removidas após a importação do produto.
* **ACSD-53750** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o erro *Pipe corrompido ou conexão fechada* durante a reindexação `catalog_product_price` de vários threads.
* **ACSD-49843** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Corrige o problema em que o link no download do produto não está disponível depois que o item solicitado é faturado automaticamente pelo método de pagamento online com a configuração **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** ativada.
* **ACSD-47054** (para Adobe Commerce >=2.4.2 &lt;2.4.6) - Corrige o problema em que a reindexação de visualização executa a reindexação para todas as lojas, causando lentidão.
* Adição de novas versões para ACSD-46541, ACSD-47079.
* ACSD-49970-v3 substituído por ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt; 2.4.6) - Corrige o problema em que o indexador de inventário limpa todos os caches no modo Atualização na Programação.
* **ACSD-50887** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que a propriedade de atributo de produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definida como *Sim* sem a opção *[!UICONTROL Use in search]* definida como *Sim*.
* **ACSD-51846** (para Adobe Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Corrige o problema de *Erro Interno* que ocorre porque nem todos os níveis de carga da API REST estão validados.
* **ACSD-52906** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que o cookie X-Magento-Vary é definido incorretamente para clientes conectados que pertencem ao mesmo segmento do cliente, causando cache inadequado para algumas páginas.
* **ACSD-52736** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que uma *Regra de Preço do Carrinho* que inclui requisitos para a quantidade de produto configurável não funciona conforme esperado.
* **ACSD-47875** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que os usuários administradores não podem adicionar um produto a um carrinho do cliente do Administrador para um escopo de exibição de loja específico com gerenciamento de estoque.
* **ACSD-53176** (para Adobe Commerce >=2.3.7 &lt;2.4.5) - Corrige o problema em que a *Regra de Produto Relacionada* com *é uma das* condições não corresponde aos produtos.
* **ACSD-51666** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o erro *A sessão expirou. Faça logon novamente.* que acontece depois que um cliente tenta fazer login.
* Adição de novas versões para MDVA-39305-v2.
* Atualização dos requisitos para o ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que o endereço de remessa padrão na etapa de remessa do check-out é preenchido automaticamente com um endereço de remessa na loja selecionado anteriormente.
* **ACSD-52041** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a mensagem de erro: *[ERRO] [!DNL Page Builder] foi renderizada por 5 segundos sem liberar bloqueios.* aparece no navegador Chrome ao salvar o conteúdo editado com [!DNL Page Builder].
* **ACSD-52095** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que o valor `manage_stock` era definido incorretamente como 0 no arquivo CSV após a exportação do produto.
* **ACSD-51358** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que a remoção de uma atualização agendada sem uma data de término leva à remoção de outras atualizações agendadas para a mesma entidade.
* **ACSD-48070** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que a edição de uma atualização agendada aciona uma exceção.
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
* Versões atualizadas para ACSD-47803.
* Atualização do título para ACSD-51892.
* Atualização do ACSD-51379.
* Atualização do ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um usuário administrador não é redirecionado corretamente após selecionar uma exibição de loja ao criar uma nova ordem no Administrador.
* **ACSD-50813** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que o Administrador não podia adicionar produtos agrupados contendo uma barra na SKU com a funcionalidade [!UICONTROL Add Products by SKU] à ordem do administrador.
* **ACSD-51630** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que uma grande quantidade de mensagens do sistema atrasa o download de páginas de administração.
* **ACSD-51853** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corrige o problema em que os estilos de texto copiados não são aplicados ao usar o [!UICONTROL Page Builder].
* **ACSD-52160** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que o resultado de validação do produto em relação à regra de preço do carrinho não era avaliado corretamente com base na condição de regra &quot;Se um item for ENCONTRADO/NÃO ENCONTRADO no carrinho com Todas/Qualquer uma dessas condições for verdadeira&quot;.
* **ACSD-51636** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que o administrador da empresa não pode adicionar novos usuários da seção de conta do cliente apesar de ter todas as funções e permissões necessárias.
* **ACSD-51739** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que um erro é retornado quando o `structure_id` é solicitado em uma solicitação de CompanyTeam GraphQL.
* **ACSD-51857** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que o desempenho lento do relatório do `aggregate_sales_report_bestsellers_data` cron em tabelas de banco de dados grandes sales_order e `sales_order_item` era devido à forma como a consulta de dados principal era gravada.
* **ACSD-48448** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que há um problema de condição de corrida ocorrendo durante os cancelamentos de pedidos, o que causa uma entrada duplicada na tabela `inventory_reservation`.
* **ACSD-52689** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6) - Corrige o problema em que as imagens não podem ser carregadas para o armazenamento do Amazon S3 usando a API REST.
* **B2B-2674** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Adicione o recurso de cache à consulta do GraphQL 1customAttributeMetadata1.
* Adição de novas versões para ACSD-44938.
* Adição de requisitos para o ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Corrige o comando de reversão de banco de dados para um caso em que o despejo de banco de dados contém acionadores e um comando SQL *delimitador*.
* **ACSD-50512** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o *Erro: o link disponível para download não está relacionado ao produto. Verifique o link e tente novamente.Erro* que ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável.
* **ACSD-50949** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o filtro de preço na pesquisa avançada não retorna resultados adequados quando usado com o filtro SKU.
* **ACSD-51645** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o erro lançado ao salvar uma nova Regra de Preço do Carrinho se a extensão `Magento_OfflineShipping` estiver desabilitada.
* **ACSD-50895** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que [!DNL Google Analytics] 3 marcas GTM não são acionadas se [!DNL Google Analytics] 4 GTM não estiver configurado.
* **ACSD-51102** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que uma regra de catálogo aplicada a um grande número de produtos não é indexada corretamente quando a regra é habilitada por uma atualização agendada.
* **ACSD-50368** (para Adobe Commerce e Magento Open Source >= 2.4.3 &lt;2.4.5) - Corrige o problema em que o `group_id` do cliente é ignorado quando um cliente é criado por meio da API REST assíncrona ou da API REST em massa assíncrona.
* **ACSD-51497** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corrige o problema em que um cliente não pode classificar uma página de catálogo por Atributo personalizado do tipo de lista suspensa.
* **ACSD-51408** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt; 2.4.7) - Corrige o problema em que o status do item do pedido está definido incorretamente como *[!UICONTROL Backordered]*.
* **ACSD-51735** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que o status do item do pedido é definido incorretamente como *[!UICONTROL Ordered]* quando o estoque do produto é *0*.
* **ACSD-51792** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que uma página não tem o evento de impressão quando o [!DNL Google Tag Manager] 4 está habilitado.
* **ACSD-51471** (para Adobe Commerce >=2.4.3 &lt;2.4.7) - Corrige o problema em que um usuário administrador não pode salvar uma atualização agendada para um produto agrupado que usa um produto simples que tem uma atualização agendada.
* **ACSD-51700** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o erro que ocorre ao alternar exibições da loja em uma página de edição de produto baixável no administrador.
* **ACSD-51120** (para Adobe Commerce >=2.3.7 &lt;2.4.3) - Corrige o problema em que o cache de solicitações do GraphQL GET não é limpo em páginas do CMS que contêm blocos do CMS atualizados por meio de uma atualização de preparo.
* **ACSD-51240** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige o problema em que o arquivo carregado está ausente se o registro for feito por meio do formulário de registro da empresa.
* **ACSD-51907** (para Adobe Commerce >=2.4.2 &lt;2.4.3) - Corrige o problema em que um usuário administrador restrito não consegue criar um memorando de crédito com um reembolso offline.
* **ACSD-52148** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que o logon de Administrador do [!DNL Google V3 reCAPTCHA] falha ocasionalmente.
* **ACSD-51431** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o status de um indexador é *funcionando* mesmo se não houver entradas novas no log de alterações.
* **ACSD-51892** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema de desempenho em que os arquivos de configuração são carregados várias vezes.
* ACSD-51114 obsoleto.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que os vários erros do [!UICONTROL Page Builder's] impedem que o administrador salve um produto sem permissões de conteúdo.
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
* **ACSD-51294** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que o preço, a quantidade, o imposto, a remessa e a receita GTM/GA são enviados como uma cadeia de caracteres para [!DNL Google Analytics] e GTM.
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
* **ACSD-50814** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que um usuário administrador não pode criar um memorando de crédito.
* **ACSD-50116** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que um usuário administrador não consegue criar uma regravação de URL para subcategorias de nível 3 ou inferior.
* **ACSD-49513** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5) - Corrige o problema em que a sincronização do armazenamento remoto falha devido a arquivos de 0 bytes.
* **ACSD-46683** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema no qual o preço de envio mostra *Ainda não calculado*.
* **ACSD-49129** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que o atributo *[!UICONTROL content]* (código de imagem base64) não é retornado nas respostas da API de mídia do produto `rest/V1/products/sku/media`.
* **ACSD-50276** (para Adobe Commerce >=2.4.0 &lt;2.4.7) - Corrige o problema em que o formulário de registro do cliente não funciona na loja se um atributo de cliente de seleção múltipla for criado.
* **ACSD-50527** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o erro que ocorre ao salvar uma página com um bloco dinâmico vazio.
* **ACSD-49973** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Melhora o desempenho da busca de produtos agrupados por meio do GraphQL.
* **ACSD-51114** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um produto aleatório desaparece de catálogos grandes quando a indexação assíncrona está habilitada. Melhora o desempenho da reindexação assíncrona para catálogos grandes.
* **B2B-2598** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Adicione o recurso de cache às consultas do GraphQL [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] e [!UICONTROL storeConfig].
* Adição de novas versões para MDVA-42806, ACSD-48627, ACSD-46815.
* Atualização de metadados de patches para ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um email pronto para coleta é enviado pela API quando o pedido não está pronto para coleta.
* **ACSD-49822** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que as atualizações na página [!UICONTROL Requisition List] não são refletidas no [!UICONTROL Print Requisition List].
* **ACSD-48771** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema de atualização do tipo de conteúdo de bloco de coluna a partir de versões [!DNL Page Builder] mais antigas.
* **ACSD-49464** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que faturas, remessas e avisos de crédito não são movidos de volta do arquivo quando orderId é diferente.
* **ACSD-49773** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que a exportação de produtos falha quando o AWS S3 é usado como armazenamento remoto.
* **ACSD-49748** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que os convites não podem ser enviados.
* **ACSD-49502** (para Adobe Commerce >=2.4.3 &lt;2.4.7) - Corrige o problema em que o link baixável não é atualizado corretamente após uma atualização de preparo ser aplicada ao produto baixável.
* **ACSD-49527** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que as funções da empresa GraphQL não exibem a paginação corretamente.
* **ACSD-49706** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado.
* **ACSD-49835** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que o valor da caixa de seleção Usar padrão não é salvo corretamente em um nível de repositório para um atributo de seleção múltipla.
* **ACSD-49898** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a grade de produtos lança uma exceção quando um produto agrupado tem um preço especial superior a 1000.
* **ACSD-50234** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.5) - Corrige o problema com o nome de cliente errado no email de confirmação se fizer um pedido com [!DNL PayPal].
* **ACSD-49960** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que a filtragem por data não funciona para a grade de pedidos do cliente.
* **ACSD-49849** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que o email do cliente foi substituído pelo email [!DNL PayPal] ao fazer um pedido com [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que a estrutura e a Precificação do Catálogo Compartilhado lançam um erro no Administrador quando os produtos têm aspas simples ou duplas no SKU.
* **ACSD-49970** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige a manipulação incorreta de erros do GraphQL quando os relatórios do [!DNL New Relic] estão ativados.
* **ACSD-50260** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que os resultados da pesquisa de produtos da GraphQL estão limitados a apenas 10.000 resultados.
* **ACSD-48813** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a pesquisa não mostra resultados relevantes com base no peso da pesquisa dos atributos.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.3) - Corrige o problema em que uma regra de preço de catálogo criada com base no atributo Sim/Não considera o escopo selecionado.
* **ACSD-47704** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o produto incluído mostra somente o preço dos produtos em estoque.
* **ACSD-49370** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o atributo de produto *Data e hora* tem um tipo *FilterMatchTypeInput* no esquema do GraphQL.
* **ACSD-48807** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corrige o problema em que as Avaliações de Produtos do cliente não são filtradas pela storeview via GraphQL.
* **ACSD-49433** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que o valor padrão é mostrado como subtotal no carrinho para cartão-presente com um valor aberto.
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
* **ACSD-47908** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corrige o erro &quot;Um valor menor ou igual a 0 é esperado&quot; ao selecionar a origem e a quantidade na etapa de envio durante a finalização da compra.
* **ACSD-49497** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que um pedido permanece no estado de processamento após o envio e um reembolso parcial é aplicado.
* **ACSD-48694** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Corrige o problema em que o erro &quot;Alteração de estado inválida solicitada&quot; impede que um cliente faça um pedido.
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
* **ACSD-48587** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que os caracteres especiais do HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes.
* **ACSD-48212** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que a importação de produtos atribui o produto à origem errada.
* **ACSD-47988** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que a exportação de produtos elimina as marcas HTML da descrição do produto do page builder.
* **ACSD-48366** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a imagem do produto não é exibida no modelo de email Voltar para o Estoque.
* **ACSD-48417** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que um erro SQL aparece após criar uma alteração de agendamento para um produto e salvar outro produto.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que a reindexação de preço do produto não funciona se o produto do pacote não estiver atribuído a nenhum site.
* **ACSD-48262** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que os produtos não estão visíveis no front-end quando a configuração &quot;Permitir todos os produtos por página&quot; está definida como Sim.
* **ACSD-48293** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corrige o problema em que os produtos compostos ficam sem estoque quando os produtos derivados que foram vendidos são devolvidos ao estoque.
* **ACSD-47520** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que os clientes perdem pontos de premiação quando um memorando de crédito é criado.
* **ACSD-48044** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que a aplicação de vários cartões-presente a um único pedido com remessa múltipla impede que os pedidos sejam feitos.
* **ACSD-48300** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que um retorno não pode ser criado se o produto configurável for removido.
* **ACSD-47910** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema de pedidos, faturas, remessas e avisos de crédito ausentes nas respectivas grades de entidade.
* **ACSD-47292** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que os produtos empacotados esgotados não estão disponíveis na resposta da GraphQL se &quot;mostrar produtos esgotados&quot; estiver definido como Sim.
* **ACSD-48234** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que o resultado da pesquisa no catálogo mostra uma contagem de itens de categoria incorreta quando a opção &quot;mostrar indisponível&quot; está habilitada.
* **ACSD-48313** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Corrige o problema em que a coluna &quot;configurable_variation&quot; não é analisada se o valor do atributo contiver uma vírgula. O mesmo algoritmo de análise é usado para &quot;additional_attributes.
* **ACSD-48627** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que o produto configurável sem estoque causa um erro ao enviar uma solicitação GraphQL para obter detalhes do carrinho.
* Patch atualizado: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que URLs amigáveis para SEO não são geradas para produtos com atributos *url_key* substituídos no nível de exibição da loja.
* **ACSD-46865** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a grade de Aviso de Remessa e Crédito não é preenchida quando a indexação assíncrona está habilitada.
* **ACSD-47004** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que o IVA não é aplicado a um endereço de cobrança sem uma ID de IVA.
* **ACSD-47803** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que amostras de produtos configuráveis e sem estoque são exibidas como disponíveis.
* **ACSD-47137** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Melhora a velocidade de carregamento da galeria de imagens quando a pasta pub/media é muito grande.
* **ACSD-46770** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que emails de pedido de administrador são enviados mesmo quando a *Confirmação de pedido de email* está desmarcada.
* **ACSD-47955** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que o GraphQL não exibe o desconto do carrinho corretamente.
* **ACSD-46617** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o botão *Continuar para o Check-out* fica esmaecido mesmo se o subtotal for maior que o *Valor Mínimo do Pedido* configurado.
* **ACSD-47079** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que o status do estoque de produtos compostos (agrupados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado via REST API POST /rest/V1/inventory/source-items.
* **ACSD-47336** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Correções *Algo deu errado.Erro* ao dispensar notificações no Administrador do Commerce.
* **ACSD-47559** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a área Visualizar Modelo de Email não estava totalmente visível.
* **ACSD-47920** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que os pedidos podem ser feitos por meio da API Rest como um usuário convidado, mesmo quando a opção *Permitir check-out de convidado* está desativada.
* Patches substituídos: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que um administrador com acesso restrito a um escopo específico não pode excluir análises de produtos.
* **ACSD-47107** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Corrige o problema em que o desconto de Regra de Preço de Catálogo é aplicado às opções de produto personalizadas.
* **ACSD-47232** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que os cupons com condições de peso total não podem ser aplicados no Admin.
* **ACSD-46519** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6) - Corrige o problema em que a solicitação categoryList do GraphQL retorna uma product_count incorreta para uma categoria âncora.
* **ACSD-47027** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige uma solicitação lenta de GraphQL updateCompanyRole.
* **ACSD-47666** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a função de filtro não funciona na grade Admin > Sistema > Permissões > Funções de usuário > uma função > Usuários de função.
* **ACSD-47497** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a guia Serviços não estava visível na Configuração sob o Administrador.
* Correção atualizada: ACSD-47743.
* Patches substituídos: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3) - Corrige o erro _Tentando acessar deslocamento de matriz no valor do tipo bool_ ao acessar determinados caminhos de categoria não existentes para produtos conhecidos no PHP 7.4.
* **ACSD-47332** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o cron falha com um erro que só é relatado durante a execução entre 00:00 e 00:59 UTC.
* **ACSD-47280** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a desabilitação do recurso de catálogo compartilhado em um escopo específico não funciona corretamente.
* **ACSD-47106** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que um valor não pode ser salvo em um novo atributo personalizado em uma página de criação de empresa.
* Correção atualizada: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que um usuário recebe um erro ao atribuir um grande número de fontes de produtos.
* **ACSD-46856** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Melhora os preços de camada de atualização de desempenho por meio de Sistema > Configuração > Importação > Advanced Pricing.
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
* **ACSD-46703** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige o problema em que não é possível arrastar e soltar opções personalizadas em uma página de edição de produtos.
* **ACSD-44851** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema em que uma categoria com subcategorias não pode abrir ou expandir.
* **ACSD-46815** (*para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6*) - Corrige o problema em que a solicitação da árvore de categoria é limitada a 20 categorias.
* **ACSD-45675** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema em que a exportação de produtos usa nomes de categoria do escopo *Exibição de Loja Padrão*.
* **ACSD-46869** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige o problema em que um produto configurável em um carrinho não é atualizado por meio de uma solicitação da *API REST do PUT* sem alterar a quantidade do produto.
* **MDVA-42768-V2** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o produto Configurável exibe o preço normal como *0* quando *Exibir Fora de Estoque* está *Sim*.
* Patches atualizados: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Patch obsoleto: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que a solicitação da árvore de categoria é limitada a 20 categorias.
* **ACSD-45781** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.2*) - Corrige o problema em que o campo de pesquisa frontal da loja não é exibido no celular.
* **ACSD-46192** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;2.4.5*) - Corrige o problema no uso do ponto de extremidade `async/bulk/V1/configurable-products/bySku/options`.
* **ACSD-46404** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige o problema em que um usuário administrador não consegue fazer logon após atualizar para a versão 2.4.4.
* Patches atualizados: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que uma mutação de produto do GraphQL para uma loja específica retorna todas as variantes configuráveis, incluindo aquelas não atribuídas à loja solicitada.
* **ACSD-46146** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que dois emails de confirmação de pedido são enviados após a realização de um pedido pelo Administrador.
* **ACSD-45255** (*para Adobe Commerce >=2.4.3 &lt;2.4.6*) - Corrige uma exceção na página Relatório de Baixo Estoque para um usuário administrador restrito.
* **ACSD-45488** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6*) - Corrige o problema em que um produto configurável com várias origens não é retornado automaticamente para o In Stock.
* **ACSD-45754** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema em que os pontos de Recompensa não são adicionados após a aplicação de um cupom ao carrinho.
* **ACSD-45849** (*para Adobe Commerce >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo.
* **ACSD-45257** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema em que o GraphQL não exibe um desconto de carrinho corretamente.
* **ACSD-44938** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que `VAT_ID` não pode ser aplicado em uma solicitação GraphQL para um usuário convidado.
* Patches atualizados: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige o problema em que a quantidade em estoque de um produto virtual é calculada incorretamente após a criação de um memorando de crédito.
* **ACSD-43887** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando as Ordens de Compra para empresas estão habilitadas.
* **ACSD-45143** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que a mutação `setShippingAddressesOnCart` não permite definir o código de região numérica como *região*.
* **ACSD-44591** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6*) - Corrige o erro que ocorre quando um pedido é feito sem confirmação CAPTCHA.
* **ACSD-45520** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que as opções de amostra não são pré-selecionadas na página de detalhes do produto quando um usuário edita produtos configuráveis do carrinho de compras.
* **ACSD-45169** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6*) - Corrige o problema em que o [!DNL Visual Merchandiser] não exibe o estoque e o preço corretos de um produto configurável após a aplicação de uma atualização de preparo.
* **ACSD-45424** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.6*) - Corrige o problema em que uma compensação de reserva incorreta é criada após um reembolso parcial (memorando de crédito).
* **MDVA-42807** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema em que o sinal de moeda personalizado não é exibido na frente da loja.
* Patches atualizados: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os totais de pedidos no relatório de Pedidos são calculados incorretamente para o usuário administrador restrito.
* **MDVA-44940** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o erro SQL que ocorre ao salvar a categoria do Administrador.
* **MDVA-44562** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Corrige o problema em que a ID de repositório não padrão para itens de cotação é substituída pela ID de repositório padrão, apesar da solicitação do GraphQL originada da exibição de repositório não padrão.
* **MDVA-43167** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que a ação em massa da grade de ordem do administrador não se aplica a várias páginas quando o usuário administrador seleciona todas as ordens.
* **MDVA-44044** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Corrige o problema em que um produto não é exibido na página de categoria depois de ser atribuído a um novo site.
* **MDVA-42509** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.4*) - Corrige o problema em que não foi possível carregar um CSV para uma ordem rápida, resultando em um erro *Não é possível enviar o cookie*.
* Patches atualizados: MDVA-41061, MDVA-42584.
* O prefixo dos novos patches [!DNL Quality Patches Tool] será alterado de *MDVA* para *ACSD* devido a alterações internas no processo.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que um item adicional não pode ser adicionado ao carrinho quando a quantidade mínima do item já está no carrinho.
* **MDVA-44887** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige o erro *Uncaught SyntaxError: Unexpected token &#39;const&#39;* no painel de Administração.
* **MDVA-43718** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Correções *O consumidor não está autorizado a acessar %resources.Erro* que aparece ao acessar um catálogo compartilhado de uma integração personalizada.
* **MDVA-44660** (*para Adobe Commerce e Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Corrige o problema em que o caractere de acento grave ``` ` ``` não pode ser usado para o nome e sobrenome de um cliente.
* **MDVA-40896** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o *Erro: TypeError: Argumento 3 passado para o erro Magento* na API assíncrona de produto em massa.
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
* **MDVA-44147** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que uma solicitação do GraphQL não retorna Listas de Requisições.
* **MDVA-44505** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige os problemas em que a Aplicação de Pontos de Recompensa pela GraphQL não atualiza o Total Geral e em que o crédito da loja é aplicado várias vezes durante o posicionamento do pedido.
* Patches atualizados: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige o problema em que a Regra de Produto Relacionada funciona somente quando o Segmento do Cliente está definido como *Todos*.
* **MDVA-39605** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que o TTL (data de expiração) de cache Redis tem um valor incorreto.
* **MDVA-43862** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige o problema em que o cliente não pode atualizar itens de carrinho devido a um erro de *AtualizarItensDeCarrinho* do GraphQL.
* **MDVA-43824** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Corrige o problema em que um erro aparece ao cancelar pedidos com um desconto.
* **MDVA-43451** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o erro *O armazenamento solicitado não foi encontrado. Verifique o armazenamento e tente novamente.* aparece ao configurar um catálogo compartilhado para um site específico.
* **MDVA-43491** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corrige o problema em que o rótulo da imagem base não é atualizado ao importar produtos para um site de várias lojas.
* **MDVA-43601** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema de disparadores ausentes após a reindexação completa.
* **MDVA-42046** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Corrige o problema em que um valor incorreto é atribuído a um atributo de produto com um campo de entrada de data ao atualizar um produto.
* **MDVA-43935** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o produto de venda adicional é exibido duas vezes.
* **MDVA-44188** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que os emails emitidos pelo sistema com `.-` em endereços não são enviados.
* **MDVA-42283** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que o formato de data e hora na grade de ordem de administração da localidade francesa é inválido.
* Patches atualizados: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Adicionados metadados de patches para o [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corrige o problema em que o usuário pode editar a hora de início de uma atualização agendada ativa.
* **MDVA-42410** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os relatórios de cupom exibem somente a moeda base padrão.
* **MDVA-41136** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que a data de expiração do `mage-cache-sessid` não é estendida, resultando na limpeza dos dados do cliente.
* **MDVA-39993** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Corrige o problema em que as alterações de inventário feitas por meio da API não refletem na página do produto no front-end.
* **MDVA-42855** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que um novo endereço de cliente não é salvo no catálogo de endereços durante o check-out.
* **MDVA-42645** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o Administrador não pode reembolsar pontos de premiação se a funcionalidade de crédito de armazenamento estiver desabilitada.
* **MDVA-43414** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Corrige o erro fatal de PHP que ocorre ao executar o consumidor da fila `inventory.reservations.updateSalabilityStatus` em SKUs numéricas.
* **MDVA-41628** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que usuários administradores restritos existentes obtêm acesso aos novos recursos quando novos módulos são adicionados.
* **MDVA-43348** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que a solicitação de cartão-presente GraphQL mostra um erro se `gift_card_options` contiver *uid*.
* **MDVA-39546** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que a data de início da atualização de preparo podia ser definida como uma data anterior à data atual durante a edição.
* **MDVA-42950** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os vídeos não são reproduzidos na página do produto.
* **MDVA-42689** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que o Adobe Commerce lança um erro de *Violação de Restrição de Integridade* ao atualizar categorias de produto durante a importação.
* **MDVA-41229** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que as imagens disponíveis no back-end não são exibidas no front-end após a importação de produtos configuráveis.
* **MDVA-43731** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os *Sinônimos de Pesquisa* não funcionam mais quando o valor é adicionado em *Termos Mínimos para Correspondência*.
* **MDVA-43232** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que a classificação de produtos em [!DNL Visual Merchandiser] por Preço Especial para Baixo/Cima causa um erro ao salvar a categoria.
* **MDVA-43726** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.3*) - Corrige o problema em que a regra de preço de catálogo baseada na correspondência de atributo no nível do repositório falha ao ser aplicada após a reindexação parcial.
* Patches atualizados: MDVA-36464, MDVA-37478, MDVA-38608.
* Adicionados metadados de patches para o [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que os atributos de preço do produto não podem ser atualizados para um site específico por meio da API REST.
* **MDVA-41350** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que uma exceção é lançada quando um usuário administrador com acesso restrito adiciona um produto fora de seu escopo de função por SKU em um pedido.
* **MDVA-42269** (*para Adobe Commerce e Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Corrige o problema em que um usuário administrador não consegue fazer logon no Administrador devido ao *TypeError: strtotime() espera que o parâmetro 1 seja uma cadeia de caracteres, nulo dado* erro.
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
* **MDVA-42584** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque configurável no back-end não é atualizado após a alteração do status da quantidade e do estoque por meio da Importação ou da API.
* **MDVA-40175** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige o problema em que *Clicar para alterar o método de envio* não mostra botões de opção para selecionar métodos de envio no Administrador durante a reorganização.
* **MDVA-42768** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que o produto Configurável exibe o preço normal como 0 quando *Exibir Fora de Estoque* está definido como Sim.
* **MDVA-43201** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que ocorre um erro no logon do cliente ao usar o atributo DOB com determinadas localidades.
* Patches atualizados: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os filtros de data não estão funcionando corretamente quando o fuso horário do Adobe Commerce é diferente do fuso horário do ambiente local.
* **MDVA-42657** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não consegue selecionar categorias nas condições do segmento do cliente.
* **MDVA-42806** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que um email de *Registro de nova empresa* é enviado sempre que uma empresa existente é atualizada por meio da API REST.
* **MDVA-37984** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que a funcionalidade [!DNL Visual Merchandiser] *Corresponder produto por regra* não filtra corretamente os produtos com atualizações de preparo.
* **MDVA-40488** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que os produtos configuráveis com produtos derivados indisponíveis não são mostrados em seu intervalo de preços correto.
* **MDVA-42507** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho.
* **MDVA-39163** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corrige o problema em que os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão de convidado.
* **MDVA-38626** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não pode fazer um pedido no back-end usando o pagamento [!DNL PayPal Payflow Pro].
* **MDVA-38666** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.3.6*) - Corrige o problema em que o usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente.
* **MDVA-38526** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o usuário administrador não consegue acessar o [!DNL Site-Wide Analysis tool].
* Patches atualizados: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que os usuários obtêm o erro 500 após definir o cookie *mage-messages* se ele já existir, mas não houver novas mensagens.
* **MDVA-41139** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os produtos configuráveis ficam Fora do Estoque após a importação do produto quando a quantidade=0 de um produto simples para uma de suas origens.
* **MDVA-42326** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os clientes recebem um erro no check-out após um tempo limite de sessão, mesmo se o carrinho de compras persistente estiver habilitado.
* **MDVA-42341** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que a consulta do GraphQL `categoryList` não filtra os resultados se uma solicitação tiver o cabeçalho Store.
* **MDVA-38393** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras do Catálogo param de funcionar para um produto configurável se seu produto simples for renomeado.
* **MDVA-39153** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que um valor de desconto é calculado incorretamente durante um novo pedido no Administrador.
* Patches atualizados: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os usuários administradores não podem acessar a grade do cliente após excluir o site.
* **MDVA-40311** (*para Adobe Commerce e Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Corrige o problema em que os usuários administradores recebem a mensagem de erro *Chave de formulário ou segurança inválida. Atualize a página* após fazer logon no Administrador se o caminho Admin personalizado estiver configurado e a chave secreta estiver habilitada.
* **MDVA-41631** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao tentar recuperar informações de pedidos sem um valor *telefone* opcional por meio do GraphQL.
* **MDVA-27239** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corrige o problema em que os produtos de venda cruzada não são exibidos.
* Patches atualizados: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige o problema de produtos ausentes no front-end durante a reindexação.
* **MDVA-40120** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que a classificação do GraphQL por DESC/ASC não funciona com produtos que tenham a mesma relevância ou preço.
* **MDVA-41399** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.2*) - Corrige o problema em que os usuários administradores não conseguem acessar a página *Gerenciar Carrinho de Compras* se um cliente adicionar um produto à lista de desejos.
* **MDVA-40609** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que os dados de produtos desabilitados estão ausentes na tabela de índice `cataloginventory_stock_status`, exibindo quantidades incorretas de produtos desabilitados.
* **MDVA-39031** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que é possível adicionar um produto ao carrinho por meio do GraphQL, mesmo que ele não esteja atribuído ao site de destino.
* **MDVA-41597** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao adicionar mais de um produto configurável ao carrinho usando o GraphQL.
* **MDVA-27456** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.3.7*) - Corrige o problema em que os usuários recebem um erro ao tentar carregar [!DNL Swagger].
* **MDVA-32776** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2*) - Corrige o problema em que o status do estoque não é atualizado quando um pedido é feito, mas não enviado.
* **MDVA-30862** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.0*) - Corrige o problema com a data de pedido incorreta na fatura PDF impressa.
* Página de índice aprimorada para [!DNL Quality Patch Tool]. Adição de pesquisa e filtragem convenientes para [!DNL quality patches] na versão mais recente da ferramenta.
* Patches atualizados: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que é impossível criar uma atualização agendada nova ou editar uma existente para um produto se a Data de Término tiver sido removida anteriormente.
* **MDVA-41046** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que produtos simples com opções personalizadas estão disponíveis para atribuição a produtos configuráveis/agrupados.
* **MDVA-40545** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que somente o primeiro nó de uma página foi recuperado, mesmo que houvesse mais de um nó para a mesma página.
* **MDVA-41164** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Corrige o problema em que um usuário administrador não pode salvar ou editar uma Empresa com um atributo de cliente personalizado do tipo arquivo ou imagem.
* **MDVA-39229** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema que faz com que o seguinte erro apareça após a atualização da hora de início da Atualização de Preparo da regra de Catálogo: *O trabalho Cron staging_synchronize_entities_period tem um erro: A atualização ativa não pode ser excluída.*
* **MDVA-40619** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as alterações na hierarquia de páginas do CMS causam um erro 500 ao tentar fazer edição em linha em uma página do CMS.
* **MDVA-41061** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque é redefinido para vendável quando um produto é salvo do Administrador.
* **MDVA-31763** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras de preço de catálogo são revertidas (ou não aplicadas) até a reindexação manual.
* **MDVA-37748** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que uma consulta do GraphQL retorna produtos não atribuídos a um catálogo compartilhado.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que faturas parciais para o mesmo pedido não podem ser criadas simultaneamente via API REST.
* **MDVA-40101** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.0*) - Corrige o problema em que os itens não são removidos do minicarrinho após um posicionamento de pedido bem-sucedido usando o Check-out do [!DNL PayPal Express].
* **MDVA-40401** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o valor de uso do cupom muda mesmo se um pedido falhar.
* **MDVA-40537** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Corrige o problema em que os usuários obtêm um erro ao criar uma exibição de repositório se existirem várias páginas do CMS com a mesma chave de URL.
* **MDVA-37725** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Corrige o problema em que emails de ordem assíncrona enviados de sites não padrão contêm URLs de logotipo do site padrão.
* **MDVA-39482** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que um produto sai do estoque se importado com a quantidade &quot;0&quot; quando ordens pendentes são habilitadas.
* **MDVA-40435** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema com um desconto incorreto em produtos de pacote com preços dinâmicos quando aplicados via GraphQL.
* **MC-42528** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Corrige o problema em que a consulta do GraphQL `categoryList` retorna categorias atribuídas e não atribuídas.
* **MDVA-29400** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com pedidos duplicados feitos com [!DNL PayPal Express Checkout].
* **MDVA-26005** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Corrige o problema em que é impossível selecionar uma categoria em uma árvore de categorias para as condições de regra de Preço do carrinho.
* **MDVA-25631** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Melhora o desempenho para editar e salvar segmentos de clientes que contêm um grande número de clientes.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que as consultas de pesquisa do GraphQL não são mostradas em termos de pesquisa populares no Administrador.
* **MDVA-40601** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários recebem um erro ao tentar obter informações sobre a categoria alteradas por meio de atualização agendada no GraphQL.
* **MDVA-37234** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que adicionar um item ao carrinho várias vezes (solicitação paralela) para o mesmo SKU cria um item de linha duplicado para a mesma ID do carrinho.
* **MDVA-33606** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários recebem um erro *Violação de restrição exclusiva* ao salvar uma página do CMS atribuída a uma hierarquia.
* **MDVA-31590** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que os usuários não podem atualizar atributos em massa usando filas assíncronas MySQL.
* **MDVA-36309** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que a pesquisa de produto por atributos está lenta nas grades de administração.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que a fatura com FPT mostra um Total Geral incorreto quando o pedido é pago a partir do crédito da loja.
* **MDVA-37364** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.3*) - Corrige o problema em que o atributo de cliente personalizado do tipo de data quebra a interface do usuário da grade do cliente.
* **MDVA-39195** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que o botão *Adicionar ao carrinho* estava inativo na página de categoria quando o redirecionamento para o carrinho estava habilitado.
* **MDVA-37115** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que um aviso *Somente 0 restante* desnecessário é exibido na página do produto configurável.
* **MDVA-39521** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que o usuário não consegue definir endereços de envio no carrinho com um número de telefone vazio por meio do GraphQL.
* **MDVA-39384** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Corrige o problema em que o atributo de cliente personalizado de um usuário da empresa não é salvo.
* **MDVA-39043** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.3*) - Corrige o problema em que o usuário administrador com acesso limitado recebe um erro ao tentar adicionar o widget *Produtos* à página do CMS.
* **MDVA-39966** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com a implantação de localidades incorretas.
* **MDVA-38852** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Corrige o problema em que o inventário de catálogo por design bloqueia as tabelas para atualizações que diminuem significativamente o desempenho em casos com várias ordens paralelas.
* **MDVA-39986** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige o problema em que o usuário não consegue fazer um pedido no Admin no MacOS usando o navegador Safari.
* **MDVA-38447** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige dois problemas: em que o *Não visível individualmente* produtos filho configuráveis são retornados na resposta do GraphQL e otimizam a consulta MySQL para a consulta de produtos da GraphQL com filtro de categoria.
* **MDVA-40134** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o GraphQL não retorna produtos relacionados quando o Catálogo Compartilhado está habilitado.
* **MDVA-39935** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o GraphQL retorna produtos filho configuráveis desabilitados no nível do site.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que o erro *Chamada para uma função de membro getId()* é exibido na página de detalhes do pedido no Administrador.
* **MDVA-34948** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com consultas de longa execução, como `GET_LOCK`.
* **MDVA-39305** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Corrige o problema em que os clientes registrados não conseguem fazer logon com o Google ReCaptcha habilitado.
* **MDVA-37897** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema com um redirecionamento incorreto quando um cliente tenta adicionar produtos com opções do widget Recentemente visualizado.

## v1.1.0 {#v1-1-0}

* As categorias de patch foram introduzidas para melhorar a experiência do usuário e facilitar a pesquisa dos patches necessários para os clientes.
* O arquivo `patches.json` foi renomeado para `support-patches.json`.
* **MDVA-38799** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os produtos baixáveis não eram salvos após a criação de uma atualização de preparo.
* **MDVA-37592** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige o problema quando a classificação por preço não funciona corretamente para produtos com preço zero atribuído ao catálogo compartilhado.
* **MDVA-38827** (*para Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Corrige o problema em que os clientes recebem um email de remessa de pedido contendo uma mensagem de erro.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*para Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Corrige o erro ao salvar páginas do CMS: *Já existe um item com a mesma ID PAGE_ID*.
* **MDVA-34680** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Corrige o problema em que o tempo de criação da conta do cliente não é filtrado corretamente na grade de clientes.
* **MDVA-37068** (*para Adobe Commerce >=2.3.1 &lt;2.4.4*) - Corrige o problema em que a alíquota de imposto incorreta é exibida quando o carrinho de compras tem apenas produtos virtuais.
* **MDVA-38608** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que tabelas temporárias não são excluídas quando a reindexação não é concluída com êxito.
* **MDVA-38308** (*para Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Corrige os problemas relacionados à adição de vídeos [!DNL Vimeo] aos produtos.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige o problema em que o cliente não é levado para a página Confirmação de Pagamento ao usar o método [!DNL Paypal Payment Advanced].
* **MDVA-37082** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao salvar o estoque personalizado de produtos agrupados, fazendo com que o produto fique sem estoque no front-end.
* **MDVA-36572** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corrige o problema quando as atualizações do Aviso de Crédito não causam mais atualizações de reserva de produtos duplicadas no banco de dados.
* **MDVA-38132** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige o problema quando o painel Admin está inacessível devido a um erro de *muitos redirecionamentos*.
* **MDVA-38270** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema de informações de cartão-presente ausentes no total de pedidos no GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*para Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Corrige o problema ao adicionar um produto configurável ao carrinho por meio do GraphQL quando a ID do site não coincide com a ID da loja.
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
* **MDVA-30186** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Corrige o problema em que as opções de atributo são classificadas pelo valor da opção em vez da contagem de itens do atributo na resposta do GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*para Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Corrige o problema em que as opções personalizadas antigas permanecem após serem alteradas por meio da API.
* **MDVA-35773** (*para Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Corrige o problema em que o Total geral não era exibido como zero na fatura para pedidos com 100% de desconto.
* **MDVA-36833** (*para Adobe Commerce 2.4.2*) - Corrige o problema em que os resultados da pesquisa mostram números aleatórios de produtos por página após excluir alguns produtos do catálogo compartilhado.
* **MDVA-37182** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Corrige o problema ao obter resultados de pesquisa incorretos no [!DNL Elasticsearch] versão 6 e versão 7.
* **MDVA-36253** (*para Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que o subtotal incorreto é exibido no minicarrinho após a exclusão do item.
* **MDVA-36853** (*para Adobe Commerce 2.4.2*) - Corrige o problema de ausência de imagens ao carregar galerias de mídia grandes.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*para Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Corrige o problema de produtos agrupados ausentes nas páginas de categoria.
* **MDVA-36615** (*para Adobe Commerce 2.4.2*) - Corrige o problema com a contagem de produtos incorreta na grade de produtos de Administração.
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
* **MDVA-21095** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema quando uma consulta `INSERT INTO search_tmp` não termina após a atualização do valor do atributo em massa.
* **MDVA-23845** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema em que os modelos de email não podem ser visualizados depois que a minificação do JavaScript é habilitada.
* **MDVA-22026** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que a importação de produtos do arquivo CSV, incluindo imagens de URLs externas, falha.
* **MDVA-22383** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema em que salvar um produto leva muito tempo e a página é quebrada.
* **MC-41359** (*para Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Corrige o problema das configurações incorretas de parâmetros de cookies do SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*para Adobe Commerce 2.4.1*) - Corrige o problema em que o Page Builder lança o seguinte erro: *Ocorreu um erro ao iniciar o Page Builder. Consulte seu contato de suporte técnico.*
* **MDVA-35356** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema de retorno de crédito de armazenamento incorreto após o cancelamento de pedido parcialmente faturado.
* **MDVA-33289** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige o problema em que o código bruto do JavaScript é exibido na interface do usuário do endereço de cobrança durante o check-out se o [!DNL Google Tag Manager] estiver habilitado.
* **MDVA-35982** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os usuários administradores restritos a um site específico não podem criar uma remessa para o pedido feito no mesmo site.
* **MDVA-35155** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que é impossível comprar um pacote de produto se o título da opção foi alterado.
* **MDVA-35910** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema em que é impossível criar uma nova conta de cliente depois de desabilitar o Logon como funcionalidade do Cliente.
* **MDVA-34474** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao adicionar um produto à lista de requisições usando a API.
* **MDVA-34591** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema com um cálculo de desconto de regra de carrinho incorreto para *O Desconto de Quantidade Máxima é Aplicado a* e *Etapa de Quantidade de Desconto (Compre X)*.
* **MDVA-33704** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige o problema em que a opção de remessa *Coleta na loja* não é exibida, embora esteja configurada para estar disponível.
* **MDVA-34928** (*para Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Corrige o problema em que o carregador de página é exibido indefinidamente após o crédito da loja ser removido do pagamento.
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
* **MDVA-33344** (*para Adobe Commerce ^2.3.0*) - Corrige o problema em que a ID do conjunto de atributos padrão de entidade `rma_item` codificada é usada em vez do valor do banco de dados.
* **MDVA-34192** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige o problema em que é impossível modificar/especificar a data de nascimento do cliente usando o formato dd/mm/aaaa.
* **MDVA-34847** (*para Adobe Commerce ^2.3.0*) - Corrige a conversão do tipo de IDs de repositório em número inteiro para a condição SQL em coleções de administradores para Usuário Admin com permissões personalizadas.
* **MDVA-34886** (*para Adobe Commerce ^2.3.2*) - Corrige o problema em que a pesquisa não retorna resultados se o atributo de produto *weight* estiver configurado como pesquisável.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema de falha no pagamento [!DNL PayPal Payflow Pro] com o erro de formato da lista de parâmetros de redirecionamento.
* **MDVA-34023** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que o erro *Nenhuma entidade com addressId* é exibida aleatoriamente nos navegadores dos visitantes.
* **MDVA-32759** (*para Adobe Commerce >=2.3.1 &lt;2.4.3 com extensão B2B*) - Corrige o problema em que os Catálogos Compartilhados estão excluindo os preços de camada existentes.
* **MDVA-33482** (*para Adobe Commerce ^2.3.5*) - Corrige o problema em que a geração de um Aviso de Crédito contra uma fatura parcial resulta em imposto para a ordem total em vez de imposto para essa fatura parcial.
* **MDVA-33393** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o erro *Desde que countryId não exista*.
* **MDVA-33632** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fornece uma correção em que a mensagem de exceção *Este produto está indisponível* agora é exibida a um usuário administrador ao tentar reordenar um produto indisponível.
* **MDVA-34469** (*para Adobe Commerce >=2.4.1 &lt;2.4.2*) - Corrige o problema em que as mutações do GraphQL no carrinho de um cliente falham ao usar várias exibições de loja.
* **MDVA-33976** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*) - Corrige o problema em que o produto do pacote é mostrado Fora de Estoque na loja após remover a segunda opção do produto do pacote.
* **MDVA-33894** (*para Adobe Commerce >=2.4.0 &lt;2.4.1 com extensão B2B*) - Corrige vários problemas para a funcionalidade de Pedidos Rápidos, incluindo a adição e remoção de vários produtos e a diferenciação entre maiúsculas e minúsculas de SKU.
* **MDVA-27664** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema no formulário de registro do cliente, causando um erro na exibição: *ERRO - A Data de Nascimento não deve ser posterior à data de hoje.*
* **MDVA-33970** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que há um sinal de moeda incorreto no Memorando de Crédito quando o escopo do atributo de preço está definido como site.
* **MDVA-33992** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema de exibição incorreta de preços especiais B2B durante o check-out.
* **MDVA-34100** (*para Adobe Commerce >=2.3.4 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que uma conta da empresa não pode ser criada a partir da página de estrutura da empresa.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*para Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Corrige o problema com imagens duplicadas após a importação de produto de um arquivo CSV.
* **MDVA-33382** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige os problemas com a invalidação de indexadores após a remoção de produtos de uma categoria.
* **MDVA-28511** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige o problema em que não é possível concluir o check-out de [!DNL PayPal] se o campo Nome contiver determinados caracteres (como letras maiúsculas acentuadas).
* **MDVA-31519** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige o problema com tempos limite de espera no check-out de convidado quando uma regra de vendas do site inteiro está em uso.
* **MDVA-33281** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema em que há um erro fatal em `inventory:reservation:list-inconsistencies` devido ao tipo incorreto de parâmetro SKU.
* **MDVA-24201** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema em que os preços não refletem a regra de preço do carrinho agendado até que sejam reindexados manualmente.
* **MDVA-32694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Corrige o problema em que um usuário administrador não pode adicionar um produto a uma cotação negociável se ele estiver relacionado a uma loja que não é padrão.
* **MDVA-33516** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que a edição de um produto de pacote em uma lista de requisições leva a um erro.
* **MDVA-33975** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige vários problemas relacionados ao cálculo de preço em solicitações GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema com [!DNL PayPal] relatórios de liquidação que não estão disponíveis em **Relatórios** > **Vendas** > **[!DNL PayPal]** conforme esperado.
* **MCP-87** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Tempo de indexação aprimorado para categoria de produto e indexadores de estoque para perfis grandes.
* **MDVA-33106** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que as alterações de produto reagendadas são apagadas após a execução do comando cron `run`.
* **MDVA-19391** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema em que `analytics_collect_data` está gerando um erro devido a registros de descrição NULL na tabela `catalog_category_entity_text`.
* **MDVA-20376** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema com a *Nenhuma entidade com customerId = 1* erro no `exception.log` para clientes conectados após o posicionamento do pedido.
* **MDVA-23764** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige o erro em `JsFooterPlugin.php` que afeta a exibição de blocos dinâmicos.
* **MDVA-13203** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o erro *violação de restrição de integridade search_tmp_ table* aparece após uma reindexação completa.
* **MDVA-23426** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*) - Corrige o problema em que os emails de notificação enviados pelo Adobe Commerce contêm um corpo em branco com conteúdo sendo adicionado como anexo.
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

* **MC-38509** (*for Adobe Commerce 2.3.6, 2.4.1*) - Corrige o problema em que o botão *Criar uma Conta* permanece desabilitado após a correção de dados inválidos no formulário *Criar Nova Conta de Cliente*.
* **MDVA-31006** (*para Adobe Commerce 2.3.0, 2.3.1*) - Corrige o problema em que pedidos duplicados são exibidos depois de fazer um pedido usando o pagamento [!DNL Paypal Express].
* **MDVA-25602** (*para Adobe Commerce 2.3.0*) - Corrige o problema com o método de pagamento [!DNL PayPal Payflow Pro] e trata os cookies como `SameSite=Lax` por padrão no navegador Chrome 80 e redireciona a resposta da API para a página de logon do cliente.

## v1.0.10 {#v1-0-10}

Correções secundárias para versões de patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema em que a Regra de Preço do Carrinho com o cupom não se aplica via GraphQL quando a ação *Desconto de valor fixo para carrinho inteiro* é usada.
* **MDVA-30889** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que ocorre um erro após faturar um pacote com produtos virtuais e simples como opções.
* **MDVA-31791** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Melhora o desempenho da página do produto nos casos em que as regras de destino ou os produtos vinculados são usados.
* **MDVA-31168** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o arquivo CSV de exportação do produto não aparece e em que há um erro de alocação de memória.
* **MDVA-32313** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema em que os produtos configuráveis podem ser adicionados à lista de desejos com as opções de configuração incorretas.
* **MDVA-31759** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os produtos não são atualizados com os valores de atributo *suspenso* e *textarea* durante a importação de CSV.
* **MDVA-32012** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os códigos postais na Coreia e na Argentina não podem ser validados.
* **MDVA-31640** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Corrige o problema em que um preço especial não pode ser atualizado por meio da API REST.
* **MDVA-28651** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 com extensão B2B*) - Corrige o problema em que há problemas de desempenho ao carregar cotações negociáveis por meio da API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*para Adobe Commerce >=2.3.0 &lt;2.4.1 com extensão B2B*) - Corrige o problema em que um sinal de moeda incorreto é exibido na grade de Aviso de Crédito.
* **MDVA-31295** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os pontos de premiação não são calculados quando um pedido parcial é concluído e os itens são tributados.
* **MDVA-30112** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que, se o número de pedidos exceder o valor de *tamanho de grupo*, a Adobe Commerce considerará os pedidos com o status *pendente* como inconsistências.
* **MDVA-31150** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os saldos de cartão-presente e de crédito de loja não são retornados pela chamada da API Rest da Fatura da GET, quando a fatura foi lançada pela chamada da API Rest e o pedido foi parcialmente pago por contas de cartão-presente e de crédito de loja.
* **MDVA-30963** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema em que os resultados da filtragem de produtos definem para conter apenas valores especificados para o escopo *Todas as exibições de loja* no Admin, incluir produtos com valores substituídos no nível de exibição de loja.
* **MDVA-29954** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 com extensão B2B*) - Corrige o problema no qual os emails *Nova Solicitação de Registro de Empresa* e *Você foi vinculado a uma empresa* são enviados do endereço errado.
* **MDVA-28357** (*para Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Substitui o analisador padrão por um analisador personalizado com tokenizador de palavra-chave para o campo SKU no índice [!DNL ElasticSearch] para fazer com que as consultas de pesquisa curinga funcionem com SKUs que contenham um hífen (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o status de pedido personalizado foi alterado para *Processando* após a criação de remessa parcial usando WebApi.
* **MDVA-30428** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se esse produto estiver atribuído a uma fonte de estoque personalizada.
* **MDVA-30594** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que um pedido com vários endereços não podia ser salvo durante o check-out quando o FPT estava configurado.
* **MDVA-29148** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema ao criar um produto por meio de uma chamada de API. O atributo personalizado de produto do tipo `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multisseleção) não usará seu valor padrão se nenhum valor for fornecido na carga.
* **MDVA-30837** (*para Adobe Commerce >=2.3.1 &lt;2.3.5*) - Adição de uma definição de configuração *Incluir Imposto no Valor: Sim/Não* na configuração do método de Envio Gratuito. Quando *Incluir Imposto no Valor* estiver definido como *Sim*, o Valor Mínimo do Pedido será calculado como Subtotal + Imposto. Quando *Incluir Imposto no Valor* estiver definido como *Não*, o Valor Mínimo da Ordem será calculado como Subtotal
* **MDVA-25028** (*para Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Corrige o problema quando os pedidos feitos usando o [!DNL PayPal Payflow Pro] não são definidos como status de Suspeita de Fraude quando os filtros de fraude são acionados.
* **MDVA-31224** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*) - Melhora o desempenho da operação de reindexação `catalog_product_price` para produtos agrupados.
* **MDVA-31321** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige uma página em branco (erro) quando *Mostrar tudo* está selecionado. [!DNL Elasticsearch] retorna uma grande lista de ids de produtos. Nesse cenário, a cláusula order by é convertida em um formato SQL incorreto.
* **MDVA-30815** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que, quando você altera quantos resultados de pesquisa devem ser exibidos na página de resultados da pesquisa, o Adobe Commerce exibe uma página em branco. [!DNL Elasticsearch] agora exibe corretamente os resultados das páginas de categoria quando você altera o número de resultados da pesquisa exibidos por página.
* **MDVA-30782** (*para Adobe Commerce >=2.3.5 &lt;2.4.2*) - Corrige o problema em que o Bloco Dinâmico é exibido, independentemente da regra do carrinho.
* **MDVA-31021** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que existem problemas de desempenho no `module-catalog-import-export/Model/Import/Product/Option.php`. Se houver mais de ~100 mil registros na tabela `catalog_product_option`, um novo CSV com um único produto levará menos de 10 segundos para ser validado.
* **MDVA-31007** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema em que os atributos de endereço personalizados não são exibidos corretamente na página de detalhes do pedido na área minha conta e no back-end.
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
* **MDVA-28202** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Corrige o problema em que a Navegação em Camadas não filtra os produtos configuráveis corretamente quando o MSI é usado.
* **MDVA-28300** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que a solicitação GQL não reflete as alterações de preço das regras de preço do catálogo.
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
* **MDVA-28656** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Corrige o problema em que, se um pedido foi feito sem nenhuma informação de pagamento necessária (por exemplo, com 100% de desconto) e uma fatura foi criada para o pedido, o status do pedido muda para *Fechado* em vez de Concluído.
* **MDVA-30209** (*para Adobe Commerce 2.3.0 - 2.3.3-p1*) - Corrige o problema em que o grupo de clientes foi alterado para o padrão se o cliente atualizou suas informações de conta.
* **MDVA-30123** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que os rótulos de opção de atributo não são traduzidos corretamente para consultas do GraphQL.
* **MDVA-29996** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que, após habilitar a permissão de categoria, a página de categoria não é armazenada em cache pelo Cache de Página Inteira.
* **MDVA-30164** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Corrige o problema em que os registros de clientes não podem ser exportados da grade Clientes se existirem atributos de clientes personalizados.
* **MDVA-30444** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige o problema em que nenhum email de confirmação é enviado para pedidos feitos usando o GraphQL.
* **MDVA-30490** (*para Adobe Commerce 2.3.4 - 2.3.5-p2*) - Corrige o problema em que a comparação de produtos lança a página de erro 500 se um dos produtos tiver uma descrição curta vazia.
* **MDVA-30232** (*para Adobe Commerce >=2.3.1 &lt;2.4.1*) - Corrige o problema em que não é possível reordenar se o pedido original contiver um cartão-presente.
* **MDVA-29965** (*for Adobe Commerce >=2.3.3 &lt;2.4.0*) - Corrige o problema em que os clientes obtêm o erro Chave de Formulário Inválida ao adicionar um produto ao carrinho.
* **MDVA-30008** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema B2B em que não é possível fazer pedidos por meio da API de Administração para um produto que está em um catálogo público.
* **MDVA-22469** (*para Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Corrige o problema em que, após a atualização para o Adobe Commerce 2.3.3, o Page Builder não está funcionando no painel Administrador e alguns arquivos JS e CSS não estão carregando.
* **MC-35984** (*for Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema em que os comerciantes não podiam interagir com nenhum elemento da página Devoluções após criar um rótulo de remessa para uma Autorização para Devolução de Mercadoria (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*para Adobe Commerce 2.3.0 - 2.3.4*) - Corrige o problema com o método de pagamento [!DNL PayPal Payflow Pro] e trata os cookies como `SameSite=Lax` por padrão no navegador Chrome 80 e redireciona a resposta da API para a página de logon do cliente.
* **MDVA-26694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Corrige o problema que fazia com que os caches de produtos e catálogos expirassem diariamente, embora estivesse sendo agendado para expirar de forma diferente.
* **MDVA-27825** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige o problema em que a exportação de grandes quantidades de dados falhava devido a vazamento de memória.
* **MDVA-29085** (*para Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Corrige o problema B2B em que nenhum email de nova empresa necessário é enviado se uma empresa é criada pela API.
* **MDVA-29344** (*para Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Corrige o problema em que o Page Builder fica preso após copiar o texto de um elemento de cabeçalho para um elemento de texto.
* **MDVA-29835** (*para Adobe Commerce >2.3.1 &lt;2.4.2*) - Corrige o problema em que os pedidos de cartão-presente continham dois códigos em vez de um.
* **MDVA-30052** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema no conteúdo particular (armazenamento local) não sendo preenchido corretamente, o que resultou em problemas de desempenho.
* **MDVA-30131** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema na navegação em camadas, em que o valor *No* para atributos de produto do tipo booleano não era incluído na navegação em camadas se [!DNL Elasticsearch] fosse usado como um mecanismo de pesquisa.
* **MDVA-35514** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema na criação de um rótulo de remessa e na adição de produtos encomendados a um pacote na janela modal Criar Pacotes.
