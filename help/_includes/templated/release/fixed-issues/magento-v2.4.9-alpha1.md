---
source-git-commit: 6c7feee0cd23d397c40bb66593a79b59ac2f620a
workflow-type: tm+mt
source-wordcount: '2806'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.9-alpha1)

## Correção de problemas na v2.4.9-alpha1

Corrigimos 67 problemas no código principal Magento Open Source 2.4.9-alpha1. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

* __A Operação em Massa Assíncrona permanece no estado aberto para async.magento.configurableproduct.api.optionrepositoryinterface.save.post__
Os pontos de extremidade de API em massa agora emitirão um erro se o corpo da solicitação não for uma Matriz, exigindo que as chaves de item em massa sejam números consecutivos começando de 0. Anteriormente, o status do item em massa não era atualizado devido à chave de item arbitrária enviada na solicitação em massa.
  _ACP2E-3544 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_
* O bug REST da API da __[NUVEM] no valor is_subscribed não está sendo considerado do repositório atual usando searchCriteria__
REST da API A consulta do cliente busca o valor &quot;is_subscribed&quot; correto no armazenamento correto usando searchCriteria
Anteriormente, a consulta do cliente REST da API não considerava o armazenamento ao buscar o valor &quot;is_subscribed&quot;.
  _ACP2E-3621 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_
* __async.operations.all pode criar várias entradas para 1 SKU__
As solicitações simultâneas para salvar e atualizar o mesmo produto agora são serializadas para evitar condições de corrida que podem resultar em inconsistência de dados ou produtos duplicados
  _ACP2E-3744 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Conta

* A operação de exclusão da __[Nuvem] é proibida para o erro de área atual durante a criação da conta do cliente__
Após a correção, salvar um cliente com um endereço inválido retorna uma mensagem descrevendo o motivo da invalidez em vez de &quot;A operação de exclusão é proibida para a área atual&quot; irrelevante.
  _ACP2E-3791 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Interface do administrador

* __[Problema] Melhore a experiência do usuário com a árvore de funções__
Essa solicitação de pull adiciona botões para recolher tudo, expandir tudo e expandir ramificações com itens selecionados. Essa funcionalidade é semelhante à fornecida na árvore de categorias (Catálogo -> Inventário -> Categorias)
  _AC-14020 - [Problema do GitHub](https://github.com/magento/magento2/issues/39654) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36511)_
* __Symfony\Component\Mime\Exception\LogicException: o cabeçalho &quot;Remetente&quot; deve ser uma instância de &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (obteve &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)__
  _AC-14520 - [Problema do GitHub](https://github.com/magento/magento2/issues/39823) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1e14bd72)_
* __Forneça um recurso para excluir taxas de imposto em massa usando a grade__
Os usuários administradores agora podem excluir simultaneamente várias alíquotas de imposto da grade Alíquotas de imposto administrativas.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)
  _AC-2238 - [Problema do GitHub](https://github.com/magento/magento2/issues/33399) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33484) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_
* __A regra de preço do carrinho com SKU de condição não leva em conta os &quot;zeros à esquerda&quot; na SKU (sku: 01234 é o mesmo que 1234)__
Agora o sistema lida corretamente com a regra de preço do carrinho com a SKU de condição. Considere os &quot;zeros à esquerda&quot; na SKU
  _AC-9428 - [Problema do GitHub](https://github.com/magento/magento2/issues/37919) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39525)_
* __Problema com o Comportamento do Valor da Opção de Atributo Padrão para Multisseleção__
Antes da correção, os valores padrão para o atributo de várias opções não eram salvos corretamente. Agora, após a correção, os valores são armazenados corretamente no banco de dados.
  _ACP2E-3523 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_
* __Problema ao mover a quantidade do produto para o carrinho de compras do administrador__
Ao criar um pedido do administrador, os produtos no carrinho do cliente na barra lateral não desaparecerão quando adicionados ao pedido.
  _ACP2E-3563 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Interface do administrador, B2B

* __O Logon B2B como cabeçalho do Cliente ainda tem marca Magento__
Anteriormente, o cabeçalho da loja exibe &quot;Agora você está conectado como &lt;nome do cliente> na &lt;nome da loja>&quot; com a marca Magento. Que agora foi corrigida e o cabeçalho é exibido com a marca ADOBE.
  _AC-14361 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### Interface do administrador, Conteúdo

* __Exceção &quot;Não é possível criar representação para caminhos de ativos de mídia&quot; durante a inserção da imagem__
Após remover os valores de Largura máxima e Altura máxima da configuração de Otimização de imagem da Galeria de mídia, o erro não ocorre mais durante o processo de otimização de imagem.
  _ACP2E-3781 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Interface do administrador, Segurança

* __Gerenciamento de Senhas Fraco__
O usuário administrador não pode ser salvo ao usar a mesma senha. Anteriormente, ele era salvo com sucesso sem uma validação adequada.
  _ACP2E-3657 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Carrinho e saída

* __Atualização (mini)carrinho do Magento 2.4.7 sem quantidade decimal permitida__
Agora, o Magento lida corretamente ao atualizar a quantidade com decimais do minicarrinho quando a localidade era NL (Holandês)
  _AC-13238 - [Problema do GitHub](https://github.com/magento/magento2/issues/39236) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39669)_
* __[Problema] Atualizar subtotal.phtml__
O sistema atualiza o subtotal.phtml com o espaçamento correto
  _AC-13907 - [Problema do GitHub](https://github.com/magento/magento2/issues/39619) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39612)_
* __Não é possível fazer o pedido com o convidado__
  _AC-14241 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/27217d0e)_
* __Cotações persistentes expiradas não são excluídas por um trabalho cron sales_clean_quotes__
As aspas persistentes expiradas agora são apagadas quando a tarefa cron &#39;persistent_clear_expired&#39; é executada. Anteriormente, as aspas persistentes expiradas não eram apagadas por nenhum outro trabalho cron.
  _ACP2E-3493 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/11be3dff)_
* __Erro &quot;Algo deu errado&quot; no check-out para a empresa inativa__
Antes da correção, a ação de logout não era concluída corretamente na página do carrinho, se a empresa do usuário conectado não estava mais habilitada. Agora, se a empresa não estiver mais disponível, o logout será executado corretamente.
  _ACP2E-3541 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_
* __A seleção de endereços não é salva quando &quot;Fizemos Check-out com Vários Endereços&quot;__
Antes da correção ao cancelar a opção de envio múltiplo, o endereço não era pré-selecionado ao reverter para o envio múltiplo. Agora, o endereço padrão é substituído por uma das seleções feitas na tela de envio múltiplo.
  _ACP2E-3646 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Carrinho e check-out, envio

* __[Linha principal] A regra de preço do carrinho não respeita o envio múltiplo__
Antes da implementação desta correção, a regra de preço do carrinho para produtos de vários envios não era aplicada corretamente quando as condições de subseleção eram aplicadas e o frete gratuito era ativado. No entanto, desde que a correção foi aplicada, a regra de preço do carrinho para carrinhos de vários envios agora funciona conforme esperado.
  _ACP2E-3666 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo

* __Fpc de cache duplicado para a mesma página com a mesma consulta__
O sistema agora identifica corretamente e usa o mesmo Cache de página cheia (FPC) para páginas com os mesmos parâmetros de consulta, independentemente da ordem ou dos caracteres à direita. Isso evita um aumento desnecessário no tamanho da pasta de cache da página. Anteriormente, o sistema criaria um identificador FPC diferente para a mesma página se a ordem dos parâmetros de consulta fosse diferente ou se houvesse caracteres à direita, resultando em um aumento no tamanho da pasta de cache da página.
  _AC-10722 - [Problema do GitHub](https://github.com/magento/magento2/issues/38269) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38270)_
* __Indexação de colunas necessárias ausente na tabela catalog_product_entity_int__
Adição da indexação ausente das colunas necessárias na tabela catalog_product_entity_int
  _AC-10844 - [Problema do GitHub](https://github.com/magento/magento2/issues/38315) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38316)_
* __A página do produto contém um erro devido a regravações de URL__
Agora, a página do produto é carregada com sucesso quando temos regravações de URL
  _AC-2950 - [Problema do GitHub](https://github.com/magento/magento2/issues/35371) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39670)_
* __indexer_update_all_views corn erro com MAGE_INDEXER_THREADS_COUNT__
Corrigido o problema de MAGE_INDEXER_THREADS_COUNT > 2 com o indexador de segmento do cliente
  _ACP2E-3538 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_
* __Exceção ao adicionar a &quot;Combinação de Condições&quot; na condição do widget Produtos do Page Builder__
O problema foi corrigido adicionando uma verificação para ignorar condições ausentes ou incompletas. Anteriormente, isso gerava registros de erros devido à manipulação de condições incompletas no sistema.
  _ACP2E-3545 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/11be3dff)_
* __Falha do navegador ao carregar o conjunto de atributos__
O navegador não trava mais na página de edição do conjunto de atributos se houver mais de 4k atributos de produto
  _ACP2E-3633 - [Problema do GitHub](https://github.com/magento/magento2/issues/38810) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_
* __[NUVEM] substituições de URL de produto não criadas para nova loja: Bloqueador Go Live__
As substituições de URL de produto para o novo armazenamento foram criadas com êxito.
A operação anterior terminou com vazamento de memória ou com tempo limite.
  _ACP2E-3669 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_
* __Valor Padrão de Atributo para Opções que Não Funcionam__
Anteriormente, quando alterávamos o valor padrão de um atributo de seleção de produto, ele aparecia como um elemento de matriz com os valores anteriores. Após a aplicação dessa correção, ao atualizar um valor de atributo de produto, ele será salvo como um único elemento na tabela eav_attribute.
  _ACP2E-3688 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Catálogo, GraphQL, Pesquisa

* __O graphql de produtos retornou categorias desabilitadas nas agregações de categorias__
Após a correção, as categorias desativadas não são retornadas para a solicitação de GraphQl de produtos.
  _ACP2E-2885 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo, Produto

* __[Bug Aleatório] A biblioteca Fotorama não foi carregada__
O sistema agora garante que a biblioteca Fotorama seja carregada corretamente, permitindo que todas as imagens anexadas sejam exibidas na galeria de imagens, conforme esperado. Anteriormente, somente a primeira imagem estava visível devido a um problema com a biblioteca Fotorama não carregando corretamente.
  _AC-12124 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/27217d0e)_

### Conteúdo

* __Colocar csp_whitelist.xml no tema não funciona e cria um problema intermitente__
Implementação do armazenamento em cache da lista de permissões da CSP por área do site.
  _AC-13069 - [Problema do GitHub](https://github.com/magento/magento2/issues/38933) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39672)_
* __Erro: erro de script para &quot;Magento_Catalog/js/validate-product&quot; para pagebuilder de conteúdo administrativo com carregamento de produtos__
Esta PR corrige o erro de script para catalogAddToCart ao editar o pagebuilder com a condição de produtos
  _AC-13891 - [Problema do GitHub](https://github.com/magento/magento2/issues/39604) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39677)_
* __Bloquear seleção em widgets com o mesmo identificador__
O Sistema agora lida corretamente com a seleção de blocos ao criar widgets quando temos os mesmos blocos de identificador
  _AC-14132 - [Problema do GitHub](https://github.com/magento/magento2/issues/39692) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39722)_
* __O prefixo da tabela não foi levado em conta__
  _AC-14556 - [Problema do GitHub](https://github.com/magento/magento2/issues/39847) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_
* __Não é possível carregar a imagem com largura relativamente pequena__
O sistema não falha mais ao redimensionar a imagem com largura relativamente pequena até sua altura.
  _ACP2E-3558 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_
* __Caminho de configuração incorreto para a configuração de estilo do caminho de armazenamento remoto__
Após a correção, definir a configuração de estilo do caminho de armazenamento remoto afetará a configuração real de estilo do caminho AWS S3.
  _ACP2E-3734 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Estrutura

* __Compilando o código do módulo desabilitado.__
Essa solicitação de pull escapa de módulos desativados antes da compilação do código.
  _AC-10933 - [Problema do GitHub](https://github.com/magento/magento2/issues/38241) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39723)_
* __Modelo Magento_Theme title.phtml inválido para PHP 8.2__
Esta solicitação pull corrige um problema quando a página do CMS criada com o cabeçalho nulo como no Php 8.x transmitindo null para trim() gera uma exceção: funcionalidade obsoleta: trim(): transmitindo null para o parâmetro #1 ($string) do tipo string
  _AC-12856 - [Problema do GitHub](https://github.com/magento/magento2/issues/39092) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39398)_
* __Ao usar o armazenamento de arquivos para o provedor de bloqueio, obtemos um diretório de arquivos em constante crescimento sem que ocorra qualquer limpeza__
Essa solicitação de pull apresenta um novo trabalho cron que é executado uma vez por dia e procura por arquivos bloqueados que não foram modificados nas últimas 24 horas e que podem, portanto, ser removidos com segurança. Isso manterá o conteúdo do diretório de arquivos de bloqueio sob controle.
Este trabalho do CRON só executará algo quando o provedor de bloqueio estiver configurado para usar arquivos, não quando um dos outros for usado (banco de dados - o padrão, zookeeper ou cache)
  _AC-13367 - [Problema do GitHub](https://github.com/magento/magento2/issues/39369) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39372)_
* __[Limpeza de problema]: não use o valor de retorno nulo das chamadas de método.__
Essa PR faz uma limpeza mínima. Às vezes, chamamos métodos que não retornavam nada (void) e, em seguida, usamos esse valor de resultado. O que não é realmente necessário.
  _AC-13664 - [Problema do GitHub](https://github.com/magento/magento2/issues/39524) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39516)_
* __[Problema] [PHPDOC] Corrigir phpdoc inválido para Magento\Framework\Message\ManagerInterface__
Esta PR corrige o phpdoc inválido para \Magento\Framework\Message\ManagerInterface e remove todos os phpdoc duplicados em \Magento\Framework\Message\Manager (use a sintaxe inheritdoc).
  _AC-14312 - [Problema do GitHub](https://github.com/magento/magento2/issues/39593) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39153)_
* __Estabilidade mínima beta removida de composer.json__
Estabilidade mínima beta removida de composer.json
  _AC-14450 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1cbbf187)_
* __allow_parallel_generation deve ser definido por meio da variável de ambiente__
Após a correção, a variável de ambiente &quot;MAGENTO_DC_CACHE_ALLOW_PARALLEL_GENERATION&quot; pode ser usada para definir a configuração &quot;allow_parallel_generation&quot;.
  _ACP2E-3673 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_
* __[Nuvem] A alteração do tipo de coluna da tabela de Int para Decimal usando o arquivo db_schema.xml no Magento 2 resulta em erros__
A alteração do tipo de dados da coluna não está funcionando corretamente. Anteriormente, ele emitia um erro: o atributo &quot;identidade&quot; não era permitido.
  _ACP2E-3709 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_
* __Novo suporte a moeda (XCG) no Adobe__
Caribbean Guilder (XCG) é adicionado à lista de moedas.
  _ACP2E-3790 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

* __A Resposta do GraphQL para posicionamento do Pedido não inclui a mensagem de exceção__
Revertida a alteração anterior que retornava erros em um formato diferente. Agora, os erros em potencial são retornados de maneira consistente, sem quebrar o esquema do GraphQL. Deve ser adicionado como BIC conhecido, aprovado pelo PM no ACP2E-3399
  _ACP2E-3399 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_
* __A resposta da GraphQL para o posicionamento do pedido foi parcialmente localizada__
Erros retornados pela mutação placeOrder GraphQl não foram totalmente localizados. Agora, em um contexto multilíngue, os erros são traduzidos corretamente.
  _ACP2E-3506 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_
* __Chamadas simultâneas para reordenar a API do GraphQL - Mesmos produtos adicionados a linhas diferentes__
Correção do problema em que chamadas simultâneas para a API Reorder GraphQL resultam na adição dos mesmos produtos como linhas diferentes, gerando inconsistências de dados.
  _ACP2E-3774 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_
* __mutação do GraphQL updateCustomerEmail (Alterar endereço de email) não aciona a Notificação de email__
Anteriormente, os emails não eram enviados aos clientes depois de atualizarem com êxito seus endereços de email em suas contas. Após a aplicação da correção, os clientes agora recebem notificações por email depois de atualizar seus endereços de email com êxito.
  _ACP2E-3785 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_
* __Atributo dinâmico não atualizado no Registro de presentes por meio da mutação updateGiftRegistry__
Anteriormente, antes dessa correção por meio da mutação updateGiftRegistry, o atributo personalizado do registro do presente não era modificado ou atualizado por meio das mutações do GraphQL. Depois que essa correção for aplicada, o atributo dinâmico do registro de presentes poderá ser atualizado com êxito por meio da mutação updateGiftRegistry.
  _ACP2E-3805 - [Problema do GitHub](https://mcstaging.briscoes.co.nz/)_

### Importar/exportar

* __[Problema] Copyedit: alterar &quot;copiar&quot; para &quot;copiar&quot;__
PR corrige o copyedit secundário para corrigir a ortografia de &quot;copiando&quot;
  _AC-13300 - [Problema do GitHub](https://github.com/magento/magento2/issues/39311) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39307)_
* O Json de Importação de Produto do ponto de extremidade __REST não valida os campos obrigatórios__
O campo Nome agora é necessário ao criar novos produtos por meio do processo de importação (administrador ou API). Antes da correção, você poderia ter criado novos produtos sem o nome. Isso quebraria a interface do administrador e criaria produtos inválidos.
  _ACP2E-3660 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_
* __Opção de Filtro de Site Ausente no Processo de Exportação__
Agora é possível filtrar produtos por sites ao criar exportações de produtos.
  _ACP2E-3720 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_
* __Duplicata de AC-13913 - Limpeza assíncrona de atributo estático.__
Após a correção, não há erro &quot;Apply_to&quot; de chave de matriz indefinida quando várias instâncias do \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType são criadas.
  _ACP2E-3752 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Inventário / MSI

* __A Escolha de Armazenamento não respeita o raio de pesquisa máximo quando o endereço é alterado no check-out__
Agora, a loja pré-selecionada em &quot;Separar na loja&quot; será atualizada se o endereço de entrega mudar. Anteriormente, uma vez que uma loja era pré-selecionada, ela não era alterada mesmo se o novo endereço de entrega não estivesse dentro do raio da loja selecionada
  _ACP2E-3728 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/07620383)_

### Pedido

* __Não é possível retornar nulo para o campo não anulável \&amp;quot;AppliedCoupon.code\&amp;quot; problema inesperado__
  _AC-14484 - [Problema do GitHub](https://github.com/magento/magento2/issues/39841) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

### Ordem, Preços

* __O administrador exibe um símbolo de moeda incorreto no ao criar o retorno__
Em uma configuração de vários sites com moedas diferentes (EUR/USD/GBP), a página de seleção de produto de retorno no admin agora exibe o símbolo de moeda correto. Anteriormente, ele exibia o símbolo de moeda padrão.
  _ACP2E-3658 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Outras ferramentas de desenvolvedor

* __Falha de acessibilidade do Lighthouse__
O sistema agora é aprovado com uma pontuação de acessibilidade de 100
  _AC-12783 - [Problema do GitHub](https://github.com/magento/magento2/issues/39054) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39164)_
* __Desabilitar a configuração da loja captcha ainda carrega os arquivos captcha js__
O sistema agora não carrega arquivos captcha js quando desativamos captcha para loja
  _AC-14267 - [Problema do GitHub](https://github.com/magento/magento2/issues/32987) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39154)_

### Pagamentos

* __[Problema] Corrigir captura de fatura offline (404)__
Ele corrige o erro de página 404 ao capturar faturas de métodos de pagamento offline do administrador do Magento
  _AC-13336 - [Problema do GitHub](https://github.com/magento/magento2/issues/39298) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39297)_

### Produto

* __Coleção de produtos - addMediaGalleryData chama getSize quando a coleção pode ou será carregada (A contagem pode ser usada para evitar uma consulta de BD extra)__
Esta PR reduz a chamada de consulta extra usando count() se a coleção de produtos já estiver carregada ao chamar o Graphql do produto com o campo media_gallery incluído.
  _AC-13055 - [Problema do GitHub](https://github.com/magento/magento2/issues/39111) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39681)_
* __[2.4.8] Nenhum retorno de chamada encontrado para o trabalho cron catalog_product_alert__
  _AC-14494 - [Problema do GitHub](https://github.com/magento/magento2/issues/39800) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_
* __A consulta lenta é executada quando o widget do produto é incluído via pagebuilder__
A Consulta para a criação de widgets de produtos, incluindo SKUs de produtos, é otimizada.
  _ACP2E-3449 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_
* __Imagens de produto não redimensionadas quando adicionadas como produto configurável__
Anteriormente, as imagens adicionadas por meio das Configurações no painel de administração não seguiam o limite de tamanho máximo do upload, o que poderia levar a inconsistências e desafios de gerenciamento. Agora, uma correção foi implementada para garantir que as imagens sejam redimensionadas automaticamente durante o upload para atender ao limite de tamanho máximo, simplificando o processo e mantendo os padrões do sistema.
  _ACP2E-3504 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Envio

* __[DHL] - Lide com dimensões opcionais em configurações de tamanho normais e variação de preço entre integrações REST e API XML__
  _AC-14601 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1e3bde4c)_
* __Exceção ao criar o rótulo de remessa UPS__
Aviso fixo: conversão de matriz em sequência de caracteres durante a criação do rótulo de remessa UPS
  _ACP2E-3676 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Preparo e visualização

* __Visualizar uma atualização agendada abre a exibição da primeira loja em ordem alfabética em vez da exibição da loja de interesse__
Antes da correção, a visualização de uma atualização agendada era aberta na primeira exibição da loja em ordem alfabética, em vez da exibição da loja atribuída.
Após a correção, a pré-visualização agora é aberta corretamente na visualização de loja atribuída à atualização de preparo de bloco do CMS.
  _ACP2E-3671 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_
