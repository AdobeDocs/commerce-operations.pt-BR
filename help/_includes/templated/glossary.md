---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '6363'
ht-degree: 0%

---
# Glossário do Adobe Commerce

## A

### acima da dobra

_adjetivo_

Em uma janela do navegador, o conteúdo é imediatamente visível depois que uma página da Web é carregada e antes que um usuário role pela página para baixo.
Ao projetar seu layout, use formatos flexíveis para exibir melhor os produtos, recursos, vendas, notificações, opções de maior prioridade nesta área.

Com dispositivos móveis e tablets, a área acima da dobra difere muito, especialmente no tamanho e nas dimensões da tela e na orientação ao visualizar (retrato versus paisagem).
Usar temas responsivos e testes pode ajudar a encontrar a combinação certa de conteúdo e layout.

_Atributos do termo:_

* _Campo: design_

### ramificação ativa

_substantivo_

Uma ramificação ou ambiente ativo é aquele conectado a uma instância implantada ou em execução com acesso a serviços.
Ao desativar, a conexão com os serviços e com a instância em execução é removida, mas o código é preservado.
Ele se torna uma ramificação Git comum.

_Atributos do termo:_

* _Campo: nuvem_

### adaptador

_substantivo_

Uma classe que permite que dois sistemas incompatíveis funcionem juntos sem modificar o código-fonte do sistema.
Os exemplos incluem adaptadores de banco de dados, adaptadores de cache, adaptadores de sistema de arquivos, adaptadores de bibliotecas de pós-processador e outros tipos de adaptadores de computação.

_Atributos do termo:_

* _Campo: programação_

### administrador

_substantivo_

No software, uma função de usuário com privilégios totais de administrador para gerenciar todas as funcionalidades do.
No Adobe Commerce, os usuários administradores têm permissões totais e acesso a todos os recursos, opções e funcionalidades no Admin.
Eles também podem criar usuários e funções.

Saiba mais: [Adicionando usuários](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Atributos do termo:_

* _Campo: software de comércio_
* _Sinônimos: administrador, superusuário_
* _Termos relacionados: administrador de comércio_

### Área de administração

_substantivo_

O back office protegido por senha da loja onde os pedidos, o catálogo, o conteúdo e as configurações são gerenciados.
Os usuários acessam a área de Administração para gerenciar a loja, incluindo produtos, pedidos, remessas, conteúdo CMS, design da loja, informações do cliente e assim por diante.
Os usuários administradores têm uma função associada com permissões que controlam o acesso a recursos, opções e funcionalidades.

Saiba mais: [Guia do Usuário do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos do termo:_

* _Campo: software de comércio_
* _Sinônimos: Administrador, Painel de Administração, back-end, Interface de Administração, Interface de Administrador_
* _Termos relacionados: admin_

### Variáveis de ADMINISTRAÇÃO

_substantivo_

As variáveis ADMIN são variáveis de ambiente do projeto para substituir as definições de configuração da conta de usuário Admin para acessar a interface de usuário Admin.

Saiba mais: [Variáveis de ADMINISTRAÇÃO](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Atributos do termo:_

* _Campo: admin, nuvem_

### adminhtml

_substantivo_

O nome da área interna atribuído ao Administrador.

Saiba mais: [Guia do Usuário do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: area, commerce admin_

### área

_substantivo_

Área é um termo abstrato para um escopo de aplicação Magento.
As áreas são componentes lógicos que organizam o código para otimizar o processamento de solicitações.
As áreas reduzem as demandas de memória dos objetos de configuração acessados da loja e simplificam as chamadas de serviço da Web carregando somente o código dependente necessário.
Cada área pode conter código completamente diferente para processar URLs e solicitações.

As áreas do Adobe Commerce incluem:

* Administrador (adminhtml)
* Loja
* REST da API da Web (webapi_rest)

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: componente de comércio, vitrine_

### atributo

_substantivo_

Uma característica ou propriedade de um produto que descreve algum aspecto do produto.
Os usuários do Adobe Commerce podem criar atributos personalizados para adicionar ao conjunto de atributos padrão ou a um conjunto de atributos personalizado.
Crie esses atributos por meio do Administrador ou de forma programática.
Exemplos: cor, tamanho, peso, preço, idade, gênero e assim por diante.

Os atributos personalizados são um tipo de atributo de Entidade-Atributo-Valor (EAV).

Para integrações como o Canal de anúncios do Google Shopping e o Sales Channel do Amazon, mapeie os atributos do Commerce a atributos no terceiro para exibir e vender corretamente os produtos e exibir os anúncios.

Saiba mais: [EAV e extension extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Sinônimos: atributo de produto, atributo personalizado_
* _Termos relacionados: atributo de extensão_

### grupo de atributos

_substantivo_

Um agrupamento lógico de atributos em um conjunto de atributos.

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: atributo_

### conjunto de atributos

_substantivo_

Uma coleção de grupos de atributos personalizados para um produto específico.
Exemplo: um conjunto de atributos de camiseta pode incluir cor, tamanho, gênero e marca.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: atributo_

### custo médio de estoque

_substantivo_

Preço do produto, menos cupons ou descontos, mais frete e impostos aplicáveis.
A média é determinada pela adição do custo inicial do inventário a cada mês, mais o custo final do inventário para o último mês do período.

_Atributos do termo:_

* _Campo: produto, preço, estoque_

## B

### moeda de base

_substantivo_

A moeda principal usada por exibição de loja para todos os pagamentos online.
As lojas podem aceitar moedas de mais de 200 países ao redor do mundo.
A loja fornece um seletor de moedas para várias moedas aceitas para um país ou localidade específica.
Os símbolos de moeda são exibidos nos preços dos produtos e nos documentos de venda, como pedidos e faturas.
Você pode personalizar os símbolos de moeda conforme necessário e definir a exibição do preço separadamente para cada loja ou exibição.

Saiba mais: [Moeda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Atributos do termo:_

* _Campo: preços_

### processamento em lote

_substantivo_

Executar uma tarefa ou alterar vários itens de uma só vez, sem repetição manual.

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: operações em massa_

### bloco

_substantivo_

Uma unidade de saída de página que renderiza algum conteúdo distinto — uma parte das informações, um elemento da interface do usuário — qualquer coisa visualmente tangível para o usuário final.
[Os blocos](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) são implementados e fornecidos por módulos.
Os blocos usam modelos para gerar HTML.
Exemplos de blocos incluem uma lista de categorias, um minicarrinho, tags de produtos e listas de produtos.

[Blocos dinâmicos](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) fornecem conteúdo com base na lógica, como regras de preço.

O Page Builder expande a interatividade e a criação de [blocos](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) e [blocos dinâmicos](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Atributos do termo:_

* _Campo: software de comércio_
* _Sinônimos: Blocos Dinâmicos_
* _Termos relacionados: bloco cms, bloco estático, contêiner, layout_

### marca

_substantivo, verbo_

Uma identidade exclusiva que define um produto ou grupo de produtos específico pelo fabricante ou pela Designer.
Isso inclui marcas de nomes para roupas, eletrodomésticos, artigos de luxo e assim por diante.
Sua empresa também pode ser a marca, vendendo produtos em várias marcas com base na unidade de negócios, público-alvo e assim por diante.

Use atributos personalizados para salvar informações sobre a marca de produtos.

Algumas extensões e integrações podem usar ou exigir uma marca para seus produtos, como o Google Shopping ads Channel e o Amazon Sales Channel.

_Atributos do termo:_

* _Campo: empresa_

### argamassa

_adjetivo_

Uma empresa de varejo com um local físico permanente, em oposição às empresas que funcionam virtual ou exclusivamente pela Internet.

Para o [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) e o [Order Management](https://omsdocs.magento.com/getting-started/terminology/), esta loja é uma fonte para rastrear quantidades de produtos, pedidos de remessa e suporte para retirada na loja.

_Atributos do termo:_

* _Campo: empresa, estoque_

### operações em massa

_substantivo_

As operações em massa são ações executadas em grande escala.
Exemplo de tarefas de operações em massa incluem importação ou exportação de itens, alteração de preços em uma escala em massa e atribuição de produtos a um depósito.

Saiba mais: [Operações em massa de DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Atributos do termo:_

* _Campo: programação_

### produto do pacote

_substantivo_

Permite que os clientes montem um produto personalizável &quot;crie o seu próprio&quot; a partir de várias opções e configurações.
Cada item no pacote é um produto simples ou virtual separado.

Saiba mais: [Produtos configuráveis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: produto simples, produto virtual, tipos de produto_

### extensão agrupada

_substantivo_

O código que estende ou personaliza o comportamento do Adobe Commerce é considerado uma extensão agrupada.
Ele pode incluir módulos, temas e pacotes de idiomas.

_Atributos do termo:_

* _Campo: extensão agrupada, extensão_
* _Sinônimos: extensão_
* _Termos relacionados: extensão, extensão agrupada de fornecedor_

## C

### back-end do cache

_substantivo_

Armazena registros de cache em um sistema de back-end de dois níveis dentro da estrutura padrão do Zend.
Um cache de primeiro nível é rápido, por exemplo, um APC ou back-end armazenado em cache, mas é limitado e não oferece suporte à marcação e ao agrupamento de entradas de cache.
Um cache de segundo nível — por exemplo, um sistema de arquivos ou um back-end Redis — é mais lento, mas oferece suporte à marcação e ao agrupamento.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: back-end_

### front-end do cache

_substantivo_

Especifica que tipo de dados são armazenados no back-end do cache.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: front-end_

### tipo de cache

_substantivo_

Um cache armazena dados para que as chamadas futuras para esses dados sejam carregadas mais rapidamente.

O Adobe Commerce inclui estes tipos:
* Configuração
* Layouts
* Bloquear saída de HTML
* Dados das coleções
* Dados de Reflexão
* Operações DDL de banco de dados
* Configuração compilada
* Tipos e atributos de EAV
* Notificação de Cliente
* Configuração de integrações
* Configuração da API de integrações
* Cache de página (o mais conhecido)
* Configuração de serviços da Web
* Traduções
* Regra de destino
* Cache de produto do Google
* Vértice

Outros tipos podem ser criados e definidos.

_Atributos do termo:_

* _Campo: programação_

### capturar

_verbo_

O processo de conversão de um valor de ordem autorizado em uma transação faturável.
As transações não podem ser capturadas até que sejam autorizadas e as autorizações não podem ser capturadas até que as mercadorias ou os serviços tenham sido enviados.

_Atributos do termo:_

* _Campo: empresa_
* _Termos relacionados: autorização, status do pedido_

### titular do cartão

_substantivo_

Uma pessoa autorizada por uma instituição financeira a fazer compras em uma conta de cartão de crédito.

_Atributos do termo:_

* _Campo: empresa, pedido_

### regras do carrinho

_substantivo_

Regras de preço que são aplicadas ao carrinho de compras e acionam uma ação em resposta a um conjunto de condições.
Usado para criar promoções.

_Atributos do termo:_

* _Campo: software comercial, preços, produto_
* _Termos relacionados: regras de catálogo, carrinho de compras_

### catálogo

_substantivo_

Para comerciantes, o catálogo representa o inventário de produtos.
Na arquitetura do Adobe Commerce, o catálogo consiste em categorias, produtos e atributos de produto.

Cada loja do Commerce tem apenas um catálogo de produtos, que é compartilhado por todas as visualizações da loja.
Em uma instalação com várias lojas, cada loja pode ter um catálogo separado ou compartilhar o catálogo.
O catálogo da loja atual é determinado pela categoria raiz padrão, visível para o usuário na navegação superior (menu principal) da loja.
(O termo &quot;categoria raiz&quot; pode ser confuso, porque a &quot;categoria raiz&quot; não é realmente uma categoria, mas um container para o menu, que consiste em categorias e subcategorias.)

Você pode criar quantas categorias raiz desejar, mas apenas uma (o padrão) pode ser usada de cada vez.

_Atributos do termo:_

* _Campo: software comercial, preços, produto_
* _Termos relacionados: catálogo compartilhado, regra de catálogo_

### regras de catálogo

_substantivo_

Regras de preço que são aplicadas a produtos específicos e acionam uma ação em resposta a um conjunto de condições.
Usado para criar promoções.

_Atributos do termo:_

* _Campo: software comercial, preços, produto_
* _Termos relacionados: regras do carrinho, catálogo_

### categoria

_substantivo_

Um grupo de produtos que têm algo em comum.
O menu principal da loja é organizado em categorias e subcategorias de produtos.

_Atributos do termo:_

* _Campo: software comercial, produto_

### check-out

_substantivo_

O processo de coleta das informações de pagamento e remessa necessárias para concluir a compra dos itens no carrinho de compras.
Depois que o cliente revisar as informações e enviar o pedido, uma confirmação por email será enviada ao cliente.

O check-out tem muitas opções e configurações prontas para uso e por meio da extensão.

Saiba mais: [Tutorial de check-out](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Atributos do termo:_

* _Campo: negócios, design, pedido, produto, programação_

### variáveis de nuvem

_substantivo_

As variáveis de nuvem são variáveis de ambiente específicas do Adobe Commerce na infraestrutura de nuvem e usam o prefixo **`MAGENTO_CLOUD`**.

Saiba mais: [Variáveis de nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Atributos do termo:_

* _Campo: nuvem_

### Bloco CMS

_substantivo_

Uma variante especial de [bloco](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) que só pode ser criada no Administrador e não pode ser referenciada por meio de arquivos de layout.

_Atributos do termo:_

* _Campo: software de comércio_
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

* _Campo: software de comércio_
* _Sinônimos: componente_
* _Termos relacionados: componente de interface do usuário_

### produto configurável

_substantivo_

Um produto configurável se parece com um único produto com listas suspensas de opções para cada variação.
Cada opção é, na verdade, um produto simples separado com um SKU exclusivo, o que permite rastrear o inventário para cada variação de produto.
Para obter um efeito semelhante, um produto simples pode ser usado com opções personalizadas, mas sem a capacidade de rastrear o inventário para cada variação.
Os produtos com várias opções às vezes são chamados de produtos compostos.

Embora um produto configurável use mais SKUs e possa, inicialmente, levar um pouco mais para ser configurado, ele pode economizar seu tempo no final.
Se você planeja expandir seu negócio, o tipo de produto configurável pode ser uma escolha melhor para um produto com várias opções.

Exemplo: camisetas disponíveis em duas cores e três tamanhos.
Seis variantes devem ser criadas como produtos individuais (cada uma com sua própria SKU).
Em seguida, todas as variantes são adicionadas a um produto configurável, em que os clientes podem escolher o tamanho e a cor e, em seguida, adicioná-los ao carrinho.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: tipos de produto_

### taxa de conversão

_substantivo_

A porcentagem de visitantes que são convertidos em compradores.

_Atributos do termo:_

* _Campo: empresa, pedido_

### escalonamento do nível principal

_substantivo_

O dimensionamento do nível principal consiste em três nós de serviço para armazenamento de dados, cache e serviços, como OpenSearch, Elasticsearch, MariaDB, Redis.

_Atributos do termo:_

* _Campo: nuvem_

### memorando de crédito

_substantivo_

Um documento emitido pelo comerciante a um cliente para dar baixa em um saldo pendente devido a sobrecarga, reembolso ou devolução de mercadorias.
O memorando restaura fundos na conta do cliente.

_Atributos do termo:_

* _Campo: empresa, pedido_

### comentário do memorando de crédito

_substantivo_

Detalhes por que um valor de aviso de crédito foi creditado ao cliente.

_Atributos do termo:_

* _Campo: empresa, pedido_

### item de aviso de crédito

_substantivo_

Um item faturado para o qual um comerciante cria um aviso de crédito.

_Atributos do termo:_

* _Campo: empresa, pedido_

### venda cruzada

_substantivo, adjetivo, verbo_

Um produto que aparece ao lado do carrinho de compras.
Quando um cliente navega até a página do carrinho de compras, esses produtos são exibidos como vendas cruzadas para os itens que já estão no carrinho de compras.
Eles são semelhantes a compras por impulso, como revistas e doces nas caixas registradoras de supermercados.

_Atributos do termo:_

* _Campo: empresa, produto_
* _Termos relacionados: venda adicional_

### CVM

_substantivo_

Abreviatura de &quot;Método de verificação do titular do cartão&quot;.
Uma maneira de verificar a identidade do cliente confirmando um código de segurança de cartão de crédito de 3 ou 4 dígitos com o processador de pagamento.

_Atributos do termo:_

* _Campo: empresa, pedido_
* _Sinônimos: Método de Verificação de Titular do Cartão_
* _Termos relacionados: código de segurança_

## D

### esquema de banco de dados

_substantivo_

A estrutura dos dados em um banco de dados.
Define como os dados são organizados e como os relacionamentos de dados são controlados, incluindo todas as restrições aplicadas aos dados.
Um módulo pode conter fragmentos do schema de banco de dados se esse módulo tiver dados que devem ser armazenados no banco de dados.

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: schema_

### injeção de dependência

_substantivo_

Um padrão de design de software que permite que uma classe especifique suas dependências sem ter que construí-las.
Essa classe delega a responsabilidade de injetar a dependência na classe chamadora.
Usado para facilitar os testes.
Para definir dependências para classes, edite o arquivo de configuração di.xml.

_Atributos do termo:_

* _Campo: programação_

### implantar chave

_substantivo_

Uma chave de implantação é a chave pública SSH do projeto e permite acesso somente leitura ou leitura-gravação (se habilitado) a um repositório Git.

Saiba mais: [Conexões seguras](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Atributos do termo:_

* _Campo: nuvem_

### aceitação dupla

_substantivo, verbo_

Um processo de verificação de email que requer que assinantes em potencial concluam uma segunda etapa que confirma sua intenção de assinar.

_Atributos do termo:_

* _Campo: empresa_

### produto baixável

_substantivo_

Um produto para download digital que consiste em um ou mais arquivos baixados, como um eBook, música, vídeo, aplicativo de software ou uma atualização.
Você pode oferecer um álbum para venda e vender cada música individualmente.
Um produto para download pode fornecer uma versão eletrônica do catálogo de produtos.

Os arquivos baixáveis podem residir no servidor ou ser fornecidos como URLs para qualquer outro servidor ou rede de entrega de conteúdo.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: tipos de produto_

### conteúdo dinâmico

_substantivo_

Conteúdo que é gerado pelo código em vez de lido de um modelo estático.
Depois que o conteúdo dinâmico é renderizado inicialmente quando um usuário visita uma página, às vezes o conteúdo pode ser armazenado em cache e reutilizado sem exigir outra chamada dinâmica em uma visita de novo.

_Atributos do termo:_

* _Campo: design_
* _Termos relacionados: php_

### URL do dynamic media

_substantivo_

Um endereço de URL que é gerado dinamicamente pelo sistema para fazer referência a uma imagem ou outra mídia.
O endereço é vinculado diretamente aos ativos armazenados em um servidor ou em uma rede de entrega de conteúdo.
Para usar um URL estático, altere a definição de configuração.
No entanto, se os URLs de mídia dinâmica forem incluídos no catálogo ao desativar a configuração, cada referência no catálogo se tornará um link corrompido.
Os links podem ser restaurados ativando novamente os URLs de mídia dinâmica.
O uso de URLs de mídia dinâmica pode afetar o desempenho da pesquisa de catálogo.

Formato de código: media url=&quot;path/to/image.jpg&quot;

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: rede de entrega de conteúdo, url_

## E

### pacote ece-tools

_substantivo_

Um conjunto de scripts e ferramentas projetado para gerenciar e implantar o aplicativo do Commerce. Esse pacote simplifica muitos processos do Adobe Commerce na infraestrutura em nuvem, incluindo implantação em um ambiente Docker, gerenciamento de crons, verificação da configuração do projeto e aplicação de patches de Adobe.

Saiba mais: [pacote ece-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Atributos do termo:_

* _Campo: cli, nuvem, implantar_

### entidade

_substantivo_

Uma unidade ou objeto exclusivo na programação.
Contém atributos ou parâmetros que podem ser modificados.
Os exemplos incluem estágios — em que uma atualização pode alterar entidades, como regras de preço, produtos ou categorias — e registros de banco de dados — em que os contratos de serviço incluem estruturas de dados enviadas e recebidas.

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: atributo, regras de carrinho, regras de catálogo_

### valor do atributo de entidade

_substantivo_

Para entidades de banco de dados, um modelo de dados que codifica entidades com eficiência.
Armazena a ID da entidade, o nome do atributo e o valor como um triplo, o que permite que novos nomes de atributos de entidade sejam criados a qualquer momento.
Na codificação, o número de atributos que podem ser usados para descrever entidades pode ser extensivamente dimensionado, mas o número que se aplica a uma determinada entidade é minimizado.
Esse modelo de dados é flexível, mas pode ser lento.

Saiba mais: [EAV e extension extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: eav_

### conteúdo permanente

_substantivo_

Conteúdo com uma longa vida útil ou conteúdo que pode ser reutilizado.

_Atributos do termo:_

* _Campo: empresa_

### extensão

_substantivo_

Código que estende ou personaliza o comportamento do Adobe Commerce.
Opcionalmente, é possível empacotar e distribuir uma extensão no Commerce Marketplace ou em outro sistema de distribuição de extensões.
Uma extensão do Commerce pode incluir módulos, temas e pacotes de idiomas.

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: componente, módulo, pacote_

### atributo de extensão

_substantivo_

Amplie a funcionalidade e geralmente use tipos de dados mais complexos do que atributos personalizados. Esses atributos não aparecem na GUI.

Saiba mais: [Adicionando atributos de extensão à entidade](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: atributo, valor de atributo de entidade_

## F

### carga a bordo

_substantivo_

No transporte marítimo internacional, esse termo significa que a parte recebedora é responsável pelos encargos de envio.
O FOB pode ser baseado no local de origem ou destino e ser designado como coleta de frete ou frete pré-pago.

_Atributos do termo:_

* _Campo: negócios, pedido, preços_
* _Sinônimos: fob_

### front-end

_adjetivo_

Em um aplicativo cliente-servidor, há o back-end e o front-end.
O componente de front-end, ou cliente, é uma interface que permite aos usuários manipular ou interagir com o código de back-end subjacente.
O código de backend é executado em um servidor.
Um usuário não pode acessar diretamente o código de backend.
Um usuário interage com a loja, que por sua vez usa o código em execução no servidor do Commerce.

Observação: antigamente, a loja era chamada de &quot;front-end&quot; e o administrador era chamado de &quot;back-end&quot;. Não há mais suporte para este uso.

_Atributos do termo:_

* _Campo: design, programação_
* _Sinônimos: lado do cliente_
* _Termos relacionados: back-end, loja, front-end do cache_

### propriedades de front-end

_substantivo_

Propriedades que determinam a apresentação e o comportamento de um atributo do ponto de vista do cliente em sua loja.

_Atributos do termo:_

* _Campo: design, programação_

### preenchimento

_substantivo_

O processo de gerenciamento de remessas de clientes.

_Atributos do termo:_

* _Campo: empresa_

## G

### cartão-presente

_substantivo_

Um cartão pré-pago ou cartão-presente que pode ser usado para fazer compras na loja.
Cada cartão-presente recebe um código exclusivo que é inserido no check-out.
O valor do cartão-presente é refletido no saldo da conta do cartão-presente.
Há três tipos de cartões-presente:

* Cartões-presente &quot;físicos&quot; podem ser produzidos a partir de plástico ou de cartão, enviados ao cliente.
* Cartões-presente &quot;virtuais&quot; são enviados por email.
* Os cartões-presente &quot;combinados&quot; são uma combinação dos dois, enviados ao recipient como um cartão físico e também entregues por email.
Os cartões-presente são configuráveis, incluindo opções para qualificação de produto e seleção de valores abertos ou fixos.

Um cartão-presente também pode ser resgatado pelo administrador da loja mediante solicitação do cliente quando o pedido estiver sendo criado no back-end.

Cartões-presente também ajudam nas promoções, já que os administradores de lojas podem criar manualmente as contas de cartão-presente no back-end e enviar os códigos de cartão-presente para o segmento de cliente específico.
Os cartões-presente podem servir como um programa de fidelidade direcionado aos clientes mais ativos que fazem várias compras na loja da Web ou uma campanha promocional específica durante os feriados.

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: tipos de produto_

### margem bruta

_substantivo_

A diferença entre custo e preço de um produto.

_Atributos do termo:_

* _Campo: empresa_

### produto agrupado

_substantivo_

Um tipo de produto com vários produtos semelhantes e independentes agrupados em uma única página.
Pode ser oferecido com variações de um único produto ou agrupando-os por temporada ou tema para criar um conjunto coordenado.
Cada produto pode ser comprado separadamente ou como parte do grupo.

Por exemplo, para uma faca disponível em quatro tamanhos, todas as quatro facas podem ser exibidas em uma página de produto agrupada.
Os clientes podem selecionar os tamanhos desejados e adicioná-los ao carrinho a partir desta página.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: produto simples, tipos de produto_

## H

### identificador

_substantivo_

Geralmente, um identificador é uma maneira de fazer referência a um objeto.
No Adobe Commerce, as alças são usadas em muitos lugares, mais comumente para identificar uma página.
Para identificadores de página, o nome do identificador é derivado do URL e, em seguida, usado para localizar e carregar os arquivos de layout da página referenciada.
Por exemplo, no módulo Cliente, há um arquivo de layout chamado &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Aqui &quot;front-end&quot; é o nome da área e &quot;checkout_cart_index&quot; é o nome do identificador, ambos derivados do URL.

_Atributos do termo:_

* _Campo: programação_
* _Sinônimos: identificador da página_

### dimensionamento horizontal

_substantivo_

O dimensionamento horizontal (também conhecido como dimensionamento) é o processo de adicionar outros nós ou máquinas à sua infraestrutura para atender à demanda crescente.

_Atributos do termo:_

* _Campo: nuvem_

## I

### interceptação

_substantivo_

O processo de inserir um novo código antes, depois ou ao redor de uma função pública existente de uma classe PHP.

Para interceptar uma função, um plug-in implementa o código adicional a ser chamado.
Os plug-ins são associados a pontos de interceptação pelo arquivo de configuração de injeção de dependência (di.xml).
Se vários plug-ins forem definidos na mesma função, a configuração de injeção de dependência definirá a ordem em que os plug-ins serão chamados, permitindo que vários plug-ins sejam usados sem conflito.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: plug-in_

## L

### layout

_substantivo_

Na construção de uma página do Commerce, um layout é uma série de blocos montados em uma hierarquia, representando a estrutura da página.

Os arquivos de layout de página se concentram no nível mais alto da estrutura da página (cabeçalho, rodapé, área de conteúdo principal, barra lateral esquerda e assim por diante).
Os arquivos de layout montam o conteúdo (blocos) nessas diferentes áreas da página.

_Atributos do termo:_

* _Campo: design, software de comércio_
* _Termos relacionados: instruções de layout, bloco_

### instruções de layout

_substantivo_

Marcação em um arquivo de layout que descreve as alterações a serem aplicadas a uma árvore de elementos estruturados de blocos, contêineres e componentes da interface do usuário.
Um único arquivo de layout pode conter várias instruções de layout.
As instruções de layout são codificadas em XML em arquivos de layout.

_Atributos do termo:_

* _Campo: design, programação_
* _Termos relacionados: layout, bloco, contêiner, componente da interface_

### atualização do layout

_substantivo_

Usado para fragmentos de código que são adicionados para modificar o layout XML ou importar as instruções de layout de outro arquivo.

_Atributos do termo:_

* _Campo: design, software de comércio_

### Proprietário da licença

_substantivo_

O Proprietário da licença (também conhecido como Proprietário da conta) é a pessoa designada em uma organização de negócios que gerencia pagamentos e outros problemas relacionados aos negócios para a conta Adobe Commerce na infraestrutura em nuvem.
Essa pessoa serve como ponto de contato com o Adobe.
Depois que uma empresa compra um Adobe Commerce na assinatura da infraestrutura em nuvem, o acesso inicial ao projeto e ao código fica disponível somente para a pessoa designada como o Proprietário da licença.

_Atributos do termo:_

* _Campo: empresa_

## M

### MAGEID

_substantivo_

A MAGEID normalmente é o contato de faturamento na conta da Adobe Commerce (e pode não ser o Proprietário do projeto do Adobe Commerce na infraestrutura em nuvem).
Para obter direito de acesso ao Adobe Commerce e Adobe Commerce em pacotes de infraestrutura em nuvem, você deve usar chaves de acesso associadas a uma MAGEID que recebeu acesso a esses pacotes.

Saiba mais: [Obtenha suas chaves de autenticação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Atributos do termo:_

* _Campo: software de comércio_

### marcação

_substantivo_

Em marketing e varejo, uma porcentagem adicionada ao custo de um item para determinar o preço de varejo.
[Configure a marcação](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html) ou o Markdown de um produto por meio de opções personalizáveis do produto.

Em desenvolvimento, um idioma de computador que controla o processamento, a apresentação e a formatação do texto.
Além disso, as tags de marcação são trechos de código que adicionam funcionalidade ou conteúdo a uma página ou bloco do CMS.

_Atributos do termo:_

* _Campo: negócios, programação_
* _Sinônimos: Markdown_

### ambiente mestre

_substantivo_

No Adobe Commerce na infraestrutura em nuvem, os projetos Pro usam um ambiente ativo da Platform as a Service (PaaS) chamado mestre que inclui uma cópia do banco de dados do ambiente de produção e do servidor Web.

_Atributos do termo:_

* _Campo: nuvem_

### conta de comerciante

_substantivo_

Uma conta com um banco ou instituição financeira que permite aceitar transações com cartão de crédito.

_Atributos do termo:_

* _Campo: empresa_

### MFTF

_substantivo_

MFTF é uma [Estrutura de teste funcional](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Ele fornece uma estrutura de teste para desenvolvedores e engenheiros de software do Commerce, como especialistas em controle de qualidade, desenvolvedores de PHP e integradores de sistema.
Os desenvolvedores e o controle de qualidade podem gravar testes para tentar interações do usuário com aplicativos da Web, verificar a funcionalidade e automatizar testes de regressão.

_Atributos do termo:_

* _Campo: software comercial, programação_
* _Termos relacionados: bloco cms, bloco estático, contêiner, layout_

### módulo

_substantivo_

Código que altera ou estende os recursos fornecidos pelo aplicativo Magento.
Um módulo está contido em uma estrutura de diretório que contém arquivos PHP e XML (configuração, blocos, controladores, auxiliares, modelos, etc.) relacionados a uma funcionalidade específica para oferecer uma coleção distinta de recursos do produto.
O objetivo de cada módulo é fornecer recursos específicos do produto implementando uma nova funcionalidade ou estendendo a funcionalidade de outros módulos.
Cada módulo foi projetado para funcionar de forma independente, de modo que a inclusão ou exclusão de um módulo específico não afete a funcionalidade de outros módulos.

Um módulo também pode implementar widgets, que são elementos de página que podem ser personalizados por usuários empresariais no Admin.

Os módulos podem ser desativados ou removidos sem romper a consistência do aplicativo Magento.
Uma exceção: quando o módulo depende de outros módulos, o que requer a desativação ou remoção dos módulos dependentes.

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: php, xml, block_

## O

### OMS

_substantivo_

[OMS](https://omsdocs.magento.com) é a oferta de Sistema Adobe Order Management.

O OMS é uma solução flexível e acessível para gerenciar, vender e realizar o inventário de qualquer canal de vendas.
O OMS oferece uma experiência perfeita ao cliente, o que aumenta as vendas e reduz os custos, além de acelerar o tempo de comercialização.

Os recursos do OMS incluem:

* Visibilidade global e gerenciamento de todo o inventário
* Capacidade de enviar para e de qualquer lugar
* Atendimento ao cliente mais fácil e ágil
* Melhor experiência e fidelidade do cliente

Saiba mais: [Introdução ao OMS](https://omsdocs.magento.com/en/getting-started/), [site de Documentação do OMS](https://omsdocs.magento.com/en/)

_Atributos do termo:_

* _Campo: recursos, software comercial, gerenciamento de pedidos_
* _Sinônimos: gerenciamento de pedidos, MOM, sistema de gerenciamento de pedidos, Magento Order Management_
* _Termos relacionados: gerenciamento de pedidos_

### cloaking de origem

_substantivo_

O cloaking de origem é um recurso de segurança que permite que o Adobe Commerce na infraestrutura em nuvem bloqueie qualquer tráfego que não seja do Fastly para evitar ataques de DDoS, indo para a infraestrutura em nuvem (origem).

Saiba mais: [Fastly origin cloaking](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Atributos do termo:_

* _Campo: segurança_
* _Termos relacionados: firewall do aplicativo web_

## P

### Page Builder

_substantivo_

O Page Builder é uma extensão do Commerce para a criação de páginas ricas em conteúdo ao arrastar e soltar controles pré-criados para definir layouts personalizados.
Esses controles também são conhecidos como &quot;tipos de conteúdo&quot;.
Os comerciantes podem criar layouts e páginas sem experiência de codificação.
O suporte à extensão é fornecido para desenvolvedores que ampliam o Page Builder.

Saiba mais: [Guia do Usuário do Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [DevDocs do Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Atributos do termo:_

* _Campo: software comercial, design_
* _Sinônimos: Administrador, Painel de Administração, back-end, Interface de Administração, Interface de Administrador_
* _Termos relacionados: admin_

### gateway de pagamento

_substantivo_

Um gateway de pagamento é um serviço de terceiros que processa facilmente transações com cartão de crédito sem que o cliente saia do site do comerciante.

_Atributos do termo:_

* _Campo: negócios, ordem, programação_

## R

### produto relacionado

_substantivo_

Uma seleção de produtos que é apresentada como um incentivo para comprar itens adicionais.
Por exemplo, se o cliente estiver visualizando a página do produto de uma câmera, os produtos relacionados poderão incluir outras câmeras comparáveis, um gabinete de câmera e um tripé.

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

No Adobe Commerce, o escopo descreve a extensão da hierarquia de loja que uma configuração pode afetar.
O escopo pode se aplicar ao seguinte:

* Global — todas as visualizações de sites, lojas e lojas
* Site — o site selecionado e todas as lojas e visualizações de loja sob ele
* Armazenamento — o armazenamento selecionado e todas as exibições de armazenamento sob ele
* Exibição de Armazenamento — a exibição de armazenamento selecionada.

Na hierarquia, as configurações aplicadas em um nível inferior podem substituir algumas configurações de nível superior.

_Atributos do termo:_

* _Campo: software de comércio_

### contrato de serviço

_substantivo_

Um conjunto de interfaces PHP definidas para um módulo.
Um contrato de serviço inclui interfaces de dados, que preservam a integridade dos dados, e interfaces de serviço, que ocultam detalhes de lógica de negócios de solicitantes de serviço, como controladores, serviços da Web e outros módulos.
As APIs da Web podem ser vinculadas a contratos de serviço por meio de arquivos de configuração.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: php, api da web_

### liquidação

_substantivo_

A liquidação ocorre quando o banco adquirente e o emitente trocam fundos e os proveitos são depositados na conta do comerciante.

_Atributos do termo:_

* _Campo: empresa_

### Catálogo compartilhado

_substantivo_

Um recurso que permite aos comerciantes criar um catálogo que pode servir como catálogo inteiro ou subconjunto dele e, em seguida, atribuir preços personalizados para um ou mais produtos.
Os comerciantes podem atribuir esse catálogo a uma ou mais empresas.

Por exemplo, um comerciante B2B tem três clientes que negociaram taxas específicas para o site de distribuição de eletrônicos do comerciante.
Usando o recurso de catálogo compartilhado, o comerciante tem:

* Um catálogo principal
* Um catálogo do cliente 1 (talvez sejam apenas três SKUs com grandes descontos do catálogo principal)
* Catálogo do cliente 2 (pode ser o catálogo inteiro com 10% de desconto)
* Catálogo do cliente 3 (algumas dezenas de produtos com descontos do catálogo principal que variam de 5% a 60%).

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: catálogo, b2b_

### remessa

_substantivo_

Uma entrega contém produtos a serem entregues e gera um registro dos produtos em uma ordem que foi entregue.
Mais de uma remessa pode ser associada a um único pedido.

_Atributos do termo:_

* _Campo: empresa, pedido_

### documento de entrega

_substantivo_

Um documento que acompanha uma entrega. O documento lista os produtos e suas quantidades no pacote de entrega.

_Atributos do termo:_

* _Campo: empresa, pedido_

### transportadora

_substantivo_

Uma empresa que transporta pacotes. As operadoras comuns incluem UPS, FedEx, DHL e USPS.

_Atributos do termo:_

* _Campo: empresa, pedido_

### carrinho de compras

_substantivo_

O conjunto de produtos que um cliente selecionou para comprar, mas ainda não comprou.
Também se refere a uma área de um site de comércio eletrônico em que esses produtos podem ser encontrados para revisão e finalização.

_Atributos do termo:_

* _Campo: negócios, design, produto, programação_
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
* _Termos relacionados: tipos de produto_

### SKU

_substantivo_

Abreviação de Unidade de Manutenção de Estoque.
Um número ou código atribuído a um produto para identificar o produto, as opções, o preço e o fabricante.

_Atributos do termo:_

* _Campo: negócios, preços, produto, programação_
* _Termos relacionados: catálogo compartilhado_

### página inicial

_substantivo_

Uma página promocional com um produto ou anúncio; normalmente exibida antes da página inicial.

_Atributos do termo:_

* _Campo: design_

### bloco estático

_substantivo_

Uma unidade modular de conteúdo que pode ser colocada por um usuário no CMS em uma página para exibir texto e imagens ou executar trechos de código.
Os blocos estáticos contêm conteúdo editável e podem atuar como páginas iniciais para categorias de produto.
Widgets podem ser adicionados a blocos estáticos para fornecer funcionalidade adicional.

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: bloco cms, bloco_

### conteúdo estático

_substantivo_

Conteúdo gerado pelo usuário (não gerado pelo código) que não é alterado com frequência.

_Atributos do termo:_

* _Campo: design_
* _Termos relacionados: conteúdo dinâmico_

### arquivos estáticos

_substantivo_

A coleção de ativos, como CSS, fontes, imagens e JavaScript, usada por um tema.

_Atributos do termo:_

* _Campo: software de comércio_

### loja

_substantivo_

O nível de escopo do Commerce de &quot;loja&quot; é o segundo nível da hierarquia do site, que é a seguinte: site > loja > visualização de loja.
As lojas podem ser organizadas em uma ou várias. Cada loja, possivelmente, tem sua própria categoria raiz e todos compartilham catálogos e dados de clientes.

Cada loja pode ter várias visualizações de loja, que normalmente são usadas para apresentar a loja em um local e idioma diferentes.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: exibição de loja, site_

### exibição de loja

_substantivo_

O nível de escopo do Commerce de &quot;exibição de loja&quot; refere-se ao terceiro nível na hierarquia de sites, lojas e visualizações de loja.
As visualizações de loja normalmente apresentam a loja em um local e idioma diferentes.
Para alterar exibições de loja, use o seletor de loja no cabeçalho.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: loja, site_

### vitrine

_substantivo_

A loja online que os clientes experimentam quando visitam o site do Commerce.

_Atributos do termo:_

* _Campo: software comercial, produto_

## T

### regra de imposto

_substantivo_

Uma combinação de uma classe de imposto do produto, classe de imposto do cliente e alíquota do imposto. Essa regra define qual cálculo de imposto é aplicado.

_Atributos do termo:_

* _Campo: empresa_

### modelo

_substantivo_

Abreviação de HTML template ou PHTML template.
Um arquivo PHTML contém uma mistura de marcação HTML e código PHP para inserir conteúdo dinâmico no HTML.
A maioria dos blocos tem pelo menos um arquivo PHTML (modelo) que contém o HTML estático gerado pelo bloco.
Nos modelos de Admin, email e boletim informativo, eles combinam texto, imagens e variáveis com a marcação HTML para produzir conteúdo personalizado enviado pelo sistema.

_Atributos do termo:_

* _Campo: software de comércio_
* _Termos relacionados: bloco_

### tema

_substantivo_

Contém informações de gráficos e aparência.
Personaliza a aparência da loja.
O Adobe Commerce pode enviar temas em pacotes (Composer).
Mas os temas podem ser colocados em um aplicativo/design, que não é enviado em um pacote.
Os pacotes são a unidade de download do Composer e, via Commerce Marketplace, os usuários do Commerce podem baixar CE ou EE como uma série de pacotes, em que os pacotes contêm módulos, temas ou pacotes de idiomas.

_Atributos do termo:_

* _Campo: software de comércio_

## U

### Componente da UI

_substantivo_

Uma tag projetada para o software Adobe Commerce a fim de permitir uma renderização mais simples e flexível da interface do usuário.
As metas do sistema de componentes da interface do usuário incluem o seguinte:

* Simplificação do identificador de layout em arquivos XML
* Transferência de elementos da interface do usuário de Admin do HTML+JavaScript para um sistema de widgets personalizados &quot;puro JavaScript&quot;
* Habilitação da criação de componentes de interface do usuário mais complexos a partir de componentes menores
* Pré-renderização de dados para componentes da interface do usuário como JSON, vinculando estreitamente a objetos de dados de back-end
* Utilização do AJAX para atualizar dados de componentes
* Introdução de um novo DSL para criar os itens acima

Saiba mais: [guia de Componentes da Interface do Usuário](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: JavaScript, layout, componente, construtor de páginas_

### PARA CIMA

_substantivo_

[PWA Studio](https://github.com/magento/pwa-studio) usa [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) no desenvolvimento.
UPWARD é um acrônimo para Unified Progressive Web App Response Definition.
Um arquivo de definição UPWARD descreve como um servidor Web fornece e suporta um Progressive Web Application.

Os arquivos de definição UPWARD fornecem detalhes sobre o comportamento do servidor usando linguagem declarativa independente de plataforma.
Isso permite que um Progressive Web Application seja executado sobre um servidor compatível com UPWARD em qualquer idioma em qualquer pilha de tecnologia, pois o aplicativo se preocupa somente com o comportamento do ponto de extremidade HTTP do servidor UPWARD.

Um servidor UPWARD usa um arquivo de definição para determinar o processo ou serviço apropriado para uma solicitação de um shell de aplicativo.
Ele descreve como o servidor deve lidar com uma solicitação e criar a resposta para ela.

Um projeto PWA pode incluir um arquivo de definição UPWARD para especificar suas dependências de serviço.

_Atributos do termo:_

* _Campo: design, software comercial, programação_
* _Sinônimos: PWA Studio, Definição De Resposta Unificada Do Aplicativo Web Progressivo_
* _Termos relacionados: pwa_

## V

### Extensão agrupada do fornecedor

_substantivo_

O código produzido pelo fornecedor que estende ou personaliza o comportamento do Commerce e opera como uma extensão de terceiros é considerado uma Extensão agrupada do fornecedor (VBE).
Os VBEs são totalmente testados e incluídos em cada versão compatível do Adobe Commerce.
Um VBE pode incluir módulos, temas e pacotes de idiomas.

Saiba mais no [tópico sobre Extensão agrupada de fornecedores](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Atributos do termo:_

* _Campo: extensão de comércio, extensão agrupada do fornecedor, extensão, VBE_
* _Sinônimos: extensão, VBE_
* _Termos relacionados: extensão, extensão agrupada_

### escala vertical

_substantivo_

Escalonamento vertical (escalonamento) refere-se ao aumento da potência de processamento de um único servidor ou cluster adicionando E/S de disco ou rede, CPUs ou RAM.

_Atributos do termo:_

* _Campo: ambiente_

### produto virtual

_substantivo_

Representa um produto não físico que pode ser vendido, como associação, serviço, garantia ou assinatura.
Os produtos virtuais podem ser vendidos individualmente ou incluídos como parte dos seguintes tipos de produtos: produto agrupado e produto de pacote.
Não requer remessa ou inventário.

O processo de criação de um produto virtual e de um produto simples é quase o mesmo.
No entanto, como um produto virtual não é enviado, não há nenhum campo Peso ou opção para incluir um cartão-presente.

_Atributos do termo:_

* _Campo: software comercial, produto_
* _Termos relacionados: tipos de produto_

### tipo virtual

_substantivo_

Tipos virtuais são uma maneira de injetar diferentes dependências em classes PHP existentes sem afetar outras classes e sem ter que criar um arquivo de classe.
Os tipos virtuais só podem ser referenciados por substituições de argumento em um elemento `<type>` dentro de arquivos di.xml, nunca no código-fonte.
Elas não podem ser estendidas e não podem ser referências como dependências em um construtor de classes.

_Atributos do termo:_

* _Campo: programação_
* _Termos relacionados: php_

## W

### site

_substantivo_

No software Adobe Commerce, o nível mais alto de uma hierarquia de site, acima da visualização de loja e loja.
Você pode ter vários sites e cada um deles pode ter um nome de domínio diferente.
Os sites podem ser configurados para compartilhar dados do cliente ou para não compartilhar dados.

_Atributos do termo:_

* _Campo: software comercial, design, produto_
* _Termos relacionados: armazenamento, exibição de armazenamento_

### widget

_substantivo_

Um [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) é um trecho de código preparado que pode ser usado para colocar blocos, links e conteúdo dinâmico em locais específicos nas páginas da loja.
Você pode usar widgets para criar páginas de aterrissagem para campanhas de marketing, exibir conteúdo promocional em locais específicos na loja.
Os widgets também podem ser usados para adicionar elementos interativos e blocos de ação para sistemas de revisão externos, chats de vídeo, votações e formulários de subscrição ou para fornecer elementos de navegação para nuvens de tags e controles deslizantes de imagem.

_Atributos do termo:_

* _Campo: negócios, software de comércio, design_
* _Termos relacionados: bloco_
