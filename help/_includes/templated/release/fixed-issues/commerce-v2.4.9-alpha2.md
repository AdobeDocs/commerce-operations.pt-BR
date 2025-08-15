---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4413'
ht-degree: 0%

---
# Correção de problemas do Adobe Commerce (v2.4.9-alpha2)

## Correção de problemas na v2.4.9-alpha2

Corrigimos 118 problemas no código principal Adobe Commerce 2.4.9-alpha2. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

#### O Preço Especial Acumulado foi validado incorretamente em applySpecialPrice

O sistema está funcionando sem problemas com relação ao Preço especial e o Preço especial do produto expirará na data definida pelo administrador ou sistema de terceiros pela API REST

_AC-13130 - [Problema do GitHub](https://github.com/magento/magento2/issues/39169) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39690)_

#### Corpo de solicitação ou parâmetros malformados causam &quot;Erro interno do servidor&quot;

_AC-746 - [Problema do GitHub](https://github.com/magento/magento2/issues/32784) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### A ordem &quot;base_row_total&quot; e &quot;row_total&quot; mostra o preço de item único na resposta da API REST

A resposta da API REST para detalhes do pedido agora contém valores corretos para os atributos &quot;base_row_total&quot; e &quot;row_total&quot; caso vários itens iguais tenham sido solicitados

_ACP2E-3874 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### APIs, Ordem

#### [NUVEM] Problema de informações do pedido com aparência total da linha para o pedido 000075568

Corrige o problema em que o valor row_total_incl_tax na resposta da API do pedido era retornado como um valor residual próximo de zero em vez de 0,00 quando um item era totalmente descontado.

_ACP2E-3950 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Conta

#### Problema ao atualizar o email do cliente no Painel de administração com o domínio ö e .swiss

_AC-13409 - [Problema do GitHub](https://github.com/magento/magento2/issues/39394) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### A opção habilitada para assinatura do informativo não está funcionando por site/loja

O sistema lida corretamente com a assinatura com o boletim informativo quando temos vários sites/lojas quando ele foi desativado em nível global

_AC-14283 - [Problema do GitHub](https://github.com/magento/magento2/issues/39751) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39752)_

#### Substituir uma condição de segmento de cliente &quot;O produto foi visualizado&quot;

_AC-14542_

#### [Problema] Remoção de divulgação de email

O Sistema agora mostra Exibir uma mensagem de erro indicando um email incorreto se o email inserido não for necessário para confirmar a conta, independentemente de o cliente existir ou não.

_AC-14561 - [Problema do GitHub](https://github.com/magento/magento2/issues/39574) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39570)_

### Interface do administrador

#### Os valores de FPT na página do carrinho e na página do produto são diferentes para as mesmas configurações de produto simples

_AC-13066 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### As opções de atributo de seleção múltipla não podem ser salvas quando os módulos Amostras estão desativados

_AC-13071 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Os valores de FPT na página do carrinho e na página do produto são diferentes para as mesmas configurações de um produto dinâmico

_AC-13075 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### A cor de foco não é aplicada em grades estáticas no admin

As cores de focalização agora são aplicadas conforme esperado nas linhas de grades estáticas de Administração.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problema do GitHub](https://github.com/magento/magento2/issues/35358) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/35384)_

#### Usuários administradores restritos não podem atualizar o status do produto em massa

O administrador personalizado pode atualizar o status do produto em massa, pois é uma propriedade no nível do site. O status é atualizado somente nos sites aos quais o administrador restrito tem acesso.

_ACP2E-3772_

#### [Preparo2] Os cartões armazenados não estão visíveis no painel Administrador

Corrige o problema em que a opção de pagamento &quot;Cartão armazenado&quot; não aparecia mais no formulário de posicionamento de pedido de back-end após uma atualização.

_ACP2E-3830 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### falha na validação de campo da empresa para check-out do convidado

_AC-14987 - [Problema do GitHub](https://github.com/magento/magento2/issues/40011) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

### Pacote

#### Excluir arquivos JS do editor hugerte da saída agrupada entre temas

_AC-15128 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/43648891) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2bc584af)_

### Carrinho e saída

#### As validações de quantidade de front-end de produto agrupado estão ausentes

Agora o sistema está funcionando bem e exibindo um erro de validação quando estamos tentando adicionar uma quantidade negativa e uma quantidade máxima

_AC-13524 - [Problema do GitHub](https://github.com/magento/magento2/issues/39479) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39480)_

#### Prefixo de convidado não salvo no endereço de cotação 2.4.8

_AC-14705 - [Problema do GitHub](https://github.com/magento/magento2/issues/39915) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### [Problema] Definir preço em item de cotação em vez de base_price

O sistema manipula corretamente o preço do item da cota definido como base_price em vez do preço se você tiver várias moedas em um site no front-end

_AC-9985 - [Problema do GitHub](https://github.com/magento/magento2/issues/38094) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36878)_

#### [Cloud] Ordens recentes não aparecem na exibição de outra loja se as ordens forem criadas em uma exibição de loja

Solução de um problema em que a página &quot;Minha conta&quot; não exibia pedidos recentes de outras Exibições da loja na mesma loja. A lógica de recuperação do pedido foi atualizada para garantir uma visibilidade consistente do pedido em todas as Exibições da loja, alinhada ao comportamento da página &quot;Meus pedidos&quot;.

_ACP2E-3807 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### qtd. exibida como  0 na seção carrinho de compras do cliente administrador ao adicionar produtos do PACOTE  

A seção Carrinho de compras em Atividades do cliente agora exibe a quantidade correta. Anteriormente, a quantidade era mostrada como 0.

_ACP2E-3872 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Carrinho e check-out, GraphQL

#### Erro ao mapear a mensagem para o código de erro ao fazer o pedido via GraphQL

As chamadas do GraphQL para fazer um pedido de um carrinho inexistente ou inativo agora retornam corretamente os códigos de erro CART_NOT_ATIVE ou CART_NOT_FOUND em todas as exibições de loja, corrigindo um problema em que as mensagens de erro traduzidas anteriormente resultavam em um código INDEFINIDO.

_ACP2E-3942 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Carrinho e check-out, GraphQL, inventário/MSI

#### O atributo is_available em CartItemInterface retorna false mesmo quando o estoque comercializável está alto

O atributo is_available retorna true quando o estoque vendável está alto. Anteriormente, retornava sempre falso.

_ACP2E-3885 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Catálogo

#### Erro de escopo no recurso de URL do catálogo (_getCategories)

Essa PR adiciona um fallback ao escopo padrão se não houver um valor definido no escopo de armazenamento no recurso de URL de categoria.

_AC-11011 - [Problema do GitHub](https://github.com/magento/magento2/issues/38393) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problema] Verifique se o OpenGraph pode mostrar o preço

O sistema está funcionando bem quando usamos plug-in que oculta o preço e com esse preço de alteração não está visível na tag OG.

_AC-11635 - [Problema do GitHub](https://github.com/magento/magento2/issues/38512) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38510)_

#### API REST [Bug]: a opção Atualizar preços especiais não define valores para todas as exibições de loja

_AC-13671 - [Problema do GitHub](https://github.com/magento/magento2/issues/39521) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Erro PHP [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] despercebido

Esta PR Altera um nome de variável de loop para adicionar corretamente os dados &quot;_cache_instance_product_ids&quot; no produto fornecido a ser usado em chamadas subsequentes.

_AC-14159 - [Problema do GitHub](https://github.com/magento/magento2/issues/39641) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39642)_

#### [Linha Principal] [NUVEM] O redimensionamento de imagens consome mais de 400 GB de espaço em disco

Após a correção, o comando `catalog:images:resize` usado com o sinalizador —skip_hidden_images não gerará caches de imagens para sites em que imagens não estão presentes.

_ACP2E-3869 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### A ID do país fornecida não existe - Irlanda (IE)

Após a correção, os códigos postais da Irlanda estão disponíveis para procurar locais de coleta.

_ACP2E-3932 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

### Catálogo, Desempenho

#### As categorias no administrador estão carregando muito lentamente

O desempenho do carregamento da categoria foi significativamente melhorado. Anteriormente, levava muito tempo para carregar a categoria que causava um problema de tempo limite.

_ACP2E-3891 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catálogo, Preços

#### Desconto de regra de preço de catálogo incorreto aplicado ao produto filho

Corrige o problema em que a regra de preço de catálogo para a variação é substituída pelo produto configurável principal, caso ambas as regras tenham a mesma prioridade.

_ACP2E-3693 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

### Catálogo, Pesquisa

#### Solicitação RestApi &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; falha com erro de tempo limite

_AC-13358 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Conteúdo

#### Depois da atualização para o magento 2.4.7 p2, não é possível visualizar a galeria de mídia de arquivos recém-carregados

_AC-13262 - [Problema do GitHub](https://github.com/magento/magento2/issues/39275)_

#### A remoção completa de uma imagem de galeria da be mantém as funções/tipos de escopo definidos (base/pequeno/miniatura) e, após adicionar novamente as funções/tipos &quot;antigos&quot;, são exibidas

O sistema está funcionando como esperado nos escopos de armazenamento. As imagens herdam as funções/tipos da nova imagem adicionada de acordo com o escopo padrão

_AC-13556 - [Problema do GitHub](https://github.com/magento/magento2/issues/39481) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Pequeno Erro] O Filtro do Painel de Administração `listing component` não pode ser acessado quando o valor do campo contém `\`

O sistema está funcionando bem ao filtrar o título da página com uma barra (por exemplo: Magento\Store)

_AC-13661 - [Problema do GitHub](https://github.com/magento/magento2/issues/39513) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39535)_

#### &quot;A página do CMS com a ID &quot;0&quot; não existe&quot; inundação de log

O sistema está funcionando como esperado depois de criar um usuário administrador e ao criar uma nova página, system.log não tem mensagens de erro

_AC-14254 - [Problema do GitHub](https://github.com/magento/magento2/issues/39743) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39746)_

#### Os widgets de link do catálogo usam URL incorreto

O Sistema agora lida corretamente com widgets após adicionar link de produto de catálogo e link de categoria de catálogo e também mostra urls corretos na fonte html

_AC-14437 - [Problema do GitHub](https://github.com/magento/magento2/issues/39464) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39710)_

#### O componente de Produto do Page Builder não funciona se o usuário não tiver permissão de Widget

Antes da correção, ao acessar um widget sem permissões, a página gerava um erro genérico e exibia um GIF &quot;carregando&quot;. Agora, após a correção, uma janela modal é exibida com &quot;Desculpe, você precisa de permissões para visualizar este conteúdo&quot;. mensagem.

_ACP2E-3664 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### A ordem do Widget de produto do Page Builder não é aplicada no GraphQL

Corrige o problema em que a resposta de consulta de &quot;rota&quot; do GraphQL não retornava produtos na ordem de classificação correta em um tipo de conteúdo de Produtos do Page Builder.

_ACP2E-3898 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problema na exibição de preços em vitrines em outros idiomas devido à versão da biblioteca ICU

Após a correção, o preço do produto é exibido corretamente no local Hebraico (Israel).

_ACP2E-3938 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Atualizando configuração de design limpa do código da loja

Correção do problema em que a atualização do código de exibição de armazenamento limpava as configurações de Design devido à atualização incorreta do cache de configuração.

_ACP2E-3941 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Estrutura

#### Erro ao executar a configuração do comando :upgrade com o gatilho DB personalizado

_AC-11487 - [Problema do GitHub](https://github.com/magento/magento2/issues/38481)_

#### O formulário de entidade de site/grupo/loja não pode ser estendido com elemento de formulário de vários valores para atributos de extensão

Essa PR permite que elementos de formulário multivalor enviem dados para o formulário de site/grupo/loja.

_AC-11657 - [Problema do GitHub](https://github.com/magento/magento2/issues/24070) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problema] Remover uso do resolvedor de escopo

Esta PR resolve as configurações de URL do Administrador globalmente em vez do armazenamento atual

_AC-11736 - [Problema do GitHub](https://github.com/magento/magento2/issues/38566) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38554)_

#### Exposição da versão do Magento por meio da rota de configuração com a configuração padrão do Nginx

O sistema agora está funcionando como esperado e não expõe a versão exata do Magento que o site está executando

_AC-13205 - [Problema do GitHub](https://github.com/magento/magento2/issues/39227) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problema] refatorar endereço de cotação fazer validar método

Esta PR inclui melhorias de legibilidade para o método doValidate.

_AC-13214 - [Problema do GitHub](https://github.com/magento/magento2/issues/38230) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38219)_

#### opção do Magento — magento-init-params nunca usado ao executar a cli?

_AC-13231 - [Problema do GitHub](https://github.com/magento/magento2/issues/39248) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### declaração de tipo incorreto de getItemsByColumnValue

O sistema agora define corretamente o parâmetro de entrada $value como um tipo primitivo, não uma matriz, na função getItemsByColumnValue, garantindo que a função retorne a coleção esperada. Anteriormente, se uma matriz com um único valor fosse usada como o parâmetro de entrada, a função retornaria como nulo e os IDEs a marcariam como um erro.

_AC-13240 - [Problema do GitHub](https://github.com/magento/magento2/issues/33070) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33120)_

#### Chaves de cache associadas ao FPC em implementações de várias lojas do Magento 2.4.7

_AC-13719 - [Problema do GitHub](https://github.com/magento/magento2/issues/39456) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### API Rest do Magento apresentando PII

_AC-13904 - [Problema do GitHub](https://github.com/magento/magento2/issues/39336)_

#### A indexação parcial parou de funcionar para clientes com um grande número de atualizações

_AC-14424 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Investigar se o &quot;uso estrito&quot; é desnecessário dentro dos módulos

_AC-14517 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Depois de Baixar etiqueta de envio, podemos ver alguma quantidade de envio que não estava correspondendo com o preço de envio e manuseio.

_AC-14560_

#### O mecanismo do MView ignora erros silenciosamente na execução do acionador

_AC-14567 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problema] Evite muitas exceções desnecessárias durante o carregamento da mesclagem XML do layout

Essa PR apresenta uma nova função (para compatibilidade B/C, não substituímos a _loadXmlString protegida) para carregar e não lançar uma exceção

_AC-14580 - [Problema do GitHub](https://github.com/magento/magento2/issues/39877) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37570)_

#### [Problema] Usar promoção de propriedade do construtor no gráfico Ql do Vault do módulo

Esta PR substitui as propriedades do construtor pela promoção de propriedade no módulo VaultGraphQl

_AC-14616 - [Problema do GitHub](https://github.com/magento/magento2/issues/39900) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36996)_

#### [Problema] Remoção da redundância de código para layouts de front-end de módulo.

Esta PR remove a redundância de código para layouts de tema para os layouts de front-end dos módulos Magento_Msrp, Magento_LoginAsCustomerAssistance, Magento_Newsletter e Magento_Sitemap.

_AC-14625 - [Problema do GitHub](https://github.com/magento/magento2/issues/30673) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/30644)_

#### [Problema] Remover código relacionado ao Microsoft IIS

Essa PR limpa o código relacionado ao Microsoft IIS de acordo com a documentação de Requisitos do Sistema do Magento, que declara que o sistema operacional Microsoft Windows não é compatível

_AC-14702 - [Problema do GitHub](https://github.com/magento/magento2/issues/39910) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39894)_

#### Erro de sintaxe da Magnifier.js

A funcionalidade da Lupa do sistema deve continuar funcionando da maneira que funcionava antes, e a lupaOptions não deve estar disponível no escopo global

_AC-14722 - [Problema do GitHub](https://github.com/magento/magento2/issues/36200) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39321)_

#### Modo Detalhado de Backport no comando da CLI `setup:db:status`

_AC-14807 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Envio de email SMTP com tls e 2.4.8

_AC-14883 - [Problema do GitHub](https://github.com/magento/magento2/issues/39947) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problema] Corrigir problema de simultaneidade na implantação de conteúdo estático

Esta PR corrige um erro em que vários processos simultâneos são gerados para lidar com o mesmo pacote de tema, dependendo de como os temas são definidos com seus pais.

_AC-14944 - [Problema do GitHub](https://github.com/magento/magento2/issues/39990) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problema] Remover código de compatibilidade herdado para versões do PHP &lt; 8.1

Este pull request remove o código que foi projetado para ser executado no PHP &lt;8.1.
Além disso, a remoção verifica a disponibilidade de contato do PHP_VERSION_ID, uma vez que está disponível em todas as versões do PHP

_AC-14971 - [Problema do GitHub](https://github.com/magento/magento2/issues/39891) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39882)_

#### O FPC não funciona ao fazer logon

_AC-14999 - [Problema do GitHub](https://github.com/magento/magento2/issues/40007) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/)_

#### [Problema]: melhorar a manipulação de erros do SchemaBuilder

Essa PR melhora a manipulação de mensagens de erro do esquema db. Isso nos ajuda a identificar o problema sem uma depuração pesada.

_AC-15020 - [Problema do GitHub](https://github.com/magento/magento2/issues/39816) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39799)_

#### Falha no teste de integração no SYNC PR para desenvolvimento 2.4.9-alpha2 devido à modificação CliStateTest

_AC-15136 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2d0f8066)_

#### Bugfix do tipo PHP8.1

Os produtos associados agora são inicializados em uma matriz vazia em vez de false quando o modo de processamento estrito não está ativo ou quando as informações do produto estão disponíveis. Essa alteração garante que a lógica subsequente de manuseio de produtos associados se comporte de forma consistente, melhorando a estabilidade e a previsibilidade no processo de preparação do produto.

_AC-6017 - [Problema do GitHub](https://github.com/magento/magento2/issues/35808) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/35842)_

#### [Problema] Remover a marca `@author` proibida da estrutura (parte 3)

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8343 - [Problema do GitHub](https://github.com/magento/magento2/issues/37270) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problema]: usar promoção de propriedade de construtor no módulo enviar gráfico amigo ql

O sistema agora utiliza a promoção de propriedade do construtor no módulo GraphQL &quot;enviar amigo&quot;, melhorando a legibilidade do código e reduzindo a complexidade. Anteriormente, o módulo usava propriedades que ocupavam várias linhas, tornando o código mais complexo e menos legível.

_AC-8346 - [Problema do GitHub](https://github.com/magento/magento2/issues/37235) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problema] Remover a marca `@author` proibida de `Magento_Downloadable`

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8355 - [Problema do GitHub](https://github.com/magento/magento2/issues/37251) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade e a consistência do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8358 - [Problema do GitHub](https://github.com/magento/magento2/issues/37264) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8360 - [Problema do GitHub](https://github.com/magento/magento2/issues/37261) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8361 - [Problema do GitHub](https://github.com/magento/magento2/issues/37260) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8363 - [Problema do GitHub](https://github.com/magento/magento2/issues/37258) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37008)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8375 - [Problema do GitHub](https://github.com/magento/magento2/issues/37257) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37007)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8376 - [Problema do GitHub](https://github.com/magento/magento2/issues/37256) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37006)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8400 - [Problema do GitHub](https://github.com/magento/magento2/issues/37254) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37004)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8401 - [Problema do GitHub](https://github.com/magento/magento2/issues/37255) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37005)_

#### [Problema] Melhore a Extensibilidade de Geração de URL de Serviço

O sistema agora permite a personalização da função de Geração de URL de serviço por meio de plug-ins, promovendo uma abordagem mais sustentável às modificações. Anteriormente, a personalização dessa função era obtida por meio de preferências, que podem não ter sido tão eficientes ou sustentáveis.

_AC-8813 - [Problema do GitHub](https://github.com/magento/magento2/issues/37404) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37403)_

#### Problema com a atualização 2.4.7-p5 devido à adição de uma nova validação

Correção de um problema na classe SchemaBuilder em que uma &quot;coluna&quot; de chave de matriz indefinida causava uma falha durante a criação ou as atualizações do esquema. Isso ocorria ao processar dados da tabela que não incluíam uma chave de &quot;coluna&quot;.

_ACP2E-3871 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### Erro de descontinuação do PHP8.4: E_USER_ERROR após a atualização para o Adobe Commerce 2.4.8

Os cenários voltados para o cliente não são afetados pela correção.

_ACP2E-3963 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Framework, Search

#### Opensearch 2.19.1 invalid_argument_exception em categorias com um preço

O Opensearch não está mais gerando um invalid_argument_exception nas categorias que contêm todos os produtos com o mesmo preço. Anteriormente, ele tinha esta exceção &quot;[do] parâmetro não pode ser negativo&quot;.

_ACP2E-3896 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### o graphql customerOrders retorna um erro quando o produto é excluído

A solicitação graphql customerOrders não está mais gerando um erro mesmo que o produto no pedido tenha sido excluído. Anteriormente, o erro &quot;Erro interno do servidor&quot; era exibido.

_ACP2E-3936_

#### Os itens da lista de desejos não são compartilhados entre visualizações de lojas em um site na solicitação do GraphQL

Antes da correção, os itens da lista de desejos eram filtrados pela ID da loja. Agora, após a correção, os itens da lista de desejos são filtrados por site.

_ACP2E-3987 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, Produto

#### Falta media_type no graphql do produto em MediaGalleryInterface

A solicitação do MediaGallery GraphQL agora inclui o campo &quot;tipos&quot; para tipos de imagem de produto. Anteriormente, esse campo &quot;tipos&quot; não existia na solicitação do MediaGallery GraphQL.

_ACP2E-3880 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Inventário / MSI

#### Nenhuma loja está disponível após o redirecionamento para a página inicial e o check-out

A loja selecionada anteriormente será pré-selecionada na remessa &quot;Separar na loja&quot; se o cliente navegar até a página de pagamento, retornar à página inicial e finalmente retornar à página de check-out. Anteriormente, após retornar repetidamente à página de check-out, a loja selecionada em &quot;Selecionar na loja&quot; era apagada.

_ACP2E-3793 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

### Pedido

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) quebra customAttributes

_AC-10568 - [Problema do GitHub](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento reorder -1 números de ordem

O sistema está funcionando como esperado e, após reordenar a partir do backend, o número do pedido será exclusivo de 8 dígitos

_AC-12854 - [Problema do GitHub](https://github.com/magento/magento2/issues/39089) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39399)_

#### Perdendo o upload do arquivo de opção personalizada do produto ao fazer check-out com o método de pagamento com cartão de crédito do Adobe

_AC-14306 - [Problema do GitHub](https://github.com/magento/magento2/issues/39647)_

#### Status do pedido paralisado no processamento

Antes da correção, ao solicitar um produto combinado com a opção &quot;Enviar juntos&quot; ativada, o status do pedido não alternava automaticamente para &quot;Concluído&quot; após a fatura e o envio. Agora, após a correção, o status do pedido muda automaticamente para &quot;concluído&quot; depois que o pedido é faturado e enviado.

_ACP2E-3947 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Código OOTB da ]Magento da {Cloud- Problema de configuração de modelo de email

Antes da correção, ao usar o envio assíncrono de email, os emails de remessa eram inconsistentes com a ordem da loja. Agora, após a correção, a ordem de e-mail de envio da loja correta é entregue.

_ACP2E-3998 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Outras ferramentas de desenvolvedor

#### [Problema] Dica de tipo incorreta para o membro protegido $_urlHelper

O sistema agora Corrige a dica de tipo errado com a correta, que também é usada no construtor

_AC-10716 - [Problema do GitHub](https://github.com/magento/magento2/issues/32503) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32496)_

### Desempenho

#### [Problema] ao atualizar Store.php

Esta PR melhora o desempenho, ignorando a resolução de loja atual.

_AC-14791 - [Problema do GitHub](https://github.com/magento/magento2/issues/39949) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38717)_

### Preços

#### O preço é sempre 0 para itens de produto agrupados sem preço dinâmico na API rest de ordem

_AC-11925 - [Problema do GitHub](https://github.com/magento/magento2/issues/38687) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7da46f52)_

### Produto

#### Desconto percentual na regra de preço de camada e de catálogo calculado no preço original sem opções selecionadas.

_AC-12004 - [Problema do GitHub](https://github.com/magento/magento2/issues/38750)_

#### Quantidade de pedidos de produtos ausentes permitidos no Magento 2.4.7 min

O sistema está funcionando bem e a origem da página está mostrando corretamente a quantidade mínima do produto

_AC-12909 - [Problema do GitHub](https://github.com/magento/magento2/issues/39142) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39480)_

#### Exceção do Magento ao executar o teste Magento Payflow Pro

_AC-13681_

#### Problema com a grade de Opções personalizáveis na página do produto no painel de administração

O sistema está funcionando como esperado quando estamos criando opções personalizáveis com a lista suspensa de tipos

_AC-14003 - [Problema do GitHub](https://github.com/magento/magento2/issues/39640) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39694)_

#### A Opção De Impressão Da Página De Lista De Requisições Não Está Funcionando

_AC-14711_

#### Todos os itens das listas de comparação de outros clientes são atribuídos ao cliente depois de fazer logon por meio do administrador

Anteriormente, quando um administrador usava o recurso &quot;Fazer logon como cliente&quot; no back-end, os produtos da lista de comparação de um cliente conectado anteriormente eram atribuídos incorretamente ao cliente representado no momento.  Depois da correção, a lista de comparação é carregada corretamente para o cliente conectado corretamente.

_ACP2E-3818 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### Atualizar a url_key do produto por meio da API REST não gera uma Reescrita de URL 301

Ao atualizar a chave de URL do produto por meio da API REST, com a configuração &quot;Criar redirecionamento permanente para URLs se a chave de URL mudar&quot; definida como Sim, as substituições de URL do produto serão criadas para redirecionar do URL antigo para um novo.

_ACP2E-3900 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Vendas

#### O estado do pedido desaparece ao selecionar o valor na lista suspensa Estado do pedido

_AC-15010_

### Segurança

#### JS agrupado/mesclado que não faz parte dos hashes da SRI

Antes da correção, os arquivos gerados ou mesclados não eram adicionados à lista de hashes SRI. Agora, os arquivos estão sendo adicionados corretamente aos hashes SRI.

_ACP2E-3854 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Envio

#### [QUANS] - O módulo principal Magento_Fedex verifica se há um token ativo válido antes de enviar uma solicitação para obter um novo?

A Adobe Commerce não faz mais muitas solicitações ao serviço de API FedEx para o token de acesso. Anteriormente, mesmo que o token de acesso ainda seja válido, o Adobe Commerce sempre faz novas solicitações à API FedEx, o que causou um problema de limitação de taxa.

_ACP2E-3930 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Preparo e visualização

#### Não é possível visualizar a Atualização de produto agendada com as Permissões de categoria ativadas

Antes da correção, um futuro produto a ser ativado não era exibido no modo de visualização. Agora ele será exibido mesmo se o status atual estiver desativado.

_ACP2E-3786 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### O escopo está mostrando diferentes modos de exibição de armazenamento durante a Visualização

Antes da correção, uma visualização de atualização de preparo do bloco de cms e do conteúdo da página de cms pode ter sido aberta em um armazenamento diferente do armazenamento atribuído no bloco ou na página de cms quando acessado do Painel de preparo de conteúdo. Após a correção, se o bloco ou a página cms tiver apenas um armazenamento específico atribuído na atualização de preparo, a visualização no Painel de preparo de conteúdo será aberta com o armazenamento correto selecionado.

_ACP2E-3815_

#### Validação ausente para o campo de valor de desconto da regra de Preço de Catálogo

Anteriormente, o campo discount_amount na atualização da programação de preparo não era validado corretamente com as regras de validação atuais. No entanto, após a aplicação da correção, o campo discount_amount será validado adequadamente.

_ACP2E-3867 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Imposto

#### Total da ordem errada, a rodada não é aplicada ao cálculo de preço.

O sistema agora é manipulado corretamente ao calcular o price_after_discount, o discount_amount e o valor dos impostos.
o total real do pedido

_AC-11389 - [Problema do GitHub](https://github.com/magento/magento2/issues/38455) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39687)_

### Estrutura de teste

#### [Problema] Ignore lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

O sistema agora ignora o arquivo &#39;env.php&#39; que é gerado ao executar testes de unidade, garantindo que o status do Git permaneça limpo após a execução dos testes. Anteriormente, a execução de testes de unidade gerava um novo arquivo &quot;env.php&quot;, fazendo com que o status do Git mostrasse um novo arquivo encontrado e o sujasse.

_AC-13293 - [Problema do GitHub](https://github.com/magento/magento2/issues/39304) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problema] Corrigir problema de teste de integração com o interceptor

O sistema agora identifica e lida corretamente com o \Magento\TestFramework\App\Config\Interceptor no teste de integração, garantindo que o teste possa acessar os dados necessários mesmo quando existir um plug-in na classe. Anteriormente, o sistema não levava em conta a possibilidade de o \Magento\TestFramework\App\Config ser um \Magento\TestFramework\App\Config\Interceptor, resultando em um erro ao tentar acessar a propriedade $data.

_AC-13305 - [Problema do GitHub](https://github.com/magento/magento2/issues/39324) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problema] MFTF: Enviando Email para Formulário Amigo com captcha habilitado

O caso de teste aborda a funcionalidade do formulário &quot;Enviar email para um amigo&quot; quando o CAPTCHA está ativado, garantindo que o processo de envio do formulário funcione corretamente com valores CAPTCHA incorretos e corretos.

_AC-13492 - [Problema do GitHub](https://github.com/magento/magento2/issues/39462) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] Usos de TestCase::getTestResultObject são inválidos desde phpunit v10

_AC-13502 - [Problema do GitHub](https://github.com/magento/magento2/issues/39463)_

#### Falhas nos testes de unidade específicos do ambiente em AC 2.4.7-p3

Esse problema corrige falhas de teste de unidade que não estão se reproduzindo em todas as versões e ambientes. Antes da correção, alguns testes de unidade falhavam devido a diferentes versões de biblioteca ou devido à falta de funcionalidade adicionada em uma versão posterior.

_ACP2E-3712 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

### Ferramentas/ FerramentaDeMigraçãoDeDados

#### [ATLH] Erro fatal quando não há diferenças

O erro fatal não aparece mais quando não há diferença para mostrar

_ACP2E-3901_

### Estrutura da interface

#### O WYSIWYG está vazio em linhas dinâmicas

_AC-12336 - [Problema do GitHub](https://github.com/magento/magento2/issues/38893) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problema] Corrigir erro de tipo MIME

O sistema manipula e corrigiu corretamente o tipo MIME e o erro de digitação da imagem gif

_AC-8001 - [Problema do GitHub](https://github.com/magento/magento2/issues/36899) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problema] Evite acesso direto à lista de revisões do Ajax

O sistema manipula corretamente e Evita acesso direto à lista de revisões do Ajax

_AC-9381 - [Problema do GitHub](https://github.com/magento/magento2/issues/37920) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33876)_

### Atualizações - Ferramenta de compatibilidade de atualização

#### Funcionalidade obsoleta: criação de propriedade dinâmica Magento\Framework\Acl::$_roleRegistry

_AC-12343 - [Problema do GitHub](https://github.com/magento/magento2/issues/37469)_
