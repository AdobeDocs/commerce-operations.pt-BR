---
source-git-commit: 62b6501fc2ba595146bf7f38a7d3352ef02be1a0
workflow-type: tm+mt
source-wordcount: '26051'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.8)

## Destaques

Os 31 destaques a seguir se aplicam à versão 2.4.8 do Magento Open Source.

### Estrutura

* _AC-10721_: atualizar as dependências do league/flysystem Composer para a versão mais recente
   * _Observação de correção_: atualize as dependências do 2.x league/flysystem Composer para a versão mais recente 3.x
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11673_: investigue as versões mais recentes do php-amqplib/php-amqplib
   * _Observação de correção_: atualização da versão mais recente php-amqplib/php-amqplib :^3.x
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11911_: limpeza de css jQuery/fileuploader após a migração para a biblioteca uppy
   * _Observação de correção_: biblioteca jQuery/fileUploader removida porque foi migrada para a biblioteca Uppy
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: adicionar compatibilidade com MySQL 8.4 LTS para Magento CE
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
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
* _AC-12576_: Investigue as falhas de testes de automação com o MySQL 8.4 LTS
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: Adicionar compatibilidade com o MariaDB 11.4 LTS Para EE
   * _Observação de correção_: suporte adicionado ao MariaDB 11.4 com Adobe Systems Comércio e extensões
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12715_: atualize as dependências do compositor laminas atualizando para a versão mais recente
   * _Observação de correção_: o sistema agora oferece suporte às versões mais recentes das dependências do compositor laminas:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
garantir a compatibilidade e as funcionalidade atualizadas. Anteriormente, atualizar para as versões mais recentes dessas dependências poderia causar problemas de incompatibilidade retroativa e teste falhas.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12823_: Investigue a unidade teste falha devido a correção atualização de phpunit durante a atualização do componente
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-13076_: [Parte 1] - Atualize todas as dependências de biblioteca e npm com a versão mais recente disponível
   * _Nota de correção_: o suporte à versão do compositor cabia somente à versão 2.2.x do compositor. Agora, o suporte estendido para a versão 2.4.x também.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/19844aa0>

### Ordem

* _ACP2E-2709_: [O Cliente de solicitação] de recursos sugere que o botão Enviar Comentário sobre detalhes do pedido página é confuso e deve ser alterado para outra coisa
   * _Observação de correção_: para minimizar a confusão, o rótulo do botão &quot;Enviar comentário&quot; foi alterado para &quot;Atualizar&quot; na página de detalhes do pedido.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/488c1034>

### Outro

* _AC-11420_: Defina indexadores como padrão no status Pronto quando uma nova versão do Adobe Commerce for instalada
   * _Observação de correção_: após a Instalação do Magento, o Status do Indexador deve estar no estado *Pronto* por padrão.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: Na instalação de Magento existente ao instalar o indexador de terceiros módulo definir indexadores na atualização por padrão.
   * _Observação de correção_: todos os novos indexadores estão por padrão no modo [Atualizar por Agendamento]. Anteriormente, o modo padrão era [Atualizar ao salvar]. O mesmo acontece com os indexadores personalizados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: as opções do Elasticsearch 7 e 8 devem vir com Deprecated na configuração do administrador.
   * _Observação de correção_: a opção Elasticsearch 8 na Configuração de administração será exibida com o texto Obsoleto para informar aos usuários que o Elasticsearch 8 não é mais uma opção recomendada para uso.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: adicionar nota de texto quando a opção Elasticsearch estiver selecionada na Configuração de Administração
   * _Observação de correção_: uma nota de texto foi adicionada para informar aos usuários administradores do Adobe Commerce que o elasticsearch não é mais suportado pelo Adobe e está obsoleto.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-13448_: fornecer patch de melhoria de desempenho de operações de preço de camada na versão 2.4.8
   * _Observação de correção_: o sistema agora permite atualizações em massa mais eficientes dos preços de camada sem causar problemas de desempenho ou falta de resposta do site ao usar o ponto de extremidade da API REST &quot;/V1/products/tier-price&quot;. Anteriormente, atualizar um grande número de preços usando esse terminal poderia resultar em problemas de desempenho e falta de resposta do site.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_: remover todos os avisos de direitos autorais confidenciais do Adobe dos repositórios Magento Open Source
   * _Observação de correção_: Todos os Adobe Systems avisos confidenciais de direitos autorais foram removidos dos repositórios de código aberto, garantindo que apenas a forma reduzida de Adobe Systems direitos autorais seja usada. Anteriormente, alguns arquivos nos repositórios públicos continham Adobe Systems avisos confidenciais de direitos autorais, o que levou a escalonamentos do comunidade.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/39493>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>

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
* _AC-12901_: Require.js atualização para a versão mais recente 2.3.7 (vulnerabilidade de segurança CVE-2024-38999)
   * _Observação de correção_: Atualização de require.js para a versão mais recente 2.3.7. Na versão anterior, relatamos vulnerabilidade de segurança
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b34c0a75>

## Problemas corrigidos

Corrigimos 497 problemas no Magento Open Source código principal 2.4.8. Um subconjunto de problemas corrigidos incluídos nesta versão é descrito abaixo.

### Apis

* _AC-10042_: API REST /V1/transações retorna erro quando parent_txn_id = txn_id
   * _Observação de correção_: o sistema agora lida corretamente com as transações de conceito pai e filho em que a ID de transação principal é a mesma que a ID da transação, impedindo um loop infinito ao consultar o endpoint de API REST /V1/transactions. Anteriormente, esse cenário resultava em um erro fatal devido ao tempo máximo de execução ser excedido.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Problema no tipo graphql] no 2.4.7
   * _Observação de correção_: o sistema agora manipula corretamente valores inteiros na função GetCustomSelectedOptionAttributes ao executar uma consulta GraphQL, evitando erros relacionados ao tipo. Anteriormente, iniciar uma consulta GraphQL que usava GetCustomSelectedOptionAttributes com um argumento inteiro resultava em um erro de tipo.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38662>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: caracteres especiais na categoria url_key (quando criada pela API REST)
   * _Observação de correção_: anteriormente, no category_url_key, o caractere especial não está presente após a correção; ele está mostrando o caractere especial no category_url_key
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/35577>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2755_: problema com api rest após habilitar dupla 2FA
   * _Observação de correção_: 2FA com opção de segurança Duo agora gera assinatura correta para Rest API
   * _Contribuição_ de código do GitHub: <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_: [REST API]: use o valor padrão na armazenamento visualização não permanece verificado após adicionar configurações para um produto configurável
   * _Observação de correção_: o problema foi corrigido garantindo as entradas corretas do banco de dados para as opções personalizáveis para um armazenamento não padrão. A caixa de seleção das armazenamento personalizadas no seção &quot;Catálogo administrador > > Editar > personalizáveis Opções&quot; foi desmarcada anteriormente devido a entradas imprecisas do banco de dados, mesmo que o título de opção para as armazenamento personalizadas permanecesse o mesmo que o armazenamento padrão.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: A API REST não pode fazer solicitações com barra (/) em SKU ao usar o Oauth1
   * __ Observação de correção: antes da correção, você não era capaz de fazer uma chamada de API bem-sucedida para um produto que tinha &quot;/&quot; em seu SKU. Agora, você pode emitir uma obtenção de solicitação de API bem-sucedida para detalhes do produto, embora seus SKU tenha uma barra avançada.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: A atualização do endereço do cliente falha ao atualizar através da API REST se &quot;validateDefaultAddress&quot; estiver ativado
   * _Observação de correção_: o endpoint da API agora está funcionando como pretendido depois que a problema com a chave de ID ausente da carga da API foi resolvida.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [] Criação de site duplicado grupo preço que o cliente grupo na API de preços de nível.
   * _Observação de correção_: agora a API de parada de preço de nível não permite criar o site Duplicado grupo preço que o cliente grupo.
Anteriormente, era possível criar o site Duplicado grupo preço que o cliente grupo na API de preços de nível que não transmitia validação na Administração durante o salvamento do produto.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: Não é possível adicionar solicitar comentário com status via API REST
   * _Observação de correção_: o problema foi resolvido permitindo a alteração no status de solicitar se for apenas do estado atual. Anteriormente, não estava honrando o Estado solicitar e impedindo mudanças em qualquer status solicitar, mesmo que fosse do mesmo estado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_: A operação assíncrona falha quando o SKU está ausente da carga
   * __ Observação de correção: as operações assíncronas e sincronizar falharam anteriormente devido a erros de salvamento do produto se a sku estiver faltando na carga útil. Após a correção, as operações de api de salvamento de rest assíncronas e sincronizar produto falham com a mensagem de exceção relevante.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Não é possível atualizar os preços básicos usando API REST (O valor de &quot;value_id&quot; em &quot;catalog_product_entity_decimal&quot; não é incrementado corretamente.)
   * _Observação de correção_: Antes dessa correção, quando rest api /rest/default/V1/products/base-prices era chamado, o incremento ID aumentava incorretamente, deixando uma lacuna entre os valores. Após a correção, o incremento id aumenta conforme esperado, incrementalmente. Além disso, o value_id intervalo de campo foi aumentado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: Os itens do pedido não estão visíveis em e-mails de memorando de crédito para a API POST V1/solicitar/:orderId/refund
   * __ Observação de correção: Anteriormente, antes desta correção, quando um cliente cria um memorando de crédito a partir de uma API solicitação notificar send_email, ele não contém a grade de detalhes do produto. Depois dessa correção, o cliente envia uma API de memorando de crédito solicitação e encontrará os detalhes do item de produto aparecendo no email.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_: Os valores padrão não são definidos para atributos de data e hora com produtos RestAPI
   * _Observação de correção_: os valores padrão agora são definidos corretamente para atributos de data e data e hora via RestAPI
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### APIs, carrinho e check-out

* _ACP2E-3343_: Erro 500 Crítico: Magento\Framework\Webapi\Exception Relacionado ao Cabeçalho HTTP Accept
   * _Observação de correção_: após a correção, não há nenhum problema com a especificação do cabeçalho &quot;Aceitar&quot;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>

### Conta

* _AC-10782_: formulário de endereço do cliente permite código aleatório nos campos de nome
   * _Observação de correção_: o sistema agora valida a entrada nos campos Nome e Sobrenome no formulário de endereço do cliente, impedindo o uso de código aleatório. Anteriormente, o sistema permitia o uso de código aleatório nesses campos sem gerar um erro.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38331>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: atualização da senha de administrador.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38352>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: falha no endereço de adição da minha conta ao salvar
   * _Observação de correção_: o sistema salva corretamente os endereços do cliente mesmo quando o campo de região não é exibido, evitando uma falha durante o processo de salvamento. Anteriormente, tentar adicionar ou editar um endereço sem um campo de região exibido resultava em um erro de exceção.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38406>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: Loop de redirecionamento quando URL tiver em maiúscula
   * _Observação de correção_: o sistema converte automaticamente caracteres em letras maiúsculas em URLs para minúsculas, impedindo um loop de redirecionar ao acessar a página inicial. Anteriormente, ter caracteres em maiúsculas no URL de base segura causava um loop de redirecionamento contínuo ao tentar acessar a página inicial.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38538>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: middlename( s) não salvo(s) para contas de convidado
   * _Observação de correção_: o sistema agora salva corretamente o nome do meio de contas de convidado durante o check-out, tornando-o acessível no modelo de email. Anteriormente, o nome do meio não era salvo na tabela de cotação e não estava acessível no template de email para contas de convidado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38593>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Admin: os botões de ações da página flutuam à esquerda em vez da direita
   * _Observação de correção_: o sistema agora alinha corretamente os Botões de ações da página à direita do cabeçalho fixo no painel de administração, melhorando a aparência profissional. Anteriormente, esses botões flutuavam incorretamente no lado esquerdo do cabeçalho fixo.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38701>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: erro dev:di:info no magento 2.4.7
   * _Observação de correção_: o sistema agora exibe corretamente os parâmetros do construtor ao executar o comando dev:di:info, impedindo a ocorrência de erros. Anteriormente, a execução desse comando resultava em um erro devido a uma incompatibilidade de tipos no argumento.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38740>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: caixa de seleção Fazer logon como aceitação do cliente não traduzível
   * _Observação de correção_: o sistema agora permite que os campos &quot;Caixa de seleção Fazer logon como aceitação do cliente&quot; e &quot;Dica de ferramenta da caixa de seleção Fazer logon como cliente&quot; sejam definidos no escopo &quot;Exibição de loja&quot;, permitindo traduções para diferentes exibições de loja. Anteriormente, esses campos eram definidos somente no escopo &quot;Site&quot;, impedindo traduções para exibições de loja individuais.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32329>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32359>
* _AC-6071_: o cliente está conectado, mas mostra o erro 404 no front-end.
   * _Observação de correção_: a página do painel do cliente da vitrine agora é carregada como esperado quando um cliente faz logon. Anteriormente, os clientes podiam fazer logon, mas essa página mostrava um erro 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/35838>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: não é possível Salvar as informações do atributo do Cliente na seção Admin Edit customer;
   * _Observação de correção_: a ID de armazenamento do cliente agora é implementada corretamente por escopo de site para o formulário de edição do cliente administrador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3329_: depois de fazer logon, os produtos adicionados à lista de comparação como usuário convidado não ficam visíveis.
   * _Observação de correção_: os produtos que foram adicionados à comparação de produtos lista antes de fazendo logon como um cliente agora são preservados após fazendo logon dentro
Anteriormente, após fazendo logon, os produtos adicionados ao lista de comparação como convidados usuário não eram visíveis.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Permitir configuração dos países causa problemas nas configurações do endereço do cliente
   * _Observação de correção_: agora selecionar a configuração Permitir países não influencia os países mostrados para fora dos escopo. Anteriormente, a configuração de Permitir países influenciou o atributo de endereço do cliente fora dado escopo
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3501_: VAPT: Empresas Logic Erro - data futura como data de nascimento do cliente
   * _Observação de correção_: a data de nascimento do cliente não pode ser definida mais tarde do que hoje
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d4de4726>

### Conta, APIs, GraphQL

* _ACP2E-3246_: API Do Cliente - Número De Falhas De Logon Não Pode Ser Redefinido Para 0 Após O Logon Bem-Sucedido
   * _Observação de correção_: agora o número da falha é redefinido para zero na tabela de entidades do cliente após o logon bem-sucedido do cliente pelos pontos de extremidade da API.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Conta, interface do administrador, B2B

* _ACP2E-3038_: Usuários administradores restritos nem sempre podem ver catálogos compartilhados personalizados
   * _Observação de correção_: os usuários de administrador restritos agora podem visualização e gerenciar clientes e todos os catálogos compartilhados aos quais os produtos são atribuídos, desde que tenham acesso às armazenamento específicas. Anteriormente, uma administrador restrita usuário com acesso a um determinado armazenamento nem sempre conseguia ver todos os catálogos compartilhados aos quais os produtos foram atribuídos ou poderiam ver clientes que não podiam salvar, levando a inconsistências no sistema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>

### Conta, carrinho e check-out

* _AC-2341_: o atributo de endereço personalizado &quot;selecionar&quot; do cliente não é renderizado para o novo endereço do cliente
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/34950>

### Interface do administrador

* _AC-10705_: [Problema] adicione verificação de permissão para o botão &quot;recarregar dados&quot;
   * _Observação de correção_: o sistema agora inclui uma verificação de permissão para o botão &quot;Recarregar Dados&quot;, garantindo que ele seja exibido e acessível somente a usuários com as permissões apropriadas. Anteriormente, o botão &quot;Recarregar dados&quot; estava visível e clicável para todos os usuários, resultando em uma página &quot;não permitido&quot; quando clicado por usuários sem as permissões necessárias.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38283>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38279>
* _AC-11427_: [Problema] Rótulos inconsistentes para atributos em regras de marketing
   * _Observação de correção_: o sistema agora preenche corretamente os rótulos de forma consistente para as opções de categoria e atributo na regra de preço do carrinho
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/31232>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/31231>
* _AC-11588_: a validação de dados foi bem-sucedida e o botão Importar está presente durante a importação de produtos com comportamento Substituir
   * _Observação de correção_: o sistema agora valida os dados corretamente e oculta o botão &quot;Importar&quot; durante o processo de importação do produto com o comportamento &quot;Substituir&quot;, impedindo qualquer substituição de dados não intencional. Anteriormente, o sistema validava os dados incorretamente e exibia o botão &quot;Importar&quot;, resultando em possíveis inconsistências de dados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Bug] Magento 2.4.7 não permite que fotos de produto com extensão de arquivo de carta maiúscula.
   * _Observação de correção_: o sistema agora aceita o upload de imagens de produto com extensões de arquivo de carta maiúscula, garantindo um processo suave de criação de produto. Anteriormente, os uploads de imagens com extensões de arquivo de carta maiúscula eram recusados, forçando os usuários a alterar a extensão do arquivo para minúsculas.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38831>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: lista suspensa oculta em grades com ação de seleção (por exemplo, Conteúdo > Elementos > Páginas)
   * _Observação de correção_: agora o sistema foi corrigido com todas as listas suspensas semelhantes para todas as grades.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38891>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39371>
* _AC-13131_: [Problema] Aviso de Correção: &quot;filtros&quot; de chave de matriz indefinida
   * _Observação de correção_: o sistema agora lida com cenários em que um novo usuário ainda não interagiu com marcadores, impedindo que um aviso de &quot;filtros&quot; de chave de matriz indefinido seja registrado. Anteriormente, esse aviso era registrado quando um novo usuário não interagia com marcadores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39013>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: arquivo csv de importação de produto com caracteres especiais falha devido a alterações de código no arquivo Validate.php
   * _Observação de correção_: o sistema agora valida e importa corretamente arquivos CSV de produtos que contêm caracteres especiais, permitindo uma transferência de dados bem-sucedida. Anteriormente, tentar importar um arquivo CSV de produto com caracteres especiais resultava em um erro, impedindo o processo de importação.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13850_: Não há asterisco vermelho para o campo de número de telefone obrigatório
   * _Observação de correção_: o asterisco vermelho anterior não era exibido para o número de telefone, mas o número de telefone era obrigatório. O que agora é corrigido, o asterisco vermelho pode ser visto no número de telefone como um arquivo obrigatório.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/c699c206>
* _AC-6975_: [Problema] define o modo do indexador padrão para &#39;programar&#39;
   * _Observação de correção_: todos os novos indexadores estão no **[!UICONTROL Update by Schedule]** modo por padrão.  Anteriormente, o modo padrão era **[!UICONTROL Update on Save]**. Os indexadores existentes não são afetados. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/36419>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: tabelas] [do indexador de lançamentos de problemas na mview cancelar inscrição
   * _Observação de correção_: O sistema agora remove automaticamente tabelas de changelog não usadas quando um índice é alternado de &quot;atualização na programação&quot; para &quot;atualizar ao salvar&quot;, marcando o índice como inválido para garantir que nenhuma entrada seja perdida. Anteriormente, alternar um índice para &quot;atualizar ao salvar&quot; deixaria tabelas de changelog nãoutilizáveis no sistema e marcaria todos os índices alterados como &quot;válidos&quot;.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/29789>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: Não link ao envio quando em pagamentos no check-out em telefones celulares visualização
   * _Observação de correção_: O sistema agora garante que os títulos/links de checkout &quot;Envio&quot; e &quot;Revisão &amp; Pagamentos&quot; estejam sempre visíveis sobre as página em visualização móveis, permitindo que os usuários naveguem facilmente entre as etapas e façam as correções necessárias. Anteriormente, esses títulos/links estavam ocultos na exibição móvel, dificultando para os usuários saber sua etapa atual ou voltar às etapas anteriores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36856>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: cliente Consulta comentários de remessa criados_em de comentários de remessa é retornado em fuso horário +0 não no fuso horário configurado de armazenamento
   * _Observação de correção_: o sistema agora exibe corretamente o campo &#39;created_at&#39; dos comentários de remessa no fuso horário configurado do cliente ao usar a consulta Pedidos do cliente. Anteriormente, o campo &quot;created_at&quot; era exibido no fuso horário +0, independentemente do fuso horário configurado pelo cliente.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/36947>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/37642>
* _AC-9843_: i18n:collect-phrases quebra a integridade das traduções
   * _Observação de correção_: o comando `bin/magento i18n:collect-phrases -o` agora coleta e adiciona corretamente novas frases de arquivos JavaScript e .phtml, garantindo que as traduções sejam refletidas com precisão no arquivo de tradução. Anteriormente, o sistema não conseguia incluir frases de tradução de várias linhas de arquivos JavaScript e frases de arquivos .phtml no arquivo de tradução, resultando em traduções incompletas ou incorretas.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: Apóstrofe na armazenamento visualização nome é substituído por &#39;
   * __ Observação de correção: as armazenamento da grade visualização filtros agora exibem os apóstrofos corretamente
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38395>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: A favicon upload falha na validação .ico arquivos
   * _Observação de correção_: o erro de validação do arquivo foi atualizado para &quot;Arquivo validação falha. Verifique as Configurações de processamento Imagem na configuração da loja&quot;. Anteriormente, era simplesmente &quot;Arquivo validação falhou&quot;.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: Galeria no PageBuilder está mostrando miniatura de imagem antiga em vez de imagem recém-carregada
   * _Observação de_ correção: regenera as visualizações de imagens para imagens excluídas e carregadas novamente com o mesmo nome através mídia galeria em página construtor conteúdo.
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: Salvar produtos ao administrador usuário com diferentes função escopo substitui/exclui informações de produtos relacionados existentes no produto
   * _Observação de correção_: Anteriormente, antes da correção, os produtos relacionados eram redefinidos e ficavam vazios quando os administrador secundários usuário clicavam na botão de salvamento sem alterar no produto relacionado. Após essa correção, o administrador secundário usuário clica na botão salvar e o produto não é redefinido e é salvo com sucesso.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: Não é possível exportar mais de 200 pedidos
   * _Observação de correção_: os limites do servidor para o tamanho solicitação das IDs selecionadas anteriormente enviadas foram negligenciados alterando as solicitação HTTP de GET para POST no solicitar para corrigir o problema. Anteriormente, devido às limitações do servidor para o tamanho solicitação GET, o problema foi encontrado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: O checkout página mensagem de validação incorreta.
   * _Observação de correção_: se algum campo obrigatório estiver vazio, como &quot;endereço&quot;, a validação no lado do servidor não exibirá a mensagem. A validação do lado do cliente garantirá que a notificação de erro do campo obrigatório seja exibida, informando &quot;Este campo é obrigatório&quot;. Anteriormente, a mensagem &quot;o endereço é obrigatório&quot; era exibida se qualquer campo obrigatório ficasse vazio, além da mensagem de validação do lado do cliente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Senha redefinir modelo problema com a administração usuário
   * _Observação de correção_: o problema foi resolvido usando a chave correta, que agora inclui o nome de usuário administrador no modelo de email e conclui o assunto corretamente. Anteriormente, o problema decorreu de uma chave ultrapassada que estava sendo usada.
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
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_: o estado do endereço de entrega não é de atualização automática
   * __ Observação de correção: antes da correção, a endereço de entrega região (ou id de região) não estava em sincronizar com o endereço faturamento informações. Agora, endereço de entrega ID de região e região são devidamente atualizadas quando faturamento informações de endereço são alteradas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: o botão Redefinir não funciona em Adicionar/Editar usuário administrador
   * _Observação de correção_: anteriormente, o botão Redefinir não funcionava na página Adicionar/Editar Usuário Administrador. Agora, no painel Admin, em System -> Permissions -> All Users, o Redefinir botão funcionará corretamente na página de Usuário administrador adicionar/Editar.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: administração da Magento URL roteamento detecção errada e erros de CORS
   * __ Observação de correção: após a correção, se o domínio de administrador personalizado for um subdomínio do domínio principal, o administrador só poderá ser acessado do subdomínio configurado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37663>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_: validação com falha para &quot;Quantidade Máxima Permitida no Carrinho de Compras&quot;
   * _Observação de correção_: anteriormente, quando colocávamos `Maximum Qty Allowed in Shopping Cart` vazio, não havia nenhuma exceção, embora um valor vazio não fosse aceito aqui. Depois que essa correção for aplicada, colocar uma string vazia gerará exceções e não permitirá salvar o produto.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Pagebuilder Visualização interface Problema] Os botões na coluna Page Builder não estão fazendo fila corretamente
   * __ Observação de correção: os botões nas colunas Page Builder agora estão alinhados corretamente. Anteriormente, eles eram desalinhados nas colunas do Page Builder.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: o relatório Produtos Solicitados não está sendo exportado. Erro 404.
   * _Observação de correção_: os relatórios solicitados de produtos CSV e XML agora funcionam conforme o esperado
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: TinyMCE JS Erro no console após a minificação do Js ativar com o modo de produção
   * _Observação de correção_: Anteriormente, a ativação JavaScript minificação no modo de produção dentro do painel administrador fazia com que erros JavaScript relacionados ao TinyMCE 6 aparecessem no console de navegador, afetando o funcionalidade e o experiência do usuário. Agora, esse problema foi resolvido, garantindo que o TinyMCE 6 funcione sem gerar erros, mesmo quando a minificação do JS está ativada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Solicitação de alterações adicionais para concluir totalmente a correção ACP2E-3375
   * _Observação de correção_: &#39;-
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_: habilitação automática de novas permissões de ACL
   * _Observação de correção_: Novo permissões adicionadas aos módulos personalizados não concederão mais acesso automaticamente a todas as funções de usuário existentes, a menos que configuradas explicitamente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_: O Relatório de Usuário do Log de Ações administrativas não mostra detalhes para adminhtml_usuário_delete
   * __ Observação de correção: o adminhtml_usuário_delete agora registra corretamente detalhes importantes. Anteriormente, os logs não eram gerados para exclusões usuário.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: Regra do carrinho com condição de envio não aplicada ao colocar solicitar de administrador
   * _Observação de correção_: anteriormente, se a regra de preço do carrinho tiver um desconto de método de envio com o cupom, ela não poderá ser aplicada por meio da interface do administrador. Depois que essa correção for aplicada, o preço carrinho regra desconto com uma cupom para um método de envio específico será aplicado do Administrador interface com sucesso.
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [O código HEX FRESCO] não está sendo atualizado corretamente no SWATCH
   * _Observação de correção_: o código HEX inserido manualmente pelo usuário no seletor de cores de Amostra Visual não é mais alterado pelo sistema. Anteriormente, alguns códigos HEX tinham pequenos ajustes devido a erros de conversão entre modelos de cores.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Interface do administrador, B2B

* _AC-13628_: logon B2B como cabeçalho do cliente ainda tem marca Magento
   * _Observação de correção_: anteriormente, o cabeçalho da loja mostrava &quot;Você está conectado agora como &lt;customer name> em &lt;store name>&quot; com a marca Magento. Que agora foi corrigida e o cabeçalho é exibido com a marca ADOBE.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/96dec499>

### Interface do administrador, Métodos de pagamento/pagamento, Pedido

* _AC-13520_: Autorização de Transação Não Exibida na Guia Transação Após a Ordem do Botão Inteligente do PayPal
   * _Observação de correção_: o sistema agora exibe corretamente a autorização da transação na guia Transação depois que um pedido é feito usando o Botão Inteligente do PayPal. Anteriormente, a transação de autorização não aparecia na guia Transação após clicar no botão &quot;Autorizar&quot; e nenhuma nova transação do tipo &quot;Autorização&quot; era criada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Interface do administrador, desempenho

* _ACP2E-3169_: após a atualização para 2.4.5-p8, ocorrem erros 500 ao criar ordem do administrador
   * _Observação de correção_: anteriormente, ao habilitar a minificação do HTML, não era possível fazer um pedido do administrador. Agora, com a minificação do HTML ativada, o pedido do administrador pode ser feito com sucesso.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Interface do administrador, Envio

* _ACP2E-2519_: a contagem de código do cupom não é atualizada no   A coluna &quot;Tempo usado&quot; na guia Gerenciar códigos de cupom se um pedido for feito com envio múltiplo.
   * _Observação de correção_: anteriormente, quando um pedido era feito com remessa múltipla, a contagem de código do cupom não era atualizada na coluna &quot;Tempo Usado&quot; da guia Gerenciar Códigos de Cupom. Agora, a contagem correta é exibida no &quot;Tempo usado&quot; refletindo os valores desejados com o envio múltiplo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/4745100c>

### Interface do administrador, preparo e visualização

* _ACP2E-3424_: [Nuvem] Remover o modelo com imagens ausentes faz com que pub/media seja excluído
   * _Observação de correção_: antes dessa correção, se o nome da imagem de visualização não estava presente em um modelo do pagebuilder, a pasta pub/media foi excluída. Após a correção, somente o modelo será excluído e a imagem de pré-visualização, se encontrada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/Relatórios

* _AC-9922_: Erro do Google Analytics CSP https://region1.analytics.google.com
   * _Observação de correção_: o sistema agora permite corretamente conexões com &#39;https://region1.analytics.google.com&#39; quando o Google Analytics está habilitado, impedindo erros de Política de Segurança de Conteúdo (CSP). Anteriormente, ativar o Google Analytics e visualizar o site da UE resultava em erros no console da CSP devido a uma recusa de conexão com &quot;https://region1.analytics.google.com&#39;&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37750>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38991>
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
* _ACP2E-3183_: o monitoramento do navegador NewRelic pelo script inlineJS causa erros de CSP
   * _Observação de correção_: os scripts de monitoramento do navegador NewRelic agora são inseridos pelo aplicativo, em vez do agente APM, para conformidade com a CSP (Política de Segurança de Conteúdo). Anteriormente, os scripts de monitoramento do navegador NewRelic inseridos pelo agente APM não eram compatíveis com o CSP e faziam com que os scripts não fossem executados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: as consultas INSERT para a tabela sales_bestsellers_aggregated_daily tornam-se lentas no projeto com grande volume de ordens de venda
   * _Observação de correção_: anteriormente, o relatório diário agregado de best-sellers demorava muito para ser gerado para um grande volume de pedidos feitos. Agora o relatório é gerado em tempo hábil.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: Relatórios de pedidos mostrando o símbolo de moeda errado
   * _Observação de correção_: o símbolo de moeda para valores solicitar no Relatório de pedido foi retirado incorretamente da moeda/opções/base. Foi corrigido ao usar moeda/opções/padrão para relatórios precisos.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Cálculos incorretos da nuvem] no relatório de uso do cupom
   * _Observação de correção_: o total de vendas na grade de relatório cupom agora é calculado com precisão incorporando tanto o &quot;Valor da Compensação de Impostos de Desconto&quot; quanto o &quot;Valor da Compensação de Impostos sobre o Desconto de Desconto&quot;. Anteriormente, esses valores estavam ausentes no cálculo, levando a discrepâncias entre o total de vendas e as vendas solicitar dados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: problemas com &quot;&lt;project_id>/var/tmp&quot; compartilhado
   * _Observação de correção_: os arquivos temporários do Analytics DataExport usarão o diretório tmp sys, que é mais adequado para acesso e alterações frequentes. Para evitar colisões, caso várias instâncias estejam em execução no mesmo servidor, o caminho tmp foi atualizado para usar a id exclusiva de uma instância
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/Relatórios, B2B

* _ACP2E-2300_: B2B - o mapa de site inclui produtos/categorias não atribuídos ao Catálogo Compartilhado
   * _Observação de correção_: restringir as categorias e os produtos gerados pelo mapa de site às categorias e aos produtos atribuídos somente ao catálogo público compartilhado e/ou à configuração de permissão da categoria de catálogo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Relatórios, Cloud

* _ACP2E-3067_: Magento descarta a maioria dos Novo transações de cron relic #34108
   * _Observação de correção_: o AC está relatórios corretamente as transações relacionadas ao trabalho cron para NewRelic. Anteriormente, algumas transações relacionadas ao trabalho cron seriam mostradas como &quot;OtherTransaction/Action/unknown&quot; em NR
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: Métrica em NR pode ser enganosa para transações em segundo plano - Acompanhamento da ACP2E-3067
   * _Observação de correção_: Fundo transações (cron) usarão Novo nome do aplicativo Relic definido nas configurações
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_: os produtos atribuídos ao catálogo compartilhado não são refletidos no front-end quando o índice parcial é executado
   * _Observação de correção_: os produtos atribuídos ao catálogo compartilhado pela API REST agora ficam visíveis na loja imediatamente após a conclusão da indexação parcial. Anteriormente, os Produtos eram visíveis somente após uma reindexação completa.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3044_: bordas desnecessárias na seção Meus Pedidos
   * _Observação de correção_: anteriormente, era criado um contêiner adicional (referências de ordem) que aplicava classes CSS adicionais, o que fazia com que linhas de borda desnecessárias fossem exibidas abaixo do número de ordem na seção Meus Pedidos, que não está visível agora.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: sales_clean_quotes cron exclui cotações de ordens de compra ainda aprovadas
   * _Corrigir observação_: cotações usadas em ordens de compra agora não serão excluídas pelo trabalho cron sales_clean_quotes
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>

### B2B, Estrutura

* _AC-9607_: Filtrar a Grade da Empresa e, em seguida, Tentar Exportar para Grade em CSV Apresentará Falha e Lançará Exceção
   * _Observação de correção_: o sistema agora permite a exportação bem-sucedida em CSV dos dados da grade Empresas no painel de administração, mesmo quando filtros como &quot;Saldo Pendente&quot; e &quot;Tipo de Empresa&quot; são aplicados. Anteriormente, a aplicação de determinados filtros e a tentativa de exportar os dados da grade resultavam em uma falha e em uma exceção.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>

### Pacote

* _AC-10826_: Contagem de mensagens de erro de validação de pacote de vitrine maior que 1
   * _Observação de correção_: o sistema agora exibe apenas uma mensagem de erro de validação quando o botão &#39;Adicionar ao carrinho&#39; é clicado sem selecionar nenhuma opção de caixa de seleção para um produto agrupado. Anteriormente, o sistema exibia várias mensagens de erro de validação para cada caixa de seleção não selecionada.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3ea26621>

### Carrinho e check-out

* _AC-10660_: A exceção não está sendo tratada corretamente ao adicionar um produto a carrinho na comparação página do produto
   * _Observação de correção_: o sistema agora lida corretamente com exceções ao adicionar um produto à carrinho a partir da página do produto de comparação, exibindo uma mensagem do gerenciador de mensagens no controlador. Anteriormente, uma exceção resultaria em uma página codificada JSON em vez de ser devidamente capturada e tratada.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38200>
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: O GTag não envia preços e totais de transação.
   * _Observação de correção_: o sistema agora envia corretamente os preços e totais da transação para a Google Tag quando o GTag está habilitado, garantindo rastreamento precisas de dados de comércio eletrônico. Anteriormente, a moeda estava sendo enviada incorretamente como parte dos pedidos &quot;todos&quot;, em vez de estar associada aos solicitar individuais.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/37348>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Problema] [Check-out] Diretivas de dependência atualizadas no modelo de email de pagamento com falha
   * _Observação de correção_: o sistema agora omite corretamente o endereço e o método de envio do modelo de email de pagamento com falha para produtos virtuais, garantindo que apenas informações relevantes sejam incluídas no email. Anteriormente, o e-mail de pagamento com falha para produtos virtuais incluía incorretamente o endereço e o método de envio.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32781>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32511>
* _AC-11717_: login do Magento 2 dentro do check-out com cliente existente fornece o erro do console no navegador Firefox
   * _Observação de correção_: o sistema agora permite que os usuários façam logon durante o processo de finalização sem encontrar erros no console do navegador Firefox. Anteriormente, tentar fazer logon como um cliente existente durante a finalização da compra resultaria em um erro de console no Firefox.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38557>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [] Regressão das regras de vendas em 2.4.7
   * _Observação de correção_: o sistema agora valida corretamente as regras de venda, impedindo que o aplicativo de um código de cupom para um carrinho quando a condição do produto não corresponde a nenhum nome de produto. Anteriormente, um regra de vendas poderia ser aplicado e um desconto fornecido sobre o valor do frete mesmo quando a condição do produto não correspondia a nenhum nome de produto.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38671>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [Emissão] de vendas regra cálculo CartFixed: valor de desconto incorreto
   * _Observação de correção_: o sistema agora calcula corretamente o valor do desconto para as regras de venda com carrinho valores fixos, garantindo que descontos precisos sejam aplicados independentemente das alterações nos itens de carrinho. Anteriormente, o valor do desconto podia variar incorretamente quando carrinho itens eram alterados, resultando em descontos significativamente maiores do que o esperado.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38694>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_: [Problema] O carregador bloqueia os métodos de envio depois que o código postal é alterado, as taxas de envio validação regras
   * _Observação de correção_: o sistema agora lida corretamente com métodos de envio personalizados sem taxas de envio validação regras, garantindo que o loader não bloqueie os métodos de envio depois que o postcode é alterado na endereço de entrega durante o check-out. Anteriormente, alterar o código postal no endereço de entrega durante o check-out fazia com que o carregador bloqueasse os métodos de envio e não desaparecesse quando métodos de envio personalizados sem taxas de frete validação regras fossem usadas.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38742>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: O recurso de código de cupom não está funcionando corretamente no check-out página no Magento 2.4.7
   * _Observação de correção_: o sistema agora permite o campo de entrada de código de desconto/cupom no página de checkout para produtos virtuais e para download, permitindo que os usuários apliquem códigos de desconto conforme esperado. Anteriormente, a entrada do código/cupom de desconto era desabilitada e o texto do título botão exibido como &quot;Cancelar cupom&quot;, impedindo que os usuários aplicassem códigos de desconto.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38826>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_: A caixa de seleção Termos e condições não permite HTML na vitrine
   * _Observação de correção_: o sistema agora suporta formatação EM HTML no texto da caixa de seleção &quot;termos e condições&quot; na vitrine, permitindo personalização e leitura aprimoradas. Anteriormente, o texto da caixa de seleção era exibido em formato de texto sem formatação, ignorando as tags HTML usadas.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: O preço do carrinho regra criado para login usuário é aplicado incorretamente para não conectado usuário
   * _Observação de correção_: O sistema agora remove corretamente o preço carrinho regra para usuários conectados quando eles são automaticamente desconectados devido à expiração cookie, garantindo que o desconto não seja aplicado a usuários não conectados. Anteriormente, o carrinho preço regra ainda era aplicado mesmo quando o usuário era desconectado, resultando em um desconto incorreto sendo aplicado a usuários não conectados.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38944>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [Emitir] [feature] Carrinhos de compras grandes otimizando o desempenho impedindo...
   * _Observação de correção_: o sistema agora otimiza o desempenho de carrinhos de compras grandes impedindo duplicado chamadas getActions, aumentando a velocidade e a eficiência das operações de carrinho de compras. Anteriormente, para um carrinho de compras com vários itens, a função getActions era chamada várias vezes, retardando o desempenho do sistema.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/39292>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/39290>
* _AC-8103_: IVA de tradução no renderizador de endereço
   * _Nota de correção_: O sistema agora permite a tradução do texto &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; nos renderizadores de endereço, permitindo que os usuários traduzam esses termos para o idioma específico do armazenamento. Anteriormente, esses termos não eram conversíveis, forçando os usuários a empregar uma solução alternativa.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/36942>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: duplicar pedidos com a mesma ID de aspas ao mesmo tempo com poucas diferenças de tempo
   * _Observação de correção_: correção do problema quando Adobe Systems clientes do Comércio encontravam duplicado pedidos feitos com a mesma Aspas
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: Carrinho de compras persistente limpo durante a etapa de checkout
   * __ Observação de correção: após a correção, selecionar o método de pagamento durante o check-out enquanto não estiver conectado não encerra a sessão persistente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: Reordenar adiciona produto não atribuído ao carrinho
   * _Observação de correção_: anteriormente, para as diferentes lojas, os produtos podem ser reordenados da outra loja. Depois que essa correção for aplicada somente à mesma loja, o mesmo produto de escopo poderá ser reordenado quando o compartilhamento de conta do cliente for habilitado
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: no admin, o &quot;Carrinho de Compras&quot; no lado esquerdo não é atualizado ao selecionar os itens e &quot;Mover para o Carrinho de Compras&quot; no lado direito
   * _Observação de correção_: o &quot;Carrinho de compras&quot; no lado esquerdo é atualizado ao selecionar os itens e a opção &quot;Mover para carrinho de compras&quot; no lado direito no lado administrativo. Anteriormente, esse funcionalidade não funcionava porque os itens do carrinho transformados não ficavam vazios na sessão.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [Regra de Vendas da {Cloud] não aplicada à primeira ordem de Envio Múltiplo
   * _Observação de correção_: após a correção, o desconto é mostrado corretamente para cada solicitar da mesma cota de envio múltiplo.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [solicitações paralelas da produção em nuvem] para adicionar o mesmo produto ao carrinho resultam em dois itens separados na API rest do carrinho
   * _Observação de correção_: o sistema agora processa corretamente várias solicitações paralelas para adicionar o mesmo produto ao carrinho em um único item de linha, impedindo a criação de itens de linha separados para o mesmo SKU. Anteriormente, fazer solicitações paralelas para adicionar o mesmo produto ao carrinho por meio da API REST resultava em vários itens de linha para a mesma SKU.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: Obtendo Não É Possível enviar o cookie. Tamanho de &quot;mage-messages&quot; ao tentar reordenar
   * _Observação de correção_: o processo de reordenação não gerará seus próprios erros agora. Ele dependerá das verificações de item integradas à lista do carrinho.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: o endereço de remessa padrão não está selecionado no check-out
   * _Observação de correção_: o endereço de remessa padrão agora está sendo selecionado no contexto da pesquisa de endereço habilitada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [CLOUD] problema da api graphql addProductsToCart com opção personalizada
   * _Observação de correção_: o GraphQL adiciona à carrinho corretamente o mesmo produto com diferentes opções personalizadas
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Vários endereços adicionados ao conta ao fazer check-out como novo cliente
   * _Observação de correção_: o sistema salva agora um novo endereço do cliente somente uma vez se o solicitar não tiver sido criado, impedindo a criação de múltiplos endereços idênticos na evento de solicitar posicionamento erros. Anteriormente, o sistema salvava um novo endereço sempre que uma tentativa de colocação de pedido era feita, independentemente de o pedido ter sido criado com sucesso ou não.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Reorganizar o solicitar do cliente por meio do formulário de solicitar de hóspedes resulta em uma carrinho vazia
   * _Observação de correção_: Anteriormente, ao reordenar os Pedidos e Devoluções página, o cliente era redirecionado para o fazer logon página. Depois que essa correção é aplicada, o cliente registrado é redirecionado corretamente para o carrinho de Exibir página ao fazer uma reordenação. O fluxo funciona da mesma forma que curtir que clientes convidados.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: Usuário administrador com recursos de função limitados incapazes de visualização carrinhos de compras
   * _Observação de correção_: Anteriormente, a administrador restrita não podia ver as carrinho de compras abandonadas do painel administrador de um site associado. Depois que essa correção é aplicada, a administrador restrita pode ver as carrinho de compras abandonadas do painel de administrador.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_: Cloud [] rapidamente solicitar grande quantidade de desempenho SKU
   * _Observação de correção_: o desempenho do check-out foi melhorado quando os atributos usados em carrinho condições de regras de preço não estão presentes para todos os produtos e quando o recurso MAP (preço mínimo anunciado) é ativado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: itens duplicados no carrinho
   * _Observação de correção_: o sistema processa corretamente várias solicitações paralelas para adicionar o mesmo produto à carrinho em uma única item da linha, impedindo a criação de itens de linha separados para o mesmo SKU. Anteriormente, fazer solicitações paralelas para adicionar o mesmo produto ao carrinho na loja resultava em vários itens de linha para o mesmo SKU.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: a confirmação do email da ordem de check-out é enviada para emails inseridos em Nome/Sobrenome
   * _Observação de correção_: a confirmação do email da ordem de check-out, que foi enviada anteriormente quando um padrão semelhante a um email foi inserido nos campos Nome e Sobrenome, não está mais sendo enviada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: Checkout endereço de entrega formulário é atualizado com endereço errado
   * _Observação de correção_: shippingAddressFromData agora é salvo na armazenamento local por site. Anteriormente, um endereço do site errado podia ser preenchido automaticamente no formulário de endereço de entrega durante o check-out se um código armazenamento fosse usado na URL e o check-out fosse iniciado a partir de vários sites durante a mesma sessão de hóspedes.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_: Produto de cartão de presente | A mesclagem do carrinho está mesclando cartões de presente
   * _Observação de correção_: os produtos giftcard agora mesclados corretamente na carrinho
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_: A persistência do carrinho não está sendo respeitada ao fazer o logout
   * _Observação de correção_: adição de falta de funcionalidade lembrar-me da fazer logon do cliente para o pop-up de autenticação e logon de check-out.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: Os dados das aspas existentes não são atualizados / não são visíveis, em vez disso, crie um novo registro de aspas quando trigger_recollect = 1
   * _Observação de correção_: os itens carrinho de compras do cliente não desaparecem mais como resultado da exclusão de um produto após sua adição ao carrinho de compras.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3618_: [Re-solicitar da NUVEM] botão funcionalidade
   * _Observação de correção_: reorquistar uma solicitar da área de administrador agora adicionará produtos com estoque para aspas, embora existam alguns produtos no solicitar original que não têm mais estoque. Antes da correção, nenhum produto era adicionado à nova cotação se o produto sem estoque estivesse na solicitar original.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_: Search lojas não estão funcionando por código postal
   * _Observação de correção_: a pesquisa de locais de coleta por código postal não funcionava corretamente nas localizações holandesas. Após a correção, a localização da coleta pesquisa fornecerá resultados com base no código postal.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/344fce23>

### Carrinho e check-out, checkout/ Checkout do Página check-out

* _AC-9386_: O [campo Email de BUG] aleatório não é renderizado ou leva muito tempo para aparecer no Checkout Shipping ou Payment página
   * _Observação de correção_: Comércio agora renderiza o **[!UICONTROL Email]** campo nas páginas de envio e pagamento de checkout conforme o esperado. Anteriormente, esse campo estava ausente ou renderizado lentamente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/e1babcfd>

### Carrinho e check-out, ordem

* _ACP2E-3097_: Datepicker para produto com várias Opções personalizáveis com campos de data não funcionando ao colocar solicitar de administrador
   * _Observação de correção_: O sistema agora exibe corretamente o seletor de datas para todos os campos de data ao configurar um produto com várias opções de data personalizáveis no administrador solicitar processo de criação. Anteriormente, o seletor de data só era exibido para o campo de primeira data, deixando os campos restantes sem um seletor de data.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b21e5d91>

### Carrinho e check-out, envio

* _AC-12119_: Compra instantânea &quot;envio mais barato&quot; quebrado para produtos configuráveis
   * _Observação de correção_: o recurso Compra instantânea selecionou incorretamente a opção entrega na loja mais cara para produtos configuráveis em vez do método de Taxa plana mais barato. Essa correção garante que o método de envio correto seja escolhido com base no preço real.&quot;
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38811>
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catálogo

* _AC-10910_: A limpeza de cron_schedule tabela de banco de dados não limpa trabalhos não existentes
   * _Observação de correção_: o sistema agora limpa automaticamente a tabela do banco de dados do cron_schedule, removendo entradas para trabalhos que não existem mais no sistema. Isso garante um desempenho ideal ao manter um número mínimo de linhas na tabela. Anteriormente, as entradas de trabalhos de módulos inativos ou removidos não eram limpas, levando a acúmulos desnecessários de dados na tabela de cron_schedule.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38217>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: O preço de nível não está sendo excluído do produto configurável
   * _Observação de correção_: O sistema agora remove corretamente o preço de nível de um produto quando é convertido de um produto simples para um produto configurável, garantindo uma exibição precisa de preço no frontend. Anteriormente, o preço de nível de um produto configurável não era excluído quando um produto era convertido de um produto simples para um produto configurável, levando a uma incompatibilidade no preço exibido.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38390>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: Categoria descrição WYSIWYG está vazia na exibição de armazenamento não padrão
   * _Observação de correção_: o sistema salva e exibe corretamente a descrição categoria na editor WYSIWYG ao editar um categoria no nível visualização de armazenamento. Anteriormente, o editor WYSIWYG aparecia vazio depois de salvar uma descrição categoria no nível visualização armazenamento.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38622>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38623>
* _AC-11970_: Impossível de reorganizar produtos configuráveis com uma opção personalizada selecionada de caixa de seleção
   * _Observação de correção_: o sistema processa corretamente a reordenação de produtos configuráveis com uma única opção personalizada de caixa de seleção selecionada, permitindo a criação bem-sucedida da cesta de compras. Anteriormente, tentar reorganizar tais produtos resultava em um erro e impedia que itens fossem adicionados ao carrinho de compras.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38736>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_: [Redação] de correção de problemas de item de filtro em navegação em camadas
   * _Observação de correção_: o sistema agora usa corretamente as palavras &quot;item&quot; e &quot;itens&quot; no item do filtro de navegação em camadas, melhorando a clareza e a precisão das descrições do filtro. Anteriormente, essas palavras eram usadas incorretamente, resultando em possível confusão para os usuários que navegavam pelas opções de filtro.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38789>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: o formato de data e hora para a opção personalizada não está funcionando
   * _Observação de correção_: o sistema agora aplica corretamente o formato de data configurado às opções personalizadas de produto do tipo Data, garantindo que o formato de data seja exibido corretamente no front-end. Anteriormente, as alterações na configuração do formato de data não refletiam no front-end para opções personalizadas de produto do tipo Data.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32990>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38925>
* _AC-13068_: opções suspensas ausentes
   * _Observação de correção_: o sistema agora exibe corretamente todos os valores na lista suspensa ao criar um novo atributo com mais de 20 valores. Anteriormente, apenas os primeiros 20 valores ou outros valores de página selecionados eram exibidos, fazendo com que os valores restantes não fossem exibidos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [Problema] Use a ID de armazenamento atual para o cache de tempo de execução de categoria
   * _Observação de correção_: o sistema agora usa corretamente a ID de armazenamento atual para o cache de tempo de execução de categoria, impedindo a substituição de dados quando a emulação é usada ou o código personalizado salva a categoria em armazenamentos diferentes. Anteriormente, o objeto armazenado em tempo de execução podia ter vindo do armazenamento errado, levando à substituição de dados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39310>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update aciona uma exceção
   * _Observação de correção_: o sistema agora aceita corretamente um valor booleano ao usar a opção —no-update no comando sampledata:deploy, evitando quaisquer erros durante a implantação dos dados de amostra. Anteriormente, um erro era gerado ao usar esse comando, pois o sistema esperava incorretamente um valor inteiro.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39344>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [Problema] Corrigir o uso do tipo de cache EAV
   * _Observação de correção_: o sistema agora usa corretamente o tipo de cache EAV em todos os locais relevantes, garantindo um armazenamento em cache de dados consistente e eficiente. Anteriormente, o tipo de cache EAV não era usado de forma consistente, resultando em possíveis ineficiências e inconsistências no armazenamento em cache de dados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32322>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: a Pesquisa avançada de catálogo com dados vazios vai para a página de resultados de pesquisa[2.4.dev branch]
   * _Observação de correção_: o sistema agora retém corretamente os usuários na página Pesquisa avançada e exibe uma mensagem de erro quando eles tentam realizar uma pesquisa sem inserir dados. Anteriormente, executar uma pesquisa vazia redirecionava os usuários para a página Pesquisa avançada de catálogo com uma mensagem solicitando que eles modificassem a pesquisa.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_: Layout [] de produto de edição baseado em attribute_set
   * _Observação de correção_: o sistema agora permite o ajuste do layout do produto com base no conjunto de atributos, fornecendo uma maneira mais prática e eficiente de gerenciar a exibição do produto na loja de front-end. Anteriormente, o layout só podia ser ajustado por SKU ou por tipos de produtos, o que nem sempre foi prático para muitos produtos ou artigos específicos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38790>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36244>
* _AC-6738_: chave exclusiva ausente na tabela eav_attribute_option_value
   * _Observação de correção_: o sistema agora inclui uma chave exclusiva nas colunas &#39;option_id&#39; e &#39;store_id&#39; na tabela &#39;eav_attribute_option_value&#39;, evitando a possibilidade de uma opção ter vários valores para a mesma exibição de armazenamento. Anteriormente, um código com falha podia resultar em uma opção com vários valores para a mesma visualização de loja, causando problemas ao editar produtos ou atributos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/24718>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Classe de] uso de visibilidade para categoria indexador de produtos, em vez de valores codificados
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
* _ACP2E-2630_: problemas que salvam preços avançados em produtos de pacote
   * _Observação de correção_: melhoria de desempenho ao salvar o produto no pacote.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [No local] processo de reindexação é ineficiente ao criar regras de preço do catálogo
   * _Observação de correção_: agora, salvar o preço do catálogo regra não invalidará os indexadores, em vez disso, reindexará apenas produtos afetados
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
   * _Corrigir observação_: atualizar corretamente default_sort_by em uma categoria por meio da solicitação REST / SOAP APi
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Nuvem] O Comerciante está enfrentando problemas com a contagem da lista de desejos
   * _Observação de correção_: adicionar um produto à lista de desejos em uma loja não aumenta mais a contagem de listas de desejos em outras lojas abertas no mesmo navegador. Anteriormente, se ambas as lojas fossem carregadas no mesmo navegador, a contagem de listas de desejos aumentaria na outra loja também.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: a Página de Categoria no front-end mostra slots vazios ao usar o produto de pacote
   * _Observação de_ correção: os produtos de pacotes que não são saláveis no contexto atual armazenamento não são mais indexados.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: [Cloud] Issue of Quote na arquitetura de vários sites
   * _Observação de correção_: anteriormente, a arquitetura de vários sites com diferentes moedas e grupos de clientes não podia aplicar descontos corretamente ao armazenamento. Após essa correção ser implementada, a arquitetura de vários sites com diferentes clientes grupo descontos de preço serão aplicados com sucesso a diferentes lojas.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38506>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 TypeError Sem uso: dataRecord.slice ao editar produtos pacote
   * _Observação de correção_: não há erro de javascript no console de navegador ao excluir a opção de pacote produto.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38505>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [preços incorretos do produto do pacote de nuvem] em solicitar confirmação
   * _Observação de correção_: Correto valor é exibido para opções de pacote em solicitar na Storefront quando a moeda diferente da base usada.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Vídeo do YouTube adicionando bug
   * _Observação de correção_: as imagens e os vídeos do produto são configurados em escopo globais. Dado que você não pode ter um vídeo de produto em um escopo e não em outro, a configuração da chave de API do YouTube foi definida como escopo globais.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [Atualização URL da nuvem] apenas para armazenamento_id=0
   * _Observação de correção_: o &quot;Caminho URL&quot; agora está armazenado com a ID de armazenamento correta. Anteriormente, a ID de armazenamento estava incorreta, resultando em caminhos de URL incorretos restantes no banco de dados ao mover categorias.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all executou e criou um erro.
   * _Observação de correção_: dados incorretos de link de produto em chamadas de API REST não causam mais erros crítico.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Problema de Publicação de conteúdo para dispositivos móveis na nuvem] não pode beliscar a imagem PDP
   * _Observação de correção_: o sistema agora suporta funcionalidade pinch-to-zoom em detalhes do produto página imagens em visualização móveis em Cromo, melhorando o experiência do usuário móvel. Anteriormente, tocar duplo na imagem em visualização móveis no Cromo não ampliava a imagem como esperado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Etiqueta ausente no LayeredNavigation com o nome da opção 0
   * _Observação de correção_: o problema foi resolvido pulando um verificador de valor vazio para o valor do atributo 0. Anteriormente, era considerado vazio e estava causando o problema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: os clientes veem os preços de outros grupos de clientes
   * _Observação de correção_: correção de um problema em que as informações relacionadas ao grupo de clientes eram salvas em um segmento incorreto devido ao valor antigo de X-Magento-Vary na solicitação
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: erro ao excluir opções de pacote
   * _Observação de correção_: o sistema agora exclui corretamente as opções de pacote sem acionar um erro ou fazer com que os página ficassem sem resposta. Anteriormente, tentar excluir pacote opções resultaria em um erro &quot;Página Sem resposta&quot; e evitaria que o produto fosse salvo.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: o Arquivo de Imagem da [Nuvem] não existe no Log de Erros do New Relic
   * _Observação de correção_: o sistema agora sincroniza imagens de espaço reservado personalizadas com o armazenamento local, garantindo que elas sejam renderizadas corretamente ao usar o armazenamento remoto, como o AWS S3. Anteriormente, as imagens personalizadas de espaço reservado não eram renderizadas ao usar o armazenamento remoto, resultando em uma exibição de imagem com falha e logs de erro.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_: o RSS feed de Novos Produtos não é atualizado com novos produtos devido ao cache
   * _Observação de correção_: o feed Rss para Novos produtos agora é atualizado quando um produto é definido como novo e salvo
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_: a resposta GQL da Galeria de Mídia do Produto [Cloud] não é classificada pela posição da imagem
   * _Observação de correção_: o sistema agora classifica corretamente os itens na galeria de mídia por posição na resposta do GraphQL, garantindo uma ordem de exibição precisa. Anteriormente, os itens na galeria de mídia não eram classificados por posição, resultando em uma ordem de exibição incorreta.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37671>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Os itens do sub-Categoria da nuvem] não são exibidos nos widgets de edição no back-end do administrador
   * _Observação de correção_: a árvore de categoria no novo widget página não deve mais ter problemas ao carregar categorias de Nível 5+. Anteriormente, algumas categorias estavam faltando ao carregar a árvore depois das categorias de Nível 5.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3198_: [nuvem] problema de zoom de dois dedos e mover no dispositivo móvel real
   * _Observação de correção_: o sistema agora garante a funcionalidade de zoom de imagem consistente em dispositivos móveis, fornecendo uma experiência do usuário suave e previsível. Anteriormente, o recurso de zoom de imagem era inconsistente e, de repente, diminuiva o zoom depois de um determinado ponto quando visualizado em um dispositivo móvel.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: Quando cancelamos a atribuição de produtos do catálogo compartilhado, os produtos da lista de desejos não estão sendo limpos
   * _Observação de correção_: agora, nenhum item estará visível na lista de desejos se um produto não estiver disponível no catálogo compartilhado. Anteriormente, a lista de desejos página exibia incorretamente uma contagem de &quot;1 item&quot; mesmo quando nenhum item estava realmente disponível na lista de desejos.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: produtos relacionados Selecione tudo/cancele a seleção de todo o problema
   * _Observação de correção_: anteriormente, os botões &quot;Selecionar tudo&quot;/&quot;Cancelar seleção de todos&quot; para produtos relacionados não funcionavam corretamente se um produto fosse selecionado manualmente. Após a correção, esses botões agora funcionam de forma consistente, mesmo após a seleção manual, garantindo que todos os produtos sejam selecionados ou não corretamente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: As [Stock da nuvem] alerta tradução por email para o idioma errado
   * _Observação de correção_: ao enviar Alertas de Stock/Preço para um site com várias armazenamento exibições usando idiomas diferentes, o idioma para as armazenamento visualização onde as alerta foram criadas será usado no email.
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: Categorias desativadas não têm mais seus nomes esmaecedos na árvore de categoria
   * _Observação de correção_: anteriormente, as categorias desativadas não eram esmaeadas na árvore de categoria. Agora, eles são exibidos com um efeito cinza-out.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: O carregamento do formulário de edição de produto configurável causa tempo limite e esgotamento de memória
   * __ Observação de correção: antes da correção, variações configuráveis do produto eram construídas com base em todas as combinações possíveis de opção de atributo. Nos casos em que os atributos tinham muitas opções, isso resultava em uma operação demorada e que consumia recursos. Agora, variações configuráveis de produtos são construídas com base em atributos de produto filho existentes. Isso resulta em muito menos cálculos - portanto, uma melhor utilização dos recursos.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: O Fotorama não carrega vídeo corretamente ao usar Amostras e a opção é pré-selecionada via URL
   * _Observação de correção_: os vídeos de produto agora serão renderizados corretamente nos detalhes do produto configuráveis página, se os URL contiver opções selecionadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: o Widget de carrossel do PageBuilder mostra produtos que não correspondem a condições
   * _Observação de correção_: a lista de produtos usada em widgets agora respeita a condição de categoria
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: Erro de Validação Disparado para Todos os Produtos do Grupo Quando Uma Quantidade É Inválida
   * _Observação de correção_: Agora, o erro de validação é acionado corretamente para todos os produtos no grupo quando um produto tem uma inválido quantidade, o que não estava acontecendo anteriormente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_: [Preço especial na NUVEm] que não aparece no produto configurável
   * _Observação de correção_: após a correção, alterar o valor &quot;Usado na listagem de produtos&quot; para o atributo de preço especial não afetará a exibição do preço especial de produtos configuráveis.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_: as tabelas Temporárias de Indexadores não serão limpas se o processo for encerrado
   * _Observação de correção_: as tabelas temporárias do indexador CatalogRule agora são limpas se o processo do indexador for concluído
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [Unidade principal do QUANS] teste falhas no 2.4.7-p3
   * _Observação de correção_: as notas de versão para esta teste não são necessárias, pois é uma melhoria no teste unidade.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_: problema de desempenho em Stock recuperação de quantidade para produtos agrupados com várias fontes
   * _Observação de correção_: o produto agrupado e o pacote página de edição de produtos são otimizados quando os produtos atribuídos têm um grande número inventário fontes.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_: Refixar https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Observação de correção_: melhor desempenho de administrador categoria página no caso de um grande número de categorias de âncora
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/982b1c42>

### Catálogo, conteúdo

* _ACP2E-3063_: O [cache na nuvem] não está sendo invalidado.
   * __ Observação de correção: anteriormente, ao salvar um página CMS com um layout de design atualizado, ele não refletia adequadamente na parte frontal. Depois que essa correção for aplicada, o layout de design apropriado estará visível no front-end quando alterarmos o layout de design e salvarmos a página do CMS.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Nuvem] Categorias Âncora/Não Âncora Revertidas no Widget de Conteúdo
   * _Observação de correção_: anteriormente, quando selecionávamos Exibir em -> Categorias de âncora, mostrava todas as categorias que não refletiam a relação pai-filho entre a âncora e a não âncora. Depois que essa correção for aplicada, Exibir em -> Categorias de âncora exibirá apenas Categorias de âncora (selecionáveis) e Exibir em -> Categorias não âncora exibirá Categorias não âncora (selecionáveis)
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Categorias que não funcionam com widgets
   * _Observação de correção_: anteriormente, se salvássemos o bloco CMS para categorias de âncora/não âncora diferentes, ele não funcionaria para as categorias secundárias quando ele fosse exibido no front-end. Depois que essa correção for aplicada, o bloco será mostrado no front-end para categorias diferentes.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>

### Catálogo, Estrutura

* _AC-9111_: coleta de get(Shipments|Creditmemos|Invoice)ordem - a coleção não deve ser carregada
   * _Observação de correção_: o sistema agora garante que as coleções de remessas e avisos de crédito não sejam pré-carregadas quando recuperadas de um pedido, permitindo que filtros ou ordens adicionais sejam aplicados a essas coleções. Anteriormente, essas coleções eram carregadas automaticamente, impedindo mais modificações.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37561>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37562>
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
* _ACP2E-3312_: os Preços de Camada retornam valores incorretos nos produtos GraphQL (em comparação com a Loja)
   * _Observação de correção_: após a correção, os preços de camada do produto retornados para solicitações graphql têm o preço por um item.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>

### Catálogo, preços, preparo e visualização

* _ACP2E-2672_: [O ponto de extremidade da API de preço especial da nuvem] retorna erro ao atualizar um grande número de produtos simultaneamente
   * _Observação de correção_: agora, a API de atualização em massa de Preço especial criará uma única campanha para cada intervalo de datas em vez de várias atualizações programadas para cada produto e intervalo de datas. Além disso, oferecerá suporte a solicitações simultâneas de API para um processamento mais rápido de um grande número de SKUs.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/f89a447e>

### Catálogo, produto

* _AC-7050_: a árvore de seleção de categoria no produto de edição não está na mesma ordem definida em Catálogo->Categorias
   * _Observação de correção_: o sistema agora exibe corretamente a árvore de seleção de categoria na seção de edição do produto na mesma ordem definida em Catálogo ->Categorias, facilitando a administração de produtos em catálogos grandes. Anteriormente, a árvore de categorias na seção de edição do produto era exibida na ordem de criação da categoria, independentemente da ordem de exibição definida em Catálogo ->Categorias.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36101>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36104>

### Catálogo, SEO

* _ACP2E-3653_: URL canônico incorreto para a categoria quando a página > 1
   * _Observação de correção_: anteriormente, a URL canônica para conteúdo de várias páginas não funcionava corretamente, exibindo consistentemente a URL base. No entanto, depois que a correção foi implementada, o URL canônico para conteúdo de várias páginas agora exibe corretamente o URL com a ID da página.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

### Catálogo, Pesquisa

* _ACP2E-2757_: os produtos não estão aparecendo na categoria e na pesquisa, mas os links diretos estão funcionando
   * _Observação de correção_: anteriormente, o atributo personalizado Sim/Não com price_* attribute_code não funcionava com indexação. Após essa correção, o atributo personalizado Sim/Não funciona conforme esperado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Nuvem] Erro de pesquisa elástica em determinadas páginas de categoria
   * _Observação de correção_: anteriormente, com o tíquete de configuração mencionado, quando colocamos o preço 0 para vários produtos, isso lançará uma exceção na página de categoria de front-end. Após essa correção aplicada quando vários preços de produto 0 e carregamos a página de categoria no front-end, não haverá nenhuma exceção e a página de categoria será carregada com êxito.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: Erro de Tipo ao criar objeto: Exceção Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor
   * _Observação de correção_: após a correção, uma instância da classe Magento\CatalogSearch\Model\Indexer\Fulltext pode ser criada sem especificar $data.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: Problema de [NUVEM] com Produtos não estão visíveis no Front-end após salvar no Administrador do Magento
   * _Observação de correção_: após a correção, os produtos configuráveis que têm produtos derivados com nomes compridos não serão perdidos na loja.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Nuvem

* _ACP2E-3010_: [Cloud] PHPSESSID está alterando cada Solicitação POST
   * _Observação de correção_: PHPSESSID não é mais regenerado em solicitações POST na área de front-end para um cliente conectado se o cache L2 Redis estiver habilitado e o cliente tiver sido atualizado no back-end
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_: Avisos de Geração de Mapa de Site
   * _Observação de correção_: após a correção, o mapa de site é gerado no diretório tmp do sistema e copiado para o destino final.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d4de4726>

### Conteúdo

* _AC-10539_: [Problema]  com a exibição de preço no widget Visualizado recentemente
   * _Observação de correção_: O sistema agora exibe corretamente o preço de produtos simples sem estoque no widget &quot;Produto visualizado recentemente&quot;, garantindo a consistência em todos os widgets e produtos lista páginas. Anteriormente, o preço de produtos simples não era exibido no widget &quot;Produto visualizado recentemente&quot; devido a uma condição nos modelos de carregamento de preço.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38167>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problema] Correto erro de digitação e gramática no arquivo acl.xsd
   * _Observação de_ correção: o sistema agora corrige um erro de digitação e gramática no arquivo acl.xsd, aumentando a clareza e a precisão da documentação. Anteriormente, o arquivo acl.xsd continha um erro de digitação e gramática incorreta que poderia causar confusão.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38061>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: imagem de banner do Pagebuilder não visível na galeria
   * _Observação de correção_: o sistema agora exibe corretamente as imagens de banner carregadas nas pastas recém-criadas na galeria do Pagebuilder, eliminando erros anteriores do console. Antes dessa correção, as imagens de banner não estavam visíveis na galeria se fossem carregadas em uma nova pasta, causando um erro de console.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;Código de área não definido&quot; após a atualização para 2.4.5-p8
   * _Observação de correção_: o sistema agora conclui com êxito o processo de implantação de conteúdo estático quando o módulo Magento_CSP está habilitado e &quot;dev/js/translate_strategy&quot; está definido como &quot;incorporado&quot;, sem disparar o erro &quot;Código de área não definido&quot;. Anteriormente, sob essas condições, a conteúdo estática implantação processo falhava com um erro de &quot;Código de Área não definido&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38845>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38922>
* _AC-12692_: árvore de categoria de widget não renderizada corretamente
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39008>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: não é possível ver a mensagem &quot;Usando o valor padrão&quot; ao alterar o tema na página de configuração de design
   * _Observação de correção_: o sistema agora inclui uma coluna separada para exibir a mensagem &quot;Usando valor padrão&quot;, dependendo do tema selecionado na página de configuração de design. Isso garante clareza e visibilidade do status do valor padrão. Anteriormente, a mensagem &quot;Usando valor padrão&quot; não era exibida, resultando em confusão sobre o status do tema selecionado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [Problema] Restaura a compatibilidade com versões anteriores dos plug-ins do TinyMCE novamente (depois disso...
   * _Observação de correção_: o sistema agora restaura a compatibilidade com versões anteriores de plug-ins do TinyMCE, permitindo que as funções definidas no plug-in sejam chamadas ao usar o widget de outro local. Anteriormente, devido a uma mudança na versão TinyMCE, os plug-ins não retornavam os widgets como um objeto, resultando em um erro ao tentar chamar determinadas funções na instância do widget.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39262>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39258>
* _AC-9638_: problema de carregamento de arquivo [Problema] no editor do WYSIWYG na página do produto
   * _Observação de correção_: o sistema agora exibe corretamente a árvore de pastas e permite carregamentos de imagens no editor do WYSIWYG na página do produto, mesmo depois de expandir a guia &quot;Imagens e vídeos&quot; primeiro. Anteriormente, expandir a guia &quot;Imagens e vídeos&quot; primeiro resultava na não exibição da árvore de pastas e em uma mensagem de erro ao tentar fazer upload de uma imagem no editor do WYSIWYG.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38026>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [problema de bloco dinâmico no PREM]
   * _Observação de correção_: os Wdigets agora estão sendo renderizados corretamente em blocos dinâmicos.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: [O Cloud] Frontend não está carregando devido a um problema no boletim informativo modelo
   * _Observação de correção_: adicionar blocos via CMS Página seção conteúdo não cliente potencial à exceção
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Exceção de investigação em nuvem] encontrada no log: InvalidArgumentException: A classe não existe no fornecedor/magento/módulo-regra/Model/ConditionFactory.php
   * _Observação de correção_: remover uma condição em produtos PageBuilder conteúdo configurações não faz mais com que uma exceção seja registrada nos arquivos de log. Anteriormente, remover uma condição em produtos PageBuilder conteúdo configurações faria com que uma crítico exceção fosse registrada nos logs, apesar de não causar problemas no frontend.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Alternando para o modo de armazenamento único - conteúdo globais não são mais exibidos
   * __ Observação de correção: o sistema agora sincroniza armazenamento visualização configurações de design com as configurações de design de site ao ativar um modo de armazenamento único, garantindo que conteúdo atualizações estejam visíveis no frontend. Anteriormente, alternar para o modo de armazenamento único evitava que as atualizações de conteúdo fossem refletidas na loja.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: Page Builder substitui imagem ao tentar adicionar link e outras falhas de usabilidade.
   * __ Observação de correção: Agora, clicando em uma imagem, os links em wysiwyg editor no Page Builder elemento de texto carregarão os dados adequados na imagem, link caixa de diálogo de configuração. Além disso, adicionar um link a uma imagem no editor agora funciona corretamente. Anteriormente, a imagem era substituída por um link.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: A galeria de mídia antiga falha ao renderizar imagens quando uma imagem de 0 byte é colocada no diretório
   * _Observação de correção_: o sistema agora lida com imagens de 0 bytes na galeria de mídia sem interromper funcionalidade, permitindo que outras imagens no diretório sejam exibidas e selecionadas como esperado. Anteriormente, a presença de uma imagem de 0 bytes na galeria mídia impediria que todas as imagens no diretório fossem exibidas ou selecionadas.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Erro Page Builder ao editar o Bloco CMS
   * _Observação de correção_: o sistema salva corretamente as alterações feitas na área de administrador usando Page Builder, sem lançar o erro &quot;Page Builder foi renderizado por 5 segundos sem liberar bloqueios&quot;. no console navegador. Anteriormente, esse erro ocorria ao tentar salvar as alterações, impedindo a atualização bem-sucedida de conteúdo.
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] Sem botões de check-out ou editar carrinho na seção carrinho
   * _Observação de correção_: o produto bundle agora é adicionado ao carrinho por meio de widgets sem erros.
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3122_: o [botão de imagem de upload de nuvem] não funciona
   * __ Observação de correção: antes do Imagem de upload botão para banner e controle deslizante do PageBuilder não funcionava como esperado, e agora, ao pressionar, abre o gerenciador de arquivos local para selecionar a imagem desejada para upload.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_: imagecreatetruecolor(): o argumento nº 2 ($height) deve ser maior que 0. Não é possível carregar uma imagem específica
   * _Observação de correção_: resolveu o problema que causava erros no administrador ao carregar imagens com altura 0 pela galeria de mídia e obteve êxito na sincronização de ativos usando o comando sync. Anteriormente, o não podia fazer upload da imagem pela galeria de mídia e o comando sync também falhava quando uma imagem específica estava na galeria.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from em conflito com a API do Google Maps
   * _Corrigir observação_: o Google Maps agora é renderizado corretamente no editor do PageBuilder. Anteriormente, um erro de Javascript impedia que o Google Maps fosse renderizado corretamente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_: [Cloud] - Controle deslizante CMS não reflete as alterações mais recentes
   * _Observação de correção_: o problema foi corrigido, garantindo que a lista de controle deslizante fosse atualizada enquanto o evento de gravação era acionado na tela de edição do slide. Anteriormente, era acionador e causava o problema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Ocorre um erro no página CSM quando blocos CMS são inseridos usando página construtor em determinadas solicitar
   * __ Observação de correção: anteriormente, em algumas versões de PHP e SO (Linux), a renderização de blocos que mencionavam outros blocos de cms por meio do PageBuilder falharia com um &quot;Ocorreu um erro desconhecido. Tente novamente.&quot;. Agora, o conteúdo dos blocos cms é renderizado corretamente dentro de uma conteúdo controlada pelo PageBuilder.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3428_: a modelo do Pagebuilder pré-visualização falha em grandes conteúdo
   * _Observação de correção_: grandes conteúdo levavam a um elemento da tela que transbordava os limites do navegador e retornava valores incorretos, o que quebrava o código de back-end (não pode decodificar corretamente a imagem). Corrigido com a limitação do tamanho da tela ao limite da navegador universal.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: Atualizações de segurança mais recentes com o TinyMCE 7 ausentes fonte tamanho
   * _Observação de correção_: o tamanho da fonte e os seletores da família fonte agora estão disponíveis em WYSIWYG editor. Antes dessa correção, com o TinyMCE 7, elas não estavam disponíveis na interface do editor.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_: tamanho da fonte do editor TinyMCE 7 no administrador em PT e não em PX. Esclareça
   * _Observação de correção_: antes da correção, não era possível especificar o tamanho da fonte em px nas áreas do WYSIWYG. Agora você pode definir o tamanho da fonte em px em vez de pt.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_: o Tipo de Conteúdo do Produto no Page Builder é Recolhido sem as Mensagens Corretas
   * _Observação de correção_: antes da correção, o html de visualização não era gerado corretamente quando não havia produtos no widget. Agora, a resposta vazia é gerada corretamente e o widget Produtos é exibido sem problemas na pré-visualização.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_: [construtor de páginas]Adicionar Listagem de Produtos para bloquear resulta em erros
   * _Observação de correção_: adicionar uma Lista de produtos do pacote ao bloqueio via construtor de páginas não resulta em erros
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/344fce23>

### Cliente/ Clientes

* _AC-12162_: Front-end - A validação da data de nascimento falhou na página de criação do cliente
   * _Observação de correção_: certifique-se de que toda a validação funcione após a dependência do sistema Moment.js de atualização para a versão secundária mais recente
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-8499_: o campo de texto Região não é redefinido quando a lista suspensa do país é alterada
   * _Observação de correção_: o sistema agora redefine o campo de texto da região quando o país é alterado no menu suspenso, garantindo que os valores anteriores não persistam. Anteriormente, alterar o país na lista suspensa não redefinia o campo de região, fazendo com que o último valor salvo fosse preservado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: a exclusão de cliente não limpa todos os dados de sessão do navegador na loja para clientes conectados e excluídos
   * _Observação de correção_: excluir um cliente agora limpa todos os dados de sessão do navegador da loja para clientes conectados e excluídos conforme esperado. O comprador pode continuar comprando e o navegador trata a sessão como uma sessão de convidado. Anteriormente, quando a conta do cliente de um comprador conectado era excluída do Administrador, o navegador do comprador exibia erros do JavaScript.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>

### Estrutura

* _AC-10037_: [Pergunta]Configuração de tipo não utilizado em `app/code/Magento/Translation/etc/di.xml`
   * _Observação de correção_: o sistema agora remove dependências nãoutilizada na configuração, aumentando a eficiência e a limpeza geral do código. Anteriormente, havia dependências não utilizadas na configuração que não estavam contribuindo para nenhuma funcionalidade.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38030>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38064>
* _AC-10654_: V1/customers/senha endpoint question/issue
   * _Observação de correção_: o sistema agora segue as restrições definidas na GUI de gerenciamento ao processar solicitações de alteração de senha por meio da API, evitando possível abuso da função de redefinição de senha. Anteriormente, a API podia processar solicitações de alteração de senha fora das regras definidas na GUI de gerenciamento, possivelmente permitindo um fluxo constante de emails de redefinição se os emails válidos fossem conhecidos.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38238>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_: A configuração de verniz não exclui todos os parâmetros marketing
   * _Observação de correção_: o sistema agora exclui corretamente todos os parâmetros de marketing comuns na configuração varnish, garantindo rastreamento e análise precisos. Anteriormente, determinados parâmetros marketing como gad_source, srsltid e msclkid não eram excluídos, levando a possíveis imprecisões na coleção de dados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38298>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39188>
* _AC-10838_: processo de indexação de erro do processo de índice de pesquisa de catálogo
   * _Observação de correção_: o sistema agora conclui com êxito o comando re-index sem encontrar nenhum erro, independentemente da versão libxml compilada com PHP. Anteriormente, a execução do comando re-index resultava em um erro de processo de índice de pesquisa de catálogo durante o processo de indexação quando o PHP era compilado com determinadas versões de libxml.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38254>
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: adição de created_at, status e grand_total filtros ao query de pedidos do cliente e correção de várias falhas filtros
   * _Observação de correção_: o sistema agora suporta o uso de created_at, status e grand_total filtros nas consultas de pedidos do cliente, e resolveu um problema em que várias filtros não estavam sendo aplicadas corretamente. Anteriormente, o sistema não suportava esses filtros e não aplicava todas as filtros quando mais de uma era usada em uma query.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38392>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: Aleatoriamente inundado de consultas de blocos relacionados / venda adicional /crosssell e indexação de preços
   * _Observação de correção_: o sistema otimiza consultas de blocos relacionados, de venda adicional e de venda cruzada, melhorando o desempenho e impedindo que o site desapareça devido a consultas excessivas. Anteriormente, o sistema poderia se tornar sobrecarregado com consultas desses blocos, causando desacelerações significativas e potencialmente derrubando o site.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/36667>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Exceção: Aviso: tentando acessar o deslocamento da matriz em... -> Calendar.php desde a atualização para o ICU 74.1 (PHP Intl)
   * __ Observação de correção: Comércio não registra mais a seguinte exceção no exception.log sempre que uma consumidor ou comerciante visita a vitrine ou o administrador: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38214>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [problemas] de correção de problemas com os Dados do cliente quando o formulário contém um elemento com nome `method`
   * _Observação de correção_: O sistema agora identifica corretamente o atributo &quot;método&quot; em envios de formulário, mesmo quando um elemento chamado &quot;método&quot; está presente no formulário. Isso garante um processamento preciso dos dados do cliente. Anteriormente, se um elemento de formulário fosse chamado de &quot;método&quot;, interferiria na identificação do atributo &quot;método&quot; nos envios de formulário, levando a possíveis problemas com o manuseio de dados do cliente.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38484>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Correção de Problemas] PHPDocs para \Magento\Framework\Data\Collection::getItemById
   * _Observação de correção_: os PHPDocs do \Magento\Framework\Data\Collection::getItemById foram atualizados para incluir null como um possível tipo de retorno, abordando problemas com ferramentas de análise estática. Anteriormente, o PHPDocs do método não especificava null como um possível tipo de retorno, levando a avisos ou erros em análise estáticos quando o método era usado em declarações condicionais.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38485>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38439>
* _AC-11592_: [Problema] permite apenas preferências válidas durante a compilação de configuração:di:
   * __ Observação de correção: o sistema agora aciona um erro durante o comando de compilação de configuração:di:se uma preferência for criada para uma classe que não existe ou é excluída especificamente, garantindo que apenas preferências válidas sejam permitidas. Anteriormente, esses cenários falhavam silenciosamente, potencialmente renderizando quaisquer plug-ins associados às classes originais inúteis.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38517>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/33161>
* _AC-11651_: Magento tentando modificar o propriedade somente leitura __wakeup método do LoggerProxy
   * _Observação de correção_: o sistema agora permite a modificação de propriedades somente leitura anteriormente no método de __wakeup do LoggerProxy, garantindo uma operação sem forçar os usuários a empregar uma solução alternativa. Anteriormente, uma tentativa de reatribuir o valor de uma propriedade somente leitura no método __wakeup do LoggerProxy causaria problemas.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38526>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_: [Problema] referências AC-2039 AC-1667 de atualização do TinyMCE
   * _Observação de correção_: atualização da versão mais recente do tinymce no composer.json
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38533>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker não funciona em vários threads
   * _Observação de correção_: o sistema agora oferece suporte à bifurcação de processo para indexação MView, evitando erros durante a execução do indexador ao operar em vários threads. Anteriormente, executar o ChangelogBatchWalker em vários threads cliente potencial à exclusão de tabelas usadas por outros threads, causando um erro durante a execução do indexador.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38246>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Problema] Renomear variável nomeada incorretamente
   * _Observação de correção_: o sistema agora nomeia corretamente a variável que contém a quantidade de dinheiro que ainda pode ser reembolsado, evitando confusão durante a depuração. Anteriormente, esse variável era nomeado incorretamente como totalRefund, o que poderia cliente potencial a mal-entendidos para os desenvolvedores.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38609>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/36205>
* _AC-11809_: [Atributos] personalizados de envio de problemas para link atuais via XML
   * _Observação de correção_: o sistema agora permite que atributos personalizados sejam transmitidos ao link atual via XML, garantindo que esses atributos sejam exibidos corretamente mesmo quando o link for o página atual. Anteriormente, os atributos personalizados não eram exibidos para o página atual link devido ao método getAttributesHtml() não estar sendo usado para o link atual.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38500>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/30070>
* _AC-11819_: O cache FPC incorporado foi quebrado no 2.4.7 para algumas configurações
   * _Observação de correção_: o sistema agora armazena em cache as páginas corretamente quando o parâmetro de MAGE_RUN_CODE é definido, garantindo o desempenho ideal. Anteriormente, as páginas não eram armazenadas em cache sob essas condições, levando a possíveis problemas de desempenho.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38626>
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [] exceção de correção de problema que lida com inconsistência entre os modos de desenvolvedor e produção
   * __ Observação de correção: o sistema agora lida consistentemente com exceções entre os modos de desenvolvedor e produção, impedindo o redirecionamento inesperado para o fazer logon página quando uma exceção é lançada. Anteriormente, uma inconsistência no tratamento de exceção poderia causar uma redirecionar ao fazer logon página no modo de produção em vez de exibir a mensagem de exceção.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38639>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: Substituir a tradução &quot;PayPal Conta&quot; em token_lista.phtml
   * _Observação de correção_: o sistema agora rotula a seção por métodos de pagamento conta tokenizáveis como &quot;Conta&quot; em vez de &quot;conta PayPal&quot; na página de Métodos de pagamento armazenados, tornando-a mais representativa de sua função. Anteriormente, esta seção era identificada especificamente como &quot;conta PayPal&quot;, o que era equivocado quando outros métodos de pagamento conta tokenizáveis eram adicionados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/35622>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37959>
* _AC-11874_: a compatibilidade com versões anteriores foi perdida na classe Magento\Catalog\Model\ProductRepository
   * _Observação de correção_: a classe ProductRepository agora mantém a compatibilidade com versões anteriores restaurando a classe Auxiliar de Inicialização como o segundo parâmetro, garantindo que os módulos estendidos dessa classe funcionem conforme esperado. Anteriormente, a remoção do Auxiliar de inicialização do construtor na classe ProductRepository resultava em uma perda de compatibilidade com versões anteriores, forçando os usuários a empregar uma solução alternativa.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [Problema] Implantação de conteúdo estático - Erro de tipo
   * _Observação de correção_: o sistema agora lida corretamente com arquivos LESS vazios durante a implantação de conteúdo estático, exibindo uma mensagem de erro &quot;MENOS arquivo está vazio&quot;. Anteriormente, um erro de tipo incorreto era lançado ao encontrar um arquivo LESS vazio durante implantação.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38682>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38683>
* _AC-12002_: [Problema] [Exibição] Remoção de espaço extra na marca de link e script
   * _Observação de correção_: o sistema agora garante que não haja espaços extras nas marcas de link e script, fornecendo um código mais limpo e eficiente. Anteriormente, espaços duplos podiam ser encontrados entre os atributos nas tags link e script.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32920>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32919>
* _AC-12127_: [Problema] evite um loop infinito de configuração incorreta
   * _Observação de correção_: o sistema agora evita um loop infinito, impedindo o mapeamento autorreferencial em configurações de tipo virtual. Isso garante que o aplicativo não fique preso em um loop infinito ao tentar cancelar a referência de um nó autorreferencial. Anteriormente, se uma configuração de tipo virtual fosse autorreferencial, ela faria com que o aplicativo girasse indefinidamente.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38822>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: Gerenciador de objetos não usado para Magento\Csp\Model\Mode\Data\ModeConfigured
   * _Observação de correção_: o sistema agora usa corretamente o Gerenciador de objetos ao criar o objeto ModeConfigured, permitindo que plug-ins sejam usados nesse objeto. Anteriormente, o Gerenciador de objetos não estava sendo usado, impedindo que plug-ins fossem aplicados ao objeto ModeConfigured.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38875>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: comentário impreciso sobre bloco de documentos em alertas de preço e estoque de produtos
   * _Observação de correção_: o comentário de bloco do documento para o método deleteCustomer no Estoque de Produtos e nos Alertas de Preço foi corrigido para refletir com precisão que o método exclui todos os alertas de produto ou preço de estoque associados a um determinado cliente e site, não o cliente do site. Anteriormente, o comentário afirmava incorretamente que o método era excluir um cliente do site.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38939>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39001>
* _AC-12594_: [Problema] Use a configuração compilada para dados gerados em vez da configuração geral
   * _Observação de correção_: o sistema agora usa a configuração compilada para dados gerados em vez da configuração geral, reduzindo a transferência de rede e a sobrecarga dos dados que dependem de uma determinada versão do código. Essa alteração impede a substituição de cache em instâncias compartilhadas durante a troca de contêiner, resultando em estabilidade aprimorada e tempo de inatividade reduzido. Anteriormente, determinadas classes principais usavam o tipo de configuração compartilhada, o que poderia resultar na substituição de cache ou no tempo de inatividade do aplicativo devido a diferenças nas versões do código em vários servidores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38785>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problema] Remover referências a arquivos de extjs que foram removidos em e1ccdb...
   * _Observação de correção_: o sistema agora remove referências a arquivos de extjs que foram removidos anteriormente, eliminando erros no console do navegador e no arquivo de log do sistema. Anteriormente, essas referências estavam causando erros devido à ausência dos arquivos referenciados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38960>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [Problema] Limpeza secundária: correção de uso incorreto de sprintf, leva apenas 2 espaços reservados aqui e w...
   * _Observação de correção_: o sistema agora usa corretamente a função sprintf com o número apropriado de espaços reservados, melhorando a limpeza e a consistência do código. Anteriormente, a função sprintf era usada incorretamente com um argumento extra, o que não causava grandes problemas, mas não era o uso correto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39062>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: PHP 8.2.15 removeu extensão FTP
   * _Observação de correção_: o sistema agora inclui a extensão FTP como uma dependência no arquivo composer.json, garantindo a configuração bem-sucedida das importações de CSV via FTP. Anteriormente, um erro era gerado ao tentar configurar importações de CSV via FTP porque a extensão FTP estava ausente no pacote PHP.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39083>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_: [Problema] corrige classes incorretas sendo referenciadas em módulos Magento.
   * _Observação de correção_: o sistema agora faz referência às classes corretamente nos módulos, garantindo uma operação mais suave e evitando falhas devido a classes não existentes. Isso inclui uma correção de bug nos módulos Indexador e Creditmemo e a implementação da HttpGetActionInterface na classe PrintAction. Anteriormente, referências de classe incorretas resultavam em erros e possíveis falhas no sistema, e certas funcionalidades, como o nome do arquivo para arquivos PDF de memorando de crédito e reindexação de estoques, não funcionavam como esperado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39126>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: capacidade de definir Área para comando CLI dev:di:info
   * _Observação de correção_: o sistema agora permite que os desenvolvedores definam uma área para o comando CLI dev:di:info, aprimorando o processo de desenvolvimento e depuração. Anteriormente, esse comando só podia exibir informações da área GLOBAL.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38758>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [Problema] adicione a propriedade isMultipleFiles ao modelo de elemento de formulário de imagem
   * _Corrigir observação_: essa correção impede que o botão &quot;Procurar para localizar ou arrastar imagem aqui&quot; desapareça quando uma imagem é adicionada em um elemento de formulário de imagem de vários arquivos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39219>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36325>
* _AC-13279_: [Problema] Remova todos os parâmetros de obtenção de marketing para minimizar o cache
   * _Observação de correção_: o sistema agora remove todos os parâmetros de obtenção de marketing para otimizar a utilização do cache, espelhando a lógica usada quando o verniz está em uso. Anteriormente, esses parâmetros podiam levar ao aumento excessivo do cache e à redução do desempenho.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39266>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [Problema] [PHPDOC] Corrigir phpdoc incorreto Magento\Directory\Model\AllowedCountries::getAllowedChannels()
   * _Observação de correção_: o PHPDoc para o método AllowedChannels:getAllowedChannels() foi corrigido para fornecer informações precisas, melhorando a clareza e a utilidade da documentação. Anteriormente, o PHPDoc para este método continha informações incorretas, o que poderia levar a confusão ou uso incorreto do método.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39246>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [Problema] Remove alguns códigos de versões do PHP para as quais não há mais suporte.
   * _Observação de correção_: remoção do código para versões do PHP que não são mais suportadas no Magento
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39361>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [Problema] Tornar o Adaptador ImageMagick compatível com php8 (Conversão implícita de float em int)
   * _Observação de correção_: o sistema agora garante a compatibilidade com o PHP8 manipulando corretamente números flutuantes ao calcular dimensões de imagem, evitando quaisquer erros devido à conversão implícita de float para int. Anteriormente, o cálculo das dimensões da imagem podia resultar em números flutuantes, que quando arredondados implicitamente causavam um erro.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39402>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [Problema] [PHPDOC] Corrigir phpdoc incorreto Magento\Framework\App\Config\ScopeConfigInterface
   * _Observação de correção_: esta atualização corrige as anotações PHPDoc no Magento\Framework\App\Config\ScopeConfigInterface para refletir precisamente o tipo do argumento $scopeCode para os métodos getValue e isSetFlag.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39492>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39199>
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http depende da frase de motivo OK
   * _Observação de correção_: a verificação de frase &quot;OK&quot; foi removida de Magento\Framework\Filesystem\Driver\Http::isExists
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39546>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: o indexador de grade do cliente não funciona corretamente no modo Atualizar por agendamento
   * _Observação de correção_: a grade Anterior do cliente foi atualizada instantaneamente, mas após a correção, a grade do cliente é atualizada após a execução do cron, mas não reflete instantaneamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: erro de digitação em um arquivo js.
   * _Observação de correção_: o sistema agora usa corretamente o termo &quot;assinantes&quot; no arquivo do JavaScript, garantindo a funcionalidade adequada dos recursos relacionados. Anteriormente, um erro tipográfico no arquivo JavaScript resultava no uso incorreto do termo &quot;assinantes&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36163>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [Problema] Remover marca `@author` proibida
   * _Observação de correção_: o sistema agora segue os padrões de codificação, removendo a marca `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, a tag `@author` estava presente em alguns módulos, o que era contrário aos padrões de codificação estabelecidos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37253>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Edição] Remover proibido `@author` tag de `Magento_Customer` (parte 2)
   * _Observação de correção_: o sistema agora segue o padrão de codificação, removendo a marca `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, o `@author` tag estava presente em alguns módulos, o que era contra as normas de codificação estabelecidas.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37250>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: espaço na regra de quebras de sintaxe editorconfig para [{composer,auth}.json]
   * _Observação de correção_: o sistema agora aplica corretamente um recuo de 4 espaços ao compositor e aos arquivos auth.json, seguindo uma correção para um erro de sintaxe no editorconfig. Anteriormente, devido a um espaço na sintaxe editorconfig, esses arquivos eram formatados incorretamente com um recuo de 2 espaços.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37394>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37395>
* _AC-8662_: [Problema] que melhora o erro cron fazendo logon
   * _Observação de correção_: o sistema agora captura e registra em log STDERR e STDOUT para processos CRN, fornecendo informações de diagnóstico valiosas em cenários em que os processos CRN falham. Anteriormente, qualquer mensagem de erro nos processos cron não era registrada, e STDERR e STDOUT para grupos cron em execução em processos separados eram perdidos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37453>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32690>
* _AC-8984_: [Problema] Adiciona mais algumas cores à saída de determinados comandos da cli de instalação
   * _Observação de correção_: o sistema agora adiciona mais cores à saída de determinados comandos de CLI (interface de linha de comando) de instalação, melhorando a legibilidade e a experiência do usuário. Anteriormente, a saída desses comandos era mais difícil de ler devido à falta de diferenciação de cores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/29335>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: a atualização do Magento redefine general/region/state_required quando um novo país com o estado/região obrigatórios é adicionado.
   * _Observação de correção_: o sistema agora só adiciona o país modificado à configuração &#39;general/region/state_required&#39; quando um novo país com estados obrigatórios é adicionado, evitando qualquer interrupção no código personalizado que pressupõe que a região esteja desabilitada. Anteriormente, adicionar um novo país com estados obrigatórios redefinia a configuração &quot;general/region/state_required&quot; para países padrão com um estado obrigatório, possivelmente quebrando a loja.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/37796>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: diferença em menos compilação entre php e biblioteca nodejs (grunt) com expressões `calc` complicadas
   * _Nota de correção_: corrija a diferença na compilação menor entre php e biblioteca nodejs (grunt) após a atualização wikimedia/less.php:^5.x
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/37841>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: erro &quot;Tabela ou exibição base não encontrada&quot; ocorre quando a indexação parcial é executada
   * _Observação de correção_: a reindexação parcial agora funciona corretamente com o log de alterações grande no caso de conexão do banco de dados secundário
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: problemas após atualizar MariaDB para 10.5.1 ou superior
   * _Observação de correção_: corrigido o problema quando valores datetime em um banco de dados eram convertidos para 0000-00-00 00:00:00 após a atualização do Mysql
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Tipo Incompatível na Comparação de Dados ao verificar se os dados têm alterações
   * _Observação de correção_: anteriormente, o objeto salvo era chamado sempre sem nenhuma alteração de dados (para qualquer campo de dados numérico, como int/float/double). Ele aciona o sinalizador _hasDataChanges para ser true e chama a função de salvamento. Depois que essa correção for aplicada, a função salvar só chamará se os dados forem alterados. O valor de dados para int/float/double-check com o valor passando para a função e faz a correspondência de tipo strict.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [A importação da nuvem] não pode ser usada com o var de diretório
   * _Observação de correção_: o produto pode ser importado com êxito independentemente do nome do arquivo.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: Em ipad mini o menu e o cabeçalho carregados como móveis, em vez disso eles devem carregar como desktop.
   * _Observação de correção_: o sistema agora trata dispositivos com uma largura de 768px como desktop, garantindo que o menu e o cabeçalho sejam carregados corretamente. Anteriormente, os dispositivos com uma largura de 768 px eram tratados como móveis, fazendo com que o menu e o cabeçalho fossem carregados em uma visualização móvel.
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3230_: Modificar o comprimento da coluna via db_schema.xml não funciona no caso de chaves estrangeiras
   * __ Observação de correção: modificar a coluna com chave externa via schema declarativa agora não aumenta erros com MariaDB
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: Alguns dos registros de relações são salvos no DB quando solicitar registro é salvo
   * __ Observação de correção: antes da correção, consultas de ATUALIZAÇÃO desnecessárias eram acionadas, o que pode afetar o desempenho. Após a correção, as consultas de ATUALIZAÇÃO desnecessárias foram eliminadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [NUVEM] No admin, há muitos erros de javascript no console
   * _Observação de correção_: anteriormente, no painel de administração, havia muitos erros de javascript no console. Agora, no painel de administração, não haverá erros de JavaScript no console e todas as funções padrão do JavaScript serão executadas com êxito sem problemas.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: fila mensagem foi excluída
   * _Observação de correção_: as mensagens da fila agora estão sendo devidamente apagadas. Antes da correção, dado que o sistema de fila SQL estava sendo usado, novas mensagens poderiam ter sido excluídas se a limpeza fila mensagem estivesse em execução ao mesmo tempo.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3537_: As entradas de chave de cache correspondentes não estão disponíveis em tags de cache, portanto, a limpeza de cache não funciona corretamente
   * _Observação de correção_: o modo LUA agora está ativado por padrão para o coletor de lixo de cache Redis para evitar as condições de corrida
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_: MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK valor é ignorado
   * __ Observação de correção: Após a correção, um ENV variável definido como &quot;falso&quot; será tratado como bool false, não como a sequência &quot;false&quot;.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/982b1c42>

### Estrutura, GraphQL

* _AC-7976_: [] Suporte a tipos de escalar personalizados para o GraphQL schema
   * _Observação de correção_: o sistema agora oferece suporte a tipos escaladores personalizados para schema GraphQL, permitindo que os desenvolvedores definam tipos e implementações escalacionais personalizadas. Esse recurso pode ser particularmente útil para expressar valores que podem exigir validação, como HTML, emails, URLs, datas, etc., e para casos mais avançados curtir atributos EAV. Anteriormente, o sistema não suportava o processamento de tipos scalar personalizados no GraphQL.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/36877>
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Estrutura, estrutura interface

* _ACP2E-3324_: Possibilidade de substituir o valor de configuração mesmo que esteja bloqueado
   * __ Observação de correção: Anteriormente, a configuração do design não podia ser definida por meio de bin/magento config:set command and locked values could be changed by manipulation of the form displaying.. Depois da correção, os valores bloqueados definidos a partir de cli com --lock-env ou --lock-conf não podem mais ser atualizados.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_: Magento_GraphQl executa o processamento de cabeçalhos mesmo que o valor do cabeçalho não passe validação
   * _Observação de correção_: O sistema agora garante que o processamento de cabeçalho seja executado apenas uma vez e somente se o valor do cabeçalho passar validação, aumentando a segurança e evitando possíveis vulnerabilidades. Anteriormente, o processamento de cabeçalho era executado mesmo que o valor do cabeçalho não transmitisse validação, levando a potenciais vulnerabilidades e comportamento inesperado devido ao duplo processamento de valores de cabeçalho.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: As opções de giftcard físico não têm a classificação certa solicitar
   * _Observação de correção_: O sistema agora classifica corretamente as opções de presente físico cartão produtos quando consultados via GraphQL, garantindo renderização consistente com o tema Luma. Anteriormente, a classificação solicitar estava incorreta de acordo com o tema luma, levando a uma exibição e ordem incorretas de opções, como nome do remetente, nome recipient e quantia.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [O cache do resolvedor de GraphQL] é invalidado ao criar/editar/mover/excluir uma atualização de armazenamento temporário
   * __ Observação de correção: O sistema agora garante que o cache do resolvedor não seja invalidado ao criar, editar, mover ou excluir uma atualização de preparo, mas apenas quando a atualização de armazenamento temporário for aplicada à entidade. Anteriormente, o cache do resolvedor era invalidado prematuramente, mesmo antes da atualização de preparo ser aplicada, o que levou a invalidações desnecessárias do cache.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: Cache rápido não limpo para conteúdo atualização de preparo
   * _Observação de correção_: agora o GraphQL com o cache de resposta do conteúdo do PageBuilder é invalidado, quando o PageBuilder conteúdo entidades relacionadas são atualizados.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Desativar a naveção em camadas - Não remove a agregação do Graphql
   * __ Observação de correção: o problema foi corrigido após aplicar a verificação ao solicitar uma pesquisa de produto com agregações de categoria por meio de uma query GraphQL quando a configuração administrador de configuração &quot;Catalog > Layered Navigation > Display Categoria Filtrar&quot;.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: A chamada de Produtos GraphQL contendo o filtro de preço {de:&quot;0&quot;} não retorna nenhum resultado
   * _Observação de correção_: Anteriormente, os produtos graphql pesquisa com filtro para preços zero não retornava nenhum resultado devido a uma exceção lançada. Agora a pesquisa retorna resultados conforme esperado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: Traduções para atributos de retorno do cliente não refletidas na API GraphQL para a respectiva StoreView
   * _Observação de correção_: as traduções para atributos de retorno do cliente são refletidas na API graphQL para a respectiva StoreView.
Os atributos de retorno do cliente anteriormente para a respectiva StoreView não foram refletidos na API GraphQL.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_: [Chamada de GraphQL quebrado na nuvem] para getPurchaseOrder com nó citação
   * _Observação de correção_: a chamada GraphQL da Ordem de Compra poderá executar a tarefa sem encontrar erros internos no servidor.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Nuvem] Produtos Configuráveis não mostrados no Site de Produção se o Produto não estiver habilitado em &quot;Todos os Modos de Exibição de Loja&quot;
   * _Observação de correção_: o sistema agora exibe corretamente os produtos configuráveis no site, mesmo que o produto não esteja habilitado em &quot;Todas as Exibições da Loja&quot;, mas esteja habilitado em escopos específicos de exibição da loja.
Anteriormente, se um produto era desativado em &quot;Todas as exibições da loja&quot; e ativado apenas em escopos de exibição da loja específicos, os atributos do produto não eram exibidos corretamente na resposta do GraphQL, fazendo com que o produto não fosse exibido corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [o graphql de produtos da nuvem] está com erro quando o mesmo produto simples foi atribuído a vários produtos configuráveis
   * _Observação de correção_: Anteriormente, com produtos configuráveis separados com o mesmo produto simples, grapQL retorna um erro. Depois que essa correção se aplica, diferentes produtos configuráveis com o mesmo produto simples, grapQL retorna resultados sem erro.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_: [Problema na nuvem] com Authentication de usuários e acesso de tokens entre sites na configuração de vários sites
   * _Observação de correção_: as consultas de informações do cliente e do carrinho do GraphQl na configuração de vários sites verificam se o cliente está em um site não padrão.
Anteriormente, a consulta funcionava sem verificar se o cliente existe em um site não padrão na configuração de vários sites.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: a paginação itemsV2 do carrinho do GraphQL não está funcionando corretamente
   * _Observação de correção_: o problema foi corrigido ao passar o valor correto para o argumento da página atual na consulta de coleção. Anteriormente, o valor errado era passado para definir a página atual, causando o problema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* O valor do modelo _ACP2E-3255_: [GRAPHQL] deve ser especificado ao obter o customerCart
   * _Observação de correção_: a consulta &#39;customerCart&#39; do GraphQL agora pode criar um carrinho vazio mesmo quando a cotação não está disponível no banco de dados. Anteriormente, essa operação falhava devido a problemas de validação de país ao criar o carrinho vazio.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [GraphQl] Os itens da lista de desejos estão visíveis via GraphQl, mas não estão visíveis na loja
   * _Observação de correção_: produtos da lista de desejos não estão sendo listados corretamente quando solicitados via GraphQL. Agora, os produtos da lista de desejos são filtrados com base no contexto de loja fornecido.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] Redefinir inconsistência de email de senha entre conteúdo e assunto/link
   * _Observação de correção_: o problema foi resolvido simulando o armazenamento correto no qual a conta do cliente está registrada ao enviar a solicitação de redefinição de senha, independentemente do armazenamento do site.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: produtos [Cloud] a consulta do GraphQL retorna produtos relacionados não atribuídos ao site atual
   * _Observação de correção_: anteriormente, para a consulta graphQL, os produtos relacionados a várias lojas não eram exibidos corretamente para a consulta de produtos. Depois que essa correção é aplicada, para produtos, os produtos relacionados a várias lojas de consulta de graphQL são exibidos de acordo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: usar a ID de Armazenamento incorreta no cabeçalho do GraphQL causa erro fatal de memória
   * _Observação de correção_: o envio de código de armazenamento incorreto na solicitação GraphQL não resulta mais em consumo excessivo de memória.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [Nuvem] Resposta 500 para resposta Graphql vazia em 2.4.7
   * _Observação de correção_: após a correção, as solicitações graphql inválidas não serão registradas no arquivo exception.log.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_: [Nuvem] Problemas com a API Graphql
   * _Observação de correção_: antes de corrigir usando o servidor de aplicativos Graphql, a solicitação de endereço do cliente não retornava os dados mais recentes.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_: o produto desabilitado ainda aparece em itens relacionados, de venda adicional e de venda cruzada na consulta GraphQL
   * _Observação de correção_: o Graphql agora fornece a resposta correta para produtos rerelacionados, de venda adicional e de venda cruzada desabilitados
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_: [NUVEM]: erro de GraphQl Erro interno do servidor placeOrder mutation
   * _Observação de correção_: a mutação &quot;placeOrder&quot; com informações de código cupom no solicitação não está mais lançando uma exceção de erro interna, a solicitar foi colocada com sucesso. Anteriormente, falhava com &quot;Erro interno do servidor&quot;.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_: a discount_percentage não é calculada para produtos agrupados com preço dinâmico
   * _Observação de correção_: correção adicionada para discount_percentage de product.price_details não mostrando o valor correto de produtos agrupados com preço dinâmico habilitado e cupom de desconto aplicado.
* _LYNX-485_: o pacote de produtos ainda exibe &quot;IN_STOCK&quot; quando um de seus produtos agrupados está esgotado
   * _Observação de correção_: resolvida o problema em que os produtos de pacote ainda exibiam &quot;IN_STOCK&quot; mesmo quando um de seus produtos de pacote estava esgotado.
* _LYNX-486_: not_available_message e only_x_left_in_stock não mostram o mesmo estoque disponível
   * _Observação de correção_: resolvido o problema em que not_available_message e only_x_left_in_stock exibiam disponibilidade de estoque inconsistente
* _LYNX-488_: campo original_row_total retornando valor incorreto
   * _Observação de correção_: resolveu o problema com o campo original_row_total, que retornava valores incorretos quando opções personalizadas eram selecionadas
* _LYNX-503_: a miniatura de produto agrupada deve ser mostrada de acordo com a configuração     .
   * _Observação de correção_: resolveu o problema para garantir que a miniatura do produto agrupado seja exibida de acordo com as configurações
* _DART-512_: original_item_price não está incluindo descontos
   * _Nota de correção_: original_item_price atualizado para incluir descontos.
* _LYNX-530_: a mensagem não disponível não está mostrando a quantidade de estoque disponível
   * _Observação de correção_: resolvida a mensagem de erro e o código de erro para a mutação AddProductsToCart para alinhar com a configuração de mensagem &quot;não disponível&quot;
* _LYNX-532_: o status &quot;OUT_OF_STOCK&quot; retorna em Simples com opções personalizadas para produtos com opções de seleção múltipla
   * _Observação de correção_: o resolvedor StockStatusProvider no pacote de estoque foi atualizado para corrigir stock_status de produtos simples com opções personalizadas.
* _LYNX-533_: Erro (GQL): cart.itemsV2.items.product.custom_attributesV2 retorna um erro de servidor
   * _Observação de correção_: resolveu o erro de servidor que ocorria quando uma consulta de carrinho incluía os atributos personalizados de um produto adicionando um produto sem atributos personalizados.
* _LYNX-536_: orders/date_of_first_order sempre retornando nulo
   * _Observação de correção_: resolvida a questão em que pedidos > date_of_first_order estava sempre retornando nulo.
* _LYNX-544_: o cliente não deve poder cancelar um pedido parcialmente enviado
   * _Observação de correção_: foi adicionada uma validação para impedir que os clientes cancelem uma ordem parcialmente remetida.
* _LYNX-548_: códigos de erro para cancelamento de pedido com base na mensagem de erro
   * _Observação de correção_: os códigos de erro para cancelamento de pedido agora se baseiam na mensagem de erro específica.
* _LYNX-581_: mover de volta as propriedades relacionadas a cookies de particular para protegido
   * _Observação de correção_: reverte a visibilidade das propriedades do construtor de classe Magento\Framework\App\PageCache\Version de particular para protegido
* _LYNX-600_: aumentar a complexidade máxima da consulta padrão do GraphQL para 1000
   * _Observação de correção_: aumento do GraphQL máximo padrão query complexidade de 300 para 1000.
* _GQ-620_: GQL - itensV2 > Total da linha original, os preços da faixa de preços são retornados como $0,00 para produto para download com opções de arquivo que tem preços separados.
   * _Observação de correção_: solução de um problema em que produtos habilitados para download com opções de link compra separadas retornavam US$ 0 para itensV2 > total da linha Original, faixa de preço retornada como US$ 0,00 para produtos com opções de arquivo com preços separados.
* _LINCE-772_: Compatibilidade GraphQL para PHP-8.4 Versão
   * _Observação sobre correções_: correção de problemas de compatibilidade do GraphQL com o PHP 8.4 em vários resolvedores, garantindo uma funcionalidade sem problemas. Atualização dos arquivos afetados nos módulos CatalogRule, Customer, GiftMessage, GiftCard e GiftWrapping.

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
* _ACP2E-948_: consulta GraphQL da lista de produtos limitada a total_count apenas 10.000 produtos
   * _Observação de correção_: após a correção, o resultado da pesquisa não fica limitado a 10.000 produtos; será possível obter todos os produtos que correspondam aos critérios da pesquisa, mesmo que a contagem seja superior a 10.000.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, Estrutura de teste

* _ACP2E-3363_: falha no Teste de Integração do Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Nota de correção_: &#39;-
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importar/exportação

* _AC-12172_: Problema na importação do produto quando fornecido com opções personalizadas: arquivo (Produto criado não contém preço para a opção personalizada e mostra apenas a primeira extensão de tipo de arquivo fornecida)
   * _Observação de correção_: O sistema agora importa corretamente dados do produto com opções personalizadas de tipo &quot;arquivo&quot;, garantindo que todas as extensões de arquivo fornecidas sejam exibidas e o preço da opção personalizada esteja incluído. Anteriormente, durante a importação do produto, se uma opção personalizada de tipo &quot;arquivo&quot; era fornecida com mais de uma extensão de arquivo, apenas a primeira extensão era exibida e o preço da opção personalizada estava ausente.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38805>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: tempo de execução incorreto para a operação de importação na grade do Histórico de Importação
   * _Observação de correção_: o tempo de execução do relatório de importação é mostrado corretamente independentemente da localidade do administrador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Clientes duplicados sendo criados com o mesmo endereço de e-mail usando a importação
   * __Observação de correção: a importação do cliente enquanto o Compartilhamento de contas está definido como Global, o cliente importado que existe no sistema é atualizado.
O cliente importado anteriormente foi duplicado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Adicionar/Atualizar Importação em Produtos Duplicando Opções Personalizáveis
   * _Observação de correção_: o problema foi resolvido com a atribuição da loja correta às opções de produto durante importações de CSV de opções de produto.
Anteriormente, o era atribuído ao armazenamento de administração em vez do respectivo armazenamento.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: Data &quot;created_at&quot; do cliente Não convertida em armazenamento fuso horário ao exportar
   * _Observação de correção_: um valor de data &quot;created_at&quot; de coluna é convertido em um formato de data apropriado com base no fuso horário armazenamento na seção de CSV de exportação do cliente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Erro de obtenção de nuvem] ao verificar os dados nos dados de importação usando CSV
   * __ Observação de correção: não há erro ao verificar os dados durante CSV importação. Anteriormente, a mensagem de erro era: &quot;Não é possível encontrar um cliente que corresponda a esse código de email e site em linha(s): 1&quot; ao verificar os dados na seção de importação usando CSV do administrador.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_: Importar botão ausente
   * _Observação de correção_: resolva o Importar botão problema ausente após as verificações de dados com registros corretos e incorretos no CSV. Anteriormente, a botão de importação não era exibida após as verificações de dados com registros corretos e incorretos no CSV.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Endereços de clientes exportados não podem ser importados
   * _Observação de correção_: a importação de endereços do cliente prosseguirá como esperado. Anteriormente, um arquivo de importação de endereço do cliente não passaria validação se Compartilhar contas do cliente = Global, e há dois sites onde o site padrão tem um país restrito lista, e o endereço que está sendo importado é para outro site onde os países permitidos são diferentes
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: A [quantidade errada da nuvem] no CSV arquivo não deu erro
   * _Observação de correção_: agora, a importação de fontes de estoque lançará validação erro para valores não numérico na coluna quantidade. Anteriormente, a importação de fontes de estoque com valor não numérico na coluna quantidade resultou na definição do quantidade como 0.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_: Duplicação URL mensagem de erro principal gerada quando a importação de um produto não está correta quando a Chave de URL já pertence a um categoria
   * _Observação de correção_: exibir a mensagem de erro correta durante a verificação de importação do produto, quando o cliente tentou importar o produto quando a chave de url do produto já pertencia a uma categoria.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_: A exportação de produtos causa OOM mesmo com o limite de memória 4G
   * __ Observação de correção: Anterior a essa correção, a exportação do produto falhava se os atributos do produto tivessem milhares de valores de opção mesmo com a memória 4G disponível. Após essa correção, a exportação do produto deve terminar de exportar o arquivo csv.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_: [processos de Importar da nuvem] interferindo uns com os outros
   * _Observação de correção_: Correto mensagens serão mostradas se a mesma administrador usuário realizar duas ou mais operações de importação usando a mesma sessão de usuário.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d4de4726>

### Importar/exportação, Desempenho

* _ACP2E-3476_: [Nuvem] O tempo de importação do produto aumentou significativamente
   * _Observação de correção_: antes da correção, a importação de produtos do catálogo com mais de 10.000 entradas tinha uma degradação de tempo significativa. Após a correção, a importação do produto de catálogo é executada em tempo hábil.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/87d012e5>

### Instalar e administrar

* _AC-13242_: falha na atualização do Magento no MariaDB 11.4 + 2.4.8-beta1
   * _Observação de correção_: a atualização deve ter ocorrido sem nenhum erro.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_: Nenhum VCL de exportação para Vernish 7 botão em administrador painel
   * _Observação de correção_: &quot;Exportar VCL para Varnish 7&quot; botão foi adicionada ao painel Admin.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventário / MSI

* _AC-10750_: a atualização de inventário do Produto Configurável falha quando o banco de dados usa prefixos
   * _Observação de_ correção: O sistema agora atualiza corretamente a inventário de produtos configuráveis quando o banco de dados usa prefixos, impedindo quaisquer mensagens de erro e garantindo que a quantidade correta seja salva. Anteriormente, ocorreria um erro ao tentar salvar a inventário quantidade de produtos simples em um produto configurável se o banco de dados estivesse usando prefixos.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: a chave da API do Google google não funciona ao adicionar o mapa com atributos
   * _Observação de correção_: o sistema agora oferece suporte à versão mais recente da API do Google Maps 3.56, permitindo que os usuários adicionem com êxito um bloco de conteúdo do Mapa do menu PageBuilder ao estágio sem encontrar erros. Anteriormente, os usuários não conseguiam adicionar um bloco de conteúdo do Mapa devido a problemas de compatibilidade com a versão da API do Google Maps, resultando em uma mensagem de erro &quot;algo deu errado&quot;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: não é possível criar remessa para item de pedido com várias fontes e SKU corrompido
   * _Observação de correção_: anteriormente, quando espaços eram adicionados por engano no sku por meio do banco de dados, ocorria um erro na página de remessa, que agora é fixa e o corte automático é considerado um erro humano e nenhum impacto foi encontrado. Portanto, o envio foi criado com êxito.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [Testar] produtos do pacote com 0 inventário exibidos armazenamento frente
   * _Observação de correção_: o pacote produto não é exibido nos sites adicionais usando estoque adicional.
* _ACP2E-2794_: [Problema crítico da nuvem] com lista de produtos com espaços vazios
   * _Observação de correção_: O sistema agora exibe corretamente listas de produtos sem espaços vazios quando os produtos são definidos como &quot;Fora de Stock&quot;, garantindo uma exibição consistente e precisa dos produtos disponíveis. Anteriormente, definir um produto como &quot;Fora de Stock&quot; resultaria em um espaço vazio aparecendo na listagem de produtos, interrompendo o layout e potencialmente confundido os clientes.
   * _Contribuição_ do código do GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: Não é possível enviar o solicitar quando o MSI pegar armazenamento está ativado
   * _Observação de correção_: desempenho inventário da criação de envio no caso de muitas fontes com coleta armazenamento local
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: A reindexação do Cron falha ao atualizar a disponibilidade do produto no frontend
   * _Observação de correção_: anteriormente, os produtos permaneciam indisponíveis no front-end após a atualização do status do backorder por meio da API REST. Agora, depois de atualizar o status do backorder por meio da API REST, os produtos são mostrados como em estoque.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Adicionar imagens ao configurável não funciona quando o MSI está ativado.
   * __ Observação de correção: Imagem upload para produtos configuráveis agora funcionará conforme esperado quando inventário módulo são usadas. Anteriormente, o upload da imagem não funcionava
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: problema com o produto bundle + MSI no Clean M2.4.7-p3
   * _Observação de correção_: Anteriormente, para inventário pacote produtos após a duplicação com o mesmo produto simples, o produto simples não pode ser salvo. Depois que essa correção é aplicada, o produto simples pode ser salvo com sucesso sem exceções.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/39358>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/0208e433>

### Inventário / MSI, Search

* _ACP2E-3413_: todos os produtos são indexados com [is_out_of_stock] = 1 quando o SKU não está definido como um atributo pesquisável
   * __ Observação de correção: após a correção, o &quot;is_out_of_stock&quot; no catálogo pesquisa índice está correto, mesmo quando sku não é pesquisável.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/inventory/commit/5b21b7af>

### Ordem

* _AC-10828_: Tela de visão geral solicitar backend: os quantidade reordenados não estão visíveis no nível de solicitar item
   * _Observação de correção_: o sistema agora exibe o número de itens com backorder na coluna de quantidade na tela de visão geral da ordem de backend. Isso garante que os usuários possam rastrear com precisão o status de todos os itens em um pedido. Anteriormente, a coluna de quantidade mostrava apenas o número de itens encomendados, faturados e entregues, mas não exibia o número de itens com backorder.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38252>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problema] errado armazenamento ID usada no Renderizador de endereço de ordem
   * _Observação de_ correção: o sistema agora usa corretamente a ID do armazenamento associada a uma solicitar ao renderizar o endereço solicitar, garantindo que os endereços sejam formatados corretamente de acordo com sua respectiva ID de armazenamento. Anteriormente, o sistema estava usando incorretamente a ID de armazenamento atual, o que poderia cliente potencial à formatação incorreta de endereços em casos em que vários e-mails solicitar de diferentes lojas precisavam ser enviados.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38412>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: problema de cache JoinProcessor
   * _Observação de correção_: o sistema agora aplica corretamente o JoinProcessor para cada iteração, mesmo com chamadas consecutivas, garantindo uma recuperação de dados precisa. Anteriormente, o JoinProcessor era marcado incorretamente como já aplicado em iterações consecutivas, resultando em erros na recuperação de dados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/27504>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [Problema] Preço de envio mostrando diferenças no pdf impresso
   * _Nota de correção_: o sistema agora exibe corretamente os preços de remessa em PDFs impressos de acordo com as configurações de imposto, garantindo a consistência entre a página de exibição da fatura da ordem de venda e a fatura impressa. Anteriormente, o preço de envio exibido no PDF impresso excluía impostos, independentemente das configurações de imposto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38608>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_: Reordenar com um produto configurável principal excluído
   * _Observação de correção_: agora, ao reordenar com o produto excluído, o sistema não mostrará o botão de reordenação para reordenar
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39568>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [Problema] Correção incorreta \Magento\Sales\Model\Order\Email\Container\Template:$id propriedade
   * _Observação de correção_: isso corrige o phpdoc inválido para \Magento\Sales\Model\Order\Email\Container\Template::$id, na verdade $id é do tipo int, mas na realidade é string.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39151>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39150>
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
* _ACP2E-3311_: [Nuvem] Não é possível criar ordem no administrador em uma loja se apenas o Endereço de Cobrança Padrão não foi configurado
   * _Observação de correção_: agora existe uma mensagem de erro relevante &quot;Um cliente com o mesmo endereço de email em um site associado.&quot; é exibido se um cliente não tiver um Endereço de cobrança padrão e tentar criar um pedido em outra loja.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Envio de solicitações de ordem de local duplicadas pelo administrador
   * _Observação de correção_: anteriormente, o botão &quot;Enviar pedido&quot; no painel do administrador podia ser clicado várias vezes ou ativado ao pressionar repetidamente a tecla &quot;Inserir&quot;, causando duplicatas ou envios de pedidos com erro. Agora, evitando ações adicionais até que o pedido seja totalmente processado, garantindo que apenas um pedido seja enviado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: o administrador ainda pode fazer o pedido mesmo sem a forma de pagamento
   * _Observação de correção_: agora o método de pagamento selecionado anteriormente é retido quando o método de pagamento reaparece na lista de pagamentos disponíveis.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Ordem, Pagamentos

* _ACP2E-3233_: O administrador ainda pode colocar solicitar mesmo sem o método de pagamento
   * _Observação de correção_: Anteriormente, o comerciante poderia fazer pedidos do painel de administrador sem selecionar um método de pagamento. Agora, o comerciante é necessário um método de pagamento para continuar com a colocação de uma solicitar.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/fd5cf3af>

### Ordem, Devoluções

* _ACP2E-2982_: o reembolso de pedido resulta em memorando de crédito duplicado
   * _Observação de correção_: emitir o reembolso pela API REST quando duas solicitações idênticas forem executadas simultaneamente não criará mais Avisos de Crédito duplicados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Pedido, Imposto

* _ACP2E-3003_: [CLOUD] base_row_total incorreto na API de ordem RESTFUL ao habilitar transações transfronteiriças e aplicar descontos de cupom
   * _Observação de correção_: agora o base_row_total correto é retornado da API de ordem RESTFUL quando a transação transfronteiriça está habilitada e o desconto do cupom é aplicado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### Outro

* _LYNX-339_: cookie private_content_version retornado em consultas GQL
   * _Observação de correção_: corrigido um problema em que o cookie private_content_version era retornado em consultas GraphQL, mesmo quando o cookie da sessão estava desabilitado. O cookie não é mais incluído nas respostas do GraphQL quando a sessão é desativada, conforme esperado.
* _LYNX-380_: o atributo is_available em CartItemInterface retorna sempre false para produtos configuráveis
   * _Observação de correção_: corrigido um problema em que o atributo is_available em CartItemInterface sempre retornava false para produtos configuráveis no estoque. Agora, ele reflete corretamente a disponibilidade como verdadeira quando aplicável.
* _LYNX-382_: o atributo is_available em CartItemInterface retorna true mesmo quando o estoque vendável é menor que a quantidade do produto
   * _Observação de correção_: corrigido o problema em que o atributo is_available em CartItemInterface retornava incorretamente true, mesmo quando a quantidade do item do carrinho excedia o estoque disponível.
* _LYNX-399_: a miniatura do espaço reservado retorna quando um produto simples é adicionado ao carrinho em um produto agrupado
   * _Observação de correção_: corrigido um problema em que a adição de um produto simples (parte de um produto agrupado) ao carrinho retornava uma imagem em miniatura de espaço reservado, mesmo quando o produto tinha uma imagem atribuída.
Detalhes da correção:
· A miniatura do produto agora exibe corretamente a imagem atribuída, se disponível.
· A seleção da miniatura respeita a configuração do administrador em:
Lojas > Configuração > Vendas > Check-out > Carrinho de compras > Imagem de produto agrupada.
Isso garante um comportamento consistente de miniaturas para produtos agrupados com base nas configurações da loja.
* _LYNX-400_: os atributos de opção personalizados do cliente não funcionam com valores inteiros
   * _Observação de correção_: corrigiu um problema onde os atributos de opção personalizados do cliente não funcionavam quando o valor retornado era um número inteiro. Agora, as opções personalizadas lidam corretamente com valores inteiros e os retornam conforme esperado.
* _LYNX-402_: erro interno do servidor ao tentar obter priceDetails para produtos do pacote com preço dinâmico
   * _Observação de correção_: resolvida um problema em que a consulta de price_details para produtos agrupados com preços dinâmicos via GraphQL resultava em um erro interno do servidor. Esse aprimoramento garante consultas estáveis do carrinho ao trabalhar com produtos de pacote configurados com preços dinâmicos.
* _LYNX-403_: only_x_left_in_stock sempre retorna 0 para produtos configuráveis
   * _Observação de correção_: resolvida um problema em que o atributo only_x_left_in_stock sempre retornava 0 para produtos configuráveis quando adicionado usando o SKU pai com opções.
Detalhes da correção:
· O valor only_x_left_in_stock agora reflete com precisão o estoque da variante secundária selecionada, em vez do SKU principal.
· Isso garante que os níveis de estoque sejam exibidos corretamente para variações de produtos configuráveis no carrinho e nas páginas do produto.
* _LYNX-411_: a consulta do GraphQL não retorna o preço regular calculado correto para produtos personalizáveis
   * _Observação de correção_: correção de um problema no qual a GraphQL não retornava o preço normal calculado correto para produtos personalizáveis. A consulta agora inclui corretamente o preço regular calculado com valores personalizáveis aplicados (por exemplo, US$ 125) na propriedade price, refletindo o preço base e quaisquer custos adicionais de personalização.
* _LYNX-412_: AppliedTaxes via EstimatedTotals persistem com mutações atualizadas
   * _Observação de correção_: corrigiu um problema com a mutação EstimatedTotals onde os impostos aplicados persistiam em um carrinho mesmo após atualizar a região ou o código postal. A mutação agora atualiza corretamente os impostos aplicados ao alterar entre valores de região e código postal, garantindo que somente a regra de imposto correta seja aplicada com base nos dados atuais do carrinho.
* _LYNX-420_: o atributo is_available em CartItemInterface retorna true mesmo quando o estoque vendável é menor que a quantidade do produto
   * _Observação de correção_: corrigido um problema em que o atributo is_available em CartItemInterface retornava incorretamente true, mesmo quando o estoque comercializável era inferior à quantidade de produto solicitada. O campo is_available agora retorna corretamente false quando a quantidade do produto excede o estoque disponível.
* _LYNX-425_: preço normal do produto com 12 decimais e valor incorreto
   * _Observação de correção_: corrigido um problema em que o valor regular_price nos caminhos de GraphQL product.price_range.maximum_price e minimum_price não correspondia ao preço do catálogo quando várias taxas de imposto eram aplicadas. O regular_price agora reflete consistentemente o preço do catálogo em todas as configurações de imposto, garantindo um preço unitário preciso, cálculos de custo de linha total e verificações de desconto no Sumário do Carrinho.
* _LYNX-430_: erro de servidor do GraphQL no carrinho com produto empacotado indisponível
   * _Observação de correção_: correção de um problema em que o GraphQL retornava um erro interno do servidor ao buscar um carrinho contendo um produto empacotado com um item indisponível, especificamente quando a consulta incluía a propriedade itemsV2. O GraphQL agora retorna corretamente uma lista de itens com mensagens de erro relevantes anexadas à entrada do item de produto agrupado, conforme esperado.
* _LINCE-441_: Não é possível criar um endereço com atributos personalizados
   * _Observação de correção_: correção de um problema com a mutação createCustomerAddress que impedia a criação de endereços com atributos personalizados necessários. A mutação agora lida corretamente com atributos de endereço personalizados quando a carga apropriada é fornecida.
* _DART-447_: Erro do servidor GraphQL na carrinho com only_x_left_in_stock no produto empacotado
   * _Observação de correção_: correção de um problema em que a busca de uma carrinho contendo um produto empacotado com o campo only_x_left_in_stock no query GraphQL resultava em um erro interno do servidor. Agora, o GraphQL retorna corretamente um flutuante ou nulo para o campo de only_x_left_in_stock sem erros.
* _CE-464_: Erro de GraphQL ao remover outros produtos com produto configurável insuficiente em carrinho
   * _Observação de correção_: correção de um problema no qual tentar remover produtos em estoque do carrinho resultava em um erro GraphQL &quot;O qty solicitado não está disponível&quot; se o carrinho também contivesse produtos configuráveis com estoque insuficiente. A remoção agora funciona como esperado sem disparar erros.
* _LINCE-469_: Não é possível adicionar produtos devido ao SKU em mutação sendo diferencia maiúsculas de minúsculas
   * _Observação de correção_: solução de um problema em que a mutação addProductsToCart retornava um erro &quot;PRODUCT_NOT_FOUND&quot; ao usar SKUs com cápsula diferente. A mutação agora lida com as skus sem distinção entre maiúsculas e minúsculas, garantindo a consistência com consultas de serviços de catálogo e comportamento PDP.
* _LYNX-603_: atributo de produto > marca comercial short form ™ é retornado como ™
   * _Observação de correção_: resolvido um problema de codificação de caracteres com o nome do produto para a API do GraphQL
* _LYNX-619_: problema de mutação updateCustomerEmail
   * _Observação de correção_: resolveu um problema com a mutação updateCustomerEmail em que clientes sem atributos personalizados necessários (adicionados após a criação da conta) não podiam atualizar seus emails.
* _LYNX-626_: Mutation setShippingAddressesOnCart gera um erro ao usar pickup_location_code
   * _Observação de correção_: correção de um problema em que a mutação setShippingAddressesOnCart retornava um erro ao usar pickup_location_code sem especificar customer_address_id ou address. A mutação agora permite corretamente configurar um endereço de entrega com apenas o pickup_location_code.
* _LYNX-637_: Compatibilidade de vitrine eletrônica - Atualize a lógica para obter o nome da tabela com o prefixo e outras melhorias secundárias
   * _Observação de correção_: lógica atualizada para recuperar o nome da tabela com o prefixo (relacionado às alterações no SCP).
* _LYNX-643_: salvar no catálogo de endereços não funciona ao usar o campo same_as_shipping do GQL setBillingAddressOnCart
   * _Observação de correção_: correção de um problema em que o endereço de entrega não era salvo no catálogo de endereços do cliente ao usar a mutação de GraphQL setBillingAddressOnCart com o campo same_as_shipping definido como true. Agora, o endereço de entrega é armazenado corretamente conforme esperado.
* _LYNX-650_: padronizar order_id em mutações
   * _Observação de correção_: padronizou a entrada order_id em mutações e atualizou o modelo de email de confirmação de cancelamento da ordem para expor a ID do incremento em vez da ID do pedido.
* _LYNX-651_: CustomerOrder não está exibindo os comentários do pedido
   * _Observação de correção_: resolveu um problema com CustomerOrder para incluir comentários de pedidos em consultas de GraphQL de convidados e de pedidos de clientes.
* _LYNX-652_: original_item_price não deve incluir nenhum desconto
   * _Nota de correção_: atualização da lógica de original_item_price nos preços de itens do carrinho do GraphQL para excluir descontos.
* _LYNX-681_: o pacote de produtos ainda exibe &quot;IN_STOCK&quot; quando um de seus produtos agrupados está esgotado
   * _Observação de correção_: correção de um problema em que product.stock_status de produtos de pacote ainda exibia &quot;IN_STOCK&quot; mesmo quando um dos itens agrupados estava indisponível.
* _LYNX-686_: a consulta de cliente retorna Erro Interno do Servidor se o valor do atributo personalizado excluído existir para um cliente
   * _Observação de correção_: corrigido o problema em que a consulta do cliente retornava um erro interno do servidor quando um atributo personalizado excluído ainda tinha um valor armazenado. Agora, uma mensagem de erro apropriada será retornada se um atributo não existente for solicitado. O cache necessário é invalidado ao excluir o atributo personalizado do cliente.
* _LYNX-687_: parâmetro de ação para links de confirmação de retorno e cancelamento
   * _Corrigir observação_: parâmetro de ação adicionado para retornar e cancelar links relacionados a emails de confirmação
* _LYNX-689_: a URL de confirmação do usuário convidado é redirecionada para a página de status do pedido porque está faltando orderRef
   * _Observação de correção_: adição do parâmetro orderRef ao link no email de confirmação de cancelamento da ordem do convidado
* _LYNX-699_: não é possível retornar nulo para o campo não anulável &quot;TaxItem.title&quot; em placeOrder GQL
   * _Observação de correção_: correção de um problema em que a mutação placeOrder falhou com um erro de servidor interno devido a um valor nulo para o campo não anulável TaxItem.title. Agora, o campo sempre retorna um valor válido, garantindo o sucesso do posicionamento do pedido.
* _LYNX-702_: EstimateTotals: os descontos são nulos para tipos de produtos virtuais
   * _Observação de correção_: resolveu o problema com a mutação estimateTotals retornando nulo para descontos quando um código de desconto é aplicado a um carrinho contendo produtos virtuais.
* _LYNX-703_: o produto do pacote não retorna a porcentagem e o valor de desconto corretos
   * _Observação de correção_: novas propriedades &quot;catalog_discount&quot; e &quot;row_catalog_discount&quot; foram introduzidas para os preços de itens de catálogo exibirem os valores e porcentagens de desconto corretos nos níveis de linha e de item único.
* _LYNX-714_: configuração da mensagem de presente no nível do produto
   * _Observação de correção_: correção de um problema em que as mensagens de presente não eram aplicadas no nível do produto quando desabilitadas globalmente. Agora, se as mensagens de presente estiverem habilitadas para um produto específico, elas poderão ser adicionadas com êxito usando a mutação updateCartItems e serão salvas e refletidas corretamente.
* _LYNX-757_: a consulta cart.rules retorna um erro em vez de uma matriz vazia, caso nenhuma regra de carrinho ativa seja aplicada
   * _Observação de correção_: corrigida a consulta cart.rules para retornar uma matriz vazia em vez de um erro quando nenhuma regra de carrinho ativa é aplicada.
* _LYNX-778_: as chamadas do GraphQL com o método OPTIONS estão retornando o código de resposta 500 quando o pacote adobe-commerce/storefront-compatibility está instalado
   * _Observação de correção_: corrigido um problema em que as chamadas do GraphQL usando o método OPTIONS retornavam um Erro interno de servidor 500 quando o pacote adobe-commerce/storefront-compatibility era instalado. O endpoint agora retorna corretamente uma resposta 200/204, conforme esperado.

### Outras ferramentas de desenvolvedor

* _AC-10658_: [Problema] Corrigir erro de sintaxe do HTML em visual.phtml
   * _Observação de correção_: o sistema agora fecha corretamente a marca de início no arquivo visual.phtml, garantindo a sintaxe apropriada do HTML. Anteriormente, a tag de início não era fechada corretamente, causando um erro de sintaxe do HTML.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38247>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problema] alterado para &quot;ativo&quot; no comando bin/magento maintenance:status
   * _Observação de correção_: o sistema agora fornece mensagens de status mais precisas para o comando de modo de manutenção, alterando o status de &quot;ativo&quot; para &quot;habilitado&quot; e de &quot;não ativo&quot; para &quot;desabilitado&quot;. Anteriormente, a mensagem de status para o comando de modo de manutenção era exibida como &quot;ativo&quot; ou &quot;não ativo&quot;, o que poderia causar confusão.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38486>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: navegar na árvore de categorias leva a erros no Redis: &quot;A sessão do Redis excedeu as conexões simultâneas&quot;
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38851>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_: problemas de CSP combinados com dev/css/use_css_critical_path
   * _Observação de correção_: o sistema agora carrega corretamente os arquivos CSS de forma assíncrona nas páginas de check-out, mesmo quando a configuração &quot;dev/css/use_css_critical_path&quot; está habilitada, garantindo que essas páginas sejam renderizadas com os estilos CSS adequados. Anteriormente, uma Política de segurança de conteúdo (CSP) restrita impedia a execução do JavaScript em linha, o que fazia com que os arquivos CSS não fossem carregados conforme esperado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39020>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: usando o tipo virtual para configurar o plug-in, o método interceptor não pode ser gerado corretamente no comando setup:di:compile
   * _Observação de correção_: o sistema agora gera corretamente métodos interceptores ao usar um tipo virtual para configurar um plug-in, garantindo resultados consistentes, sejam pré-compilados ou compilados em tempo de execução. Anteriormente, o sistema gerava resultados incorretos quando pré-compilado em comparação à compilação em tempo de execução.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/33980>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3631_: Adobe Systems Comércio testes de unidade 2.4.7-p3 estão falhando
   * _Observação de correção_: não é necessário notas de versão.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/982b1c42>

### Métodos de pagamento/pagamento, pedido

* _AC-13699_: detalhes do cartão de crédito do fluxo de pagamento papal salvos para uso posterior não são exibidos na página de método de pagamento armazenado
   * _Observação de correção_: os detalhes do cartão de crédito do fluxo de pagamento papal anterior salvos para uso posterior não apareciam na página de método de pagamento armazenado, que agora apresenta os detalhes do cartão de crédito fixo na página de método de pagamento armazenado.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/96dec499>

### Pagamentos

* _AC-13414_: O pagamento do cartão de crédito (link de fluxo de pagamento) não está funcionando
   * _Observação de correção_: Anteriormente, o erro de obtenção (o pagamento foi recusado) enquanto colocava solicitar com cartão de crédito após o Pedido de correção colocado com sucesso.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: O fluxo de pagamento cria uma nova transação sempre que clicamos em buscar botão na tela de transação visualização
   * _Observação de correção_: O sistema agora busca corretamente as informações de transação sem criar uma nova transação de pagamento sempre que a busca botão for clicada na tela visualização transação. Anteriormente, clicar na busca botão criaria incorretamente uma nova transação de pagamento para uma solicitar que já havia sido paga.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: Mensagem do paylater não exibida no PDP para PayPal canadense comerciante conta
   * _Observação de correção_: O sistema agora exibe corretamente a mensagem PayLater para contas do PayPal canadense comerciante na Página de Detalhes do produto (PDP) quando o país do comprador pode ser determinado a partir do endereço conta faturamento ou envio. Anteriormente, a mensagem PayLater não era exibida devido a um parâmetro ausente, resultando em um erro no console navegador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_: reembolso de pedido do PayPal resulta em memorando de crédito duplicado
   * _Observação de correção_: correção de um problema de simultaneidade de avisos de crédito criados pelo IPN para o serviço de pagamento do PayPal.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: a regra de preço do carrinho não funciona para Paypal
   * _Observação de correção_: Correto quantia é mostrada PayPal lado quando o desconto é aplicado pelo método de pagamento
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [Usuários da nuvem] com um função específico não podem fazer logon
   * __ Observação de correção: administrador usuário com função que contêm apenas PayPal acesso à Seção agora pode fazer logon sem erros
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/66dea0de>

### Desempenho

* _AC-11932_: Problema de Configurações de Atributo de Produto Padrão
   * _Observação de correção_: o sistema agora permite que os usuários cancelem a seleção de uma opção padrão para um atributo de produto, garantindo que o atributo nem sempre tenha um conjunto padrão. Anteriormente, uma vez que o padrão era definido para um atributo do produto, não havia como desmarcá-lo, resultando no atributo sempre tendo um conjunto padrão.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38703>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-12000_: [Edição] Code limpeza e adicionar novo bloco de cabeça crítico e mover crítico css antes de ativos
   * _Observação de correção_: o sistema agora inclui um novo bloco de cabeçalho crítico e move CSS crítico antes dos ativos, permitindo mais personalização e otimização de desempenho no front-end. Anteriormente, o CSS crítico não era posicionado antes dos ativos, limitando as oportunidades de personalização e otimização.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38748>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: a compilação de tema é interrompida quando o host mysql contém informações de porta
   * _Observação de correção_: o sistema agora lida corretamente com a configuração de host MySQL, que inclui informações de porta, garantindo uma compilação bem-sucedida do tema. Anteriormente, a compilação de temas falharia se a configuração do MySQL host na conexão do banco de dados incluísse informações porta.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38799>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: Suporte ao CommandLoaderInterface de Symfony em Magento CLI
   * _Observação de correção_: essa alteração reduz o tempo de inicialização do aplicativo CLI Magento permitindo inicialização adiada de comandos até que eles sejam necessários.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/29266>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: Problema de desempenho ao carregar atributos de produto em carrinho regras
   * _Observação de correção_: desempenho query aperfeiçoado para regras de vendas - de cerca de 150 ms para um único dígito.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: Desempenho parcial de indexação do preço
   * _Observação de correção_: o desempenho da indexação parcial de preço foi aprimorado otimizando algumas das consultas de exclusão usadas no processo de indexação.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: A ordem é rejeitada em configurações de várias armazenamento ao usar o processamento assíncrono-solicitar + termos e condições
   * _Observação de correção_: os pedidos feitos a partir de sites não padrão com termos e condições habilitados agora são processados.
Antes de serem automaticamente rejeitados.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: A chamada da API Order Rest está demorando muito tempo para ser executada
   * _Observação de correção_: o sistema agora executa a chamada da API Order Rest dentro de uma período razoável, melhorando o desempenho ao buscar um grande número de pedidos. Anteriormente, a chamada da API Order Rest demorava muito tempo para ser executada, causando atrasos ao recuperar um grande número de pedidos.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/001e5188>

### Precificação

* _AC-11810_: Preço ausente da API do pedido Magento2.4.6-p4
   * _Observação de correção_: o sistema agora exibe corretamente o preço de produtos simples quando consultados por meio da API do pedido, garantindo uma representação precisa dos dados. Anteriormente, o preço de produtos simples era exibido incorretamente como zero na resposta da API.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: Erro de arredondamento de centavo no catálogo regra
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/276e0acd>

### Produto

* _AC-10535_: Caracteres especiais em nome de produto associado configurável estão sendo convertidos em entidades HTML.
   * _Observação de correção_: o sistema agora retém corretamente caracteres especiais nos nomes dos produtos associados ao editar um produto configurável, impedindo que eles sejam convertidos em entidades HTML. Anteriormente, caracteres especiais em nomes de produtos associados eram convertidos em entidades HTML quando o produto configurável era editado.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38146>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: a função GetById do ProductRepository não cria a chave de cache correta
   * __ Observação de correção: o sistema agora cria corretamente uma chave de cache na função GetById do ProductRepository, independentemente de a ID do armazenamento ser passada como uma string ou um número inteiro. Isso garante que o produto seja recuperado da memória em chamadas subsequentes, melhorando o desempenho. Anteriormente, o sistema recuperava o produto do banco de dados sempre que a função fosse chamada, mesmo com os mesmos parâmetros, devido à criação incorreta da chave de cache.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38384>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: Problema] [MFTF [] adicionado AdminClickAddOptionForBundleItemsActionGroup
   * _Observação de correção_: o sistema agora inclui o AdminClickAddOptionForBundleItemsActionGroup, aprimorando as funcionalidade do painel administrador. Anteriormente, esse grupo de ação não estava disponível.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/30857>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/30838>
* _AC-13173_: [Problema] Corrigir erro de digitação no bloco PHPDoc
   * _Observação de correção_: o sistema agora remove corretamente uma variável referenciada desconhecida no PHPDoc para a declaração de variável $helper, melhorando a clareza e a precisão do código. Anteriormente, essa variável referenciada desconhecida no PHPDoc estava causando confusão e possíveis imprecisões no código.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38961>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problema] Corrigido o pacote corrompido e o layout de páginas de produto baixáveis no Magento >= 2.4.7
   * _Observação de correção_: o layout das páginas de produto agrupadas e baixáveis foi corrigido, garantindo uma exibição consistente e correta em todos os dispositivos. Anteriormente, essas páginas apresentavam problemas de layout devido a uma reorganização do bloco de mídia de informações do produto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39403>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>
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
* _ACP2E-2811_: O [Indexador de produtos de regras do catálogo de reindexação de nuvem] lança SQLSTATE[HY000]: Erro geral: o servidor MySQL de 2006 foi embora.
   * _Observação de correção_: o sistema agora lida corretamente com o valor &quot;batchCount&quot; personalizado no di.xml para o &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, evitando erros SQL como &quot;Erro geral: 2006 O servidor MySQL foi embora&quot; durante a reindexação do Indexador de produtos de regra de catálogo devido ao tamanho incorreto do lote em catálogos grandes
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3139_: a Regra de Vendas com o atributo Etapa de Qtd. de Desconto (Buy X) faz com que outras regras não sejam aplicadas
   * _Observação de correção_: a regra de preço do carrinho não cancela as regras aplicadas anteriormente se a quantidade do produto no carrinho não for suficiente para que a regra seja aplicada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_: Emitir regras de vendas com desconto de valor fixo e &quot;Desconto de Quantidade Máxima Aplicado a&quot;
   * _Observação de correção_: problema corrigido com desconto de regras de carrinho, quando um desconto de valor fixo está configurado para ser aplicado a uma quantidade limitada de produtos, o carrinho. Anteriormente, o valor &quot;Desconto de Qtd. Máxima Aplicado a&quot; era usado para calcular o preço do item atual no carrinho, não apenas para calcular o desconto da regra.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3349_: Regras do carrinho &quot;Desconto de valor fixo para carrinho inteiro&quot;  A ação aplica descontos incorretamente
   * _Observação de correção_: os códigos de cupom serão validados corretamente independentemente de maiúsculas ou minúsculas, quando usados na criação da ordem da área de administração. Antes, o código do cupom não era validado se não correspondesse à letra exata de maiúsculas e minúsculas do código de regra do carrinho configurado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: no back-end, os valores de armazenamento padrão para atributos de produto (em vez dos valores de administrador esperados)
   * _Observação de correção_: agora no back-end, valores de administrador são usados em vez dos valores de loja padrão para atributos de produto.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: a ação &quot;Desconto de valor fixo para carrinho inteiro&quot; das regras do carrinho aplica descontos incorretamente ao adicionar produtos do pacote
   * _Observação de correção_: as regras de carrinho de valor fixo não eram aplicadas corretamente a produtos agrupados. Agora, ao calcular o valor total do desconto, os produtos secundários agrupados são considerados, resultando no cálculo de desconto adequado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: Desconto Calculado Incorretamente de Regras de Preço do Carrinho
   * _Observação de correção_: os descontos de valor fixo agora estão sendo calculados corretamente. Antes da correção, os descontos de valor fixo não eram totalizados corretamente para os produtos agrupados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: as categorias aninhadas nas condições da regra não são exibidas
   * _Observação de correção_: correção de um problema quando categorias aninhadas na categoria de nível 3 não são mostradas nas regras de marketing para a condição de categoria
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit e uses_per_customer não são atualizados na Tabela salesrule_coupon
   * _Observação de correção_: a atualização de Usos por Cupom e Usos por Cliente na regra de preço do carrinho agora afetará os cupons gerados automaticamente existentes. Anteriormente, os novos valores afetavam somente os novos cupons
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: a regra de preço do carrinho não considera a categoria pai quando está usando a condição &quot;igual ou maior que&quot;.
   * _Observação de correção_: as regras de preço do carrinho agora consideram a categoria principal corretamente quando usada em condições avançadas
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: Cálculo de desconto inválido com prioridade
   * _Observação de correção_: no caso de um valor fixo aplicado ao tipo de desconto de carrinho inteiro, o valor não estava sendo calculado corretamente para itens de carrinho que já foram descontados por uma promoção anterior. Agora, os descontos são devidamente resumidos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3472_: [NUVEM] O cálculo de remessa não está considerando a regra do carrinho de compras
   * _Observação de correção_: antes da correção, uma regra de carrinho com condição de região não era aplicada de forma consistente. Após a correção, as regras do carrinho com condições de região são aplicadas corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_: a condição de sku da regra de carrinho está falhando para a fatura.
   * _Observação de correção_: o desconto no produto do pacote com preço dinâmico agora é refletido corretamente na fatura. Anteriormente, o desconto não era refletido na fatura.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_: valor de desconto incorreto quando várias regras de preço de carrinho são aplicadas simultaneamente a produtos com desconto/preço especial
   * _Observação de correção_: antes da correção, o valor fixo para regras de carrinho inteiro não era aplicado corretamente se mais de um estava sendo aplicado. Agora, as regras do carrinho de desconto de valor fixo estão sendo aplicadas corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

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
* _ACP2E-3383_: criação de entradas url_rewrite incorreta com vários armazenamentos em um grupo de armazenamento
   * _Observação de correção_: antes da correção, você só podia gerar regravações de URL em um nível de site ao editar um produto. Com a correção, uma nova configuração foi introduzida (Lojas > Configuração > Catálogo > Catálogo > Otimização do mecanismo de pesquisa, &quot;Escopo de regravação de URL do produto&quot; com opções &quot;Exibição da loja&quot;, &quot;Site&quot;) que permite gerar regravações de URL na exibição da loja ou no nível do site.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/2d627301>

### Pesquisar

* _AC-13053_: Obtendo &quot;Insira um termo de pesquisa e tente novamente.&quot; erro na página de pesquisa avançada na loja na versão 2.4.8-beta1
   * _Observação de correção_: o sistema agora exibe corretamente os resultados da pesquisa na página Pesquisa avançada quando um atributo de produto é definido como &quot;Não&quot;. Anteriormente, definir um atributo de produto como &quot;Não&quot; e executar uma pesquisa resultava em uma mensagem de erro, &quot;Insira um termo de pesquisa e tente novamente&quot;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-search depende de uma ramificação opensearch-php inexistente
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: tabela search_query quando de grande tamanho, tem grande impacto no front-end de tempo de carregamento
   * _Observação de correção_: tempo de carregamento de página da listagem de pesquisa aprimorado. Antes da correção, a página de listagem de pesquisa estava sendo adiada devido a uma consulta não otimizada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Segurança

* _AC-11855_: [Problema] Pop-up Paylater de Fonte Ausente CSP
   * _Observação de correção_: o sistema agora permite o carregamento da fonte &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sem violar a diretiva de Política de Segurança de Conteúdo, garantindo a exibição correta do Popup Paylater. Anteriormente, o carregamento da fonte era recusado devido a uma violação da diretiva da Política de segurança de conteúdo, causando problemas de exibição com o pop-up Paylater.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38624>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37401>
* _AC-12035_: [Problema] Atualização do texto DOM js.js reinterpretado como HTML
   * _Observação de correção_: usando innerText, isso evitará o risco de injeção de HTML, pois essas propriedades escapam automaticamente qualquer caractere especial do HTML no texto fornecido. Essa correção ajuda a evitar vulnerabilidades de criação de script entre sites (XSS), tratando a entrada como texto sem formatação em vez de HTML interpretado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_: ReCaptcha V2 é exibido incorretamente no check-out para o idioma alemão
   * _Observação de correção_: anteriormente, a recaptcha em endereço de email do check-out parecia sem estilo para idiomas com palavras longas, como alemão. Depois disso, o recaptcha tem a mesma aparência que todos os elementos recaptcha do resto das áreas.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha na administrador fazer logon não requer interação para alguns usuários
   * _Observação de correção_: ReCaptcha para administrador fazer logon é validada conforme o esperado
   * _Contribuição_ de código do GitHub: <https://github.com/magento/security-package/commit/8f64ab3c>

### Transporte

* _AC-10757_: [Problema] corrigido erro de digitação em rastreamento.phtml - funções JS renomeadas &quot;currier&quot; para &quot;porta-aviões&quot;
   * _Nota de correção_: O sistema agora usa corretamente o termo &quot;porta-aviões&quot; em vez do &quot;currier&quot; escrito incorretamente nas funções JavaScript manipulador usadas no solicitar rastreamento modelo, garantindo a nomenclatura adequada da função e a clareza do código. Anteriormente, o termo &quot;currier&quot; escrito incorretamente era usado, levando a uma possível confusão e inconsistência na base de código.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/34523>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/33414>
* _AC-11938_: UPS REST &quot;Um carregamento não pode ter um KGS/IN ou LBS/CM ou OZS/CM como sua unidade de medidas&quot;
   * _Observação de correção_: as taxas de UPS devem estar visíveis no check-out e na carrinho.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38618>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-13172_: [problema] Correto ortografia de variáveis para endereço do cliente
   * _Observação de correção_: o sistema agora soletre corretamente as variáveis para endereços do cliente, garantindo uma exibição precisa na área conta da frente. Anteriormente, a ortografia incorreta dessas variáveis podia cliente potencial a erros durante as revisões do código local.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/32817>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: Janela de rastreamento mostrando data de entrega esperada errada
   * _Observação de correção_: exibir a data de entrega correta para a operadora Fedex.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: As Taxas Da Tabela Ainda Estão Sendo Exibidas, Embora A Remessa Gratuita Seja Aplicada
   * _Observação de correção_: o método de envio de Taxa de Tabela agora é exibido mesmo se o Frete gratuito estiver disponível após a aplicação do cupom
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF teste AdminCreatingShippingLabelTest falhando devido a credenciais não adicionadas no Jenkins ambiente
   * _Observação de correção_: correção de teste mftf
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: API de Rastreamento FedEx não funciona com credenciais REST
   * _Observação de correção_: anteriormente, a integração FedEx não exigia chaves de API adicionais para a API de rastreamento. Agora, uma nova configuração foi adicionada para oferecer suporte a chaves de API de rastreamento.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Taxas Negociadas por FedEx da {Cloud] não retornadas em REST
   * _Observação de correção_: antes da correção, as taxas específicas da conta FedEx não eram enviadas na resposta, mesmo de acordo com a documentação do FedEx elas deveriam ter sido enviadas. Após a correção, as taxas específicas da conta são enviadas na resposta do alterando a solicitação do nosso lado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Preparo e visualização

* _ACP2E-3453_: Não é Possível Atualizar a Atualização Agendada ao Usar Atributo de Categoria Personalizada Exclusivo
   * _Observação de correção_: corrigido um problema onde a atualização agendada de uma categoria não era possível se a categoria tivesse um atributo exclusivo
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/078c387e>

### Direcionamento

* _AC-9432_: [] Permitir o uso de intervalos CIDR em manutenção permite lista
   * _Observação de correção_: o sistema agora suporta o uso de intervalos CIDR no modo de manutenção permite lista IP, permitindo que uma gama de endereços IP ignore o modo de manutenção. Anteriormente, o modo de manutenção permitia lista ip permitido apenas endereços IP individuais para ignorar o modo de manutenção.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/37943>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/30699>

### Imposto

* _AC-13295_: [Problema] Promoção de propriedade de construtor Feature/php8.1 wee graph ql
   * _Observação de_ correção: Substituir todas as propriedades com o construtor propriedade promoção em módulo ql gráfico de wee:
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39309>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: o Imposto Fixo sobre Produtos (FPT) não está funcionando com produtos configuráveis
   * _Observação de correção_: FPT para variações configuráveis do produto que funcionam corretamente.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>

### Teste estrutura

* _AC-11654_: Integração teste falha no testDbSchemaUpToDate devido ao tipo de coluna JSON
   * _Observação de_ correção: o sistema agora reconhece corretamente os tipos de colunaS JSON no banco de dados schema durante testes de integração, impedindo teste falhas devido a uma incompatibilidade entre o schema do banco de dados e as schema declarativas. Anteriormente, o sistema identificava incorretamente os tipos de coluna JSON como LONGTEXT na MariaDB, causando falha nos testes de integração.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [ortografia de] correção PHPDoc de problema
   * _Observação de correção_: o sistema reconhece corretamente os métodos obsoletos nas IDEs devido a uma correção ortográfica no PHPDoc. Anteriormente, um erro ortográfico no PHPDoc fazia com que as IDEs não reconhecessem determinados métodos como obsoletos.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/31399>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Verificando o comportamento com o carrinho de compras persistente após a sessão expirar
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13848_: Corrigir testes estáticos para habilitar o uso por extensões de 3d
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_: [Interno] A falha na aplicação de correção não é mostrada durante a execução ou nos logs
   * _Nota de correção_: &#39;-
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Observação de correção_: mftfs fixos
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/078c387e>

### Estrutura de interface

* _AC-12128_: vulnerabilidade de segurança Protótipo.js correção CVE-2020-27511
   * _Observação de correção_: O sistema foi atualizado para lidar com a vulnerabilidade de segurança CVE-2020-27511 no Protótipo.js 1.7.3, aumentando a segurança geral do sistema. Antes desta atualização, o sistema era suscetível a uma Negação de Serviço de Expressão Regular (ReDOS) por meio da remoção de tags HTML elaboradas.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less usa pub/prefixo para sourcemaps
   * __ Nota de correção: O sistema agora gera less/css sourcemaps sem o prefixo /pub para caminhos ao usar grunhido, eliminando a necessidade de uma solução alternativa na configuração do servidor web. Anteriormente, o uso do prefixo /pub nos caminhos de sourcemaps exigia que uma configuração específica no servidor web funcionasse corretamente.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38837>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38840>
* _AC-12432_: Campo de Componente da interface do usuário Arquivo
   * _Observação de correção_: O sistema valida corretamente o campo de arquivo em uma interface formulário de componente, permitindo que o formulário seja enviado sem erro quando um arquivo é selecionado. Anteriormente, o validação falhava mesmo quando um arquivo era selecionado, impedindo que o formulário fosse enviado.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38908>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [Formato] de data de edição aprimorado no console js: alternar de 12 horas para 24 horas fo...
   * _Observação de correção_: formato de data aprimorado no console js: alternar de 12 horas para 24 horas
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38983>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [Problema] adiciona geração de sourceMap para menos arquivos no modo de desenvolvedor
   * __ Observação de correção: o sistema agora gera mapas de origem para menos arquivos quando no modo de desenvolvedor, facilitando a identificação da fonte de um estilo. Anteriormente, identificar a fonte de um estilo era desafiador ao executar o sistema no modo de desenvolvedor com lado do servidor menos compilação.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/38982>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/38977>
* _AC-1306_: A conteúdo estática está implantando para módulos desativados
   * _Observação de correção_: o sistema agora exclui o CSS relacionado aos módulos desativados dos arquivos de saída CSS finais, garantindo que estilos desnecessários não sejam carregados. Anteriormente, o CSS relacionado aos módulos desativados estava incluído nos arquivos de saída finais de CSS, levando ao carregamento de estilos extras e desnecessários.
   * _Problema_ do GitHub: <https://github.com/magento/magento2/issues/24666>
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: Inconsistente Comportamento na classificação &quot;Fora de Stock&quot; com limite mínimo de Stock
   * _Observação de correção_: O sistema agora classifica corretamente os produtos no catálogo com base nos níveis de estoque, cumprindo o limite mínimo de Stock definido e movendo itens fora de estoque para a parte inferior do lista consistentemente. Anteriormente, o comportamento de classificação era inconsistente, com os itens nem sempre aparecendo nas solicitar corretas com base em seus níveis de estoque, e mudanças na classificação poderiam ocorrer imprevisíveis depois de salvar, atualizar ou modificar a categoria hierarquia.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Sugestão para o relatório de erros aprimorado para problemas de carregamento do require.js
   * _Observação de correção_: esta PR melhora a mensagem de erro quando o required js falha ao carregar um componente.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36761>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: erros de descontinuação do PHP 8.4 que causam falhas de compilação no 2.4-develop
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Problema] Não carregar contexto de bloco de back-end no front-end
   * _Observação de correção_: o sistema agora garante que o contexto do bloco de back-end não seja carregado no front-end, impedindo a criação de sessões de back-end desnecessárias e possíveis bloqueios de sessão. Anteriormente, o sistema carregava incorretamente o contexto do bloco de back-end no front-end, levando à criação de sessões de back-end e possíveis bloqueios de sessão.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37617>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: [Problema] Remover o resumo de revisão de scripts desnecessários
   * _Observação de correção_: o sistema agora otimiza o tempo de carregamento da página removendo scripts JavaScript desnecessários da seção de classificação, em vez de usar estilos CSS em linha para obter um código mais eficiente e legível. Anteriormente, o uso de scripts JavaScript para a seção de classificação podia retardar o tempo de carregamento da página.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37776>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: exceção ao verificar um saldo de cartão-presente quando Recaptcha está habilitado
   * _Observação de correção_: os usuários poderão buscar o saldo de um vale-presente na tela de exibição e edição do carrinho. Anteriormente, esses detalhes não eram exibidos quando o reCAPTCHA estava ativado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [ESCLARECIMENTO] Solicitação de Conformidade com o ADA
   * _Observação de correção_: o sistema agora garante a conformidade com o ADA, removendo propriedades CSS sem suporte e substituindo-as por outras com suporte no arquivo print.css. Anteriormente, o uso de propriedades CSS não compatíveis levava a navegador problemas de compatibilidade.
   * _Contribuição_ de código do GitHub: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Confusão na nuvem] biblioteca código em effect-drop.js do AC 2.4.4-p8
   * _Observação de correção_: o sistema agora implementa corretamente a biblioteca effect-drop.js, garantindo o funcionamento adequado dos efeitos da interface do usuário do jQuery. Anteriormente, a effect-drop.js biblioteca foi erroneamente substituída pela effect-clip.js biblioteca, causando possíveis problemas com efeitos interface jQuery.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: Cabeçalho do Site | Caracteres especiais quebrando a seção de boas-vindas do cliente
   * _Observação de correção_: após a correção, os caracteres especiais são mostrados corretamente na seção de boas-vindas do cliente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: a edição do Segmento do cliente falha com daterange
   * _Observação de correção_: é possível salvar o segmento do cliente com a condição de intervalo de datas, quando apenas uma das datas foi editada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>
