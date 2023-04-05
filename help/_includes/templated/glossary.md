---
source-git-commit: 405c1d7073e5936aefc7fb3c6eb1d5dd4d69a066
workflow-type: tm+mt
source-wordcount: '6574'
ht-degree: 0%

---
# Glossário do Adobe Commerce

## A

### acima da dobra

_adjetivo_

Em uma janela do navegador, o conteúdo imediatamente visível após uma página da Web ser carregada e antes de um usuário rolar a página para baixo.
Ao projetar o layout, use formatos flexíveis para exibir melhor os produtos, recursos, vendas, notificações, opções de prioridade mais alta nesta área.

Com dispositivos móveis e tablets, a área acima da dobra é muito diferente, especialmente no tamanho e nas dimensões da tela e da orientação na visualização (retrato vs paisagem).
O uso de temas responsivos e testes pode ajudar a encontrar a combinação correta de conteúdo e layout.

_Atributos do termo:_

* _Campo: projeto_

### ramificação ativa

_substantivo_

Uma ramificação ou ambiente ativo é aquela que está conectada a uma instância implantada ou em execução com acesso a serviços.
Quando você desativa, a conexão com os serviços e com a instância em execução é removida, mas o código é preservado.
Torna-se uma ramificação git comum.

_Atributos do termo:_

* _Campo: nuvem_

### adaptador

_substantivo_

Uma classe que permite que dois sistemas que, de outra forma, são incompatíveis funcionem juntos sem modificar o código-fonte dos sistemas.
Exemplos incluem adaptadores de banco de dados, adaptadores de cache, adaptadores de sistema de arquivos, adaptadores de bibliotecas pós-processador e outros tipos de adaptadores de computação.

_Atributos do termo:_

* _Campo: programação_

### administrador

_substantivo_

No software, uma função de usuário com privilégios completos de administrador para gerenciar todas as funcionalidades.
No Adobe Commerce, os usuários administradores têm permissões completas e acesso a todos os recursos, opções e recursos no Administrador.
Eles também podem criar usuários e funções.

Saiba mais: [Adicionar usuários](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Atributos do termo:_

* _Campo: software comercial_
* _Sinônimos: administrador, superusuário_
* _Termos relacionados: administrador de comércio_

### Área de administração

_substantivo_

O back-office protegido por senha da sua loja onde pedidos, catálogo, conteúdo e configurações são gerenciados.
Os usuários acessam a área de Administração para gerenciar a loja, incluindo produtos, pedidos, remessas, conteúdo de CMS, design da loja, informações do cliente e assim por diante.
Os usuários administradores têm uma função associada com permissões que controla o acesso a recursos, opções e recursos.

Saiba mais: [Guia do usuário do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos do termo:_

* _Campo: software comercial_
* _Sinônimos: Admin, Painel de administração, back-end, Interface de administração, Interface de administração_
* _Termos relacionados: administrador_

### Variáveis do ADMIN

_substantivo_

As variáveis ADMIN são variáveis de ambiente do projeto para substituir as configurações da conta de usuário Admin para acessar a interface do usuário Admin.

Saiba mais: [Variáveis do ADMIN](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Atributos do termo:_

* _Campo: administrador, nuvem_

### adminhtml

_substantivo_

O nome da área interna atribuído ao Administrador.

Saiba mais: [Guia do usuário do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: area, administrador de comércio_

### area

_substantivo_

Área é um termo abstrato para um escopo de aplicativo Magento.
Áreas são componentes lógicos que organizam o código para o processamento otimizado de solicitações.
As áreas reduzem as demandas de memória dos objetos de configuração acessados da loja e simplificam as chamadas de serviço da Web ao carregar apenas o código dependente necessário.
Cada área pode conter código completamente diferente para processar URLs e solicitações.

As áreas do Adobe Commerce incluem:

* Admin (adminhtml)
* Loja
* REST da API da Web (webapi_rest)

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: componente de comércio, vitrine_

### atributo

_substantivo_

Uma característica ou propriedade de um produto que descreve algum aspecto do produto.
Usuários do Adobe Commerce ou Magento Open Source podem criar atributos personalizados para adicionar ao conjunto de atributos padrão ou a um conjunto de atributos personalizado.
Crie esses atributos por meio do Administrador ou de um programa.
Exemplos: cor, tamanho, peso, preço, idade, gênero e assim por diante.

Os atributos personalizados são um tipo de atributo de valor de atributo de entidade (EAV).

Para integrações como o Canal de anúncios do Google Shopping e o Sales Channel do Amazon, você mapeia atributos de comércio para atributos de terceiros para exibir e vender produtos corretamente e exibir anúncios.

Saiba mais: [EAV e extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Sinônimos: atributo do produto, atributo personalizado_
* _Termos relacionados: atributo de extensão_

### grupo de atributos

_substantivo_

Um agrupamento lógico de atributos dentro de um conjunto de atributos.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: atributo_

### conjunto de atributos

_substantivo_

Uma coleção de grupos de atributos, personalizada para um produto específico.
Exemplo: Um conjunto de atributos de camiseta pode incluir cor, tamanho, gênero e marca.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: atributo_

### custo médio do inventário

_substantivo_

Preço do produto, menos cupons ou descontos, mais frete e impostos aplicáveis.
A média é determinada adicionando o custo inicial do inventário a cada mês, mais o custo final do inventário para o último mês do período.

_Atributos do termo:_

* _Campo: produto, preço, inventário_

## B

### moeda base

_substantivo_

A moeda principal usada por exibição de loja para todos os pagamentos online.
As lojas podem aceitar moedas de mais de 200 países em todo o mundo.
A frente de loja fornece um seletor de moeda para várias moedas aceitas de um país ou localidade específica.
Os símbolos monetários aparecem nos preços do produto e nos documentos de venda, como pedidos e faturas.
Você pode personalizar os símbolos de moeda conforme necessário e definir a exibição do preço separadamente para cada loja ou exibição.

Saiba mais: [Moeda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Atributos do termo:_

* _Campo: preços_

### processamento em lote

_substantivo_

Para executar uma tarefa ou alterar vários itens de uma só vez, sem a repetição manual.

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: operações em massa_

### bloco

_substantivo_

Uma unidade de saída de página que renderiza algum conteúdo distinto - uma parte das informações, um elemento da interface do usuário - qualquer coisa visualmente tangível para o usuário final.
[Blocos](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) são implementadas e fornecidas por módulos.
Os blocos usam templates para gerar HTML.
Os exemplos de blocos incluem uma lista de categorias, um minicarrinho, tags de produto e uma lista de produtos.

[Blocos dinâmicos](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) fornecer conteúdo com base na lógica, como regras de preço.

O Page Builder se expande na interatividade e na criação de [blocos](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) e [blocos dinâmicos](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Atributos do termo:_

* _Campo: software comercial_
* _Sinônimos: Blocos dinâmicos_
* _Termos relacionados: bloco cms, bloco estático, contêiner, layout_

### marca

_substantivo, verbo_

Uma identidade exclusiva que define um produto ou grupo de produtos específico pelo fabricante ou Designer.
Elas incluem marcas de nome para roupas, eletrodomésticos, artigos de luxo e assim por diante.
Sua empresa também pode ser a marca, vendendo produtos em várias marcas com base na unidade comercial, público-alvo e assim por diante.

Use atributos personalizados para salvar informações de marca de produtos.

Algumas extensões e integrações podem usar ou exigir uma marca para seus produtos, como o Canal de anúncios do Google Shopping e o Sales Channel do Amazon.

_Atributos do termo:_

* _Campo: empresa_

### tijolo e argamassa

_adjetivo_

Uma empresa de varejo com um local físico permanente, em vez de empresas que funcionam virtualmente ou unicamente através da Internet.

Para [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) e [Gerenciamento de pedidos](https://omsdocs.magento.com/getting-started/terminology/), esta loja é uma fonte para rastrear quantidades de produtos, pedidos de envio e suporte à retirada na loja.

_Atributos do termo:_

* _Campo: negócios, inventário_

### operações em massa

_substantivo_

Operações em massa são ações executadas em grande escala.
Exemplos de tarefas de operações em massa incluem importação ou exportação de itens, alteração de preços em uma escala de massa e atribuição de produtos a um depósito.

Saiba mais: [Operações em massa de DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Atributos do termo:_

* _Campo: programação_

### produto de pacote

_substantivo_

Permite que os clientes reúnam um produto personalizável para &quot;criar seu próprio&quot; a partir de várias opções e configurações.
Cada item no pacote é um produto simples ou virtual separado.

Saiba mais: [Produtos configuráveis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: produto simples, produto virtual, tipos de produto_

### extensão agrupada

_substantivo_

O código que estende ou personaliza o comportamento do Adobe Commerce é considerado uma Extensão embutida.
Ele pode incluir módulos, temas e pacotes de idiomas.

_Atributos do termo:_

* _Campo: extensão agrupada, extensão_
* _Sinônimos: extensão_
* _Termos relacionados: extensão, extensão fornecida pelo fornecedor_

## C

### back-end do cache

_substantivo_

Armazena registros de cache em um sistema de back-end de dois níveis dentro da estrutura padrão do Zend.
Um cache de primeiro nível é rápido — por exemplo, um back-end APC ou Memcached — mas é limitado e não suporta marcação e agrupamento de entradas de cache.
Um cache de segundo nível — por exemplo, um sistema de arquivos ou um back-end do Redis — é mais lento, mas oferece suporte para marcação e agrupamento.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: backend_

### front-end de cache

_substantivo_

Especifica o tipo de dados armazenado no back-end do cache.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: frontend_

### tipo de cache

_substantivo_

Um cache armazena dados para que chamadas futuras desses dados sejam carregadas mais rapidamente.

O Adobe Commerce inclui estes tipos:
* Configuração
* Layouts
* Bloquear saída HTML
* Dados de coleções
* Dados de reflexo
* Operações DDL do banco de dados
* Configuração compilada
* Tipos e atributos de EAV
* Notificação do cliente
* Configuração de integrações
* Configuração da API de integrações
* Cache de página (o mais conhecido)
* Configuração dos serviços da Web
* Traduções
* Regra de destino
* Cache do produto Google
* Vertex

Outros tipos podem ser criados e definidos.

_Atributos do termo:_

* _Campo: programação_

### captura

_verbo_

O processo de conversão de um valor de pedido autorizado em uma transação faturável.
As transações não podem ser capturadas até que sejam autorizadas e as autorizações não podem ser capturadas até que os bens ou serviços tenham sido entregues.

_Atributos do termo:_

* _Campo: empresa_
* _Termos relacionados: autorização, status do pedido_

### titular do cartão

_substantivo_

Uma pessoa autorizada por uma instituição financeira a efetuar compras numa conta de cartão de crédito.

_Atributos do termo:_

* _Campo: empresa, pedido_

### regras do carrinho

_substantivo_

As regras de preço que são aplicadas ao carrinho de compras e acionam uma ação em resposta a um conjunto de condições.
Usado para criar promoções.

_Atributos do termo:_

* _Campo: software comercial, preços, produto_
* _Termos relacionados: regras de catálogo, carrinho de compras_

### catálogo

_substantivo_

Para comerciantes, o catálogo representa seu inventário de produtos.
Na arquitetura do Adobe Commerce, o catálogo consiste em categorias, produtos e atributos de produto.

Cada loja do Commerce tem apenas um catálogo de produtos, que é compartilhado por todas as visualizações de loja.
Em uma instalação de várias lojas, cada loja pode ter um catálogo separado ou compartilhar o catálogo.
O catálogo de loja atual é determinado pela categoria raiz padrão, visível ao usuário na navegação superior (menu principal) da loja.
(O termo &quot;categoria raiz&quot; pode ser confuso, pois a &quot;categoria raiz&quot; não é realmente uma categoria, mas um contêiner do menu, que consiste de categorias e subcategorias.)

Você pode criar quantas categorias raiz desejar, mas somente uma (o padrão) pode ser usada de cada vez.

_Atributos do termo:_

* _Campo: software comercial, preços, produto_
* _Termos relacionados: catálogo compartilhado, regra de catálogo_

### regras de catálogo

_substantivo_

As regras de preço que são aplicadas a produtos específicos e acionam uma ação em resposta a um conjunto de condições.
Usado para criar promoções.

_Atributos do termo:_

* _Campo: software comercial, preços, produto_
* _Termos relacionados: regras do carrinho, catálogo_

### categoria

_substantivo_

Um grupo de produtos que tem algo em comum.
O menu principal da loja é organizado em categorias e subcategorias de produtos.

_Atributos do termo:_

* _Campo: software comercial, produto_

### checkout

_substantivo_

O processo de coleta das informações de pagamento e envio necessárias para concluir a compra de itens no carrinho de compras.
Depois que o cliente revisar as informações e enviar o pedido, uma confirmação por email será enviada ao cliente.

O check-out tem muitas opções e configurações prontas para uso e por meio da extensão .

Saiba mais: [Tutorial de check-out](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Atributos do termo:_

* _Campo: empresa, design, pedido, produto, programação_

### variáveis na nuvem

_substantivo_

As variáveis da nuvem são variáveis de ambiente específicas ao Adobe Commerce na infraestrutura da nuvem e usam o **`MAGENTO_CLOUD`** prefixo.

Saiba mais: [Variáveis da nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Atributos do termo:_

* _Campo: nuvem_

### Bloco CMS

_substantivo_

Uma variante especial de [bloco](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) que só pode ser criado no Admin e não pode ser referenciado por meio de arquivos de layout.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: bloco, bloco estático_

### dados complexos

_substantivo_

Dados associados a várias opções de produto.

_Atributos do termo:_

* _Campo: programação_

### componente

_substantivo_

Usado para se referir a um módulo, tema ou pacote de idioma no Adobe Commerce.

_Atributos do termo:_

* _Campo: software comercial_
* _Sinônimos: componente_
* _Termos relacionados: componente ui_

### produto configurável

_substantivo_

Um produto configurável se parece com um único produto com listas suspensas de opções para cada variação.
Cada opção é, na verdade, um produto simples separado com um SKU exclusivo, o que permite rastrear o inventário de cada variação de produto.
Para obter um efeito semelhante, um produto simples pode ser usado com opções personalizadas, mas sem a capacidade de rastrear o inventário para cada variação.
Produtos com várias opções são, às vezes, chamados de produtos compostos.

Embora um produto configurável use mais SKUs e possa demorar um pouco mais para ser configurado, ele pode economizar tempo no final.
Se você planeja expandir sua empresa, o tipo de produto configurável pode ser uma melhor escolha para um produto com várias opções.

Exemplo: Camisas disponíveis em duas cores e três tamanhos.
Seis variantes devem ser criadas como produtos individuais (cada uma com sua própria SKU).
Em seguida, todas as variantes são adicionadas a um produto configurável, onde os clientes podem escolher o tamanho e a cor, e depois adicioná-las ao carrinho.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: tipos de produtos_

### taxa de conversão

_substantivo_

A porcentagem de visitantes convertidos em compradores.

_Atributos do termo:_

* _Campo: empresa, pedido_

### escalação de camada principal

_substantivo_

O dimensionamento da camada principal consiste em três nós de serviço para armazenamento de dados, cache e serviços, como OpenSearch, Elasticsearch, MariaDB, Redis.

_Atributos do termo:_

* _Campo: nuvem_

### aviso de crédito

_substantivo_

Um documento emitido pelo comerciante para um cliente para amortizar um saldo pendente por sobretaxa, desconto ou devolução de bens.
O memorando restaura fundos na conta do cliente.

_Atributos do termo:_

* _Campo: empresa, pedido_

### comentário do aviso de crédito

_substantivo_

Detalhes sobre o motivo pelo qual uma quantia de aviso de crédito foi creditada ao cliente.

_Atributos do termo:_

* _Campo: empresa, pedido_

### item do aviso de crédito

_substantivo_

Um item faturado para o qual um comerciante cria um aviso de crédito.

_Atributos do termo:_

* _Campo: empresa, pedido_

### venda cruzada

_substantivo, adjetivo, verbo_

Um produto que aparece ao lado do carrinho de compras.
Quando um cliente navega até a página do carrinho de compras, esses produtos são exibidos como vendas cruzadas para os itens que já estão no carrinho de compras.
São semelhantes a impulsos de compras, como revistas e doces nas caixas registradoras de compras.

_Atributos do termo:_

* _Campo: empresa, produto_
* _Termos relacionados: venda adicional_

### CVM

_substantivo_

Abreviatura de &quot;Método de verificação do titular do cartão&quot;.
Uma forma de verificar a identidade do cliente, confirmando um código de segurança de cartão de crédito de 3 ou 4 dígitos com o processador de pagamento.

_Atributos do termo:_

* _Campo: empresa, pedido_
* _Sinônimos: Método de verificação do titular do cartão_
* _Termos relacionados: código de segurança_

## D

### esquema de banco de dados

_substantivo_

A estrutura dos dados em um banco de dados.
Define como os dados são organizados e como os relacionamentos de dados são governados, incluindo todas as restrições aplicadas aos dados.
Um módulo pode conter fragmentos do schema do banco de dados se esse módulo tiver dados que devem ser armazenados no banco de dados.

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: schema_

### injeção de dependência

_substantivo_

Um padrão de design de software que permite que uma classe especifique suas dependências sem ter que construí-las.
Essa classe delega a responsabilidade de injetar a dependência à classe chamadora.
Usado para facilitar os testes.
Para definir dependências para classes, edite o arquivo de configuração di.xml.

_Atributos do termo:_

* _Campo: programação_

### chave de implantação

_substantivo_

Uma chave de implantação é a chave pública SSH do projeto e permite acesso somente leitura ou leitura/gravação (se ativada) a um repositório Git.

Saiba mais: [Conexões seguras](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Atributos do termo:_

* _Campo: nuvem_

### opt in duplo

_substantivo, verbo_

Um processo de verificação de email que requer que assinantes potenciais concluam uma segunda etapa que confirma sua intenção de assinar.

_Atributos do termo:_

* _Campo: empresa_

### produto baixável

_substantivo_

Um produto baixável digitalmente que consiste em um ou mais arquivos que são baixados, como um eBook, música, vídeo, aplicativo de software ou uma atualização.
Você pode oferecer um álbum para venda e vender cada música individualmente.
Um produto disponível para download pode fornecer uma versão eletrônica do catálogo de produtos.

Os arquivos baixáveis podem residir no seu servidor ou ser fornecidos como URLs para qualquer outro servidor ou rede de entrega de conteúdo.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: tipos de produtos_

### conteúdo dinâmico

_substantivo_

Conteúdo que é gerado pelo código em vez de ler de um modelo estático.
Depois que o conteúdo dinâmico é renderizado inicialmente quando um usuário visita uma página, às vezes o conteúdo pode ser armazenado em cache e reutilizado sem precisar de outra chamada dinâmica após uma visita.

_Atributos do termo:_

* _Campo: projeto_
* _Termos relacionados: php_

### URL de mídia dinâmica

_substantivo_

Um endereço de URL que é gerado dinamicamente pelo sistema para fazer referência a uma imagem ou outra mídia.
O endereço se vincula diretamente aos ativos armazenados em um servidor ou em uma rede de entrega de conteúdo.
Para usar um URL estático, altere a configuração .
No entanto, se os URLs de mídia dinâmica forem incluídos em seu catálogo quando você desativar a configuração, cada referência em seu catálogo se tornará um link quebrado.
Os links podem ser restaurados ativando novamente URLs de mídia dinâmica.
O uso de URLs de mídia dinâmica pode afetar o desempenho da pesquisa no catálogo.

Formato do código: media url=&quot;path/to/image.jpg&quot;

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: rede de entrega de conteúdo, url_

## E

### pacote de ferramentas ecológicas

_substantivo_

Um conjunto de scripts e ferramentas projetado para gerenciar e implantar o aplicativo Commerce. Esse pacote simplifica muitos processos de infraestrutura em nuvem do Adobe Commerce, incluindo a implantação em um ambiente Docker, o gerenciamento de crons, a verificação da configuração do projeto e a aplicação de patches de Adobe.

Saiba mais: [pacote de ferramentas ecológicas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Atributos do termo:_

* _Campo: cli, nuvem, implantação_

### entity

_substantivo_

Uma unidade ou objeto exclusivo na programação.
Contém atributos ou parâmetros que podem ser modificados.
Os exemplos incluem o armazenamento temporário — em que uma atualização pode alterar entidades como regras de preços, produtos ou categorias — e registros de banco de dados — em que os contratos de serviço incluem estruturas de dados enviadas e recebidas.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: atributo, regras de carrinho, regras de catálogo_

### valor do atributo da entidade

_substantivo_

Para entidades de banco de dados, um modelo de dados que codifica entidades com eficiência.
Armazena a ID da entidade, o nome do atributo e o valor como um triplo, o que permite que novos nomes de atributos da entidade sejam criados a qualquer momento.
Na codificação, o número de atributos que podem ser usados para descrever entidades pode ser dimensionado extensivamente, mas o número que se aplica a uma determinada entidade é minimizado.
Esse modelo de dados é flexível, mas pode ser lento.

Saiba mais: [EAV e extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: eav_

### conteúdo permanente

_substantivo_

Conteúdo com uma longa duração de validade ou conteúdo que pode ser reutilizado.

_Atributos do termo:_

* _Campo: empresa_

### extensão

_substantivo_

Código que estende ou personaliza o comportamento do Adobe Commerce.
Opcionalmente, é possível empacotar e distribuir uma extensão no Commerce Marketplace ou em outro sistema de distribuição de extensão.
Uma extensão Commerce pode incluir módulos, temas e pacotes de idiomas.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: componente, módulo, pacote_

### atributo de extensão

_substantivo_

Amplie a funcionalidade e use com frequência tipos de dados mais complexos do que atributos personalizados. Esses atributos não aparecem na GUI.

Saiba mais: [Adicionar atributos de extensão à entidade](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: atributo, valor do atributo da entidade_

## F

### frete a bordo

_substantivo_

No transporte marítimo internacional, este termo significa que a parte receptora é responsável pelas taxas de frete.
O FOB pode ser baseado no local de origem ou de destino e ser designado como cobrança de frete ou frete pré-pago.

_Atributos do termo:_

* _Campo: empresa, pedido, preços_
* _Sinônimos: fob_

### frontend

_adjetivo_

Em um aplicativo cliente-servidor, há o back-end e o front-end.
O componente de front-end, ou cliente, é uma interface que permite aos usuários manipular ou interagir com o código de back-end subjacente.
O código de back-end é executado em um servidor.
Um usuário não pode acessar diretamente o código de back-end.
Um usuário interage com a loja, que por sua vez usa o código em execução no servidor do Commerce.

Observação: No passado, a loja era conhecida como &quot;frontend&quot; e o Admin era conhecido como &quot;backend&quot;. Esse uso não é mais suportado.

_Atributos do termo:_

* _Campo: projeto, programação_
* _Sinônimos: lado do cliente_
* _Termos relacionados: back-end, vitrine, front-end de cache_

### propriedades de frontend

_substantivo_

Propriedades que determinam a apresentação e o comportamento de um atributo do ponto de vista do cliente em sua loja.

_Atributos do termo:_

* _Campo: projeto, programação_

### cumprimento

_substantivo_

O processo de gerenciamento de remessas de clientes.

_Atributos do termo:_

* _Campo: empresa_

## G

### cartão-presente

_substantivo_

Um cartão pré-pago ou certificado de presente que pode ser usado para fazer compras na loja.
Cada cartão-presente recebe um código exclusivo que é inserido no check-out.
O valor do cartão-presente é refletido no saldo da conta do cartão-presente.
Há três tipos de cartões-presente:

* Os cartões-presente &quot;físicos&quot; podem ser produzidos a partir de plástico ou de estoque de cartão, enviados para o cliente.
* Os cartões-presente &quot;virtuais&quot; são enviados por e-mail.
* Os cartões-presente &quot;combinados&quot; são uma combinação dos dois, enviados para o recipient como um cartão físico e também entregues por email.
Os cartões-presente são configuráveis, incluindo opções para qualificação de produto e seleção de quantidades abertas ou fixas.

Um cartão-presente também pode ser resgatado pelo administrador da loja, mediante solicitação do cliente, quando o pedido estiver sendo criado no back-end.

Os cartões-presente também ajudam as promoções, já que os administradores de lojas podem criar manualmente as contas do cartão-presente no backend e enviar os códigos do cartão-presente para o segmento específico do cliente.
Os cartões-presente podem servir como um programa de fidelidade direcionado aos clientes mais ativos que fazem várias compras na loja da Web ou uma campanha promocional específica durante as festas.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: tipos de produtos_

### margem bruta

_substantivo_

A diferença entre o custo e o preço de um produto.

_Atributos do termo:_

* _Campo: empresa_

### produto agrupado

_substantivo_

Um tipo de produto com vários produtos similares independentes agrupados em uma única página.
Pode ser oferecido com variações de um único produto ou agrupando-as por estação ou tema para criar um conjunto coordenado.
Cada produto pode ser comprado separadamente ou como parte do grupo.

Por exemplo, para uma faca que está disponível em quatro tamanhos, todas as quatro facas podem ser exibidas em uma página de produto agrupada.
Os clientes podem selecionar os tamanhos desejados e adicioná-los ao carrinho nesta página.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: produto simples, tipos de produto_

## H

### identificador

_substantivo_

Geralmente, um identificador é uma maneira de fazer referência a um objeto.
No Adobe Commerce, os identificadores são usados em vários locais, geralmente para identificar uma página.
Para identificadores de página, o nome do identificador é derivado do URL e, em seguida, é usado para localizar e carregar os arquivos de layout da página referenciada.
Por exemplo, no módulo Cliente, há um arquivo de layout chamado &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Aqui, &quot;frontend&quot; é o nome da área e &quot;checkout_cart_index&quot; é o nome do identificador, ambos derivados do URL.

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: identificador de página_

### escala horizontal

_substantivo_

A escala horizontal (também conhecida como expansão) é o processo de adicionar nós ou máquinas adicionais à sua infraestrutura para atender à demanda crescente.

_Atributos do termo:_

* _Campo: nuvem_

## I

### intercepção

_substantivo_

O processo de injetar novo código antes, depois ou ao redor de uma função pública existente de uma classe PHP.

Para interceptar uma função, um plug-in implementa o código adicional a ser chamado.
Os plug-ins são associados a pontos de intercepção pelo arquivo de configuração de injeção de dependência (di.xml).
Se vários plug-ins forem definidos na mesma função, a configuração de injeção de dependência definirá a ordem em que os plug-ins serão chamados, permitindo que vários plug-ins sejam usados sem conflitos.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: plug-in_

## L

### layout

_substantivo_

Na construção de uma página de Comércio, um layout é uma série de blocos montados em uma hierarquia, representando a estrutura da página.

Os arquivos de layout de página se concentram no nível mais alto da estrutura da página (cabeçalho, rodapé, área do conteúdo principal, barra lateral esquerda e assim por diante).
Os arquivos de layout então reúnem o conteúdo (blocos) nessas diferentes áreas da página.

_Atributos do termo:_

* _Campo: design, software comercial_
* _Termos relacionados: instruções de layout, bloco_

### instruções de layout

_substantivo_

Marcação em um arquivo de layout que descreve as alterações a serem aplicadas a uma árvore de elementos estruturados de blocos, contêineres e componentes da interface do usuário.
Um único arquivo de layout pode conter várias instruções de layout.
As instruções de layout são codificadas em XML nos arquivos de layout.

_Atributos do termo:_

* _Campo: projeto, programação_
* _Termos relacionados: layout, bloco, contêiner, componente de interface_

### atualização de layout

_substantivo_

Usado para trechos de código adicionados para modificar o layout XML ou para importar as instruções de layout de outro arquivo.

_Atributos do termo:_

* _Campo: design, software comercial_

### Proprietário da licença

_substantivo_

O Proprietário da Licença (também conhecido como Proprietário da Conta) é a pessoa designada em uma organização comercial que gerencia pagamentos e outros problemas relacionados aos negócios para a conta da infraestrutura em nuvem da Adobe Commerce.
Essa pessoa serve como ponto de contato com o Adobe.
Depois que uma empresa compra uma assinatura da infraestrutura em nuvem da Adobe Commerce, o projeto inicial e o acesso ao código são disponibilizados somente para a pessoa designada como o Proprietário da licença.

_Atributos do termo:_

* _Campo: empresa_

## M

### MAGEID

_substantivo_

O MAGEID geralmente é o contato de faturamento na conta do Adobe Commerce (e pode não ser o Proprietário do Projeto do Adobe Commerce no projeto de infraestrutura em nuvem).
Para obter o direito de acesso ao Adobe Commerce e ao Adobe Commerce em pacotes de infraestrutura em nuvem, você deve usar chaves de acesso associadas a um MAGEID que recebeu acesso a esses pacotes.

Saiba mais: [Obter as chaves de autenticação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Atributos do termo:_

* _Campo: software comercial_

### marcação

_substantivo_

Em marketing e varejo, uma porcentagem adicionada ao custo de um item para determinar o preço de varejo.
[Configurar a marcação](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html)ou marcação de um produto por meio de opções personalizáveis do produto.

Em desenvolvimento, um idioma do computador que controla o processamento, a apresentação e a formatação do texto.
Além disso, tags de marcação são trechos de código que adicionam funcionalidade ou conteúdo a uma página ou bloco CMS.

_Atributos do termo:_

* _Campo: negócios, programação_
* _Sinônimos: Markdown_

### Ambiente principal

_substantivo_

Na infraestrutura em nuvem do Adobe Commerce, os projetos Pro usam um ambiente ativo do Platform as a Service (PaaS) chamado principal que inclui uma cópia do banco de dados do ambiente de produção e do servidor da Web.

_Atributos do termo:_

* _Campo: nuvem_

### conta comercial

_substantivo_

Uma conta num banco ou instituição financeira que permita aceitar transações com cartão de crédito.

_Atributos do termo:_

* _Campo: empresa_

### MFTF

_substantivo_

O MFTF é um [Estrutura de testes funcionais](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Ele fornece uma estrutura de teste para desenvolvedores de Comércio e engenheiros de software, como especialistas em QA, desenvolvedores PHP e integradores de sistemas.
Os desenvolvedores e o controle de qualidade podem gravar testes para tentar interações do usuário com aplicativos da Web, verificar a funcionalidade e automatizar o teste de regressão.

_Atributos do termo:_

* _Campo: software comercial, programação_
* _Termos relacionados: bloco cms, bloco estático, contêiner, layout_

### módulo

_substantivo_

Código que altera ou estende os recursos fornecidos pelo aplicativo Magento.
Um módulo está contido em uma estrutura de diretório que contém arquivos PHP e XML (configuração, blocos, controladores, auxiliares, modelos e assim por diante) relacionados a uma funcionalidade específica para fornecer uma coleção distinta de recursos do produto.
O objetivo de cada módulo é fornecer recursos específicos do produto, implementando novas funcionalidades ou estendendo a funcionalidade de outros módulos.
Cada módulo é projetado para funcionar de forma independente, de modo que a inclusão ou exclusão de um módulo específico não afete a funcionalidade de outros módulos.

Um módulo também pode implementar widgets, que são elementos de página que podem ser personalizados por usuários empresariais no Administrador.

Os módulos podem ser desativados ou removidos sem quebrar a consistência do aplicativo Magento.
Uma exceção: Quando o módulo depende de outros módulos, o que requer desativar ou remover os módulos dependentes.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: php, xml, bloco_

## O

### OMS

_substantivo_

[OMS](https://omsdocs.magento.com) é a oferta do Adobe Order Management.

O OMS é uma solução flexível e acessível para gerenciar, vender e cumprir o inventário de qualquer canal de vendas.
O OMS fornece uma experiência contínua para o cliente, o que aumenta as vendas e reduz os custos, além de acelerar o tempo de comercialização.

Os recursos OMS incluem:

* Visibilidade e gerenciamento globais de todo o inventário
* Capacidade de enviar para e de qualquer lugar
* Serviço de atendimento ao cliente mais fácil e responsivo
* Melhor experiência e fidelidade do cliente

Saiba mais: [Introdução ao OMS](https://omsdocs.magento.com/en/getting-started/), [Local dos documentos OMS](https://omsdocs.magento.com/en/)

_Atributos do termo:_

* _Campo: recurso, software comercial, gerenciamento de pedidos_
* _Sinônimos: gerenciamento de pedidos, MOM, sistema de gerenciamento de pedidos, Magento Order Management_
* _Termos relacionados: gerenciamento de pedidos_

### colagem de origem

_substantivo_

O cloaking de origem é um recurso de segurança que permite ao Adobe Commerce na infraestrutura de nuvem bloquear qualquer tráfego não-Fastly para evitar ataques de DDoS, indo para a infraestrutura de nuvem (origem).

Saiba mais: [Cobertura rápida da origem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Atributos do termo:_

* _Campo: segurança_
* _Termos relacionados: firewall da aplicação web_

## P

### Page Builder

_substantivo_

O Page Builder é uma extensão do Commerce para criar páginas ricas em conteúdo, arrastando e soltando controles pré-criados para definir layouts personalizados.
Esses controles também são conhecidos como &quot;tipos de conteúdo&quot;.
Os comerciantes podem projetar layouts e páginas sem experiência de codificação.
O suporte de extensão é fornecido para desenvolvedores a fim de estender o Page Builder.

Saiba mais: [Guia do usuário do Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [DevDocs do Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Atributos do termo:_

* _Campo: software comercial, design_
* _Sinônimos: Admin, Painel de administração, back-end, Interface de administração, Interface de administração_
* _Termos relacionados: administrador_

### gateway de pagamento

_substantivo_

Um gateway de pagamento é um serviço de terceiros que processa sem problemas as transações com cartões de crédito sem que o cliente saia do site do comerciante.

_Atributos do termo:_

* _Campo: negócios, pedido, programação_

## R

### produto relacionado

_substantivo_

Uma seleção de produtos que é apresentada como um incentivo para comprar itens adicionais.
Por exemplo, se o cliente estiver visualizando a página do produto de uma câmera, os produtos relacionados podem incluir outras câmeras comparáveis, um gabinete de câmera e um tripé.

_Atributos do termo:_

* _Campo: software comercial, produto_

## S

### regras de vendas

_substantivo_

Inclui regras de carrinho e catálogo, que são usadas para precificar um produto para promoções.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: regras de carrinho, regras de catálogo_

### escopo

_substantivo_

No Adobe Commerce, o escopo descreve a extensão da hierarquia da loja que uma configuração pode afetar.
O escopo pode se aplicar ao seguinte:

* Global — todos os sites, lojas e visualizações de loja
* Site — o site selecionado e todas as lojas e visualizações de loja
* Loja — a loja selecionada e todas as visualizações de loja nela
* Exibição de Armazenamento — a exibição de loja selecionada.

Na hierarquia, as configurações aplicadas em um nível inferior podem substituir algumas configurações de nível superior.

_Atributos do termo:_

* _Campo: software comercial_

### contrato de serviço

_substantivo_

Um conjunto de interfaces PHP definidas para um módulo.
Um contrato de serviço inclui interfaces de dados, que preservam a integridade dos dados, e interfaces de serviço, que ocultam detalhes de lógica comercial de solicitantes de serviço, como controladores, serviços da Web e outros módulos.
As APIs da Web podem ser vinculadas a contratos de serviço por meio de arquivos de configuração.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: php, api da web_

### liquidação

_substantivo_

A liquidação ocorre quando o banco adquirente e os fundos de câmbio do emitente e o produto são depositados na conta do comerciante.

_Atributos do termo:_

* _Campo: empresa_

### Catálogo compartilhado

_substantivo_

Um recurso que permite aos comerciantes criar um catálogo que pode servir como seu catálogo inteiro ou um subconjunto dele e, em seguida, atribuir preços personalizados para um ou mais produtos.
Os comerciantes podem então atribuir esse catálogo a uma ou mais empresas.

Por exemplo, um comerciante B2B tem três clientes que negociaram taxas específicas para o site de distribuição de eletrônicos do comerciante.
Usando o recurso de catálogo compartilhado, o comerciante tem:

* Um catálogo principal
* Um catálogo de cliente 1 (talvez sejam apenas três SKUs com pesados descontos no catálogo principal)
* Catálogo de cliente 2 (pode ser o catálogo inteiro com 10% de desconto)
* Catálogo Customer 3 (algumas dezenas de produtos com descontos do catálogo principal que variam de 5% a 60%).

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: catálogo, b2b_

### entrega

_substantivo_

Uma remessa contém produtos a serem entregues e gera um registro dos produtos em um pedido que foi enviado.
Mais de uma remessa pode ser associada a uma única ordem.

_Atributos do termo:_

* _Campo: empresa, pedido_

### documento de remessa

_substantivo_

Um documento que acompanha uma remessa. O documento lista os produtos e suas quantidades no pacote de delivery.

_Atributos do termo:_

* _Campo: empresa, pedido_

### transportadora marítima

_substantivo_

Uma empresa que transporta pacotes. As operadoras comuns incluem UPS, FedEx, DHL e USPS.

_Atributos do termo:_

* _Campo: empresa, pedido_

### carrinho de compras

_substantivo_

O conjunto de produtos que um cliente selecionou para compra, mas que ainda não comprou.
Refere-se também a uma área de um site de comércio eletrônico onde esses produtos podem ser encontrados para análise e check-out.

_Atributos do termo:_

* _Campo: empresa, design, produto, programação_
* _Sinônimos: carrinho, cesta_
* _Termos relacionados: regras do carrinho_

### produto simples

_substantivo_

O tipo de produto mais básico, um item físico com um único SKU.
Produtos simples têm vários preços e controles de entrada que permitem vender variações do produto.
Produtos simples podem ser usados em associação com produtos agrupados, agrupados e configuráveis.
Um produto simples com opções personalizadas às vezes é chamado de produto composto.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: tipos de produtos_

### SKU

_substantivo_

Abreviação da unidade de manutenção de estoque.
Um número ou código atribuído a um produto para identificar o produto, as opções, o preço e o fabricante.

_Atributos do termo:_

* _Campo: negócios, preços, produto, programação_
* _Termos relacionados: catálogo compartilhado_

### página inicial

_substantivo_

Uma página promocional com um produto ou anúncio; normalmente exibida antes da página inicial.

_Atributos do termo:_

* _Campo: projeto_

### bloco estático

_substantivo_

Uma unidade modular de conteúdo que pode ser colocada por um usuário no CMS em uma página para exibir texto e imagens ou executar trechos de código.
Os blocos estáticos contêm conteúdo editável e podem atuar como páginas de aterrissagem para categorias de produtos.
Os widgets podem ser adicionados a blocos estáticos para fornecer funcionalidade adicional.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: bloco cms, bloco_

### conteúdo estático

_substantivo_

Conteúdo gerado pelo usuário (não gerado pelo código) que não é alterado com frequência.

_Atributos do termo:_

* _Campo: projeto_
* _Termos relacionados: conteúdo dinâmico_

### arquivos estáticos

_substantivo_

A coleção de ativos, como CSS, fontes, imagens e JavaScript, que é usada por um tema.

_Atributos do termo:_

* _Campo: software comercial_

### loja

_substantivo_

O nível de escopo de comércio de &quot;loja&quot; é o segundo nível da hierarquia do seu site, que é o seguinte: site > loja > visualização de loja.
As lojas podem ser organizadas em uma ou várias. Cada loja, potencialmente, tem sua própria categoria raiz e todos compartilham dados de catálogo e cliente.

Cada loja pode ter várias visualizações de loja, que normalmente são usadas para apresentar a loja em um local e idioma diferentes.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: exibição de loja, site_

### exibição de loja

_substantivo_

O nível de escopo de Comércio de &quot;visualização de loja&quot; refere-se ao terceiro nível na hierarquia de sites, lojas e visualizações de loja.
As exibições da loja normalmente apresentam a loja em um local e idioma diferentes.
Para alterar exibições de loja, use o seletor de loja no cabeçalho.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: loja, site_

### vitrine

_substantivo_

A loja online que os clientes experimentam quando visitam seu site de Comércio.

_Atributos do termo:_

* _Campo: software comercial, produto_

## T

### regra fiscal

_substantivo_

Uma combinação de uma classe de imposto do produto, classe de imposto do cliente e alíquota de imposto. Essa regra define qual cálculo de imposto é aplicado.

_Atributos do termo:_

* _Campo: empresa_

### modelo

_substantivo_

Abreviação de HTML template ou PHTML template.
Um arquivo PHTML contém uma mistura de marcação HTML e código PHP para injetar conteúdo dinâmico no HTML.
A maioria dos blocos tem pelo menos um arquivo PHTML (template) que contém o HTML estático gerado pelo bloco.
Nos modelos de Admin, email e informativo combinam texto, imagens e variáveis com marcação de HTML para produzir conteúdo personalizado enviado pelo sistema.

_Atributos do termo:_

* _Campo: software comercial_
* _Termos relacionados: bloco_

### tema

_substantivo_

Contém gráficos e informações de aparência.
Personaliza a aparência da loja.
A Adobe Commerce pode enviar temas em pacotes (Composer).
Mas os temas podem ser colocados em aplicativo/design, que não é enviado em um pacote.
Pacotes são a unidade de download do Composer e, por meio do Commerce Marketplace, os usuários do Commerce podem baixar CE ou EE como uma série de pacotes, onde os pacotes contêm módulos, temas ou pacotes de idioma.

_Atributos do termo:_

* _Campo: software comercial_

## U

### componente da interface do usuário

_substantivo_

Uma tag projetada para o software Adobe Commerce para permitir a renderização mais simples e flexível da interface do usuário.
As metas do sistema de componentes da interface do usuário incluem o seguinte:

* Simplificando arquivos XML do Identificador de layout
* Mover elementos da interface do usuário do Administrador do HTML+JavaScript para um sistema de widget personalizado &quot;JavaScript puro&quot;
* Ativar a criação de componentes mais complexos da interface do usuário de componentes menores
* Pré-renderização de dados para componentes da interface do usuário como JSON, vinculação próxima a objetos de dados de backend
* Usar AJAX para atualizar os dados do componente
* Introdução de um novo DSL para criar os itens acima

Saiba mais: [Guia de componentes da interface do usuário](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: JavaScript, layout, componente, construtor de páginas_

### PARA CIMA

_substantivo_

[PWA Studio](https://github.com/magento/pwa-studio) uses [PARA CIMA](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) em desenvolvimento.
UPWARD é um acrônimo de Unified Progressive Web App Response Definition.
Um arquivo de definição UPWARD descreve como um servidor da Web fornece e suporta um Progressive Web Application.

Os arquivos de definição UPWARD fornecem detalhes sobre o comportamento do servidor usando uma linguagem declarativa independente de plataforma.
Isso permite que um Progressive Web Application seja executado sobre um servidor compatível com UPWARD em qualquer idioma em qualquer pilha de tecnologia, pois o aplicativo só está preocupado com o comportamento de ponto de extremidade HTTP do servidor UPWARD.

Um servidor UPWARD usa um arquivo de definição para determinar o processo ou serviço apropriado para uma solicitação de um shell de aplicativo.
Ele descreve como o servidor deve lidar com uma solicitação e criar a resposta para ela.

Um projeto do PWA pode incluir um arquivo de definição UPWARD para especificar suas dependências de serviço.

_Atributos do termo:_

* _Campo: design, software comercial, programação_
* _Sinônimos: PWA Studio, Definição de resposta de aplicativos web progressivos unificados_
* _Termos relacionados: pwa_

## V

### Extensão embutida do fornecedor

_substantivo_

O código produzido pelo fornecedor que estende ou personaliza o comportamento do Commerce e opera como uma extensão de terceiros é considerado uma VBE (Vendor Bundled Extension).
Os VBEs são totalmente testados e incluídos com cada versão compatível do Magento Open Source e do Adobe Commerce.
Um VBE pode incluir módulos, temas e pacotes de idiomas.

Saiba mais na [Tópico Extensão embutida do fornecedor](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Atributos do termo:_

* _Campo: extensão de comércio, extensão fornecida pelo fornecedor, extensão, VBE_
* _Sinônimos: extensão, VBE_
* _Termos relacionados: extensão, extensão agrupada_

### dimensionamento vertical

_substantivo_

O dimensionamento vertical (dimensionamento) refere-se ao aumento da potência de processamento de um único servidor ou cluster, adicionando E/S de disco ou rede, CPUs ou RAM.

_Atributos do termo:_

* _Campo: ambiente_

### produto virtual

_substantivo_

Representa um produto não físico que pode ser vendido, como associação, serviço, garantia ou assinatura.
Os produtos virtuais podem ser vendidos individualmente ou incluídos como parte dos seguintes tipos de produtos: produto agrupado e produto de pacote.
Não requer entrega ou inventário.

O processo de criação de um produto virtual e um produto simples é quase o mesmo.
No entanto, como um produto virtual não é enviado, não há campo Peso ou opção para incluir um cartão-presente.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: tipos de produtos_

### tipo virtual

_substantivo_

Tipos virtuais são uma maneira de inserir diferentes dependências em classes PHP existentes sem afetar outras classes e sem precisar criar um arquivo de classe.
Os tipos virtuais só podem ser referenciados por substituições de argumento em um `<type>` em arquivos di.xml, nunca no código-fonte.
Elas não podem ser estendidas e não podem ser referências como dependências em um construtor de classes.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: php_

## W

### site

_substantivo_

No software Adobe Commerce, o nível mais alto de uma hierarquia de site, acima da visualização de loja e loja.
Você pode ter vários sites e cada site pode ter um nome de domínio diferente.
Os sites podem ser configurados para compartilhar dados do cliente ou não para compartilhar dados.

_Atributos do termo:_

* _Campo: software comercial, design, produto_
* _Termos relacionados: loja, visualização de loja_

### widget

_substantivo_

A [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) é um trecho de código preparado que pode ser usado para colocar blocos, links e conteúdo dinâmico em locais específicos nas páginas da loja.
Você pode usar widgets para criar páginas de aterrissagem para campanhas de marketing, exibir conteúdo promocional em locais específicos na loja.
Os widgets também podem ser usados para adicionar elementos interativos e blocos de ação para sistemas de revisão externos, chats de vídeo, votação e formulários de assinatura, ou para fornecer elementos de navegação para nuvens de tags e controles deslizantes de imagens.

_Atributos do termo:_

* _Campo: empresa, software comercial, design_
* _Termos relacionados: bloco_
