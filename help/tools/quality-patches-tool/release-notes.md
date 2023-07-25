---
title: Notas de versão
description: Saiba mais sobre os patches disponíveis para o Adobe Commerce e os problemas que eles resolvem.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 7649f4ffb0a04053d9a674aae7c29eb09ed02006
workflow-type: tm+mt
source-wordcount: '13737'
ht-degree: 0%

---

# Notas de versão

A variável [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) O fornece patches individuais desenvolvidos pela Adobe e pela comunidade Magento Open Source. Ela permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce ou Magento Open Source. Você pode aplicar patches a projetos Adobe Commerce e Magento Open Source, independentemente de quem os desenvolveu. Por exemplo, você pode aplicar uma correção desenvolvida pela comunidade para projetos do Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) para obter instruções sobre como aplicar patches aos projetos Adobe Commerce ou Magento Open Source. Consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no Guia de Atualização de Software para revisar uma lista completa de patches lançados.

>[!INFO]
>
>Para obter informações sobre [!DNL quality patches] criado pela Comunidade para o Magento Open Source, consulte a [notas de versão](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que o endereço de envio padrão na etapa de envio do check-out é preenchido automaticamente com um endereço de entrega na loja selecionado anteriormente.
* **ACSD-52041** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a mensagem de erro: *[ERRO] [!DNL Page Builder] O era renderizado por 5 segundos sem liberar bloqueios.* aparece no navegador Chrome ao salvar o conteúdo editado com [!DNL Page Builder].
* **ACSD-52095** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que a variável `manage_stock` O valor foi incorretamente definido como 0 no arquivo CSV após a exportação do produto.
* **ACSD-51358** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que a remoção de uma atualização agendada sem uma data final leva à remoção de outras atualizações agendadas para a mesma entidade.
* **ACSD-48070** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que a edição de uma atualização programada aciona uma exceção.
* **ACSD-51890** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que a variável [!UICONTROL Submit review] pode ser clicado várias vezes sem [!DNL Google reCAPTCHA] Validação da v3.
* **ACSD-51984** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que estava desmarcado *[!UICONTROL Use Default Value]* e *[!UICONTROL non-default product field]* Os valores de não são salvos para a segunda exibição de site, loja e loja.
* **ACSD-52398** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o erro *A quantidade solicitada não está disponível* que ocorre ao tentar atualizar a quantidade de um produto agrupado no carrinho na loja.
* **ACSD-52786** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que uma condição de regra de catálogo *O SKU é* se aplica a todos os produtos que começam com o SKU fornecido.
* **ACSD-52921** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - corrige o problema em que ocorre um erro interno se solicitar detalhes do carrinho da GraphQL quando há um produto configurável indisponível no carrinho.
* **ACSD-51683** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que uma opção personalizável não pode ser adicionada ao carrinho usando o GraphQL.
* **ACSD-52133** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que uma conta do cliente não pode ser salva após uma atualização.
* **ACSD-52202** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a quantidade comercializável do estoque padrão muda incorretamente para 0 quando um estoque não padrão é alterado para 0 na execução do pedido.
* **ACSD-51265** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema com `catalog_product_price` reindexação do desempenho quando há muitos produtos agrupados no sistema.
* **ACSD-52831** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - corrige o problema em que os clientes não podem fazer pedidos de cotação negociáveis quando [!DNL Google reCAPTCHA v3 Invisible] está ativado.
* **ACSD-51845** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - corrige o problema em que os produtos subsequentes com preços de nível e conjuntos de atributos diferentes não podem ser atualizados por meio da API REST em massa assíncrona.
* **ACSD-52815** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a entrada para o campo de quantidade de uma fonte não padrão suporta apenas até 6 dígitos, ao contrário de 8 para um estoque padrão.
* **ACSD-51149** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que a Exportação de importação agendada com Permissões de catálogo ativadas invalida os indexadores e, em seguida, libera o cache pelo cron.
* **ACSD-50815** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - corrige o problema em que a quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupado.
* Versões atualizadas para ACSD-47803.
* Atualização do título para ACSD-51892.
* Atualização do ACSD-51379.
* Atualização do ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um usuário administrador não é redirecionado corretamente após selecionar uma visualização de loja ao criar um novo pedido no Admin.
* **ACSD-50813** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que o administrador não podia adicionar produtos empacotados contendo uma barra na SKU com o [!UICONTROL Add Products by SKU] para a ordem do administrador.
* **ACSD-51630** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que uma grande quantidade de mensagens do sistema atrasa o download de páginas de administrador.
* **ACSD-51853** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corrige o problema em que os estilos de texto copiados não são aplicados ao usar o [!UICONTROL Page Builder].
* **ACSD-52160** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que o resultado da validação do produto em relação à regra de preço do carrinho não era avaliado corretamente com base na condição de regra &quot;Se um item for ENCONTRADO/NÃO ENCONTRADO no carrinho com Todas/Qualquer uma dessas condições é verdadeira&quot;.
* **ACSD-51636** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - corrige o problema em que o administrador da empresa não pode adicionar novos usuários na seção conta do cliente, apesar de ter todas as funções e permissões necessárias.
* **ACSD-51739** (para Adobe Commerce >=2.4.6 &lt;2.4.7) - Corrige o problema em que um erro é retornado ao `structure_id` é solicitado em uma solicitação do CompanyTeam GraphQL.
* **ACSD-51857** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que o desempenho lento do `aggregate_sales_report_bestsellers_data` relatório cron sobre sales_order grande e `sales_order_item` as tabelas do banco de dados eram devidas à forma como a consulta de dados principal era gravada.
* **ACSD-48448** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que há um problema de condição de corrida ocorrendo durante os cancelamentos de pedidos, o que causa uma entrada duplicada no `inventory_reservation` tabela.
* **ACSD-52689** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6) - Corrige o problema em que as imagens não podem ser carregadas no armazenamento do Amazon S3 usando a API REST.
* **B2B-2674** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Adicione o recurso de cache à consulta do GraphQL 1customAttributeMetadata1.
* Adição de novas versões para ACSD-44938.
* Adição de requisitos para o ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Corrige o comando de reversão de banco de dados para um caso em que o despejo de banco de dados contém acionadores e um *delimitador* Comando SQL.
* **ACSD-50512** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige a *Erro: o link disponível para download não está relacionado ao produto. Verifique o link e tente novamente.* erro que ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável.
* **ACSD-50949** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que o filtro de preço na pesquisa avançada não retorna resultados adequados quando usado com o filtro SKU.
* **ACSD-51645** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o erro lançado ao salvar uma nova Regra de preço do carrinho se a extensão `Magento_OfflineShipping` está desativado.
* **ACSD-50895** (para Adobe Commerce >=2.4.5 &lt;2.4.7) - Corrige o problema em que [!DNL Google Analytics] 3 tags GTM não são acionadas se [!DNL Google Analytics] 4 GTM não está configurado.
* **ACSD-51102** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que uma regra de catálogo aplicada a um grande número de produtos não é indexada corretamente quando a regra é habilitada por uma atualização agendada.
* **ACSD-50368** (para Adobe Commerce e Magento Open Source >= 2.4.3 &lt;2.4.5) - Corrige o problema em que a `group_id` é ignorado quando um cliente é criado por meio da API REST assíncrona ou da API REST assíncrona em massa.
* **ACSD-51497** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corrige o problema em que um cliente não pode classificar uma página de catálogo por Atributo personalizado do tipo de lista suspensa.
* **ACSD-51408** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt; 2.4.7) - Corrige o problema em que o status do item do pedido é definido incorretamente como *[!UICONTROL Backordered]*.
* **ACSD-51735** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que o status do item do pedido é definido incorretamente como *[!UICONTROL Ordered]* quando o estoque do produto é *0*.
* **ACSD-51792** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que uma página não tem o evento de impressão quando [!DNL Google Tag Manager] 4 está ativado.
* **ACSD-51471** (para Adobe Commerce >=2.4.3 &lt;2.4.7) - Corrige o problema em que um usuário administrador não pode salvar uma atualização agendada para um produto agrupado que usa um produto simples que tem uma atualização agendada.
* **ACSD-51700** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o erro que ocorre ao alternar as exibições da loja em uma página de edição de produto baixável no administrador.
* **ACSD-51120** (para Adobe Commerce >=2.3.7 &lt;2.4.3) - Corrige o problema em que o cache de solicitações do GraphQL GET não é limpo para páginas CMS que contêm blocos CMS atualizados por meio de uma atualização de preparo.
* **ACSD-51240** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - Corrige o problema em que o arquivo carregado estava ausente se o registro fosse feito por meio do formulário de registro da empresa.
* **ACSD-51907** (para Adobe Commerce >=2.4.2 &lt;2.4.3) - Corrige o problema em que um usuário administrador restrito não consegue criar um memorando de crédito com um reembolso offline.
* **ACSD-52148** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que a variável [!DNL Google V3 reCAPTCHA] Ocasionalmente, o logon do administrador falha.
* **ACSD-51431** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o status de um indexador é *trabalhando* mesmo se não houver novas entradas no changelog.
* **ACSD-51892** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema de desempenho em que os arquivos de configuração são carregados várias vezes durante a implantação.
* ACSD-51114 obsoleto.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema em que a variável [!UICONTROL Page Builder's] vários erros impedem que o administrador salve um produto sem permissões de conteúdo.
* **ACSD-51305** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que os produtos secundários configuráveis esgotados não estão disponíveis na resposta do GraphQL.
* **ACSD-50621** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que [!UICONTROL Tier Prices] para sites diferentes no catálogo compartilhado não ficam visíveis ao tentar editá-los em um ambiente de vários sites.
* **ACSD-51041** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Melhora o desempenho do indexador de preços.
* **ACSD-51379** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que as alterações eram feitas no conteúdo de texto da página por meio de [!UICONTROL Page Builder] não são salvas.
* **ACSD-49480** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que apenas uma regra de preço do carrinho é aplicada ao carrinho.
* **ACSD-51230** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - corrige o problema em que a conta do cartão-presente é excluída quando um reembolso parcial de um produto simples é processado de um pedido.
* **ACSD-51238** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corrige o problema em que a origem do inventário é removida ao atualizar produtos configuráveis e editar o preço.
* **ACSD-50794** (para Adobe Commerce >=2.4.1 &lt;2.4.7) - Corrige o problema em que a mensagem de presente ou os detalhes de invólucro do presente não são atualizados no banco de dados ao removê-lo pelo GraphQL.
* **ACSD-51528** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que a variável *x_forwarded_for* a coluna tem valores nulos na variável *sales_order* tabela.
* **ACSD-50849** (para Adobe Commerce >=2.4.4 &lt;2.4.6) - corrige o problema em que adicionar um novo produto à categoria após limpar o cache resulta em uma incompatibilidade de posições e seleções dos produtos existentes.
* **ACSD-51294** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema no qual o preço, a quantidade, o imposto, a remessa e a receita do GTM/GA são enviados como uma sequência de caracteres para [!DNL Google Analytics] e GTM.
* **ACSD-51204** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um produto totalmente vendido não retorna no estoque após a criação de um memorando de crédito.
* **ACSD-51291** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Corrige o problema em que o administrador restrito com acesso a um site pode adicionar imagens/vídeos ao produto atribuído a vários sites.
* Adição de novas versões para ACSD-50336.
* Substituídos os patches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Corrige o problema em que o Recaptcha v2 não é recarregado após o envio de um pagamento com falha.
* **ACSD-50817** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Otimiza o trabalho do Cron `sales_clean_quotes` para ser executado mais rápido.
* **ACSD-49392** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corrige o problema em que o status do pedido muda para fechado após uma restituição parcial para um produto agrupado.
* **ACSD-51036** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - corrige o problema em que as condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição das informações de status de envio no [!UICONTROL Items Ordered] tabela.
* **ACSD-50858** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Melhora o desempenho para carregar o conteúdo dos banners.
* Adição de novas versões para MDVA-39305-v2, ACSD-45169.
* Atualização dos patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (para Adobe Commerce e Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Corrige o problema em que os emails de alerta do produto não são enviados quando um produto está de volta ao estoque ou o preço é alterado.
* **ACSD-50367** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - corrige o problema em que a exportação de endereço do cliente não funciona quando um atributo de endereço do cliente de seleção múltipla sem valores é criado.
* **ACSD-49877** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a reprodução automática de vídeo não funciona em dispositivos móveis [!DNL Safari] quando o vídeo é vinculado diretamente a um arquivo de vídeo remoto e não a um serviço de streaming.
* **ACSD-50165** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o erro *O arquivo não pode ser excluído. Aviso!unlink: esse arquivo ou diretório não existe* ao limpar o cache de JS/CSS do Admin.
* **ACSD-49737** (para Adobe Commerce e Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Corrige o problema em que um cupom é marcado incorretamente como usado após uma falha no pagamento por cartão.
* **ACSD-50814** (para Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corrige o problema em que um usuário administrador não consegue criar um memorando de crédito.
* **ACSD-50116** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que um usuário administrador não consegue criar uma regravação de URL para subcategorias de nível 3 ou inferior.
* **ACSD-49513** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5) - Corrige o problema em que a sincronização do armazenamento remoto falha devido a arquivos de 0 bytes.
* **ACSD-46683** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corrige o problema no qual o preço de envio aparece *Ainda não calculado*.
* **ACSD-49129** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que a variável *[!UICONTROL content]* o atributo (código de imagem base64) não é retornado em `rest/V1/products/sku/media` respostas da API de mídia do produto.
* **ACSD-50276** (para Adobe Commerce >=2.4.0 &lt;2.4.7) - corrige o problema em que o formulário de registro do cliente não funciona na loja se um atributo de cliente de seleção múltipla for criado.
* **ACSD-50527** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o erro que ocorre ao salvar uma página com um bloco dinâmico vazio.
* **ACSD-49973** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Melhora o desempenho da busca de produtos agrupados por meio do GraphQL.
* **ACSD-51114** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um produto aleatório desaparece de catálogos grandes quando a indexação assíncrona está ativada. Melhora o desempenho da reindexação assíncrona para catálogos grandes.
* **B2B-2598** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Adicione o recurso de cache ao [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], e [!UICONTROL storeConfig] consultas do GraphQL.
* Adição de novas versões para MDVA-42806, ACSD-48627, ACSD-46815.
* Atualização de metadados de patches para ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corrige o problema em que um email pronto para coleta é enviado pela API quando o pedido não está pronto para coleta.
* **ACSD-49822** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que as atualizações no [!UICONTROL Requisition List] página não são refletidas na variável [!UICONTROL Print Requisition List].
* **ACSD-48771** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema de atualização do tipo de conteúdo de bloco de coluna a partir da versão mais antiga [!DNL Page Builder] versões.
* **ACSD-49464** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que faturas, remessas e avisos de crédito não são movidos de volta do arquivo quando a orderId é diferente.
* **ACSD-49773** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - corrige o problema em que a exportação de produtos falha quando o AWS S3 é usado como armazenamento remoto.
* **ACSD-49748** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - Corrige o problema em que os convites não podem ser enviados.
* **ACSD-49502** (para Adobe Commerce >=2.4.3 &lt;2.4.7) - Corrige o problema em que o link baixável não é atualizado corretamente após uma atualização de preparo ser aplicada ao produto baixável.
* **ACSD-49527** (para Adobe Commerce >=2.4.2 &lt;2.4.7) - Corrige o problema em que as funções da empresa no GraphQL não exibem a paginação corretamente.
* **ACSD-49706** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que o valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado.
* **ACSD-49835** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que o valor da caixa de seleção Usar padrão não é salvo corretamente em um nível de armazenamento para um atributo de seleção múltipla.
* **ACSD-49898** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a grade de produtos lança uma exceção quando um produto agrupado tem um preço especial superior a 1000.
* **ACSD-50234** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.5) - Corrige o problema com o nome de cliente errado no email de confirmação se fizer um pedido com [!DNL PayPal].
* **ACSD-49960** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - corrige o problema em que a filtragem por data não funciona para a grade de pedidos do cliente.
* **ACSD-49849** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - corrige o problema em que o email do cliente foi substituído por [!DNL PayPal] ao fazer um pedido com o [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - corrige o problema em que a estrutura e os preços do catálogo compartilhado geram um erro no Administrador quando os produtos têm aspas simples ou duplas no SKU.
* **ACSD-49970** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige a manipulação incorreta de erros do GraphQL quando [!DNL New Relic] relatórios está ativado.
* **ACSD-50260** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que os resultados da pesquisa de produtos do GraphQL são limitados a apenas 10.000 resultados.
* **ACSD-48813** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que a pesquisa não mostra resultados relevantes com base no peso da pesquisa dos atributos.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.3) - Corrige o problema em que uma regra de preço de catálogo criada com base no atributo Sim/Não não considera o escopo selecionado.
* **ACSD-47704** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - corrige o problema em que o produto incluído mostra somente o preço dos produtos em estoque.
* **ACSD-49370** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que a variável *Data e hora* atributo de produto tem um *FilterMatchTypeInput* digite no esquema do GraphQL.
* **ACSD-48807** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - corrige o problema em que as análises de produtos do cliente não são filtradas pela loja via GraphQL.
* **ACSD-49433** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que o valor padrão é mostrado como subtotal no carrinho para cartão-presente com um valor aberto.
* **ACSD-48866** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que ocorre um erro ao solicitar o feed RSS para categorias.
* **ACSD-48784** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - corrige o problema em que os preços do segmento do cliente são armazenados incorretamente em cache entre os grupos de clientes.
* **ACSD-48857** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um usuário não consegue salvar alterações após editar com o Page Builder.
* **ACSD-49065** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - corrige o problema em que os itens de cotação não estão visíveis no Admin se atribuídos apenas ao estoque personalizado.
* **ACSD-49179** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - corrige o problema em que o Relatório de pedidos mostra valores incorretos no caso de moedas diferentes para lojas diferentes.
* **ACSD-49286** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corrige o problema em que um produto é adicionado duas vezes ao carrinho quando vários widgets de produto estão presentes na página.
* **ACSD-49574** (para Adobe Commerce >=2.4.4 &lt;2.4.7) - Adiciona a funcionalidade de suportar atualizações de produto de cartão-presente em um carrinho por meio do GraphQL.
* Correção atualizada: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (para Adobe Commerce >=2.4.1 &lt;2.4.7) - Corrige o problema em que o endereço de entrega padrão é usado em vez de um novo ao fazer um pedido usando uma cotação negociável.
* **ACSD-48059** (para Adobe Commerce >=2.3.7 &lt;2.4.7) - corrige o problema em que os comerciantes não podem salvar o &quot;[!UICONTROL Match product by rule]&quot; na categoria.
* **ACSD-48216** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corrige o problema em que [!UICONTROL AUTO_INCREMENT] do [!UICONTROL inventory_source_item] a tabela aumenta no [!UICONTROL UPDATE] operação.
* **ACSD-47908** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corrige o erro &quot;Um valor menor ou igual a 0 é esperado&quot; ao selecionar a origem e a quantidade na etapa de envio durante a finalização da compra.
* **ACSD-49497** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que um pedido permanece no estado de processamento após o envio e um reembolso parcial é aplicado.
* **ACSD-48694** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Corrige o problema em que o erro &quot;Alteração de estado inválida solicitada&quot; impede que um cliente faça um pedido.
* **ACSD-49013** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - corrige o problema em que a confirmação por email não é traduzida para o local do site ao criar clientes usando a API em massa.
* **ACSD-48164** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que um administrador restrito não pode salvar um valor no nível do site.
* **ACSD-48404** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que &quot;Lembrar paginação de categoria = Sim&quot; causa um erro ao pressionar o botão Voltar do navegador.
* **ACSD-48634** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige erros de JS em uma página de atualização em preparo quando &quot;[!UICONTROL Google Analytics Content Experiments]&quot; está ativado.
* **ACSD-49042** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que um produto com backorder infinito não pode ser encomendado na Loja.
* Patches atualizados: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (para Adobe Commerce e Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - corrige o problema em que as notificações de queda de preço nem sempre são enviadas devido ao armazenamento em cache no nível do aplicativo.
* **ACSD-48661** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que, se o limite de crédito da empresa for maior que 999, o separador de vírgulas impedirá o salvamento da empresa devido a um erro de validação.
* **ACSD-48773** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - corrige o problema em que o modelo de email de pontos de premiação é retirado do armazenamento errado.
* **ACSD-48587** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corrige o problema em que os caracteres especiais de HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes.
* **ACSD-48212** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que a importação de produtos atribui o produto à origem errada.
* **ACSD-47988** (para Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corrige o problema em que a exportação de produtos elimina as tags HTML da descrição de produto do page builder.
* **ACSD-48366** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - corrige o problema em que a imagem do produto não é exibida no modelo de email Voltar para o Stock.
* **ACSD-48417** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corrige o problema em que um erro SQL aparece após criar uma alteração de agendamento para um produto e salvar outro produto.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que a reindexação de preço do produto não funciona se o produto do pacote não estiver atribuído a nenhum site.
* **ACSD-48262** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que os produtos não estão visíveis no front-end quando a configuração &quot;Permitir todos os produtos por página&quot; está definida como Sim.
* **ACSD-48293** (para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corrige o problema em que os produtos compostos ficam sem estoque quando os produtos secundários que foram vendidos são devolvidos ao estoque.
* **ACSD-47520** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - corrige o problema em que os clientes perdem pontos de recompensa quando um memorando de crédito é criado.
* **ACSD-48044** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - corrige o problema em que a aplicação de vários cartões-presente a um único pedido com vários envios impede que os pedidos sejam feitos.
* **ACSD-48300** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que um retorno não pode ser criado se o produto configurável for removido.
* **ACSD-47910** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige a emissão de pedidos, faturas, remessas e avisos de crédito ausentes nas respectivas grades de entidade.
* **ACSD-47292** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que os produtos empacotados esgotados não estão disponíveis na resposta da GraphQL, se &quot;mostrar produtos esgotados&quot; estiver definido como Sim.
* **ACSD-48234** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que o resultado da pesquisa no catálogo mostra uma contagem de itens de categoria incorreta quando a opção &quot;mostrar indisponível&quot; está ativada.
* **ACSD-48313** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Corrige o problema em que a coluna &quot;configurable_variation&quot; não é analisada se o valor do atributo contiver uma vírgula. O mesmo algoritmo de análise é usado para &quot;additional_attributes.
* **ACSD-48627** (para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corrige o problema em que o produto configurável esgotado causa um erro ao enviar uma solicitação do GraphQL para obter detalhes do carrinho.
* Patch atualizado: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que URLs amigáveis para SEO não são gerados para produtos que têm o *url_key* atributos substituídos no nível da exibição de armazenamento.
* **ACSD-46865** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a grade Remessa e Aviso de crédito não é preenchida quando a indexação assíncrona está ativada.
* **ACSD-47004** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que o IVA não é aplicado a um endereço de faturamento sem uma ID de IVA.
* **ACSD-47803** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que as amostras de produtos configuráveis e indisponíveis são exibidas.
* **ACSD-47137** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Melhora a velocidade de carregamento da galeria de imagens quando a pasta pub/media é muito grande.
* **ACSD-46770** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que emails de pedido de administrador são enviados mesmo quando a variável *Confirmação de pedido por email* está desmarcada.
* **ACSD-47955** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que o GraphQL não exibe o desconto do carrinho corretamente.
* **ACSD-46617** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a variável *Prosseguir para o check-out* fica esmaecido mesmo se o subtotal for maior que o valor configurado *Valor Mínimo do Pedido*.
* **ACSD-47079** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corrige o problema em que o status do estoque de produtos compostos (agrupados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado por meio da API REST POST /rest/V1/inventory/source-items.
* **ACSD-47336** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Correções *Algo deu errado.* erro ao dispensar notificações no Administrador do Commerce.
* **ACSD-47559** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a área Visualizar modelo de email não estava totalmente visível.
* **ACSD-47920** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que os pedidos podem ser feitos por meio da API Rest como um usuário convidado mesmo quando a variável *Permitir check-out de convidado* está desativado.
* Patches substituídos: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que um administrador com acesso restrito a um escopo específico não pode excluir análises de produtos.
* **ACSD-47107** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Corrige o problema em que o desconto da Regra de preço de catálogo é aplicado às opções de produto personalizadas.
* **ACSD-47232** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - corrige o problema em que os cupons com condições de peso total não podem ser aplicados no Admin.
* **ACSD-46519** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6) - Corrige o problema em que a solicitação categoryList do GraphQL retorna uma contagem de produto incorreta para uma categoria âncora.
* **ACSD-47027** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige uma solicitação lenta de updateCompanyRole GraphQL.
* **ACSD-47666** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a função de filtro não funciona na grade Admin > Sistema > Permissões > Funções de usuário > uma função > Usuários de função.
* **ACSD-47497** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a guia Serviços não estava visível na Configuração no Administrador.
* Correção atualizada: ACSD-47743.
* Patches substituídos: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3) - Corrige a _Tentando acessar o deslocamento da matriz no valor do tipo bool_ erro ao acessar certos caminhos de categorias não existentes para produtos conhecidos no PHP 7.4.
* **ACSD-47332** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o cron falha com um erro que é relatado somente ao ser executado entre 00:00 e 00:59 UTC.
* **ACSD-47280** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que a desativação do recurso de catálogo compartilhado em um escopo específico não funciona corretamente.
* **ACSD-47106** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que um valor não pode ser salvo em um novo atributo personalizado em uma página de criação de empresa.
* Correção atualizada: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige o problema em que um usuário recebe um erro ao atribuir um grande número de fontes de produtos.
* **ACSD-46856** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Melhora os preços de nível de atualização de desempenho via Sistema > Configuração > Importação > Advanced Pricing.
* **ACSD-46541** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corrige o problema em que um usuário administrador não pode criar um memorando de crédito se um item de pedido for excluído.
* **ACSD-46581** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o total de imposto estimado não é atualizado após selecionar um país no carrinho de compras.
* **ACSD-46618** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corrige o problema em que o widget lista de produtos mostra preços em cache incorretos para um cliente conectado.
* **ACSD-46674** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - corrige o problema em que as opções personalizadas de um tipo de imagem são exibidas como HTML nos emails do cliente.
* **ACSD-46988** (para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corrige o problema em que a solicitação de API &#39;currency&#39; do GraphQL retorna valores NULL para uma moeda personalizada.
* **ACSD-47076** (para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) - Corrige o problema em que os vídeos do Vimeo não podem ser reproduzidos na loja.
* **ACSD-45071** (para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Corrige o problema em que a origem padrão é adicionada ao produto durante a importação.
* **AC-3023** (para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Atualize o esquema DHL para a versão mais recente 10.0.
* Patches atualizados: MDVA-42584.
* Patches substituídos: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que um usuário recebe um status de pedido incorreto quando reembolsado usando o crédito da loja.
* **ACSD-46703** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige o problema em que não é possível arrastar e soltar opções personalizadas em uma página de edição de produto.
* **ACSD-44851** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema em que uma categoria com subcategorias não pode ser aberta ou expandida.
* **ACSD-46815** (*para Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6*) - Corrige o problema em que a solicitação da árvore de categoria é limitada a 20 categorias.
* **ACSD-45675** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corrige o problema em que a exportação de produtos usa nomes de categoria da *Visualização da loja padrão* âmbito de aplicação.
* **ACSD-46869** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corrige o problema em que um produto configurável em um carrinho não é atualizado por meio de uma *API REST PUT* solicitação sem alterar a quantidade do produto.
* **MDVA-42768-V2** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o produto Configurável exibe o preço normal como *0* quando *Exibir sem estoque* é *Sim*.
* Patches atualizados: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Patch obsoleto: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que a solicitação da árvore de categoria é limitada a 20 categorias.
* **ACSD-45781** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.2*) - Corrige o problema em que o campo de pesquisa frontal da loja não é exibido em dispositivos móveis.
* **ACSD-46192** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;2.4.5*) - Corrige o problema com o uso do `async/bulk/V1/configurable-products/bySku/options` terminal.
* **ACSD-46404** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige o problema em que um usuário administrador não consegue fazer logon após atualizar para a versão 2.4.4.
* Patches atualizados: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que uma mutação de produto do GraphQL para uma loja específica retorna todas as variantes configuráveis, incluindo aquelas não atribuídas à loja solicitada.
* **ACSD-46146** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que dois emails de confirmação de pedido são enviados após a inserção de um pedido do administrador.
* **ACSD-45255** (*para Adobe Commerce >=2.4.3 &lt;2.4.6*) - Corrige uma exceção na página Relatório de baixo estoque para um usuário administrador restrito.
* **ACSD-45488** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6*) - Corrige o problema em que um produto configurável com várias origens não é retornado automaticamente para o In Stock.
* **ACSD-45754** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema em que os pontos de premiação não são adicionados após aplicar um cupom ao carrinho.
* **ACSD-45849** (*para Adobe Commerce >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo.
* **ACSD-45257** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema em que o GraphQL não exibe um desconto de carrinho corretamente.
* **ACSD-44938** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que `VAT_ID` não pode ser aplicado em uma solicitação GraphQL para um usuário convidado.
* Patches atualizados: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige o problema em que a quantidade em estoque de um produto virtual é calculada incorretamente após a criação de um memorando de crédito.
* **ACSD-43887** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando as Ordens de compra para empresas estão ativadas.
* **ACSD-45143** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que a variável `setShippingAddressesOnCart` a mutação não permite definir o código de região numérico como *região*.
* **ACSD-44591** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6*) - Corrige o erro que ocorre quando um pedido é feito sem confirmação CAPTCHA.
* **ACSD-45520** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corrige o problema em que as opções de amostra não são pré-selecionadas na página de detalhes do produto quando um usuário edita produtos configuráveis do carrinho de compras.
* **ACSD-45169** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6*) - Corrige o problema em que [!DNL Visual Merchandiser] não exibe o estoque e o preço corretos de um produto configurável após a aplicação de uma atualização de preparo.
* **ACSD-45424** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.6*) - Corrige o problema em que uma compensação de reserva incorreta é criada após uma restituição parcial (aviso de crédito).
* **MDVA-42807** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige o problema em que o sinal de moeda personalizado não é exibido na frente da loja.
* Patches atualizados: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os totais de pedido no relatório de Pedidos são calculados incorretamente para o usuário administrador restrito.
* **MDVA-44940** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o erro de SQL que ocorre ao salvar a categoria do Admin.
* **MDVA-44562** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Corrige o problema em que a ID de armazenamento não padrão para itens de cotação é substituída pela ID de armazenamento padrão, apesar da solicitação do GraphQL se originar da exibição de armazenamento não padrão.
* **MDVA-43167** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que a ação em massa da grade de pedido do administrador não se aplica a várias páginas quando o usuário administrador seleciona todos os pedidos.
* **MDVA-44044** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Corrige o problema em que um produto não é exibido na página de categoria depois de ser atribuído a um novo site.
* **MDVA-42509** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.4*) - Corrige o problema em que não era possível carregar um CSV para um pedido rápido, resultando em uma *Não foi possível enviar o cookie* erro.
* Patches atualizados: MDVA-41061, MDVA-42584.
* O prefixo para o novo [!DNL Quality Patches Tool] os patches serão alterados de *MDVA* para *ACSD* devido a alterações internas no processo.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que um item adicional não pode ser adicionado ao carrinho quando a quantidade mínima do item já está no carrinho.
* **MDVA-44887** (*para Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corrige a *SyntaxError não capturado: token &#39;const&#39; inesperado* erro no painel Admin.
* **MDVA-43718** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Correções *O consumidor não está autorizado a acessar %resources.* erro que aparece ao acessar um catálogo compartilhado de uma integração personalizada.
* **MDVA-44660** (*para Adobe Commerce e Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Corrige o problema em que o caractere de acento grave ``` ` ``` não pôde ser usado para o nome e sobrenome de um cliente.
* **MDVA-40896** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige a *Erro: TypeError: Argumento 3 transmitido para Magento* erro na API de produto assíncrona em massa.
* **MDVA-38559** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige a *API /V1/customers/search* erro para clientes com mais de uma assinatura.
* **MDVA-44533** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.4*) - Corrige o problema em que o desconto é aplicado incorretamente a um produto filho de pacote.
* Patches atualizados: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que os produtos *Não visível individualmente* ainda aparecerão em Resultados da pesquisa avançada do catálogo.
* **MDVA-44100** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que todos os FPTs são atribuídos ao último produto no carrinho de compras e redefinidos para outros produtos.
* **MDVA-43605** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corrige o problema em que os dados de pedido retornam valores negativos para totais de linha ao usar a API Rest.
* **MDVA-43102** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corrige o problema em que a quantidade vendável não é atualizada corretamente quando um reembolso é feito por meio da API REST.
* **MDVA-43178** (*para Adobe Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Corrige o problema em que um token do cliente para um armazenamento personalizado não pode ser recuperado no GraphQL.
* **MDVA-43859** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o erro *Nenhuma entidade com customerId =* é registrado quando um cliente excluído tenta fazer logon.
* **MDVA-44147** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que uma solicitação do GraphQL não retorna Listas de requisições.
* **MDVA-44505** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige os problemas nos quais a Aplicação de pontos de recompensa da GraphQL não atualiza o Total geral e nos quais o crédito da loja é aplicado várias vezes durante a realização do pedido.
* Patches atualizados: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige o problema em que a Regra de produto relacionada funciona somente quando o Segmento do cliente está definido como *Todos*.
* **MDVA-39605** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que o TTL (expiration date) do cache Redis tem um valor incorreto.
* **MDVA-43862** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige o problema em que o cliente não pode atualizar itens do carrinho por causa de uma GraphQL *Mutação em UpdateCartItems* erro.
* **MDVA-43824** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Corrige o problema em que um erro é exibido ao cancelar pedidos com desconto.
* **MDVA-43451** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o erro *O armazenamento solicitado não foi encontrado. Verifique o armazenamento e tente novamente.* é exibido ao configurar um catálogo compartilhado para um site específico.
* **MDVA-43491** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corrige o problema em que o rótulo da imagem base não é atualizado ao importar produtos para um site de várias lojas.
* **MDVA-43601** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema de acionadores ausentes após a reindexação completa.
* **MDVA-42046** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Corrige o problema em que um valor incorreto é atribuído a um atributo de produto com um campo de entrada de data ao atualizar um produto.
* **MDVA-43935** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o produto de venda adicional é exibido duas vezes.
* **MDVA-44188** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que os emails emitidos pelo sistema com o `.-` Os endereços IP não são enviados.
* **MDVA-42283** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que o formato de data e hora na grade de pedido de administração da localidade francesa é inválido.
* Patches atualizados: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Adição de metadados de patches para o [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corrige o problema em que o usuário pode editar a hora de início de uma atualização agendada ativa.
* **MDVA-42410** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os relatórios de cupom exibem somente a moeda base padrão.
* **MDVA-41136** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que a data de expiração do `mage-cache-sessid` não é estendido, resultando na limpeza dos dados do cliente.
* **MDVA-39993** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Corrige o problema em que as alterações de inventário feitas por meio da API não refletiam na página do produto no front-end.
* **MDVA-42855** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que um novo endereço de cliente não é salvo no catálogo de endereços durante a finalização da compra.
* **MDVA-42645** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o Administrador não pode reembolsar pontos de premiação se a funcionalidade de crédito de armazenamento estiver desativada.
* **MDVA-43414** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Corrige o erro fatal do PHP que ocorre ao executar `inventory.reservations.updateSalabilityStatus` consumidor de fila em SKUs numéricas.
* **MDVA-41628** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corrige o problema em que usuários administradores restritos existentes obtêm acesso aos novos recursos quando novos módulos são adicionados.
* **MDVA-43348** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que a solicitação do GraphQL de cartão-presente mostra um erro se `gift_card_options` contain *uid*.
* **MDVA-39546** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que a data de início da atualização de preparo podia ser definida como uma data anterior à data atual durante a edição.
* **MDVA-42950** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os vídeos não são reproduzidos na página do produto.
* **MDVA-42689** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que o Adobe Commerce lança um *Violação de Restrição de Integridade* erro ao atualizar categorias de produto durante a importação.
* **MDVA-41229** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que as imagens disponíveis no back-end do não são exibidas no front-end após a importação de produtos configuráveis.
* **MDVA-43731** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que *Pesquisar Sinônimos* não funciona mais quando o valor é adicionado em *Termos mínimos para corresponder*.
* **MDVA-43232** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema de classificação de produtos no [!DNL Visual Merchandiser] Por Preço Especial para Baixo/Superior causa um erro ao salvar a categoria.
* **MDVA-43726** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.3*) - Corrige o problema em que a regra de Preço de catálogo com base na correspondência de atributo no nível do armazenamento falha ao ser aplicada após a reindexação parcial.
* Patches atualizados: MDVA-36464, MDVA-37478, MDVA-38608.
* Adição de metadados de patches para o [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que os atributos de preço do produto não podem ser atualizados para um site específico por meio da API REST.
* **MDVA-41350** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que uma exceção é lançada quando um usuário administrador com acesso restrito adiciona um produto fora do escopo de sua função por SKU em um pedido.
* **MDVA-42269** (*para Adobe Commerce e Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Corrige o problema em que um usuário administrador não consegue fazer logon no Administrador devido à *TypeError: strtotime() espera que o parâmetro 1 seja uma cadeia de caracteres, nulo fornecido* erro.
* **MDVA-40830** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que o crédito de armazenamento é aplicado várias vezes durante a inserção do pedido.
* **MDVA-42237** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que um preço especial de produto configurável não é atualizado após alterações no preço do subproduto.
* **MDVA-42520** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que a taxa de imposto é aplicada duas vezes se *Habilitar Comércio Transfronteiriço* é usada.
* Patches atualizados: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Patch obsoleto: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.5*) - Corrige o problema em que a atualização de atributo em massa cria a regravação de URL para o Armazenamento padrão somente após a alteração *Visibilidade do produto*.
* **MDVA-43091** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que o pedido de um produto incluído do administrador no back-end resulta no erro *Você não pode usar uma quantidade decimal para este produto*.
* **MDVA-40816** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que as regras de produto relacionadas mostram produtos de categorias não definidas nas condições de regra.
* **MDVA-41305** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corrige o problema em que o GraphQL mutation não retorna opções de produto configuráveis após adicioná-las à lista de desejos.
* **MDVA-39181** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que as regras de produto relacionadas mostram produtos de categorias não definidas nas condições de regra.
* **MDVA-42584** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque configurável no back-end não é atualizado após a alteração do status da quantidade e do estoque por meio da Importação ou da API.
* **MDVA-40175** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corrige o problema em que *Clique para alterar o método de envio* não mostra botões de opção para selecionar métodos de envio no Administrador durante a reorganização.
* **MDVA-42768** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corrige o problema em que o produto Configurável exibe o preço normal como 0 quando *Exibir sem estoque* é Sim.
* **MDVA-43201** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que um erro ocorre no logon do cliente ao usar o atributo DOB com determinadas localidades.
* Patches atualizados: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corrige o problema em que os filtros de data não estão funcionando corretamente quando o fuso horário do Adobe Commerce é diferente do fuso horário do ambiente local.
* **MDVA-42657** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não consegue selecionar categorias nas condições do segmento do cliente.
* **MDVA-42806** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que uma *Registro de nova empresa* O email é enviado sempre que uma empresa existente é atualizada por meio da API REST.
* **MDVA-37984** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corrige o problema em que a variável [!DNL Visual Merchandiser] *Combinar produto por regra* A funcionalidade não filtra corretamente os produtos com atualizações de preparo.
* **MDVA-40488** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que os produtos configuráveis com produtos secundários indisponíveis não são mostrados em sua faixa de preço correta.
* **MDVA-42507** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corrige o problema em que o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho.
* **MDVA-39163** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corrige o problema em que os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão de convidado.
* **MDVA-38626** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corrige o problema em que o usuário administrador não consegue colocar um pedido no back-end usando o [!DNL PayPal Payflow Pro] pagamento.
* **MDVA-38666** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.3.6*) - Corrige o problema em que o usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente.
* **MDVA-38526** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o usuário administrador não consegue acessar o [!DNL Site-Wide Analysis tool].
* Patches atualizados: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que os usuários recebem o erro 500 após definir a variável *image-messages* cookie se ele já existir, mas não houver novas mensagens.
* **MDVA-41139** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige o problema em que os produtos configuráveis ficam sem estoque após a importação do produto quando a quantidade de um produto simples é qty=0 para uma de suas origens.
* **MDVA-42326** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os clientes recebem um erro no check-out após um tempo limite de sessão mesmo se o carrinho de compras persistente estiver ativado.
* **MDVA-42341** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que a variável `categoryList` A consulta do GraphQL não filtra os resultados se uma solicitação tiver o cabeçalho Loja.
* **MDVA-38393** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras do Catálogo param de funcionar para um produto configurável se seu produto simples for renomeado.
* **MDVA-39153** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que um valor de desconto é calculado incorretamente durante o novo pedido no Administrador.
* Patches atualizados: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os usuários administradores não conseguem acessar a grade do cliente após excluir o site.
* **MDVA-40311** (*para Adobe Commerce e Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Corrige o problema em que os usuários administradores recebem a mensagem de erro *Chave de formulário ou segurança inválida. Atualize a página* após fazer logon no Admin, se o caminho Admin personalizado estiver configurado e a chave secreta estiver ativada.
* **MDVA-41631** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao tentar recuperar informações de pedidos sem uma *telefone* por meio do GraphQL.
* **MDVA-27239** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corrige o problema em que os produtos de venda cruzada não são exibidos.
* Patches atualizados: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corrige o problema de produtos ausentes no front-end durante a reindexação.
* **MDVA-40120** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que a classificação de GraphQL por DESC/ASC não funciona com produtos que têm a mesma relevância ou preço.
* **MDVA-41399** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.2*) - Corrige o problema em que os usuários administradores não conseguem acessar o *Gerenciar carrinho de compras* página se um cliente adicionar um produto à lista de desejos.
* **MDVA-40609** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que os dados de produtos desativados estão ausentes no `cataloginventory_stock_status` tabela de índice, exibindo quantidades incorretas de produtos desabilitados.
* **MDVA-39031** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que é possível adicionar um produto ao carrinho por meio do GraphQL, mesmo que ele não esteja atribuído ao site de destino.
* **MDVA-41597** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que os usuários recebem um erro ao adicionar mais de um produto configurável ao carrinho usando o GraphQL.
* **MDVA-27456** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.3.7*) - Corrige o problema em que os usuários recebem um erro ao tentar carregar [!DNL Swagger].
* **MDVA-32776** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2*) - Corrige o problema em que o status do estoque não é atualizado quando um pedido é feito, mas não é enviado.
* **MDVA-30862** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.0*) - Corrige o problema com a data de pedido incorreta na fatura de PDF impressa.
* Melhoria na página de índice do [!DNL Quality Patch Tool]. Adição de pesquisa e filtragem convenientes para [!DNL quality patches] na versão mais recente da ferramenta.
* Patches atualizados: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que é impossível criar uma nova atualização agendada ou editar uma existente para um produto se a Data final tiver sido removida anteriormente.
* **MDVA-41046** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que produtos simples com opções personalizadas estão disponíveis para atribuição a produtos configuráveis/agrupados.
* **MDVA-40545** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que somente o primeiro nó de uma página era recuperado, mesmo se houvesse mais de um nó para a mesma página.
* **MDVA-41164** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Corrige o problema em que um usuário administrador não pode salvar ou editar uma Empresa com um atributo de cliente personalizado do tipo arquivo ou imagem.
* **MDVA-39229** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema que faz com que o seguinte erro apareça após a atualização da hora de início da Atualização da regra de catálogo: *O Cron Job staging_synchronize_entities_period tem um erro: A atualização ativa não pode ser excluída.*
* **MDVA-40619** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as alterações na hierarquia de página do CMS causam um erro 500 ao tentar fazer edição em linha em uma página do CMS.
* **MDVA-41061** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o status do estoque é redefinido para vendável quando um produto é salvo do Administrador.
* **MDVA-31763** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que as regras de preço do catálogo são revertidas (ou não aplicadas) até a reindexação manual.
* **MDVA-37748** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que uma consulta do GraphQL retorna produtos não atribuídos a um catálogo compartilhado.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que faturas parciais para o mesmo pedido não podem ser criadas simultaneamente por meio da API REST.
* **MDVA-40101** (*para Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.0*) - Corrige o problema em que os itens não são removidos do minicarrinho após um pedido bem-sucedido usando [!DNL PayPal Express] Check-out.
* **MDVA-40401** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o valor de uso do cupom muda mesmo se a realização de um pedido falhar.
* **MDVA-40537** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Corrige o problema em que os usuários recebem um erro ao criar uma visualização de loja se houver várias páginas CMS com a mesma chave de URL.
* **MDVA-37725** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Corrige o problema em que os emails de pedido assíncrono enviados de sites não padrão contêm URLs de logotipo do site padrão.
* **MDVA-39482** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige o problema em que um produto sai do estoque se importado com a quantidade &quot;0&quot; quando ordens pendentes são ativadas.
* **MDVA-40435** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corrige o problema com um desconto incorreto em produtos de pacote com preços dinâmicos quando aplicado via GraphQL.
* **MC-42528** (*para Adobe Commerce e Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Corrige o problema em que a variável `categoryList` O GraphQL query retorna categorias atribuídas e não atribuídas.
* **MDVA-29400** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com pedidos duplicados feitos com o [!DNL PayPal Express Checkout].
* **MDVA-26005** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Corrige o problema em que é impossível selecionar uma categoria em uma árvore de categorias para condições de regra de Preço do carrinho.
* **MDVA-25631** (*para Adobe Commerce e Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Melhora o desempenho para editar e salvar segmentos de clientes que contêm um grande número de clientes.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige o problema em que as consultas de pesquisa do GraphQL não são exibidas em termos de pesquisa populares no Administrador.
* **MDVA-40601** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários recebem um erro ao tentar obter informações sobre a categoria alteradas por uma atualização agendada por meio do GraphQL.
* **MDVA-37234** (*para Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que adicionar um item ao carrinho várias vezes (solicitação paralela) para o mesmo SKU cria um item de linha duplicado para a mesma ID do carrinho.
* **MDVA-33606** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corrige o problema em que os usuários recebem uma *Violação de restrição exclusiva* erro ao salvar uma página CMS atribuída a uma hierarquia.
* **MDVA-31590** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que os usuários não conseguem atualizar atributos em massa usando filas assíncronas MySQL.
* **MDVA-36309** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que a pesquisa de produto por atributos é lenta nas grades de administração.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema em que a fatura com FPT mostra um Total geral incorreto quando o pedido é pago a partir do crédito da loja.
* **MDVA-37364** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.3*) - Corrige o problema em que o atributo de cliente personalizado do tipo de data quebra a interface do usuário da grade do cliente.
* **MDVA-39195** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que *Adicionar ao carrinho* O botão estava inativo na página categoria quando o redirecionamento para o carrinho estava ativado.
* **MDVA-37115** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corrige o problema em que uma *Apenas 0 restantes* esse aviso é exibido na página do produto configurável.
* **MDVA-39521** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que o usuário não consegue definir endereços de envio no carrinho com um número de telefone vazio por meio do GraphQL.
* **MDVA-39384** (*para Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Corrige o problema em que o atributo de cliente personalizado de um usuário da empresa não é salvo.
* **MDVA-39043** (*para Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.3*) - Corrige o problema em que o usuário administrador com acesso limitado recebe um erro ao tentar adicionar o *Produtos* para a página do CMS.
* **MDVA-39966** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com a implantação de localidades incorretas.
* **MDVA-38852** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Corrige o problema em que o inventário de catálogo por design bloqueia as tabelas para atualizações que diminuem significativamente o desempenho em casos com várias ordens paralelas.
* **MDVA-39986** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corrige o problema em que o usuário não consegue fazer um pedido no Admin no MacOS usando o navegador Safari.
* **MDVA-38447** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corrige dois problemas: em que a *Não visível individualmente* os produtos secundários configuráveis são retornados na resposta do GraphQL e otimizam a consulta do MySQL para a consulta de produtos da GraphQL com o filtro de categoria.
* **MDVA-40134** (*para Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corrige o problema em que o GraphQL não retorna produtos relacionados quando o Catálogo compartilhado está ativado.
* **MDVA-39935** (*para Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corrige o problema em que o GraphQL retorna produtos secundários configuráveis desativados no nível do site.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corrige o problema em que a variável *Chamada para uma função membro getId()* é exibido na página de detalhes do pedido no Admin.
* **MDVA-34948** (*para Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corrige o problema com consultas de longa execução, como `GET_LOCK`.
* **MDVA-39305** (*para Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Corrige o problema em que os clientes registrados não conseguem fazer logon com o Google ReCaptcha ativado.
* **MDVA-37897** (*para Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige o problema de redirecionamento incorreto quando um cliente tenta adicionar produtos com opções do widget Recentemente visualizado.

## v1.1.0 {#v1-1-0}

* As categorias de patch foram introduzidas para melhorar a experiência do usuário e facilitar a pesquisa dos patches necessários para os clientes.
* A variável `patches.json` o arquivo foi renomeado para `support-patches.json`.
* **MDVA-38799** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os produtos baixáveis não eram salvos após a criação de uma atualização de preparo.
* **MDVA-37592** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige o problema quando a classificação por preço não funciona corretamente para produtos com um preço zero atribuído ao catálogo compartilhado.
* **MDVA-38827** (*para Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Corrige o problema em que os clientes recebem um email de envio de pedido contendo uma mensagem de erro.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*para Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Corrige o erro ao salvar páginas CMS: *Já existe um item com a mesma ID PAGE_ID*.
* **MDVA-34680** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Corrige o problema em que o horário de criação da conta do cliente não é filtrado corretamente na grade de clientes.
* **MDVA-37068** (*para Adobe Commerce >=2.3.1 &lt;2.4.4*) - Corrige o problema em que a alíquota de imposto incorreta é exibida quando o carrinho de compras tem apenas produtos virtuais.
* **MDVA-38608** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que tabelas temporárias não são excluídas quando a reindexação não é concluída com êxito.
* **MDVA-38308** (*para Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Corrige os problemas relacionados à adição [!DNL Vimeo] vídeos para produtos.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige o problema em que o cliente não é levado para a página Confirmação de pagamento ao usar o [!DNL Paypal Payment Advanced] método.
* **MDVA-37082** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao salvar o estoque personalizado de produtos agrupados, o que faz com que o produto fique sem estoque no front-end.
* **MDVA-36572** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corrige o problema quando as atualizações do Aviso de crédito não causam mais atualizações de reserva de produtos duplicadas no banco de dados.
* **MDVA-38132** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige o problema quando o painel Admin está inacessível devido a uma *muitos redirecionamentos* erro.
* **MDVA-38270** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema de informações de cartão-presente ausentes no total do pedido no GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*para Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Corrige o problema que ocorria ao adicionar um produto configurável ao carrinho por meio do GraphQL quando a ID do site não coincidia com a ID da loja.
* **MDVA-36832** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corrige o problema em que as imagens são duplicadas em páginas com largura de exibição de 768px.
* **MDVA-37874** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Corrige o problema em que *Valor de desconto fixo para o carrinho inteiro* é aplicado incorretamente a um produto de pacote que contém mais de uma opção.
* **MDVA-37913** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Corrige o problema em que os links baixáveis desaparecem se o produto baixável for atualizado por meio da API.
* **MDVA-34330** (*para Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Corrige o problema em que os pedidos na grade Pedidos não são filtrados de acordo com o fuso horário do Administrador.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*para Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Corrige o problema em que a Adobe Commerce emite um erro ao criar uma fatura parcial para pedidos feitos com o *Pagamento por conta* método de pagamento por meio da API REST.
* **MDVA-37362** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corrige o problema em que os valores de opção de produto e os valores de atributo de variante configuráveis estavam vazios na resposta do GraphQL.
* **MDVA-37288** (*para Adobe Commerce 2.4.2*) - Corrige o problema em que preços de nível incorretos eram retornados após a solicitação do GraphQL.
* **MDVA-37225** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Corrige o problema em que o processo de upload fica preso durante a criação rápida de pedido quando há um valor inteiro em SKUs importadas.
* **MDVA-37224** (*para Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Corrige o problema em que os clientes não podem pagar pela cotação negociável com o [!DNL PayFlow Pro] com outro produto no carrinho.
* **MDVA-36286** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corrige o problema em que a visualização do widget de produtos do Page Builder é interrompida se o mesmo SKU tiver uma posição diferente em subcategorias.
* **MDVA-30186** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Corrige o problema em que as opções de atributo são classificadas pelo valor da opção em vez da contagem de itens do atributo na resposta do GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*para Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Corrige o problema em que as opções personalizadas antigas permanecem após serem alteradas por meio da API.
* **MDVA-35773** (*para Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Corrige o problema em que o Total geral não era exibido como zero na Fatura para pedidos com 100% de desconto.
* **MDVA-36833** (*para Adobe Commerce 2.4.2*) - Corrige o problema em que os resultados da pesquisa mostram números aleatórios de produtos por página após excluir alguns produtos do catálogo compartilhado.
* **MDVA-37182** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Corrige o problema de resultados de pesquisa incorretos no [!DNL Elasticsearch] versão 6 e versão 7.
* **MDVA-36253** (*para Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Corrige o problema em que o subtotal incorreto é exibido no minicarrinho após a exclusão do item.
* **MDVA-36853** (*para Adobe Commerce 2.4.2*) - Corrige o problema de ausência de imagens ao carregar grandes galerias de mídia.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*para Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Corrige o problema de produtos empacotados ausentes nas páginas de categoria.
* **MDVA-36615** (*para Adobe Commerce 2.4.2*) - Corrige o problema com a contagem de produtos incorreta na grade de produtos de Administração.
* **MDVA-36464** (*para Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Corrige o problema em que a configuração de notificação por email não está funcionando no nível de visualização da loja.
* **MDVA-36138** (*para Adobe Commerce ^2.3.2*) - Corrige o problema em que o preço do frete não é ajustado e o preço total do frete é mostrado aos clientes se nem todos os itens no carrinho se qualificarem para a regra do carrinho de frete gratuito.
* **MDVA-36424** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Corrige o problema em que as imagens de mídia anexadas aos elementos do page builder desaparecem quando o conteúdo está sendo editado repetidamente se o URL base de back-end for diferente do URL base da loja.
* **MDVA-35984** (*para Adobe Commerce ^2.4.0*) - Corrige o problema com a quantidade de produto e a quantidade vendável incorretas após criar várias entregas simultâneas para o mesmo produto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Isso corrige o problema em que a consulta do GraphQL não é armazenada em cache usando a tag de cache de categoria.
* **MDVA-33168** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema ao atualizar um atributo de produto por meio da API. Todos os outros atributos são alterados para um valor vazio.
* **MDVA-19640** (*para Adobe Commerce >=2.3.0*) - Corrige o problema em que [!DNL Advanced Reporting] O não está mostrando dados.
* **MDVA-11189** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema ao importar um arquivo CSV para atualizar o estoque de produtos, linhas do `cataloginventory_stock` tabela são excluídas.
* **MDVA-26639** (*para Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Corrige o problema em que, se um novo modelo de e-mail de confirmação de pedido for criado, os itens de pedido estarão ausentes no e-mail de pedido.
* **MDVA-15546** (*para Adobe Commerce >=2.3.0*) - Corrige o problema em que, após criar um pedido, um *Coluna entity_id onde a cláusula é ambígua* um erro é exibido no log de exceções.
* **MDVA-21095** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema quando uma consulta `INSERT INTO search_tmp` não terminará após a atualização do valor do atributo em massa.
* **MDVA-23845** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema em que os modelos de email não podem ser visualizados após a ativação da minificação do JavaScript.
* **MDVA-22026** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema de falha na importação de produtos do arquivo CSV, incluindo imagens de URLs externos.
* **MDVA-22383** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema em que salvar um produto demora e a página é quebrada.
* **MC-41359** (*para Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Corrige o problema das configurações incorretas de parâmetros de cookie SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*para Adobe Commerce 2.4.1*) - Corrige o problema no qual o Page Builder emite o seguinte erro: *Ocorreu um erro ao iniciar o Page Builder. Consulte seu contato de suporte técnico.*
* **MDVA-35356** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema com a devolução incorreta do crédito da loja após o cancelamento do pedido parcialmente faturado.
* **MDVA-33289** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige o problema em que o código JavaScript bruto é exibido na interface do usuário do endereço de faturamento durante o check-out se [!DNL Google Tag Manager] está ativado.
* **MDVA-35982** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os usuários administradores restritos a um site específico não podem criar uma remessa para o pedido feito no mesmo site.
* **MDVA-35155** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema de impossibilidade de comprar um produto combinado se o título da opção fosse alterado.
* **MDVA-35910** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema em que é impossível criar uma nova conta de cliente após desabilitar a funcionalidade Logon como cliente.
* **MDVA-34474** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema ao adicionar um produto à lista de requisições usando a API.
* **MDVA-34591** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema com um cálculo de desconto de regra de carrinho incorreto para *Desconto de Qtde Máxima Aplicado a* e *Etapa de Qtde. de Desconto (Compra X)*.
* **MDVA-33704** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corrige o problema em que a variável *Coleta na loja* a opção de envio não é exibida, embora esteja configurada para estar disponível.
* **MDVA-34928** (*para Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Corrige o problema em que o carregador de página é exibido indefinidamente após o crédito da loja ser removido do pagamento.
* **MDVA-35254** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige os problemas com CAPTCHA durante o check-out.
* **MDVA-35569** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que a variável *impostos fixos do produto* O campo não está sendo preenchido na resposta da GraphQL quando o estado é especificado.
* **MDVA-35847** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige o problema B2B em que o formulário Usuários da empresa é interrompido se um atributo de cliente personalizado é usado.
* **MDVA-31307** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que há *Sem memória* erros em determinadas categorias devido a problemas com a lista de permissões dinâmica de CSP para blocos em cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige os erros *em andamento* status da mensagem para o correto *concluído* mensagem para o consumidor `quoteItemCleaner` após excluir vários produtos.
* **MDVA-34102** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige a quantidade de Estoque padrão em zero para produtos desabilitados nas páginas Grade de produtos e Editar produto na área de Administração.
* **MDVA-35286** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que há um erro se um cliente tiver agrupado produtos no carrinho e alternar do check-out de Vários endereços para o check-out de Uma página.
* **MDVA-35312** (*para Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Corrige o código de resposta 500 quando uma solicitação GraphQL está vazia.
* **MDVA-34189** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige o tempo limite de 503 primeiros bytes em [!DNL Visual Merchandiser] consultas ao carregar a página Categoria do administrador.
* **MDVA-34695** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correções negativas `children_count` depois de excluir categorias.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corrige o problema em que a variável *Usar valor padrão* A caixa de seleção é desmarcada depois que as alterações programadas são aplicadas. O problema aparece quando as alterações agendadas não estão mais em vigor.
* **MDVA-35064** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corrige o problema em que as substituições de URL não são geradas para produtos configuráveis criados por meio da API.
* **MDVA-34943** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o pedido rápido armazena em cache as SKUs inseridas anteriormente.
* **MDVA-35197** (*para Adobe Commerce >=2.3.5 &lt;2.4.0*) - Corrige o problema de erro ao adicionar ao carrinho usando o GraphQL se os produtos adicionados anteriormente ficassem indisponíveis.
* **MDVA-34850** (*para Adobe Commerce >=2.3.1 &lt;2.4.0*) - Corrige o problema em que as opções indisponíveis de um produto configurável não são exibidas, em vez de serem exibidas como impressionadas.
* **MDVA-34867** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que os valores de um campo de condição definidos para uma atualização programada não são salvos.
* **MDVA-35092** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corrige o problema em que os usuários não conseguem adicionar [!DNL Vimeo] vídeos devido a obsoletos [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corrige o problema em que a pré-visualização do tipo de conteúdo de Produtos do Page Builder é interrompida se os produtos correspondentes tiverem preços diferentes para cada site.
* **MDVA-32634** (*para Adobe Commerce ^2.3.1*) - Corrige o problema em que a variável `url_path` da categoria atribuída a todos os armazenamentos permanece inalterada após mover a categoria na hierarquia.
* **MDVA-33344** (*para Adobe Commerce ^2.3.0*) - Corrige o problema de codificação rígida `rma_item` a ID do conjunto de atributos padrão de entidade é usada em vez do valor do banco de dados.
* **MDVA-34192** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige o problema em que é impossível modificar/especificar a data de nascimento do cliente usando o formato dd/mm/aaaa.
* **MDVA-34847** (*para Adobe Commerce ^2.3.0*) - Corrige a conversão do tipo de IDs de armazenamento em número inteiro para a condição SQL em coleções de administradores para o Usuário administrador com permissões personalizadas.
* **MDVA-34886** (*para Adobe Commerce ^2.3.2*) - Corrige o problema em que a pesquisa não retorna resultados se *peso* o atributo de produto está configurado como pesquisável.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema de [!DNL PayPal Payflow Pro] falha no pagamento com erro de formato da lista de parâmetros de redirecionamento.
* **MDVA-34023** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrige o problema em que o erro *Nenhuma entidade com addressId* é exibido aleatoriamente nos navegadores dos visitantes.
* **MDVA-32759** (*para Adobe Commerce >=2.3.1 &lt;2.4.3 com extensão B2B*) - Corrige o problema em que os Catálogos compartilhados excluem os preços de camada existentes.
* **MDVA-33482** (*para Adobe Commerce ^2.3.5*) - Corrige o problema em que a geração de um Aviso de Crédito contra uma NFF parcial resulta em imposto para a ordem total em vez de imposto para essa NFF parcial.
* **MDVA-33393** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o erro *A countryId fornecida não existe*.
* **MDVA-33632** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fornece uma correção em que a mensagem de exceção *Este produto está esgotado* O agora é exibido para um usuário administrador ao tentar resolicitar um produto indisponível.
* **MDVA-34469** (*para Adobe Commerce >=2.4.1 &lt;2.4.2*) - Corrige o problema em que as mutações do GraphQL no carrinho de um cliente falham ao usar várias exibições de loja.
* **MDVA-33976** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*) - Corrige o problema em que o produto incluído é mostrado Fora de estoque na loja após remover a segunda opção do produto incluído.
* **MDVA-33894** (*para Adobe Commerce >=2.4.0 &lt;2.4.1 com extensão B2B*) - Corrige vários problemas na funcionalidade de Pedido rápido, incluindo a adição e remoção de vários produtos e a diferenciação entre maiúsculas e minúsculas de SKU.
* **MDVA-27664** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema no formulário de registro do cliente, que causa um erro na exibição: *ERRO - A Data de Nascimento não deve ser posterior à data de hoje.*
* **MDVA-33970** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que há um sinal de moeda incorreto no Aviso de crédito quando o escopo do atributo de preço é definido como site.
* **MDVA-33992** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema de preço especial B2B sendo exibido incorretamente durante a finalização.
* **MDVA-34100** (*para Adobe Commerce >=2.3.4 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que uma conta da empresa não pode ser criada a partir da página de estrutura da empresa.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*para Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Corrige o problema com imagens duplicadas após a importação do produto de um arquivo CSV.
* **MDVA-33382** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige os problemas com a invalidação de indexadores após a remoção de produtos de uma categoria.
* **MDVA-28511** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige o problema em que não é possível concluir [!DNL PayPal] check-out se o campo Nome contiver determinados caracteres (como letras maiúsculas acentuadas).
* **MDVA-31519** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corrige o problema com tempos limite de espera na finalização de compra do convidado quando uma regra de vendas do site inteiro está em uso.
* **MDVA-33281** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema em que há um erro fatal no `inventory:reservation:list-inconsistencies` devido ao tipo incorreto de parâmetro SKU.
* **MDVA-24201** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema em que os preços não refletem a regra de preço do carrinho programado até serem reindexados manualmente.
* **MDVA-32694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Corrige o problema em que um usuário administrador não pode adicionar um produto a uma cotação negociável se estiver relacionado a uma loja não padrão.
* **MDVA-33516** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que a edição de um produto combinado em uma lista de requisições leva a um erro.
* **MDVA-33975** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige vários problemas relacionados ao cálculo de preço em solicitações do GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema com o [!DNL PayPal] Relatórios de liquidação não disponíveis em **Relatórios** > **Vendas** > **[!DNL PayPal]** Liquidação conforme esperado.
* **MCP-87** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Tempo de indexação aprimorado para categorias de produtos e indexadores de ações para perfis grandes.
* **MDVA-33106** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que as alterações de produto reagendadas são apagadas após o cron `run` é executado.
* **MDVA-19391** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corrige o problema em que `analytics_collect_data` está gerando um erro devido a registros de descrição NULL no `catalog_category_entity_text` tabela.
* **MDVA-20376** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema com a *Nenhuma entidade com customerId = 1* erro no `exception.log` para clientes conectados após o posicionamento do pedido.
* **MDVA-23764** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige o erro no `JsFooterPlugin.php` que afeta a exibição de blocos dinâmicos.
* **MDVA-13203** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que a variável *Tabela search_tmp_ de violação de restrição de integridade* aparece após uma reindexação completa.
* **MDVA-23426** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*) - Corrige o problema em que os emails de notificação enviados pelo Adobe Commerce contêm um corpo em branco com conteúdo que está sendo adicionado como anexo.
* **MDVA-22150** (*para Adobe Commerce >=2.3.1 &lt;2.3.4*) - Corrige o problema em que os clientes com um produto configurável no carrinho e um cupom aplicado não podem fazer logon se esse produto configurável estiver desativado no Administrador.
* **MDVA-32545** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que as faturas não são enviadas automaticamente ao criar pedidos do Administrador.
* **MDVA-32714** (*para Adobe Commerce >=2.3.4 &lt;2.4.1*) - Corrige o problema em que o preço de grupo de clientes não está funcionando na consulta de produto do GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Adiciona a variável *Subtotal (Incl. Imposto)* opção de precificar condições da regra.
* **MDVA-31236** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corrige o problema em que os Administradores com acesso a recursos personalizados não podem configurar o 2FA ou fazer logon.
* **MDVA-30845** (*para Adobe Commerce >=2.3.5 &lt;2.3.7*) - Corrige o problema em que a variável *Não há cotações disponíveis para este pedido no momento* O erro é exibido quando ocorre uma falha de conexão ao UPS XML/USPS/DHL e nenhum outro método de envio está disponível.
* **MDVA-32133** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema em que a galeria de mídia não é carregada do Page Builder em determinados casos.
* **MDVA-12304** (*para Adobe Commerce >=2.3.0*) - Aumenta o número máximo de cookies de 50 para 200.
* **MDVA-32632** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige o problema em que os pedidos são exibidos no sistema de pagamento, mas não no Adobe Commerce.
* **MDVA-32449** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que o histórico do pedido é carregado muito lentamente ou não é carregado.
* **MDVA-32739** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que a ativação de Notificações por email assíncronas envia emails de vendas antigos.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*para Adobe Commerce 2.3.6, 2.4.1*) - Corrige o problema em que a variável *Criar uma conta* O botão permanece desativado após a correção de dados inválidos na *Criar nova conta de cliente* formulário.
* **MDVA-31006** (*para Adobe Commerce 2.3.0, 2.3.1*) - Corrige o problema em que pedidos duplicados são exibidos após a realização de um pedido usando [!DNL Paypal Express] pagamento.
* **MDVA-25602** (*para Adobe Commerce 2.3.0*) - Corrige o problema com o [!DNL PayPal Payflow Pro] método de pagamento e tratamento de cookies como `SameSite=Lax` por padrão, no navegador Chrome 80 e na resposta da API, redirecione para a página de logon do cliente.

## v1.0.10 {#v1-0-10}

Correções secundárias para versões de patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema em que a Regra de preço do carrinho com o cupom não se aplica por meio do GraphQL quando *Desconto de valor fixo para o carrinho inteiro* é usada.
* **MDVA-30889** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que um erro ocorre após faturar um pacote com produtos virtuais e simples como opções.
* **MDVA-31791** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Melhora o desempenho da página do produto nos casos em que as regras de direcionamento ou os produtos vinculados são usados.
* **MDVA-31168** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o arquivo CSV de exportação do produto não é exibido e em que há um erro de alocação de memória.
* **MDVA-32313** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema em que os produtos configuráveis podiam ser adicionados à lista de desejos com as opções de configuração incorretas.
* **MDVA-31759** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os produtos não são atualizados com o *lista suspensa* e *textarea* valores de atributo durante a importação de CSV.
* **MDVA-32012** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os códigos postais na Coreia e na Argentina não podem ser validados.
* **MDVA-31640** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Corrige o problema em que um preço especial não pode ser atualizado por meio da API REST.
* **MDVA-28651** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 com extensão B2B*) - Corrige o problema em que há problemas de desempenho ao carregar cotações negociáveis por meio da API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*para Adobe Commerce >=2.3.0 &lt;2.4.1 com extensão B2B*) - Corrige o problema em que um sinal de moeda incorreto é exibido na grade Aviso de crédito.
* **MDVA-31295** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que os pontos de premiação não são calculados quando um pedido parcial é concluído e os itens são tributados.
* **MDVA-30112** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que, se o número de pedidos exceder o *tamanho de grupo* valor, a Adobe Commerce considera os pedidos com *pendente* status como inconsistências.
* **MDVA-31150** (*para Adobe Commerce >=2.3.0 &lt;2.4.2* GET ) - Corrige o problema em que os saldos de cartão de crédito e de cartão-presente da loja não são retornados pela chamada da API Rest da fatura, quando a fatura foi lançada pela chamada da API Rest e o pedido foi parcialmente pago por contas de cartão-presente e de crédito da loja.
* **MDVA-30963** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corrige o problema em que os resultados da filtragem de produtos definidos para conter apenas valores especificados para *Todas as exibições de loja* escopo em Admin, inclua produtos com valores substituídos no nível de exibição da loja.
* **MDVA-29954** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 com extensão B2B*) - Corrige o problema em que a variável *Nova solicitação de registro da empresa* e *Você foi vinculado a uma empresa* os emails são enviados do endereço errado.
* **MDVA-28357** (*para Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Substitui o analisador padrão por um analisador personalizado com tokenizador de palavra-chave para o campo SKU no [!DNL ElasticSearch] o índice para fazer com que as consultas de pesquisa curinga funcionem com SKUs que contêm um hífen (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o status do pedido personalizado foi alterado para *Processando* após a criação da entrega parcial usando a WebApi.
* **MDVA-30428** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) - Corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se esse produto estiver atribuído a uma origem de inventário personalizada.
* **MDVA-30594** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que um pedido com vários endereços não podia ser salvo durante o check-out quando o FPT estava configurado.
* **MDVA-29148** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema ao criar um produto por meio de uma chamada de API, o atributo personalizado do produto de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multisseleção), o tipo não usará seu valor padrão se nenhum valor tiver sido fornecido na carga.
* **MDVA-30837** (*para Adobe Commerce >=2.3.1 &lt;2.3.5*) - Adição de uma configuração *Incluir Imposto na Quantia: Sim/Não* na configuração do método de envio gratuito. Quando *Incluir Imposto no Valor* está definida como *Sim*, a Quantia Mínima do Pedido é calculada como Subtotal + Imposto. Quando *Incluir Imposto no Valor* está definida como *Não*, a Quantia mínima do pedido é calculada como Subtotal
* **MDVA-25028** (*para Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Corrige o problema quando os pedidos são feitos usando [!DNL PayPal Payflow Pro] não são definidos como Status de suspeita de fraude quando os filtros de fraude são acionados.
* **MDVA-31224** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*) - Melhora o desempenho do `catalog_product_price` operação de reindexação para produtos de pacote.
* **MDVA-31321** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige uma página em branco (erro) ao *Mostrar tudo* está selecionada. [!DNL Elasticsearch] retorna uma grande lista de ids de produtos. Nesse cenário, a cláusula order by é convertida em um formato SQL incorreto.
* **MDVA-30815** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que, ao alterar a quantidade de resultados de pesquisa que devem ser exibidos na página de resultados da pesquisa, o Adobe Commerce exibe uma página em branco. [!DNL Elasticsearch] O agora exibe corretamente os resultados das páginas de categoria quando você altera o número de resultados da pesquisa exibidos por página.
* **MDVA-30782** (*para Adobe Commerce >=2.3.5 &lt;2.4.2*) - Corrige o problema em que o Bloco dinâmico é exibido independentemente da regra do carrinho.
* **MDVA-31021** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que há problemas de desempenho no `module-catalog-import-export/Model/Import/Product/Option.php`. Se houver mais de ~100 k registros em `catalog_product_option` novo CSV com um único produto leva menos de 10 segundos para ser validado.
* **MDVA-31007** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema em que os atributos de endereço personalizados não são exibidos corretamente na página de detalhes do pedido na área minha conta e no back-end do.
* **MDVA-29389** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema nos Relatórios avançados em que a variável `analytics_collect_data` cronjob diz: *A porta deve ser configurada no parâmetro de host (como localhost:3306)*.
* **MDVA-31343** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige o problema com a classe de corpo removida `page-layout-category-full-width` quando uma categoria é agendada.
* **MDVA-30945** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que você recebe uma mensagem de erro fatal ao atualizar carrinhos `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*para Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementa a *O mínimo deve corresponder a* funcionalidade e pesquisa parcial para [!DNL Elasticsearch] motor. Soluciona problemas com hifens em consultas de pesquisa.
* **MDVA-30102** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corrige o problema em que o cache Redis cresce rapidamente, pois os caches de layout não têm TTL.
* **MDVA-30599** (*para Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Corrige o problema em que as cotações de convidado criadas usando a API são marcadas incorretamente como cotações para clientes conectados.
* **MDVA-29446** (*para Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Corrige o problema em que o preço do método de envio não aplicável é mostrado como zero durante a finalização da compra.
* **MDVA-30357** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corrige o problema em que URLs de imagem incorretos são criados ao gerar um mapa de site pelo cron.
* **MDVA-30565** (*para Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Corrige o problema em que *Nenhuma entidade com cartid = 0* o erro será exibido para o cliente convidado na finalização da loja se o carrinho de compras persistente estiver ativado.
* **MDVA-29787** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Corrige o problema em que a regra do Target para produtos relacionados não funciona quando *é um de* condição é usada para definir os produtos a serem exibidos.
* **MDVA-30977** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Corrige o problema com produtos aleatórios ausentes nas categorias após a reindexação.
* **MDVA-28202** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Corrige o problema em que a Navegação em camadas não filtra os produtos configuráveis corretamente quando o MSI é usado.
* **MDVA-28300** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que a solicitação GQL não reflete as alterações de preço das regras de preço do catálogo.
* **MDVA-31006** (*para Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Corrige o problema em que pedidos duplicados são exibidos após a realização de um pedido usando [!DNL Paypal Express] pagamento.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema de navegação em camadas, onde a variável *Não* valor para atributos de produto do tipo booleano não foi incluído na navegação em camadas se [!DNL Elasticsearch] foi usado como um mecanismo de pesquisa.
* **MDVA-28191** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que nenhum método de pagamento é carregado durante a criação do pedido por meio do Administrador.
* **MDVA-29959** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 com extensão B2B*) - Corrige o problema em que o usuário administrador restrito com *Empresas* permissões não tem permissão para excluir a conta da empresa.
* **MDVA-30265** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que o link de rastreamento de remessa pára de funcionar após a criação da fatura.
* **MDVA-28409** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema em que a variável `sales_clean_quotes` falha na tarefa cron com *memória insuficiente* erro quando o número de aspas expiradas no banco de dados é enorme.
* **MDVA-30593** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corrige o problema em que as cotações expiradas de acordo com a configuração Tempo de vida da cotação não são limpas.
* **MDVA-30107** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige o problema em que o alternador de armazenamento não funciona como esperado se URLs de base diferentes forem usadas para exibições de loja.
* **MDVA-28763** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corrige o problema em que a imagem do produto é duplicada após atualizar as informações do produto usando a API REST mais de uma vez.
* **MDVA-30284** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema em que o indexador da Pesquisa no catálogo falha devido ao seguinte *[!DNL Elasticsearch]erro: o limite do total de campos no índice foi excedido.*
* **MDVA-29042** (*para Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 com extensão B2B*) - Corrige o problema em que as permissões do Catálogo foram alteradas para *Permitir* automaticamente depois que o novo produto foi adicionado ao catálogo compartilhado.
* **MDVA-30428** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que os clientes não podem adicionar um produto à lista de desejos se esse produto estiver atribuído a uma origem de inventário personalizada.
* **MDVA-28661** (*para Adobe Commerce >=2.3.0 &lt;2.4.2 com extensão B2B*) - Corrige o problema em que um erro é lançado na seção de conta da empresa Usuários da empresa após a alteração do administrador da empresa.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*para Adobe Commerce 2.3.1 - 2.3.4-p2*) - Corrige o problema em que os trabalhos cron falham se o nome do banco de dados for muito longo, resultando na atualização de categorias no front-end.
* **MDVA-30106** (*para Adobe Commerce ^2.3.0*) - Corrige um problema no qual, durante a finalização, os pagamentos não são carregados com *Não é possível ler a propriedade &#39;length&#39; de null* erro no console JS.
* **MDVA-28656** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Corrige o problema em que, se um pedido foi feito sem a necessidade de informações de pagamento (por exemplo, com 100% de desconto) e uma fatura foi criada para o pedido, o status do pedido muda para *Fechado* em vez de Concluído.
* **MDVA-30209** (*para Adobe Commerce 2.3.0 - 2.3.3-p1*) - Corrige o problema em que o grupo de clientes era alterado para o padrão se o cliente atualizasse as informações da conta.
* **MDVA-30123** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige o problema em que os rótulos de opção de atributo não são traduzidos corretamente para consultas do GraphQL.
* **MDVA-29996** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige o problema em que, após habilitar a permissão de categoria, a página de categoria não é armazenada em cache pelo Cache de página cheia.
* **MDVA-30164** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Corrige o problema em que os registros de clientes não podem ser exportados da grade Clientes se existirem atributos de cliente personalizados.
* **MDVA-30444** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige o problema em que nenhum email de confirmação é enviado para pedidos feitos usando o GraphQL.
* **MDVA-30490** (*para Adobe Commerce 2.3.4 - 2.3.5-p2*) - Corrige o problema em que a comparação de produtos lança a página de erro 500 se um dos produtos tiver uma descrição curta vazia.
* **MDVA-30232** (*para Adobe Commerce >=2.3.1 &lt;2.4.1*) - Corrige o problema em que não é possível fazer o novo pedido se o pedido original contiver um vale-presente.
* **MDVA-29965** (*para Adobe Commerce >=2.3.3 &lt;2.4.0*) - Corrige o problema em que os clientes obtêm o erro Chave de formulário inválido ao adicionar um produto ao carrinho.
* **MDVA-30008** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige o problema B2B em que não é possível fazer pedidos por meio da API de administração para um produto que está em um catálogo público.
* **MDVA-22469** (*para Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Corrige o problema em que, após a atualização para o Adobe Commerce 2.3.3, o Page Builder não funcionava no painel de Administração e alguns arquivos JS e CSS não eram carregados.
* **MC-35984** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema em que os comerciantes não podiam interagir com nenhum elemento de página na página Devoluções após criar uma etiqueta de remessa para uma Autorização de devolução de produto (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*para Adobe Commerce 2.3.0 - 2.3.4*) - Corrige o problema com o [!DNL PayPal Payflow Pro] método de pagamento e tratamento de cookies como `SameSite=Lax` por padrão, no navegador Chrome 80 e na resposta da API, redirecione para a página de logon do cliente.
* **MDVA-26694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Corrige o problema com caches de produtos e catálogos que expiram diariamente, embora sejam agendados para expirar de forma diferente.
* **MDVA-27825** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corrige o problema em que a exportação de grandes quantidades de dados falhava devido a vazamento de memória.
* **MDVA-29085** (*para Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Corrige o problema B2B em que nenhum email de nova empresa necessário é enviado se uma empresa é criada pela API.
* **MDVA-29344** (*para Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Corrige o problema em que o Page Builder fica preso após copiar o texto de um elemento de cabeçalho para um elemento de texto.
* **MDVA-29835** (*para Adobe Commerce >2.3.1 &lt;2.4.2*) - Corrige o problema em que os pedidos de cartão-presente continham dois códigos em vez de um.
* **MDVA-30052** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corrige o problema com o conteúdo privado (armazenamento local) não sendo preenchido corretamente, o que resultava em problemas de desempenho.
* **MDVA-30131** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corrige o problema de navegação em camadas, onde a variável *Não* valor para atributos de produto do tipo booleano não foi incluído na navegação em camadas se [!DNL Elasticsearch] foi usado como um mecanismo de pesquisa.
* **MDVA-35514** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corrige o problema na criação de um rótulo de remessa e na adição de produtos solicitados a um pacote na janela modal Criar pacotes.
