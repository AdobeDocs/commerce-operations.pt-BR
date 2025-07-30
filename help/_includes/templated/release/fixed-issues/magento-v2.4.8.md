---
source-git-commit: 1f377ab6e4dcdd2d350366f3889b8befd233474b
workflow-type: tm+mt
source-wordcount: '25720'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.8)

## Destaques

Os 31 destaques a seguir se aplicam à versão 2.4.8 do Magento Open Source.

### Estrutura

#### Atualizar as dependências do League/flysystem Composer para a versão mais recente

Atualize as dependências do 2.x league/flysystem Composer para a versão mais recente 3.x

_AC-10721 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/91cb4d46>)_

#### Investigar as versões mais recentes do php-amqplib/php-amqplib

Atualização da versão mais recente de php-amqplib/php-amqplib :^3.x

_AC-11673 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### limpeza do css jQuery/fileuploader após a migração para a biblioteca uppy

Remoção da biblioteca jQuery/fileUploader porque ela foi migrada para a biblioteca Upload

_AC-11911 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/7cabfb46>)_

#### Adicionar compatibilidade com o MySQL 8.4 LTS para Magento CE

_AC-11995 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Limpeza da pasta ExtJs após a migração para a biblioteca jsTree

A pasta extJs removida, pois a funcionalidade relacionada foi migrada para jsTree

_AC-12015 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/7cabfb46>)_

#### Atualizar dependência de sistema monólogo/monólogo para a versão principal mais recente

O sistema foi atualizado para usar a versão principal mais recente da biblioteca &quot;monolog/monolog:^3.x&quot;, garantindo compatibilidade e melhor desempenho. Anteriormente, o sistema usava uma versão desatualizada da biblioteca &quot;monolog/monolog&quot;, que poderia ter levado a possíveis problemas e limitações.

_AC-12022 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### Atualize a dependência wikimedia/less.php para a versão principal mais recente

O sistema foi atualizado para usar a versão principal mais recente 5.x da biblioteca &quot;wikimedia/less.php&quot;, garantindo a compatibilidade e a funcionalidade atualizada. Anteriormente, o sistema usava uma versão desatualizada da biblioteca que poderia ter causado problemas de segurança.

_AC-12023 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### Atualizar dependência de biblioteca jquery/validate para a versão secundária mais recente

Atualizar dependência de biblioteca jquery/validate para a versão secundária mais recente 1.20.0

_AC-12024 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### Atualizar dependência do sistema Moment.js para a versão secundária mais recente

Atualizar dependência do sistema Moment.js para a versão secundária mais recente 2.30.1

_AC-12025 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### Adicionar compatibilidade com o MySQL 8.4 LTS para EE

_AC-12032 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Adicionar compatibilidade com o MySQL 8.4 LTS para B2B

_AC-12034 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Adicionar compatibilidade com o MySQL 8.4 LTS para extensões de pacote

_AC-12074 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Adicionar compatibilidade com MariaDB 11.4 LTS para CE

Adição do suporte ao MariaDB 11.4 com Adobe Commerce e extensões

_AC-12085 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### Otimização De Assinantes - PhpUnit10

_AC-12165 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/90e25b6b>)_

#### Suporte a novas tentativas de conexão para a sessão Redis e compatível com colinmollenhour/php-redis-session-abstract v2.0.0

Atualização da versão mais recente de colinmollenhour/php-redis-session-abstract v2.0.0 compatível com o adobe commerce

_AC-12267 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Investigar as falhas de testes de automação com o MySQL 8.4 LTS

_AC-12576 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_

#### Adicionar compatibilidade com o MariaDB 11.4 LTS for EE

Adição do suporte ao MariaDB 11.4 com Adobe Commerce e extensões

_AC-12595 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### Atualizar dependências do Caminas Composer atualizando para a versão mais recente

O sistema agora oferece suporte às versões mais recentes das dependências do compositor laminas:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
lâminas/lâminas-validador
garantir a compatibilidade e a funcionalidade atualizada. Anteriormente, a atualização para as versões mais recentes dessas dependências podia causar problemas de incompatibilidade com versões anteriores e falhas de teste.

_AC-12715 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### Investigue a falha no teste de unidade devido à atualização de patch phpunit durante a atualização do componente

_AC-12823 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### [Parte 1] - Atualizar toda a biblioteca js e a dependência npm com a versão mais recente disponível

o suporte à versão do compositor era somente para a versão 2.2.x do compositor. Agora, o suporte também foi estendido para a versão 2.4.x.

_AC-13076 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/19844aa0>)_

### Pedido

#### [Solicitação de recursos] O cliente sugere que o botão Enviar Comentário na página Detalhes do pedido é confuso e deve ser alterado para algo diferente

Para minimizar a confusão, o rótulo do botão &quot;Enviar comentário&quot; foi alterado para &quot;Atualizar&quot; na página de detalhes do pedido.

_ACP2E-2709 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/488c1034>)_

### Outro

#### Os indexadores definidos aparecem no padrão de status Pronto quando a nova versão do Adobe Commerce é instalada

Após a Instalação do Magento, o Status do Indexador deve estar no estado *Pronto* por padrão.

_AC-11420 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/71432aeb>)_

#### Na instalação existente do Magento, ao instalar indexadores de terceiros, defina os indexadores como atualizar por padrão.

Todos os novos indexadores estão por padrão no modo [Atualizar por Agendamento]. Anteriormente, o modo padrão era [Atualizar ao salvar]. O mesmo acontece com os indexadores personalizados.

_AC-11421 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/71432aeb>)_

#### As opções do Elasticsearch 7 e 8 devem vir com Obsoleto na configuração do administrador.

A opção Elasticsearch 8 na Configuração de administração será exibida com o Texto obsoleto para informar aos usuários que o Elasticsearch 8 não é mais a opção recomendada para uso.

_AC-12480 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/0611e750>)_

#### Adicionar nota de texto quando a opção Elasticsearch estiver selecionada na Configuração de administração

Uma nota de texto é adicionada para informar aos usuários administradores do Adobe Commerce que o elasticsearch não é mais compatível com o Adobe e está obsoleto.

_AC-12481 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/0611e750>)_

#### Fornecer patch de melhoria de desempenho de operações de preço de nível na versão 2.4.8

O sistema agora permite atualizações em massa de preços de nível mais eficientes sem causar problemas de desempenho ou falta de resposta do site ao usar o endpoint da API REST &quot;/V1/products/tier-price&quot;. Anteriormente, atualizar um grande número de preços usando esse endpoint podia resultar em problemas de desempenho e incapacidade de resposta do site.

_AC-13448 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/082d981c>)_

#### Remova todos os avisos de direitos autorais confidenciais da Adobe dos repositórios Magento Open Source

Todos os avisos confidenciais de direitos autorais do Adobe foram removidos dos repositórios de código aberto, garantindo que somente a forma reduzida dos direitos autorais do Adobe seja usada. Anteriormente, alguns arquivos nos repositórios públicos continham avisos confidenciais de direitos autorais da Adobe, o que levou a escaladas da comunidade.

_AC-13550 - [Problema do GitHub](https://github.com/magento/magento2/issues/39493) - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/4bca5dfe>)_

### Estrutura da interface

#### [2.4.8-beta1] Migração do TinyMCE 5 para o TinyMCE 7

O TinyMCE 5 foi migrado para o TinyMCE 7.3.0 para ser uma versão compatível com o Adobe Commerce. Anteriormente, o sistema usava a versão 5.10.2, que estava desatualizada e relatava vulnerabilidade de segurança

_AC-12726 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### [2.4.8-beta1] Migração do TinyMCE 5 para o TinyMCE 7 Page Builder

O TinyMCE 5 foi migrado para o TinyMCE 7.3.0 para ser uma versão compatível com o Adobe Commerce. Anteriormente, o sistema usava a versão 5.10.2, que estava desatualizada e relatava vulnerabilidade de segurança

_AC-12825 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### [2.4.8-beta1] Migração do TinyMCE 5 para o TinyMCE 7 - Magento2-infra - palavras banidas

O TinyMCE 5 foi migrado para o TinyMCE 7.3.0 para ser uma versão compatível com o Adobe Commerce. Anteriormente, o sistema usava a versão 5.10.2, que estava desatualizada e relatava vulnerabilidade de segurança

_AC-12844 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### Atualização do Require.js para a versão mais recente 2.3.7 (vulnerabilidade de segurança CVE-2024-38999)

Atualização do require.js para a versão mais recente 2.3.7. Na versão anterior, relatou vulnerabilidade de segurança

_AC-12901 - [Contribuição de código do GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_

## Correção de problemas na v2.4.8

Corrigimos 497 problemas no código principal do Magento Open Source 2.4.8. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

#### /V1/transactions REST API retorna erro quando parent_txn_id = txn_id

O sistema agora lida corretamente com as transações de conceito pai e filho, nas quais o ID da transação pai é igual ao ID da transação, impedindo um loop infinito ao consultar o ponto de extremidade da API REST /V1/transactions. Anteriormente, esse cenário resultava em um erro fatal devido ao tempo máximo de execução ser excedido.

_AC-10042 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### Problema do tipo [Graphql] na versão 2.4.7

O sistema agora lida corretamente com valores inteiros na função GetCustomSelectedOptionAttributes ao executar uma consulta do GraphQL, evitando erros relacionados ao tipo. Anteriormente, iniciar uma consulta GraphQL que usava GetCustomSelectedOptionAttributes com um argumento inteiro resultava em um erro de tipo.

_AC-11878 - [Problema do GitHub](https://github.com/magento/magento2/issues/38662) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38663)_

#### Caracteres especiais na categoria url_key (quando criada por meio da API REST)

Anteriormente Em category_url_key, o caractere especial não está presente após a correção e está mostrando o caractere especial em category_url_key

_AC-3223 - [Problema do GitHub](https://github.com/magento/magento2/issues/35577) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### Problema com a api rest após ativar o 2FA Duo

2FA com opção de segurança Duo agora gera a assinatura correta para API Rest

_ACP2E-2755 - [Contribuição de código do GitHub](https://github.com/magento/security-package/commit/412fa642)_

#### [REST API]: o valor Usar padrão no modo de exibição de loja não permanece marcado após a adição de configurações para um produto configurável

O problema foi corrigido, garantindo entradas corretas do banco de dados para as opções personalizáveis para um armazenamento não padrão. A caixa de seleção do armazenamento personalizado na seção &quot;admin > Catálogo > Edição de produto > Opções personalizáveis&quot; foi desmarcada anteriormente devido a entradas imprecisas do banco de dados, mesmo que o título da opção do armazenamento personalizado permanecesse o mesmo que o armazenamento padrão.

_ACP2E-2927 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### A API REST não pode fazer solicitações com barra (/) no SKU ao usar Oauth1

Antes da correção, você não conseguia fazer uma chamada de API bem-sucedida para um produto que tinha &quot;/&quot; em sua SKU. Agora, você pode emitir uma solicitação de obtenção de API bem-sucedida para detalhes do produto, mesmo que o SKU tenha uma barra.

_ACP2E-2969 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### Falha na atualização do endereço do cliente ao atualizar por meio da API REST se &quot;validateDefaultAddress&quot; estiver ativado

O endpoint da API agora está funcionando como esperado depois que o problema com a chave de ID ausente na carga da API foi resolvido.

_ACP2E-3079 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### [Nuvem] Criando o grupo de clientes de preços de grupo de sites duplicado na API de Preços de Camada.

Agora, a API Restrição de Preço da Camada não permite criar o grupo de clientes de preço de grupo de sites duplicado.
Anteriormente, era possível criar o grupo de clientes Duplicar preço do grupo de sites na API Preços de camada que não passaria na validação no Administrador durante o salvamento do produto.

_ACP2E-3091 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### Não é possível adicionar comentário do pedido com status via API REST

O problema foi resolvido permitindo a alteração no status do pedido se for somente do estado atual. Anteriormente, não respeitava o estado do pedido e impedia alterações em qualquer status do pedido, mesmo que fosse do mesmo estado.

_ACP2E-3130 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Falha na operação assíncrona quando o SKU está ausente da carga

As operações assíncronas e de sincronização falhavam anteriormente devido a erros de salvamento do produto se o SKU estiver ausente da carga. Após a correção, as operações de salvar rest api do produto assíncrono e síncrono falham com a mensagem de exceção relevante.

_ACP2E-3236 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### [NUVEM] Não é possível atualizar os Preços base usando a API REST (o valor de &#39;value_id&#39; em &#39;catalog_product_entity_decimal&#39; não foi incrementado corretamente.)

Antes dessa correção, quando rest api /rest/default/V1/products/base-price era chamado, a id do incremento era aumentada incorretamente, deixando uma lacuna entre os valores. Após a correção, a ID do incremento é aumentada conforme esperado, de forma incremental. Além disso, o intervalo do campo value_id foi aumentado.

_ACP2E-3376 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Os itens da ordem não estão visíveis nos emails de memorando de crédito para a API POST V1/order/:orderId/return

Anteriormente, antes dessa correção, quando um cliente cria um memorando de crédito de uma solicitação de API que notifica send_email, ele não contém a grade de detalhes do produto. Depois que essa correção for aplicada, o cliente enviará uma solicitação de API de aviso de crédito e localizará os detalhes do item de produto que aparecem no email.

_ACP2E-3460 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Os valores padrão não são definidos para atributos de data e hora com produtos RestAPI

Os valores padrão agora são definidos corretamente para atributos de data e data e hora por meio da RestAPI

_ACP2E-3486 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### APIs, carrinho e check-out

#### Erro crítico 500: Magento\Framework\Webapi\Exception relacionado ao cabeçalho HTTP Accept

Após a correção, não há problema em especificar o cabeçalho &quot;Accept&quot;.

_ACP2E-3343 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

### Conta

#### O formulário de endereço do cliente permite código aleatório nos campos de nome

O sistema agora valida a entrada nos campos Nome e Sobrenome no formulário de endereço do cliente, impedindo o uso de código aleatório. Anteriormente, o sistema permitia o uso de código aleatório nesses campos sem gerar um erro.

_AC-10782 - [Problema do GitHub](https://github.com/magento/magento2/issues/38331) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38345)_

#### admin Atualização da senha.

_AC-10886 - [Problema do GitHub](https://github.com/magento/magento2/issues/38352) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4bca5dfe)_

#### falha ao adicionar endereço da minha conta ao salvar

Agora, o sistema salva corretamente os endereços do cliente, mesmo quando o campo de região não é exibido, evitando uma falha durante o processo de salvamento. Anteriormente, tentar adicionar ou editar um endereço sem um campo de região exibido resultava em um erro de exceção.

_AC-10990 - [Problema do GitHub](https://github.com/magento/magento2/issues/38406) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38407)_

#### Redirecionar loop quando o URL estiver em maiúsculas

O sistema agora converte automaticamente caracteres em maiúsculas nos URLs para minúsculas, impedindo um loop de redirecionamento ao acessar a página inicial. Anteriormente, ter caracteres em maiúsculas no URL de base segura causava um loop de redirecionamento contínuo ao tentar acessar a página inicial.

_AC-11718 - [Problema do GitHub](https://github.com/magento/magento2/issues/38538) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38539)_

#### middlename( s) não salvo(s) para contas guest

Agora, o sistema salva corretamente o nome do meio de contas de convidado durante o check-out, tornando-o acessível no template de email. Anteriormente, o nome do meio não era salvo na tabela de cotação e não estava acessível no template de email para contas de convidado.

_AC-11755 - [Problema do GitHub](https://github.com/magento/magento2/issues/38593) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39067)_

#### Admin: botões de ações de página flutuantes à esquerda em vez à direita

O sistema agora alinha corretamente os Botões de ações da página ao lado direito do cabeçalho adesivo no painel do administrador, melhorando a aparência profissional. Anteriormente, esses botões flutuavam incorretamente no lado esquerdo do cabeçalho fixo.

_AC-11919 - [Problema do GitHub](https://github.com/magento/magento2/issues/38701) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### `dev:di:info` erro no magento 2.4.7

O sistema agora exibe corretamente os parâmetros do construtor ao executar o comando `dev:di:info`, impedindo a ocorrência de erros. Anteriormente, a execução desse comando resultava em um erro devido a uma incompatibilidade de tipos no argumento.

_AC-11999 - [Problema do GitHub](https://github.com/magento/magento2/issues/38740) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### A caixa de seleção Fazer logon como aceitação do cliente não pode ser traduzida

O sistema agora permite que os campos &quot;Fazer logon como aceitação do cliente&quot; e &quot;Dica de ferramenta da caixa de seleção Fazer logon como cliente&quot; sejam definidos no escopo &quot;Visualização da loja&quot;, permitindo traduções para diferentes visualizações da loja. Anteriormente, esses campos eram definidos somente no escopo &quot;Site&quot;, impedindo traduções para exibições de loja individuais.

_AC-13000 - [Problema do GitHub](https://github.com/magento/magento2/issues/32329) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32359)_

#### O cliente está conectado, mas mostrando o erro 404 no front-end.

A página do painel do cliente da loja agora é carregada conforme esperado quando um cliente faz logon. Anteriormente, os clientes podiam fazer logon, mas essa página mostrava um erro 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)

_AC-6071 - [Problema do GitHub](https://github.com/magento/magento2/issues/35838) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36263)_

#### Não é possível Salvar as informações do atributo do Cliente na seção Admin Edit customer;

A ID da loja do cliente agora é implementada corretamente por escopo de site para o formulário de edição do cliente administrador.

_ACP2E-2791 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/488c1034)_

#### Depois de fazer logon, os produtos adicionados à lista de comparação como usuário convidado não ficam visíveis.

Os produtos adicionados à lista de comparação de produtos antes de fazer logon como cliente agora são preservados após o logon.
Anteriormente, após o logon, os produtos adicionados à lista de comparação como usuário convidado não estavam visíveis.

_ACP2E-3329 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Permitir configuração de países causa problemas nas configurações de endereço do cliente

Agora, selecionar a configuração Permitir Países não influencia os países mostrados fora do escopo especificado. Anteriormente, a configuração Permitir Países influenciava o atributo de endereço do cliente fora do escopo especificado

_ACP2E-3433 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### VAPT: Erro Lógico de Negócios - data futura como data de nascimento do cliente

A data de nascimento do cliente não pode ser posterior a hoje

_ACP2E-3501 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Conta, APIs, GraphQL

#### API do cliente - Número de falhas de logon não pode ser redefinido para 0 após o logon bem-sucedido

Agora, o número da falha é redefinido para zero na tabela de entidades do cliente após o logon bem-sucedido do cliente por meio dos endpoints da API.

_ACP2E-3246 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Conta, interface do administrador, B2B

#### Os usuários administradores restritos nem sempre podem ver catálogos compartilhados personalizados

Os usuários administradores restritos agora podem exibir e gerenciar de forma consistente os clientes e todos os catálogos compartilhados aos quais os produtos são atribuídos, desde que tenham acesso à loja específica. Anteriormente, um usuário administrador restrito com acesso a uma loja específica nem sempre podia ver todos os catálogos compartilhados aos quais os produtos eram atribuídos ou os clientes que não podiam ser salvos, resultando em inconsistências no sistema.

_ACP2E-3038 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7377de59)_

### Conta, carrinho e check-out

#### o atributo de endereço personalizado do cliente &quot;selecionar&quot; não é renderizado para o novo endereço do cliente

_AC-2341 - [Problema do GitHub](https://github.com/magento/magento2/issues/34950)_

### Interface do administrador

#### [Problema] adicione verificação de permissão para o botão &quot;recarregar dados&quot; de dados

O sistema agora inclui uma verificação de permissão para o botão &quot;Recarregar dados&quot;, garantindo que ele seja exibido e acessível somente aos usuários com as permissões apropriadas. Anteriormente, o botão &quot;Recarregar dados&quot; estava visível e clicável para todos os usuários, resultando em uma página &quot;não permitido&quot; quando clicado por usuários sem as permissões necessárias.

_AC-10705 - [Problema do GitHub](https://github.com/magento/magento2/issues/38283) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38279)_

#### [Problema] Rótulos inconsistentes para atributos em regras de marketing

Agora o sistema preenche corretamente os rótulos de forma consistente para as opções de categoria e atributo na regra de preço do carrinho

_AC-11427 - [Problema do GitHub](https://github.com/magento/magento2/issues/31232) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/31231)_

#### A validação de dados foi bem-sucedida e o botão Importar está presente durante a importação de produtos com comportamento Substituir

O sistema agora valida os dados corretamente e oculta o botão &quot;Importar&quot; durante o processo de importação do produto com o comportamento &quot;Substituir&quot;, impedindo qualquer substituição não intencional de dados. Anteriormente, o sistema validava os dados incorretamente e exibia o botão &quot;Importar&quot;, resultando em possíveis inconsistências de dados.

_AC-11588 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Bug] O Magento 2.4.7 não permite fotos de produtos com extensão de arquivo de letra maiúscula.

O sistema agora aceita uploads de imagem de produto com extensões de arquivo de carta de capital, garantindo um processo de criação de produto tranquilo. Anteriormente, os uploads de imagem com extensões de arquivo em letras maiúsculas eram recusados, forçando os usuários a alterar a extensão do arquivo para minúsculas.

_AC-12167 - [Problema do GitHub](https://github.com/magento/magento2/issues/38831) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### Lista suspensa oculta em grades com a ação de seleção (por exemplo, Conteúdo > Elementos > Páginas)

Agora, o sistema foi corrigido com todas as listas suspensas semelhantes para todas as grades.

_AC-12319 - [Problema do GitHub](https://github.com/magento/magento2/issues/38891) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39371)_

#### [Problema] Aviso de Correção: &quot;filtros&quot; da chave de matriz indefinida

O sistema agora lida com cenários em que um novo usuário ainda não interagiu com marcadores, impedindo que um aviso de &quot;filtros&quot; de chave de matriz indefinido seja registrado. Anteriormente, esse aviso era registrado quando um novo usuário não interagia com marcadores.

_AC-13131 - [Problema do GitHub](https://github.com/magento/magento2/issues/39013) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38996)_

#### O arquivo csv de importação do produto com caracteres especiais falha devido a alterações de código no arquivo Validate.php

O sistema agora valida e importa corretamente arquivos CSV de produtos contendo caracteres especiais, permitindo uma transferência de dados bem-sucedida. Anteriormente, tentar importar um arquivo CSV de produto com caracteres especiais resultava em um erro, impedindo o processo de importação.

_AC-13529 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### Não há asterisco vermelho para o campo obrigatório de número de telefone

O asterisco vermelho anterior não era exibido para o número de telefone, mas  o número de telefone era obrigatório. O que agora é um asterisco vermelho fixo pode ser visto no número de telefone como um campo obrigatório.

_AC-13850 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### [Problema] Defina o modo de indexador padrão como &#39;agenda&#39;

Todos os novos indexadores estão por padrão no modo **[!UICONTROL Update by Schedule]**.  Anteriormente, o modo padrão era **[!UICONTROL Update on Save]**. Os indexadores existentes não são afetados. [GitHub-36419](https://github.com/magento/magento2/issues/36419)

_AC-6975 - [Problema do GitHub](https://github.com/magento/magento2/issues/36419) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0b410856)_

#### [Problema] Descartar tabelas de log de alterações do indexador no cancelamento de inscrição do mview

O sistema agora remove automaticamente tabelas de log de alterações não usadas quando um índice é alternado de &quot;atualização na programação&quot; para &quot;atualização ao salvar&quot;, marcando o índice como inválido para garantir que nenhuma entrada seja perdida. Anteriormente, alternar um índice para &quot;atualizar ao salvar&quot; deixaria as tabelas de log de alterações não usadas no sistema e marcaria todos os índices alterados como &quot;válidos&quot;.

_AC-7700 - [Problema do GitHub](https://github.com/magento/magento2/issues/29789) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/25859)_

#### Nenhum link para envio quando em pagamentos no check-out na visualização de telefone celular

O sistema agora garante que os títulos/links de check-out &quot;Envio&quot; e &quot;Revisão e pagamentos&quot; estejam sempre visíveis na parte superior da página na exibição móvel, permitindo que os usuários naveguem facilmente entre as etapas e façam as correções necessárias. Anteriormente, esses títulos/links estavam ocultos na exibição móvel, dificultando para os usuários saber sua etapa atual ou voltar às etapas anteriores.

_AC-7962 - [Problema do GitHub](https://github.com/magento/magento2/issues/36856) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36982)_

#### cliente Pedidos consulta comentários de remessa created_at é retornado em +0 fuso horário não no fuso horário configurado de armazenamento

O sistema agora exibe corretamente o campo &quot;created_at&quot; a partir dos comentários de remessa no fuso horário configurado do cliente ao usar a consulta Pedidos do cliente. Anteriormente, o campo &quot;created_at&quot; era exibido no fuso horário +0, independentemente do fuso horário configurado pelo cliente.

_AC-8109 - [Problema do GitHub](https://github.com/magento/magento2/issues/36947) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37642)_

#### i18n:collect-phrases interrompe a integridade das traduções

O comando `bin/magento i18n:collect-phrases -o` agora coleta e adiciona corretamente novas frases dos arquivos JavaScript e .phtml, garantindo que as traduções sejam refletidas com precisão no arquivo de tradução. Anteriormente, o sistema não conseguia incluir frases de tradução de várias linhas de arquivos JavaScript e frases de arquivos .phtml no arquivo de tradução, resultando em traduções incompletas ou incorretas.

_AC-9843 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### O apóstrofo no nome da exibição de armazenamento é substituído por &#039;

Os filtros de exibição de armazenamento da grade agora exibem corretamente apóstrofos

_ACP2E-2787 - [Problema do GitHub](https://github.com/magento/magento2/issues/38395) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### Falha no upload do Favicon para validar arquivos .ico

O erro de validação de arquivo foi atualizado para &quot;Falha na validação do arquivo. Verifique as configurações de processamento da imagem na configuração da loja.&quot; Anteriormente, era simplesmente &quot;Falha na validação do arquivo&quot;.

_ACP2E-2847 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### A Galeria no PageBuilder está mostrando a miniatura de imagem antiga em vez da imagem recém-carregada

Gere visualizações de imagem novamente para imagens excluídas e recarregadas com o mesmo nome por meio da galeria de mídia no conteúdo do page builder.

_ACP2E-2957 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/001e5188)_

#### Salvar produto por usuário administrador com escopo de função diferente substitui/exclui informações de produto relacionadas no produto

Anteriormente, antes da correção, os produtos relacionados eram redefinidos e ficavam vazios quando o usuário administrador secundário clicava no botão Salvar sem alterar no produto relacionado. Após essa correção, o usuário administrador secundário clica no botão Salvar e o produto não é redefinido e é salvo com sucesso.

_ACP2E-2978 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### Não é possível exportar mais de 200 pedidos

Os limites de servidor para o tamanho da solicitação de IDs selecionadas enviadas anteriormente foram negligenciados ao alterar a solicitação HTTP do GET para POST para corrigir o problema. Anteriormente, devido às limitações do servidor para o tamanho de solicitação do GET, o problema era encontrado.

_ACP2E-3033 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Mensagem de validação da página de check-out incorreta.

Se qualquer campo obrigatório estiver vazio, como &quot;endereço&quot;, a validação do lado do servidor não exibirá a mensagem. A validação do lado do cliente garantirá que a notificação de erro do campo obrigatório seja exibida, informando &quot;Este campo é obrigatório&quot;. Anteriormente, a mensagem &quot;o endereço é obrigatório&quot; era exibida se qualquer campo obrigatório ficasse vazio, além da mensagem de validação do lado do cliente.

_ACP2E-3037 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### Problema de modelo de redefinição de senha com o usuário administrador

O problema foi resolvido usando a chave correta, que agora inclui o nome de usuário administrador no modelo de email e conclui o assunto corretamente. Anteriormente, o problema vinha de uma chave desatualizada que estava sendo usada.

_ACP2E-3125 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Barras duplas no URL do segmento do cliente

Barras duplas não aparecem no URL quando &quot;Redefinir filtro&quot; é clicado na grade.

_ACP2E-3149 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### O COD não está disponível para países específicos permitidos

Agora o dinheiro na entrega está disponível para países específicos permitidos sempre que necessário e   O AC-3216 está funcionando como esperado.

_ACP2E-3171 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Não é possível atualizar o status do Pedido criado pelo Cliente

&quot;Agora podemos atualizar os status de pedidos criados de forma personalizada, enquanto anteriormente, o status só podia ser alterado se o status atual fosse &quot;processando&quot; ou &quot;fraude&quot;.&quot;

_ACP2E-3178 - [Problema do GitHub](https://github.com/magento/magento2/issues/38659) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### O estado do endereço de entrega não é atualização automática

Antes da correção, a região do endereço de entrega (ou id da região) não estava sincronizada com as informações de cobrança do endereço. Agora, a região do endereço de entrega e a ID da região são atualizadas corretamente quando as informações de endereço de cobrança são alteradas.

_ACP2E-3294 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### O botão Redefinir não funciona em Adicionar/Editar usuário administrador

Anteriormente, o botão Redefinir não funcionava na página Adicionar/Editar usuário administrador. Agora, no painel Administrador, em Sistema -> Permissões -> Todos os usuários, o botão Redefinir funcionará corretamente na página Adicionar/Editar usuário administrador.

_ACP2E-3364 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Detecção incorreta de roteamento de URL administrativo do Magento e erros de CORS

Após a correção, se o domínio de administrador personalizado for um subdomínio do domínio principal, o administrador poderá ser acessado somente pelo subdomínio configurado.

_ACP2E-3373 - [Problema do GitHub](https://github.com/magento/magento2/issues/37663) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Validação interrompida para &#39;Quantidade máxima permitida no carrinho de compras&#39;

Anteriormente, quando colocávamos `Maximum Qty Allowed in Shopping Cart` vazio, ele não gerava nenhuma exceção, embora um valor vazio não fosse aceito aqui. Depois que essa correção for aplicada, colocar uma string vazia gerará exceções e não permitirá salvar o produto.

_ACP2E-3392 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Problema na interface de visualização do Pagebuilder] Os botões na coluna do Page Builder não estão alinhados corretamente

Os botões nas colunas do Page Builder agora estão alinhados corretamente. Anteriormente, eles estavam desalinhados nas colunas do Page Builder.

_ACP2E-3408 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_

#### O relatório Produtos encomendados não está exportando. Erro 404 em vez disso.

A exportação de relatórios solicitados de produtos para CSV e XML agora funciona conforme esperado

_ACP2E-3431 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### Erro TinyMCE JS no console após a ativação da minificação Js com o modo de produção

Anteriormente, ativar a minificação do JavaScript no modo de produção no painel de administração fazia com que erros do JavaScript relacionados ao TinyMCE 6 aparecessem no console do navegador, afetando a funcionalidade e a experiência do usuário. Agora, esse problema foi resolvido, garantindo que o TinyMCE 6 funcione sem problemas sem gerar erros, mesmo quando a minificação JS estiver ativada.

_ACP2E-3457 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### Solicitação de alterações adicionais para concluir a correção do ACP2E-3375

&quot;-

_ACP2E-3459 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Ativação automática de novas permissões de ACL

Novas permissões adicionadas a módulos personalizados não concederão mais acesso automaticamente a todas as funções de usuário existentes, a menos que estejam configuradas explicitamente.

_ACP2E-3503 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### O Relatório de usuário do log de ações do administrador não mostra detalhes para adminhtml_user_delete

O adminhtml_user_delete agora registra corretamente detalhes importantes. Anteriormente, os logs não eram gerados para exclusões de usuários.

_ACP2E-3509 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4de008a9)_

#### A regra do carrinho com a condição de remessa não se aplica ao fazer o pedido do administrador

Anteriormente, se a regra de preço do carrinho tiver um desconto de método de envio com o cupom, ela não poderá ser aplicada por meio da interface do administrador. Depois que essa correção for aplicada, o desconto da regra de preço do carrinho com um cupom para um método de envio específico será aplicado com êxito da interface do administrador.

_ACP2E-3536 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a52ff98f) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/11ce816b)_

#### O código HEX [FRESH] não está sendo atualizado corretamente na AMOSTRA

O código HEX inserido manualmente pelo usuário no seletor de cores da Amostra visual não é mais alterado pelo sistema. Anteriormente, alguns códigos HEX tinham pequenos ajustes devido a erros de conversão entre modelos de cores.

_ACP2E-3559 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/344fce23) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/1ef984c0)_

### Interface do administrador, B2B

#### O logon B2B como cabeçalho do cliente ainda tem a marca Magento

Anteriormente, o cabeçalho da loja exibe &quot;Agora você está conectado como &lt;nome do cliente> na &lt;nome da loja>&quot; com a marca Magento. Que agora foi corrigida e o cabeçalho é exibido com a marca ADOBE.

_AC-13628 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Interface do administrador, Métodos de pagamento/pagamento, Pedido

#### Autorização de Transação Não Exibida na Guia Transação Após a Ordem do Botão Inteligente do PayPal

O sistema agora exibe corretamente a autorização da transação na guia Transação depois que um pedido é feito usando o botão inteligente do PayPal. Anteriormente, a transação de autorização não aparecia na guia Transação após clicar no botão &quot;Autorizar&quot; e nenhuma nova transação do tipo &quot;Autorização&quot; era criada.

_AC-13520 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Interface do administrador, desempenho

#### Após a atualização para 2.4.5-p8, ocorrem erros 500 ao criar um pedido do administrador

Anteriormente, ao ativar a minificação do HTML, um pedido do administrador não podia ser feito. Agora, com a minificação do HTML ativada, o pedido do administrador pode ser feito com sucesso.

_ACP2E-3169 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Interface do administrador, Envio

#### A contagem de código do cupom não é atualizada no   A coluna &quot;Tempo usado&quot; na guia Gerenciar códigos de cupom se um pedido for feito com envio múltiplo.

Anteriormente, quando um pedido era feito com envio múltiplo, a contagem de código do cupom não era atualizada na coluna &quot;Tempo usado&quot; na guia Gerenciar códigos de cupom. Agora, a contagem correta é exibida no &quot;Tempo usado&quot; refletindo os valores desejados com o envio múltiplo.

_ACP2E-2519 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4745100c)_

### Interface do administrador, preparo e visualização

#### [Nuvem] A remoção do modelo com imagens ausentes faz com que o pub/media seja excluído

Antes dessa correção, se o nome da imagem de visualização não estava presente em um modelo do pagebuilder, a pasta pub/media foi excluída. Após a correção, somente o modelo será excluído e a imagem de pré-visualização, se encontrada.

_ACP2E-3424 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/Relatórios

#### Erro do Google Analytics CSP https://region1.analytics.google.com

O sistema agora permite corretamente conexões com &quot;https://region1.analytics.google.com&#39;&quot; quando o Google Analytics é ativado, evitando erros da Política de segurança de conteúdo (CSP). Anteriormente, ativar o Google Analytics e visualizar o site da UE resultava em erros no console da CSP devido a uma recusa de conexão com &quot;https://region1.analytics.google.com&#39;&quot;.

_AC-9922 - [Problema do GitHub](https://github.com/magento/magento2/issues/37750) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38991)_

#### O Relatório avançado não está funcionando

O sistema agora oferece suporte à geração de arquivos de dados de Relatórios avançados para conjuntos de dados extragrandes ao carregar e gravar relatórios em lotes de 10.000. Anteriormente, o módulo Relatórios avançados não conseguia gerar arquivos de dados para conjuntos de dados extragrandes, causando erros &quot;O servidor MySQL desapareceu&quot; durante a execução do trabalho analytics_collect_data cron.

_ACP2E-2570 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Problemas de visibilidade do intervalo de datas do relatório de produtos solicitados pelo administrador.

O usuário poderá selecionar qualquer data no relatório de produtos solicitados. Anteriormente, após a atualização de uma tabela, selecionar a data &#39;DE&#39; redefinirá a data &#39;ATÉ&#39;.

_ACP2E-3080 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Cabeçalhos curl incorretos, fazendo com que `newrelic:create:deploy-marker` não funcione

O sistema agora formata corretamente os cabeçalhos curl, permitindo que o comando `newrelic:create:deploy-marker` crie com êxito um marcador de implantação no New Relic. Anteriormente, cabeçalhos curl incorretos impediam a criação de um marcador de implantação no New Relic.

_ACP2E-3096 - [Problema do GitHub](https://github.com/magento/magento2/issues/37641) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### O monitoramento do navegador NewRelic pelo script inlineJS causa erros de CSP

Os scripts de monitoramento do navegador NewRelic agora são inseridos pelo aplicativo, em vez do agente APM, para conformidade com a CSP (Política de segurança de conteúdo). Anteriormente, os scripts de monitoramento do navegador NewRelic inseridos pelo agente APM não eram compatíveis com o CSP e faziam com que os scripts não fossem executados.

_ACP2E-3183 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### INSERIR consultas na tabela sales_bestsellers_aggregated_daily torna-se lento em projetos com grande volume de ordens de venda

Anteriormente, o relatório diário agregado de best-sellers demorava muito para ser gerado para um grande volume de pedidos feitos. Agora o relatório é gerado em tempo hábil.

_ACP2E-3189 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Relatórios de pedidos mostrando o símbolo de moeda errado

O símbolo de moeda para valores de pedidos no Relatório de pedidos foi retirado incorretamente de moeda/opções/base. Agora foi corrigido para usar moeda/opções/padrão para obter relatórios precisos.

_ACP2E-3276 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Nuvem] Cálculos incorretos no Relatório de Uso do Cupom

O total de vendas na grade do relatório de cupom agora é calculado com precisão, incorporando a &quot;Quantia de Compensação de Imposto sobre Desconto&quot; e a &quot;Quantia de Compensação de Imposto sobre Desconto de Remessa&quot;. Anteriormente, esses valores estavam ausentes no cálculo, gerando discrepâncias entre o total de vendas e os dados da ordem de venda.

_ACP2E-3302 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Problemas com &quot;&lt;project_id>/var/tmp&quot; compartilhado

Os arquivos temporários do Analytics DataExport usarão o diretório tmp sys, que é mais adequado para acesso e alterações frequentes. Para evitar colisões, caso várias instâncias estejam em execução no mesmo servidor, o caminho tmp foi atualizado para usar a id exclusiva de uma instância

_ACP2E-3339 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/Relatórios, B2B

#### B2B - o mapa de site inclui produtos/categorias não atribuídos ao Catálogo compartilhado

Restrinja as categorias e os produtos gerados pelo mapa de site às categorias e aos produtos atribuídos somente ao catálogo público compartilhado e/ou à configuração de permissão da categoria de catálogo.

_ACP2E-2300 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/Relatórios, Cloud

#### A Magento descarta a maioria das transações New Relic cron #34108

A AC está relatando corretamente as transações relacionadas ao trabalho do cron para a NewRelic. Anteriormente, algumas transações relacionadas a trabalhos do cron eram mostradas como &quot;OtherTransaction/Action/unknown&quot; no NR

_ACP2E-3067 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Métrica no NR pode induzir em erro para transações de segundo plano- Acompanhamento da ACP2E-3067

As transações em segundo plano (cron) usarão o nome do aplicativo New Relic definido nas configurações

_ACP2E-3187 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

#### Os produtos atribuídos ao catálogo compartilhado não refletem no front-end quando o índice parcial é executado

Os produtos atribuídos ao catálogo compartilhado por meio da API REST agora ficam visíveis imediatamente na loja após a conclusão da indexação parcial. Anteriormente, os Produtos eram visíveis somente após uma reindexação completa.

_ACP2E-2139 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Bordas desnecessárias na seção Meus pedidos

Anteriormente, era criado um contêiner adicional (referências de pedido) que aplicava classes CSS adicionais, o que fazia com que linhas de borda desnecessárias aparecessem abaixo do número do pedido na seção Meus pedidos, que não está visível agora.

_ACP2E-3044 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### sales_clean_quotes cron exclui cotações de ordens de compra ainda aprovadas

As cotações usadas em ordens de compra agora não serão excluídas pelo trabalho cron sales_clean_quotes

_ACP2E-3247 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

### B2B, Estrutura

#### Filtrar a grade da empresa e tentar exportar em grade CSV causará falha e lançará exceção

O sistema agora permite a exportação bem-sucedida dos dados da grade Empresas em CSV no painel de administração, mesmo quando filtros como &quot;Saldo pendente&quot; e &quot;Tipo de empresa&quot; são aplicados. Anteriormente, a aplicação de determinados filtros e a tentativa de exportar os dados da grade resultavam em uma falha e em uma exceção.

_AC-9607 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

### Pacote

#### Contagem de mensagens de erro de validação de pacote de vitrine maior que 1

O sistema agora exibe apenas uma mensagem de erro de validação quando o botão &#39;Adicionar ao carrinho&#39; é clicado sem selecionar nenhuma opção de caixa de seleção para um produto incluído. Anteriormente, o sistema exibia várias mensagens de erro de validação para cada caixa de seleção não selecionada.

_AC-10826 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ea26621)_

### Carrinho e saída

#### A exceção não é tratada corretamente ao adicionar um produto ao carrinho na página comparar produtos

O sistema agora lida corretamente com exceções ao adicionar um produto ao carrinho na página comparar produtos, exibindo uma mensagem do gerenciador de mensagens no controlador. Anteriormente, uma exceção resultava no retorno de uma página codificada em JSON, em vez de ser capturada e manipulada corretamente.

_AC-10660 - [Problema do GitHub](https://github.com/magento/magento2/issues/38200) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38257) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### GTag não envia preços de transação e totais.

O sistema agora envia corretamente os preços e os totais da transação para a tag da Google quando a GTag está ativada, garantindo um rastreamento preciso dos dados de comércio eletrônico. Anteriormente, a moeda estava sendo enviada incorretamente como parte dos pedidos &quot;all&quot;, em vez de ser associada ao pedido individual.

_AC-10698 - [Problema do GitHub](https://github.com/magento/magento2/issues/37348) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37504) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37349)_

#### [Problema] [Check-out] Diretivas de dependência atualizadas no modelo de email de pagamento com falha

O sistema agora omite corretamente o endereço de envio e o método de envio do template de email de pagamento com falha para produtos virtuais, garantindo que apenas as informações relevantes sejam incluídas no email. Anteriormente, o e-mail de pagamento com falha para produtos virtuais incluía incorretamente o endereço e o método de envio.

_AC-11641 - [Problema do GitHub](https://github.com/magento/magento2/issues/32781) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32511)_

#### O logon do Magento 2 na finalização da compra com um cliente existente fornece um erro de console no navegador Firefox

O sistema agora permite que os usuários façam logon durante o processo de finalização sem encontrar erros no console do navegador Firefox. Anteriormente, tentar fazer logon como um cliente existente durante a finalização da compra resultaria em um erro de console no Firefox.

_AC-11717 - [Problema do GitHub](https://github.com/magento/magento2/issues/38557) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39509)_

#### [Problema] Regressão de regras de vendas em 2.4.7

O sistema agora valida corretamente as regras de vendas, impedindo a aplicação de um código de cupom a um carrinho quando a condição do produto não corresponde a nenhum nome de produto. Anteriormente, era possível aplicar uma regra de vendas e conceder um desconto no valor do envio mesmo quando a condição do produto não correspondia a nenhum nome de produto.

_AC-11876 - [Problema do GitHub](https://github.com/magento/magento2/issues/38671) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Problema] Cálculo de CartFixed de regra de vendas: valor de desconto incorreto

O sistema agora calcula corretamente o valor do desconto para regras de vendas com valores fixos do carrinho, garantindo que os descontos precisos sejam aplicados independentemente das alterações nos itens do carrinho. Anteriormente, o valor do desconto podia variar incorretamente quando os itens do carrinho eram alterados, às vezes resultando em descontos significativamente maiores do que o esperado.

_AC-11914 - [Problema do GitHub](https://github.com/magento/magento2/issues/38694) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### [Problema] O carregador bloqueia os métodos de envio depois que o CEP é alterado, as regras de validação de taxas de envio

O sistema agora lida corretamente com métodos de envio personalizados sem regras de validação de taxas de envio, garantindo que o carregador não bloqueie os métodos de envio depois que o código postal for alterado no endereço de envio durante a finalização da compra. Anteriormente, alterar o código postal no endereço de entrega durante a finalização da compra fazia com que o carregador bloqueasse os métodos de entrega e não desaparecesse quando métodos de entrega personalizados sem regras de validação de taxas de entrega fossem usados.

_AC-11993 - [Problema do GitHub](https://github.com/magento/magento2/issues/38742) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### O recurso de código do cupom não está funcionando corretamente na página de check-out do Magento 2.4.7

O sistema agora habilita o campo de entrada de código de desconto/cupom na página de check-out para produtos virtuais e baixáveis, permitindo que os usuários apliquem códigos de desconto conforme esperado. Anteriormente, a entrada do código de desconto/cupom era desativada e o texto do título do botão era exibido como &quot;Cancelar cupom&quot;, impedindo que os usuários aplicassem códigos de desconto.

_AC-12170 - [Problema do GitHub](https://github.com/magento/magento2/issues/38826) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### A caixa de seleção dos Termos e condições não permite o HTML na loja

O sistema agora oferece suporte à formatação HTML no texto da caixa de seleção &quot;Termos e condições&quot; na loja, permitindo mais personalização e legibilidade. Anteriormente, o texto da caixa de seleção era exibido em formato de texto sem formatação, ignorando as tags HTML usadas.

_AC-12479 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### A regra de preço do carrinho criada para o usuário conectado é aplicada incorretamente para o usuário não conectado

O sistema agora remove corretamente a regra de preço do carrinho para usuários conectados quando eles são automaticamente desconectados devido à expiração do cookie, garantindo que o desconto não seja aplicado a usuários não conectados. Anteriormente, a regra de preço do carrinho ainda era aplicada mesmo quando o usuário estava desconectado, resultando em um desconto incorreto aplicado a usuários não conectados.

_AC-12541 - [Problema do GitHub](https://github.com/magento/magento2/issues/38944) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problema] [RECURSO]: otimização de desempenho de grandes carrinhos de compras, evitando...

O sistema agora otimiza o desempenho de grandes carrinhos de compras, evitando chamadas getActions duplicadas, melhorando a velocidade e a eficiência das operações de carrinho de compras. Anteriormente, em um carrinho de compras com vários itens, a função getActions era chamada várias vezes, retardando o desempenho do sistema.

_AC-13302 - [Problema do GitHub](https://github.com/magento/magento2/issues/39292) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39290)_

#### IVA de tradução no renderizador de endereço

O sistema agora permite a tradução do texto &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; nos renderizadores de endereço, permitindo que os usuários traduzam esses termos para o idioma específico da loja. Anteriormente, esses termos não podiam ser traduzidos, forçando os usuários a fazerem uma solução alternativa.

_AC-8103 - [Problema do GitHub](https://github.com/magento/magento2/issues/36942) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36943)_

#### Pedidos duplicados com a mesma ID de cotação ao mesmo tempo com poucas diferenças de tempo

Correção do problema em que os clientes do Adobe Commerce encontravam pedidos duplicados feitos com a mesma QuoteID

_ACP2E-2055 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Carrinho de compras persistente apagado durante a etapa de finalização

Após a correção, selecionar o método de pagamento durante o check-out sem estar conectado não encerra a sessão persistente.

_ACP2E-2470 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Reordenar adiciona produto não atribuído ao carrinho

Anteriormente, para as diferentes lojas, os produtos podem ser resolicitados da outra loja. Depois que essa correção for aplicada somente à mesma loja, o mesmo produto de escopo poderá ser reordenado quando o compartilhamento de conta do cliente for habilitado

_ACP2E-2518 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### No admin, o &quot;Carrinho de compras&quot; no lado esquerdo não é atualizado ao selecionar os itens e &quot;Mover para o carrinho de compras&quot; no lado direito

O &quot;Carrinho de compras&quot; no lado esquerdo é atualizado ao selecionar os itens e &quot;Mover para o carrinho de compras&quot; no lado direito no lado do administrador. Anteriormente, essa funcionalidade não funcionava porque os itens do carrinho transformados não ficavam vazios na sessão.

_ACP2E-2620 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### [Regra de Vendas da &lbrace;Cloud] não aplicada à primeira ordem de Envio Múltiplo

Após a correção, o desconto é mostrado corretamente para cada pedido da mesma cotação de remessa múltipla.

_ACP2E-2646 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### As solicitações paralelas de produção [Cloud] para adicionar o mesmo produto ao carrinho resultam em dois itens separados na API de repouso do carrinho

O sistema agora processa corretamente várias solicitações paralelas para adicionar o mesmo produto ao carrinho em um único item de linha, impedindo a criação de itens de linha separados para o mesmo SKU. Anteriormente, fazer solicitações paralelas para adicionar o mesmo produto ao carrinho por meio da API REST resultava em vários itens de linha para a mesma SKU.

_ACP2E-2664 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Obtendo Não é possível enviar o cookie. Tamanho de &quot;mage-messages&quot; ao tentar reordenar

O processo de reordenação não gerará seus próprios erros agora. Ele dependerá das verificações de item integradas à lista do carrinho.

_ACP2E-2704 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### O endereço de entrega padrão não está selecionado no check-out

O endereço de entrega padrão agora está sendo selecionado para o evento no contexto da pesquisa de endereço ativada.

_ACP2E-2798 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Problema da API graphql addProductsToCart [CLOUD] com opção personalizada

O GraphQL adiciona ao carrinho corretamente o mesmo produto com diferentes opções personalizadas

_ACP2E-2897 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Vários endereços adicionados à conta ao fazer check-out como novo cliente

O sistema agora salva um novo endereço do cliente apenas uma vez se o pedido falhar ao ser criado, impedindo a criação de vários endereços idênticos no caso de erros de posicionamento do pedido. Anteriormente, o sistema salvava um novo endereço sempre que uma tentativa de colocação de pedido era feita, independentemente de o pedido ter sido criado com sucesso ou não.

_ACP2E-2923 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/001e5188) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/2ebcef39)_

#### A reorganização do pedido do cliente por meio do formulário de pedido de convidado resulta em um carrinho vazio

Anteriormente, ao fazer um novo pedido por meio da página Pedidos e devoluções, o cliente era redirecionado para a página de login. Depois que essa correção for aplicada, o cliente registrado será redirecionado corretamente para a página Exibir carrinho ao fazer um novo pedido. O fluxo funciona da mesma forma que os clientes convidados.

_ACP2E-3004 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Usuário administrador com recursos de função limitada não consegue visualizar carrinhos de compras

Anteriormente, o administrador restrito não podia ver o carrinho de compras abandonado do painel de administração de um site associado. Depois que essa correção for aplicada, o administrador restrito poderá ver o carrinho de compras abandonado no painel de administração.

_ACP2E-3025 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Grande quantidade de desempenho de SKU de pedido rápido da [Cloud]

O desempenho do check-out foi aprimorado quando os atributos usados nas condições das regras de preço do carrinho não estão presentes para todos os produtos e quando o recurso MAP (Preço mínimo anunciado) está habilitado.

_ACP2E-3176 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Itens duplicados no carrinho

O sistema agora processa corretamente várias solicitações paralelas para adicionar o mesmo produto ao carrinho em um único item de linha, impedindo a criação de itens de linha separados para o mesmo SKU. Anteriormente, fazer solicitações paralelas para adicionar o mesmo produto ao carrinho na loja resultava em vários itens de linha para o mesmo SKU.

_ACP2E-3211 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### A confirmação do email do pedido de check-out é enviada para emails inseridos em Nome/Sobrenome

A confirmação do email do pedido de check-out, que foi enviada anteriormente quando um padrão semelhante a um email foi inserido nos campos Nome e Sobrenome, não está mais sendo enviada.

_ACP2E-3296 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Obter atualização de formulário de endereço de entrega com endereço errado

shippingAddressFromData agora é salvo no armazenamento local por site. Anteriormente, um endereço do site errado podia ser preenchido automaticamente no formulário de endereço de entrega durante o check-out se um código de loja fosse usado no URL e o check-out fosse iniciado de vários sites durante a mesma sessão de convidado.

_ACP2E-3402 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Produto de cartão-presente | A Mesclagem de Carrinhos está mesclando Cartões-presente

Os produtos de cartão-presente agora são mesclados corretamente no carrinho

_ACP2E-3407 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### A persistência do carrinho não é respeitada ao fazer logoff

Adição da funcionalidade ausente Lembre-se de mim do logon do cliente para pop-up de autenticação e logons de check-out.

_ACP2E-3415 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/344fce23)_

#### Os dados de cota existentes não são atualizados/não estão visíveis. Em vez disso, crie um novo registro de cota quando trigger_recollect = 1

Os itens do carrinho de compras do cliente não desaparecem mais como resultado da exclusão de um produto após sua adição ao carrinho.

_ACP2E-3488 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [NUVEM] Reordena a funcionalidade do botão

Reordenar um pedido na área de administrador agora adicionará produtos com estoque à cotação, mesmo que haja alguns produtos no pedido original que não tenham mais estoque. Antes da correção, nenhum produto estava sendo adicionado à nova cotação se o produto sem estoque estivesse no pedido original.

_ACP2E-3618 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### As lojas de pesquisa não estão funcionando com o código postal

A pesquisa de locais de recebimento por código postal não estava funcionando corretamente para localizações em holandês. Após a correção, a pesquisa de localização de coleta fornecerá resultados com base no código postal.

_ACP2E-3622 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Carrinho e check-out, check-out/check-out de uma página

#### [BUG Aleatório] O campo Email não é renderizado ou leva muito tempo para ser exibido na página Envio de check-out ou Pagamento

O Commerce agora renderiza o campo **[!UICONTROL Email]** nas páginas de envio e pagamento de check-out conforme esperado. Anteriormente, esse campo estava ausente ou era renderizado lentamente.

_AC-9386 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e1babcfd)_

### Carrinho e check-out, pedido

#### Datepicker para produto com várias opções personalizáveis com campos de data que não funcionam ao fazer pedido do administrador

O sistema agora exibe corretamente o seletor de datas para todos os campos de data ao configurar um produto com várias opções de data personalizáveis no processo de criação do pedido de administrador. Anteriormente, o seletor de datas era exibido apenas para o primeiro campo de data, deixando os campos restantes sem um seletor de datas.

_ACP2E-3097 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Carrinho e check-out, envio

#### Compra instantânea &quot;envio mais barato&quot; quebrada para produtos configuráveis

O recurso Compra instantânea selecionou incorretamente a opção de Entrega na loja mais cara para produtos configuráveis em vez do método de taxa fixa mais barato. Essa correção garante que o método de envio correto seja escolhido com base no preço real.&quot;

_AC-12119 - [Problema do GitHub](https://github.com/magento/magento2/issues/38811) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38819) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/29fe9097)_

### Catálogo

#### A limpeza da tabela de banco de dados cron_schedule não limpa trabalhos não existentes

O sistema agora limpa automaticamente a tabela de banco de dados cron_schedule, removendo entradas de tarefas que não existem mais no sistema. Isso garante o desempenho ideal, mantendo um número mínimo de linhas na tabela. Anteriormente, as entradas para trabalhos de módulos inativos ou removidos não eram limpas, resultando em acúmulo desnecessário de dados na tabela cron_schedule.

_AC-10910 - [Problema do GitHub](https://github.com/magento/magento2/issues/38217) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38693)_

#### A camada de preço não está sendo excluída do produto configurável

Agora, o sistema remove corretamente o preço de nível de um produto quando ele é convertido de um produto simples para um produto configurável, garantindo uma exibição precisa do preço no front-end. Anteriormente, o preço de nível de um produto configurável não era excluído quando um produto era convertido de um produto simples em um produto configurável, resultando em uma incompatibilidade no preço exibido.

_AC-10953 - [Problema do GitHub](https://github.com/magento/magento2/issues/38390) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38427)_

#### Descrição da categoria O WYSIWYG está vazio na loja não padrão

Agora, o sistema salva e exibe corretamente a descrição da categoria no editor do WYSIWYG ao editar uma categoria no nível de exibição da loja. Anteriormente, o editor do WYSIWYG parecia vazio após salvar uma descrição de categoria no nível de exibição de loja.

_AC-11804 - [Problema do GitHub](https://github.com/magento/magento2/issues/38622) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38623)_

#### Impossível reordenar produtos configuráveis com uma caixa de seleção marcada opção personalizada

O sistema agora processa corretamente o reordenamento de produtos configuráveis com uma única opção personalizada de caixa de seleção selecionada, permitindo a criação bem-sucedida da cesta. Anteriormente, tentar reordenar esses produtos resultava em um erro e impedia que itens fossem adicionados ao carrinho.

_AC-11970 - [Problema do GitHub](https://github.com/magento/magento2/issues/38736) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1d144bce)_

#### [Problema] Corrigir o texto do item de filtro na navegação em camadas

O sistema agora usa corretamente as palavras &quot;item&quot; e &quot;itens&quot; no item do filtro de navegação em camadas, melhorando a clareza e a precisão das descrições do filtro. Anteriormente, essas palavras eram usadas incorretamente, resultando em possível confusão para os usuários que navegavam pelas opções de filtro.

_AC-12076 - [Problema do GitHub](https://github.com/magento/magento2/issues/38789) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37852)_

#### O Formato de Data e Hora para a Opção Personalizada Não Funciona

O sistema agora aplica corretamente o formato de data configurado às opções personalizadas de produto do tipo Data, garantindo que o formato de data seja exibido corretamente no front-end. Anteriormente, as alterações na configuração do formato de data não refletiam no front-end para opções personalizadas de produto do tipo Data.

_AC-12164 - [Problema do GitHub](https://github.com/magento/magento2/issues/32990) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38925)_

#### Opções suspensas ausentes

O sistema agora exibe corretamente todos os valores na lista suspensa ao criar um novo atributo com mais de 20 valores. Anteriormente, apenas os primeiros 20 valores ou outros valores de página selecionados eram exibidos, fazendo com que os valores restantes não fossem exibidos.

_AC-13068 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] Use a ID da loja atual para o cache de tempo de execução de categoria

O sistema agora usa corretamente a ID da loja atual para o cache de tempo de execução da categoria, impedindo a substituição de dados quando a emulação é usada ou o código personalizado salva a categoria em lojas diferentes. Anteriormente, o objeto armazenado em tempo de execução podia ter vindo do armazenamento errado, levando à substituição de dados.

_AC-13296 - [Problema do GitHub](https://github.com/magento/magento2/issues/39310) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36394)_

#### bin/magento sampledata:deploy —no-update gera uma exceção

O sistema agora aceita corretamente um valor booleano ao usar a opção —no-update no comando sampledata:deploy, evitando quaisquer erros durante a implantação dos dados de amostra. Anteriormente, um erro era gerado ao usar esse comando, pois o sistema esperava incorretamente um valor inteiro.

_AC-13324 - [Problema do GitHub](https://github.com/magento/magento2/issues/39344) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39345)_

#### [Problema] Corrigir o uso do tipo de cache EAV

O sistema agora usa corretamente o tipo de cache EAV em todos os locais relevantes, garantindo um armazenamento consistente e eficiente dos dados em cache. Anteriormente, o tipo de cache EAV não era usado de forma consistente, resultando em possíveis ineficiências e inconsistências no armazenamento em cache de dados.

_AC-13355 - [Problema do GitHub](https://github.com/magento/magento2/issues/32322) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/31264)_

#### A Pesquisa Avançada do Catálogo com dados vazios vai para a página de resultados da pesquisa[2.4.dev branch]

O sistema agora retém corretamente os usuários na página Pesquisa avançada e exibe uma mensagem de erro quando eles tentam realizar uma pesquisa sem inserir dados. Anteriormente, executar uma pesquisa vazia redirecionava os usuários para a página Pesquisa avançada de catálogo com uma mensagem solicitando que eles modificassem a pesquisa.

_AC-13596 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### Layout do produto [Problema] com base no attribute_set

O sistema agora permite o ajuste do layout do produto com base no conjunto de atributos, fornecendo uma maneira mais prática e eficiente de gerenciar a exibição do produto na loja de front-end. Anteriormente, o layout só podia ser ajustado por SKU ou por tipos de produto, o que nem sempre era prático para muitos produtos ou artigos específicos.

_AC-13622 - [Problema do GitHub](https://github.com/magento/magento2/issues/38790) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36244)_

#### Chave exclusiva ausente na tabela eav_attribute_option_value

O sistema agora inclui uma chave exclusiva nas colunas &quot;option_id&quot; e &quot;store_id&quot; na tabela &quot;eav_attribute_option_value&quot;, evitando a possibilidade de uma opção ter vários valores para a mesma exibição de armazenamento. Anteriormente, um código com falha podia resultar em uma opção com vários valores para a mesma visualização de loja, causando problemas ao editar produtos ou atributos.

_AC-6738 - [Problema do GitHub](https://github.com/magento/magento2/issues/24718) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/28796)_

#### [Problema] Use a classe de visibilidade para o indexador de produto da categoria, em vez de valores codificados

O sistema agora usa a classe de visibilidade para o indexador de produto da categoria em vez de valores codificados, melhorando a modularidade. Anteriormente, valores codificados eram usados no indexador de produto da categoria, limitando a flexibilidade e adaptabilidade.

_AC-8297 - [Problema do GitHub](https://github.com/magento/magento2/issues/37200) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37199)_

#### O código de moeda não é alterado no widget Novo produto

O sistema agora atualiza corretamente o código monetário no widget Novo produto quando a moeda é alterada no front-end, garantindo a consistência na exibição da moeda em todo o site. Anteriormente, alterar a moeda no front-end não afetava o código de moeda exibido no widget Novo produto.

_AC-9375 - [Problema do GitHub](https://github.com/magento/magento2/issues/37898) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37899)_

#### O preço normal não aparece na PLP para o produto configurável

O preço normal agora é exibido nas páginas de listagem de produtos para produtos configuráveis que têm produtos secundários com preço especial.

_ACP2E-2224 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### As informações das ações não são exibidas na grade de merchandising visual

O estoque agora é exibido de acordo com o armazenamento selecionado.

_ACP2E-2478 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

#### O conteúdo do widget não é atualizado na página cms

O sistema agora atualiza o conteúdo do widget em uma página do CMS quando um produto é definido como novo e salvo, garantindo que a página exiba a coleção de produtos atualizada. Anteriormente, a página não era atualizada para mostrar o novo produto devido às identidades de cache incorretas usadas para o widget no cache.

_ACP2E-2621 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Problemas ao salvar preços avançados de pacotes de produtos

Melhoria no desempenho da economia de produtos do pacote.

_ACP2E-2630 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [No local] O processo de reindexação é ineficiente ao criar Regras de Preço de Catálogo

Agora, salvar a regra de preço de catálogo não invalidará os indexadores; em vez disso, ela reindexará somente os produtos afetados

_ACP2E-2652 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Atualização da hora dos atributos de produto do tipo Data e hora por meio da importação de CSV

Agora, os atributos datetime terão parte do tempo nos dados exportados. Também será possível atualizar o horário desses atributos usando importar. Além disso, se &quot;Compartimento de campos&quot; estiver ativado, os valores de atributo na coluna &quot;additional_attributes&quot; serão colocados entre aspas duplas.

_ACP2E-2679 - [Problema do GitHub](https://github.com/magento/magento2/issues/38306) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Nenhuma mensagem de erro apropriada quando a ID do site está incorreta na solicitação

Agora, a mensagem de erro apropriada foi adicionada para ser exibida quando a ID do site estiver incorreta na solicitação. Anteriormente, não havia validação quando a ID do site estava incorreta na solicitação.

_ACP2E-2689 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### A imagem do produto é perdida após excluir uma Atualização agendada existente que não afeta a imagem

As imagens do produto não são removidas durante a exclusão da atualização de preparo.

_ACP2E-2785 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### [Nuvem] Preço de pacote incorreto quando usado com preços de camada

Anteriormente, ao calcular determinados descontos percentuais arredondados para até 2 pontos decimais, os preços finais do carrinho e da página de listagem de produtos/detalhes do produto eram diferentes. Depois que essa correção é aplicada, o preço final do pacote é o mesmo da página Detalhes do produto, da página Lista de produtos e da página do minicarrinho.

_ACP2E-2799 - [Problema do GitHub](https://github.com/magento/magento2/issues/38091) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### A Regra de Promoções do Catálogo não funciona com o atributo quantity_and_stock_status

O atributo quantity_and_stock_status agora será considerado pela regra de promoção do catálogo, que não foi considerada anteriormente ao gerar um novo produto pelo lado do administrador.

_ACP2E-2805 - [Problema do GitHub](https://github.com/magento/magento2/issues/35627) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/cf34971d)_

#### Os valores de coluna updated_at da entidade do produto não são atualizados durante a atualização do preço por meio da API REST

A coluna &quot;Última atualização em&quot; do produto do administrador é atualizada na data e hora apropriadas durante a atualização dos produtos existentes por meio da API REST. Anteriormente, a coluna &quot;Última atualização em&quot; não era atualizada corretamente.

_ACP2E-2837 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### É possível definir valores não exclusivos por meio da importação do produto

O sistema agora impõe corretamente a restrição de valor único para atributos exclusivos de produto durante a importação do produto, evitando valores duplicados para esse atributo. Anteriormente, era possível definir valores não exclusivos para atributos de produto configurados para terem valores exclusivos por meio da importação de produtos.

_ACP2E-2840 - [Problema do GitHub](https://github.com/magento/magento2/issues/38445) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Os produtos no front-end usam dados específicos do armazenamento quando o Modo de armazenamento único está ativado

Anteriormente, quando ativávamos o modo de armazenamento único para a exibição de armazenamento padrão, as alterações não eram migradas para o escopo no nível do site. Depois que essa correção for aplicada, ao habilitar o modo de loja única, os dados específicos da exibição da loja padrão serão sincronizados com os dados específicos do nível do site e resolverão os possíveis conflitos de produtos e categorias.

_ACP2E-2843 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Não é possível definir &quot;Padrão, Classificar por&quot; em uma categoria usando a API rest

Atualizar corretamente default_sort_by em uma categoria por meio da solicitação REST / SOAP APi

_ACP2E-2857 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### [Nuvem] O Comerciante está enfrentando problemas com a contagem da lista de desejos

Adicionar um produto à lista de desejos em uma loja não aumenta mais a contagem de listas de desejos em outras lojas abertas no mesmo navegador. Anteriormente, se ambas as lojas fossem carregadas no mesmo navegador, a contagem de listas de desejos aumentaria na outra loja também.

_ACP2E-2871 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### A página de categoria no front-end mostra slots vazios ao usar o produto de pacote

Os produtos do pacote que não podem ser vendidos no contexto da loja atual não são mais indexados.

_ACP2E-2874 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/bc37ec76)_

#### [Problema de Cotação da &lbrace;Cloud] na arquitetura de vários sites

Anteriormente, a arquitetura de vários sites com moedas e grupos de clientes diferentes não podia aplicar descontos corretamente à loja. Depois que essa correção for implementada, a arquitetura de vários sites com descontos de preço de grupo de clientes diferentes será aplicada com sucesso a diferentes lojas.

_ACP2E-2905 - [Problema do GitHub](https://github.com/magento/magento2/issues/38506) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice ao editar produtos de pacote

Não há erro de javascript no console do navegador ao excluir a opção do produto do pacote.

_ACP2E-2909 - [Problema do GitHub](https://github.com/magento/magento2/issues/38505) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### [Cloud] Pacote de produto com preço incorreto na confirmação do pedido

O valor correto é exibido para opções de pacote em ordem na Loja quando uma moeda diferente da base foi usada.

_ACP2E-2950 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Vídeo do YouTube adicionando bug

As imagens e os vídeos do produto são configurados no escopo global. Considerando que você não pode ter um vídeo de produto em um escopo e não em outro, a configuração da chave de API do Youtube foi definida como escopo global.

_ACP2E-2956 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Atualização da URL da [Nuvem] somente para store_id=0

O &quot;Caminho do URL&quot; agora é armazenado com a ID de armazenamento correta. Anteriormente, a ID de armazenamento estava incorreta, resultando em caminhos de URL incorretos restantes no banco de dados ao mover categorias.

_ACP2E-2964 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### async.operations.all foi executado e criou um erro.

Dados incorretos de link de produto em chamadas REST API não causam mais erros críticos.

_ACP2E-3009 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Problema de Publicação de Conteúdo Móvel da [Nuvem] somente não pode ser detectado na imagem PDP

O sistema agora oferece suporte à funcionalidade de pinçar para zoom em imagens da página de detalhes do produto na exibição móvel no Chrome, melhorando a experiência do usuário móvel. Anteriormente, o toque duplo na imagem na exibição móvel no Chrome não aumentava a imagem conforme esperado.

_ACP2E-3029 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### Rótulo ausente em LayeredNavigation com o nome de opção 0

O problema foi resolvido ignorando um verificador de valor vazio para o valor de atributo 0. Anteriormente, era considerado vazio e estava causando o problema.

_ACP2E-3058 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Os clientes veem os preços de outros grupos de clientes

Correção de um problema em que as informações relacionadas ao grupo de clientes eram salvas em um segmento incorreto devido ao valor antigo do X-Magento-Vary na solicitação

_ACP2E-3069 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Erro ao excluir opções de pacote

O sistema agora exclui corretamente as opções do pacote sem disparar um erro ou fazer com que a página pare de responder. Anteriormente, tentar excluir opções de pacote resultava em um erro de &quot;Página sem resposta&quot; e impedia que o produto fosse salvo.

_ACP2E-3076 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### O arquivo de imagem da [nuvem] não existe no log de erros do New Relic

O sistema agora sincroniza imagens personalizadas de espaço reservado para o armazenamento local, garantindo que elas sejam renderizadas corretamente ao usar o armazenamento remoto, como o AWS S3. Anteriormente, as imagens personalizadas de espaço reservado não eram renderizadas ao usar o armazenamento remoto, resultando em uma exibição de imagem com falha e logs de erro.

_ACP2E-3100 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### O feed RSS de novos produtos não é atualizado com novos produtos devido ao cache

O feed Rss para Novos produtos agora é atualizado quando um produto é definido como novo e salvo

_ACP2E-3103 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### A resposta GQL da Galeria de Mídia de Produto da [Cloud] não é classificada pela posição da imagem

Agora o sistema classifica corretamente os itens na galeria de mídia por posição na resposta do GraphQL, garantindo uma ordem de exibição precisa. Anteriormente, os itens na galeria de mídia não eram classificados por posição, resultando em uma ordem de exibição incorreta.

_ACP2E-3126 - [Problema do GitHub](https://github.com/magento/magento2/issues/37671) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### Os itens da subcategoria [Nuvem] não são exibidos na edição de widgets do back-end do administrador

A árvore de categorias na nova página do widget não deve mais ter problemas ao carregar categorias de nível 5+. Anteriormente, algumas categorias estavam ausentes ao carregar a árvore após as categorias de Nível 5.

_ACP2E-3136 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [nuvem] Zoom com dois dedos e mover problema no dispositivo móvel real

O sistema agora garante uma funcionalidade consistente de zoom de imagem em dispositivos móveis, fornecendo uma experiência do usuário suave e previsível. Anteriormente, o recurso de zoom de imagem era inconsistente e repentinamente diminuía o zoom após um determinado ponto quando visualizado em um dispositivo móvel.

_ACP2E-3198 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Quando cancelamos a atribuição de produtos do catálogo compartilhado, os produtos da lista de desejos não são apagados

Agora, nenhum item fica visível na lista de desejos se um produto não estiver disponível no catálogo compartilhado. Anteriormente, a página da lista de desejos exibia incorretamente uma contagem de &quot;1 item&quot;, mesmo quando nenhum item estava realmente disponível na lista de desejos.

_ACP2E-3282 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Produtos relacionados Selecionar tudo/Cancelar seleção de todos os problemas

Anteriormente, os botões &quot;Selecionar tudo&quot;/&quot;Cancelar seleção de todos&quot; para produtos relacionados não funcionavam corretamente se um produto fosse selecionado manualmente. Após a correção, esses botões agora funcionam de forma consistente, mesmo após a seleção manual, garantindo que todos os produtos sejam selecionados ou não corretamente.

_ACP2E-3286 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] Tradução de email de alerta do Stock para o idioma errado

Ao enviar alertas de preço/estoque para um site com várias exibições de loja usando diferentes idiomas, o idioma da exibição de loja em que o alerta foi criado será usado no email.

_ACP2E-3336 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4cf5e62) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### As categorias desativadas não terão mais seus nomes esmaecidos na árvore de categorias

Anteriormente, as categorias desativadas não estavam esmaecidas na árvore de categorias. Agora, eles são exibidos com um efeito cinza.

_ACP2E-3350 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### O carregamento do formulário de edição do produto configurável causa tempo limite e esgotamento de memória

Antes da correção, as variações de produto configuráveis eram construídas com base em todas as combinações de opções de atributo possíveis. Nos casos em que os atributos tinham muitas opções, isso resultava em uma operação demorada e que consumia recursos. Agora, as variações de produtos configuráveis são construídas com base em atributos de produtos secundários existentes. Isso resulta em muito menos cálculos - o que resulta em uma melhor utilização dos recursos.

_ACP2E-3410 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### O Fotorama não carrega o vídeo corretamente ao usar Amostras e a opção é pré-selecionada via URL

Os vídeos de produtos agora serão renderizados adequadamente na página de detalhes configurável do produto, se o URL contiver opções selecionadas.

_ACP2E-3454 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### O Widget de carrossel do PageBuilder mostra produtos que não correspondem às condições

A lista de produtos usada em widgets agora respeita a condição da categoria

_ACP2E-3461 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Erro de validação disparado para todos os produtos do grupo quando uma quantidade é inválida

Agora, o erro de validação é acionado corretamente para todos os produtos no grupo quando um produto tem uma quantidade inválida, o que não acontecia anteriormente.

_ACP2E-3469 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### [NUVEM] O preço especial não é exibido no produto Configurável

Após a correção, alterar o valor &quot;Usado na Lista de produtos&quot; para o atributo de preço especial não afetará a exibição do preço especial para produtos configuráveis.

_ACP2E-3513 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### Indexadores As tabelas temporárias não serão limpas se o processo for finalizado

As tabelas temporárias do indexador CatalogRule agora são limpas se o processo do indexador for encerrado

_ACP2E-3516 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [QUANS] Falha no teste da unidade principal em 2.4.7-p3

As notas de versão para este teste não são necessárias, pois é uma melhoria de Teste de unidade.

_ACP2E-3520 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Problema de Desempenho na Recuperação da Quantidade do Estoque para Produtos Agrupados com Várias Origens

A página de edição agrupada de produto e pacote agora é otimizada quando os produtos atribuídos têm um grande número de fontes de estoque.

_ACP2E-3533 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/0208e433)_

#### Refix ACP2E-3389

Desempenho aprimorado da página de categoria de administrador em caso de grande número de categorias de âncora

_ACP2E-3641 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catálogo, Conteúdo

#### O Cache da [Nuvem] não está sendo invalidado.

Anteriormente, ao salvar uma página do CMS com um layout de design atualizado, ela não refletia adequadamente no front-end. Depois que essa correção for aplicada, o layout de design apropriado estará visível no front-end quando alterarmos o layout de design e salvarmos a página do CMS.

_ACP2E-3063 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### [Categorias de âncora/não âncora ] da nuvem revertidas no widget de conteúdo

Anteriormente, ao selecionar Exibir em -> Categorias de âncora, mostrava todas as categorias que não refletiam a relação pai-filho entre a âncora e a não âncora. Depois que essa correção for aplicada, Exibir em -> Categorias de âncora exibirá apenas Categorias de âncora (selecionáveis) e Exibir em -> Categorias não âncora exibirá Categorias não âncora (selecionáveis)

_ACP2E-3131 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Categorias que não funcionam com widgets

Anteriormente, se salvássemos o bloco CMS para categorias de âncora/não âncora diferentes, ele não funcionava para as categorias secundárias quando ele era exibido no front-end. Depois que essa correção for aplicada, o bloco será mostrado no front-end para categorias diferentes.

_ACP2E-3152 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

### Catálogo, Estrutura

#### Obtenção de ordem (Entregas|Avisos de Crédito|NFF)Cobrança - A cobrança não deve ser carregada

O sistema agora garante que as coleções de remessas e avisos de crédito não sejam pré-carregadas quando recuperadas de um pedido, permitindo que filtros ou ordens adicionais sejam aplicados a essas coleções. Anteriormente, essas coleções eram carregadas automaticamente, impedindo mais modificações.

_AC-9111 - [Problema do GitHub](https://github.com/magento/magento2/issues/37561) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37562)_

#### [Nuvem]Acompanhamento: incompatibilidade na Comparação de Dados ao verificar se os dados foram alterados

Anteriormente, o objeto salvo era chamado todas as vezes sem qualquer alteração nos dados (para qualquer campo de dados numérico, como int/float/double). Ele aciona o sinalizador _hasDataChanges para ser true e chama a função de salvamento. Também não verifica os números flutuantes encapsulados por string. Depois que essa correção for aplicada, a função salvar só chamará se os dados forem alterados. O valor de dados para int/float/double-check com o valor passando para a função e faz correspondência de tipo strict

_ACP2E-2949 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8931218)_

### Catálogo, GraphQL

#### Lidar com filtros de categoria no GraphQL: includeDirectChildrenOnly e category_uid

Somente as categorias secundárias diretas são buscadas durante a filtragem por category_uid.

_ACP2E-3090 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### A classificação de produto Graphql da [Cloud] não funciona

A classificação de produto GraphQl por vários campos quando os campos são transmitidos em variáveis agora funciona como esperado.

_ACP2E-3166 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Os preços de nível retornam valores incorretos nos produtos GraphQL (em comparação com a Loja)

Após a correção, os preços de nível do produto retornados para solicitações graphql têm preço por um item.

_ACP2E-3312 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

### Catálogo, preços, preparo e visualização

#### O ponto de extremidade da API de preço especial da [Nuvem] retorna um erro ao atualizar um grande número de produtos simultaneamente

Agora, a API de atualização em massa de Preço especial criará uma única campanha para cada intervalo de datas, em vez de várias atualizações programadas para cada produto e intervalo de datas. Além disso, oferecerá suporte a solicitações de API simultâneas para processamento mais rápido de um grande número de SKUs.

_ACP2E-2672 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f89a447e)_

### Catálogo, Produto

#### A árvore de seleção de categoria em editar produto não está na mesma ordem definida em Catálogo ->Categorias

O sistema agora exibe corretamente a árvore de seleção de categorias na seção de edição do produto na mesma ordem definida em Catálogo -> Categorias, facilitando a administração de produtos em catálogos grandes. Anteriormente, a árvore de categorias na seção de edição do produto era exibida na ordem de criação da categoria, independentemente da ordem de exibição definida em Catálogo ->Categorias.

_AC-7050 - [Problema do GitHub](https://github.com/magento/magento2/issues/36101) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36104)_

### Catálogo, SEO

#### URL canônico incorreto para a categoria quando a página > 1

Anteriormente, o URL canônico para conteúdo de várias páginas não funcionava corretamente, exibindo de forma consistente o URL base. No entanto, depois que a correção foi implementada, o URL canônico para conteúdo de várias páginas agora exibe corretamente o URL com a ID da página.

_ACP2E-3653 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catálogo, Pesquisa

#### Os produtos não aparecem na categoria e na pesquisa, mas os links diretos estão funcionando

Anteriormente, o atributo personalizado Sim/Não com price_* attribute_code não funcionava com indexação. Após essa correção, o atributo personalizado Sim/Não funciona conforme esperado.

_ACP2E-2757 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### [Nuvem] Erro de pesquisa elástica em determinadas páginas de categoria

Anteriormente, com o tíquete de configuração mencionado, quando colocávamos o preço 0 para vários produtos, uma exceção era lançada na página de categoria de front-end. Após essa correção aplicada quando vários preços de produto 0 e carregamos a página de categoria no front-end, não haverá nenhuma exceção e a página de categoria será carregada com êxito.

_ACP2E-3053 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Erro de tipo ao criar objeto: Exceção Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor

Após a correção, uma ocorrência da classe Magento\CatalogSearch\Model\Indexer\Fulltext pode ser criada sem especificar $data.

_ACP2E-3345 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Problema da [NUVEM] com produtos não está visível no front-end após salvar no administrador do Magento

Após a correção, os produtos configuráveis que têm produtos secundários com nomes longos não serão perdidos na loja.

_ACP2E-3521 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Nuvem

#### [Cloud] PHPSESSID está alterando cada solicitação POST

O PHPSESSID não é mais regenerado em solicitações POST na área de front-end para um cliente conectado se o cache L2 Redis estiver ativado e o cliente tiver sido atualizado do back-end

_ACP2E-3010 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Avisos de Geração de Mapa do Site

Após a correção, o mapa do site é gerado no diretório tmp do sistema e copiado para o destino final.

_ACP2E-3532 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Conteúdo

#### [Problema] com o preço de exibição no widget Recentemente visualizado

O sistema agora exibe corretamente o preço dos produtos simples indisponíveis no widget &quot;Produto visualizado recentemente&quot;, garantindo a consistência entre todos os widgets e páginas de lista de produtos. Anteriormente, o preço dos produtos simples indisponíveis não era exibido no widget &quot;Produto visualizado recentemente&quot; devido a uma condição nos modelos de carregamento de preço.

_AC-10539 - [Problema do GitHub](https://github.com/magento/magento2/issues/38167) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38159)_

#### [Problema] Corrija o erro de digitação e a gramática no arquivo acl.xsd

O sistema agora corrige um erro de digitação e gramática no arquivo acl.xsd, melhorando a clareza e a precisão da documentação. Anteriormente, o arquivo acl.xsd continha um erro de digitação e uma gramática incorreta que poderia causar confusão.

_AC-10596 - [Problema do GitHub](https://github.com/magento/magento2/issues/38061) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38046)_

#### Imagem de banner do Pagebuilder não visível na galeria

O sistema agora exibe corretamente as imagens de banner carregadas nas pastas recém-criadas na galeria do Pagebuilder, eliminando erros anteriores do console. Antes dessa correção, as imagens de banner não estavam visíveis na galeria se fossem carregadas em uma nova pasta, causando um erro de console.

_AC-10845 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### &quot;Código de área não definido&quot; após a atualização para 2.4.5-p8

O sistema agora conclui com êxito o processo de implantação de conteúdo estático quando o módulo Magento_CSP está ativado e &quot;dev/js/translate_strategy&quot; está definido como &quot;incorporado&quot;, sem acionar o erro &quot;Código de área não definido&quot;. Anteriormente, sob essas condições, o processo de implantação de conteúdo estático falhava com um erro &quot;Código de área não definido&quot;.

_AC-12283 - [Problema do GitHub](https://github.com/magento/magento2/issues/38845) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38922)_

#### A árvore de categoria do widget não é renderizada corretamente

_AC-12692 - [Problema do GitHub](https://github.com/magento/magento2/issues/39008) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/58e40ceb)_

#### Não é possível ver a mensagem &quot;Usando valor padrão&quot; ao alterar o tema na página de configuração de design

O sistema agora inclui uma coluna separada para exibir a mensagem &quot;Usando valor padrão&quot;, dependendo do tema selecionado na página de configuração de design. Isso garante clareza e visibilidade do status do valor padrão. Anteriormente, a mensagem &quot;Usando valor padrão&quot; não era exibida, resultando em confusão sobre o status do tema selecionado.

_AC-13054 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] Restaura a compatibilidade com versões anteriores dos plug-ins do TinyMCE novamente (depois disso...

O sistema agora restaura a compatibilidade com versões anteriores com plug-ins TinyMCE, permitindo que as funções definidas dentro do plug-in sejam chamadas quando o widget for usado de outro local. Anteriormente, devido a uma mudança na versão TinyMCE, os plug-ins não retornavam os widgets como um objeto, resultando em um erro ao tentar chamar determinadas funções na instância do widget.

_AC-13569 - [Problema do GitHub](https://github.com/magento/magento2/issues/39262) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39258)_

#### [Problema de carregamento de arquivo do ] no editor do WYSIWYG na página do produto

Agora o sistema exibe corretamente a árvore de pastas e permite uploads de imagens no editor do WYSIWYG na página do produto, mesmo depois de expandir a guia &quot;Imagens e vídeos&quot; primeiro. Anteriormente, expandir a guia &quot;Imagens e vídeos&quot; primeiro resultava na não exibição da árvore de pastas e em uma mensagem de erro ao tentar fazer upload de uma imagem no editor do WYSIWYG.

_AC-9638 - [Problema do GitHub](https://github.com/magento/magento2/issues/38026) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38025)_

#### [Problema de bloqueio dinâmico no local]

Os wdigets agora estão sendo renderizados corretamente dentro de blocos dinâmicos.

_ACP2E-2392 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### O front-end da [Cloud] não está carregando devido a um problema no modelo do informativo

A adição de blocos por meio da seção de conteúdo da página do CMS não gera mais exceções

_ACP2E-2693 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### ACP2E-2836: [Nuvem] Exceção de investigação encontrada no log: InvalidArgumentException: a classe não existe em vendor/magento/module-rule/Model/ConditionFactory.php

A remoção de uma condição nas configurações de conteúdo dos produtos do PageBuilder não faz mais com que uma exceção seja registrada nos arquivos de log. Anteriormente, a remoção de uma condição nas configurações de conteúdo dos produtos do PageBuilder causava a gravação de uma exceção crítica nos logs, embora não causasse problemas no front-end.

_ACP2E-2836 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_

#### Alternar para o modo de armazenamento único - o conteúdo global não é mais exibido

O sistema agora sincroniza as configurações de design de visualização da loja com as configurações de design do site ao ativar o modo de loja única, garantindo que as atualizações de conteúdo estejam visíveis no front-end. Anteriormente, alternar para o modo de armazenamento único evitava que as atualizações de conteúdo fossem refletidas na loja.

_ACP2E-2842 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### O Page Builder substitui a imagem ao tentar adicionar links e outras falhas de usabilidade.

Agora, ao clicar em uma imagem, os links no editor wysiwyg no elemento de texto do Page Builder carregarão os dados apropriados na imagem, na caixa de diálogo de configuração do link. Adicionar um link a uma imagem no editor agora funciona corretamente. Anteriormente, a imagem era substituída por um link.

_ACP2E-2903 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### A galeria de mídia antiga falha ao renderizar imagens quando uma imagem de 0 byte é colocada no diretório

O sistema agora lida com imagens de 0 bytes na galeria de mídia sem interromper a funcionalidade, permitindo que outras imagens no diretório sejam exibidas e selecionadas conforme esperado. Anteriormente, a presença de uma imagem de 0 byte na galeria de mídia impedia que todas as imagens no diretório fossem exibidas ou selecionadas.

_ACP2E-2970 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Erro no Page Builder ao editar o bloco do CMS

Agora, o sistema salva corretamente as alterações feitas na área de administração usando o Page Builder, sem gerar o erro &quot;O Page Builder foi renderizado por 5 segundos sem liberar bloqueios&quot;. no console do navegador. Anteriormente, esse erro ocorria ao tentar salvar alterações, impedindo a atualização bem-sucedida do conteúdo.

_ACP2E-3064 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### [NUVEM] Não há botões para fazer check-out ou editar o carrinho na seção do carrinho

O produto do pacote agora é adicionado ao carrinho por meio de widgets sem erros.

_ACP2E-3092 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b21e5d91) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_

#### O botão Carregar imagem da [NUVEM] não funciona

Antes do botão Fazer upload da imagem para o banner e controle deslizante do PageBuilder não funcionava como esperado e agora, ao pressioná-lo, o gerenciador de arquivos local é aberto para selecionar a imagem desejada para upload.

_ACP2E-3122 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_

#### imagecreatetruecolor(): o argumento #2 ($height) deve ser maior que 0. Não é possível carregar uma imagem específica

Solução do problema que causava erros no administrador ao carregar imagens com altura 0 pela galeria de mídia e êxito na sincronização de ativos usando o comando sync. Anteriormente, o não podia fazer upload da imagem pela galeria de mídia e o comando sync também falhava quando uma imagem específica estava na galeria.

_ACP2E-3127 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Prototype.js Array.from em conflito com a API do Google Maps

O Google Maps agora é renderizado corretamente no editor do PageBuilder. Anteriormente, um erro de Javascript impedia que o Google Maps fosse renderizado corretamente.

_ACP2E-3154 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Nuvem] - o controle deslizante do CMS não reflete as alterações mais recentes

O problema foi corrigido, garantindo que a lista de controles deslizantes fosse atualizada enquanto o evento de salvamento era acionado na tela editar slide. Anteriormente, ela estava acionando e causando o problema.

_ACP2E-3275 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### Ocorre um erro na página CSM quando blocos CMS são inseridos usando o page builder em determinada ordem

Anteriormente em algumas versões do PHP e OS (Linux), a renderização de blocos que referenciavam outros blocos cms através do PageBuilder teria falhado com um &quot;Erro desconhecido&quot;. Tente novamente.&quot;. Agora, o conteúdo dos blocos cms é renderizado corretamente dentro de um conteúdo controlado pelo PageBuilder.

_ACP2E-3326 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### Falha na visualização do modelo do Pagebuilder para conteúdo grande

Um conteúdo grande estava fazendo com que o elemento da tela excedesse os limites do navegador e retornasse um valor incorreto, o que danificou o código de back-end (não é possível decodificar a imagem corretamente). Corrigido com a limitação do tamanho da tela de desenho ao limite do navegador universal.

_ACP2E-3428 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/adfb1747)_

#### Atualizações de segurança mais recentes com tamanho de fonte ausente no TinyMCE 7

Os seletores de tamanho de fonte e família de fontes agora estão disponíveis no editor do WYSIWYG. Antes dessa correção, com o TinyMCE 7, eles não estavam disponíveis na interface do editor.

_ACP2E-3430 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d50f6b5d) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_

#### Tamanho de fonte do editor TinyMCE 7 no administrador em PT e não em PX. Esclareça

Antes da correção, não era possível especificar o tamanho da fonte em px nas áreas do WYSIWYG. Agora você pode definir o tamanho da fonte em px em vez de pt.

_ACP2E-3483 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### O tipo de conteúdo do produto no Page Builder é recolhido sem mensagens corretas

Antes da correção, o html de visualização não era gerado corretamente quando não havia produtos no widget. Agora, a resposta vazia é gerada corretamente e o widget Produtos é exibido sem problemas na pré-visualização.

_ACP2E-3490 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### [construtor de páginas]Adicionar lista de produtos para bloquear resulta em erros

Agora, adicionar a Lista de produtos do pacote ao bloqueio via construtor de páginas não resulta em erros

_ACP2E-3534 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Cliente/ Clientes

#### Front-end - A validação da data de nascimento falhou na página Criação do cliente

Verifique se toda a validação deve funcionar após a dependência do sistema da atualização Moment.js para a versão secundária mais recente

_AC-12162 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### O campo de texto Região não é redefinido quando a lista suspensa do país é alterada

O sistema agora redefine o campo de texto da região quando o país é alterado no menu suspenso, garantindo que os valores anteriores não persistam. Anteriormente, alterar o país na lista suspensa não redefinia o campo de região, fazendo com que o último valor salvo fosse preservado.

_AC-8499 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### A exclusão de cliente não limpa todos os dados de sessão do navegador na loja para clientes conectados e excluídos

A exclusão de um cliente agora limpa todos os dados de sessão do navegador da loja para clientes conectados e excluídos, conforme esperado. O comprador pode continuar comprando e o navegador trata a sessão como uma sessão de convidado. Anteriormente, quando a conta do cliente de um comprador conectado era excluída do Administrador, o navegador do comprador exibia erros de JavaScript.

_AC-9240 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

### Estrutura

#### [Pergunta]Configuração de tipo não utilizado em `app/code/Magento/Translation/etc/di.xml`

O sistema agora remove dependências não utilizadas na configuração, melhorando a limpeza e a eficiência gerais do código. Anteriormente, havia dependências não usadas na configuração do que não contribuíam para nenhuma funcionalidade do.

_AC-10037 - [Problema do GitHub](https://github.com/magento/magento2/issues/38030) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38064)_

#### Pergunta/problema do ponto de extremidade V1/customers/password

O sistema agora segue as restrições definidas na GUI de gerenciamento ao processar solicitações de alteração de senha por meio da API, evitando o potencial abuso da função de redefinição de senha. Anteriormente, a API podia processar solicitações de alteração de senha fora das regras definidas na GUI de gerenciamento, possivelmente permitindo um fluxo constante de emails de redefinição se os emails válidos fossem conhecidos.

_AC-10654 - [Problema do GitHub](https://github.com/magento/magento2/issues/38238) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### A configuração de verniz não exclui todos os parâmetros de marketing

O sistema agora exclui corretamente todos os parâmetros de marketing comuns na configuração do verniz, garantindo um rastreamento e análise precisos. Anteriormente, determinados parâmetros de marketing, como gad_source, srsltid e msclkid, não eram excluídos, resultando em possíveis imprecisões na coleta de dados.

_AC-10738 - [Problema do GitHub](https://github.com/magento/magento2/issues/38298) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39188)_

#### Processo de indexação de erros do processo de índice de pesquisa de catálogo

O sistema agora completa com sucesso o comando re-index sem encontrar nenhum erro, independentemente da versão libxml compilada com PHP. Anteriormente, a execução do comando re-index resultava em um erro de processo de índice de pesquisa de catálogo durante o processo de indexação quando o PHP era compilado com determinadas versões de libxml.

_AC-10838 - [Problema do GitHub](https://github.com/magento/magento2/issues/38254) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38553) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### Adicionados filtros created_at, status e grand_total à consulta Ordens do cliente e correção de várias falhas de filtros

O sistema agora oferece suporte ao uso de filtros created_at, status e grand_total em consultas de Pedidos do cliente e resolveu um problema em que vários filtros não eram aplicados corretamente. Anteriormente, o sistema não aceitava esses filtros e não aplicava todos os filtros quando mais de um era usado em um query.

_AC-10941 - [Problema do GitHub](https://github.com/magento/magento2/issues/38392) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36949)_

#### Obtenção aleatória de consultas de blocos relacionados/de venda adicional/venda cruzada e indexação de preços

O sistema agora otimiza as consultas de blocos relacionados, de venda adicional e de venda cruzada, melhorando o desempenho e evitando que o site seja desativado devido a consultas excessivas. Anteriormente, o sistema podia ficar sobrecarregado com consultas desses blocos, causando lentidão significativa e possivelmente desativando o site.

_AC-10991 - [Problema do GitHub](https://github.com/magento/magento2/issues/36667) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38050)_

#### Exceção: Aviso: Tentando acessar deslocamento de matriz em... -> Calendar.php desde a atualização para ICU 74.1 (PHP Intl)

A Commerce não registra mais a seguinte exceção no exception.log sempre que um comprador ou comerciante visita a vitrine ou o Administrador: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)

_AC-11423 - [Problema do GitHub](https://github.com/magento/magento2/issues/38214) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38364)_

#### [Problema] Corrija problemas com os Dados do cliente quando o formulário contém um elemento com o nome `method`

O sistema agora identifica corretamente o atributo &quot;método&quot; nos envios de formulário, mesmo quando um elemento chamado &quot;método&quot; está presente no formulário. Isso garante o processamento preciso dos dados do cliente. Anteriormente, se um elemento de formulário fosse nomeado como &quot;método&quot;, ele interferiria na identificação do atributo &quot;método&quot; nos envios de formulários, resultando em possíveis problemas com o manuseio de dados do cliente.

_AC-11476 - [Problema do GitHub](https://github.com/magento/magento2/issues/38484) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38449)_

#### [Problema] Corrigir PHPDocs para \Magento\Framework\Data\Collection::getItemById

Os PHPDocs para o método \Magento\Framework\Data\Collection::getItemById foram atualizados para incluir nulo como um possível tipo de retorno, abordando problemas com ferramentas de análise estática. Anteriormente, os PHPDocs do método não especificavam null como um possível tipo de retorno, levando a avisos ou erros na análise estática quando o método era usado em declarações condicionais.

_AC-11489 - [Problema do GitHub](https://github.com/magento/magento2/issues/38485) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38439)_

#### [Problema] Permitir apenas preferências válidas durante `setup:di:compile`

O sistema agora emite um erro durante o comando `setup:di:compile` se uma preferência for criada para uma classe que não existe ou está especificamente excluída, garantindo que somente preferências válidas sejam permitidas. Anteriormente, esses cenários falhavam silenciosamente, possivelmente inutilizando todos os plug-ins associados às classes originais.

_AC-11592 - [Problema do GitHub](https://github.com/magento/magento2/issues/38517) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33161)_

#### Magento tentando modificar propriedade somente leitura no método __wakeup de LoggerProxy

O sistema agora permite a modificação de propriedades somente leitura anteriores no método __wakeup do LoggerProxy, garantindo uma operação suave sem forçar os usuários a empregar uma solução alternativa. Anteriormente, uma tentativa de reatribuir o valor de uma propriedade somente leitura no método __wakeup do LoggerProxy causaria problemas.

_AC-11651 - [Problema do GitHub](https://github.com/magento/magento2/issues/38526) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### [Problema] AC-2039 AC-1667 atualização referências TinyMCE

Atualização da versão mais recente do tinymce no composer.json

_AC-11681 - [Problema do GitHub](https://github.com/magento/magento2/issues/38533) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36543) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### ChangelogBatchWalker não funciona em vários threads

O sistema agora oferece suporte à bifurcação de processos para indexação do MView, evitando erros durante a execução do indexador ao operar em vários threads. Anteriormente, executar ChangelogBatchWalker em várias threads levava à exclusão de tabelas usadas por outras threads, causando um erro durante a execução do indexador.

_AC-11696 - [Problema do GitHub](https://github.com/magento/magento2/issues/38246) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38248)_

#### [Problema] Renomear variável nomeada incorretamente

O sistema agora nomeia corretamente a variável que contém a quantidade de dinheiro que ainda pode ser reembolsado, evitando confusão durante a depuração. Anteriormente, essa variável era nomeada incorretamente como totalRefund, o que poderia levar a mal-entendidos para os desenvolvedores.

_AC-11781 - [Problema do GitHub](https://github.com/magento/magento2/issues/38609) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36205)_

#### [Problema] passar atributos personalizados para o link atual via XML

O sistema agora permite que atributos personalizados sejam passados para o link atual via XML, garantindo que esses atributos sejam exibidos corretamente mesmo quando o link for a página atual. Anteriormente, os atributos personalizados não eram exibidos para o link da página atual porque o método getAttributesHtml() não estava sendo usado para o link atual.

_AC-11809 - [Problema do GitHub](https://github.com/magento/magento2/issues/38500) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/30070)_

#### O cache FPC integrado foi corrompido na versão 2.4.7 para algumas configurações

O sistema agora armazena as páginas em cache corretamente quando o parâmetro MAGE_RUN_CODE é definido, garantindo um desempenho ideal. Anteriormente, as páginas não eram armazenadas em cache sob essas condições, resultando em possíveis problemas de desempenho.

_AC-11819 - [Problema do GitHub](https://github.com/magento/magento2/issues/38626) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38646) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### [Problema] Corrija a exceção ao manipular a inconsistência entre os modos de desenvolvedor e de produção

O sistema agora lida consistentemente com exceções entre os modos de desenvolvedor e de produção, impedindo o redirecionamento inesperado para a página de logon quando uma exceção é lançada. Anteriormente, uma inconsistência no tratamento da exceção poderia causar um redirecionamento para a página de logon no modo de produção em vez de exibir a mensagem de exceção.

_AC-11829 - [Problema do GitHub](https://github.com/magento/magento2/issues/38639) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37712)_

#### Substituir a tradução &quot;Conta do PayPal&quot; em token_list.phtml

O sistema agora rotula a seção para métodos de pagamento de conta tokenizáveis como &quot;Conta&quot; em vez de &quot;Conta do PayPal&quot; na página Métodos de pagamento armazenados, tornando-a mais representativa de sua função. Anteriormente, essa seção era especificamente rotulada como &quot;Conta do PayPal&quot;, o que induzia em erro quando outros métodos de pagamento de conta tokenizáveis eram adicionados.

_AC-11852 - [Problema do GitHub](https://github.com/magento/magento2/issues/35622) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37959)_

#### A compatibilidade com versões anteriores foi perdida na classe Magento\Catalog\Model\ProductRepository

A classe ProductRepository agora mantém a compatibilidade com versões anteriores restaurando a classe Auxiliar de inicialização como o segundo parâmetro, garantindo que os módulos estendidos dessa classe funcionem conforme esperado. Anteriormente, a remoção do Auxiliar de inicialização do construtor na classe ProductRepository resultava em uma perda de compatibilidade com versões anteriores, forçando os usuários a empregar uma solução alternativa.

_AC-11874 - [Problema do GitHub](https://github.com/magento/magento2/issues/38669)_

#### [Problema] Implantação de conteúdo estático - Erro de tipo

O sistema agora lida corretamente com arquivos LESS vazios durante a implantação de conteúdo estático, exibindo uma mensagem de erro &quot;LESS file is empty&quot;. Anteriormente, um erro de tipo incorreto era exibido ao encontrar um arquivo LESS vazio durante a implantação.

_AC-11905 - [Problema do GitHub](https://github.com/magento/magento2/issues/38682) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38683)_

#### [Problema] [Visualização] Removeu espaço extra na marca de link e script

O sistema agora garante que não haja espaços extras nas tags de link e script, fornecendo um código mais limpo e eficiente. Anteriormente, espaços duplos podiam ser encontrados entre os atributos nas tags link e script.

_AC-12002 - [Problema do GitHub](https://github.com/magento/magento2/issues/32920) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32919)_

#### [Problema] evitar um loop infinito de configuração incorreta

O sistema agora evita um loop infinito, impedindo o mapeamento autorreferencial em configurações de tipo virtual. Isso garante que o aplicativo não fique preso em um loop infinito ao tentar cancelar a referência de um nó autorreferencial. Anteriormente, se uma configuração de tipo virtual fosse autorreferencial, ela faria com que o aplicativo girasse indefinidamente.

_AC-12127 - [Problema do GitHub](https://github.com/magento/magento2/issues/38822) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38794)_

#### Gerenciador de objetos não usado para Magento\Csp\Model\Mode\Data\ModeConfigured

O sistema agora usa corretamente o Gerenciador de objetos ao criar o objeto ModeConfigured, permitindo que os plug-ins sejam usados nesse objeto. Anteriormente, o Gerenciador de objetos não estava sendo usado, impedindo que plug-ins fossem aplicados ao objeto ModeConfigured.

_AC-12299 - [Problema do GitHub](https://github.com/magento/magento2/issues/38875) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38886)_

#### Comentário impreciso de bloco de documento em alertas de preço e estoque do produto

O comentário de bloco do documento para o método deleteCustomer no Estoque de produto e Alertas de preço foi corrigido para refletir com precisão que o método exclui todos os alertas de produto ou preço de estoque associados a um determinado cliente e site, não o cliente do site. Anteriormente, o comentário afirmava incorretamente que o método era excluir um cliente do site.

_AC-12540 - [Problema do GitHub](https://github.com/magento/magento2/issues/38939) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39001)_

#### [Problema] Use a configuração compilada para dados gerados em vez da configuração geral

O sistema agora usa a configuração compilada para dados gerados em vez da configuração geral, reduzindo a transferência de rede e a sobrecarga dos dados que dependem de uma determinada versão do código. Essa alteração impede a substituição de cache em instâncias compartilhadas durante a troca de contêiner, resultando em estabilidade aprimorada e tempo de inatividade reduzido. Anteriormente, determinadas classes principais usavam o tipo de configuração compartilhada, o que poderia resultar na substituição de cache ou no tempo de inatividade do aplicativo devido a diferenças nas versões do código em vários servidores.

_AC-12594 - [Problema do GitHub](https://github.com/magento/magento2/issues/38785) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/29954)_

#### [Problema] Remover referências a arquivos do extjs que foram removidos no e1ccdb...

O sistema agora remove referências a arquivos do extjs que foram removidos anteriormente, eliminando erros no console do navegador e no arquivo de log do sistema. Anteriormente, essas referências estavam causando erros devido à ausência dos arquivos referenciados.

_AC-12597 - [Problema do GitHub](https://github.com/magento/magento2/issues/38960) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38951)_

#### [Problema] limpeza secundária: corrigido o uso incorreto de sprintf, leva apenas 2 espaços reservados aqui e w...

O sistema agora usa corretamente a função sprintf com o número apropriado de espaços reservados, melhorando a limpeza e a consistência do código. Anteriormente, a função sprintf era usada incorretamente com um argumento extra, o que não causava grandes problemas, mas não era o uso correto.

_AC-12778 - [Problema do GitHub](https://github.com/magento/magento2/issues/39062) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38628)_

#### Extensão FTP removida do PHP 8.2.15

O sistema agora inclui a extensão FTP como uma dependência no arquivo composer.json, garantindo a configuração bem-sucedida das importações de CSV via FTP. Anteriormente, um erro era gerado ao tentar configurar importações de CSV via FTP porque a extensão FTP estava ausente no pacote PHP.

_AC-12857 - [Problema do GitHub](https://github.com/magento/magento2/issues/39083) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] corrige classes incorretas sendo referenciadas em módulos Magento.

O sistema agora faz referência corretamente às classes nos módulos, garantindo uma operação mais suave e evitando falhas devido a classes não existentes. Isso inclui uma correção de bug nos módulos Indexador e Creditmemo e a implementação da HttpGetActionInterface na classe PrintAction. Anteriormente, referências de classe incorretas resultavam em erros e possíveis falhas no sistema, e certas funcionalidades, como o nome do arquivo para arquivos PDF de memorando de crédito e reindexação de estoques, não funcionavam como esperado.

_AC-12869 - [Problema do GitHub](https://github.com/magento/magento2/issues/39126) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37784)_

#### Capacidade de definir Área para o comando CLI `dev:di:info`

O sistema agora permite que os desenvolvedores definam uma área para o comando da CLI `dev:di:info`, aprimorando o processo de desenvolvimento e depuração. Anteriormente, esse comando só podia exibir informações da área GLOBAL.

_AC-12964 - [Problema do GitHub](https://github.com/magento/magento2/issues/38758) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38759)_

#### [Problema]: adicionar a propriedade isMultipleFiles ao modelo de elemento de formulário de imagem

Essa correção impede que o botão &quot;Procurar para localizar ou arrastar imagem aqui&quot; desapareça quando uma imagem é adicionada em um elemento de formulário de imagem com vários arquivos.

_AC-13149 - [Problema do GitHub](https://github.com/magento/magento2/issues/39219) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36325)_

#### [Problema] Remova todos os parâmetros de obtenção de marketing para minimizar o cache

O sistema agora remove todos os parâmetros de obtenção de marketing para otimizar a utilização do cache, espelhando a lógica usada quando o Verniz está em uso. Anteriormente, esses parâmetros podiam levar ao aumento excessivo do cache e à redução do desempenho.

_AC-13279 - [Problema do GitHub](https://github.com/magento/magento2/issues/39266) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39099)_

#### [Problema] [PHPDOC] Corrigir phpdoc inválido Magento\Directory\Model\AllowedCountries::getAllowedChannels()

O PHPDoc para o método AllowedCountry::getAllowedChannels() foi corrigido para fornecer informações precisas, melhorando a clareza e a utilidade da documentação. Anteriormente, o PHPDoc para este método continha informações incorretas, o que poderia levar a confusão ou uso incorreto do método.

_AC-13345 - [Problema do GitHub](https://github.com/magento/magento2/issues/39246) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39241)_

#### [Problema] Remove alguns códigos de versões do PHP que não são mais suportadas.

Remoção do código para versões do PHP que não são mais suportadas no Magento

_AC-13348 - [Problema do GitHub](https://github.com/magento/magento2/issues/39361) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39202)_

#### [Problema] Tornar o ImageMagick Adapter compatível com php8 (Conversão implícita de float para int)

O sistema agora garante compatibilidade com o PHP8 manipulando corretamente números flutuantes ao calcular dimensões de imagem, evitando quaisquer erros devido à conversão implícita de float para int. Anteriormente, o cálculo das dimensões da imagem podia resultar em números flutuantes, que quando arredondados implicitamente causavam um erro.

_AC-13417 - [Problema do GitHub](https://github.com/magento/magento2/issues/39402) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37362)_

#### [Problema] [PHPDOC] Corrigir phpdoc inválido Magento\Framework\App\Config\ScopeConfigInterface

Essa atualização corrige as anotações PHPDoc no Magento\Framework\App\Config\ScopeConfigInterface para refletir com precisão o tipo do argumento $scopeCode para os métodos getValue e isSetFlag.

_AC-13537 - [Problema do GitHub](https://github.com/magento/magento2/issues/39492) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39199)_

#### Magento\Framework\Filesystem\Driver\Http depende da frase de motivo OK

Remoção da verificação de frase &quot;OK&quot; de Magento\Framework\Filesystem\Driver\Http::isExists

_AC-13725 - [Problema do GitHub](https://github.com/magento/magento2/issues/39546) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39558)_

#### O indexador de Grade do Cliente não funciona corretamente no modo Atualizar por Agendamento

A grade do cliente anterior foi atualizada instantaneamente, mas depois da correção, a grade do cliente é atualizada após a execução do cron, mas não reflete instantaneamente.

_AC-13810 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### erro de digitação em um arquivo js.

O sistema agora usa corretamente o termo &quot;assinantes&quot; no arquivo do JavaScript, garantindo a funcionalidade adequada dos recursos relacionados. Anteriormente, um erro tipográfico no arquivo JavaScript resultava no uso incorreto do termo &quot;assinantes&quot;.

_AC-6754 - [Problema do GitHub](https://github.com/magento/magento2/issues/36163) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36171)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, a tag `@author` estava presente em alguns módulos, o que era contrário aos padrões de codificação estabelecidos.

_AC-8353 - [Problema do GitHub](https://github.com/magento/magento2/issues/37253) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37003)_

#### [Problema] Remover a marca `@author` proibida de `Magento_Customer` (parte 2)

O sistema agora segue o padrão de codificação, removendo a tag `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, a tag `@author` estava presente em alguns módulos, o que era contrário aos padrões de codificação estabelecidos.

_AC-8356 - [Problema do GitHub](https://github.com/magento/magento2/issues/37250) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37000)_

#### Espaço na regra de quebras de sintaxe editorconfig para `[&lbrace;composer,auth&rbrace;.json]`

O sistema agora aplica corretamente um recuo de 4 espaços para os arquivos composer e auth.json, seguindo uma correção para um erro de sintaxe no editorconfig. Anteriormente, devido a um espaço na sintaxe editorconfig, esses arquivos eram formatados incorretamente com um recuo de 2 espaços.

_AC-8659 - [Problema do GitHub](https://github.com/magento/magento2/issues/37394) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37395)_

#### [Problema] Melhore o log de erros do CRON

O sistema agora captura e registra os processos STDERR e STDOUT para cron, fornecendo informações valiosas de diagnóstico em cenários onde os processos cron falham. Anteriormente, qualquer mensagem de erro nos processos cron não era registrada, e STDERR e STDOUT para grupos cron em execução em processos separados eram perdidos.

_AC-8662 - [Problema do GitHub](https://github.com/magento/magento2/issues/37453) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32690)_

#### [Problema] Adiciona mais algumas cores à saída de determinados comandos da cli de instalação

O sistema agora adiciona mais cores à saída de determinados comandos da interface de linha de comando (CLI) de configuração, melhorando a legibilidade e a experiência do usuário. Anteriormente, a saída desses comandos era mais difícil de ler devido à falta de diferenciação de cores.

_AC-8984 - [Problema do GitHub](https://github.com/magento/magento2/issues/29335) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/29298)_

#### A atualização do Magento redefine general/region/state_required quando um novo país com estado/região obrigatórios é adicionado.

O sistema agora só adiciona o país modificado à configuração &quot;general/region/state_required&quot; quando um novo país com estados obrigatórios é adicionado, evitando qualquer interrupção no código personalizado que presume que a região está desativada. Anteriormente, adicionar um novo país com estados obrigatórios redefinia a configuração &quot;general/region/state_required&quot; para países padrão com um estado obrigatório, possivelmente quebrando a loja.

_AC-9630 - [Problema do GitHub](https://github.com/magento/magento2/issues/37796) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38076)_

#### Diferença na menor compilação entre biblioteca php e nodejs (grunt) com expressões `calc` complicadas

Corrigir a diferença na menor compilação entre a biblioteca php e nodejs (grunt) após a atualização wikimedia/less.php:^5.x

_AC-9712 - [Problema do GitHub](https://github.com/magento/magento2/issues/37841) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### O erro &quot;Tabela ou exibição base não encontrada&quot; ocorre quando a indexação parcial é executada

A reindexação parcial agora funciona corretamente com o changelog grande no caso de conexão de banco de dados secundária

_ACP2E-2692 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Problemas após atualizar o MariaDB para a versão 10.5.1 ou superior

Correção do problema em que valores datetime em um banco de dados eram convertidos em 0000-00-00 00:00:00 após a atualização do Mysql

_ACP2E-2844 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Tipos de incompatibilidade na comparação de dados ao verificar se os dados foram alterados

Anteriormente, o objeto salvo era chamado todas as vezes sem qualquer alteração nos dados (para qualquer campo de dados numérico, como int/float/double). Ele aciona o sinalizador _hasDataChanges para ser true e chama a função de salvamento. Depois que essa correção for aplicada, a função salvar só chamará se os dados forem alterados. O valor de dados para int/float/double-check com o valor passando para a função e faz a correspondência de tipo strict.

_ACP2E-2855 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### A importação da [Nuvem] não pode ser usada com a variável de diretório

O produto pode ser importado com sucesso, independentemente do nome do arquivo.

_ACP2E-2959 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### No ipad mini, o menu e o cabeçalho são carregados como móveis, em vez disso, eles devem ser carregados como desktop.

O sistema agora trata os dispositivos com uma largura de 768 px como desktop, garantindo que o menu e o cabeçalho sejam carregados corretamente. Anteriormente, os dispositivos com uma largura de 768 px eram tratados como móveis, fazendo com que o menu e o cabeçalho fossem carregados em uma visualização móvel.

_ACP2E-2966 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### A modificação do comprimento da coluna via db_schema.xml não funciona no caso de chaves estrangeiras

a modificação da coluna com chave estrangeira por meio do schema declarativo agora não gera erros com MariaDB

_ACP2E-3230 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Alguns dos registros de relações são salvos no banco de dados quando o registro de pedido é salvo

Antes da correção, estavam sendo acionadas consultas UPDATE desnecessárias que podem ter impacto no desempenho. Após a correção, as consultas UPDATE desnecessárias foram eliminadas.

_ACP2E-3361 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [NUVEM] No admin, há muitos erros de javascript no console

Anteriormente, no painel de administração, havia muitos erros de javascript no console. Agora, no painel de administração, não haverá erros de JavaScript no console e todas as funções padrão do JavaScript serão executadas com êxito sem problemas.

_ACP2E-3375 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### [Cloud] Magento: a mensagem da fila foi excluída

As mensagens em fila agora estão sendo apagadas corretamente. Antes da correção, considerando que o sistema de fila SQL estava sendo usado, novas mensagens poderiam ter sido excluídas se a mensagem da fila de limpeza estivesse sendo executada ao mesmo tempo.

_ACP2E-3387 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### As entradas de chave de cache correspondentes não estão disponíveis nas tags de cache, portanto, a limpeza do cache não funciona corretamente

O modo LUA agora está habilitado por padrão para o coletor de lixo do cache Redis para evitar condições de corrida

_ACP2E-3537 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### O valor Magento_DC_INDEXER_USE_APPLICATION_LOCK é ignorado

Após a correção, uma variável ENV definida como &quot;false&quot; será tratada como bool false, não como uma cadeia de caracteres &#39;false&#39;.

_ACP2E-3681 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

#### [Problema] Introdução ao suporte de tipos escalares personalizados para o esquema do GraphQL

O sistema agora é compatível com tipos escalares personalizados para o esquema do GraphQL, permitindo que os desenvolvedores definam tipos e implementações escalares personalizados. Esse recurso pode ser particularmente útil para expressar valores que podem exigir validação, como HTML, emails, URLs, datas etc., e para casos mais avançados, como atributos EAV. Anteriormente, o sistema não aceitava o processamento de tipos escalares personalizados no GraphQL.

_AC-7976 - [Problema do GitHub](https://github.com/magento/magento2/issues/36877) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/34651) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### Estrutura, Estrutura da interface

#### Possibilidade de substituir o valor de configuração mesmo se estiver bloqueado

Antes dessa correção, a configuração de design não podia ser definida por meio do comando bin/magento config:set e os valores bloqueados podiam ser alterados por manipulação do formulário que os exibia. Após a correção, os valores bloqueados definidos na cli com o — lock-env ou o — lock-conf não poderão mais ser atualizados.

_ACP2E-3324 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

#### Magento_GraphQl executa o processamento de cabeçalhos mesmo se o valor do cabeçalho não passar na validação

O sistema agora garante que o processamento de cabeçalho seja executado apenas uma vez e somente se o valor do cabeçalho passar na validação, melhorando a segurança e evitando possíveis vulnerabilidades. Anteriormente, o processamento de cabeçalho era executado mesmo se o valor do cabeçalho não passasse na validação, resultando em possíveis vulnerabilidades e comportamento inesperado devido ao processamento duplo dos valores do cabeçalho.

_AC-11729 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### As opções de Cartão Presente Físico não têm a ordem de classificação correta

O sistema agora classifica corretamente as opções de produtos de cartão-presente físico quando consultado via GraphQL, garantindo uma renderização consistente com o tema Luma. Anteriormente, a ordem de classificação estava incorreta de acordo com o tema da Luma, resultando na exibição e na ordenação incorretas de opções como nome do remetente, nome do destinatário e quantidade.

_AC-8951 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### O Cache do Resolvedor [GraphQL] é Invalidado ao Criar/Editar/Mover/Excluir uma Atualização de Preparo

O sistema agora garante que o cache do resolvedor não seja invalidado ao criar, editar, mover ou excluir uma atualização de preparo, mas somente quando a atualização de preparo for aplicada à entidade. Anteriormente, o cache de resolvedor era invalidado prematuramente, mesmo antes da atualização de preparo ser aplicada, o que resultava em invalidações desnecessárias do cache.

_AC-9157 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### O cache do Fastly não foi limpo para a atualização do preparo de conteúdo

Agora, o GraphQL com o cache de resposta de conteúdo do PageBuilder é invalidado quando as entidades relacionadas ao conteúdo do PageBuilder são atualizadas.

_ACP2E-2642 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Desativar a navegação em camadas - Não remove a agregação do Graphql

O problema foi corrigido após a aplicação da verificação ao solicitar uma pesquisa de produto com agregações de categoria por meio de uma consulta do GraphQL quando a definição de configuração de administrador de &quot;Catálogo > Navegação em camadas > Exibir filtro de categoria&quot;.

_ACP2E-2653 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### A chamada de Produtos GraphQL contendo o filtro de preço `&lbrace;from:&quot;0&quot;&rbrace;` não retorna nenhum resultado

Anteriormente, a pesquisa de produtos graphql com o filtro para preços zero não retornava nenhum resultado devido a uma exceção lançada. Agora, a pesquisa retorna os resultados conforme esperado.

_ACP2E-2928 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Traduções para atributos de retorno do cliente não refletidas na API do GraphQL para o respectivo StoreView

As traduções para atributos de retorno do cliente são refletidas na API do GraphQL para o respectivo StoreView.
Anteriormente, os atributos de Retorno do cliente para o respectivo StoreView não eram refletidos na API do GraphQL.

_ACP2E-2974 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Nuvem] chamada de GraphQL interrompida para getPurchaseOrder com cotação de nó

A chamada GraphQL da Ordem de Compra poderá executar a tarefa sem encontrar erros internos no servidor.

_ACP2E-3128 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Produtos Configuráveis da [Cloud] não mostrados no Site de Produção se o Produto não estiver habilitado em &quot;Todas as Exibições da Loja&quot;

O sistema agora exibe corretamente os produtos configuráveis no site, mesmo que o produto não esteja habilitado em &quot;Todas as exibições da loja&quot;, mas esteja habilitado em escopos específicos de exibição da loja.
Anteriormente, se um produto era desativado em &quot;Todas as exibições da loja&quot; e ativado apenas em escopos de exibição da loja específicos, os atributos do produto não eram exibidos corretamente na resposta do GraphQL, fazendo com que o produto não fosse exibido corretamente.

_ACP2E-3184 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/3f300077)_

#### Graphql de produtos da [Cloud] apresentando erro quando o mesmo produto simples foi atribuído a vários produtos configuráveis

Anteriormente, com produtos configuráveis separados com o mesmo produto simples, o grapQL retornava um erro. Depois que essa correção se aplica, diferentes produtos configuráveis com o mesmo produto simples, o grapQL retorna o resultado sem erros.

_ACP2E-3190 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Problema na &lbrace;Cloud] com Autenticação de Usuário e Acesso a Token Entre Sites na Instalação de Vários Sites

As consultas de informações do cliente e do carrinho do GraphQl na configuração de vários sites verificam se o cliente em um site não padrão existe.
Anteriormente, a consulta funcionava sem verificar se o cliente existe em um site não padrão na configuração de vários sites.

_ACP2E-3215 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Itens do carrinho de GraphQLA paginação V2 não está funcionando corretamente

O problema foi corrigido transmitindo o valor correto para o argumento da página atual na consulta de coleção. Anteriormente, o valor errado era passado para definir a página atual, causando o problema.

_ACP2E-3253 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### O valor do modelo [GRAPHQL] deve ser especificado ao obter o customerCart

A consulta &quot;customerCart&quot; do GraphQL agora pode criar um carrinho vazio mesmo quando a cotação não está disponível no banco de dados. Anteriormente, essa operação falhava devido a problemas de validação de país ao criar o carrinho vazio.

_ACP2E-3255 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [GraphQl] Os itens da lista de desejos são visíveis via GraphQl, mas não são visíveis na loja

Os produtos da lista de desejos não estão sendo listados corretamente quando solicitados pelo GraphQL. Agora, os produtos da lista de desejos são filtrados com base no contexto de loja fornecido.

_ACP2E-3380 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/55615e61)_

#### [GraphQL] Redefine a inconsistência de email da senha entre o conteúdo e o assunto/link

O problema foi resolvido simulando a loja correta em que a conta do cliente é registrada ao enviar a solicitação de redefinição de senha, independentemente da loja do site.

_ACP2E-3404 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### A consulta de produtos do GraphQL [Cloud] retorna produtos relacionados não atribuídos ao site atual

Anteriormente, para consultas de GraphQL, os produtos relacionados a várias lojas não eram exibidos corretamente para consultas de produtos. Depois que essa correção é aplicada, para produtos, os produtos relacionados a várias lojas de consulta de graphQL são exibidos de acordo.

_ACP2E-3419 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### O uso da ID de armazenamento incorreta no cabeçalho do GraphQL causa um erro de memória fatal

O envio de código de armazenamento incorreto na solicitação do GraphQL não resulta mais em consumo excessivo de memória.

_ACP2E-3447 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Resposta 500 da [Cloud] para resposta Graphql vazia na 2.4.7

Após a correção, as solicitações graphql inválidas não serão registradas no arquivo exception.log.

_ACP2E-3467 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [Problemas de &lbrace;Cloud] com a API Graphql

Antes da correção com o uso do servidor de aplicativos Graphql, a solicitação de endereço do cliente não retornava os dados mais recentes.

_ACP2E-3492 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### O produto desabilitado ainda aparece em itens relacionados, de venda adicional e de venda cruzada na consulta do GraphQL

O Graphql agora fornece a resposta correta para produtos de remarketing, venda adicional e venda cruzada com deficiência

_ACP2E-3505 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [NUVEM]: erro do GraphQl Erro interno do servidor, mutação placeOrder

A mutação &quot;placeOrder&quot; com informações de código de cupom na solicitação não está mais gerando uma exceção de erro interno, o pedido foi feito com sucesso. Anteriormente, falhava com &quot;Erro interno de servidor&quot;.

_ACP2E-3647 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/982b1c42)_

#### A discount_percentage não é calculada para produtos de pacote com preço dinâmico

Correção adicionada para discount_percentage de product.price_details não mostrando o valor correto para produtos agrupados com preço dinâmico ativado e cupom de desconto aplicado.

_LYNX-426_

#### O pacote de produtos ainda exibe &quot;IN_STOCK&quot; quando um de seus produtos agrupados está esgotado

Solução do problema em que os produtos agrupados ainda exibiam &quot;IN_STOCK&quot; mesmo quando um de seus produtos agrupados estava esgotado.

_LYNX-485_

#### not_available_message e only_x_left_in_stock não mostram o mesmo estoque disponível

Solução do problema em que not_available_message e only_x_left_in_stock exibiam disponibilidade de estoque inconsistente

_LYNX-486_

#### campo original_row_total retornando valor incorreto

Solução do problema com o campo original_row_total, que retornava valores incorretos quando opções personalizadas eram selecionadas

_LYNX-488_

#### A miniatura do produto agrupado deve ser mostrada de acordo com a configuração     .

Solução do problema para garantir que a miniatura do produto agrupado seja exibida de acordo com as configurações

_LYNX-503_

#### original_item_price não inclui descontos

Atualização de original_item_price para incluir descontos.

_LYNX-512_

#### A mensagem não disponível não mostra a quantidade de estoque disponível

Correção da mensagem de erro e do código de erro da mutação AddProductsToCart para alinhar-se à configuração de mensagem &quot;não disponível&quot;

_LYNX-530_

#### O status &quot;OUT_OF_STOCK&quot; retorna em Simples com opções personalizadas produtos com opções de seleção múltipla

O resolvedor StockStatusProvider no pacote de inventário foi atualizado para corrigir o stock_status de produtos simples com opções personalizadas.

_LYNX-532_

#### Erro (GQL): cart.itemsV2.items.product.custom_attributesV2 retorna um erro de servidor

Correção do erro de servidor que ocorria quando uma consulta de carrinho incluía atributos personalizados de um produto adicionando um produto sem atributos personalizados.

_LYNX-533_

#### orders/date_of_first_order sempre retornando nulo

Solução do problema em que pedidos > date_of_first_order sempre retornava um valor nulo.

_LYNX-536_

#### O cliente não poderá cancelar uma ordem parcialmente remetida

A validação foi adicionada para impedir que os clientes cancelem uma ordem parcialmente entregue.

_LYNX-544_

#### Códigos de erro para cancelamento de pedido com base na mensagem de erro

Os códigos de erro para cancelamento de pedido agora se baseiam na mensagem de erro específica.

_LYNX-548_

#### Voltar as propriedades relacionadas a cookies de particular para protegido

Reverte a visibilidade das propriedades do construtor de classe Magento\Framework\App\PageCache\Version de private para protected

_LYNX-581_

#### Aumente a complexidade máxima de consulta padrão do GraphQL para 1000

Aumento da complexidade máxima padrão de consulta do GraphQL de 300 para 1000.

_LYNX-600_

#### GQL - itemsV2 > Total da linha original, os preços da faixa de preços são retornados como US$ 0,00 para o produto para download com opções de arquivo com preços separados.

Solução de um problema em que os produtos baixáveis com opções de compra de link separadas ativadas retornavam US$ 0 para os itens V2 > Total da linha original, faixa de preço retornada como US$ 0,00 para os produtos com opções de arquivo com preços separados.

_LYNX-620_

#### Compatibilidade GraphQl para a versão PHP-8.4

Correção de problemas de compatibilidade do GraphQL com o PHP 8.4 em vários resolvedores, garantindo uma funcionalidade sem problemas. Atualização dos arquivos afetados nos módulos CatalogRule, Customer, GiftMessage, GiftCard e GiftWrapping.

_LYNX-772_

### GraphQL, Inventário / MSI

#### A mutação MergeCart aciona uma exceção quando os carrinhos de origem e de destino têm os mesmos itens de pacote

&quot;-

_ACP2E-2607 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c971859e) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, Inventário / MSI, Desempenho

#### Site inativo após atualização

O desempenho da busca de pacotes de produtos por meio do GraphQl foi aprimorado.

_ACP2E-1716 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ba25af8a) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, Desempenho

#### [GraphQL Resolver] Os Dados Do Customer Resolver Não São Invalidados Na Importação

O cache do resolvedor de clientes do GraphQL agora é invalidado, conforme esperado, quando um cliente é editado ou excluído por meio de importações. Anteriormente, o cache não era invalidado e os dados do cliente podiam ser editados ou excluídos durante a importação.

_AC-9569 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, Pesquisar

#### A classificação da lista de produtos do GraphQL por vários parâmetros não funciona

A classificação de produtos por vários campos no GraphQl agora funciona conforme descrito na documentação

_ACP2E-2809 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Consulta GraphQL de lista de produtos limitada a total_count somente 10.000 produtos

Após a correção, o resultado da pesquisa não se limita a 10000 produtos, é possível obter todos os produtos que correspondem aos critérios da pesquisa mesmo que a contagem seja superior a 10000.

_ACP2E-948 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, Estrutura de teste

#### Falha no teste de integração do Magento\GraphQl\App\GraphQlCustomerMutationsTest.php

&quot;-

_ACP2E-3363 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Importar/exportar

#### Problema na importação do produto quando fornecido com o tipo de opções personalizadas: arquivo (o Produto criado não contém o preço da opção personalizada e mostra apenas a primeira extensão de tipo de arquivo fornecida)

O sistema agora importa corretamente os dados do produto com opções personalizadas do tipo &quot;arquivo&quot;, garantindo que todas as extensões de arquivo fornecidas sejam exibidas e o preço da opção personalizada seja incluído. Anteriormente, durante a importação do produto, se uma opção personalizada do tipo &quot;arquivo&quot; fosse fornecida com mais de uma extensão de arquivo, somente a primeira extensão era exibida e o preço da opção personalizada não era exibido.

_AC-12172 - [Problema do GitHub](https://github.com/magento/magento2/issues/38805) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38926)_

#### Tempo de execução incorreto para a operação de importação na grade Histórico de Importação

O tempo de execução do relatório de importação é mostrado corretamente, independentemente da localidade do administrador.

_ACP2E-2710 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Clientes duplicados que estão sendo criados com o mesmo endereço de email usando importar

Importação do cliente enquanto o Compartilhamento de conta estiver definido como Global, o cliente importado que existe no sistema será atualizado.
O cliente importado anteriormente foi duplicado.

_ACP2E-2737 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Adicionar/atualizar importação em produtos duplicando opções personalizáveis

O problema foi resolvido com a atribuição da loja correta às opções do produto durante as importações de opções do produto em CSV.
Anteriormente, o era atribuído ao armazenamento de administração em vez do respectivo armazenamento.

_ACP2E-2902 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Data &quot;created_at&quot; do cliente Não convertida para armazenar fuso horário na exportação

Um valor de data da coluna &#39;created_at&#39; é convertido no formato de data apropriado com base no fuso horário da loja na seção CSV de exportação do cliente.

_ACP2E-2990 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### [Nuvem] Obtendo erro ao verificar os dados nos dados de importação usando CSV

Não há erros ao verificar os dados durante a importação de CSV. Anteriormente, a mensagem de erro exibida era: &quot;Não é possível encontrar um cliente que corresponda a esse email e código do site na(s) linha(s): 1&quot; ao verificar os dados na seção de importação usando o CSV do administrador.

_ACP2E-3165 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Botão Importar ausente

Resolva o problema de falta do botão Importar após as verificações de dados com registros corretos e incorretos no CSV. Anteriormente, o botão Importar não era exibido após as verificações de dados com registros corretos e incorretos no CSV.

_ACP2E-3172 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1819fe73)_

#### O endereço do cliente exportado não pode ser importado

A importação do endereço do cliente continuará conforme esperado. Anteriormente, um arquivo de importação de endereço de cliente não passaria na validação se Compartilhar contas de cliente = Global, e há dois sites em que o site padrão tem uma lista de países restrita, e o endereço que está sendo importado é de outro site em que os países permitidos são diferentes

_ACP2E-3382 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Nuvem] Quantidade incorreta no arquivo CSV não deu erro

Agora, a importação de origens de estoque lançará um erro de validação para valores não numéricos na coluna de quantidade. Anteriormente, a importação de origens de estoque com valor não numérico na coluna de quantidade resultava na definição da quantidade como 0.

_ACP2E-3448 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

#### Mensagem de erro de chave de URL duplicada gerada ao importar um produto não está correta quando a chave de URL já pertence a uma categoria

Exibição da mensagem de erro correta durante a verificação de importação do produto, quando o cliente tentou importar o produto quando a chave url do produto já pertencia a uma categoria.

_ACP2E-3455 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### A exportação de produtos provoca OOM mesmo com limite de memória 4G

Antes dessa correção, a exportação do produto falhava se os atributos do produto tivessem milhares de valores de opção mesmo com memória 4G disponível. Após essa correção, a exportação do produto deve concluir a exportação do arquivo csv.

_ACP2E-3475 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [Processos De Importação Da &lbrace;Cloud] Que Interferem Entre Si

Mensagens corretas serão exibidas se o mesmo usuário administrador executar duas ou mais operações de importação usando a mesma sessão de usuário.

_ACP2E-3527 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Importação/exportação, desempenho

#### O tempo de importação do produto [Cloud] aumentou significativamente

Antes da correção, a importação de produtos do catálogo com mais de 10 mil entradas tinha uma degradação de tempo significativa. Após a correção, a importação do produto de catálogo é executada em tempo hábil.

_ACP2E-3476 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/87d012e5)_

### Instalar e administrar

#### Falha na atualização do Magento no MariaDB 11.4 + 2.4.8-beta1

A atualização deve ocorrer sem erros.

_AC-13242 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7b336d0a)_

#### Não Exportar VCL para o botão Verniz 7 no painel de administração

O botão &quot;Exportar VCL para Verniz 7&quot; foi adicionado ao painel de Administração.

_ACP2E-2102 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventário / MSI

#### A atualização de inventário de produtos configuráveis falha quando o banco de dados usa prefixos

O sistema agora atualiza corretamente o inventário de produtos configuráveis quando o banco de dados usa prefixos, evitando mensagens de erro e garantindo que a quantidade correta seja salva. Anteriormente, ocorria um erro ao tentar salvar a quantidade de estoque de produtos simples em um produto configurável se o banco de dados estivesse usando prefixos.

_AC-10750 - [Problema do GitHub](https://github.com/magento/magento2/issues/38045)_

#### A chave de API do Google Google não está funcionando ao adicionar o Mapa com atributos

O sistema agora é compatível com a versão mais recente da API do Google Maps 3.56, permitindo que os usuários adicionem com êxito um bloco de conteúdo do Mapa do menu do PageBuilder ao estágio sem encontrar erros. Anteriormente, os usuários não conseguiam adicionar um bloco de conteúdo do Mapa devido a problemas de compatibilidade com a versão da API do Google Maps, resultando em uma mensagem de erro &quot;algo deu errado&quot;.

_AC-11593 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### Não é possível criar remessa para item do pedido com várias fontes e SKU corrompido

Anteriormente, quando espaços foram adicionados por engano no SKU por meio do banco de dados, ocorre um erro na página de remessa, que agora é fixa e o corte automático é considerado um erro humano e nenhum impacto foi encontrado. Portanto, o envio foi criado com êxito.

_AC-13922 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/c18eb5fa)_

#### [Testar] agrupar produtos com 0 inventário sendo exibido na loja

O produto do pacote não é exibido nos sites adicionais usando o estoque adicional.

_ACP2E-1411_

#### [Problema crítico] da nuvem com a listagem de produtos com espaços vazios

O sistema agora exibe corretamente as listagens de produtos sem espaços vazios quando os produtos estão definidos como &quot;Fora de estoque&quot;, garantindo uma exibição consistente e precisa dos produtos disponíveis. Anteriormente, definir um produto como &quot;Fora de estoque&quot; resultava na exibição de um espaço vazio na lista de produtos, interrompendo o layout e causando confusão aos clientes.

_ACP2E-2794 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ea79f7dd) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/b59e48ca)_

#### Não é possível entregar a ordem quando o armazenamento de retirada MSI está ativado

Desempenho de inventário aprimorado para criar remessa no caso de muitas origens com retirada na loja

_ACP2E-3335 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### A reindexação do Cron não atualiza a disponibilidade do produto no front-end

Anteriormente, os produtos permaneciam indisponíveis no front-end após a atualização do status do backorder por meio da API REST. Agora, depois de atualizar o status do backorder por meio da API REST, os produtos são mostrados como em estoque.

_ACP2E-3355 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/e6fe0aa7)_

#### A adição de imagens ao configurável não funciona quando o MSI está habilitado.

O upload de imagem para o produto configurável agora funcionará conforme esperado quando o módulo de inventário for usado. Anteriormente, o upload da imagem não funcionava

_ACP2E-3357 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/fdf409aa)_

#### Problema com o pacote de produto + MSI no Clean M2.4.7-p3

Anteriormente, para produtos de pacote de estoque após a duplicação com o mesmo produto simples, o produto simples não pode ser salvo. Depois que essa correção é aplicada, o produto simples pode ser salvo com sucesso sem exceções.

_ACP2E-3470 - [Problema do GitHub](https://github.com/magento/magento2/issues/39358) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/0208e433)_

### Inventário / MSI, pesquisa

#### Todos os produtos são indexados com [is_out_of_stock] = 1 quando o SKU não está definido como um atributo pesquisável

Após a correção, o &quot;is_out_of_stock&quot; no índice de pesquisa do catálogo estará correto, mesmo quando o SKU não for pesquisável.

_ACP2E-3413 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

### Pedido

#### Tela de visão geral da ordem de backend: quantidade com backorder não visível no nível do item da ordem

O sistema agora exibe o número de itens com backorder na coluna de quantidade na tela de visão geral do pedido de backend. Isso garante que os usuários possam rastrear com precisão o status de todos os itens em um pedido. Anteriormente, a coluna de quantidade mostrava apenas o número de itens encomendados, faturados e entregues, mas não exibia o número de itens com backorder.

_AC-10828 - [Problema do GitHub](https://github.com/magento/magento2/issues/38252) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38320)_

#### [Problema] ID de armazenamento incorreta usada no Renderizador de Endereço de Pedido

O sistema agora usa corretamente a ID da loja associada a um pedido ao renderizar o endereço do pedido, garantindo que os endereços sejam formatados corretamente de acordo com sua respectiva ID da loja. Anteriormente, o sistema estava usando incorretamente a ID da loja atual, o que poderia resultar na formatação incorreta do endereço nos casos em que vários emails de pedidos de lojas diferentes precisavam ser enviados.

_AC-10994 - [Problema do GitHub](https://github.com/magento/magento2/issues/38412) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37932)_

#### Problema de cache do JoinProcessor

O sistema agora aplica corretamente o JoinProcessor para cada iteração, mesmo com chamadas consecutivas, garantindo uma recuperação de dados precisa. Anteriormente, o JoinProcessor era marcado incorretamente como já aplicado em iterações consecutivas, resultando em erros na recuperação de dados.

_AC-11690 - [Problema do GitHub](https://github.com/magento/magento2/issues/27504) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37550)_

#### [Problema] Preço de envio mostrando diferenças no PDF impresso

O sistema agora exibe corretamente os preços de envio em PDFs impressos de acordo com as configurações de imposto, garantindo a consistência entre a página de exibição da fatura da ordem de venda e a fatura impressa. Anteriormente, o preço de envio exibido no PDF impresso excluía impostos, independentemente das configurações de imposto.

_AC-11798 - [Problema do GitHub](https://github.com/magento/magento2/issues/38608) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38595) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### Reordenar com um produto configurável principal excluído

Agora, ao reordenar com o produto excluído, o sistema não mostrará o botão de reordenação para reordenar

_AC-13839 - [Problema do GitHub](https://github.com/magento/magento2/issues/39568) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39601)_

#### [Problema] Correção incorreta \Magento\Sales\Model\Order\Email\Container\Template:$id property

Isso corrige o phpdoc inválido para \Magento\Sales\Model\Order\Email\Container\Template::$id, na verdade $id é do tipo int, mas na realidade é string.

_AC-13924 - [Problema do GitHub](https://github.com/magento/magento2/issues/39151) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39150)_

#### Não é possível salvar alterações no número de telefone nos detalhes do pedido existente

Agora o usuário pode adicionar o prefixo internacional 00 no campo de telefone do endereço do pedido

_ACP2E-2622 - [Problema do GitHub](https://github.com/magento/magento2/issues/38201) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### Falha no envio de emails

O sistema agora inclui uma opção de configuração async_sending_tries para especificar o número de tentativas de envio de um e-mail antes de parar, melhorando o tratamento de envios de e-mail com falha quando o &quot;Envio assíncrono&quot; estiver ativado. Anteriormente, se ocorresse uma falha no envio de um email, o sistema tentaria continuamente reenviá-lo, resultando em um loop infinito de mensagens de erro no log do sistema.

_ACP2E-2734 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [Nuvem] Status do Pedido alterado para concluído quando o reembolso parcial de um pedido parcialmente enviado

Ao emitir um aviso de crédito, o status da ordem não é mais alterado para &quot;concluído&quot; se houver itens que ainda não foram entregues.

_ACP2E-2756 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### [A NUVEM] Não Pode Desabilitar o Envio de Emails da Interface do Usuário do Administrador, Como mostra o Dev Docs

O sistema agora impede corretamente que emails de vendas sejam enviados quando a comunicação por email está desativada. Esses emails não serão mais enviados quando a comunicação por email for reativada. Anteriormente, os emails de vendas iniciados enquanto a comunicação por email estava desativada ainda eram enviados assim que a comunicação por email era reativada.

_ACP2E-3002 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Ordem fechada sem reembolso total

O sistema agora mantém corretamente o status do pedido como &#39;Processando&#39; e o status da NFF como &#39;Pendente&#39; quando um pedido com um pagamento não capturado tem uma entrega criada. Isso garante que os pedidos só sejam marcados como &quot;Fechados&quot; depois de serem totalmente reembolsados. Anteriormente, a criação de uma entrega para uma ordem com uma fatura pendente alterava incorretamente o status da ordem para &#39;Fechado&#39;.

_ACP2E-3045 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### [Nuvem] Não é possível criar ordem no administrador em uma loja se apenas o Endereço de Cobrança Padrão não foi configurado

Agora há uma mensagem de erro relevante &quot;Um cliente com o mesmo endereço de email já existe em um site associado&quot;. é exibido se um cliente não tiver um Endereço de cobrança padrão e tentar criar um pedido em outra loja.

_ACP2E-3311 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Solicitações de colocação de ordem duplicadas do administrador enviadas

Anteriormente, o botão &quot;Enviar pedido&quot; no painel de administração podia ser clicado várias vezes ou ativado ao pressionar repetidamente a tecla &quot;Inserir&quot;, causando duplicatas ou envios de pedidos com erro. Agora, evitando ações adicionais até que o pedido seja totalmente processado, garantindo que apenas um pedido seja enviado.

_ACP2E-3416 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### O administrador ainda pode fazer o pedido mesmo sem o método de pagamento

O método de pagamento selecionado anteriormente agora será retido quando o método de pagamento reaparecer na lista de pagamentos disponíveis.

_ACP2E-3425 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

### Ordem, Pagamentos

#### O administrador ainda pode fazer o pedido mesmo sem o método de pagamento

Anteriormente, o comerciante podia fazer pedidos pelo painel de administração sem selecionar um método de pagamento. Agora, o comerciante precisa de um método de pagamento para continuar com a realização de um pedido.

_ACP2E-3233 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

### Ordem, Devoluções

#### O reembolso de ordem resulta em aviso de crédito duplicado

A emissão do reembolso sobre a API REST quando duas solicitações idênticas foram executadas simultaneamente não criará mais avisos de crédito duplicados.

_ACP2E-2982 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Pedido, Imposto

#### [NUVEM] base_row_total incorreto na API de ordem RESTFUL ao habilitar transações transfronteiriças e aplicar descontos de cupom

Agora, base_row_total correto é retornado da API de ordem RESTFUL quando a transação transfronteiriça é ativada e o desconto do cupom é aplicado.

_ACP2E-3003 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9af794a4)_

### Outro

#### cookie private_content_version retornado em consultas GQL

Correção de um problema em que o cookie private_content_version era retornado em consultas do GraphQL, mesmo quando o cookie da sessão estava desativado. O cookie não é mais incluído nas respostas do GraphQL quando a sessão é desativada, conforme esperado.

_LYNX-339_

#### O atributo is_available em CartItemInterface retorna sempre false para produtos configuráveis

Correção de um problema em que o atributo is_available em CartItemInterface sempre retornava false para produtos configuráveis no estoque. Agora, ele reflete corretamente a disponibilidade como verdadeira quando aplicável.

_LYNX-380_

#### O atributo is_available em CartItemInterface retorna true mesmo quando o estoque vendável é inferior à quantidade do produto

Correção do problema em que o atributo is_available no CartItemInterface retornava incorretamente true, mesmo quando a quantidade do item do carrinho excedia o estoque vendável.

_LYNX-382_

#### A miniatura do espaço reservado retorna quando um produto simples adicionado ao carrinho em um produto agrupado

Correção de um problema em que a adição de um produto simples (parte de um produto agrupado) ao carrinho retornava uma imagem em miniatura de espaço reservado, mesmo quando o produto tinha uma imagem atribuída.
Detalhes da correção:
- A miniatura do produto agora exibe corretamente a imagem atribuída, se disponível.
- A seleção da miniatura respeita a configuração do administrador em:
Lojas > Configuração > Vendas > Check-out > Carrinho de compras > Imagem de produto agrupada.
Isso garante um comportamento consistente de miniaturas para produtos agrupados com base nas configurações da loja.

_LYNX-399_

#### Os atributos de opção personalizados do cliente não funcionam com valores inteiros

Correção de um problema em que os atributos de opção personalizados do cliente não funcionavam quando o valor retornado era um número inteiro. Agora, as opções personalizadas lidam corretamente com valores inteiros e os retornam conforme esperado.

_LYNX-400_

#### Erro interno do servidor ao tentar obter priceDetails para produtos do pacote com preço dinâmico

Solução de um problema em que a consulta de price_details para pacotes de produtos com preços dinâmicos via GraphQL resultava em um erro interno do servidor. Esse aprimoramento garante consultas estáveis do carrinho ao trabalhar com produtos de pacote configurados com preços dinâmicos.

_LYNX-402_

#### only_x_left_in_stock sempre retorna 0 para produtos configuráveis

Solução de um problema em que o atributo only_x_left_in_stock sempre retornava 0 para produtos configuráveis quando adicionado usando o SKU principal com opções.
Detalhes da correção:
- O valor only_x_left_in_stock agora reflete com precisão o estoque da variante secundária selecionada, em vez do SKU principal.
- Isso garante que os níveis de estoque sejam exibidos corretamente para variações de produtos configuráveis no carrinho e nas páginas do produto.

_LYNX-403_

#### A consulta do GraphQL não retorna o preço regular calculado correto para produtos personalizáveis

Correção de um problema em que a GraphQL não retornava o preço normal calculado correto para produtos personalizáveis. A consulta agora inclui corretamente o preço regular calculado com valores personalizáveis aplicados (por exemplo, US$ 125) na propriedade price, refletindo o preço base e quaisquer custos adicionais de personalização.

_LYNX-411_

#### AppliedTaxes via EstimatedTotals persistem com mutações atualizadas

Correção de um problema com a mutação EstimatedTotals em que os impostos aplicados persistiam em um carrinho mesmo após atualizar a região ou o código postal. A mutação agora atualiza corretamente os impostos aplicados ao alterar entre valores de região e código postal, garantindo que somente a regra de imposto correta seja aplicada com base nos dados atuais do carrinho.

_LYNX-412_

#### O atributo is_available em CartItemInterface retorna true mesmo quando o estoque vendável é inferior à quantidade do produto

Correção de um problema em que o atributo is_available em CartItemInterface retornava incorretamente true, mesmo quando o estoque comercializável era inferior à quantidade de produto solicitada. O campo is_available agora retorna corretamente false quando a quantidade do produto excede o estoque disponível.

_LYNX-420_

#### Preço normal do produto com 12 decimais e valor incorreto

Correção de um problema em que o valor regular_price nos caminhos GraphQL product.price_range.maximum_price e minimum_price não correspondia ao preço do catálogo quando várias taxas de imposto eram aplicadas. O regular_price agora reflete consistentemente o preço do catálogo em todas as configurações de imposto, garantindo um preço unitário preciso, cálculos de custo de linha total e verificações de desconto no Sumário do Carrinho.

_LYNX-425_

#### Erro de servidor do GraphQL no carrinho com produto empacotado esgotado

Correção de um problema em que o GraphQL retornava um erro interno do servidor ao buscar um carrinho contendo um produto empacotado com um item indisponível, especificamente quando a consulta incluía a propriedade itemsV2. O GraphQL agora retorna corretamente uma lista de itens com mensagens de erro relevantes anexadas à entrada do item de produto agrupado, conforme esperado.

_LYNX-430_

#### Não é possível criar um endereço com atributos personalizados

Correção de um problema com a mutação createCustomerAddress que impedia a criação de endereços com atributos personalizados necessários. A mutação agora lida corretamente com atributos de endereço personalizados quando a carga útil apropriada é fornecida.

_LYNX-441_

#### Erro de servidor do GraphQL no carrinho com only_x_left_in_stock no produto empacotado

Correção de um problema em que a busca de um carrinho contendo um produto incluído no campo only_x_left_in_stock na consulta do GraphQL resultava em um erro interno do servidor. Agora, o GraphQL retorna corretamente um flutuante ou nulo para o campo only_x_left_in_stock sem erros.

_LYNX-447_

#### Erro do GraphQL ao remover outros produtos com produto configurável insuficiente no carrinho

Correção de um problema em que a tentativa de remover produtos em estoque do carrinho resultava em um erro do GraphQL &quot;A quantidade solicitada não está disponível&quot; se o carrinho também contivesse produtos configuráveis com estoque insuficiente. A remoção agora funciona como esperado sem disparar erros.

_LYNX-464_

#### Não é possível adicionar produtos porque o SKU em mutação diferencia maiúsculas de minúsculas

Solução de um problema em que a mutação addProductsToCart retornava um erro &quot;PRODUCT_NOT_FOUND&quot; ao usar SKUs com invólucro diferente. A mutação agora lida com SKUs sem distinção entre maiúsculas e minúsculas, garantindo consistência com consultas do Serviço de catálogo e comportamento de PDP.

_LYNX-469_

#### Atributo do produto > formulário curto da marca comercial &trade; é retornado como &trade;

Solução de um problema de codificação de caracteres com o nome do produto para a API do GraphQL

_LYNX-603_

#### problema de mutação updateCustomerEmail

Solução de um problema com a mutação updateCustomerEmail em que clientes sem atributos personalizados necessários (adicionados após a criação da conta) não podiam atualizar seus emails.

_LYNX-619_

#### Mutation setShippingAddressesOnCart gera um erro ao usar pickup_location_code

Correção de um problema em que a mutação setShippingAddressesOnCart retornava um erro ao usar pickup_location_code sem especificar customer_address_id ou address. A mutação agora permite corretamente configurar um endereço de entrega com apenas o pickup_location_code.

_LYNX-626_

#### Compatibilidade da loja - atualize a lógica para obter o nome da tabela com o prefixo e outras melhorias secundárias

Atualização da lógica para recuperar o nome da tabela com o prefixo (relacionado às alterações no SCP).

_LYNX-637_

#### salvar no catálogo de endereços não funciona ao usar o campo same_as_shipping do setBillingAddressOnCart GQL

Correção de um problema em que o endereço de entrega não era salvo no catálogo de endereços do cliente ao usar a mutação de GraphQL setBillingAddressOnCart com o campo same_as_shipping definido como true. Agora, o endereço de entrega é armazenado corretamente conforme esperado.

_LYNX-643_

#### Padronizar o order_id em mutações

Padronização da entrada order_id em mutações e atualização do modelo de email de confirmação de cancelamento da ordem para expor a id de incremento em vez da id da ordem.

_LYNX-650_

#### CustomerOrder não está exibindo os comentários do pedido

Solução de um problema com a Ordem do cliente para incluir comentários sobre a ordem em consultas da GraphQL de convidados e clientes.

_LYNX-651_

#### original_item_price não deve incluir nenhum desconto

Atualização da lógica de original_item_price em Preços de item do carrinho de GraphQL para excluir descontos.

_LYNX-652_

#### O pacote de produtos ainda exibe &quot;IN_STOCK&quot; quando um de seus produtos agrupados está esgotado

Solução de um problema em que product.stock_status de produtos de pacote ainda exibia &quot;IN_STOCK&quot; mesmo quando um dos itens agrupados estava indisponível.

_LYNX-681_

#### a consulta de cliente retorna Erro Interno do Servidor se o valor do atributo personalizado excluído existir para um cliente

Correção do problema em que a consulta do cliente retornava um erro interno do servidor quando um atributo personalizado excluído ainda tinha um valor armazenado. Agora, uma mensagem de erro apropriada será retornada se um atributo não existente for solicitado. O cache necessário é invalidado ao excluir o atributo personalizado do cliente.

_LYNX-686_

#### Parâmetro de ação para links de confirmação de retorno e cancelamento

Parâmetro de ação adicionado para retornar e cancelar links relacionados ao email de confirmação

_LYNX-687_

#### O URL de confirmação do usuário convidado é redirecionado para a página de status do pedido porque está faltando orderRef

Adição do parâmetro orderRef ao link no email de confirmação de cancelamento da ordem do convidado

_LYNX-689_

#### Não é possível retornar nulo para o campo não anulável &quot;TaxItem.title&quot; no placeOrder GQL

Correção de um problema em que a mutação placeOrder falhava com um erro interno do servidor devido a um valor nulo para o campo não anulável TaxItem.title. Agora, o campo sempre retorna um valor válido, garantindo o sucesso do posicionamento do pedido.

_LYNX-699_

#### EstimateTotals: os descontos são nulos para tipos de produtos virtuais

Solução do problema com a mutação estimateTotals que retornava nulo para descontos quando um código de desconto era aplicado a um carrinho que continha produtos virtuais.

_LYNX-702_

#### O produto do pacote não retorna a porcentagem e o valor de desconto corretos

Novas propriedades &quot;catalog_discount&quot; e &quot;row_catalog_discount&quot; foram introduzidas para que os preços de item de catálogo exibam as quantias e as porcentagens de desconto corretas nos níveis de linha e de item único.

_LYNX-703_

#### Configuração da mensagem de presente no nível do produto

Correção de um problema em que as mensagens de presente não eram aplicadas no nível do produto quando desativadas globalmente. Agora, se as mensagens de presente estiverem habilitadas para um produto específico, elas poderão ser adicionadas com êxito usando a mutação updateCartItems e serão salvas e refletidas corretamente.

_LYNX-714_

#### cart.rules retorna um erro em vez de um array vazio caso nenhuma regra de carrinho ativa seja aplicada

Correção da consulta cart.rules para retornar um array vazio em vez de um erro quando nenhuma regra de carrinho ativa é aplicada.

_LYNX-757_

#### As chamadas do GraphQL com o método OPTIONS retornam o código de resposta 500 quando o pacote adobe-commerce/storefront-compatibility é instalado

Correção de um problema em que as chamadas do GraphQL que usavam o método OPTIONS retornavam um Erro interno de servidor 500 quando o pacote adobe-commerce/storefront-compatibility era instalado. O endpoint agora retorna corretamente uma resposta 200/204, conforme esperado.

_LYNX-778_

### Outras ferramentas de desenvolvedor

#### [Problema] Corrigir erro de sintaxe do HTML em visual.phtml

O sistema agora fecha corretamente a tag de início no arquivo visual.phtml, garantindo a sintaxe apropriada do HTML. Anteriormente, a tag de início não era fechada corretamente, causando um erro de sintaxe do HTML.

_AC-10658 - [Problema do GitHub](https://github.com/magento/magento2/issues/38247) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37457)_

#### [Problema] alterado para &quot;ativo&quot; no comando bin/magento maintenance:status

O sistema agora fornece mensagens de status mais precisas para o comando de modo de manutenção, alterando o status de &quot;ativo&quot; para &quot;ativado&quot; e de &quot;não ativo&quot; para &quot;desativado&quot;. Anteriormente, a mensagem de status para o comando de modo de manutenção era exibida como &quot;ativo&quot; ou &quot;não ativo&quot;, o que poderia causar confusão.

_AC-11474 - [Problema do GitHub](https://github.com/magento/magento2/issues/38486) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38410)_

#### Navegar na árvore de categorias leva a erros no Redis: &quot;A sessão Redis excedeu as conexões simultâneas&quot;

_AC-12571 - [Problema do GitHub](https://github.com/magento/magento2/issues/38851) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0611e750)_

#### Problemas de CSP combinados com dev/css/use_css_critical_path

O sistema agora carrega corretamente os arquivos CSS de forma assíncrona nas páginas de check-out, mesmo quando a configuração &quot;dev/css/use_css_critical_path&quot; está ativada, garantindo que essas páginas sejam renderizadas com os estilos CSS adequados. Anteriormente, uma Política de segurança de conteúdo (CSP) restrita impedia a execução do JavaScript em linha, o que fazia com que os arquivos CSS não fossem carregados conforme esperado.

_AC-12731 - [Problema do GitHub](https://github.com/magento/magento2/issues/39020) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39040)_

#### Usando tipo virtual para configurar plug-in, o método interceptor não pode ser gerado corretamente no comando `setup:di:compile`

O sistema agora gera corretamente métodos interceptores ao usar um tipo virtual para configurar um plug-in, garantindo resultados consistentes tanto pré-compilados quanto compilados em tempo de execução. Anteriormente, o sistema gerava resultados incorretos quando pré-compilado em comparação à compilação em tempo de execução.

_AC-13398 - [Problema do GitHub](https://github.com/magento/magento2/issues/33980) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38141)_

#### Os testes de unidade Adobe Commerce 2.4.7-p3 estão falhando

Nenhuma nota de versão é necessária.

_ACP2E-3631 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Métodos de pagamento/pagamento, Ordem

#### Fluxo de pagamento papal Os detalhes do cartão de crédito salvos para uso posterior não são exibidos na página de método de pagamento armazenado

Fluxo de pagamento papal anterior Os detalhes do cartão de crédito salvos para uso posterior não eram exibidos na página do método de pagamento armazenado, que agora contém detalhes do cartão de crédito fixo, são exibidos na página do método de pagamento armazenado.

_AC-13699 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Pagamentos

#### O pagamento por Cartão de Crédito (Link do Fluxo de Pagamento) não está funcionando

Erro ao obter mais cedo (o pagamento foi recusado) ao fazer o pedido com cartão de crédito após o pedido fixo ser feito com sucesso.

_AC-13414 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a68324bc)_

#### O fluxo de pagamento cria uma nova transação sempre que clicamos no botão Buscar na tela exibir transação

O sistema agora extrai corretamente as informações da transação sem criar uma nova transação de pagamento cada vez que o botão obter é clicado na tela de visualização da transação. Anteriormente, clicar no botão Buscar criaria incorretamente uma nova transação de pagamento para um pedido que já tinha sido pago.

_ACP2E-2841 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### A mensagem Paylater não é exibida no PDP para a conta de comerciante paypal canadense

O sistema agora exibe corretamente a mensagem do PayLater para contas de comerciante do PayPal canadense na Página de detalhes do produto (PDP) quando o país do comprador pode ser determinado a partir do endereço de faturamento da conta ou da remessa. Anteriormente, a mensagem do PayLater não era exibida devido a um parâmetro ausente, resultando em um erro no console do navegador.

_ACP2E-3028 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### O reembolso de pedido do PayPal resulta em aviso de crédito duplicado

Correção de uma emissão de simultaneidade de avisos de crédito criados pelo IPN para o serviço de pagamento do PayPal.

_ACP2E-3143 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### A regra de preço do carrinho não funciona para Paypal

O valor correto é mostrado no PayPal quando o desconto é aplicado pelo método de pagamento

_ACP2E-3163 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Usuários da [Nuvem] com uma função específica não podem fazer logon

O usuário administrador com a função que contém somente o acesso à Seção do PayPal agora pode fazer logon sem erros

_ACP2E-3208 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/66dea0de)_

### Desempenho

#### Problema de configurações de atributo de produto padrão

O sistema agora permite que os usuários desmarquem uma opção padrão para um atributo de produto, garantindo que o atributo nem sempre tenha um conjunto padrão. Anteriormente, uma vez que um padrão era definido para um atributo de produto, não havia como desmarcá-lo, resultando no atributo sempre ter um conjunto padrão.

_AC-11932 - [Problema do GitHub](https://github.com/magento/magento2/issues/38703) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problema] Limpeza de código, adicionar novo bloco de cabeçalho crítico e mover css crítico antes dos ativos

O sistema agora inclui um novo bloco de cabeçalho crítico e move CSS crítico antes dos ativos, permitindo mais personalização e otimização de desempenho no front-end. Anteriormente, o CSS crítico não era posicionado antes dos ativos, limitando as oportunidades de personalização e otimização.

_AC-12000 - [Problema do GitHub](https://github.com/magento/magento2/issues/38748) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/35580)_

#### A compilação de tema é interrompida quando o host mysql contém informações de porta

O sistema agora lida corretamente com a configuração do host MySQL, que inclui informações de porta, garantindo uma compilação bem-sucedida do tema. Anteriormente, a compilação de temas falharia se a configuração do host MySQL na conexão de banco de dados incluísse informações de porta.

_AC-12176 - [Problema do GitHub](https://github.com/magento/magento2/issues/38799) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38842)_

#### Suporte para CommandLoaderInterface do Symfony na CLI do Magento

Essa alteração reduz o tempo de inicialização do aplicativo Magento CLI, permitindo a inicialização adiada de comandos até que sejam necessários.

_AC-13471 - [Problema do GitHub](https://github.com/magento/magento2/issues/29266) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/29355)_

#### Problema de desempenho ao carregar atributos de produto nas regras do carrinho

Desempenho de consulta aprimorado para regras de vendas - de cerca de 150 ms a ms de dígito único.

_ACP2E-2494 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Desempenho de indexação parcial de preço

O desempenho de indexação parcial de preço foi aprimorado com a otimização de algumas consultas de exclusão usadas no processo de indexação.

_ACP2E-2673 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### O pedido é rejeitado na configuração de várias lojas ao usar o Processamento assíncrono de pedido + Termos e condições

Os pedidos feitos de sites não padrão com termos e condições ativados agora são processados.
Antes de serem automaticamente rejeitados.

_ACP2E-2850 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### A chamada da API Rest do pedido está demorando muito para ser executada

O sistema agora executa a chamada da API Rest do pedido em um período de tempo razoável, melhorando o desempenho ao buscar um grande número de pedidos. Anteriormente, a chamada da API Order Rest demorava muito para ser executada, causando atrasos ao recuperar um grande número de pedidos.

_ACP2E-2910 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/001e5188)_

### Preços

#### Magento2.4.6-p4 Pedido API preço em falta

O sistema agora exibe corretamente o preço de produtos simples quando consultados por meio da API do pedido, garantindo uma representação precisa dos dados. Anteriormente, o preço de produtos simples era exibido incorretamente como zero na resposta da API.

_AC-11810 - [Problema do GitHub](https://github.com/magento/magento2/issues/38603)_

#### Erro de arredondamento de centavo na regra de catálogo

_AC-13855 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/276e0acd)_

### Produto

#### Caracteres especiais no nome de produto associado configurável estão sendo convertidos em entidades do HTML.

O sistema agora retém corretamente caracteres especiais nos nomes de produtos associados ao editar um produto configurável, impedindo que sejam convertidos em entidades HTML. Anteriormente, os caracteres especiais nos nomes de produtos associados eram convertidos em entidades do HTML quando o produto configurável era editado.

_AC-10535 - [Problema do GitHub](https://github.com/magento/magento2/issues/38146) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38447)_

#### A função GetById do ProductRepository não cria a chave de cache correta

O sistema agora cria corretamente uma chave de cache na função GetById do ProductRepository, independentemente da ID do armazenamento ser passada como uma sequência ou um número inteiro. Isso garante que o produto seja recuperado da memória em chamadas subsequentes, melhorando o desempenho. Anteriormente, o sistema recuperava o produto do banco de dados sempre que a função era chamada, mesmo com os mesmos parâmetros, devido à criação incorreta da chave de cache.

_AC-10947 - [Problema do GitHub](https://github.com/magento/magento2/issues/38384) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38433)_

#### [Problema] [MFTF] Adicionou AdminClickAddOptionForBundleItemsActionGroup

O sistema agora inclui o AdminClickAddOptionForBundleItemsActionGroup, aprimorando a funcionalidade do painel de administração. Anteriormente, esse grupo de ação não estava disponível.

_AC-11992 - [Problema do GitHub](https://github.com/magento/magento2/issues/30857) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/30838)_

#### [Problema] Corrigir erro de digitação no bloco PHPDoc

O sistema agora remove corretamente uma variável referenciada desconhecida no PHPDoc para a declaração de variável $helper, melhorando a clareza e a precisão do código. Anteriormente, essa variável referenciada desconhecida no PHPDoc estava causando confusão e possíveis imprecisões no código.

_AC-13173 - [Problema do GitHub](https://github.com/magento/magento2/issues/38961) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38940)_

#### [Problema] Corrigido o pacote corrompido e o layout de páginas de produto baixáveis no Magento >= 2.4.7

O layout das páginas de produto agrupadas e baixáveis foi corrigido, garantindo uma exibição consistente e correta em todos os dispositivos. Anteriormente, essas páginas apresentavam problemas de layout devido a uma reorganização do bloco de mídia de informações do produto.

_AC-13423 - [Problema do GitHub](https://github.com/magento/magento2/issues/39403) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### AlertProcessor - Argumento #2 ($storeId) deve ser do tipo int, string fornecida

O sistema agora aciona corretamente os emails de alerta do produto, garantindo que o identificador da loja tenha o tipo de dados correto. Anteriormente, os emails de alerta do produto não eram enviados devido a uma incompatibilidade de tipo no identificador da loja.

_AC-5969 - [Problema do GitHub](https://github.com/magento/magento2/issues/35602) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### A função addFilterToMap da [Cloud] não está funcionando para determinadas colunas

Agora, o módulo personalizado pode ser usado na grade de pedidos. Ocorreram erros anteriores ao usar um módulo personalizado.

_ACP2E-2944 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

### Promoção

#### Atributo de cliente não visível ao criar conta a partir do convite

Os atributos do cliente estão disponíveis ao criar a conta a partir do convite.

_ACP2E-2602 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### O código do cupom com Limite de usos por cupom não está sendo liberado para pagamento falhou com o cancelamento do pedido

O sistema agora atualiza imediatamente os usos de cupom quando um pedido é criado ou cancelado, e adiciona os usos de regras a uma fila para evitar possíveis bloqueios. Isso garante que um código de cupom com um limite &quot;Usos por cupom&quot; seja liberado e possa ser reutilizado se um pedido for cancelado devido a uma falha no pagamento. Anteriormente, o sistema não liberava o código do cupom para reutilização nesses casos, resultando em uma mensagem de erro informando que o código do cupom não era válido.

_ACP2E-2627 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### O Indexador de Produto da Regra de Catálogo de Reindexação da [Cloud] lança SQLSTATE[HY000]: Erro geral: o servidor MySQL 2006 desapareceu.

O sistema agora lida corretamente com o valor &quot;batchCount&quot; personalizado no di.xml para o &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, evitando erros de SQL, como &quot;Erro geral: o servidor MySQL 2006 desapareceu&quot; durante a reindexação do Indexador de Produto de Regra de Catálogo devido ao tamanho de lote incorreto em catálogos grandes

_ACP2E-2811 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Regra de Vendas com o atributo Etapa de Qtd. de Desconto (Comprar X) faz com que outras regras não sejam aplicadas

A regra de preço do carrinho não cancela as regras aplicadas anteriormente se a quantidade do produto no carrinho não for suficiente para que a regra seja aplicada.

_ACP2E-3139 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### Emitir regras de vendas com desconto de valor fixo e &quot;Desconto de Qtd. Máxima Aplicado a&quot;

Correção de um problema com o desconto de regras do carrinho, quando o desconto de valor fixo é configurado para ser aplicado a uma quantidade limitada de produtos, é o carrinho. Anteriormente, o valor &quot;Desconto de Qtd. Máxima Aplicado a&quot; era usado para calcular o preço do item atual no carrinho, não apenas para calcular o desconto da regra.

_ACP2E-3332 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Regras do carrinho &quot;Desconto de valor fixo para carrinho inteiro&quot;  A ação aplica descontos incorretamente

Os códigos de cupom serão validados corretamente, independentemente de letras maiúsculas ou minúsculas, quando usados na criação do pedido da área de administração. Antes, o código do cupom não era validado se não correspondesse à letra exata de maiúsculas e minúsculas do código de regra do carrinho configurado.

_ACP2E-3349 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### No back-end, os valores padrão da loja para atributos do produto (em vez dos valores administrativos esperados)

Agora, no back-end, são usados valores de administrador em vez dos valores de loja padrão para atributos de produto.

_ACP2E-3374 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### A ação &quot;Desconto de valor fixo para carrinho inteiro&quot; das regras do carrinho aplica descontos incorretamente ao adicionar produtos do pacote

As regras de carrinho de quantidade fixa não eram aplicadas corretamente a produtos de pacote. Agora, ao calcular o valor total do desconto, os produtos secundários agrupados são considerados, resultando no cálculo de desconto adequado.

_ACP2E-3377 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Desconto Calculado Incorretamente de Regras de Preço do Carrinho

Descontos de valor fixo estão sendo calculados corretamente agora. Antes da correção, os descontos de valor fixo não eram totalizados corretamente para os produtos agrupados.

_ACP2E-3403 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0b488dd1)_

#### As categorias aninhadas nas condições da regra não mostram

Correção de um problema em que categorias aninhadas na categoria de nível 3 não eram exibidas nas regras de marketing para a condição de categoria

_ACP2E-3406 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### usage_limit e uses_per_customer não são atualizados na Tabela salesrule_coupon

A atualização de Usos por cupom e Usos por cliente na regra de preço do carrinho agora afetará os cupons gerados automaticamente. Anteriormente, os novos valores afetavam somente os novos cupons

_ACP2E-3432 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### A regra de preço do carrinho não considera a categoria principal quando está usando a condição &quot;igual ou maior que&quot;.

As Regras de preço do carrinho agora consideram a categoria principal corretamente quando usada em condições avançadas

_ACP2E-3456 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/93359343)_

#### Cálculo de desconto inválido com prioridade

No caso de valor fixo aplicado ao tipo de desconto de carrinho inteiro, o valor não estava sendo calculado corretamente para itens de carrinho que já foram descontados por uma promoção anterior. Agora, os descontos são devidamente resumidos.

_ACP2E-3463 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### [NUVEM] O cálculo de envio não está considerando a regra do carrinho de compras

Antes da correção, uma regra de carrinho com condição de região não era aplicada de maneira consistente. Após a correção, as regras do carrinho com condições de região são aplicadas corretamente.

_ACP2E-3472 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### A condição de SKU da regra de carrinho está falhando para a fatura.

O desconto no produto do pacote com preço dinâmico agora é refletido corretamente na fatura. Anteriormente, o desconto não era refletido na fatura.

_ACP2E-3491 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Valor de desconto incorreto quando várias regras de preço do carrinho são aplicadas simultaneamente com produtos com desconto/com preço especial

Antes da correção, o valor fixo para regras de carrinho inteiro não era aplicado corretamente se mais de um estava sendo aplicado. Agora, as regras do carrinho de desconto de valor fixo estão sendo aplicadas corretamente.

_ACP2E-3498 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### SEO

#### A adição de regravações de URL com ênfase causa carregamento infinito

O sistema agora cria com sucesso e funciona regravações de URL com acentos, impedindo o carregamento infinito durante o processo de salvamento. Anteriormente, adicionar uma regravação de URL com ênfase causava um problema de carregamento infinito.

_AC-11907 - [Problema do GitHub](https://github.com/magento/magento2/issues/38692) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### Reescrita de URL de categoria incorreta de vários armazenamentos para categoria de terceiro nível

Gerar substituições de URL corretas para filhos com pai com chave de URL com escopo personalizado

_ACP2E-2641 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Caracteres de dois bytes (caracteres especiais) no campo Nome do produto bloqueiam a criação do produto no back-end

Foi adicionada uma nova configuração que permite aplicar transliteração ou não ao URL do produto. A configuração está disponível aqui: Lojas > Configuração > Catálogo > Catálogo > Otimização do mecanismo de pesquisa: &quot;Aplicar transliteração para URL do produto&quot;

_ACP2E-2770 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Criação incorreta de entradas url_rewrite com vários armazenamentos em um grupo de armazenamento

Antes da correção, você só podia gerar regravações de URL em um nível de site ao editar um produto. Com a correção, uma nova configuração foi introduzida (Lojas > Configuração > Catálogo > Catálogo > Otimização do mecanismo de pesquisa, &quot;Escopo de regravação de URL do produto&quot; com opções &quot;Exibição da loja&quot;, &quot;Site&quot;) que permite gerar regravações de URL na exibição da loja ou no nível do site.

_ACP2E-3383 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2d627301)_

### Pesquisar

#### Obter &quot;Insira um termo de pesquisa e tente novamente&quot;. erro na página de pesquisa avançada na loja na versão 2.4.8-beta1

O sistema agora exibe corretamente os resultados da pesquisa na página Pesquisa avançada quando um atributo de produto é definido como &quot;Não&quot;. Anteriormente, definir um atributo de produto como &quot;Não&quot; e executar uma pesquisa resultava em uma mensagem de erro, &quot;Insira um termo de pesquisa e tente novamente&quot;.

_AC-13053 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### magento/module-open-search depende de uma ramificação opensearch-php inexistente

_AC-13721 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/05dc0bbf)_

#### tabela search_query quando de grande tamanho, tem grande impacto no front-end do tempo de carregamento

Tempo de carregamento de página da listagem de pesquisa aprimorado. Antes da correção, a página de listagem de pesquisa estava sendo adiada devido a uma consulta não otimizada.

_ACP2E-3362 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Segurança

#### [Problema] Fonte Ausente CSP Paylater Popup

O sistema agora permite o carregamento da fonte &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sem violar a diretiva de Política de segurança de conteúdo, garantindo a exibição correta do pop-up Paylater. Anteriormente, o carregamento da fonte era recusado devido a uma violação da diretiva da Política de segurança de conteúdo, causando problemas de exibição com o pop-up Paylater.

_AC-11855 - [Problema do GitHub](https://github.com/magento/magento2/issues/38624) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37401)_

#### [Problema]. Atualize o texto DOM js.js reinterpretado como HTML

Ao usar innerText, ele evitará o risco de injeção de HTML, já que essas propriedades escapam automaticamente de qualquer caractere especial do HTML no texto fornecido. Essa correção ajuda a evitar vulnerabilidades de criação de script entre sites (XSS), tratando a entrada como texto sem formatação em vez de HTML interpretado.

_AC-12035 - [Problema do GitHub](https://github.com/magento/magento2/issues/38767)_

#### O ReCaptcha V2 é exibido incorretamente no check-out para o idioma alemão

Anteriormente, o recaptcha de em endereço de email do checkout aparece sem estilo para idiomas com palavras longas, como alemão. Depois disso, o recaptcha tem a mesma aparência que todos os elementos recaptcha do resto das áreas.

_ACP2E-3273 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### O captcha no logon do administrador não requer interação para alguns usuários

O ReCaptcha para logon de administrador é validado conforme esperado

_ACP2E-3300 - [Contribuição de código do GitHub](https://github.com/magento/security-package/commit/8f64ab3c)_

### Envio

#### [Problema] Corrigido o erro de digitação em tracking.phtml - renomeado JS-functions &quot;currier&quot; para &quot;carrier&quot;

O sistema agora usa corretamente o termo &quot;operadora&quot; em vez do termo &quot;currier&quot; escrito incorretamente nas funções do manipulador do JavaScript usadas no modelo de rastreamento de pedido, garantindo a nomenclatura de função adequada e a clareza do código. Anteriormente, o termo incorreto &quot;currier&quot; era usado, levando a uma potencial confusão e inconsistência na base de código.

_AC-10757 - [Problema do GitHub](https://github.com/magento/magento2/issues/34523) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33414)_

#### UPS REST &quot;Uma remessa não pode ter um KGS/IN ou LBS/CM ou OZS/CM como sua unidade de medida&quot;

Certifique-se de que as taxas de no-break estejam visíveis no check-out e no carrinho.

_AC-11938 - [Problema do GitHub](https://github.com/magento/magento2/issues/38618) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/493e01f5)_

#### [Problema] Ortografia correta das variáveis para o endereço do cliente

O sistema agora soletra corretamente as variáveis para endereços de clientes, garantindo uma exibição precisa na área de conta do front-end. Anteriormente, a ortografia incorreta dessas variáveis podia causar erros durante as revisões de código locais.

_AC-13172 - [Problema do GitHub](https://github.com/magento/magento2/issues/32817) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32815)_

#### A janela de rastreamento mostra a data de entrega esperada incorreta

Exiba a data de entrega correta para a operadora Fedex.

_ACP2E-2738 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### As Taxas Da Tabela Ainda Estão Sendo Exibidas, Mesmo Que O Frete Gratuito Seja Aplicado

Tabela Taxa método de envio agora é mostrado mesmo se Frete grátis se torna disponível após a aplicação do cupom

_ACP2E-2763 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Falha de MFTF test AdminCreatingShippingLabelTest devido a credenciais não adicionadas no ambiente Jenkins

correção de teste mftf

_ACP2E-2765 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### A API de rastreamento do FedEx não está funcionando com credenciais REST

Anteriormente, a integração FedEx não exigia chaves de API adicionais para a API de rastreamento. Agora, uma nova configuração foi adicionada para oferecer suporte a chaves de API de rastreamento.

_ACP2E-3340 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### Taxas negociadas por FedEx [Cloud] não retornadas em REST

Antes da correção, as taxas específicas da conta FedEx não eram enviadas na resposta, mesmo que, de acordo com a documentação do FedEx, elas devessem ter sido enviadas. Após a correção, as taxas específicas da conta são enviadas na resposta do alterando a solicitação do nosso lado.

_ACP2E-3354 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Preparo e visualização

#### Não é Possível Atualizar a Atualização Agendada ao Usar o Atributo Exclusivo de Categoria Personalizada

Correção de um problema em que a atualização programada de uma categoria não era possível se a categoria tivesse um atributo exclusivo

_ACP2E-3453 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Direcionamento

#### [Problema] Permitir o uso de intervalos CIDR na lista de permissões de manutenção

O sistema agora oferece suporte ao uso de intervalos CIDR no modo de manutenção permitir lista de IP, permitindo que um intervalo de endereços IP ignore o modo de manutenção. Anteriormente, o modo de manutenção permitia que somente endereços IP individuais fossem ignorados pelo modo de manutenção.

_AC-9432 - [Problema do GitHub](https://github.com/magento/magento2/issues/37943) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/30699)_

### Imposto

#### [Problema] Promoção de propriedade do construtor Feature/php8.1 wee graph ql

Substitua quase todas as propriedades com a promoção de propriedade do construtor no módulo wee graph ql:

_AC-13295 - [Problema do GitHub](https://github.com/magento/magento2/issues/39309) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36975)_

#### O Imposto Fixo do Produto (FPT) não está funcionando com produtos configuráveis

FPT para variações de produtos configuráveis funcionando corretamente.

_ACP2E-3193 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Estrutura de teste

#### Falha no teste de integração testDbSchemaUpToDate devido ao tipo de coluna JSON

O sistema agora reconhece corretamente os tipos de coluna JSON no esquema do banco de dados durante testes de integração, evitando falhas de teste devido a uma incompatibilidade entre o esquema do banco de dados e o esquema declarativo. Anteriormente, o sistema identificava incorretamente os tipos de coluna JSON como LONGTEXT no MariaDB, causando falha nos testes de integração.

_AC-11654 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ef81f5a2)_

#### [Problema] correção ortográfica do PHPDoc

O sistema agora reconhece corretamente os métodos obsoletos nos IDEs devido a uma correção ortográfica no PHPDoc. Anteriormente, um erro de ortografia no PHPDoc fazia com que os IDEs não reconhecessem determinados métodos como obsoletos.

_AC-13362 - [Problema do GitHub](https://github.com/magento/magento2/issues/31399) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/31398)_

#### MAGETWO-95118: Verificando o comportamento com o carrinho de compras persistente após a sessão expirar

_AC-13478 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### Corrigir testes estáticos para permitir o uso por extensões de terceiros

_AC-13848 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9e383b4d)_

#### A falha de aplicação do Fixture [Interna] não é mostrada durante a execução ou nos logs

&quot;-

_ACP2E-3334 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest

Mftfs fixos

_ACP2E-3458 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Estrutura da interface

#### Correção de vulnerabilidade de segurança do Prototype.js CVE-2020-27511

O sistema foi atualizado para lidar com a vulnerabilidade de segurança CVE-2020-27511 no Prototype.js 1.7.3, melhorando a segurança geral do sistema. Antes dessa atualização, o sistema era susceptível a uma Negação de serviço de expressão regular (ReDOS) por meio da remoção de tags HTML criadas.

_AC-12128 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### O Grunt Less usa o prefixo pub/ para mapas- fonte

O sistema agora gera menos mapas de origem/css sem o prefixo /pub para caminhos ao usar o grunt, eliminando a necessidade de uma solução alternativa na configuração do servidor Web. Anteriormente, o uso do prefixo /pub em caminhos de mapas de origem exigia uma configuração específica no servidor Web para funcionar corretamente.

_AC-12189 - [Problema do GitHub](https://github.com/magento/magento2/issues/38837) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38840)_

#### Campo De Arquivo Do Componente Da Interface Do Usuário

Agora o sistema valida corretamente o campo de arquivo em um formulário de componente da interface do usuário, permitindo que o formulário seja enviado sem erros quando um arquivo for selecionado. Anteriormente, a validação falhava mesmo quando um arquivo era selecionado, impedindo o envio do formulário.

_AC-12432 - [Problema do GitHub](https://github.com/magento/magento2/issues/38908) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39004)_

#### [Problema] Formato de data aprimorado no console js: alternar de 12 horas para 24 horas para...

Formato de data aprimorado no console js: alternar de 12 horas para 24 horas

_AC-12645 - [Problema do GitHub](https://github.com/magento/magento2/issues/38983) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38972)_

#### [Problema] ao adicionar geração de sourceMap para menos arquivos no modo de desenvolvedor

O sistema agora gera mapas de origem para menos arquivos quando no modo de desenvolvedor, facilitando a identificação da origem de um estilo. Anteriormente, identificar a origem de um estilo era um desafio ao executar o sistema no modo de desenvolvedor com menos compilação no lado do servidor.

_AC-12650 - [Problema do GitHub](https://github.com/magento/magento2/issues/38982) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38977)_

#### O conteúdo estático está sendo implantado para módulos desabilitados

O sistema agora exclui CSS relacionado a módulos desativados dos arquivos finais de saída CSS, garantindo que os estilos desnecessários não sejam carregados. Anteriormente, o CSS relacionado a módulos desativados era incluído nos arquivos finais de saída do CSS, levando ao carregamento de estilos extras e desnecessários.

_AC-1306 - [Problema do GitHub](https://github.com/magento/magento2/issues/24666) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32922)_

#### Comportamento inconsistente na classificação &quot;Sem estoque&quot; com limite mínimo de estoque

O sistema agora classifica corretamente os produtos no catálogo com base nos níveis de estoque, seguindo o Limite mínimo de estoque definido e movendo os itens esgotados para o final da lista de forma consistente. Anteriormente, o comportamento de classificação era inconsistente, com itens nem sempre aparecendo na ordem correta com base em seus níveis de estoque, e as alterações na classificação podiam ocorrer de forma imprevisível após salvar, atualizar ou modificar a hierarquia de categorias.

_AC-13459 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### Sugestão para o relatório de erros aprimorado para problemas de carregamento do require.js

Essa PR melhora a mensagem de erro quando o require js falha ao carregar um componente.

_AC-13472 - [Problema do GitHub](https://github.com/magento/magento2/issues/36761) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38971)_

#### Erros de descontinuação do PHP 8.4 que causam falhas de build no 2.4-develop

_AC-14004 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### [Problema] Não carregar contexto de bloco de back-end no front-end

O sistema agora garante que o contexto de bloco de back-end não seja carregado no front-end, evitando a criação de sessões de back-end desnecessárias e possíveis bloqueios de sessão. Anteriormente, o sistema carregava incorretamente o contexto do bloco de back-end no front-end, levando à criação de sessões de back-end e possíveis bloqueios de sessão.

_AC-9007 - [Problema do GitHub](https://github.com/magento/magento2/issues/37617) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36368)_

#### [Problema] Remover scripts desnecessários resumo de revisão

O sistema agora otimiza o tempo de carregamento da página removendo scripts JavaScript desnecessários da seção de classificação, em vez de usar estilos CSS em linha para obter um código mais eficiente e legível. Anteriormente, o uso de scripts JavaScript para a seção de classificação podia retardar o tempo de carregamento da página.

_AC-9168 - [Problema do GitHub](https://github.com/magento/magento2/issues/37776) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/34643)_

#### Exceção ao verificar um saldo de cartão-presente quando Recaptcha está habilitado

Os usuários poderão buscar o saldo do vale-presente na tela de exibição e edição do carrinho. Anteriormente, esses detalhes não eram exibidos quando o reCAPTCHA estava ativado.

_ACP2E-2529 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_

#### [ESCLARECIMENTO] Solicitação de recursos Conformidade com o ADA

O sistema agora garante a conformidade com o ADA, removendo propriedades CSS não compatíveis e substituindo-as por outras compatíveis no arquivo print.css. Anteriormente, o uso de propriedades CSS não compatíveis resultava em problemas de compatibilidade do navegador.

_ACP2E-2729 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### [Nuvem] Código de biblioteca de confusão em effect-drop.js de AC 2.4.4-p8

O sistema agora implementa corretamente a biblioteca effect-drop.js, garantindo o funcionamento adequado dos efeitos da interface do usuário do jQuery. Anteriormente, a biblioteca effect-drop.js era substituída por engano pela biblioteca effect-clip.js, causando possíveis problemas com os efeitos da interface do jQuery.

_ACP2E-3061 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Cabeçalho do site | Caracteres especiais quebrando a seção de boas-vindas do cliente

Após a correção, os caracteres especiais são mostrados corretamente na seção de boas-vindas do cliente.

_ACP2E-3367 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### A edição do segmento do cliente falha com o intervalo de datas

É possível salvar o segmento do cliente com a condição de intervalo de datas, quando apenas uma das datas foi editada.

_ACP2E-3561 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a52ff98f)_
