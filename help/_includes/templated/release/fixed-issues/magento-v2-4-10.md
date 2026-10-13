---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '9924'
ht-degree: 0%
---
# Correção de problemas do Magento Open Source (v2.4.10-alpha1)

## Correção de problemas na v2.4.10-alpha1

Corrigimos 152 problemas no código principal Magento Open Source 2.4.10-alpha1. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

#### [Problema] TypeError em Creditmemo\Validation\QuantityValidator causado por min() com a quantidade da cadeia de caracteres

Para estabilizar os pipelines de log financeiro e evitar falhas de solicitação de API durante reembolsos automatizados de pedidos em massa, foram adicionadas medidas de proteção de projeção de tipo de dados às camadas internas de fábrica e validação do memorando de crédito de vendas.

_AC-16056 - [Problema do GitHub](https://github.com/magento/magento2/issues/40302) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40429) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40303)_

#### Falha na atualização de atributo REST API sem attribute_id

Correção de um problema em que a atualização de um atributo de produto existente por meio da API REST falhava quando attribute_id não era fornecido. A API agora identifica corretamente o atributo usando o attribute_code do URL e o atualiza com sucesso.

_AC-16424 - [Problema do GitHub](https://github.com/magento/magento2/issues/40458) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### O Visual Swatch é excluído ao atualizar a opção por meio da API REST

Para proteger a integridade dos dados do catálogo e simplificar integrações automatizadas, um erro foi resolvido na camada de gerenciamento Amostra EAV, onde os valores de amostra visuais ou textuais existentes eram inadvertidamente eliminados durante atualizações de opção padrão.

_AC-9199 - [Problema do GitHub](https://github.com/magento/magento2/issues/37794) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40872)_

#### A API de preço de nível em massa falha em todo o lote quando um SKU está ausente

Anteriormente, a API de atualização de preço de nível em massa (POST /V1/products/tier-price) falhava em toda a solicitação quando não existia qualquer SKU na carga, deixando SKUs válidas sem atualizações. Agora, SKUs válidas são processadas com êxito enquanto SKUs ausentes são relatadas como erros por item, portanto, uma única entrada incorreta não anula mais o lote inteiro.

_ACP2E-4998 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### A atualização de atributo falha com o valor do rótulo correspondente à ID de valor de opção existente

Correção do problema em que uma nova opção de atributo de produto suspenso/de seleção múltipla não podia ser criada por meio da API REST quando o rótulo correspondia à ID de uma opção existente. Anteriormente, a API retornava um erro &quot;já existe&quot; (e podia retornar a ID de opção errada), mesmo que a mesma opção pudesse ser criada com êxito por meio da interface do usuário do administrador.

_ACP2E-5107 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### APIs, Importação e exportação

#### A API REST permite preços de produtos negativos enquanto a interface do usuário do administrador os bloqueia

A importação de produtos por meio do endpoint da API REST agora rejeita valores negativos para atributos de tipo de preço (preço, special_price, custo e campos MSRP relacionados), consistente com o comportamento da importação da interface do administrador. Anteriormente, a API aceitava preços negativos silenciosamente e os mantinha.

_ACP2E-4941 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### APIs, Ordem

#### O recurso Limite de taxa de pedido é incompatível com o back-end do cache Valkey

Antes, essa limitação de taxa de correção era ignorada silenciosamente e cada solicitação era permitida, independentemente do limite configurado. Após a correção, as solicitações que excedem o limite configurado são rejeitadas corretamente com HTTP 429.

_ACP2E-4899 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Conta

#### Correção de [Problema]: rótulo de senha incorreto do formulário de logon

Correção de um problema em que o campo Senha na página de logon do cliente tinha uma associação de rótulo incorreta. O rótulo da senha agora é direcionado corretamente para o campo Senha, permitindo que seja identificado corretamente pelas ferramentas de teste automatizado.

_AC-16193 - [Problema do GitHub](https://github.com/magento/magento2/issues/40353) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### [Problema] Validar tipo de entrada de front-end para carregamentos de arquivos

Os uploads de arquivo de endereço do cliente agora validam se o tipo de entrada do atributo de destino é arquivo ou imagem antes do processamento, portanto, o texto e outros atributos que não são de arquivo não podem ser usados como destinos de upload. Tentativas de upload inválidas retornam um erro de validação claro em vez de falhar de forma imprevisível ou aceitar tipos de arquivos não permitidos.

_AC-17076 - [Problema do GitHub](https://github.com/magento/magento2/issues/40795) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40583)_

#### O token do cliente gerado no site A pode ser usado no site B na configuração do cliente com escopo de site

Para aplicar o isolamento rigoroso de dados do cliente em instâncias de vários sites, uma lacuna de segurança foi resolvida na camada de autenticação do GraphQL, onde os tokens eram validados incorretamente entre limites separados.

_AC-17299 - [Problema do GitHub](https://github.com/magento/magento2/issues/40847) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40858)_

#### [Problema] Corrigir a descontinuação do PHP 8.5: usar null como parâmetro de chave para array_key_exists()

Correção de um problema no PHP 8.5 em que o login do cliente durante o checkout do convidado falhava devido a uma chamada array_key_exists() descontinuada com uma chave nula. O logon do cliente agora funciona com êxito sem gerar o erro de desativação.

_AC-17395 - [Problema do GitHub](https://github.com/magento/magento2/issues/40875) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problema] magento/magento2: adicionar traduções i18 para requestPasswordResetEmail e resetPassword GraphQL mutations

Para garantir uma experiência de loja headless totalmente localizada, os recursos de internacionalização (i18n) foram adicionados aos endpoints da API de recuperação de conta do cliente

_AC-9356 - [Problema do GitHub](https://github.com/magento/magento2/issues/29658) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/28950)_

### Interface do administrador

#### O painel deve mostrar Últimos 7 dias por padrão quando os dados agregados são usados

Correção de um problema em que o Painel mostrava Hoje por padrão quando os dados de vendas agregados eram ativados. O Painel agora mostra Últimos 7 dias por padrão ao usar dados agregados.

_AC-13799 - [Problema do GitHub](https://github.com/magento/magento2/issues/28152) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Os valores de FPT na página do carrinho e na página do produto são diferentes para as mesmas configurações de um produto simples

Correção de um problema em que os valores de Imposto Fixo sobre Produtos (FPT) eram exibidos de forma diferente nas páginas do produto e do carrinho para a mesma configuração de imposto. Os valores de FPT agora são exibidos de forma consistente nas páginas do produto, catálogo, minicarrinho e carrinho de compras.

_AC-17007 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Implementação de configuração lenta

Otimização do desempenho que melhora o desempenho do carregamento da configuração, resolvendo com lentidão os dados de configuração do sistema com escopo, preservando o comportamento existente da configuração.

_ACP2E-4751 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/65f660bd)_

#### Editor HugeRTE bloqueia emojis - falha na validação de javascript

Correção do problema em que o HugeRTE bloqueava o salvamento de conteúdo contendo emojis utf8mb4 (por exemplo, 🔵⚪🔴) ao editar dentro dos modais de tipo de conteúdo do PageBuilder (Texto, Banner, Slide). Anteriormente, a configuração de validação wysiwyg para esses formulários modais resolvia de `allowUtf8mb4` a `false`, fazendo com que o editor rejeitasse caracteres UTF-8 de 4 bytes mesmo em instalações onde o banco de dados suporta totalmente utf8mb4.

_ACP2E-4822 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### O administrador é desconectado ao visualizar clientes com catálogos de endereços grandes na página de edição do cliente no Painel de administração

Correção de um problema em que o Administrador era desconectado ao visualizar clientes com catálogos de endereços grandes na página de edição do cliente no Painel de administração

_ACP2E-4875 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Os pedidos não aparecem na Grade de Vendas

Correção de um problema em que novos pedidos eram atrasados na exibição nas grades de vendas quando a indexação de grade assíncrona era ativada, devido à redefinição do cursor de reconciliação depois de atingir a entidade mais recente. Novas entradas agora aparecem na grade na próxima execução do cron.

_ACP2E-4893 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

### Interface do administrador, Ordem

#### Preço incorreto mostrado para produto agrupado em Admin Create Order quando dois produtos agrupados compartilham o mesmo produto simples

Correção de um problema em que o preço de um produto agrupado em Admin Create Order era calculado incorretamente quando dois produtos agrupados que compartilhavam o mesmo produto simples eram configurados sem serem adicionados ao carrinho.

_ACP2E-4965 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### Interface do administrador, Estrutura da interface

#### O Magento2 redireciona para a página inicial em vez de mostrar o erro com a declaração de menu errada

Para otimizar o fluxo de trabalho de desenvolvimento de extensão e garantir o carregamento estável do back-end, um defeito de roteamento estrutural foi resolvido, em que declarações de menu de administrador inválidas acionavam falhas silenciosas de loop do navegador em vez de exibir mensagens de diagnóstico acionáveis.

_AC-7543 - [Problema do GitHub](https://github.com/magento/magento2/issues/36632) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40881)_

### Analytics/Relatórios

#### [QUANS] É possível exibir a ID e o nome do email do cliente na Tabela de KPI do cliente em Relatórios avançados

O Adobe Commerce agora inclui o nome, o nome do meio e o sobrenome do cliente nos dados exportados para Relatórios avançados, permitindo que a Tabela de KPI do cliente exiba o nome do cliente. Anteriormente, somente um identificador de cliente codificado era exportado, portanto, os comerciantes não podiam identificar clientes por nome nos Relatórios avançados.

_ACP2E-3928 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### Inserção pesada em sales_bestsellers_aggregated_month

Desempenho aprimorado para aggregate_sales_report_bestsellers_data cron.

_ACP2E-4559 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### A carga útil do evento Adicionar ao carrinho está no formato herdado de comércio eletrônico aprimorado do Universal Analytics, em vez do formato de comércio eletrônico GA4.

Antes da correção, os eventos de comércio eletrônico enviados para o Google Analytics 4 por meio do Google Tag Manager usavam o formato herdado do Universal Analytics e não tinham vários eventos de check-out. Após a correção, todos os eventos de comércio eletrônico usam o formato GA4 correto e o funnel de check-out completo é rastreado.

_ACP2E-5176 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/24667df1)_

### B2B, Ordem

#### Ajuda para limpar tabelas de cotações de mais de 59 milhões (sales_clean_quotes não pode ser executado)

Correção do problema em que o trabalho cron `sales_clean_quotes` expirava em instâncias com tabelas de aspas grandes. Anteriormente, a consulta de limpeza selecionava todas as colunas da tabela `negotiable_quote` desnecessariamente, fazendo com que o MySQL executasse uma classificação de arquivos completa em milhões de linhas; e cada aspas era excluída individualmente através da camada de modelo PHP, aumentando o custo de desempenho.

_ACP2E-4891 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

### Carrinho e saída

#### Notificação de Adicionar ao carrinho para produtos relacionados

Correção de um problema em que a notificação Adicionar ao carrinho não incluía o produto relacionado ao adicionar um produto e seu produto relacionado juntos.
A notificação agora exibe os nomes de ambos os produtos adicionados ao carrinho.

_AC-11976 - [Problema do GitHub](https://github.com/magento/magento2/issues/27164) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problema] Atualizar CartRepositoryInterface.php

Atualização de CartRepositoryInterface.php para declarar as exceções que podem ser lançadas ao salvar um carrinho. Isso mantém a interface consistente com a implementação subjacente de salvamento do carrinho.

_AC-13323 - [Problema do GitHub](https://github.com/magento/magento2/issues/39328) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### O campo da empresa [Bug] no endereço para entrega está definido como nulo na configuração de várias lojas ao adicionar um novo endereço durante a etapa de envio do check-out

Correção de um problema em que o campo Empresa não era salvo quando os clientes adicionavam um novo endereço de entrega durante o check-out em uma configuração de várias lojas. O valor da Empresa agora é salvo corretamente na cotação, no pedido feito e no catálogo de endereços do cliente.

_AC-13456 - [Problema do GitHub](https://github.com/magento/magento2/issues/39424) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### Paypal > Incompatibilidade de dados do cliente (prefixo, nome, sobrenome)

Correção de um problema em que os detalhes do nome do cliente eram mapeados incorretamente durante o fluxo de finalização SEPA do PayPal. Prefixo, nome e sobrenome agora são preenchidos corretamente na ordem sem incompatibilidade.

_AC-15366 - [Problema do GitHub](https://github.com/magento/magento2/issues/39061) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Sinalizador de frete_gratuito incorreto para produtos virtuais

Correção de um problema em que o sinalizador free_shipping era definido incorretamente para produtos virtuais quando vários itens eram adicionados ao carrinho. O sinalizador agora está corretamente definido para todos os itens quando a regra de frete gratuito aplicável é aplicada.

_AC-15648 - [Problema do GitHub](https://github.com/magento/magento2/issues/40184) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Guest add-to-cart: minicarrinho/seção &quot;carrinho&quot; de dados do cliente subinforma o carrinho como vazio, apesar de o item ser mantido corretamente

Correção de um problema em que o minicarrinho de convidado não refletia itens imediatamente após adicionar um produto ao carrinho. O contador e a lista suspensa do minicarrinho agora são atualizados corretamente e os produtos adicionados são exibidos no carrinho, conforme esperado.

_AC-17973 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### Mensagens de erro em linha do complemento ao carrinho do AJAX perdidas da semântica de função=&quot;alerta&quot;

Correção de um problema em que as mensagens de erro de suplementos ao carrinho do AJAX estavam visíveis na loja, mas não eram anunciadas por leitores de tela. Os erros de adição ao carrinho agora são exibidos em uma região acessível role=&quot;alert&quot; para suporte de acessibilidade adequado.

_AC-18036 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### Descartar regras subsequentes para valor de remessa

Para garantir preços promocionais precisos e conformidade estrita com as regras de desconto configuradas, uma falha na calculadora de regras de preço do carrinho de compras foi resolvida, onde descontos de envio de prioridade mais baixa foram aplicados incorretamente

_AC-9612 - [Problema do GitHub](https://github.com/magento/magento2/issues/37985) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40869)_

#### Pedidos duplicados criados mesmo que o erro seja disparado

Correção de um problema em que os pedidos ainda podiam ser feitos com um endereço de cliente inválido

_ACP2E-4774 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Impacto do produto configurável no desempenho na finalização da compra (totais-informações, estimativa-módulos de envio)

Antes da correção, as solicitações de finalização da compra, como informações de totais e métodos de envio de estimativa, poderiam se tornar significativamente mais lentas para produtos configuráveis com muitos produtos secundários quando o primeiro secundário comercializável aparecesse tardiamente na lista de secundários. Após a correção, essa degradação de desempenho não ocorrerá mais e os tempos de resposta permanecerão consistentes, independentemente da posição do primeiro filho escalável.

_ACP2E-4805 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Totais do carrinho recalculados em cada exibição de página do carrinho

Solicitações de totais de carrinho otimizadas na página do carrinho. Os totais do carrinho foram recalculados duas vezes em cada exibição de página do carrinho.

_ACP2E-4817 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### As regras de validação Cidade e Rua do Atributo de Endereço do Cliente (EAV) estão em conflito com as regras de validação codificadas.

Correção de um problema em que o validador cidade rejeitava incorretamente nomes de cidade válidos com mais de 100 caracteres (o limite do banco de dados é 255) e em que endereços de rua com mais de 255 caracteres podiam ser truncados silenciosamente no banco de dados sem\
erro de validação. Ambos os validadores agora impõem limites alinhados com a restrição de coluna de banco de dados mais estreita em todas as tabelas de endereços.

_ACP2E-4861 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Vitrine] A mensagem &quot;a quantidade solicitada não está disponível&quot; do suplemento ao carrinho intermitentemente não é renderizada no PDP

Correção do problema em que a mensagem de indisponibilidade de estoque (&quot;A quantidade solicitada não está disponível, reduza a quantidade&quot;). O não era exibido intermitentemente na página de detalhes do produto após uma tentativa mal-sucedida de Adicionar ao carrinho. Anteriormente, a página podia ser atualizada silenciosamente sem feedback de erro quando um comprador clicava repetidamente em Adicionar ao carrinho para um produto cujo estoque disponível já estava totalmente reservado no carrinho.

_ACP2E-5071 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### O carrinho de compras persistente é limpo na expiração natural da sessão quando a opção Limpar persistência no logoff = Sim

Correção do problema em que o carrinho de compras persistentes era limpo quando a sessão do navegador expirava. Anteriormente, com a opção Limpar persistência no logout ativada, uma sessão expirada esvaziava o carrinho e removia o cookie persistente, mesmo que o comprador não tivesse feito logout.

_ACP2E-5088 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### A cotação de convidado customer_email não é ressincronizada do endereço de cobrança após restoreQuote() ao tentar o check-out novamente

Correção de um problema em que tentar novamente um check-out de convidado com falha fazia o pedido com o email inserido anteriormente em vez do atualizado.

_ACP2E-5188 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Carrinho e check-out, GraphQL

#### A API da GraphQL de cotação pode atribuir objetos de moeda em vez de códigos de moeda ISO a campos de cotação

Atualização da API do Quote GraphQL para atribuir códigos de moeda ISO a campos de moeda de cotação e armazenamento, em vez de atribuir objetos de moeda.

_ACP2E-5229 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catálogo

#### [Problema] melhorias no arquivo module.xml para os módulos Magento_ConfigurableProductGraphQl, Magento_MsrpConfigurableProduct, Magento_NewRelicReporting e Magento_Swatches.

Otimização da arquitetura de declaração do módulo, removendo dependências redundantes do Magento_Catalog de quatro submódulos principais. Essa limpeza aborda duplicações desnecessárias na árvore de dependência, simplifica os cálculos de ordem de carregamento do módulo e melhora a capacidade de manutenção da estrutura de longo prazo sem introduzir alterações quebradas.

_AC-10762 - [Problema do GitHub](https://github.com/magento/magento2/issues/30675) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/30638)_

#### Possível vazamento de memória na função getUsedProducts para configuráveis

Correção de um problema em que o processamento de vários produtos configuráveis fazia com que o tempo de execução e o uso de memória aumentassem ao longo do tempo.
Os produtos configuráveis agora podem ser processados sem a lentidão progressiva e o aumento de memória.

_AC-10942 - [Problema do GitHub](https://github.com/magento/magento2/issues/37639) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/8c058c2e)_

#### Filtro Comprar por categoria visível em categorias que não são de âncora

Correção de um problema em que o filtro Comprar por categoria era exibido em categorias que não eram de âncora mesmo quando o filtro de categoria estava desativado no Administrador.
O filtro agora está oculto na loja de acordo com a configuração definida.

_AC-10945 - [Problema do GitHub](https://github.com/magento/magento2/issues/38379) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### O Tipo de dados de apply_rule_ids no Item de Cotação e Cotação é diferente

Para garantir a consistência absoluta do esquema do banco de dados e evitar incompatibilidades críticas de dados do carrinho em lojas promocionais de alto volume, o rastreamento da coluna de dados das definições promocionais ativas foi expandido pelas estruturas de check-out principais.

_AC-14518 - [Problema do GitHub](https://github.com/magento/magento2/issues/39838) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40540)_

#### Não é possível obter o atributo `decimal` do escopo da coleção de produtos se o preço for do escopo global

Para garantir preços precisos da loja e renderização de atributos em configurações internacionais, um erro de coleta de dados principal foi resolvido, onde valores decimais específicos da loja foram substituídos incorretamente por valores globais padrão.

_AC-15806 - [Problema do GitHub](https://github.com/magento/magento2/issues/40218) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40419)_

#### Tratamento incorreto dos parâmetros GET

Para melhorar a estabilidade da plataforma e proteger o funnel de check-out, uma camada de validação de entrada em nível de bloco foi adicionada para impedir que consultas de URL malformadas travem as páginas de produto da loja.

_AC-16262 - [Problema do GitHub](https://github.com/magento/magento2/issues/40405) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes::afterGetProductAttributes sendo acionados em todas as consultas do carrinho

Para reduzir as tensões de execução do banco de dados e eliminar ocorrências de banco de dados não otimizadas durante os check-outs do cliente, o plug-in de configuração do produto da regra de vendas foi otimizado para ser executado condicionalmente e aproveitar as estruturas de cache.

_AC-16559 - [Problema do GitHub](https://github.com/magento/magento2/issues/40226) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40251)_

#### [Problema] [PHPDOC] Corrigir funções orderComment em Magento\Sales\Model\Order

Para eliminar restrições rígidas de digitação, melhorar a precisão da análise estática e melhorar a experiência do desenvolvedor com mecanismos de listas rigorosos como o PHPStan (Nível 5 ou superior), os blocos de documentação estrutural em linha foram padronizados nos subsistemas principais de ordens de venda.

_AC-16759 - [Problema do GitHub](https://github.com/magento/magento2/issues/39575) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39572)_

#### [Problema] [Bug] GraphQL SearchCriteriaValidator não carregado — removido por substituição de matriz module-graph-ql di.xml

Para preservar a validação de consulta robusta e aplicar medidas de proteção da plataforma, um defeito de configuração de injeção de dependência (ID) foi resolvido, em que a camada SearchCriteriaValidator estava sendo desabilitada inadvertidamente.

_AC-16959 - [Problema do GitHub](https://github.com/magento/magento2/issues/40762) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40742)_

#### strpos() espera que o parâmetro 1 seja uma string, matriz fornecida | magento/module-eav

Para proteger a estabilidade da loja e fornecer uma experiência ininterrupta de detecção de clientes, um defeito crítico de incompatibilidade de tipo foi resolvido nos mecanismos de processamento avançados de pesquisa de catálogos.

_AC-1706 - [Problema do GitHub](https://github.com/magento/magento2/issues/33588) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40422)_

#### Registros de cotação vazios estão sendo criados quando o cliente visita uma página

Visitar a página do produto na loja não cria registros de cotação vazios em algumas situações.
Anteriormente, registros de cotação vazios eram criados quando o cliente visitava uma página de produto na loja

_ACP2E-4682 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### O atributo &quot;Peso&quot; da página de detalhes do produto não mostra o sufixo da unidade na seção &quot;Informações adicionais&quot;

Corrige o problema em que o atributo Weight na página de produto Storefront exibia apenas um valor numérico bruto na seção &quot;Additional Information&quot; ou &quot;More Information&quot; sem a unidade de medida configurada (lb ou kgs).

_ACP2E-4808 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Ativação da regra de preço de catálogo da &lbrace;Cloud] não refletida no Live Search até a próxima ressincronização forçada — atraso de sincronização do feed de preço

Correção de um problema em que a ativação de uma regra de preço de catálogo não atualizava os preços no Live Search até uma ressincronização forçada posterior. O indexador de feed de preço poderia ser executado antes do indexador de regra de catálogo do qual dependia ter terminado e, portanto, exportou preços obsoletos. Os indexadores com dependências não concluídas agora são adiados para a próxima execução de cron, portanto, o feed de preço sempre é executado com preços atualizados.

_ACP2E-5029 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### O texto alternativo (rótulo) não é salvo para uma imagem de produto recém-adicionada

Correção de um problema em que o texto alternativo (rótulo) de uma imagem de produto recém-carregada não era salvo quando o arquivo carregado era renomeado ao ser salvo devido a uma colisão de nome de arquivo na galeria de mídia. Anteriormente, os atributos de função da imagem (imagem, small_image, miniatura) eram armazenados corretamente, mas seus atributos *_label correspondentes eram descartados silenciosamente, deixando o texto alternativo vazio nas páginas de pesquisa e listagem da loja. O manipulador de criação da galeria agora resolve o arquivo renomeado de volta para sua entrada de imagem de origem, de modo que o rótulo é mantido para todas as funções de imagem atribuídas. Como resultado, o texto alternativo inserido durante a criação do produto é salvo e renderizado de maneira confiável na loja.

_ACP2E-5216 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/24667df1)_

#### Descontinuação do PHP 8.5 &quot;null como array offset&quot; erro ao abrir a página Adicionar produto no administrador quando o usuário não tem o recurso Editar status do produto

Anteriormente, usuários administradores sem a permissão &quot;Editar status do produto&quot; podiam encontrar um erro de descontinuação &quot;nulo como deslocamento de matriz&quot; ao abrir a página Adicionar produto. Isso foi corrigido para que a página seja carregada corretamente, independentemente das permissões de status do produto do usuário.

_ACP2E-5248 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catálogo, GraphQL

#### Problemas de filtro de preço de consulta de produtos [GraphQl] com preços líquidos inseridos em adminhtml

Correção de um problema em que a consulta de produtos do GraphQL não considerava impostos ao aplicar um filtro de preço.
O filtro de preço agora usa o preço com imposto incluído exibido, para que somente os produtos dentro da faixa de preços especificada sejam retornados.

_AC-6883 - [Problema do GitHub](https://github.com/magento/magento2/issues/36337) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

### Catálogo, SEO

#### Categoria url_path não está sincronizando na alteração de url_key para todas as exibições de loja

Anteriormente, alterar a chave de URL de uma categoria no escopo &quot;Todas as exibições de loja&quot; poderia deixar categorias descendentes no escopo da loja com um url_path obsoleto ou com prefixo incorreto, e editar uma categoria com sua própria substituição de url_path específica da loja poderia escolher sua chave de URL de pré-edição em vez da recém-inserida. Isso agora é corrigido — As alterações na chave de URL são corretamente aplicadas em cascata a todos os descendentes com escopo de armazenamento na ordem hierárquica correta com o caminho principal correto, e a substituição de url_path com escopo de armazenamento de uma categoria é recalculada usando sua chave de URL recém-alterada, de modo que os URLs com escopo de armazenamento permanecem precisos imediatamente após o salvamento.

_ACP2E-5113 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Nuvem, Estrutura

#### Regressão de desempenho e armazenamento de cache incorreto com o SymfonyL2 ativado

Correção de um problema em que a configuração do caminho de armazenamento em cache L1 como um caminho absoluto (por exemplo, /dev/shm) fazia com que ele fosse redirecionado silenciosamente para o diretório var/ e um problema de desempenho separado em que a invalidação de tags de cache em catálogos grandes poderia causar atrasos significativos no tempo de resposta devido a uma operação Redis de bloqueio.

_ACP2E-4989 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Conteúdo

#### A solicitação de visualização ajax do Page Builder retorna o erro 500 com o cache de tradução desativado

A pré-visualização do PageBuilder agora é renderizada corretamente, independentemente do cache de Traduções estar ativado ou desativado. Anteriormente, a pré-visualização do PageBuilder não era renderizada quando o cache de traduções estava desativado.

_ACP2E-5118 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### Os uploads animados do GIF são convertidos em PNG quando a opção Habilitar galeria de mídia antiga está habilitada

Correção de um problema em que imagens animadas do GIF carregadas por meio da galeria de mídia eram convertidas em PNG quando a galeria de mídia herdada era ativada. Anteriormente, quando a opção Ativar redimensionamento de front-end estava ativada, os GIFs animados carregados por meio da Galeria de mídia antiga perdiam as animações e eram salvos como arquivos PNG estáticos. Agora, os GIFs animados são carregados e armazenados em seu formato original.

_ACP2E-5232 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Conteúdo / CMS

#### [Problema] Corrija a guia da galeria de produtos quando um rótulo de atributo de imagem contiver aspas simples

Para garantir uma experiência confiável e ininterrupta de gerenciamento de catálogos no painel de administração, foi resolvido um defeito de formatação do JavaScript que rompeu completamente a interface do espaço de trabalho do produto de back-end

_AC-16474 - [Problema do GitHub](https://github.com/magento/magento2/issues/40519) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40870)_

#### [Problema] Melhore o desempenho quando a URL de imagem redimensionada é acessada, mas ainda não existe.

Para maximizar a capacidade de resposta da entrega de ativos, reduzir significativamente a E/S de disco do servidor e evitar picos graves do processador do servidor, o subsistema de geração de imagens do catálogo foi otimizado para lidar com URLs de mídia ausentes estritamente sob demanda.

_AC-16547 - [Problema do GitHub](https://github.com/magento/magento2/issues/40399) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40388)_

#### Regressão: o componente URI codificado não UTF-8 ainda lança &quot;Não é possível serializar o valor&quot; no CatalogWidget no 2.4.7-p5

Para eliminar falhas críticas de renderização causadas por tráfego ruim na Web de produção, o bloco de widget de catálogo foi fortificado para lidar com sequências de dados não UTF-8 dentro dos URLs solicitados.

_AC-17264 - [Problema do GitHub](https://github.com/magento/magento2/issues/40824) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40825)_

#### `Using null as an array offset is deprecated, use an empty string instead` ao editar o escopo de configuração de design global

Correção de um problema em que a edição do escopo Global em Content > Design > Configuration retornava um erro HTTP 500 no PHP 8.5 devido a um deslocamento de matriz nula obsoleta. A configuração de design global agora é aberta com êxito sem o erro.

_AC-17456 - [Problema do GitHub](https://github.com/magento/magento2/issues/40886) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Estrutura

#### SELECIONE de media_storage_file_storage quando o armazenamento de dados do banco de dados de mídia não estiver em uso ou desativado

Para reduzir a sobrecarga desnecessária de consulta do banco de dados e eliminar exceções ruidosas do sistema, a camada de sincronização de arquivos de mídia foi otimizada para ignorar as verificações de armazenamento do banco de dados quando o sistema está configurado explicitamente para usar o sistema de arquivos local

_AC-10586 - [Problema do GitHub](https://github.com/magento/magento2/issues/38116) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40480)_

#### Erro fatal lançado no construtor de exceção quando o repositório de cookies é uma matriz

Correção de um problema em que um valor de cookie de armazenamento inválido causava um erro fatal de PHP.
Agora, a Magento lança corretamente uma exceção de &quot;Parâmetro de armazenamento inválido&quot; quando o cookie de armazenamento contém um valor inválido.

_AC-10888 - [Problema do GitHub](https://github.com/magento/magento2/issues/38365) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [Problema] Use const estática em Magento\Customer\Model\Address\Config

Correção de um problema em que as classes de configuração de endereço personalizadas tinham que duplicar getFormats() para usar um caminho de modelo de endereço personalizado. As configurações de endereço personalizadas agora podem definir seu próprio caminho de modelo usando uma constante estática sem duplicar o método.

_AC-12906 - [Problema do GitHub](https://github.com/magento/magento2/issues/39135) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Não é possível usar processFilter na coleção do produto

Correção de um problema em que a aplicação de vários filtros a uma coleção de produtos usando o FilterProcessor causava um erro de PHP. Agora as coleções de produtos podem ser filtradas corretamente usando várias condições de filtro.

_AC-15018 - [Problema do GitHub](https://github.com/magento/magento2/issues/40014) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### Possível problema de desempenho do indexador para catálogos grandes - Inserção em massa e bloqueio da tabela de CL inteira para identificar a versão mais recente

Para proteger o desempenho do banco de dados em grandes catálogos de escala empresarial, o pipeline do indexador de banco de dados do sistema foi reforçado para analisar modificações de dados programadas em lotes limitados, eliminando bloqueios de banco de dados de alta pressão.

_AC-16238 - [Problema do GitHub](https://github.com/magento/magento2/issues/40331) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40546)_

#### [Problema]: melhoria de desempenho

Para eliminar alocação desnecessária de memória e reduzir a sobrecarga do processamento de tempo de execução, várias rotinas de manipulação de sequência de caracteres principais foram alteradas para utilizar o comportamento nativo otimizado do PHP.

_AC-16565 - [Problema do GitHub](https://github.com/magento/magento2/issues/40383) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40375)_

#### [Problema] Suporte a correções para GLOB_BRACE em sistemas Linux não-GNU

Para garantir a capacidade de implantação contínua em ambientes de virtualização leves, um erro crítico de descoberta de caminho foi corrigido para restaurar totalmente o suporte à execução para sistemas que utilizam bibliotecas não-GNU, como imagens do Alpine Linux Docker.

_AC-16568 - [Problema do GitHub](https://github.com/magento/magento2/issues/40552) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40538)_

#### Parâmetros de marketing adicionados novamente à consulta usados para a criação de identificador FPC integrado

Para melhorar as taxas de ocorrência do cache e eliminar regressões de desempenho do servidor, uma falha estrutural foi corrigida no sistema FPC (Cache de página completa) interno nativo, no qual os parâmetros de consulta de marketing e rastreamento eram reintroduzidos acidentalmente nas assinaturas do identificador de cache.

_AC-16583 - [Problema do GitHub](https://github.com/magento/magento2/issues/40350) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40349)_

#### Adicionar suporte para objetos simples com propriedades promovidas na comunicação da fila de mensagens

Para suportar práticas modernas de desenvolvimento de PHP e simplificar workflows de arquitetura assíncrona, o mecanismo de reflexão de estrutura foi aprimorado para processar nativamente objetos de transferência de dados (DTOs) utilizando propriedades de construtor públicas, promovidas e somente leitura.

_AC-16672 - [Problema do GitHub](https://github.com/magento/magento2/issues/36660) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40457)_

#### [Problema] Correção: a introspecção do tipo de coluna real ignora processadores sem assinatura/anuláveis, usa padrões

Para garantir um rastreamento preciso da configuração do sistema, um defeito de abstração do banco de dados foi resolvido, em que comandos de verificação de esquema declarativo relatam perpetuamente alterações de modificação pendentes para colunas DOUBLE UNSIGNED sem precisão explícita ou atributos de escala.

_AC-16758 - [Problema do GitHub](https://github.com/magento/magento2/issues/40646) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40582)_

#### [Recurso] Suporte ao estado &quot;desabilitado&quot; para opções de seleção individuais na configuração do administrador

Para aprimorar a flexibilidade do formulário de back-end e fornecer aos desenvolvedores controle de layout granular, o suporte no nível da estrutura foi introduzido para marcar tags de opção individuais como não selecionáveis dentro dos elementos de formulário.

_AC-16761 - [Problema do GitHub](https://github.com/magento/magento2/issues/40564) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40565)_

#### Desempenho ⚡: memorização ausente no StoreManager e sobrecarga do plug-in no módulo Store

Para reduzir drasticamente a sobrecarga de execução do CPU e minimizar a rotatividade desnecessária da memória do aplicativo, uma rotina de armazenamento em cache com valor crítico de configuração foi implementada para interceptar processos de verificação de armazenamento redundantes.

_AC-16838 - [Problema do GitHub](https://github.com/magento/magento2/issues/40706) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40732)_

#### [Correção de problema]: remover o caminho de código inativo openssl_free_key() no JwkFactory

Para limpar a dívida de tecnologia estrutural e alinhar as ferramentas de criptografia aos perfis de execução modernos, os ganchos herdados que liberam recursos foram removidos do back-end do utilitário Chave da Web JSON.

_AC-16958 - [Problema do GitHub](https://github.com/magento/magento2/issues/40761) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40688)_

#### [Problema] correção ortográfica do PHPDoc

Para manter altos padrões de qualidade de código e melhorar a precisão das dicas de código do ambiente de desenvolvimento integrado (IDE), as limpezas estruturais foram aplicadas às camadas de documentação de código em linha nos módulos principais da estrutura.

_AC-16960 - [Problema do GitHub](https://github.com/magento/magento2/issues/40763) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40745)_

#### [Problema] perf(di:compile): armazenamento em cache de instâncias RefletionClass em Type, Config/Reader e ClassReader

Para acelerar significativamente os tempos de compilação e maximizar a taxa de transferência de implantação da integração contínua (CI), o back-end do compilador de injeção de dependência interna (`setup:di:compile`) foi otimizado para eliminar ciclos de reflexão de PHP redundantes.

_AC-17077 - [Problema do GitHub](https://github.com/magento/magento2/issues/40796) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40615)_

#### [Problema] Atualize o Filter.php para permitir `{{block template="Magento_Module::path/to/template.phtml"}}` e configurar \Magento\Framework\View\Element\Template como classe padrão

Para simplificar a criação de conteúdo e alinhar as diretivas CMS com os padrões de layout do modelo, o sistema de processamento de tags de marcação principal foi aprimorado para oferecer suporte a declarações de bloco sem uma definição de classe explícita.

_AC-17078 - [Problema do GitHub](https://github.com/magento/magento2/issues/38477) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38469)_

#### [Problema] perf(di:compile): memorizar leituras de escopo da Configuração de Interceptação durante a compilação

Para acelerar drasticamente as implantações do site e a compilação automatizada de back-end, o compilador de injeção de dependência (`setup:di:compile`) foi otimizado para eliminar operações de análise XML redundantes.

_AC-17313 - [Problema do GitHub](https://github.com/magento/magento2/issues/40852) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40614)_

#### Atualização do underscore.js para 1.13.8 para evitar vulnerabilidade de segurança

A biblioteca Underscore.js agrupada (lib/web/underscore.js) foi atualizada da versão 1.13.7 para a 1.13.8. Nenhuma alteração na configuração é necessária.

_AC-17349 - [Problema do GitHub](https://github.com/magento/magento2/issues/40857) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/12d0be1e)_

#### o magento-composer-installer deixa silenciosamente a configuração/ (e outros dirs mapeados) despreenchida quando um destino de implantação é um link simbólico

Correção de um problema em que o magento-composer-installer poderia silenciosamente falhar ao preencher setup/ e outros diretórios mapeados pelo Composer quando o destino de implantação era configurado como um link simbólico. Isso pode resultar em arquivos ausentes e uma implantação incompleta do Commerce.

_AC-17360 - [Problema do GitHub](https://github.com/magento/magento2/issues/40864)_

#### As chaves de pré-carregamento de cache não precisam mais do prefixo de ID ao usar o adaptador de cache do Symfony

As chaves de pré-carregamento (preload_keys) para o adaptador do Symfony Cache agora podem ser configuradas sem o id_prefix do cache. Anteriormente, seguindo a configuração documentada e incluindo o prefixo em cada chave (por exemplo, 061_SYSTEM_DEFAULT) fazia com que as chaves não fossem pré-carregadas. Agora é possível especificar as chaves exatamente como o aplicativo as solicita (por exemplo, SYSTEM_DEFAULT), e o Adobe Commerce aplica o id_prefix automaticamente.

_AC-17407 - [Problema do GitHub](https://github.com/magento/magento2/issues/40877) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3a6b9667)_

#### [Problema] Corrija a descontinuação do PHP 8.5 quando o atributo de categoria tem &#39;frontend_input&#39; ...

Correção de um problema em que a abertura de uma categoria no painel Admin causava um erro no PHP 8.5 quando um atributo category tinha frontend_input definido como null. Páginas de categoria agora abrem e podem ser editadas com êxito sem o erro de desativação.

_AC-17499 - [Problema do GitHub](https://github.com/magento/magento2/issues/40908) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [Problema] Substituir asserções PHPUnit obsoletas e configuração de test-stub

Atualização do conjunto de testes da unidade principal do Magento 2 para atualizações futuras do PHPUnit, substituindo sete usos obsoletos do PHPUnit. As alterações endereçam `isType()` asserções e `with*()` configuração em stubs de teste — padrões que disparam avisos de descontinuação nas versões atuais do PHPUnit e estão programadas para remoção no PHPUnit 13 ou posterior.

_AC-17750 - [Problema do GitHub](https://github.com/magento/magento2/issues/41040) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/41033)_

#### Os carimbos de data/hora GraphQL order_date e comment retornam data de calendário incorreta em locais diferentes de en_US (erro de análise IntlDateFormatter) — Correção AC-14431 incompleta

Correção de um problema em que as datas de pedido do GraphQL podiam mostrar uma data de calendário incorreta para localidades francesas e alemãs.
As datas de pedido e os carimbos de data e hora de comentário relacionados agora retornam a data e a hora corretas.
Formatação de data aprimorada para que os valores de data do GraphQL possam ser analisados de forma confiável pelos aplicativos.
O comportamento existente para a localidade en_US permanece inalterado.

_AC-18084 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d10ab92b)_

#### [Problema] Remover marca @author proibida

Para garantir o alinhamento estrito com as diretrizes técnicas principais, uma varredura de manutenção de código incremental foi concluída para limpar os blocos de documentação de recursos em linha em vários módulos do sistema.

_AC-8366 - [Problema do GitHub](https://github.com/magento/magento2/issues/37248) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36993)_

#### [Problema] Remover a marca `@author` proibida de `Magento_Catalog` (parte 2)

Para garantir o alinhamento total com as diretrizes de entrega de código unificado da Magento, uma passagem de limpeza incremental foi executada para retirar sistematicamente comentários de arquivos não compatíveis entre os modelos de recursos principais da loja.

_AC-8370 - [Problema do GitHub](https://github.com/magento/magento2/issues/37247) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36988)_

#### Preço da Camada Interface de Armazenamento Excluir Bug não exclui todos os Preços da Camada

Correção de um problema no TierPriceStorage em que a exclusão de preços de camada de produto em vários sites não excluía todos os preços ao atualizar a lógica de correspondência de ID de preço para contabilizar a ID de site atribuída.

_AC-9738 - [Problema do GitHub](https://github.com/magento/magento2/issues/37949) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40557)_

#### [B2B] Ordens de compra não convertidas automaticamente em ordem de venda com AtiveMQ

Correção de um problema em que os consumidores iniciados pelo cron não processavam mensagens quando o AtiveMQ era usado com o protocolo STOMP. Como resultado, as ordens de compra aprovadas automaticamente não eram convertidas em ordens de venda. O processamento de mensagens para filas STOMP agora é mais confiável e consistente com as implementações de fila DB e AMQP.

_ACP2E-4349 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/08b91f1a) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/239464da)_

#### Falha nas exportações com o armazenamento AWS S3 configurado

A exportação do produto agora funciona corretamente quando o armazenamento remoto do AWS S3 é configurado. Anteriormente, os arquivos exportados não podiam ser gravados em S3 devido à resolução de caminho inválida no driver de armazenamento.

_ACP2E-4786 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Indexadores presos em loop de autobloqueio com provedor &#39;use_application_lock&#39; e &#39;file&#39;

Correção de um problema em que os indexadores travavam indefinidamente durante a reindexação quando a configuração do indexador use_application_lock era ativada junto com o provedor de bloqueio de arquivo. As operações de reindexação agora são concluídas conforme esperado.

_ACP2E-5027 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Desempenho lento com variáveis MAGENTO_DC definidas na interface do usuário da nuvem

Após a correção, a configuração de implantação não é recarregada sempre que a chave solicitada não está presente e algumas variáveis de ambiente são definidas.

_ACP2E-5094 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

#### O caminho de URL malformado da [NUVEM] retorna HTTP 500 em vez de 404 no roteador de reescrita de URL

Correção do problema em que um URL de vitrine malformado retornava uma página de erro HTTP 500 em vez de uma página 404 Não encontrada padrão. Anteriormente, certos caminhos de solicitação malformados causavam um erro inesperado durante a resolução de regravação do URL.

_ACP2E-5154 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### Compatibilidade do PHP 8.5 com [CLOUD] — ComponentRegistrar::getPath() null array offset falha na configuração:static-content:deploy (estratégia compacta) na versão 2.4.9

Correção de um problema em que `setup:static-content:deploy` falhava no PHP 8.5 com um erro &quot;Using null as a array offset&quot; ao compilar os arquivos LESS do módulo que usavam a diretiva //@magento_import. A implantação do conteúdo estático agora é concluída com sucesso no PHP 8.5.

_ACP2E-5183 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS] Falso-positivo &quot;Conteúdo de HTML inválido fornecido&quot; ao salvar o bloco do CMS com um href de âncora seguido por outro atributo

O conteúdo CMS que contém um link de âncora padrão (por exemplo, `&lt;a href="https://example.com/page" target="_blank" rel="noopener">`) não aciona mais um aviso falso de validação &quot;Conteúdo HTML inválido fornecido&quot; ou uma falha de salvamento quando cms/wysiwyg/force_valid está habilitado.

_ACP2E-5203 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Framework, GraphQL

#### O item da matriz di.xml é substituído se a configuração posterior usar uma chave numérica

Para proteger a integridade dos dados arquitetônicos e melhorar a extensibilidade modular, um bug central foi resolvido no mecanismo de análise XML da Injeção de Dependência (DI), onde as configurações de matriz que usam a chave numérica &quot;0&quot; eram silenciosamente substituídas ou descartadas durante a compilação do módulo.

_AC-8102 - [Problema do GitHub](https://github.com/magento/magento2/issues/36861) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### addProductsToCart aciona erros em custom_attributesV2 se o código do atributo for modelo

Correção de um problema em que addProductsToCart retornava um erro interno do servidor quando um produto tinha um atributo personalizado com o modelo de código. O atributo personalizado agora pode ser recuperado corretamente por meio de custom_attributesV2.

_AC-16987 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/809ba93c)_

#### Quantidade GQL nula enquanto stock_status é IN_STOCK

O campo de quantidade na consulta de produtos GraphQL retornou incorretamente nulo para produtos que estavam em estoque em um estoque MSI personalizado. O resolvedor estava obtendo a resposta no valor de configuração cataloginventory/options/not_available_message antes de buscar a quantidade real do estoque, e o padrão XML dessa configuração (2 — &quot;Itens insuficientes para venda&quot;) fez com que nulo fosse retornado em qualquer loja nova sem uma substituição explícita do administrador.
O cheque agora é avaliado depois que a quantidade vendável é resolvida. é retornado nulo somente quando o produto não tem estoque disponível (saleableQty &lt;= 0) e a loja é explicitamente configurada com &quot;Itens insuficientes para venda&quot;. Os produtos que estão em estoque sempre retornam sua quantidade comercializável real, independentemente dessa configuração. A leitura da configuração também é corrigida para usar o escopo do armazenamento, de modo que as substituições no nível do armazenamento sejam respeitadas.

_ACP2E-4840 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price ignora os preços no escopo do site quando o Escopo de Preço do Catálogo = Site

Correção dos preços de opção de pacote no escopo do site na GraphQL: resolveu um problema em que a consulta de opções de produto de pacote por meio do GraphQL retornava preços globais para &quot;Todas as exibições da loja&quot; em vez de preços no escopo do site quando o escopo do preço de catálogo era definido para o site. O resolvedor Magento\BundleGraphQl\Model\Resolver\Links\Collection agora verifica corretamente o escopo de preço e se junta aos preços de seleção específicos do site com base no escopo de loja solicitado.

_ACP2E-5057 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Carrinho ativo duplicado criado para o cliente devido à condição de corrida de solicitações simultâneas do GraphQL customerCart

O sistema agora garante que somente um carrinho ativo seja criado por cliente, independentemente da simultaneidade da solicitação. Anteriormente, duas consultas simultâneas de GraphQL customerCart ou solicitações REST POST /V1/carts/mine para o mesmo cliente autenticado sem carrinho ativo podiam resultar em registros de carrinho ativos duplicados no banco de dados.

_ACP2E-5077 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### [GraphQlNoSoEntityException da Cloud] tratada a partir do QuoteGraphQl registrado no exception.log, causando crescimento de log não associado

Correção de um problema em que os erros esperados de GraphQlNoTaisEntityException, como aqueles retornados por uma ID de carrinho expirada ou inválida, eram gravados em var/log/exception.log. Esses erros tratados ainda são retornados ao cliente como respostas normais de erro do GraphQL, mas não preenchem mais o log de exceções.

_ACP2E-5122 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL, Inventário / MSI

#### GraphQL: a ID da loja passada como ID do site em ProductStock::isProductAvailable causa o erro &quot;o site ... não foi encontrado&quot;

Anteriormente, algumas lojas podiam encontrar um site. Erro não encontrado ao verificar a disponibilidade do estoque de produtos ao adicionar itens ao carrinho, devido à ID da loja ser usada onde uma ID de site era necessária. Isso foi corrigido para que as verificações de disponibilidade de estoque usem o contexto correto do site, evitando o erro.

_ACP2E-5242 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL, Pedido

#### [Solicitação de recurso] Limpar redundantes nos dados de retirada do armazenamento ao alterar a transportadora da remessa

Ao alternar da coleta na loja para o método de entrega inicial, o local de coleta e o endereço de armazenamento associado são removidos do carrinho. Um endereço de entrega válido deve ser fornecido antes que o pedido possa ser feito.

_ACP2E-4973 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL, Produto

#### Chave \&quot;model\&quot; ausente nos dados de valor da lista de desejos

Correção de um problema em que a consulta de detalhes da lista de desejos por meio do GraphQL retornava um erro interno do servidor.
A consulta da lista de desejos agora é retornada com sucesso sem o erro &quot;Modelo de chave ausente nos dados de valor da lista de desejos&quot;.

_AC-8062 - [Problema do GitHub](https://github.com/magento/magento2/issues/36909) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Importação e exportação

#### [Problema] Corrigir a visibilidade do iframe de importação

Para garantir uma interface de usuário limpa e elegante no painel de administração da Magento, um defeito no layout do modelo foi resolvido, onde um iframe de execução em segundo plano interno ficou visível para os gerentes de armazenamento durante as validações de dados

_AC-13250 - [Problema do GitHub](https://github.com/magento/magento2/issues/39267) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39265)_

#### [Correção de problema]: algoritmo de hash xxh128 codificado na importação do produto

Para limpar subsistemas internos e aproveitar linhas de base modernas de otimização do sistema, o componente de importação de produtos foi simplificado para usar um único algoritmo de hash permanente.

_AC-16967 - [Problema do GitHub](https://github.com/magento/magento2/issues/40770) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40687)_

#### O botão Importar permanece disponível após erros de validação quando a Estratégia de validação é definida como &quot;Parar em caso de erro&quot;

Correção do problema em que o botão Importar ainda era exibido nos resultados da validação após uma falha na validação de dados, quando a Estratégia de validação era definida como &quot;Parar em caso de erro&quot;. Anteriormente, o botão aparecia e podia ser clicado mesmo com falha na validação de todos os registros, portanto, a tentativa de importação era encerrada imediatamente.

_ACP2E-5124 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Instalar e administrar

#### Correção de códigos de subdivisão ISO desatualizados da [Cloud]

Atualização dos códigos de região para 13 países para corresponder ao padrão ISO 3166-2. Anteriormente, alguns códigos de região não correspondiam ao padrão, o que poderia causar problemas com integrações de terceiros e conformidade internacional. Novas regiões adicionadas para Bélgica, Colômbia, Espanha, França, Itália e Letônia. Códigos de região atualizados para Áustria, Colômbia, Costa Rica, Alemanha, Estônia, Espanha, Finlândia, França, Índia, Islândia e Letônia.

_ACP2E-4495 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Inventário / MSI

#### [CLOUD] Cartão-presente e WF-1688 relacionado não vendável

O produto não desaparece quando ações/origens fora do padrão são usadas e o produto relacionado (relacionado ou de venda adicional ou venda cruzada) é salvo.

_ACP2E-4741 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Inconsistência no status do estoque do produto do pacote

Anteriormente, quando um administrador de loja atualizava manualmente o status do estoque de um produto incluído no painel Administrador, a alteração não era refletida na loja para lojas configuradas com várias fontes de estoque. Os clientes continuariam a ver o status de estoque desatualizado, apesar das alterações do administrador.

Esse problema foi corrigido. As alterações no status do estoque de produtos agrupados feitas no painel de Administração agora são propagadas corretamente em todas as fontes de inventário e locais de estoque configurados, garantindo que os clientes sempre vejam a disponibilidade precisa do estoque na loja.

_ACP2E-4866 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/db712a46)_

#### NoSoEntityException &quot;armazenamento solicitado não encontrado&quot; lançado por GetStockIdForCurrentWebsite.php

Correção do problema em que visitar uma página de loja com um parâmetro de consulta ?store= inválido fazia com que NoSoEntityException fosse registrado em nível CRITICAL em cada solicitação. Anteriormente, o plug-in de dados de estoque do MSI transmitia o código de armazenamento bruto diretamente para StoreManager::getStore() sem lidar com o caso em que o armazenamento não existia, resultando em confusão de log de exceção.

_ACP2E-5003 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/1bf25e46)_

### Pedido

#### O Observador de Pedido de Cancelamento não é executado quando o escopo é de front-end ou webapi_rest

Correção de um problema em que o cancelamento de uma ordem da loja ou por meio do escopo webapi_rest não executava o observador de cancelamento corretamente. Os valores do cartão-presente agora são restaurados para o crédito da loja do cliente quando o pedido é cancelado.

_AC-16353 - [Problema do GitHub](https://github.com/magento/magento2/issues/40414) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### A regra de preço do carrinho com uso limitado não é aplicada ao editar um pedido existente no Admin (por exemplo, &quot;Usos por cliente = 1&quot;)

Correção de um problema em que os descontos da Regra de preço do carrinho com limites de uso eram removidos ao editar um pedido existente no Administrador. O desconto original agora é preservado quando o pedido é editado, mesmo depois que o limite de uso é atingido.

_AC-16671 - [Problema do GitHub](https://github.com/magento/magento2/issues/40624) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Erro de validação de quantidade mínima no painel do administrador para produtos agrupados

Para melhorar a experiência de ordenação de back-end e remover blocos funcionais ao gerar cotações manuais, um erro de validação foi resolvido, em que os parâmetros de item filho eram avaliados incorretamente durante a criação do pedido administrativo.

_AC-17193 - [Problema do GitHub](https://github.com/magento/magento2/issues/40812) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40863)_

#### Inconsistência de quantidade de itens secundários do produto de pacote na Exibição de Pedido de Front-end

A página de detalhes do pedido da loja agora mostrará a quantidade total solicitada para cada opção de produto de pacote. Anteriormente, a coluna de quantidade para cada opção filha mostrava a quantidade solicitada do pacote pai em vez da quantidade total solicitada por opção.

_ACP2E-4820 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex::execute() sem DeadlockException e causa falha permanente de ShipOrder/InvoiceOrder-

As operações ShipOrder e InvoiceOrder agora são resolvidas com êxito no caso de Deadlock.
Anteriormente, as operações ShipOrder e InvoiceOrder falhavam permanentemente devido ao Deadlock

_ACP2E-4913 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Cálculo incorreto em nível de linha FPT/WEEE em itens configuráveis principais durante a geração da fatura

Os totais gerais de notas fiscais e avisos de crédito para produtos configuráveis agora incluem corretamente o valor de Imposto Fixo do Produto. Anteriormente, as quantias em nível de linha do FPT não eram propagadas para o item da ordem pai configurável, fazendo com que os totais da NFF e do aviso de crédito fossem inferiores ao total geral da ordem pela quantia do FPT.

_ACP2E-4977 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Quantidades de produto modificadas na atualização da página ao criar pedido do administrador

Solução de um problema em que atualizar a página poderia fazer com que o mesmo SKU fosse adicionado várias vezes.

_ACP2E-5046 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Trabalhadores simultâneos do cron de email assíncrono enviam emails de confirmação de pedido duplicados para o mesmo pedido

Solução de um problema em que os trabalhadores simultâneos de email podiam enviar emails de confirmação de pedido duplicados para o mesmo pedido.

_ACP2E-5059 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### O trabalho cron [CLOUD] sales_clean_quotes está sem memória

Correção do problema em que o trabalho sales_clean_quotes cron ficava sem memória ao limpar um grande número de cotações expiradas. Anteriormente, o trabalho retinha cada cotação processada na memória e terminava com um erro fatal de esgotamento de memória antes que todas as cotações expiradas fossem removidas.

_ACP2E-5137 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### Pedido, Promoção

#### Descontos de regra de preço do carrinho de categoria de valor fixo filho de pacote dinâmico não correspondente quando a regra corresponde ao pai do pacote

Correção do problema em que uma regra de preço do carrinho de valor fixo com uma condição de categoria aplicava incorretamente um desconto a todos os filhos de um pacote de preço dinâmico quando a regra correspondia somente ao pai do pacote. Anteriormente, os filhos agrupados que não pertenciam à categoria de destino recebiam uma parte rateada do desconto em vez de zero.

_ACP2E-5075 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Pagamentos

#### O comando config:show não funciona com caminhos parciais em versões mais recentes

O comando `config:show` agora aceita caminhos de configuração parciais, como pagamento, e exibe os valores de configuração nesse caminho. Anteriormente, a execução do pagamento `php bin/magento config:show` retornava um erro: `The "payment" path doesn't exist. Verify and try again.` em vez de mostrar os valores corretos.

_AC-13908 - [Problema do GitHub](https://github.com/magento/magento2/issues/39610) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40432)_

### Desempenho

#### a instalação :upgrade está alterando o modo indexador de `schedule` para `save`, tornando-a imensamente lenta

Solução de um problema antigo em que a execução da configuração bin/magento:upgrade alteraria inadvertidamente os modos do indexador de &quot;Salvar na Programação&quot; para &quot;Salvar ao Salvar&quot; e desnecessariamente descartaria e recriaria os acionadores do banco de dados, reduzindo drasticamente o tempo de inatividade e evitando gargalos de desempenho durante implantações em catálogos grandes.

_AC-2423 - [Problema do GitHub](https://github.com/magento/magento2/issues/33386) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40643)_

#### As chaves de cache de LAYOUT Valkey consomem muito espaço para um grande catálogo de produtos

Anteriormente, cada produto gerava sua própria entrada de cache de LAYOUT por exibição de loja, causando consumo excessivo de memória no Redis/Valkey em catálogos grandes. Agora, as entradas de cache de LAYOUT são compartilhadas entre produtos com o mesmo tipo, conjunto de atributos e visualização de loja, limitando o crescimento do cache independentemente do tamanho do catálogo.

_ACP2E-4908 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### Erro de deadlock na consulta do produto

Correção de um impasse do InnoDB em páginas com uma Lista de produtos CatalogWidget filtrada por categoria, que ocorria quando o indexador de preço do modo de agendamento era executado simultaneamente.

_ACP2E-5052 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] degradação do desempenho de consulta de resolução de URL do Adobe Commerce

Correção do problema em que a consulta de rota do GraphQL sempre renderizava o conteúdo completo da página do CMS, incluindo a execução de widget do Page Builder e o carregamento da coleção de produtos, mesmo quando somente os metadados de roteamento de URL (relative_url, redirect_code, type) eram solicitados. Anteriormente, isso causava a renderização desnecessária de widgets/produtos e um aumento significativo nas consultas ao banco de dados por solicitação de páginas do CMS que continham widgets do Page Builder.

_ACP2E-5143 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Admin Customer Edit dos tanques de desempenho quando o Compartilhamento de conta do cliente estiver configurado para Global

Correção de um problema de desempenho na página Editar clientes administradores, em que o tempo de carregamento e o tamanho da resposta HTTP aumentavam de forma quadrática quando Compartilhar contas de clientes era definido como Global.

_ACP2E-5164 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Produto

#### O botão Adicionar ao carrinho no pop-up &quot;Clique para preço&quot; não funciona.

Correção de um problema em que o botão Adicionar ao carrinho no pop-up &quot;Clique para obter preço&quot; na página da lista de produtos não adicionava o produto ao carrinho.
Os produtos agora podem ser adicionados ao carrinho com êxito a partir do pop-up.

_AC-11896 - [Problema do GitHub](https://github.com/magento/magento2/issues/30356) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Resolvedores de BundleGraphQL Criam Instâncias de Produto Adiadas Separadas, Derrotando o Lote de Consultas (N+1)

Para acelerar drasticamente a taxa de transferência de resposta da API e minimizar a sobrecarga do servidor, a camada de resolução do GraphQL foi otimizada para aplicar o verdadeiro agrupamento de consultas para produtos agrupados, eliminando vazamentos de banco de dados N+1, que consomem muito o desempenho.

_AC-16647 - [Problema do GitHub](https://github.com/magento/magento2/issues/40595) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40867)_

#### A validação de atributos Select e Multiselect EAV rejeita incorretamente rótulos de opção com o valor &quot;0&quot;

Para melhorar a integridade dos dados e eliminar erros inesperados de envio em formulários de catálogo e de cliente, uma falha de validação foi resolvida, onde rótulos de opção contendo o valor exato da sequência de caracteres &quot;0&quot; foram rejeitados incorretamente pela estrutura principal do EAV

_AC-16986 - [Problema do GitHub](https://github.com/magento/magento2/issues/40634) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40827)_

#### Rótulos de opção personalizáveis e títulos de opção personalizáveis não podem ser salvos quando a função de um usuário está limitada a um determinado escopo

Correção de um problema em que rótulos e títulos de opções personalizáveis eram revertidos quando editados por um usuário administrador com acesso limitado a um escopo de loja específico.
Os rótulos e títulos atualizados agora são salvos corretamente para o escopo selecionado.

_AC-2684 - [Problema do GitHub](https://github.com/magento/magento2/issues/35210)_

#### O Consumidor de Alerta do Produto ignora o sistema/carimbo/desabilitação com escopo de armazenamento

O Consumidor de Alerta do Produto agora é responsável pela configuração de sistema/carimbo/desativação com escopo de loja.

_ACP2E-4870 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Página de comparação de front-end exibindo traduções incorretas de rótulo de Descrição curta

Anteriormente, na página Comparar produtos, rótulos de atributos comparáveis, como Descrição curta, podiam exibir uma tradução de uma visualização de loja diferente, em vez da exibição da loja atual. Agora, as traduções corretas específicas da loja são exibidas.

_ACP2E-4929 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

#### O carrossel de produtos do Page Builder ignora a ordem de classificação de posição da categoria, exibindo produtos na ordem DESC de entity_id

Correção de um problema em que os produtos exibidos em um carrossel do Page Builder definido para classificar por posição de categoria apareciam na ordem errada na loja. Os produtos agora são mostrados na ordem configurada na guia Admin → Catálogo → Categorias → Produtos.

_ACP2E-4980 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Regras de promoção

#### Cálculo de desconto incorreto quando uma das regras de preço do carrinho aplicadas tem valor de Etapa de Qtd. de Desconto

Correção de um problema em que o desconto era calculado incorretamente quando várias regras de preço do carrinho eram aplicadas e uma regra tinha um valor de Etapa de quantidade de desconto (Comprar X).
Os descontos agora são calculados corretamente para todas as quantidades qualificadas.

_AC-12307 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c10554e1)_

### Devoluções

#### RMA - Adicionar API de Comentários de Devolução - Os emails são acionados para o Remetente (Representante de Vendas), mas não para o Cliente

Correção de um problema em que os emails de comentário de retorno enviados por meio da API de retornos eram enviados ao representante de vendas, mas não ao cliente.
Agora os clientes recebem uma notificação por email quando um comentário de retorno é adicionado por meio da API, com a notificação do cliente ativada.

_AC-1138 - [Problema do GitHub](https://github.com/magento/magento2/issues/33985)_

### Vendas

#### `[Order][REST]` sales_order_items coluna product_options sem dados quando o pedido é feito da API rest V1/orders ou V1/orders/create endpoints

Correção de um problema em que os itens de pedido criados por meio da API REST não incluíam dados completos de product_options. Os rótulos de opção personalizados e os detalhes de opção relevantes agora são salvos corretamente para pedidos criados por meio da API REST.

_AC-15187 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### Grade de ordem de venda presa permanentemente no status obsoleto quando a indexação de grade assíncrona está habilitada devido a carimbos de data e hora vinculados updated_at

Correção de um problema em que a Grade de ordens de venda podia permanecer presa a um status de pedido obsoleto quando a indexação de grade assíncrona era ativada. O status da grade de pedidos agora é atualizado corretamente para corresponder ao status atual do pedido, incluindo casos em que várias atualizações de pedidos ocorrem no mesmo segundo.

_AC-17118 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/478f8e7c)_

### Segurança

#### [Problema] Atualize o texto DOM js.phtml reinterpretado como HTML

Para fortalecer a linha de base de segurança da plataforma e minimizar o risco de execução de entrada mal-intencionada, o modelo de script integrado principal que lida com atualizações dinâmicas de DOM foi refatorado para eliminar os vetores de injeção de script entre sites (XSS).

_AC-12118 - [Problema do GitHub](https://github.com/magento/magento2/issues/38821) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38804)_

### Envio

#### Problema com a API REST USPS, taxas incorretas para o Peso máximo do pacote

Correção de estimativas de envio incorretas quando um pedido é dividido em vários pacotes (por exemplo, acima de &quot;Peso máximo do pacote&quot;). A operadora agora solicita uma taxa para cada pacote e totaliza os valores, de acordo com o fluxo de Web Tools herdado.

_ACP2E-4813 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6c67a9b5)_

### Imposto

#### base_wee_tax_plied_amount não foi definido para produto principal

o valor base_weee_tax_plied_amount agora é preenchido para o produto configurável em tabelas de banco de dados como sales_order_item, sales_Invoice_item, sales_creditmemo_item, não apenas para seu filho

_ACP2E-4922 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### Estrutura de teste

#### [Problema] Atualizar o GraphQL testa o Client.php para comparação de substring que não diferencia maiúsculas de minúsculas

Correção de um problema em que os testes de API do GraphQL não reconheciam cabeçalhos Set-Cookie quando o cabeçalho usava letras maiúsculas e minúsculas diferentes. Os testes agora manipulam corretamente os cabeçalhos Set-Cookie, set-cookie e SET-COOKIE.

_AC-15337 - [Problema do GitHub](https://github.com/magento/magento2/issues/39713) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Testes funcionais do WebAPI GraphQL extremamente lentos

Para otimizar as configurações de entrega de build e acelerar os ambientes de integração contínua (CI), um gargalo de infraestrutura de teste foi resolvido com a transição dos comportamentos de limpeza de cache das chamadas de comando do sistema externo para o manuseio de memória nativa em andamento.

_AC-15395 - [Problema do GitHub](https://github.com/magento/magento2/issues/39725) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40804)_

### Estrutura da interface

#### O minicart não pode ser usado duas vezes na mesma página

Para fornecer aos desenvolvedores de front-end maior flexibilidade de layout, uma limitação da interface do usuário principal de longa data foi resolvida, permitindo que vários blocos de minicart (por exemplo, um no cabeçalho e outro no rodapé) existam e sejam atualizados de forma independente em um layout de página única.

_AC-12579 - [Problema do GitHub](https://github.com/magento/magento2/issues/38958) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [Correção de problema]&#x200B;(pagecache): reconhecer o PATCH como método HTTP válido no VCL do Verniz

O VCL de verniz padrão da Magento agora reconhece o PATCH como um método HTTP válido, portanto, as solicitações de atualização parcial da API REST (por exemplo, PATCH /rest/V1/products/:sku) são passadas para o back-end em vez de serem canalizadas. Isso corrige as chamadas de PATCH que falham ou se comportavam incorretamente quando o Cache de página cheia é definido como Verniz.

_AC-16954 - [Problema do GitHub](https://github.com/magento/magento2/issues/40757) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40657)_

#### [Problema] Substituir todos os parâmetros gad_* no VCL

Para eliminar as regressões de desempenho causadas por campanhas de anúncios dinâmicos, as camadas de cache do aplicativo foram atualizadas para ignorar proativamente todas as sequências de consulta gad_* do Google Ads. Isso impede que links de campanha externos invalidem caches de página e retardem páginas de destino

_AC-16980 - [Problema do GitHub](https://github.com/magento/magento2/issues/40781) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40780)_

#### Correção de [Problema]: atualizar verificação de versão mínima do PHP na inicialização para 8.3

Para evitar erros de tempo de execução confusos e melhorar a solução de problemas da instalação do desenvolvedor, o validador de ambiente nativo do PHP dentro da estrutura de inicialização do sistema foi trazido de acordo com os requisitos principais reais do aplicativo.

_AC-17312 - [Problema do GitHub](https://github.com/magento/magento2/issues/40851) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40686)_

#### `health_check.php` retorna 500 quando `igbinary` está instalado e o cache de arquivos padrão é usado (Verniz 503)

Correção de um problema onde health_check.php retornava HTTP 500 quando igbinary era instalado com o back-end de cache de arquivo padrão. A verificação de integridade agora aceita configurações de cache válidas sem uma chave de back-end explícita, impedindo que o Vernish marque o back-end como não íntegro e retornando HTTP 503.

_AC-17400 - [Problema do GitHub](https://github.com/magento/magento2/issues/40876) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### Correção de [Problema]: atualizar tipos gzip e remover a solução alternativa do IE6 na configuração nginx

Para melhorar as velocidades de carregamento da página e otimizar a entrega de ativos de rede, a configuração do servidor de fallback foi modernizada para oferecer melhor suporte aos componentes modernos da loja e remover a sobrecarga técnica herdada

_AC-17498 - [Problema do GitHub](https://github.com/magento/magento2/issues/40774) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40681)_

#### [Problema] Tentativa de corrigir graphql não sincronizado OrderStatusChangeDateTest.

Para melhorar a confiabilidade da integração contínua (CI) e reduzir falhas de build falso-positivo, uma condição de corrida foi resolvida no conjunto de testes funcional WebAPI. O teste de validação do status do pedido do GraphQL (OrderStatusChangeDateTest) teve falhas intermitentes anteriormente devido a discretas disparidades de tempo entre a memória do PHP e os carimbos de data e hora do MySQL

_AC-17959 - [Problema do GitHub](https://github.com/magento/magento2/issues/41126) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40618)_
