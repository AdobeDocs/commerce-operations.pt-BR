---
source-git-commit: 2d46933005b9848fee526d0a9f96e2e5ff58cbb8
workflow-type: tm+mt
source-wordcount: '14732'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.8-beta1)

## Destaques

Os 49 destaques a seguir se aplicam à versão 2.4.8 do Magento Open Source.

### Estrutura

* _AC-10721_: atualizar as dependências do league/flysystem Composer para a versão mais recente
   * _Observação de correção_: atualize as dependências do 2.x league/flysystem Composer para a versão mais recente 3.x
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11495_: atualização dos componentes da plataforma 2.4.8-beta1
* _AC-11673_: investigue as versões mais recentes do php-amqplib/php-amqplib
   * _Observação de correção_: atualização da versão mais recente php-amqplib/php-amqplib :^3.x
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11723_: Refatoração da estrutura de Teste de Integração para compatibilidade com phpunit 10 - IntegrationTest.php não encontrado
   * _Observação de correção_: o PHPUnit 9 foi atualizado para o PHPUnit 10 com alterações de estrutura Integration and WebAPI Test do Adobe Commerce. As alterações do PHPUnit 10 são compatíveis com versões anteriores.
   * _Contribuição de código do GitHub_: &lt;https://github.com/magento/magento2/ (Interno, Não Mesclado)>
* _AC-11813_: Estrutura de teste WebApi para compatibilidade com phpunit 10 - Problema relacionado à conectividade do RabbitMQ com módulos SOAP e B2B
   * _Observação de correção_: o PHPUnit 9 foi atualizado para o PHPUnit 10 com alterações de estrutura Integration and WebAPI Test do Adobe Commerce. As alterações do PHPUnit 10 são compatíveis com versões anteriores.
   * _Contribuição de código do GitHub_: &lt;https://github.com/magento/magento2/ (Interno, Não Mesclado)>
* _AC-11816_: adicionar compatibilidade com MySQL 8.4 LTS
* _AC-11911_: limpeza de css jQuery/fileuploader após a migração para a biblioteca uppy
   * _Observação de correção_: biblioteca jQuery/fileUploader removida porque foi migrada para a biblioteca Uppy
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: adicionar compatibilidade com MySQL 8.4 LTS para Magento CE
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12014_: marcar o módulo elasticsearch 8 como obsoleto
* _AC-12015_: limpeza da pasta ExtJs após a migração para a biblioteca jsTree
   * _Observação de correção_: a pasta extJs foi removida, pois a funcionalidade relacionada foi migrada para jsTree
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_: atualizar dependência de sistema de monólogo/monólogo para a versão principal mais recente
   * _Observação de correção_: o sistema foi atualizado para usar a versão principal mais recente da biblioteca &quot;monolog/monolog:^3.x&quot;, garantindo compatibilidade e desempenho aprimorado. Anteriormente, o sistema usava uma versão desatualizada da biblioteca &quot;monolog/monolog&quot;, que poderia ter levado a possíveis problemas e limitações.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_: atualizar dependência wikimedia/less.php para a versão principal mais recente
   * _Observação de correção_: o sistema foi atualizado para usar a versão principal mais recente 5.x da biblioteca &quot;wikimedia/less.php&quot;, garantindo a compatibilidade e a funcionalidade atualizada. Anteriormente, o sistema usava uma versão desatualizada da biblioteca que poderia ter causado problemas de segurança.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_: atualizar dependência de biblioteca jquery/validate para a versão secundária mais recente
   * _Observação de correção_: atualize a dependência da biblioteca jquery/validate para a versão secundária mais recente 1.20.0
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_: atualizar dependência do sistema Moment.js para a versão secundária mais recente
   * _Observação de correção_: atualize a dependência do sistema Moment.js para a versão secundária mais recente 2.30.1
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_: adicionar compatibilidade com MySQL 8.4 LTS for EE
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_: adicionar compatibilidade com MySQL 8.4 LTS para B2B
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_: adicionar compatibilidade com MySQL 8.4 LTS para extensões de pacote
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_: adicionar compatibilidade com MariaDB 11.4 LTS para CE
   * _Observação de correção_: adição do suporte ao MariaDB 11.4 com Adobe Commerce e extensões
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_: Otimização de Assinantes - PhpUnit10
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: suporte a novas tentativas de conexão para a sessão Redis e compatível com colinmollenhour/php-redis-session-abstract v2.0.0
   * _Observação de correção_: a versão mais recente atualizada de colinmollenhour/php-redis-session-abstract v2.0.0 é compatível com o adobe commerce
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12268_: atualizar as dependências do league/flysystem Composer para a versão mais recente
   * _Observação de correção_: atualize as dependências do 2.x league/flysystem Composer para a versão mais recente 3.x
* _AC-12576_: Investigue as falhas de testes de automação com o MySQL 8.4 LTS
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: adicionar compatibilidade com MariaDB 11.4 LTS For EE
   * _Observação de correção_: adição do suporte ao MariaDB 11.4 com Adobe Commerce e extensões
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12693_: Investigar a Ferramenta de Migração de Dados (DMT) com o MySQL 8.4 LTS
* _AC-12715_: atualizar dependências do laminas composer para a versão mais recente
   * _Observação de correção_: o sistema agora oferece suporte às versões mais recentes das dependências do laminas composer:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
lâminas/lâminas-validador
garantir a compatibilidade e a funcionalidade atualizada. Anteriormente, a atualização para as versões mais recentes dessas dependências podia causar problemas de incompatibilidade com versões anteriores e falhas de teste.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12752_: adicionar compatibilidade com MariaDB 11.4 LTS para a ferramenta Migração de Dados
   * _Observação de correção_: adição do suporte ao MariaDB 11.4 com Adobe Commerce e extensões
* _AC-12823_: Investigue a falha de teste de unidade devido à atualização de patch phpunit durante a atualização do componente
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12897_: compatibilidade das ferramentas SVC e EAT com o MySQL 8.4
* _AC-12898_: compatibilidade da ferramenta UCT com o MySQL 8.4
   * _Observação de correção_: a UCT (Ferramenta de Compatibilidade de Atualização) agora é compatível com o MySQL 8.4, garantindo uma operação perfeita e verificações de compatibilidade para instâncias em execução nesta versão. Anteriormente, a ferramenta UCT não era testada e verificada quanto à compatibilidade com o MySQL 8.4.
* _AC-9749_: atualização do PHPUnit 10
   * _Observação de correção_: as dependências do phpunit/phpunit composer foram atualizadas para uma versão compatível - &quot;phpunit/phpunit&quot;:&quot;10.x&quot;

### Instalar e administrar

* _AC-6819_: definir indexadores como &quot;Atualizar por Agendamento&quot; por padrão

### Pedido

* _ACP2E-2709_: [Solicitação de Recursos] O cliente sugere que o Botão Enviar Comentário na página Detalhes do Pedido é confuso e deve ser alterado para outra coisa
   * _Observação de correção_: para minimizar a confusão, o rótulo do botão &quot;Enviar comentário&quot; foi alterado para &quot;Atualizar&quot; na página de detalhes do pedido.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/488c1034>

### Outro

* _AC-11420_: Defina indexadores como padrão no status Pronto quando uma nova versão do Adobe Commerce for instalada
   * _Observação de correção_: após o Magento de instalação, o Status do Indexador deve estar no estado *Pronto* por padrão.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: em instalação de Magento existente ao instalar indexadores de conjunto de módulos indexadores de terceiros em atualização por padrão.
   * _Observação de correção_: todos os novos indexadores estão por padrão no modo [Atualizar por Agendamento]. Anteriormente, o modo padrão era [Atualizar ao salvar]. O mesmo acontece com os indexadores personalizados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: as opções Elasticsearch 7 e 8 devem vir com Deprecated na configuração do administrador.
   * _Observação de correção_: a opção Elasticsearch 8 da Configuração do administrador será exibida com o texto Obsoleto, para informar aos usuários que o Elasticsearch 8 não é mais uma opção recomendada para uso.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: adicionar nota de texto quando a opção Elasticsearch estiver selecionada na Configuração de Administração
   * _Observação de correção_: uma nota de texto é adicionada para informar aos usuários administradores do Adobe Commerce que o elasticsearch não é mais suportado pelo Adobe e está obsoleto.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12870_: compatibilidade das ferramentas SVC e EAT com MariaDB 11.4
   * _Observação de correção_: compatibilidade das ferramentas SVC e EAT com MariaDB 11.4
* _AC-12876_: Compatibilidade da ferramenta UCT com MariaDB 11.4
* _LYNX-374_: Confirmação de Email de Documento via GraphQL
* _LYNX-376_: documento obtendo configurações para reCAPTCHA no GraphQL
* _LYNX-409_: Otimizações de Consulta de Banco de Dados para Mutação de Itens do Carrinho de Atualização

### Segurança

* _AC-11041_: Melhorias de segurança para 2.4.8-beta1 da versão de junho de 2024
* _AC-11864_: Melhorias de segurança para 2.4.8-beta1 da versão de agosto de 2024
* _AC-12346_: Melhorias de segurança para 2.4.8-beta1 da versão de outubro de 2024
* _AC-12691_: [2.4.8-beta1] O ponto de extremidade da API REST de atualização do cliente não está funcionando
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4102373>, <https://github.com/magento/magento2/commit/a4102373>

### Estrutura da interface

* _AC-12726_: [2.4.8-beta1] Migração do TinyMCE 5 para o TinyMCE 7
   * _Observação de correção_: o TinyMCE 5 foi migrado para o TinyMCE 7.3.0 para ser uma versão com suporte para o Adobe Commerce; anteriormente, o sistema estava usando o 5.10.2, que estava desatualizado e relatava vulnerabilidade de segurança
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [2.4.8-beta1] Migração do TinyMCE 5 para o TinyMCE 7 Page Builder
   * _Observação de correção_: o TinyMCE 5 foi migrado para o TinyMCE 7.3.0 para ser uma versão com suporte para o Adobe Commerce; anteriormente, o sistema estava usando o 5.10.2, que estava desatualizado e relatava vulnerabilidade de segurança
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [2.4.8-beta1] Migração do TinyMCE 5 para o TinyMCE 7 - Magento2-infra - palavras banidas
   * _Observação de correção_: o TinyMCE 5 foi migrado para o TinyMCE 7.3.0 para ser uma versão com suporte para o Adobe Commerce; anteriormente, o sistema estava usando o 5.10.2, que estava desatualizado e relatava vulnerabilidade de segurança
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Atualização do Require.js para a versão mais recente 2.3.7 (vulnerabilidade de segurança CVE-2024-38999)
   * _Observação de correção_: o arquivo require.js foi atualizado para a versão mais recente 2.3.7. Na versão anterior, relatou vulnerabilidade de segurança
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>

## Problemas corrigidos

Corrigimos 253 problemas no código principal Magento Open Source 2.4.8. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

* _AC-10042_: /V1/transactions REST API retorna erro quando parent_txn_id = txn_id
   * _Observação de correção_: o sistema agora manipula corretamente as transações de conceito pai e filho, em que a ID da transação pai é a mesma que a ID da transação, impedindo um loop infinito ao consultar o ponto de extremidade da API REST /V1/transactions. Anteriormente, esse cenário resultava em um erro fatal devido ao tempo máximo de execução ser excedido.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] Digite o problema na versão 2.4.7
   * _Observação de correção_: o sistema agora manipula corretamente valores inteiros na função GetCustomSelectedOptionAttributes ao executar uma consulta GraphQL, evitando erros relacionados ao tipo. Anteriormente, iniciar uma consulta GraphQL que usava GetCustomSelectedOptionAttributes com um argumento inteiro resultava em um erro de tipo.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38662>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38663>
* _ACP2E-2927_: [REST API]: o valor Padrão de Uso no modo de exibição de armazenamento não permanece verificado após a adição de configurações para um produto configurável
   * _Observação de correção_: o problema foi corrigido ao garantir entradas corretas no banco de dados para as opções personalizáveis para um repositório não padrão. A caixa de seleção do armazenamento personalizado na seção &quot;admin > Catálogo > Edição de produto > Opções personalizáveis&quot; foi desmarcada anteriormente devido a entradas imprecisas do banco de dados, mesmo que o título da opção do armazenamento personalizado permanecesse o mesmo que o armazenamento padrão.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: REST API não pode fazer solicitações com barra (/) no SKU ao usar Oauth1
   * _Observação de correção_: antes da correção, você não podia fazer uma chamada de API bem-sucedida para um produto que tinha &quot;/&quot; em sua SKU. Agora, você pode emitir uma solicitação de obtenção de API bem-sucedida para detalhes do produto, mesmo que o SKU tenha uma barra.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: falha na atualização do endereço do cliente ao atualizar por meio da API REST se &quot;validateDefaultAddress&quot; estiver habilitado
   * _Observação de correção_: o ponto de extremidade da API agora está funcionando como pretendido depois que o problema com a chave de ID ausente na carga da API foi resolvido.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Nuvem] Criação do grupo de preços de site Duplicado na API de Preços de Camada.
   * _Observação de correção_: agora a API Restrição de Preço de Camada não permite criar o grupo de clientes de preço de grupo de sites duplicado.
Anteriormente, era possível criar o grupo de clientes Duplicar preço do grupo de sites na API Preços de camada que não passaria na validação no Administrador durante o salvamento do produto.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: não é possível adicionar comentário de pedido com status via API REST
   * _Observação de correção_: o problema foi resolvido permitindo a alteração no status do pedido se for somente do estado atual. Anteriormente, não respeitava o estado do pedido e impedia alterações em qualquer status do pedido, mesmo que fosse do mesmo estado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>

### Conta

* _AC-10782_: formulário de endereço do cliente permite código aleatório nos campos de nome
   * _Observação de correção_: o sistema agora valida a entrada nos campos Nome e Sobrenome no formulário de endereço do cliente, impedindo o uso de código aleatório. Anteriormente, o sistema permitia o uso de código aleatório nesses campos sem gerar um erro.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38331>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38345>
* _AC-10990_: falha no endereço de adição da minha conta ao salvar
   * _Observação de correção_: o sistema agora salva corretamente os endereços dos clientes, mesmo quando o campo de região não é exibido, evitando uma falha durante o processo de salvamento. Anteriormente, tentar adicionar ou editar um endereço sem um campo de região exibido resultava em um erro de exceção.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38406>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38407>
* _AC-11919_: Admin: os botões de ações da página flutuam à esquerda em vez da direita
   * _Observação de correção_: o sistema agora alinha corretamente os Botões de ações da página à direita do cabeçalho fixo no painel de administração, melhorando a aparência profissional. Anteriormente, esses botões flutuavam incorretamente no lado esquerdo do cabeçalho fixo.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38701>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: erro dev:di:info no magento 2.4.7
   * _Observação de correção_: o sistema agora exibe corretamente os parâmetros do construtor ao executar o comando dev:di:info, impedindo a ocorrência de erros. Anteriormente, a execução desse comando resultava em um erro devido a uma incompatibilidade de tipos no argumento.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38740>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_: o cliente está conectado, mas mostra o erro 404 no front-end.
   * _Observação de correção_: a página do painel do cliente da vitrine agora é carregada como esperado quando um cliente faz logon. Anteriormente, os clientes podiam fazer logon, mas essa página mostrava um erro 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/35838>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: não é possível Salvar as informações do atributo do Cliente na seção Admin Edit customer;
   * _Observação de correção_: a ID de armazenamento do cliente agora é implementada corretamente por escopo de site para o formulário de edição do cliente administrador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/488c1034>

### Interface do administrador

* _AC-11588_: a validação de dados foi bem-sucedida e o botão Importar está presente durante a importação de produtos com comportamento Substituir
   * _Observação de correção_: o sistema agora valida os dados corretamente e oculta o botão &quot;Importar&quot; durante o processo de importação do produto com o comportamento &quot;Substituir&quot;, impedindo qualquer substituição de dados não intencional. Anteriormente, o sistema validava os dados incorretamente e exibia o botão &quot;Importar&quot;, resultando em possíveis inconsistências de dados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Bug] o Magento 2.4.7 não permite fotos de produto com extensão de arquivo de letra maiúscula.
   * _Observação de correção_: o sistema agora aceita uploads de imagens de produtos com extensões de arquivo de carta em maiúsculas, garantindo um processo suave de criação de produtos. Anteriormente, os uploads de imagem com extensões de arquivo em letras maiúsculas eram recusados, forçando os usuários a alterar a extensão do arquivo para minúsculas.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38831>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-6975_: [Problema] Defina o modo de indexador padrão como &#39;agendamento&#39;
   * _Observação de correção_: todos os novos indexadores estão no modo **[!UICONTROL Update by Schedule]** por padrão.  Anteriormente, o modo padrão era **[!UICONTROL Update on Save]**. Os indexadores existentes não são afetados. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36419>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Problema] Descartar tabelas de log de alterações do indexador no cancelamento de inscrição do mview
   * _Observação de correção_: o sistema agora remove automaticamente tabelas de log de alterações não usadas quando um índice é alternado de &#39;atualização na programação&#39; para &#39;atualização ao salvar&#39;, marcando o índice como inválido para garantir que nenhuma entrada seja perdida. Anteriormente, alternar um índice para &quot;atualizar ao salvar&quot; deixaria as tabelas de log de alterações não usadas no sistema e marcaria todos os índices alterados como &quot;válidos&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/29789>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/25859>
* _AC-9843_: i18n:collect-expressions interrompe a integridade das traduções
   * _Observação de correção_: o comando `bin/magento i18n:collect-phrases -o` agora coleta e adiciona corretamente novas frases de arquivos JavaScript e .phtml, garantindo que as traduções sejam refletidas com precisão no arquivo de tradução. Anteriormente, o sistema não conseguia incluir frases de tradução de várias linhas de arquivos JavaScript e frases de arquivos .phtml no arquivo de tradução, resultando em traduções incompletas ou incorretas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: apóstrofo no nome de exibição de repositório é substituído por &#39;
   * _Observação de correção_: os filtros de exibição de armazenamento da grade agora exibem apóstrofos corretamente
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38395>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: falha no carregamento de Favicon ao validar arquivos .ico
   * _Observação de correção_: o erro de validação de arquivo foi atualizado para &quot;Falha na validação do arquivo. Verifique as configurações de processamento da imagem na configuração da loja.&quot; Anteriormente, era simplesmente &quot;Falha na validação do arquivo&quot;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: a Galeria no PageBuilder está mostrando a miniatura de imagem antiga em vez da imagem recém-carregada
   * _Observação de correção_: gere novamente as visualizações de imagens para imagens excluídas e recarregadas com o mesmo nome através da galeria de mídia no conteúdo do construtor de páginas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_: Salvar produto por usuário administrador com escopo de função diferente substitui/exclui informações de produto relacionadas existentes no produto
   * _Observação de correção_: anteriormente, antes da correção, os produtos relacionados eram redefinidos e ficavam vazios quando o usuário administrador secundário clicava no botão Salvar sem alterar no produto relacionado. Após essa correção, o usuário administrador secundário clica no botão Salvar e o produto não é redefinido e é salvo com sucesso.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: não é possível exportar mais de 200 pedidos
   * _Observação de correção_: os limites de servidor para o tamanho da solicitação de IDs selecionadas enviadas anteriormente foram negligenciados ao alterar a solicitação HTTP de GET para POST para corrigir o problema. Anteriormente, devido às limitações do servidor para o tamanho da solicitação do GET, o problema era encontrado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Mensagem de Validação da página de check-out incorreta.
   * _Observação de correção_: se algum campo obrigatório estiver vazio, como &quot;endereço&quot;, a validação no lado do servidor não exibirá a mensagem. A validação do lado do cliente garantirá que a notificação de erro do campo obrigatório seja exibida, informando &quot;Este campo é obrigatório&quot;. Anteriormente, a mensagem &quot;o endereço é obrigatório&quot; era exibida se qualquer campo obrigatório ficasse vazio, além da mensagem de validação do lado do cliente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Problema de modelo de redefinição de senha com o usuário Administrador
   * _Observação de correção_: o problema foi resolvido com o uso da chave correta, que agora inclui o nome de usuário administrador no modelo de email e conclui o assunto corretamente. Anteriormente, o problema vinha de uma chave desatualizada que estava sendo usada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: barras duplas na URL do segmento do cliente
   * _Observação de correção_: barras duplas não aparecem na URL quando o botão &#39;Redefinir filtro&#39; é clicado na grade.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: COD não está disponível para países específicos permitidos
   * _Observação de correção_: agora o Cash on delivery está disponível para países específicos permitidos sempre que necessário e   O AC-3216 está funcionando como esperado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: não é possível atualizar o status de Pedido criado pelo Cliente
   * _Nota de correção_: &#39;
Agora podemos atualizar status de pedidos personalizados, enquanto anteriormente, o status só podia ser alterado se o status atual fosse &quot;processando&quot; ou &quot;fraude&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38659>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/8459b17d>

### Interface do administrador, desempenho

* _ACP2E-3169_: após a atualização para 2.4.5-p8, ocorrem erros 500 ao criar ordem do administrador
   * _Observação de correção_: anteriormente, ao habilitar a minificação de HTML, não era possível fazer um pedido pelo administrador. Agora, com a minificação de HTML ativada, o pedido do administrador pode ser feito com sucesso.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Interface do administrador, Envio

* _ACP2E-2519_: a contagem de código do cupom não é atualizada no   A coluna &quot;Tempo usado&quot; na guia Gerenciar códigos de cupom se um pedido for feito com envio múltiplo.
   * _Observação de correção_: anteriormente, quando um pedido era feito com remessa múltipla, a contagem de código do cupom não era atualizada na coluna &quot;Tempo Usado&quot; da guia Gerenciar Códigos de Cupom. Agora, a contagem correta é exibida no &quot;Tempo usado&quot; refletindo os valores desejados com o envio múltiplo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/4745100c>

### Analytics/Relatórios

* _ACP2E-2570_: o Relatório Avançado não está funcionando
   * _Observação de correção_: o sistema agora oferece suporte à geração de arquivos de dados de Relatórios avançados para conjuntos de dados extragrandes ao carregar e gravar relatórios em lotes de 10.000. Anteriormente, o módulo Relatórios avançados não conseguia gerar arquivos de dados para conjuntos de dados extragrandes, causando erros &quot;O servidor MySQL desapareceu&quot; durante a execução do trabalho analytics_collect_data cron.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: problema de visibilidade do intervalo de datas do relatório de Produtos Solicitados pelo Administrador.
   * _Observação de correção_: o usuário poderá selecionar qualquer data no relatório de produtos solicitados. Anteriormente, após a atualização de uma tabela, selecionar a data &#39;DE&#39; redefinirá a data &#39;ATÉ&#39;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Cabeçalhos de curl incorretos que fazem com que newrelic:create:deploy-marker não funcione
   * _Observação de correção_: o sistema agora formata corretamente os cabeçalhos curl, permitindo que o comando newrelic:create:deploy-marker crie com êxito um marcador de implantação no New Relic. Anteriormente, cabeçalhos curl incorretos impediam a criação de um marcador de implantação no New Relic.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37641>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Analytics/Relatórios, B2B

* _ACP2E-2300_: B2B - o mapa de site inclui produtos/categorias não atribuídos ao Catálogo Compartilhado
   * _Observação de correção_: restringir as categorias e os produtos gerados pelo mapa de site às categorias e aos produtos atribuídos somente ao catálogo público compartilhado e/ou à configuração de permissão da categoria de catálogo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Relatórios, Cloud

* _ACP2E-3067_: o Magento descarta a maioria das transações New Relic cron #34108
   * _Observação de correção_: o AC está relatando corretamente as transações relacionadas ao trabalho cron para a NewRelic. Anteriormente, algumas transações relacionadas a trabalhos do cron eram mostradas como &quot;OtherTransaction/Action/unknown&quot; no NR
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_: bordas desnecessárias na seção Meus Pedidos
   * _Observação de correção_: anteriormente, era criado um contêiner adicional (referências de ordem) que aplicava classes CSS adicionais, o que fazia com que linhas de borda desnecessárias fossem exibidas abaixo do número de ordem na seção Meus Pedidos, que não está visível agora.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### B2B, Estrutura

* _AC-9607_: Filtrar a Grade da Empresa e, em seguida, Tentar Exportar para Grade em CSV Apresentará Falha e Lançará Exceção
   * _Observação de correção_: o sistema agora permite a exportação bem-sucedida em CSV dos dados da grade Empresas no painel de administração, mesmo quando filtros como &quot;Saldo Pendente&quot; e &quot;Tipo de Empresa&quot; são aplicados. Anteriormente, a aplicação de determinados filtros e a tentativa de exportar os dados da grade resultavam em uma falha e em uma exceção.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _PACOTE-3367_: Pagar via LPM
   * _Observação de correção_: o sistema agora renderiza corretamente os Métodos de Pagamento Local (LPM) na carga inicial, mesmo quando os endereços de entrega e cobrança de um cliente conectado não coincidem, garantindo um processo de finalização suave. Anteriormente, uma incompatibilidade entre os endereços de envio e de cobrança de um cliente impedia a renderização do LPM, causando possíveis interrupções durante o checkout.
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_: configurável com o produto Virtual como secundário
   * _Observação de correção_: o sistema agora permite métodos de pagamento expresso para produtos configuráveis que têm um produto filho virtual, garantindo um processo de finalização suave. Anteriormente, os métodos de pagamento expresso não estavam disponíveis quando um produto configurável com um produto filho virtual era adicionado ao carrinho.
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_: Erro de falha na verificação de CVV
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PACOTE-3370_: Problemas de Compartimentação pela Área da conta 247
   * _Observação de correção_: o sistema agora permite que os clientes salvem informações de um novo cartão ou de uma conta do PayPal em vários sites sem encontrar erros de autorização. Anteriormente, os clientes não conseguiam salvar novos métodos de pagamento em diferentes sites e apresentavam uma mensagem de erro de autorização.
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_: Enviar para um endereço de um país diferente
   * _Observação de correção_: o sistema agora permite que as transações sejam processadas sem erros ao enviar para um endereço de um país diferente, garantindo um processo de finalização suave. Anteriormente, tentar enviar para um endereço de um país diferente resultava em erros de console, apesar de não haver erros visíveis no front-end.
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_: Cartão de Crédito - Função de Desmontagem
   * _Observação de correção_: o sistema agora lida corretamente com a desmontagem dos componentes do Braintree PayPal quando um cliente navega de volta da página de pagamento para a página de remessa, evitando erros e garantindo que os botões do PayPal Express sejam renderizados corretamente. Anteriormente, navegar de volta para a página de remessa a partir da página de pagamento às vezes resultava em um erro ao tentar destruir os componentes do Braintree PayPal.
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PACOTE-3373_: Retorno de Chamada de Remessa para PayPal Express
   * _Observação de correção_: o sistema agora exibe corretamente os métodos de envio disponíveis no modal do PayPal Express, permitindo que os clientes selecionem seu método de envio preferido antes de prosseguir para a página de revisão ou concluir sua transação. Anteriormente, nenhum método de envio estava disponível para seleção no modal do PayPal Express, exigindo que os clientes selecionassem um método de envio em uma página de revisão separada antes que pudessem concluir sua transação.
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/204>

### Carrinho e saída

* _AC-10660_: a exceção não está sendo tratada corretamente ao adicionar um produto ao carrinho na página comparar produtos
   * _Observação de correção_: o sistema agora lida corretamente com exceções ao adicionar um produto ao carrinho na página de comparação do produto, exibindo uma mensagem do gerenciador de mensagens no controlador. Anteriormente, uma exceção resultava no retorno de uma página codificada em JSON, em vez de ser capturada e manipulada corretamente.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38200>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag não envia preços e totais de transação.
   * _Observação de correção_: o sistema agora envia corretamente os preços e os totais das transações para a Marca da Google quando o GTag está habilitado, garantindo um rastreamento preciso dos dados de comércio eletrônico. Anteriormente, a moeda estava sendo enviada incorretamente como parte dos pedidos &quot;all&quot;, em vez de ser associada ao pedido individual.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37348>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Problema] [Check-out] Diretivas de dependência atualizadas no modelo de email de pagamento com falha
   * _Observação de correção_: o sistema agora omite corretamente o endereço e o método de envio do modelo de email de pagamento com falha para produtos virtuais, garantindo que apenas informações relevantes sejam incluídas no email. Anteriormente, o e-mail de pagamento com falha para produtos virtuais incluía incorretamente o endereço e o método de envio.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32781>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32511>
* _AC-11876_: [Problema] Regressão de regras de vendas na versão 2.4.7
   * _Observação de correção_: o sistema agora valida corretamente as regras de vendas, impedindo a aplicação de um código de cupom a um carrinho quando a condição do produto não corresponde a nenhum nome de produto. Anteriormente, era possível aplicar uma regra de vendas e conceder um desconto no valor do envio mesmo quando a condição do produto não correspondia a nenhum nome de produto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38671>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_: [Problema] O carregador bloqueia os métodos de envio depois que o código postal é alterado, taxas de envio e regras de validação
   * _Observação de correção_: o sistema agora lida corretamente com métodos de envio personalizados sem regras de validação de taxas de envio, garantindo que o carregador não bloqueie os métodos de envio depois que o código postal for alterado no endereço de envio durante o check-out. Anteriormente, alterar o código postal no endereço de entrega durante a finalização da compra fazia com que o carregador bloqueasse os métodos de entrega e não desaparecesse quando métodos de entrega personalizados sem regras de validação de taxas de entrega fossem usados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38742>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: o recurso de código do cupom não está funcionando corretamente na página de check-out do Magento 2.4.7
   * _Observação de correção_: o sistema agora habilita o campo de entrada de código de desconto/cupom na página de check-out para produtos virtuais e baixáveis, permitindo que os usuários apliquem códigos de desconto conforme esperado. Anteriormente, a entrada do código de desconto/cupom era desativada e o texto do título do botão era exibido como &quot;Cancelar cupom&quot;, impedindo que os usuários aplicassem códigos de desconto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38826>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-8103_: IVA de tradução no renderizador de endereço
   * _Observação de correção_: o sistema agora permite a tradução do texto &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; nos renderizadores de endereço, permitindo que os usuários traduzam esses termos para o idioma específico do armazenamento. Anteriormente, esses termos não podiam ser traduzidos, forçando os usuários a fazerem uma solução alternativa.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36942>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: Pedidos duplicados com a mesma Id de Cotação ao mesmo tempo com poucas diferenças de tempo
   * _Observação de correção_: corrigiu o problema quando os clientes da Adobe Commerce encontraram pedidos duplicados feitos com a mesma QuoteID
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: carrinho de compras persistente limpo durante a etapa de check-out
   * _Observação de correção_: após a correção, selecionar o método de pagamento durante o check-out sem logon não encerra a sessão persistente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: Reordenar adiciona produto não atribuído ao carrinho
   * _Observação de correção_: anteriormente, para as diferentes lojas, os produtos podem ser reordenados da outra loja. Depois que essa correção for aplicada somente à mesma loja, o mesmo produto de escopo poderá ser reordenado quando o compartilhamento de conta do cliente for habilitado
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: no admin, o &quot;Carrinho de Compras&quot; no lado esquerdo não é atualizado ao selecionar os itens e &quot;Mover para o Carrinho de Compras&quot; no lado direito
   * _Observação de correção_: o &quot;Carrinho de compras&quot; no lado esquerdo é atualizado ao selecionar os itens e a opção &quot;Mover para carrinho de compras&quot; no lado direito no lado administrativo. Anteriormente, essa funcionalidade não funcionava porque os itens do carrinho transformados não ficavam vazios na sessão.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [Regra de Vendas da {Cloud] não aplicada à primeira ordem de Envio Múltiplo
   * _Observação de correção_: após a correção, o desconto é mostrado corretamente para cada pedido da mesma cotação de remessa múltipla.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: As Solicitações Paralelas de Produção da [Cloud] para Adicionar o Mesmo Produto ao Carrinho Resultam em Dois Itens Separados na API de Resto do Carrinho
   * _Observação de correção_: o sistema agora processa corretamente várias solicitações paralelas para adicionar o mesmo produto ao carrinho em um único item de linha, impedindo a criação de itens de linha separados para o mesmo SKU. Anteriormente, fazer solicitações paralelas para adicionar o mesmo produto ao carrinho por meio da API REST resultava em vários itens de linha para a mesma SKU.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: Obtendo Não É Possível enviar o cookie. Tamanho de &quot;mage-messages&quot; ao tentar reordenar
   * _Observação de correção_: o processo de reordenação não gerará seus próprios erros agora. Ele dependerá das verificações de item integradas à lista do carrinho.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: o endereço de remessa padrão não está selecionado no check-out
   * _Observação de correção_: o endereço de remessa padrão agora está sendo selecionado no contexto da pesquisa de endereço habilitada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [CLOUD] problema da api graphql addProductsToCart com opção personalizada
   * _Observação de correção_: a GraphQL adiciona ao carrinho corretamente o mesmo produto com diferentes opções personalizadas
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Vários endereços adicionados à conta ao fazer check-out como novo cliente
   * _Observação de correção_: o sistema agora salva um novo endereço de cliente apenas uma vez se a ordem não for criada, impedindo a criação de vários endereços idênticos em caso de erros de posicionamento de ordem. Anteriormente, o sistema salvava um novo endereço sempre que uma tentativa de colocação de pedido era feita, independentemente de o pedido ter sido criado com sucesso ou não.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Reordenar o pedido do cliente através do formulário de pedido de convidado resulta em um carrinho vazio
   * _Observação de correção_: anteriormente, ao fazer um novo pedido por meio da página Pedidos e Devoluções, o cliente era redirecionado para a página de logon. Depois que essa correção for aplicada, o cliente registrado será redirecionado corretamente para a página Exibir carrinho ao fazer um novo pedido. O fluxo funciona da mesma forma que os clientes convidados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: usuário administrador com recursos de função limitada não pode exibir carrinhos de compras
   * _Observação de correção_: anteriormente, o administrador restrito não podia ver o carrinho de compras abandonado no painel de administração de um site associado. Depois que essa correção for aplicada, o administrador restrito poderá ver o carrinho de compras abandonado no painel de administração.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>

### Carrinho e check-out, check-out/check-out de uma página

* _AC-9386_: [BUG aleatório] O campo Email não é renderizado ou leva muito tempo para ser exibido na página Envio para Finalização de Compra ou Pagamento
   * _Observação de correção_: o Commerce agora renderiza o campo **[!UICONTROL Email]** nas páginas de remessa e pagamento de check-out conforme esperado. Anteriormente, esse campo estava ausente ou era renderizado lentamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/e1babcfd>

### Carrinho e check-out, pedido

* _ACP2E-3097_: Datepicker para um produto com várias Opções Personalizáveis com campos de data que não funcionam ao solicitar do administrador
   * _Observação de correção_: o sistema agora exibe corretamente o seletor de datas para todos os campos de data ao configurar um produto com várias opções de data personalizáveis no processo de criação de pedido de administrador. Anteriormente, o seletor de datas era exibido apenas para o primeiro campo de data, deixando os campos restantes sem um seletor de datas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Carrinho e check-out, envio

* _AC-12119_: compra instantânea &quot;envio mais barato&quot; interrompida para produtos configuráveis
   * _Observação de correção_: o recurso Compra instantânea selecionou incorretamente a opção Entrega na loja mais cara para produtos configuráveis, em vez do método de Taxa fixa mais barato. Essa correção garante que o método de envio correto seja escolhido com base no preço real.&quot;
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38811>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catálogo

* _AC-10910_: a limpeza da tabela de banco de dados cron_schedule não limpa trabalhos não existentes
   * _Observação de correção_: o sistema agora limpa automaticamente a tabela de banco de dados cron_schedule, removendo entradas para trabalhos que não existem mais no sistema. Isso garante o desempenho ideal, mantendo um número mínimo de linhas na tabela. Anteriormente, as entradas para trabalhos de módulos inativos ou removidos não eram limpas, resultando em acúmulo desnecessário de dados na tabela cron_schedule.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38217>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: o preço da camada não está sendo excluído do produto configurável
   * _Observação de correção_: o sistema agora remove corretamente o preço de camada de um produto quando ele é convertido de um produto simples em um produto configurável, garantindo uma exibição precisa do preço no front-end. Anteriormente, o preço de nível de um produto configurável não era excluído quando um produto era convertido de um produto simples em um produto configurável, resultando em uma incompatibilidade no preço exibido.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38390>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: descrição de categoria WYSIWYG está vazia em uma loja não padrão
   * _Observação de correção_: o sistema agora salva e exibe corretamente a descrição da categoria no editor do WYSIWYG ao editar uma categoria no nível de exibição da loja. Anteriormente, o editor do WYSIWYG parecia vazio após salvar uma descrição de categoria no nível de exibição de loja.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38622>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38623>
* _AC-12076_: [Problema] Corrigir o texto do item de filtro na navegação em camadas
   * _Observação de correção_: o sistema agora usa corretamente as palavras &quot;item&quot; e &quot;itens&quot; no item do filtro de navegação em camadas, melhorando a clareza e a precisão das descrições do filtro. Anteriormente, essas palavras eram usadas incorretamente, resultando em possível confusão para os usuários que navegavam pelas opções de filtro.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38789>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: o formato de data e hora para a opção personalizada não está funcionando
   * _Observação de correção_: o sistema agora aplica corretamente o formato de data configurado às opções personalizadas de produto do tipo Data, garantindo que o formato de data seja exibido corretamente no front-end. Anteriormente, as alterações na configuração do formato de data não refletiam no front-end para opções personalizadas de produto do tipo Data.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32990>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38925>
* _AC-6738_: chave exclusiva ausente na tabela eav_attribute_option_value
   * _Observação de correção_: o sistema agora inclui uma chave exclusiva nas colunas &#39;option_id&#39; e &#39;store_id&#39; na tabela &#39;eav_attribute_option_value&#39;, evitando a possibilidade de uma opção ter vários valores para a mesma exibição de armazenamento. Anteriormente, um código com falha podia resultar em uma opção com vários valores para a mesma visualização de loja, causando problemas ao editar produtos ou atributos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/24718>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Problema] Use a classe de visibilidade para indexador de produto de categoria, em vez de valores codificados
   * _Observação de correção_: o sistema agora usa a classe de visibilidade para o indexador de produto da categoria em vez de valores codificados, melhorando a modularidade. Anteriormente, valores codificados eram usados no indexador de produto da categoria, limitando a flexibilidade e adaptabilidade.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37200>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: o código de moeda não é alterado no novo widget do produto
   * _Observação de correção_: o sistema agora atualiza corretamente o código de moeda no widget Novo produto quando a moeda é alterada no front-end, garantindo a consistência na exibição da moeda no site. Anteriormente, alterar a moeda no front-end não afetava o código de moeda exibido no widget Novo produto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37898>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: o Preço Normal não é exibido no PLP para o Produto Configurável
   * _Observação de correção_: o preço normal agora é exibido nas páginas de listagem de produtos para produtos configuráveis que têm produtos secundários com preço especial.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: as informações de ações não são exibidas diretamente na grade Visual Merchandising
   * _Observação de correção_: o estoque agora é exibido de acordo com o armazenamento selecionado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: o conteúdo do widget não está sendo atualizado na página cms
   * _Observação de correção_: o sistema agora atualiza o conteúdo do widget em uma página do CMS quando um produto é definido como novo e salvo, garantindo que a página exiba a coleção de produtos atualizada. Anteriormente, a página não era atualizada para mostrar o novo produto devido às identidades de cache incorretas usadas para o widget no cache.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: problemas ao salvar preços avançados em produtos de pacote
   * _Observação de correção_: melhoria no desempenho de economia de produtos em pacote.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [No Local] O processo de reindexação é ineficiente ao criar Regras de Preço de Catálogo
   * _Observação de correção_: salvar agora a regra de preço de catálogo não invalidará os indexadores; em vez disso, ela reindexará somente os produtos afetados
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: atualizando hora dos atributos de produto do tipo Data e Hora por meio da importação de CSV
   * _Observação de correção_: agora, os atributos datetime terão parte do tempo nos dados exportados. Também será possível atualizar o horário desses atributos usando importar. Além disso, se &quot;Compartimento de campos&quot; estiver ativado, os valores de atributo na coluna &quot;additional_attributes&quot; serão colocados entre aspas duplas.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38306>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: Nenhuma mensagem de erro apropriada quando a ID do site estiver incorreta na solicitação
   * _Observação de correção_: agora a mensagem de erro apropriada foi adicionada para ser exibida quando a ID do site estiver incorreta na solicitação. Anteriormente, não havia validação quando a ID do site estava incorreta na solicitação.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: a imagem do produto é perdida após a exclusão de uma Atualização Agendada existente que não afeta a imagem
   * _Observação de correção_: as imagens do produto não são removidas durante a exclusão da atualização de preparo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Nuvem] Preço de produto de pacote incorreto quando usado com preços de camada
   * _Observação de correção_: anteriormente, ao calcular determinados descontos percentuais arredondados para até 2 pontos decimais, geravam preços finais diferentes para o carrinho e a página de página de listagem de produtos/detalhes do produto. Depois que essa correção é aplicada, o preço final do pacote é o mesmo da página Detalhes do produto, da página Lista de produtos e da página do minicarrinho.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38091>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: a Regra de Promoções de Catálogo não funciona com o atributo quantity_and_stock_status
   * _Observação de correção_: o atributo quantity_and_stock_status agora será considerado pela regra de promoção do catálogo, que não foi considerada anteriormente ao gerar um novo produto pelo lado administrativo.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/35627>
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: os valores de coluna updated_at da entidade do produto não são atualizados durante a atualização do preço por meio da API REST
   * _Observação de correção_: a coluna &#39;última atualização às&#39; do produto do administrador é atualizada na data e hora apropriadas durante a atualização dos produtos existentes por meio da API REST. Anteriormente, a coluna &quot;Última atualização em&quot; não era atualizada corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: é possível definir valores não exclusivos através da importação do produto
   * _Observação de correção_: o sistema agora impõe corretamente a restrição de valor único para atributos de produto exclusivos durante a importação do produto, impedindo que haja valores duplicados para esse atributo. Anteriormente, era possível definir valores não exclusivos para atributos de produto configurados para terem valores exclusivos por meio da importação de produtos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38445>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: os produtos no front-end usam dados específicos do repositório quando o Modo de Repositório Único está habilitado
   * _Observação de correção_: anteriormente, quando habilitávamos o modo de repositório único para a exibição de repositório padrão, as alterações não eram migradas para o escopo no nível do site. Depois que essa correção for aplicada, ao habilitar o modo de loja única, os dados específicos da exibição da loja padrão serão sincronizados com os dados específicos do nível do site e resolverão os possíveis conflitos de produtos e categorias.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: não é possível definir &quot;Classificar por Padrão&quot; em uma categoria usando a API rest
   * _Observação de correção_: atualize corretamente default_sort_by em uma categoria por meio da solicitação REST/SOAP APi
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Nuvem] O Comerciante está enfrentando problemas com a contagem da lista de desejos
   * _Observação de correção_: adicionar um produto à lista de desejos em uma loja não aumenta mais a contagem de listas de desejos em outras lojas abertas no mesmo navegador. Anteriormente, se ambas as lojas fossem carregadas no mesmo navegador, a contagem de listas de desejos aumentaria na outra loja também.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: a Página de Categoria no front-end mostra slots vazios ao usar o produto de pacote
   * _Observação de correção_: os produtos do pacote que não podem ser vendidos no contexto de armazenamento atual não são mais indexados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: [Problema de Cotação na Nuvem] na arquitetura de vários sites
   * _Observação de correção_: anteriormente, a arquitetura de vários sites com moedas e grupos de clientes diferentes não podia aplicar descontos corretamente à loja. Depois que essa correção for implementada, a arquitetura de vários sites com descontos de preço de grupo de clientes diferentes será aplicada com sucesso a diferentes lojas.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38506>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 TypeError não capturado: dataRecord.slice ao editar produtos do pacote
   * _Observação de correção_: não há erro de javascript no console do navegador ao excluir a opção do produto do pacote.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38505>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Pacote de preços incorretos do produto na confirmação do pedido
   * _Observação de correção_: o valor correto é exibido para opções de pacote em ordem na Loja quando uma moeda diferente da base foi usada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Vídeo do YouTube Adicionando Erro
   * _Observação de correção_: imagens e vídeos de produtos estão configurados no escopo global. Considerando que você não pode ter um vídeo de produto em um escopo e não em outro, a configuração da chave de API do Youtube foi definida como escopo global.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: Atualização de URL da [Nuvem] somente para store_id=0
   * _Observação de correção_: o &quot;Caminho da URL&quot; agora é armazenado com a ID de armazenamento correta. Anteriormente, a ID de armazenamento estava incorreta, resultando em caminhos de URL incorretos restantes no banco de dados ao mover categorias.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all executado e criou um erro.
   * _Observação de correção_: dados incorretos do link do produto em chamadas da API REST não causam mais erros críticos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: Problema de Celular da [Nuvem] não pode beliscar apenas na imagem PDP
   * _Observação de correção_: o sistema agora oferece suporte à funcionalidade pinçar para zoom em imagens da página de detalhes do produto no modo de exibição móvel no Chrome, melhorando a experiência do usuário móvel. Anteriormente, o toque duplo na imagem na exibição móvel no Chrome não aumentava a imagem conforme esperado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: rótulo ausente em LayeredNavigation com o nome de opção 0
   * _Observação de correção_: o problema foi resolvido ignorando um verificador de valor vazio para o valor de atributo 0. Anteriormente, era considerado vazio e estava causando o problema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: os clientes veem os preços de outros grupos de clientes
   * _Observação de correção_: correção de um problema em que as informações relacionadas ao grupo de clientes eram salvas em um segmento incorreto devido ao valor antigo de X-Magento-Vary na solicitação
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: erro ao excluir opções de pacote
   * _Observação de correção_: o sistema agora exclui corretamente as opções do pacote sem disparar um erro ou fazer com que a página não responda. Anteriormente, tentar excluir opções de pacote resultava em um erro de &quot;Página sem resposta&quot; e impedia que o produto fosse salvo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: o Arquivo de Imagem da [Nuvem] não existe no Log de Erros do New Relic
   * _Observação de correção_: o sistema agora sincroniza imagens de espaço reservado personalizadas com o armazenamento local, garantindo que elas sejam renderizadas corretamente ao usar o armazenamento remoto, como o AWS S3. Anteriormente, as imagens personalizadas de espaço reservado não eram renderizadas ao usar o armazenamento remoto, resultando em uma exibição de imagem com falha e logs de erro.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_: a resposta GQL da Galeria de Mídia do Produto [Cloud] não é classificada pela posição da imagem
   * _Observação de correção_: o sistema agora classifica corretamente os itens na galeria de mídia por posição na resposta do GraphQL, garantindo uma ordem de exibição precisa. Anteriormente, os itens na galeria de mídia não eram classificados por posição, resultando em uma ordem de exibição incorreta.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37671>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: os itens da subcategoria [Nuvem] não são exibidos na edição de widgets no back-end do administrador
   * _Observação de correção_: a árvore de categorias na nova página do widget não deve mais ter problemas ao carregar as categorias de Nível 5+. Anteriormente, algumas categorias estavam ausentes ao carregar a árvore após as categorias de Nível 5.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/148c3ead>

### Catálogo, Estrutura

* _ACP2E-2949_: [Nuvem]Acompanhamento: Incompatibilidade na Comparação de Dados ao verificar se os dados têm alterações
   * _Observação de correção_: anteriormente, o objeto salvo era chamado sempre sem nenhuma alteração de dados (para qualquer campo de dados numérico, como int/float/double). Ele aciona o sinalizador _hasDataChanges para ser true e chama a função de salvamento. Também não verifica os números flutuantes encapsulados por string. Depois que essa correção for aplicada, a função salvar só chamará se os dados forem alterados. O valor de dados para int/float/double-check com o valor passando para a função e faz correspondência de tipo strict
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8931218>

### Catálogo, GraphQL

* _ACP2E-3090_: Manipulando Filtros de Categoria no GraphQL: includeDirectChildrenOnly e category_uid
   * _Observação de correção_: somente as categorias secundárias diretas são buscadas durante a filtragem por category_uid.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: a classificação de produto Graphql da [Cloud] não funciona
   * _Observação de correção_: a classificação de produto GraphQl por vários campos quando os campos são passados em variáveis agora funciona conforme esperado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/8459b17d>

### Catálogo, preços, preparo e visualização

* _ACP2E-2672_: [Nuvem] O ponto de extremidade da API de preço especial retorna um erro ao atualizar um grande número de produtos simultaneamente
   * _Observação de correção_: agora, a API de atualização em massa de Preço especial criará uma única campanha para cada intervalo de datas, em vez de várias atualizações agendadas para cada produto e intervalo de datas. Além disso, oferecerá suporte a solicitações de API simultâneas para processamento mais rápido de um grande número de SKUs.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>

### Catálogo, Produto

* _AC-7050_: a árvore de seleção de categoria no produto de edição não está na mesma ordem definida em Catálogo->Categorias
   * _Observação de correção_: o sistema agora exibe corretamente a árvore de seleção de categoria na seção de edição do produto na mesma ordem definida em Catálogo ->Categorias, facilitando a administração de produtos em catálogos grandes. Anteriormente, a árvore de categorias na seção de edição do produto era exibida na ordem de criação da categoria, independentemente da ordem de exibição definida em Catálogo ->Categorias.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36101>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36104>

### Catálogo, Pesquisa

* _ACP2E-2757_: os produtos não estão aparecendo na categoria e na pesquisa, mas os links diretos estão funcionando
   * _Observação de correção_: anteriormente, o atributo personalizado Sim/Não com price_* attribute_code não funcionava com indexação. Após essa correção, o atributo personalizado Sim/Não funciona conforme esperado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Nuvem] Erro de pesquisa elástica em determinadas páginas de categoria
   * _Observação de correção_: anteriormente, com o tíquete de configuração mencionado, quando colocamos o preço 0 para vários produtos, isso lançará uma exceção na página de categoria de front-end. Após essa correção aplicada quando vários preços de produto 0 e carregamos a página de categoria no front-end, não haverá nenhuma exceção e a página de categoria será carregada com êxito.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8931218>

### Nuvem

* _ACP2E-3010_: [Cloud] PHPSESSID está alterando cada Solicitação POST
   * _Observação de correção_: PHPSESSID não é mais regenerado em solicitações de POST na área de front-end para um cliente conectado se o cache L2 Redis estiver habilitado e o cliente tiver sido atualizado no back-end
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Conteúdo

* _AC-10539_: [Problema] problema com o preço de exibição no widget Recentemente visualizado
   * _Observação de correção_: o sistema agora exibe corretamente o preço dos produtos simples indisponíveis no widget &quot;Produto visualizado recentemente&quot;, garantindo a consistência entre todos os widgets e páginas de lista de produtos. Anteriormente, o preço dos produtos simples indisponíveis não era exibido no widget &quot;Produto visualizado recentemente&quot; devido a uma condição nos modelos de carregamento de preço.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38167>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problema] Corrija o erro de digitação e gramática no arquivo acl.xsd
   * _Observação de correção_: o sistema agora corrige um erro de digitação e gramática no arquivo acl.xsd, melhorando a clareza e a precisão da documentação. Anteriormente, o arquivo acl.xsd continha um erro de digitação e uma gramática incorreta que poderia causar confusão.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38061>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: imagem de banner do Pagebuilder não visível na galeria
   * _Observação de correção_: o sistema agora exibe corretamente as imagens de banner carregadas nas pastas recém-criadas na galeria do Pagebuilder, eliminando erros anteriores do console. Antes dessa correção, as imagens de banner não estavam visíveis na galeria se fossem carregadas em uma nova pasta, causando um erro de console.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;Código de área não definido&quot; após a atualização para 2.4.5-p8
   * _Observação de correção_: o sistema agora conclui com êxito o processo de implantação de conteúdo estático quando o módulo Magento_CSP está habilitado e &quot;dev/js/translate_strategy&quot; está definido como &quot;incorporado&quot;, sem disparar o erro &quot;Código de área não definido&quot;. Anteriormente, sob essas condições, o processo de implantação de conteúdo estático falhava com um erro &quot;Código de área não definido&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38845>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38922>
* _AC-9638_: problema de carregamento de arquivo [Problema] no editor do WYSIWYG na página do produto
   * _Observação de correção_: o sistema agora exibe corretamente a árvore de pastas e permite carregamentos de imagens no editor do WYSIWYG na página do produto, mesmo depois de expandir a guia &quot;Imagens e vídeos&quot; primeiro. Anteriormente, expandir a guia &quot;Imagens e vídeos&quot; primeiro resultava na não exibição da árvore de pastas e em uma mensagem de erro ao tentar fazer upload de uma imagem no editor do WYSIWYG.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38026>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [No LOCAL] Problema de bloco dinâmico
   * _Observação de correção_: os wdigets estão sendo renderizados corretamente dentro de blocos dinâmicos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: [Nuvem] O front-end não está carregando devido a um problema no modelo de informativo
   * _Observação de correção_: a adição de blocos por meio da seção de conteúdo da Página do CMS não gera mais exceções
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Cloud] Investigar exceção encontrada no log: InvalidArgumentException: A classe não existe em vendor/magento/module-rule/Model/ConditionFactory.php
   * _Observação de correção_: a remoção de uma condição nas configurações de conteúdo dos produtos do PageBuilder não faz mais com que uma exceção seja registrada nos arquivos de log. Anteriormente, a remoção de uma condição nas configurações de conteúdo dos produtos do PageBuilder causava a gravação de uma exceção crítica nos logs, embora não causasse problemas no front-end.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: alternando para o modo de repositório único - o conteúdo global não aparece mais
   * _Observação de correção_: o sistema agora sincroniza configurações de design de modo de exibição de repositório com configurações de design de site ao habilitar o modo de repositório único, garantindo que as atualizações de conteúdo estejam visíveis no front-end. Anteriormente, alternar para o modo de armazenamento único evitava que as atualizações de conteúdo fossem refletidas na loja.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: o Page Builder substitui a imagem ao tentar adicionar o link e outras falhas de usabilidade.
   * _Observação de correção_: agora, ao clicar em uma imagem, os links no editor wysiwyg no elemento de texto do Page Builder carregarão os dados apropriados na imagem e na caixa de diálogo de configuração do link. Adicionar um link a uma imagem no editor agora funciona corretamente. Anteriormente, a imagem era substituída por um link.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: a galeria de mídia antiga falha ao renderizar imagens quando uma imagem de 0 bytes é colocada no diretório
   * _Observação de correção_: o sistema agora lida com imagens de 0 bytes na galeria de mídia sem interromper a funcionalidade, permitindo que outras imagens no diretório sejam exibidas e selecionadas conforme esperado. Anteriormente, a presença de uma imagem de 0 byte na galeria de mídia impedia que todas as imagens no diretório fossem exibidas ou selecionadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Erro no Page Builder ao editar o Bloco do CMS
   * _Observação de correção_: o sistema agora salva corretamente as alterações feitas na área de administração usando o Page Builder, sem gerar o erro &quot;O Page Builder foi renderizado por 5 segundos sem liberar bloqueios.&quot; no console do navegador. Anteriormente, esse erro ocorria ao tentar salvar alterações, impedindo a atualização bem-sucedida do conteúdo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] Não há botões para check-out ou editar o carrinho na seção do carrinho
   * _Observação de correção_: o produto do pacote agora é adicionado ao carrinho por meio de widgets sem erros.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3127_: imagecreatetruecolor(): O argumento #2 ($height) deve ser maior que 0. Não é possível carregar uma imagem específica
   * _Observação de correção_: resolveu o problema que causava erros no administrador ao carregar imagens com altura 0 pela galeria de mídia e obteve êxito na sincronização de ativos usando o comando sync. Anteriormente, o não podia fazer upload da imagem pela galeria de mídia e o comando sync também falhava quando uma imagem específica estava na galeria.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from em conflito com a API do Google Maps
   * _Corrigir observação_: o Google Maps agora é renderizado corretamente no editor do PageBuilder. Anteriormente, um erro de Javascript impedia que o Google Maps fosse renderizado corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/148c3ead>

### Cliente/ Clientes

* _AC-12162_: Front-end - A validação da data de nascimento falhou na página de criação do cliente
   * _Observação de correção_: certifique-se de que toda a validação funcione após a dependência do sistema Moment.js de atualização para a versão secundária mais recente
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>

### Estrutura

* _AC-10654_: V1/customers/password/endpoint question/issue
   * _Observação de correção_: o sistema agora segue as restrições definidas na GUI de gerenciamento ao processar solicitações de alteração de senha por meio da API, evitando possível abuso da função de redefinição de senha. Anteriormente, a API podia processar solicitações de alteração de senha fora das regras definidas na GUI de gerenciamento, possivelmente permitindo um fluxo constante de emails de redefinição se os emails válidos fossem conhecidos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38238>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_:
   * _Observação de correção_: atualize as dependências do league/flysystem Composer para a versão mais recente
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _Contribuição de código do GitHub_: atualize as dependências do 2.x league/flysystem Composer para a versão mais recente 3.x
* _AC-10838_: processo de indexação de erro do processo de índice de pesquisa de catálogo
   * _Observação de correção_: o sistema agora conclui com êxito o comando re-index sem encontrar nenhum erro, independentemente da versão libxml compilada com PHP. Anteriormente, a execução do comando re-index resultava em um erro de processo de índice de pesquisa de catálogo durante o processo de indexação quando o PHP era compilado com determinadas versões de libxml.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38254>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: adição dos filtros created_at, status e grand_total à consulta Pedidos do cliente e correção de várias falhas de filtros
   * _Observação de correção_: o sistema agora oferece suporte ao uso de filtros created_at, status e grand_total em consultas de Pedidos de clientes e resolveu um problema em que vários filtros não estavam sendo aplicados corretamente. Anteriormente, o sistema não aceitava esses filtros e não aplicava todos os filtros quando mais de um era usado em um query.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38392>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36949>
* _AC-10971_: https://github.com/magento/magento2/issues/38415
   * _Nota de correção_: PHP 8.2/8.3, somente uma dependência falha no linter php no momento: league/flysystem
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribuição de código do GitHub_: o sistema agora oferece suporte ao PHP 8.2/8.3 ao atualizar o pacote league/flysystem para a versão 3.0.20, garantindo que não ocorram erros de listagem do PHP. Anteriormente, a execução de arquivos PHP através do PHP linter com PHP 8.3 resultava em erros de linting no pacote league/flysystem.
* _AC-10991_: aleatoriamente inundação de consultas de blocos relacionados/de venda adicional/venda cruzada e indexação de preços
   * _Observação de correção_: o sistema agora otimiza consultas de blocos relacionados, de venda adicional e de venda cruzada, melhorando o desempenho e evitando que o site seja desativado devido a consultas excessivas. Anteriormente, o sistema podia ficar sobrecarregado com consultas desses blocos, causando lentidão significativa e possivelmente desativando o site.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36667>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Exceção: Aviso: Tentando acessar deslocamento de matriz em... -> Calendar.php desde a atualização para ICU 74.1 (Intl PHP)
   * _Observação de correção_: a Commerce não registra mais a seguinte exceção no exception.log sempre que um comprador ou comerciante visita a loja ou o Administrador: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38214>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Problema] Corrija problemas com os Dados do cliente quando o formulário contém um elemento com o nome `method`
   * _Observação de correção_: o sistema agora identifica corretamente o atributo &quot;método&quot; nos envios de formulários, mesmo quando um elemento chamado &quot;método&quot; está presente no formulário. Isso garante o processamento preciso dos dados do cliente. Anteriormente, se um elemento de formulário fosse nomeado como &quot;método&quot;, ele interferiria na identificação do atributo &quot;método&quot; nos envios de formulários, resultando em possíveis problemas com o manuseio de dados do cliente.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38484>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Problema] Corrigir PHPDocs para \Magento\Framework\Data\Collection::getItemById
   * _Observação de correção_: os PHPDocs do método \Magento\Framework\Data\Collection::getItemById foram atualizados para incluir nulo como um possível tipo de retorno, abordando problemas com ferramentas de análise estática. Anteriormente, os PHPDocs do método não especificavam null como um possível tipo de retorno, levando a avisos ou erros na análise estática quando o método era usado em declarações condicionais.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38485>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38439>
* _AC-11651_: Magento tentando modificar propriedade somente leitura no método __wakeup de LoggerProxy
   * _Observação de correção_: o sistema agora permite a modificação de propriedades somente leitura anteriores no método __wakeup do LoggerProxy, garantindo uma operação suave sem forçar os usuários a empregar uma solução alternativa. Anteriormente, uma tentativa de reatribuir o valor de uma propriedade somente leitura no método __wakeup do LoggerProxy causaria problemas.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38526>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_:
   * _Observação de correção_: investigue as versões mais recentes do php-amqplib/php-amqplib
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribuição de código do GitHub_: atualização da versão mais recente php-amqplib/php-amqplib :^3.x
* _AC-11681_: [Problema] referências AC-2039 AC-1667 de atualização do TinyMCE
   * _Observação de correção_: atualização da versão mais recente do tinymce no composer.json
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38533>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker não funciona em vários threads
   * _Observação de correção_: o sistema agora oferece suporte à bifurcação de processo para indexação MView, evitando erros durante a execução do indexador ao operar em vários threads. Anteriormente, executar ChangelogBatchWalker em várias threads levava à exclusão de tabelas usadas por outras threads, causando um erro durante a execução do indexador.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38246>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Problema] Renomear variável nomeada incorretamente
   * _Observação de correção_: o sistema agora nomeia corretamente a variável que contém a quantidade de dinheiro que ainda pode ser reembolsado, evitando confusão durante a depuração. Anteriormente, essa variável era nomeada incorretamente como totalRefund, o que poderia levar a mal-entendidos para os desenvolvedores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38609>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36205>
* _AC-11808_:
   * _Observação de correção_: investigue e atualize a lista de dependências principais do Adobe Commerce
   * _Contribuição de código do GitHub_: é necessário atualizar a lista de dependências principais do Adobe Commerce 
* _AC-11819_: o cache FPC interno está corrompido na versão 2.4.7 para algumas configurações
   * _Observação de correção_: o sistema agora armazena páginas em cache corretamente quando o parâmetro MAGE_RUN_CODE está definido, garantindo um desempenho ideal. Anteriormente, as páginas não eram armazenadas em cache sob essas condições, resultando em possíveis problemas de desempenho.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38626>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [Problema] Corrigir exceção ao manipular inconsistência entre modos de desenvolvedor e de produção
   * _Observação de correção_: o sistema agora lida consistentemente com exceções entre os modos de desenvolvedor e de produção, impedindo o redirecionamento inesperado para a página de logon quando uma exceção é lançada. Anteriormente, uma inconsistência no tratamento da exceção poderia causar um redirecionamento para a página de logon no modo de produção em vez de exibir a mensagem de exceção.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38639>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: Substituir a conversão &#39;Conta do PayPal&#39; em token_list.phtml
   * _Observação de correção_: o sistema agora rotula a seção para métodos de pagamento de conta tokenizáveis como &quot;Conta&quot; em vez de &quot;Conta do PayPal&quot; na página Métodos de Pagamento Armazenados, tornando-a mais representativa de sua função. Anteriormente, essa seção era especificamente rotulada como &quot;Conta do PayPal&quot;, o que induzia em erro quando outros métodos de pagamento de conta tokenizáveis eram adicionados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/35622>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37959>
* _AC-11905_: [Problema] Implantação de conteúdo estático - Erro de tipo
   * _Observação de correção_: o sistema agora lida corretamente com arquivos LESS vazios durante a implantação de conteúdo estático, exibindo uma mensagem de erro &quot;MENOS arquivo está vazio&quot;. Anteriormente, um erro de tipo incorreto era exibido ao encontrar um arquivo LESS vazio durante a implantação.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38682>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38683>
* _AC-11911_:
   * _Observação de correção_: limpeza de css jQuery/fileuploader após a migração para a biblioteca de atualização
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribuição de código do GitHub_: biblioteca jQuery/fileUploader removida porque foi migrada para a biblioteca Uppy
* _AC-12002_: [Problema] [Exibição] Remoção de espaço extra na marca de link e script
   * _Observação de correção_: o sistema agora garante que não haja espaços extras nas marcas de link e script, fornecendo um código mais limpo e eficiente. Anteriormente, espaços duplos podiam ser encontrados entre os atributos nas tags link e script.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32920>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32919>
* _AC-12015_:
   * _Observação de correção_: limpeza da pasta ExtJs após a migração para a biblioteca jsTree
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribuição de código do GitHub_: a pasta extJs foi removida, pois a funcionalidade relacionada foi migrada para jsTree
* _AC-12022_:
   * _Observação de correção_: atualizar a dependência do sistema monolog/monolog para a versão principal mais recente
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribuição de código do GitHub_: o sistema foi atualizado para usar a versão principal mais recente da biblioteca &quot;monolog/monolog:^3.x&quot;, garantindo compatibilidade e melhor desempenho. Anteriormente, o sistema usava uma versão desatualizada da biblioteca &quot;monolog/monolog&quot;, que poderia ter levado a possíveis problemas e limitações.
* _AC-12023_:
   * _Observação de correção_: atualize a dependência wikimedia/less.php para a versão principal mais recente
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribuição de código do GitHub_: o sistema foi atualizado para usar a versão principal mais recente 5.x da biblioteca &quot;wikimedia/less.php&quot;, garantindo a compatibilidade e a funcionalidade atualizada. Anteriormente, o sistema usava uma versão desatualizada da biblioteca que poderia ter causado problemas de segurança.
* _AC-12024_:
   * _Corrigir observação_: atualize a dependência da biblioteca jquery/validate para a versão secundária mais recente
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribuição de código do GitHub_: atualize a dependência da biblioteca jquery/validate para a versão secundária mais recente 1.20.0
* _AC-12025_:
   * _Observação de correção_: atualize a dependência do sistema Moment.js para a versão secundária mais recente
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribuição de código do GitHub_: atualize a dependência do sistema Moment.js para a versão secundária mais recente 2.30.1
* _AC-12267_:
   * _Observação de correção_: suporte a novas tentativas de conexão para a sessão Redis e compatível com colinmollenhour/php-redis-session-abstract v2.0.0
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribuição de código do GitHub_: a versão mais recente atualizada de colinmollenhour/php-redis-session-abstract v2.0.0 é compatível com o adobe commerce
* _AC-12268_:
   * _Observação de correção_: atualize as dependências do League/flysystem Composer para a versão mais recente
   * _Contribuição de código do GitHub_: atualize as dependências do 2.x league/flysystem Composer para a versão mais recente 3.x
* _AC-12594_: [Problema] Use a configuração compilada para dados gerados em vez da configuração geral
   * _Observação de correção_: o sistema agora usa a configuração compilada para dados gerados em vez da configuração geral, reduzindo a transferência de rede e a sobrecarga dos dados que dependem de uma determinada versão do código. Essa alteração impede a substituição de cache em instâncias compartilhadas durante a troca de contêiner, resultando em estabilidade aprimorada e tempo de inatividade reduzido. Anteriormente, determinadas classes principais usavam o tipo de configuração compartilhada, o que poderia resultar na substituição de cache ou no tempo de inatividade do aplicativo devido a diferenças nas versões do código em vários servidores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38785>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problema] Remover referências a arquivos de extjs que foram removidos em e1ccdb...
   * _Observação de correção_: o sistema agora remove referências a arquivos de extjs que foram removidos anteriormente, eliminando erros no console do navegador e no arquivo de log do sistema. Anteriormente, essas referências estavam causando erros devido à ausência dos arquivos referenciados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38960>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38951>
* _AC-12715_:
   * _Corrigir observação_: atualizar dependências do laminas composer atualizando para a versão mais recente
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contribuição de código do GitHub_: o sistema agora oferece suporte às versões mais recentes das dependências do laminas Composer:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
lâminas/lâminas-validador
garantir a compatibilidade e a funcionalidade atualizada. Anteriormente, a atualização para as versões mais recentes dessas dependências podia causar problemas de incompatibilidade com versões anteriores e falhas de teste.
* _AC-12778_: [Problema] Limpeza secundária: correção de uso incorreto de sprintf, leva apenas 2 espaços reservados aqui e w...
   * _Observação de correção_: o sistema agora usa corretamente a função sprintf com o número apropriado de espaços reservados, melhorando a limpeza e a consistência do código. Anteriormente, a função sprintf era usada incorretamente com um argumento extra, o que não causava grandes problemas, mas não era o uso correto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39062>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38628>
* _AC-12866_:
   * _Observação De Correção_: Remover Desaprovações- Testes De Integração PhpUnit10
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribuição de código do GitHub_: resolva as descontinuações do PHPUnit
* _AC-12868_:
   * _Observação De Correção_: Remover Desaprovações- Testes De WebApi PhpUnit10
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribuição de código do GitHub_: resolva as descontinuações do PHPUnit
* _AC-12869_: [Problema] corrige classes incorretas sendo referenciadas em módulos Magento.
   * _Observação de correção_: o sistema agora faz referência às classes corretamente nos módulos, garantindo uma operação mais suave e evitando falhas devido a classes não existentes. Isso inclui uma correção de bug nos módulos Indexador e Creditmemo e a implementação da HttpGetActionInterface na classe PrintAction. Anteriormente, referências de classe incorretas levaram a erros e possíveis travamentos do sistema, e certas funcionalidades, como o nome do arquivo para os arquivos de PDF de memorando de crédito e reindexação de estoques, não funcionavam como esperado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39126>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37784>
* _AC-6754_: erro de digitação em um arquivo js.
   * _Observação de correção_: o sistema agora usa corretamente o termo &quot;assinantes&quot; no arquivo do JavaScript, garantindo a funcionalidade adequada dos recursos relacionados. Anteriormente, um erro tipográfico no arquivo JavaScript resultava no uso incorreto do termo &quot;assinantes&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36163>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [Problema] Remover marca `@author` proibida
   * _Observação de correção_: o sistema agora segue os padrões de codificação, removendo a marca `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, a tag `@author` estava presente em alguns módulos, o que era contrário aos padrões de codificação estabelecidos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37253>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problema] Remover marca `@author` proibida de `Magento_Customer` (parte 2)
   * _Observação de correção_: o sistema agora segue o padrão de codificação, removendo a marca `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, a tag `@author` estava presente em alguns módulos, o que era contrário aos padrões de codificação estabelecidos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37250>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: espaço na regra de quebras de sintaxe editorconfig para [{composer,auth}.json]
   * _Observação de correção_: o sistema agora aplica corretamente um recuo de 4 espaços ao compositor e aos arquivos auth.json, seguindo uma correção para um erro de sintaxe no editorconfig. Anteriormente, devido a um espaço na sintaxe editorconfig, esses arquivos eram formatados incorretamente com um recuo de 2 espaços.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37394>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37395>
* _AC-8984_: [Problema] Adiciona mais algumas cores à saída de determinados comandos da cli de instalação
   * _Observação de correção_: o sistema agora adiciona mais cores à saída de determinados comandos de CLI (interface de linha de comando) de instalação, melhorando a legibilidade e a experiência do usuário. Anteriormente, a saída desses comandos era mais difícil de ler devido à falta de diferenciação de cores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/29335>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: a atualização do Magento redefine general/region/state_required quando um novo país com o estado/região obrigatórios é adicionado.
   * _Observação de correção_: o sistema agora só adiciona o país modificado à configuração &#39;general/region/state_required&#39; quando um novo país com estados obrigatórios é adicionado, evitando qualquer interrupção no código personalizado que pressupõe que a região esteja desabilitada. Anteriormente, adicionar um novo país com estados obrigatórios redefinia a configuração &quot;general/region/state_required&quot; para países padrão com um estado obrigatório, possivelmente quebrando a loja.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37796>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: https://github.com/magento/magento2/issues/37841
   * _Observação de correção_: diferença em menos compilação entre php e biblioteca nodejs (grunt) com expressões `calc` complicadas
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contribuição de código do GitHub_: corrija a diferença na menor compilação entre a biblioteca php e nodejs (grunt) após a atualização wikimedia/less.php:^5.x
* _ACP2E-2692_: erro &quot;Tabela ou exibição base não encontrada&quot; ocorre quando a indexação parcial é executada
   * _Observação de correção_: a reindexação parcial agora funciona corretamente com o log de alterações grande no caso de conexão do banco de dados secundário
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: problemas após atualizar MariaDB para 10.5.1 ou superior
   * _Observação de correção_: corrigido o problema quando valores datetime em um banco de dados eram convertidos para 0000-00-00 00:00:00 após a atualização do Mysql
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Tipo Incompatível na Comparação de Dados ao verificar se os dados têm alterações
   * _Observação de correção_: anteriormente, o objeto salvo era chamado sempre sem nenhuma alteração de dados (para qualquer campo de dados numérico, como int/float/double). Ele aciona o sinalizador _hasDataChanges para ser true e chama a função de salvamento. Depois que essa correção for aplicada, a função salvar só chamará se os dados forem alterados. O valor de dados para int/float/double-check com o valor passando para a função e faz a correspondência de tipo strict.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: a importação de [Nuvem] não pode ser usada com a variável de diretório
   * _Observação de correção_: o produto pode ser importado com êxito, independentemente do nome do arquivo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: no ipad mini, o menu e o cabeçalho são carregados como móveis; em vez disso, eles devem ser carregados como desktop.
   * _Observação de correção_: o sistema agora trata dispositivos com uma largura de 768px como desktop, garantindo que o menu e o cabeçalho sejam carregados corretamente. Anteriormente, os dispositivos com uma largura de 768 px eram tratados como móveis, fazendo com que o menu e o cabeçalho fossem carregados em uma visualização móvel.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>

### Framework, GraphQL

* _AC-7976_: [Problema] Introdução ao suporte de tipos escalares personalizados para o esquema do GraphQL
   * _Observação de correção_: o sistema agora oferece suporte a tipos escalares personalizados para esquemas do GraphQL, permitindo que os desenvolvedores definam tipos e implementações escalares personalizados. Esse recurso pode ser particularmente útil para expressar valores que podem exigir validação, como HTML, emails, URLs, datas etc., e para casos mais avançados, como atributos EAV. Anteriormente, o sistema não aceitava o processamento de tipos escalares personalizados no GraphQL.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36877>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL

* _AC-11729_: Magento_GraphQl executa o processamento de cabeçalhos mesmo se o valor do cabeçalho não passar na validação
   * _Observação de correção_: o sistema agora garante que o processamento de cabeçalho seja executado apenas uma vez e somente se o valor do cabeçalho passar na validação, melhorando a segurança e evitando possíveis vulnerabilidades. Anteriormente, o processamento de cabeçalho era executado mesmo se o valor do cabeçalho não passasse na validação, resultando em possíveis vulnerabilidades e comportamento inesperado devido ao processamento duplo dos valores do cabeçalho.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: as opções de Cartão Presente Físico não têm a ordem de classificação correta
   * _Observação de correção_: o sistema agora classifica corretamente as opções de produtos de cartão-presente físico quando consultado via GraphQL, garantindo uma renderização consistente com o tema Luma. Anteriormente, a ordem de classificação estava incorreta de acordo com o tema da Luma, resultando na exibição e na ordenação incorretas de opções como nome do remetente, nome do destinatário e quantidade.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: o Cache do Resolvedor do [GraphQL] é Invalidado ao Criar/Editar/Mover/Excluir uma Atualização de Preparo
   * _Observação de correção_: o sistema agora garante que o cache de resolvedor não seja invalidado ao criar, editar, mover ou excluir uma atualização de preparo, mas somente quando a atualização de preparo for aplicada à entidade. Anteriormente, o cache de resolvedor era invalidado prematuramente, mesmo antes da atualização de preparo ser aplicada, o que resultava em invalidações desnecessárias do cache.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: cache rápido não limpo para atualização de preparo de conteúdo
   * _Observação de correção_: agora o GraphQL com o cache de resposta de conteúdo do PageBuilder é invalidado quando as entidades relacionadas ao conteúdo do PageBuilder são atualizadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Desabilitando Navegação em Camadas - Não remove a agregação do Graphql
   * _Observação de correção_: o problema foi corrigido após a aplicação da verificação ao solicitar uma pesquisa de produto com agregações de categoria por meio de uma consulta GraphQL quando a configuração de administrador de &quot;Catálogo > Navegação em camadas > Exibir filtro de categoria&quot;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: a chamada Produtos GraphQL contendo o filtro de preço {from:&quot;0&quot;} não retorna nenhum resultado
   * _Observação de correção_: anteriormente, a pesquisa de produtos graphql com filtro para preços zero não retornava nenhum resultado devido a uma exceção lançada. Agora, a pesquisa retorna os resultados conforme esperado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-3128_: [Nuvem] chamada do GraphQL interrompida para getPurchaseOrder com cotação de nó
   * _Observação de correção_: a chamada GraphQL da Ordem de Compra poderá executar a tarefa sem encontrar erros internos no servidor.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Nuvem] Produtos Configuráveis não mostrados no Site de Produção se o Produto não estiver habilitado em &quot;Todos os Modos de Exibição de Loja&quot;
   * _Observação de correção_: o sistema agora exibe corretamente os produtos configuráveis no site, mesmo que o produto não esteja habilitado em &quot;Todas as Exibições da Loja&quot;, mas esteja habilitado em escopos específicos de exibição da loja.
Anteriormente, se um produto era desativado em &quot;Todas as exibições da loja&quot; e ativado apenas em escopos de exibição da loja específicos, os atributos do produto não eram exibidos corretamente na resposta do GraphQL, fazendo com que o produto não fosse exibido corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: graphql de produtos da [Cloud] apresentando erro quando o mesmo produto simples foi atribuído a vários produtos configuráveis
   * _Observação de correção_: anteriormente, com produtos configuráveis separados com o mesmo produto simples, o grapQL retornava um erro. Depois que essa correção se aplica, diferentes produtos configuráveis com o mesmo produto simples, o grapQL retorna o resultado sem erros.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3253_: a paginação itemsV2 do carrinho do GraphQL não está funcionando corretamente
   * _Observação de correção_: o problema foi corrigido ao passar o valor correto para o argumento da página atual na consulta de coleção. Anteriormente, o valor errado era passado para definir a página atual, causando o problema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/8459b17d>

### GraphQL, Inventário / MSI

* _ACP2E-2607_: a mutação MergeCart gera uma exceção quando os carrinhos de origem e de destino têm os mesmos itens de pacote
   * _Nota de correção_: &#39;-
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventário / MSI, Desempenho

* _ACP2E-1716_: site inativo após atualização
   * _Observação de correção_: o desempenho da busca de pacotes de produtos por meio do GraphQl foi aprimorado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, Desempenho

* _AC-9569_: [GraphQL Resolver] Os Dados Do Customer Resolver Não São Invalidados Na Importação
   * _Observação de correção_: o cache do resolvedor de clientes do GraphQL agora é invalidado conforme esperado quando um cliente é editado ou excluído por meio de importações. Anteriormente, o cache não era invalidado e os dados do cliente podiam ser editados ou excluídos durante a importação.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Pesquisar

* _ACP2E-2809_: a classificação da lista de produtos GraphQL por vários parâmetros não funciona
   * _Observação de correção_: a classificação de produto por vários campos no GraphQl agora funciona conforme descrito na documentação
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c971859e>

### Importar/exportar

* _AC-12172_: problema na importação do produto quando fornecido com o tipo de opções personalizadas: arquivo (o Produto Criado não contém o preço para a opção personalizada e mostra apenas a primeira extensão de tipo de arquivo fornecida)
   * _Observação de correção_: o sistema agora importa corretamente os dados do produto com opções personalizadas do tipo &#39;arquivo&#39;, garantindo que todas as extensões de arquivo fornecidas sejam exibidas e que o preço da opção personalizada seja incluído. Anteriormente, durante a importação do produto, se uma opção personalizada do tipo &quot;arquivo&quot; fosse fornecida com mais de uma extensão de arquivo, somente a primeira extensão era exibida e o preço da opção personalizada não era exibido.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38805>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: tempo de execução incorreto para a operação de importação na grade do Histórico de Importação
   * _Observação de correção_: o tempo de execução do relatório de importação é mostrado corretamente independentemente da localidade do administrador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Clientes duplicados sendo criados com o mesmo endereço de email usando a importação
   * _Observação de correção_: importar o cliente enquanto o Compartilhamento de Conta estiver definido como Global, o cliente importado que existe no sistema será atualizado.
O cliente importado anteriormente foi duplicado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Adicionar/Atualizar Importação em Produtos Duplicando Opções Personalizáveis
   * _Observação de correção_: o problema foi resolvido com a atribuição da loja correta às opções de produto durante importações de CSV de opções de produto.
Anteriormente, o era atribuído ao armazenamento de administração em vez do respectivo armazenamento.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: Data &quot;created_at&quot; do cliente não convertida para fuso horário de armazenamento na exportação
   * _Observação de correção_: um valor de data &#39;created_at&#39; da coluna é convertido no formato de data apropriado com base no fuso horário do armazenamento na seção CSV de exportação de cliente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Nuvem] Obtendo erro ao verificar os dados nos dados de importação usando CSV
   * _Observação de correção_: não há erros ao verificar os dados durante a importação de CSV. Anteriormente, a mensagem de erro exibida era: &quot;Não é possível encontrar um cliente que corresponda a esse email e código do site na(s) linha(s): 1&quot; ao verificar os dados na seção de importação usando o CSV do administrador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/8459b17d>

### Instalar e administrar

* _ACP2E-2102_: nenhum botão Exportar VCL para Vernish 7 no painel de administração
   * _Observação de correção_: o botão &quot;Exportar VCL para Verniz 7&quot; foi adicionado ao painel de Administração.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventário / MSI

* _AC-11593_: a chave de API do Google google não está funcionando ao adicionar o Mapa com atributos
   * _Observação de correção_: o sistema agora oferece suporte à versão mais recente da API do Google Maps 3.56, permitindo que os usuários adicionem com êxito um bloco de conteúdo do Mapa do menu PageBuilder ao estágio sem encontrar erros. Anteriormente, os usuários não conseguiam adicionar um bloco de conteúdo do Mapa devido a problemas de compatibilidade com a versão da API do Google Maps, resultando em uma mensagem de erro &quot;algo deu errado&quot;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_: [Nuvem] Problema Crítico com Listagem de Produtos com Espaços Vazios
   * _Observação de correção_: o sistema agora exibe corretamente as listas de produtos sem espaços vazios quando os produtos estão definidos como &#39;esgotados&#39;, garantindo uma exibição consistente e precisa dos produtos disponíveis. Anteriormente, definir um produto como &quot;Fora de estoque&quot; resultava na exibição de um espaço vazio na lista de produtos, interrompendo o layout e causando confusão aos clientes.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Pedido

* _AC-10828_: tela de visão geral da ordem de back-end: quantidade com backorder não visível no nível de item de ordem
   * _Observação de correção_: o sistema agora exibe o número de itens com backorder na coluna de quantidade na tela de visão geral da ordem de backend. Isso garante que os usuários possam rastrear com precisão o status de todos os itens em um pedido. Anteriormente, a coluna de quantidade mostrava apenas o número de itens encomendados, faturados e entregues, mas não exibia o número de itens com backorder.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38252>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problema] ID de armazenamento incorreta usada no Renderizador de Endereço de Pedido
   * _Observação de correção_: o sistema agora usa corretamente a ID de armazenamento associada a uma ordem ao renderizar o endereço da ordem, garantindo que os endereços sejam formatados corretamente de acordo com sua respectiva ID de armazenamento. Anteriormente, o sistema estava usando incorretamente a ID da loja atual, o que poderia resultar na formatação incorreta do endereço nos casos em que vários emails de pedidos de lojas diferentes precisavam ser enviados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38412>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37932>
* _AC-11798_: [Problema] Preço de envio mostrando diferenças no pdf impresso
   * _Nota de correção_: o sistema agora exibe corretamente os preços de remessa em PDF impressos de acordo com as configurações de imposto, garantindo a consistência entre a página de exibição da fatura da ordem de venda e a fatura impressa. Anteriormente, o preço de envio exibido no PDF impresso estava excluindo impostos, independentemente das configurações de imposto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38608>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _ACP2E-2622_: não é possível salvar alterações no número de telefone nos detalhes do pedido existente
   * _Observação de correção_: agora o usuário pode adicionar o prefixo internacional 00 no campo de telefone do endereço do pedido
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38201>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: Falha ao enviar emails
   * _Observação de correção_: o sistema agora inclui uma opção de configuração async_sending_tries para especificar o número de tentativas de envio de email antes da interrupção, melhorando o tratamento de emails com falha quando o &quot;Envio assíncrono&quot; estiver habilitado. Anteriormente, se ocorresse uma falha no envio de um email, o sistema tentaria continuamente reenviá-lo, resultando em um loop infinito de mensagens de erro no log do sistema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: Status do Pedido da [Nuvem] alterado para concluído quando o reembolso parcial de um pedido parcialmente enviado
   * _Observação de correção_: ao emitir um memorando de crédito, o status do pedido não será mais alterado para &quot;concluído&quot; se houver itens que ainda não foram remetidos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] Não Pode Desabilitar o Envio de Emails da Interface do Administrador, como mostra o Dev Docs
   * _Observação de correção_: o sistema agora impede corretamente que emails de vendas sejam enviados quando a comunicação por email está desabilitada. Esses emails não serão mais enviados quando a comunicação por email for reativada. Anteriormente, os emails de vendas iniciados enquanto a comunicação por email estava desativada ainda eram enviados assim que a comunicação por email era reativada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Pedido fechado sem reembolso total
   * _Observação de correção_: o sistema agora mantém corretamente o status do pedido como &#39;Processando&#39; e o status da fatura como &#39;Pendente&#39; quando um pedido com um pagamento não capturado tem uma remessa criada. Isso garante que os pedidos só sejam marcados como &quot;Fechados&quot; depois de serem totalmente reembolsados. Anteriormente, a criação de uma entrega para uma ordem com uma fatura pendente alterava incorretamente o status da ordem para &#39;Fechado&#39;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Ordem, Devoluções

* _ACP2E-2982_: o reembolso de pedido resulta em memorando de crédito duplicado
   * _Observação de correção_: emitir o reembolso pela API REST quando duas solicitações idênticas forem executadas simultaneamente não criará mais Avisos de Crédito duplicados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Pedido, Imposto

* _ACP2E-3003_: [CLOUD] base_row_total incorreto na API de ordem RESTFUL ao habilitar transações transfronteiriças e aplicar descontos de cupom
   * _Observação de correção_: agora o base_row_total correto é retornado da API de ordem RESTFUL quando a transação transfronteiriça está habilitada e o desconto do cupom é aplicado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### Outras ferramentas de desenvolvedor

* _AC-10658_: [Problema] Corrigir erro de sintaxe de HTML em visual.phtml
   * _Observação de correção_: o sistema agora fecha corretamente a marca de início no arquivo visual.phtml, garantindo a sintaxe de HTML adequada. Anteriormente, a tag de início não era fechada corretamente, causando um erro de sintaxe de HTML.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38247>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problema] alterado para &quot;ativo&quot; no comando bin/magento maintenance:status
   * _Observação de correção_: o sistema agora fornece mensagens de status mais precisas para o comando de modo de manutenção, alterando o status de &quot;ativo&quot; para &quot;habilitado&quot; e de &quot;não ativo&quot; para &quot;desabilitado&quot;. Anteriormente, a mensagem de status para o comando de modo de manutenção era exibida como &quot;ativo&quot; ou &quot;não ativo&quot;, o que poderia causar confusão.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38486>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: navegar na árvore de categorias leva a erros no Redis: &quot;A sessão do Redis excedeu as conexões simultâneas&quot;
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38851>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0611e750>

### Pagamentos

* _ACP2E-2841_: o fluxo de pagamento cria uma nova transação sempre que clicamos no botão Buscar na tela exibir transação
   * _Observação de correção_: o sistema agora busca corretamente as informações da transação sem criar uma nova transação de pagamento sempre que o botão de busca é clicado na tela de exibição da transação. Anteriormente, clicar no botão Buscar criaria incorretamente uma nova transação de pagamento para um pedido que já tinha sido pago.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: a mensagem do Paylater não é exibida no PDP para a conta de comerciante do paypal canadense
   * _Nota de correção_: o sistema agora exibe corretamente a mensagem do PayLater para contas de comerciante do PayPal do Canadá na Página de detalhes do produto (PDP) quando o país do comprador pode ser determinado a partir do endereço de cobrança da conta ou da remessa. Anteriormente, a mensagem do PayLater não era exibida devido a um parâmetro ausente, resultando em um erro no console do navegador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Desempenho

* _AC-12000_: [Problema] Limpeza de código e adição de novo bloco de cabeçalho crítico e movimentação de css críticos antes dos ativos
   * _Observação de correção_: o sistema agora inclui um novo bloco de cabeçalho crítico e move CSS crítico antes dos ativos, permitindo mais personalização e otimização de desempenho no front-end. Anteriormente, o CSS crítico não era posicionado antes dos ativos, limitando as oportunidades de personalização e otimização.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38748>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: a compilação de tema é interrompida quando o host mysql contém informações de porta
   * _Observação de correção_: o sistema agora lida corretamente com a configuração de host MySQL, que inclui informações de porta, garantindo uma compilação bem-sucedida do tema. Anteriormente, a compilação de temas falharia se a configuração do host MySQL na conexão de banco de dados incluísse informações de porta.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38799>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38842>
* _ACP2E-2494_: problema de desempenho ao carregar atributos do produto nas regras do carrinho
   * _Observação de correção_: desempenho de consulta aprimorado para regras de vendas - de cerca de 150 ms a ms de dígito único.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: desempenho de indexação parcial de preço
   * _Observação de correção_: o desempenho de indexação parcial de preço foi aprimorado com a otimização de algumas consultas de exclusão usadas no processo de indexação.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: a ordem é rejeitada na configuração de várias lojas ao usar o processamento assíncrono de pedidos + Termos e Condições
   * _Observação de correção_: os pedidos feitos em sites não padrão com os termos e condições habilitados agora são processados.
Antes de serem automaticamente rejeitados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: a chamada à API Rest da ordem está demorando muito para ser executada
   * _Observação de correção_: o sistema agora executa a chamada à API Rest do pedido em um período de tempo razoável, melhorando o desempenho ao buscar um grande número de pedidos. Anteriormente, a chamada da API Order Rest demorava muito para ser executada, causando atrasos ao recuperar um grande número de pedidos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/001e5188>

### Produto

* _AC-10535_: caracteres especiais no nome de produto associado configurável estão sendo convertidos em Entidades HTML.
   * _Observação de correção_: o sistema agora retém corretamente caracteres especiais nos nomes de produtos associados ao editar um produto configurável, impedindo que sejam convertidos em entidades HTML. Anteriormente, os caracteres especiais nos nomes de produtos associados eram convertidos em entidades HTML quando o produto configurável era editado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38146>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: a função GetById de ProductRepository não cria a chave de cache correta
   * _Observação de correção_: o sistema agora cria corretamente uma chave de cache na função GetById do ProductRepository, independentemente da ID do armazenamento ser passada como uma cadeia de caracteres ou um inteiro. Isso garante que o produto seja recuperado da memória em chamadas subsequentes, melhorando o desempenho. Anteriormente, o sistema recuperava o produto do banco de dados sempre que a função era chamada, mesmo com os mesmos parâmetros, devido à criação incorreta da chave de cache.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38384>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [Problema] [MFTF] Adicionou AdminClickAddOptionForBundleItemsActionGroup
   * _Observação de correção_: o sistema agora inclui o AdminClickAddOptionForBundleItemsActionGroup, aprimorando a funcionalidade do painel de administração. Anteriormente, esse grupo de ação não estava disponível.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/30857>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/30838>
* _AC-5969_: AlertProcessor - Argumento #2 ($storeId) deve ser do tipo int, string fornecida
   * _Observação de correção_: o sistema agora aciona corretamente os emails de alerta do produto, garantindo que o identificador do armazenamento seja do tipo de dados correto. Anteriormente, os emails de alerta do produto não eram enviados devido a uma incompatibilidade de tipo no identificador da loja.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/35602>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* A função addFilterToMap _ACP2E-2944_: [Cloud] não está funcionando para determinadas colunas
   * _Observação de correção_: agora, o módulo personalizado pode ser usado na grade de ordem. Ocorreram erros anteriores ao usar um módulo personalizado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>

### Promoção

* _ACP2E-2602_: atributo do cliente não visível ao criar conta a partir do convite
   * _Observação de correção_: os atributos do cliente estão disponíveis ao criar a conta a partir do convite.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: o código do cupom com Usos por Limite de Cupom não está sendo liberado para pagamento falhou com o cancelamento do pedido
   * _Observação de correção_: o sistema atualiza imediatamente os usos de cupom quando um pedido é criado ou cancelado e adiciona os usos de regras a uma fila para evitar possíveis bloqueios. Isso garante que um código de cupom com um limite &quot;Usos por cupom&quot; seja liberado e possa ser reutilizado se um pedido for cancelado devido a uma falha no pagamento. Anteriormente, o sistema não liberava o código do cupom para reutilização nesses casos, resultando em uma mensagem de erro informando que o código do cupom não era válido.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Cloud] O Indexador de Produto de Regra de Catálogo de Reindexação lança SQLSTATE[HY000]: Erro geral: o servidor MySQL 2006 desapareceu.
   * _Observação de correção_: o sistema agora manipula corretamente o valor &quot;batchCount&quot; personalizado no di.xml para &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, evitando erros de SQL, como &quot;Erro geral: 2006 O servidor MySQL desapareceu&quot; durante a reindexação do Indexador de Produto de Regra de Catálogo devido ao tamanho de lote incorreto em catálogos grandes
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>

### SEO

* _AC-11907_: a adição de regravações de URL com ênfase causa carregamento infinito
   * _Observação de correção_: o sistema agora cria e funciona com êxito substituições de URL com acentos, impedindo o carregamento infinito durante o processo de salvamento. Anteriormente, adicionar uma regravação de URL com ênfase causava um problema de carregamento infinito.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38692>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: Reescrita de URL de categoria incorreta de vários armazenamentos para categoria de terceiro nível
   * _Observação de correção_: gerar substituições de URL corretas para filhos com pai com chave de URL com escopo personalizado
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: caracteres de dois bytes (caracteres especiais) no campo Nome do Produto bloqueia a criação do produto no back-end
   * _Observação de correção_: uma nova configuração foi adicionada permitindo que você aplique ou não a transliteração à URL do produto. A configuração está disponível aqui: Lojas > Configuração > Catálogo > Catálogo > Otimização do mecanismo de pesquisa: &quot;Aplicar transliteração para URL do produto&quot;
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>

### Segurança

* _AC-11762_:
   * _Observação de correção_: atualizar o campo de janela OTP 2FA com a descrição correta e o valor padrão após a alteração de BiC
   * _Contribuição de código do GitHub_: comando atualizado para o modo como o período otp_window será inserido a partir de agora bin/magento config:set twofactorauth/google/otp_window VALUE
para a configuração bin/magento:definir valor de twofactorauth/google/leeway
* _AC-11855_: [Problema] Pop-up Paylater de Fonte Ausente CSP
   * _Observação de correção_: o sistema agora permite o carregamento da fonte &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sem violar a diretiva de Política de Segurança de Conteúdo, garantindo a exibição correta do Popup Paylater. Anteriormente, o carregamento da fonte era recusado devido a uma violação da diretiva da Política de segurança de conteúdo, causando problemas de exibição com o pop-up Paylater.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38624>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37401>
* _AC-11937_:
   * _Observação de correção_: atualizar o campo de janela OTP 2FA com a descrição correta e o valor padrão após a alteração de BiC
   * _Contribuição de código do GitHub_: comando atualizado para o modo como o período otp_window será inserido a partir de agora bin/magento config:set twofactorauth/google/otp_window VALUE
para a configuração bin/magento:definir valor de twofactorauth/google/leeway
* _AC-12309_:
   * _Observação de correção_: atualize a documentação do usuário para autenticação de dois fatores (2FA) para alterar o comando otp_window
   * _Contribuição de código do GitHub_: atualize a documentação do usuário para autenticação de dois fatores (2FA) para alterar o comando de configurações OTP_WINDOW conforme: https://jira.corp.adobe.com/browse/AC-11762

### Envio

* _AC-10757_: [Problema] Correção de erro de digitação em tracking.phtml - funções JS renomeadas &quot;currier&quot; para &quot;carrier&quot;
   * _Observação de correção_: o sistema agora usa corretamente o termo &quot;operadora&quot; em vez do erro ortográfico &quot;currier&quot; nas funções do manipulador do JavaScript usadas no modelo de rastreamento de pedidos, garantindo a nomenclatura de função adequada e a clareza do código. Anteriormente, o termo incorreto &quot;currier&quot; era usado, levando a uma potencial confusão e inconsistência na base de código.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/34523>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/33414>
* _AC-11811_:
   * _Observação de correção_: UPS REST &quot;Uma remessa não pode ter KGS/IN, LBS/CM ou OZS/CM como sua unidade de medida&quot;
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _Contribuição de código do GitHub_: as taxas de UPS estão visíveis no check-out e no carrinho.
* _AC-11916_:
   * _Observação de correção_: [QPT] UPS REST &quot;Uma remessa não pode ter KGS/IN, LBS/CM ou OZS/CM como sua unidade de medida&quot;
   * _Contribuição de código do GitHub_: as taxas de UPS estão visíveis no check-out e no carrinho.
* _AC-11938_: UPS REST &quot;Uma remessa não pode ter KGS/IN, LBS/CM ou OZS/CM como sua unidade de medida&quot;
   * _Observação de correção_: certifique-se de que as taxas de no-break estejam visíveis no check-out e no carrinho.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38618>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_:
   * _Observação de correção_: [QPT] UPS REST &quot;Uma remessa não pode ter KGS/IN, LBS/CM ou OZS/CM como sua unidade de medida&quot;
   * _Contribuição de código do GitHub_: as taxas de UPS estão visíveis no check-out e no carrinho.
* _AC-11984_:
   * _Observação de correção_: [QPT] UPS REST &quot;Uma remessa não pode ter KGS/IN, LBS/CM ou OZS/CM como sua unidade de medida&quot;
   * _Contribuição de código do GitHub_: as taxas de UPS estão visíveis no check-out e no carrinho.
* _ACP2E-2738_: Janela de Rastreamento mostrando a Data de Entrega Esperada incorreta
   * _Observação de correção_: exibir a data de entrega correta para a operadora Fedex.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: As Taxas Da Tabela Ainda Estão Sendo Exibidas, Embora A Remessa Gratuita Seja Aplicada
   * _Observação de correção_: o método de envio de Taxa de Tabela agora é exibido mesmo se o Frete gratuito estiver disponível após a aplicação do cupom
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: falha de MFTF test AdminCreatingShippingLabelTest devido a credenciais não adicionadas no ambiente Jenkins
   * _Observação de correção_: correção de teste mftf
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Direcionamento

* _AC-9432_: [Problema] Permitir o uso de intervalos CIDR na lista de permissões de manutenção
   * _Observação de correção_: o sistema agora oferece suporte ao uso de intervalos CIDR na lista de permissões de modo de manutenção, permitindo que um intervalo de endereços IP ignore o modo de manutenção. Anteriormente, o modo de manutenção permitia que somente endereços IP individuais fossem ignorados pelo modo de manutenção.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37943>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/30699>

### Estrutura de teste

* _AC-11491_:
   * _Observação de correção_: [Ignorar] Precisa ser removido do teste de integração novamente
   * _Problema do GitHub_: &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _Contribuição de código do GitHub_: cancele todos os testes de integração que foram ignorados nesta PR - https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_: falha no teste de integração testDbSchemaUpToDate devido ao tipo de coluna JSON
   * _Observação de correção_: o sistema agora reconhece corretamente os tipos de colunas JSON no esquema de banco de dados durante testes de integração, evitando falhas de teste devido a uma incompatibilidade entre o esquema de banco de dados e o esquema declarativo. Anteriormente, o sistema identificava incorretamente os tipos de coluna JSON como LONGTEXT no MariaDB, causando falha nos testes de integração.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ef81f5a2>

### Estrutura da interface

* _AC-12128_: correção de vulnerabilidade de segurança Prototype.js CVE-2020-27511
   * _Observação de correção_: o sistema foi atualizado para resolver a vulnerabilidade de segurança CVE-2020-27511 em Prototype.js 1.7.3, melhorando a segurança geral do sistema. Antes dessa atualização, o sistema era susceptível a uma negação de serviço de expressão regular (ReDOS) por meio da remoção de tags HTML criadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less usa pub/ prefix para sourcemaps
   * _Observação de correção_: o sistema agora gera menos/css sourcemaps sem o prefixo /pub para caminhos ao usar grunt, eliminando a necessidade de uma solução alternativa na configuração do servidor Web. Anteriormente, o uso do prefixo /pub em caminhos de mapas de origem exigia uma configuração específica no servidor Web para funcionar corretamente.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38837>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38840>
* _AC-1306_: conteúdo estático está sendo implantado para módulos desabilitados
   * _Observação de correção_: o sistema agora exclui CSS relacionado a módulos desabilitados dos arquivos finais de saída de CSS, garantindo que estilos desnecessários não sejam carregados. Anteriormente, o CSS relacionado a módulos desativados era incluído nos arquivos finais de saída do CSS, levando ao carregamento de estilos extras e desnecessários.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/24666>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32922>
* _AC-9007_: [Problema] Não carregar contexto de bloco de back-end no front-end
   * _Observação de correção_: o sistema agora garante que o contexto do bloco de back-end não seja carregado no front-end, impedindo a criação de sessões de back-end desnecessárias e possíveis bloqueios de sessão. Anteriormente, o sistema carregava incorretamente o contexto do bloco de back-end no front-end, levando à criação de sessões de back-end e possíveis bloqueios de sessão.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37617>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_: exceção ao verificar um saldo de cartão-presente quando Recaptcha está habilitado
   * _Observação de correção_: os usuários poderão buscar o saldo de um vale-presente na tela de exibição e edição do carrinho. Anteriormente, esses detalhes não eram exibidos quando o reCAPTCHA estava ativado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [ESCLARECIMENTO] Solicitação de Conformidade com o ADA
   * _Observação de correção_: o sistema agora garante a conformidade com o ADA, removendo propriedades CSS sem suporte e substituindo-as por outras com suporte no arquivo print.css. Anteriormente, o uso de propriedades CSS não compatíveis resultava em problemas de compatibilidade do navegador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Nuvem] Código de biblioteca de confusão em effect-drop.js de AC 2.4.4-p8
   * _Observação de correção_: o sistema agora implementa corretamente a biblioteca effect-drop.js, garantindo o funcionamento adequado dos efeitos da interface do usuário do jQuery. Anteriormente, a biblioteca effect-drop.js era substituída por engano pela biblioteca effect-clip.js, causando possíveis problemas com os efeitos da interface do jQuery.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
