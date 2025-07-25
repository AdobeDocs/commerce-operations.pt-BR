---
source-git-commit: 2f471a1bc1cbf31076aeb67ceaee289196841cd4
workflow-type: tm+mt
source-wordcount: '2806'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.9-alpha1)

## Correção de problemas na v2.4.9-alpha1

Corrigimos 67 problemas no código principal Magento Open Source 2.4.9-alpha1. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

#### A operação em massa assíncrona permanece no estado aberto para async.magento.configurableproduct.api.optionrepositoryinterface.save.post

Os pontos de extremidade de API em massa agora emitirão um erro se o corpo da solicitação não for uma Matriz, exigindo que as chaves de item em massa sejam números consecutivos começando de 0. Anteriormente, o status do item em massa não era atualizado devido à chave de item arbitrária enviada na solicitação em massa.

_ACP2E-3544 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### O bug REST da API da [NUVEM] no valor is_subscribed não está sendo considerado do repositório atual usando searchCriteria

REST da API A consulta do cliente busca o valor &quot;is_subscribed&quot; correto no armazenamento correto usando searchCriteria
Anteriormente, a consulta do cliente REST da API não considerava o armazenamento ao buscar o valor &quot;is_subscribed&quot;.

_ACP2E-3621 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all pode criar várias entradas para 1 SKU

As solicitações simultâneas para salvar e atualizar o mesmo produto agora são serializadas para evitar condições de corrida que podem resultar em inconsistência de dados ou produtos duplicados

_ACP2E-3744 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Conta

#### A operação de exclusão da [Nuvem] é proibida para o erro de área atual durante a criação da conta do cliente

Após a correção, salvar um cliente com um endereço inválido retorna uma mensagem descrevendo o motivo da invalidez em vez de &quot;A operação de exclusão é proibida para a área atual&quot; irrelevante.

_ACP2E-3791 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Interface do administrador

#### [Problema] Melhore a experiência do usuário com a árvore de funções

Essa solicitação de pull adiciona botões para recolher tudo, expandir tudo e expandir ramificações com itens selecionados. Essa funcionalidade é semelhante à fornecida na árvore de categorias (Catálogo -> Inventário -> Categorias)

_AC-14020 - [Problema do GitHub](https://github.com/magento/magento2/issues/39654) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36511)_

#### Symfony\Component\Mime\Exception\LogicException: o cabeçalho &quot;Remetente&quot; deve ser uma instância de &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (obteve &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

_AC-14520 - [Problema do GitHub](https://github.com/magento/magento2/issues/39823) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1e14bd72)_

#### Fornecer um recurso para excluir alíquotas de imposto em massa usando a grade

Os usuários administradores agora podem excluir simultaneamente várias alíquotas de imposto da grade Alíquotas de imposto administrativas.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [Problema do GitHub](https://github.com/magento/magento2/issues/33399) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33484) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_

#### A regra de preço do carrinho com a condição SKU não considera os &quot;zeros à esquerda&quot; no SKU (sku: 01234 é o mesmo que 1234)

Agora o sistema lida corretamente com a regra de preço do carrinho com a SKU de condição. Considere os &quot;zeros à esquerda&quot; na SKU

_AC-9428 - [Problema do GitHub](https://github.com/magento/magento2/issues/37919) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39525)_

#### Problema com o Comportamento do Valor da Opção de Atributo Padrão para Multisseleção

Antes da correção, os valores padrão para o atributo de várias opções não eram salvos corretamente. Agora, após a correção, os valores são armazenados corretamente no banco de dados.

_ACP2E-3523 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Problema ao mover a quantidade do produto do administrador para o carrinho de compras

Ao criar um pedido do administrador, os produtos no carrinho do cliente na barra lateral não desaparecerão quando adicionados ao pedido.

_ACP2E-3563 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Interface do administrador, B2B

#### O logon B2B como cabeçalho do cliente ainda tem a marca Magento

Anteriormente, o cabeçalho da loja exibe &quot;Agora você está conectado como &lt;nome do cliente> na &lt;nome da loja>&quot; com a marca Magento. Que agora foi corrigida e o cabeçalho é exibido com a marca ADOBE.

_AC-14361 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### Interface do administrador, Conteúdo

#### Exceção &quot;Não é possível criar representação para caminhos de ativos de mídia&quot; durante a inserção da imagem

Após remover os valores de Largura máxima e Altura máxima da configuração de Otimização de imagem da Galeria de mídia, o erro não ocorre mais durante o processo de otimização de imagem.

_ACP2E-3781 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Interface do administrador, Segurança

#### Gerenciamento de Senhas Fracas

O usuário administrador não pode ser salvo ao usar a mesma senha. Anteriormente, ele era salvo com sucesso sem uma validação adequada.

_ACP2E-3657 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Carrinho e saída

#### Atualização (mini)carrinho do Magento 2.4.7 sem quantidade decimal permitida

Agora, o Magento lida corretamente ao atualizar a quantidade com decimais do minicarrinho quando a localidade era NL (Holandês)

_AC-13238 - [Problema do GitHub](https://github.com/magento/magento2/issues/39236) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39669)_

#### [Problema] Atualizar subtotal.phtml

O sistema atualiza o subtotal.phtml com o espaçamento correto

_AC-13907 - [Problema do GitHub](https://github.com/magento/magento2/issues/39619) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39612)_

#### Não é possível fazer o pedido com o convidado

_AC-14241 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### Cotações persistentes expiradas não são excluídas por um trabalho cron sales_clean_quotes

As aspas persistentes expiradas agora são apagadas quando a tarefa cron &#39;persistent_clear_expired&#39; é executada. Anteriormente, as aspas persistentes expiradas não eram apagadas por nenhum outro trabalho cron.

_ACP2E-3493 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Erro &quot;Algo deu errado&quot; no check-out para empresa inativa

Antes da correção, a ação de logout não era concluída corretamente na página do carrinho, se a empresa do usuário conectado não estava mais habilitada. Agora, se a empresa não estiver mais disponível, o logout será executado corretamente.

_ACP2E-3541 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### A seleção de endereços não é salva quando &quot;Fazemos check-out com vários endereços&quot;

Antes da correção ao cancelar a opção de envio múltiplo, o endereço não era pré-selecionado ao reverter para o envio múltiplo. Agora, o endereço padrão é substituído por uma das seleções feitas na tela de envio múltiplo.

_ACP2E-3646 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Carrinho e check-out, envio

#### [Linha principal] A regra de preço do carrinho não respeita o envio múltiplo

Antes da implementação desta correção, a regra de preço do carrinho para produtos de vários envios não era aplicada corretamente quando as condições de subseleção eram aplicadas e o frete gratuito era ativado. No entanto, desde que a correção foi aplicada, a regra de preço do carrinho para carrinhos de vários envios agora funciona conforme esperado.

_ACP2E-3666 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo

#### Duplicar fpc de cache para a mesma página com a mesma consulta

O sistema agora identifica corretamente e usa o mesmo Cache de página cheia (FPC) para páginas com os mesmos parâmetros de consulta, independentemente da ordem ou dos caracteres à direita. Isso evita um aumento desnecessário no tamanho da pasta de cache da página. Anteriormente, o sistema criaria um identificador FPC diferente para a mesma página se a ordem dos parâmetros de consulta fosse diferente ou se houvesse caracteres à direita, resultando em um aumento no tamanho da pasta de cache da página.

_AC-10722 - [Problema do GitHub](https://github.com/magento/magento2/issues/38269) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38270)_

#### Indexação de colunas necessárias ausente na tabela catalog_product_entity_int

Adição da indexação ausente das colunas necessárias na tabela catalog_product_entity_int

_AC-10844 - [Problema do GitHub](https://github.com/magento/magento2/issues/38315) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38316)_

#### A página do produto fornece erro devido a regravações de URL

Agora, a página do produto é carregada com sucesso quando temos regravações de URL

_AC-2950 - [Problema do GitHub](https://github.com/magento/magento2/issues/35371) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39670)_

#### erro indexer_update_all_views cron com MAGE_INDEXER_THREADS_COUNT

Corrigido o problema de MAGE_INDEXER_THREADS_COUNT > 2 com o indexador de segmento do cliente

_ACP2E-3538 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Exceção ao adicionar &quot;Combinação de condições&quot; na condição do widget Produtos do Page Builder

O problema foi corrigido adicionando uma verificação para ignorar condições ausentes ou incompletas. Anteriormente, isso gerava registros de erros devido à manipulação de condições incompletas no sistema.

_ACP2E-3545 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Falha do navegador ao carregar o conjunto de atributos

O navegador não trava mais na página de edição do conjunto de atributos se houver mais de 4k atributos de produto

_ACP2E-3633 - [Problema do GitHub](https://github.com/magento/magento2/issues/38810) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [NUVEM] substituições de URL de produto não criadas para nova loja: Bloqueador Go Live

As substituições de URL de produto para o novo armazenamento foram criadas com êxito.
A operação anterior terminou com vazamento de memória ou com tempo limite.

_ACP2E-3669 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Valor padrão de atributo para opções que não funcionam

Anteriormente, quando alterávamos o valor padrão de um atributo de seleção de produto, ele aparecia como um elemento de matriz com os valores anteriores. Após a aplicação dessa correção, ao atualizar um valor de atributo de produto, ele será salvo como um único elemento na tabela eav_attribute.

_ACP2E-3688 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Catálogo, GraphQL, Pesquisa

#### O graphql de produtos retornou categorias desabilitadas nas agregações de categorias

Após a correção, as categorias desativadas não são retornadas para a solicitação de GraphQl de produtos.

_ACP2E-2885 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo, Produto

#### [Bug Aleatório] A biblioteca Fotorama não está carregada

O sistema agora garante que a biblioteca Fotorama seja carregada corretamente, permitindo que todas as imagens anexadas sejam exibidas na galeria de imagens, conforme esperado. Anteriormente, somente a primeira imagem estava visível devido a um problema com a biblioteca Fotorama não carregando corretamente.

_AC-12124 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/27217d0e)_

### Conteúdo

#### A inserção de csp_whitelist.xml no tema não funciona e cria um problema intermitente

Implementação do armazenamento em cache da lista de permissões da CSP por área do site.

_AC-13069 - [Problema do GitHub](https://github.com/magento/magento2/issues/38933) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39672)_

#### Erro: erro de script para &quot;Magento_Catalog/js/validate-product&quot; para pagebuilder do conteúdo administrativo com carregamento de produtos

Esta PR corrige o erro de script para catalogAddToCart ao editar o pagebuilder com a condição de produtos

_AC-13891 - [Problema do GitHub](https://github.com/magento/magento2/issues/39604) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39677)_

#### Bloquear seleção em widgets com o mesmo identificador

O Sistema agora lida corretamente com a seleção de blocos ao criar widgets quando temos os mesmos blocos de identificador

_AC-14132 - [Problema do GitHub](https://github.com/magento/magento2/issues/39692) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39722)_

#### O prefixo da tabela não é levado em conta

_AC-14556 - [Problema do GitHub](https://github.com/magento/magento2/issues/39847) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Não é possível carregar a imagem com largura relativamente pequena

O sistema não falha mais ao redimensionar a imagem com largura relativamente pequena até sua altura.

_ACP2E-3558 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Caminho de configuração incorreto para configuração de estilo de caminho de armazenamento remoto

Após a correção, definir a configuração de estilo do caminho de armazenamento remoto afetará a configuração real de estilo do caminho AWS S3.

_ACP2E-3734 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Estrutura

#### Compilando código do módulo desabilitado.

Essa solicitação de pull escapa de módulos desativados antes da compilação do código.

_AC-10933 - [Problema do GitHub](https://github.com/magento/magento2/issues/38241) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39723)_

#### Modelo Magento_Theme title.phtml inválido para PHP 8.2

Esta solicitação pull corrige um problema quando a página do CMS criada com o cabeçalho nulo como no Php 8.x transmitindo null para trim() gera uma exceção: funcionalidade obsoleta: trim(): transmitindo null para o parâmetro #1 ($string) do tipo string

_AC-12856 - [Problema do GitHub](https://github.com/magento/magento2/issues/39092) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39398)_

#### Ao usar o armazenamento de arquivos para o provedor de bloqueio, obtemos um diretório de arquivos em constante crescimento sem que ocorra qualquer limpeza

Essa solicitação de pull apresenta um novo trabalho cron que é executado uma vez por dia e procura por arquivos bloqueados que não foram modificados nas últimas 24 horas e que podem, portanto, ser removidos com segurança. Isso manterá o conteúdo do diretório de arquivos de bloqueio sob controle.
Este trabalho do CRON só executará algo quando o provedor de bloqueio estiver configurado para usar arquivos, não quando um dos outros for usado (banco de dados - o padrão, zookeeper ou cache)

_AC-13367 - [Problema do GitHub](https://github.com/magento/magento2/issues/39369) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39372)_

#### [Limpeza de problema]: não use o valor de retorno nulo das chamadas de método.

Essa PR faz uma limpeza mínima. Às vezes, chamamos métodos que não retornavam nada (void) e, em seguida, usamos esse valor de resultado. O que não é realmente necessário.

_AC-13664 - [Problema do GitHub](https://github.com/magento/magento2/issues/39524) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39516)_

#### [Problema] [PHPDOC] Corrigir phpdoc inválido para Magento\Framework\Message\ManagerInterface

Esta PR corrige o phpdoc inválido para \Magento\Framework\Message\ManagerInterface e remove todos os phpdoc duplicados em \Magento\Framework\Message\Manager (use a sintaxe inheritdoc).

_AC-14312 - [Problema do GitHub](https://github.com/magento/magento2/issues/39593) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39153)_

#### Estabilidade mínima beta removida de composer.json

Estabilidade mínima beta removida de composer.json

_AC-14450 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1cbbf187)_

#### allow_parallel_generation deve ser definido por meio da variável de ambiente

Após a correção, a variável de ambiente &quot;MAGENTO_DC_CACHE_ALLOW_PARALLEL_GENERATION&quot; pode ser usada para definir a configuração &quot;allow_parallel_generation&quot;.

_ACP2E-3673 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Nuvem] A alteração do tipo de coluna da tabela de Int para Decimal usando o arquivo db_schema.xml no Magento 2 resulta em erros

A alteração do tipo de dados da coluna não está funcionando corretamente. Anteriormente, ele emitia um erro: o atributo &quot;identidade&quot; não era permitido.

_ACP2E-3709 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Novo suporte a moeda (XCG) no Adobe

Caribbean Guilder (XCG) é adicionado à lista de moedas.

_ACP2E-3790 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

#### O GraphQL Response for Order placement não inclui a mensagem de exceção

Revertida a alteração anterior que retornava erros em um formato diferente. Agora, os erros em potencial são retornados de maneira consistente, sem quebrar o esquema do GraphQL. Deve ser adicionado como BIC conhecido, aprovado pelo PM no ACP2E-3399

_ACP2E-3399 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### O GraphQL Response for Order placement está parcialmente localizado

Erros retornados pela mutação placeOrder GraphQl não foram totalmente localizados. Agora, em um contexto multilíngue, os erros são traduzidos corretamente.

_ACP2E-3506 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Chamadas simultâneas para reordenar a API do GraphQL - Mesmos produtos adicionados a linhas diferentes

Correção do problema em que chamadas simultâneas para a API Reorder GraphQL resultam na adição dos mesmos produtos como linhas diferentes, gerando inconsistências de dados.

_ACP2E-3774 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail A mutação do GraphQL (Alterar endereço de email) não aciona o email Notificação

Anteriormente, os emails não eram enviados aos clientes depois de atualizarem com êxito seus endereços de email em suas contas. Após a aplicação da correção, os clientes agora recebem notificações por email depois de atualizar seus endereços de email com êxito.

_ACP2E-3785 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Atributo dinâmico não atualizado no Registro de presentes por meio da mutação updateGiftRegistry

Anteriormente, antes dessa correção por meio da mutação updateGiftRegistry, o atributo personalizado do registro do presente não era modificado ou atualizado por meio das mutações do GraphQL. Depois que essa correção for aplicada, o atributo dinâmico do registro de presentes poderá ser atualizado com êxito por meio da mutação updateGiftRegistry.

_ACP2E-3805 - [Problema do GitHub](https://mcstaging.briscoes.co.nz/)_

### Importar/exportar

#### [Problema] Copyedit: alterar &quot;copiar&quot; para &quot;copiar&quot;

PR corrige o copyedit secundário para corrigir a ortografia de &quot;copiando&quot;

_AC-13300 - [Problema do GitHub](https://github.com/magento/magento2/issues/39311) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39307)_

#### O Json de importação de produto do ponto de extremidade REST não valida os campos obrigatórios

O campo Nome agora é necessário ao criar novos produtos por meio do processo de importação (administrador ou API). Antes da correção, você poderia ter criado novos produtos sem o nome. Isso quebraria a interface do administrador e criaria produtos inválidos.

_ACP2E-3660 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Opção de filtro de site ausente no processo de exportação

Agora é possível filtrar produtos por sites ao criar exportações de produtos.

_ACP2E-3720 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Duplicata de AC-13913 - Limpeza assíncrona de atributo estático.

Após a correção, não há erro &quot;Apply_to&quot; de chave de matriz indefinida quando várias instâncias do \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType são criadas.

_ACP2E-3752 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Inventário / MSI

#### A retirada de armazenamento não respeita o raio máximo de pesquisa quando o endereço é alterado no check-out

Agora, a loja pré-selecionada em &quot;Separar na loja&quot; será atualizada se o endereço de entrega mudar. Anteriormente, uma vez que uma loja era pré-selecionada, ela não era alterada mesmo se o novo endereço de entrega não estivesse dentro do raio da loja selecionada

_ACP2E-3728 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/07620383)_

### Pedido

#### Não é possível retornar nulo para campo não anulável \&amp;quot;AppliedCoupon.code\&amp;quot; problema inesperado

_AC-14484 - [Problema do GitHub](https://github.com/magento/magento2/issues/39841) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

### Ordem, Preços

#### O administrador exibe um símbolo de moeda incorreto na ao criar a devolução

Em uma configuração de vários sites com moedas diferentes (EUR/USD/GBP), a página de seleção de produto de retorno no admin agora exibe o símbolo de moeda correto. Anteriormente, ele exibia o símbolo de moeda padrão.

_ACP2E-3658 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Outras ferramentas de desenvolvedor

#### Falha de acessibilidade do Lighthouse

O sistema agora é aprovado com uma pontuação de acessibilidade de 100

_AC-12783 - [Problema do GitHub](https://github.com/magento/magento2/issues/39054) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39164)_

#### Desativar a configuração da loja captcha ainda carrega os arquivos captcha js

O sistema agora não carrega arquivos captcha js quando desativamos captcha para loja

_AC-14267 - [Problema do GitHub](https://github.com/magento/magento2/issues/32987) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39154)_

### Pagamentos

#### [Problema] Corrigir captura de fatura offline (404)

Ele corrige o erro de página 404 ao capturar faturas de métodos de pagamento offline do administrador do Magento

_AC-13336 - [Problema do GitHub](https://github.com/magento/magento2/issues/39298) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39297)_

### Produto

#### Coleção de produtos - addMediaGalleryData chama getSize quando a coleção pode ou será carregada (Pode usar count para evitar uma consulta DB extra)

Esta PR reduz a chamada de consulta extra usando count() se a coleção de produtos já estiver carregada ao chamar o Graphql do produto com o campo media_gallery incluído.

_AC-13055 - [Problema do GitHub](https://github.com/magento/magento2/issues/39111) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39681)_

#### [2.4.8] Nenhum retorno de chamada encontrado para o trabalho cron catalog_product_alert

_AC-14494 - [Problema do GitHub](https://github.com/magento/magento2/issues/39800) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### A consulta lenta é executada quando o widget do produto é incluído pelo pagebuilder

A Consulta para a criação de widgets de produtos, incluindo SKUs de produtos, é otimizada.

_ACP2E-3449 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Imagens de produto não redimensionadas quando adicionadas como produto configurável

Anteriormente, as imagens adicionadas por meio das Configurações no painel de administração não seguiam o limite de tamanho máximo do upload, o que poderia levar a inconsistências e desafios de gerenciamento. Agora, uma correção foi implementada para garantir que as imagens sejam redimensionadas automaticamente durante o upload para atender ao limite de tamanho máximo, simplificando o processo e mantendo os padrões do sistema.

_ACP2E-3504 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Envio

#### [DHL] - Lide com dimensões opcionais em configurações de tamanho normais e variação de preço entre integrações de REST e API XML

_AC-14601 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1e3bde4c)_

#### Exceção ao criar rótulo de remessa UPS

Aviso fixo: conversão de matriz em sequência de caracteres durante a criação do rótulo de remessa UPS

_ACP2E-3676 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Preparo e visualização

#### Visualizar uma atualização agendada abre a primeira exibição de loja em ordem alfabética em vez da exibição de loja de interesse

Antes da correção, a visualização de uma atualização agendada era aberta na primeira exibição da loja em ordem alfabética, em vez da exibição da loja atribuída.
Após a correção, a pré-visualização agora é aberta corretamente na visualização de loja atribuída à atualização de preparo de bloco do CMS.

_ACP2E-3671 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_
