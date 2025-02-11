---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '8487'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.8-beta2)

## Destaques na v2.4.8-beta2

Os 30 destaques a seguir se aplicam à versão 2.4.8 do Magento Open Source.

### Braintree

* _BUNDLE-3400_: Remover LPMs sem Suporte
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _PACOTE-3401_: Marca de Pagamento Google
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _PACOTE-3402_: Marca de Pagamento Apple
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _PACOTE-3403_: retorno de chamada de envio pago do Google
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3404_: Pagar Mensagens Mais Tarde
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3405_: botão JS-SDK
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3406_: otimizar código na extensão do Braintree
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3407_: atualizar Braintree PHP e JS SDK
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _PACOTE-3408_: Itens de Linha (GooglePay)
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _PACOTE-3409_: Itens de Linha (Apple Pay)
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3420_: Rastreamento de Pacote
   * _Contribuição de código do GitHub_: <https://github.com/magento/ext-braintree/pull/208>

### Estrutura

* _AC-12012_: atualizar versão Nginx de 1.24 para 1.26
* _AC-12028_: adicionar compatibilidade com a versão mais recente do Composer 2.8 para 2.4.8 e 2.4.7
* _AC-12029_: verificar compatibilidade com o Verniz 7.6
* _AC-12970_: parte 2 da atualização do PHPUnit 10 - Remover descontinuações
   * _Observação de correção_: as dependências do phpunit/phpunit composer foram atualizadas para uma versão compatível - &quot;phpunit/phpunit&quot;:&quot;10.x&quot;
* _AC-13076_: atualizar todas as dependências js e npm com a versão mais recente disponível
   * _Observação de correção_: o suporte à versão do compositor era somente para a versão 2.2.x do compositor. Agora, o suporte também foi estendido para a versão 2.4.x.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/19844aa0>
* _AC-13077_: todas as extensões agrupadas e componentes integrados são compatíveis com o PHP 8.4
* _AC-13078_: todas as ferramentas do Adobe Commerce são compatíveis com o PHP 8.4
* _AC-13079_: todas as laminas/dependências de projetos do Adobe Commerce são compatíveis com o PHP 8.4
* _AC-13256_: fazer downgrade da dependência do TinyMCE da versão 7 para a versão 6.8.5
* _AC-13276_: as descontinuações do PHP 8.4 requerem alterações de quebra do Adobe Commerce
* _AC-8828_: definir agrupamento padrão como utf8mb4 para MySQL

### Outro

* _AC-12133_: o código principal do Adobe Commerce 2.4.8 é compatível com o PHP 8.4
* _AC-12972_: melhorias na qualidade principal de 2.4.8-beta2
* _AC-13038_: remover o PHP 8.1 do composer.json e todo o suporte relacionado
* _AC-13448_: fornecer patch de melhoria de desempenho de operações de preço de camada na versão 2.4.8
   * _Observação de correção_: o sistema agora permite atualizações em massa mais eficientes dos preços de camada sem causar problemas de desempenho ou falta de resposta do site ao usar o ponto de extremidade da API REST &quot;/V1/products/tier-price&quot;. Anteriormente, atualizar um grande número de preços usando esse endpoint podia resultar em problemas de desempenho e incapacidade de resposta do site.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_: remover todos os avisos de direitos autorais confidenciais do Adobe dos repositórios Magento Open Source
   * _Observação de correção_: todas as notificações de direitos autorais confidenciais da Adobe foram removidas dos repositórios de código aberto, garantindo que somente a forma reduzida de direitos autorais da Adobe seja usada. Anteriormente, alguns arquivos nos repositórios públicos continham avisos confidenciais de direitos autorais da Adobe, o que levou a escaladas da comunidade.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39493>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>

### Segurança

* _AC-10982_: [2FA] Integre-se com o Duo Web SDK para oferecer suporte ao Universal Prompt
   * _Nota de correção_: a ser definida

### Estrutura de teste

* _AC-9037_: capacidade de usar os direitos autorais do Adobe para o código-fonte do Adobe Commerce

### Estrutura da interface

* _AC-12944_: remover o TinyMCE 5 do adobe commerce

## Correção de problemas na v2.4.8-beta2

Corrigimos 159 problemas no código principal do Magento Open Source 2.4.8. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

* _ACP2E-3236_: falha na operação assíncrona quando o SKU está ausente da carga
   * _Observação de correção_: as operações assíncronas e de sincronização falharam anteriormente devido a erros de salvamento do produto se o SKU estiver ausente da carga. Após a correção, as operações de salvar rest api do produto assíncrono e síncrono falham com a mensagem de exceção relevante.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [NUVEM] Não é possível atualizar os Preços base usando a API REST (O valor de &#39;value_id&#39; em &#39;catalog_product_entity_decimal&#39; não é incrementado corretamente.)
   * _Observação de correção_: anteriormente para essa correção, quando rest api /rest/default/V1/products/base-price era chamado, a ID do incremento era aumentada incorretamente, deixando uma lacuna entre os valores. Após a correção, a ID do incremento é aumentada conforme esperado, de forma incremental. Além disso, o intervalo do campo value_id foi aumentado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_: os valores padrão não estão definidos para atributos de data e hora com produtos RestAPI
   * _Observação de correção_: os valores padrão agora são definidos corretamente para atributos de data, data e hora via RestAPI
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### APIs, carrinho e check-out

* _ACP2E-3343_: Erro 500 Crítico: Magento\Framework\Webapi\Exception Relacionado ao Cabeçalho HTTP Accept
   * _Observação de correção_: após a correção, não há nenhum problema com a especificação do cabeçalho &quot;Aceitar&quot;.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>

### Conta

* _AC-10886_: atualização da senha de administrador.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38352>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_: loop de redirecionamento quando a URL está em maiúsculas
   * _Observação de correção_: o sistema agora converte automaticamente caracteres em maiúsculas nas URLs para minúsculas, impedindo um loop de redirecionamento ao acessar a página inicial. Anteriormente, ter caracteres em maiúsculas no URL de base segura causava um loop de redirecionamento contínuo ao tentar acessar a página inicial.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38538>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38539>
* _AC-13000_: caixa de seleção Fazer logon como aceitação do cliente não traduzível
   * _Observação de correção_: o sistema agora permite que os campos &quot;Caixa de seleção Fazer logon como aceitação do cliente&quot; e &quot;Dica de ferramenta da caixa de seleção Fazer logon como cliente&quot; sejam definidos no escopo &quot;Exibição de loja&quot;, permitindo traduções para diferentes exibições de loja. Anteriormente, esses campos eram definidos somente no escopo &quot;Site&quot;, impedindo traduções para exibições de loja individuais.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/32329>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: depois de fazer logon, os produtos adicionados à lista de comparação como usuário convidado não ficam visíveis.
   * _Observação de correção_: os produtos adicionados à lista de comparação de produtos antes de fazer logon como cliente agora são preservados depois de fazer logon.
Anteriormente, após o logon, os produtos adicionados à lista de comparação como usuário convidado não estavam visíveis.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: a permissão de configuração de Países causa problemas nas configurações de endereço do cliente
   * _Observação de correção_: agora a seleção da configuração Permitir Países não influencia os países exibidos para fora do escopo especificado. Anteriormente, a configuração Permitir Países influenciava o atributo de endereço do cliente fora do escopo especificado
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Conta, APIs, GraphQL

* _ACP2E-3246_: API Do Cliente - Número De Falhas De Logon Não Pode Ser Redefinido Para 0 Após O Logon Bem-Sucedido
   * _Observação de correção_: agora o número da falha é redefinido para zero na tabela de entidades do cliente após o logon bem-sucedido do cliente pelos pontos de extremidade da API.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Conta, interface do administrador, B2B

* _ACP2E-3038_: Usuários administradores restritos nem sempre podem ver catálogos compartilhados personalizados
   * _Observação de correção_: os usuários administradores restritos agora podem exibir e gerenciar de forma consistente todos os clientes e todos os catálogos compartilhados aos quais os produtos estão atribuídos, desde que tenham acesso à loja específica. Anteriormente, um usuário administrador restrito com acesso a uma loja específica nem sempre podia ver todos os catálogos compartilhados aos quais os produtos eram atribuídos ou os clientes que não podiam ser salvos, resultando em inconsistências no sistema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>

### Interface do administrador

* _AC-10705_: [Problema] adicione verificação de permissão para o botão &quot;recarregar dados&quot;
   * _Observação de correção_: o sistema agora inclui uma verificação de permissão para o botão &quot;Recarregar Dados&quot;, garantindo que ele seja exibido e acessível somente a usuários com as permissões apropriadas. Anteriormente, o botão &quot;Recarregar dados&quot; estava visível e clicável para todos os usuários, resultando em uma página &quot;não permitido&quot; quando clicado por usuários sem as permissões necessárias.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38283>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38279>
* _AC-13131_: [Problema] Aviso de Correção: &quot;filtros&quot; de chave de matriz indefinida
   * _Observação de correção_: o sistema agora lida com cenários em que um novo usuário ainda não interagiu com marcadores, impedindo que um aviso de &quot;filtros&quot; de chave de matriz indefinido seja registrado. Anteriormente, esse aviso era registrado quando um novo usuário não interagia com marcadores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39013>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: arquivo csv de importação de produto com caracteres especiais falha devido a alterações de código no arquivo Validate.php
   * _Observação de correção_: o sistema agora valida e importa corretamente arquivos CSV de produtos que contêm caracteres especiais, permitindo uma transferência de dados bem-sucedida. Anteriormente, tentar importar um arquivo CSV de produto com caracteres especiais resultava em um erro, impedindo o processo de importação.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-7962_: nenhum link para remessa quando em pagamentos no check-out na exibição do telefone celular
   * _Observação de correção_: o sistema agora garante que os títulos/links de check-out &quot;Envio&quot; e &quot;Revisão e Pagamentos&quot; estejam sempre visíveis na parte superior da página na exibição móvel, permitindo que os usuários naveguem facilmente entre as etapas e façam as correções necessárias. Anteriormente, esses títulos/links estavam ocultos na exibição móvel, dificultando para os usuários saber sua etapa atual ou voltar às etapas anteriores.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36856>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: cliente Consulta comentários de remessa criados_em de comentários de remessa é retornado em fuso horário +0 não no fuso horário configurado de armazenamento
   * _Observação de correção_: o sistema agora exibe corretamente o campo &#39;created_at&#39; dos comentários de remessa no fuso horário configurado do cliente ao usar a consulta Pedidos do cliente. Anteriormente, o campo &quot;created_at&quot; era exibido no fuso horário +0, independentemente do fuso horário configurado pelo cliente.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36947>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_: o estado do endereço de entrega não é atualização automática
   * _Observação de correção_: antes da correção, a região do endereço para remessa (ou id de região) não estava sincronizada com as informações de cobrança do endereço. Agora, a região do endereço de entrega e a ID da região são atualizadas corretamente quando as informações de endereço de cobrança são alteradas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: o botão Redefinir não funciona em Adicionar/Editar usuário administrador
   * _Observação de correção_: anteriormente, o botão Redefinir não funcionava na página Adicionar/Editar Usuário Administrador. Agora, no painel Administrador, em Sistema -> Permissões -> Todos os usuários, o botão Redefinir funcionará corretamente na página Adicionar/Editar usuário administrador.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_: validação com falha para &quot;Quantidade Máxima Permitida no Carrinho de Compras&quot;
   * _Observação de correção_: anteriormente, quando colocávamos `Maximum Qty Allowed in Shopping Cart` vazio, não havia nenhuma exceção, embora um valor vazio não fosse aceito aqui. Depois que essa correção for aplicada, colocar uma string vazia gerará exceções e não permitirá salvar o produto.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problema na Interface do Usuário de Visualização do Pagebuilder] Os botões na coluna do Page Builder não estão alinhados corretamente
   * _Observação de correção_: os botões nas colunas do Page Builder agora estão alinhados corretamente. Anteriormente, eles estavam desalinhados nas colunas do Page Builder.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: o relatório Produtos Solicitados não está sendo exportado. Erro 404 em vez disso.
   * _Observação de correção_: a exportação de relatórios de produtos solicitados para CSV e XML agora funciona conforme esperado
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: Erro TinyMCE JS no console após a minificação de Js habilitada com o modo de produção
   * _Observação de correção_: anteriormente, ativar a minificação do JavaScript no modo de produção no painel de administração fazia com que erros do JavaScript relacionados ao TinyMCE 7 aparecessem no console do navegador, afetando a funcionalidade e a experiência do usuário. Agora, esse problema foi resolvido, garantindo que o TinyMCE 7 funcione sem problemas sem gerar erros, mesmo quando a minificação JS estiver ativada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Solicitação de alterações adicionais para concluir totalmente a correção ACP2E-3375
   * _Nota de correção_: &#39;-
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Interface do administrador, Métodos de pagamento/pagamento, Pedido

* _AC-13520_: Autorização de Transação Não Exibida na Guia Transação Após a Ordem do Botão Inteligente do PayPal
   * _Observação de correção_: o sistema agora exibe corretamente a autorização da transação na guia Transação depois que um pedido é feito usando o Botão Inteligente do PayPal. Anteriormente, a transação de autorização não aparecia na guia Transação após clicar no botão &quot;Autorizar&quot; e nenhuma nova transação do tipo &quot;Autorização&quot; era criada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Interface do administrador, preparo e visualização

* _ACP2E-3424_: [Nuvem] Remover o modelo com imagens ausentes faz com que pub/media seja excluído
   * _Observação de correção_: antes dessa correção, se o nome da imagem de visualização não estava presente em um modelo do pagebuilder, a pasta pub/media foi excluída. Após a correção, somente o modelo será excluído e a imagem de pré-visualização, se encontrada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/Relatórios

* _AC-9922_: Erro do Google Analytics CSP https://region1.analytics.google.com
   * _Observação de correção_: o sistema agora permite corretamente conexões com &#39;https://region1.analytics.google.com&#39; quando o Google Analytics está habilitado, impedindo erros de Política de Segurança de Conteúdo (CSP). Anteriormente, ativar o Google Analytics e visualizar o site da UE resultava em erros no console da CSP devido a uma recusa de conexão com &quot;https://region1.analytics.google.com&#39;&quot;.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37750>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3183_: o monitoramento do navegador NewRelic pelo script inlineJS causa erros de CSP
   * _Observação de correção_: os scripts de monitoramento do navegador NewRelic agora são inseridos pelo aplicativo, em vez do agente APM, para conformidade com a CSP (Política de Segurança de Conteúdo). Anteriormente, os scripts de monitoramento do navegador NewRelic inseridos pelo agente APM não eram compatíveis com o CSP e faziam com que os scripts não fossem executados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: as consultas INSERT para a tabela sales_bestsellers_aggregated_daily tornam-se lentas no projeto com grande volume de ordens de venda
   * _Observação de correção_: anteriormente, o relatório diário agregado de best-sellers demorava muito para ser gerado para um grande volume de pedidos feitos. Agora o relatório é gerado em tempo hábil.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: Relatórios de pedidos mostrando o símbolo de moeda errado
   * _Observação de correção_: o símbolo de moeda para valores de ordem no Relatório de Pedido foi retirado incorretamente de currency/options/base. Agora foi corrigido para usar moeda/opções/padrão para obter relatórios precisos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Nuvem] Cálculos Incorretos no Relatório de Uso do Cupom
   * _Observação de correção_: o total de vendas na grade do relatório de cupom agora é calculado com precisão, incorporando o &quot;Valor de Compensação de Imposto sobre Desconto&quot; e o &quot;Valor de Compensação de Imposto sobre Desconto de Remessa&quot;. Anteriormente, esses valores estavam ausentes no cálculo, gerando discrepâncias entre o total de vendas e os dados da ordem de venda.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: problemas com &quot;&lt;project_id>/var/tmp&quot; compartilhado
   * _Observação de correção_: os arquivos temporários do Analytics DataExport usarão o diretório tmp sys, que é mais adequado para acesso e alterações frequentes. Para evitar colisões, caso várias instâncias estejam em execução no mesmo servidor, o caminho tmp foi atualizado para usar a id exclusiva de uma instância
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/Relatórios, Cloud

* _ACP2E-3187_: a métrica no NR pode ser enganosa para transações em segundo plano- Acompanhamento de ACP2E-3067
   * _Observação de correção_: as transações em segundo plano (cron) usarão o nome do aplicativo New Relic definido nas configurações
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_: os produtos atribuídos ao catálogo compartilhado não são refletidos no front-end quando o índice parcial é executado
   * _Observação de correção_: os produtos atribuídos ao catálogo compartilhado pela API REST agora ficam visíveis na loja imediatamente após a conclusão da indexação parcial. Anteriormente, os Produtos eram visíveis somente após uma reindexação completa.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: sales_clean_quotes cron exclui cotações de ordens de compra ainda aprovadas
   * _Corrigir observação_: cotações usadas em ordens de compra agora não serão excluídas pelo trabalho cron sales_clean_quotes
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>

### Pacote

* _AC-10826_: Contagem de mensagens de erro de validação de pacote de vitrine maior que 1
   * _Observação de correção_: o sistema agora exibe apenas uma mensagem de erro de validação quando o botão &#39;Adicionar ao carrinho&#39; é clicado sem selecionar nenhuma opção de caixa de seleção para um produto agrupado. Anteriormente, o sistema exibia várias mensagens de erro de validação para cada caixa de seleção não selecionada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3ea26621>

### Carrinho e saída

* _AC-11914_: [Problema] Cálculo de CartFixed de regra de vendas: valor de desconto incorreto
   * _Observação de correção_: o sistema agora calcula corretamente o valor do desconto para regras de vendas com valores fixos de carrinho, garantindo que os descontos precisos sejam aplicados independentemente das alterações nos itens de carrinho. Anteriormente, o valor do desconto podia variar incorretamente quando os itens do carrinho eram alterados, às vezes resultando em descontos significativamente maiores do que o esperado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38694>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_: a caixa de seleção dos Termos e condições não permite o HTML na loja
   * _Observação de correção_: o sistema agora oferece suporte à formatação do HTML no texto da caixa de seleção &quot;Termos e Condições&quot; na vitrine eletrônica, permitindo uma personalização e legibilidade aprimoradas. Anteriormente, o texto da caixa de seleção era exibido em formato de texto sem formatação, ignorando as tags HTML usadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: a regra de preço do carrinho criada para o usuário conectado é aplicada incorretamente ao usuário não conectado
   * _Observação de correção_: o sistema agora remove corretamente a regra de preço do carrinho para usuários conectados quando eles são automaticamente desconectados devido à expiração do cookie, garantindo que o desconto não seja aplicado a usuários não conectados. Anteriormente, a regra de preço do carrinho ainda era aplicada mesmo quando o usuário estava desconectado, resultando em um desconto incorreto aplicado a usuários não conectados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38944>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [Problema] [RECURSO] Otimização de desempenho de carrinhos de compras grandes, evitando...
   * _Observação de correção_: o sistema agora otimiza o desempenho de grandes carrinhos de compras, evitando chamadas getActions duplicadas e melhorando a velocidade e a eficiência das operações de carrinhos de compras. Anteriormente, em um carrinho de compras com vários itens, a função getActions era chamada várias vezes, retardando o desempenho do sistema.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39292>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39290>
* _ACP2E-3176_: [Nuvem] para solicitar rapidamente uma grande quantidade de desempenho de SKU
   * _Observação de correção_: o desempenho do check-out foi aprimorado quando os atributos usados nas condições das regras de preço do carrinho não estão presentes para todos os produtos e quando o recurso MAP (Preço mínimo anunciado) está habilitado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: itens duplicados no carrinho
   * _Observação de correção_: o sistema agora processa corretamente várias solicitações paralelas para adicionar o mesmo produto ao carrinho em um único item de linha, impedindo a criação de itens de linha separados para o mesmo SKU. Anteriormente, fazer solicitações paralelas para adicionar o mesmo produto ao carrinho na loja resultava em vários itens de linha para o mesmo SKU.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: a confirmação do email da ordem de check-out é enviada para emails inseridos em Nome/Sobrenome
   * _Observação de correção_: a confirmação do email da ordem de check-out, que foi enviada anteriormente quando um padrão semelhante a um email foi inserido nos campos Nome e Sobrenome, não está mais sendo enviada.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: formulário de endereço de envio de check-out obter atualização com endereço errado
   * _Observação de correção_: shippingAddressFromData agora é salvo no armazenamento local por site. Anteriormente, um endereço do site errado podia ser preenchido automaticamente no formulário de endereço de entrega durante o check-out se um código de loja fosse usado no URL e o check-out fosse iniciado de vários sites durante a mesma sessão de convidado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_: Produto de Cartão Presente | A Mesclagem de Carrinhos está mesclando Cartões-presente
   * _Observação de correção_: os produtos de cartão-presente agora são mesclados corretamente no carrinho
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_: os dados de cotação existentes não são atualizados/não estão visíveis; em vez disso, crie um novo registro de cotação quando trigger_recollect = 1
   * _Observação de correção_: os itens do carrinho de compras do cliente não desaparecem mais como resultado da exclusão de um produto após sua adição ao carrinho.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catálogo

* _AC-11970_: impossível reordenar produtos configuráveis com uma opção personalizada marcada na caixa de seleção
   * _Observação de correção_: o sistema agora processa corretamente a reorganização de produtos configuráveis com uma única opção personalizada de caixa de seleção selecionada, permitindo a criação bem-sucedida da cesta. Anteriormente, tentar reordenar esses produtos resultava em um erro e impedia que itens fossem adicionados ao carrinho.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38736>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1d144bce>
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
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3103_: o RSS feed de Novos Produtos não é atualizado com novos produtos devido ao cache
   * _Observação de correção_: o feed Rss para Novos produtos agora é atualizado quando um produto é definido como novo e salvo
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_: [nuvem] Zoom com dois dedos e mover problema no dispositivo móvel real
   * _Observação de correção_: o sistema agora garante a funcionalidade de zoom de imagem consistente em dispositivos móveis, fornecendo uma experiência do usuário suave e previsível. Anteriormente, o recurso de zoom de imagem era inconsistente e repentinamente diminuía o zoom após um determinado ponto quando visualizado em um dispositivo móvel.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: quando cancelamos a atribuição de produtos do catálogo compartilhado, os produtos da lista de desejos não são apagados
   * _Observação de correção_: agora, nenhum item estará visível na lista de desejos se um produto não estiver disponível no catálogo compartilhado. Anteriormente, a página da lista de desejos exibia incorretamente uma contagem de &quot;1 item&quot;, mesmo quando nenhum item estava realmente disponível na lista de desejos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: Produtos relacionados Selecionar Tudo/Cancelar Seleção de Todos os Problemas
   * _Observação de correção_: anteriormente, os botões &quot;Selecionar tudo&quot;/&quot;Cancelar seleção de todos&quot; para produtos relacionados não funcionavam corretamente se um produto fosse selecionado manualmente. Após a correção, esses botões agora funcionam de forma consistente, mesmo após a seleção manual, garantindo que todos os produtos sejam selecionados ou não corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Nuvem] Tradução de email de alerta do Stock para o idioma errado
   * _Observação de correção_: ao enviar Alertas de Ações/Preços para um site com várias exibições de loja usando diferentes idiomas, o idioma para a exibição de loja em que o alerta foi criado será usado no email.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: as Categorias Desabilitadas não estão mais com seus nomes esmaecidos na árvore de categorias
   * _Observação de correção_: anteriormente, as categorias desabilitadas não estavam esmaecidas na árvore de categorias. Agora, eles são exibidos com um efeito cinza.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: o carregamento do formulário de edição de produto configurável causa tempo limite e esgotamento de memória
   * _Observação de correção_: antes da correção, as variações de produto configuráveis eram construídas com base em todas as combinações de opções de atributos possíveis. Nos casos em que os atributos tinham muitas opções, isso resultava em uma operação demorada e que consumia recursos. Agora, as variações de produtos configuráveis são construídas com base em atributos de produtos secundários existentes. Isso resulta em muito menos cálculos - o que resulta em uma melhor utilização dos recursos.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama não carrega o vídeo corretamente ao usar Amostras e a opção é pré-selecionada via URL
   * _Observação de correção_: os vídeos de produtos serão renderizados corretamente na página de detalhes do produto configurável, se a URL contiver opções selecionadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: o Widget de carrossel do PageBuilder mostra produtos que não correspondem a condições
   * _Observação de correção_: a lista de produtos usada em widgets agora respeita a condição de categoria
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: Erro de Validação Disparado para Todos os Produtos do Grupo Quando Uma Quantidade É Inválida
   * _Observação de correção_: agora, o erro de validação é disparado corretamente para todos os produtos do grupo quando um produto tem uma quantidade inválida, o que não acontecia anteriormente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_: as tabelas Temporárias de Indexadores não serão limpas se o processo for encerrado
   * _Observação de correção_: as tabelas temporárias do indexador CatalogRule agora são limpas se o processo do indexador for encerrado
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] Falha no teste de unidade principal em 2.4.7-p3
   * _Observação de correção_: as notas de versão para este teste não são necessárias, pois é uma melhoria de Teste de unidade.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catálogo, Conteúdo

* _ACP2E-3063_: o Cache da [Nuvem] não está sendo invalidado.
   * _Observação de correção_: anteriormente, ao salvar uma página do CMS com um layout de design atualizado, ela não refletia adequadamente no front-end. Depois que essa correção for aplicada, o layout de design apropriado estará visível no front-end quando alterarmos o layout de design e salvarmos a página do CMS.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Nuvem] Categorias Âncora/Não Âncora Revertidas no Widget de Conteúdo
   * _Observação de correção_: anteriormente, quando selecionávamos Exibir em -> Categorias de âncora, mostrava todas as categorias que não refletiam a relação pai-filho entre a âncora e a não âncora. Depois que essa correção for aplicada, Exibir em -> Categorias de âncora exibirá apenas Categorias de âncora (selecionáveis) e Exibir em -> Categorias não âncora exibirá Categorias não âncora (selecionáveis)
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Categorias que não funcionam com widgets
   * _Observação de correção_: anteriormente, se salvássemos o bloco CMS para categorias de âncora/não âncora diferentes, ele não funcionaria para as categorias secundárias quando ele fosse exibido no front-end. Depois que essa correção for aplicada, o bloco será mostrado no front-end para categorias diferentes.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>

### Catálogo, GraphQL

* _ACP2E-3312_: os Preços de Camada retornam valores incorretos nos produtos GraphQL (em comparação com a Loja)
   * _Observação de correção_: após a correção, os preços de camada do produto retornados para solicitações graphql têm o preço por um item.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>

### Catálogo, Pesquisa

* _ACP2E-3345_: Erro de Tipo ao criar objeto: Exceção Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor
   * _Observação de correção_: após a correção, uma instância da classe Magento\CatalogSearch\Model\Indexer\Fulltext pode ser criada sem especificar $data.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: Problema de [NUVEM] com Produtos não estão visíveis no Front-end após salvar no Administrador do Magento
   * _Observação de correção_: após a correção, os produtos configuráveis que têm produtos derivados com nomes compridos não serão perdidos na loja.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Conteúdo

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
* _ACP2E-3122_: [NUVEM] O botão Carregar imagem não funciona
   * _Observação de correção_: antes do botão Carregar imagem para o banner e controle deslizante do PageBuilder não funcionava como esperado e agora, ao pressioná-lo, o gerenciador de arquivos local é aberto para selecionar a imagem desejada para carregamento.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Nuvem] - O controle deslizante do CMS não reflete as alterações mais recentes
   * _Observação de correção_: o problema foi corrigido, garantindo que a lista de controle deslizante fosse atualizada enquanto o evento de gravação era acionado na tela de edição do slide. Anteriormente, ela estava acionando e causando o problema.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Ocorre um erro na página CSM quando blocos CMS são inseridos usando o construtor de páginas em determinada ordem
   * _Observação de correção_: anteriormente, em algumas versões do PHP e do OS (Linux), a renderização de blocos que referenciavam outros blocos cms por meio do PageBuilder falharia com &quot;Ocorreu um erro desconhecido. Tente novamente.&quot;. Agora, o conteúdo dos blocos cms é renderizado corretamente dentro de um conteúdo controlado pelo PageBuilder.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3430_: Últimas atualizações de segurança com tamanho de fonte ausente no TinyMCE 7
   * _Observação de correção_: os seletores de tamanho de fonte e família de fontes agora estão disponíveis no editor do WYSIWYG. Antes dessa correção, com o TinyMCE 7, eles não estavam disponíveis na interface do editor.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### Cliente/ Clientes

* _AC-8499_: o campo de texto Região não é redefinido quando a lista suspensa do país é alterada
   * _Observação de correção_: o sistema agora redefine o campo de texto da região quando o país é alterado no menu suspenso, garantindo que os valores anteriores não persistam. Anteriormente, alterar o país na lista suspensa não redefinia o campo de região, fazendo com que o último valor salvo fosse preservado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: a exclusão de cliente não limpa todos os dados de sessão do navegador na loja para clientes conectados e excluídos
   * _Observação de correção_: excluir um cliente agora limpa todos os dados de sessão do navegador da loja para clientes conectados e excluídos conforme esperado. O comprador pode continuar comprando e o navegador trata a sessão como uma sessão de convidado. Anteriormente, quando a conta do cliente de um comprador conectado era excluída do Administrador, o navegador do comprador exibia erros do JavaScript.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>

### Estrutura

* _AC-10738_: a configuração de verniz não exclui todos os parâmetros de marketing
   * _Observação de correção_: o sistema agora exclui corretamente todos os parâmetros de marketing comuns na configuração de verniz, garantindo um rastreamento e análise precisos. Anteriormente, determinados parâmetros de marketing, como gad_source, srsltid e msclkid, não eram excluídos, resultando em possíveis imprecisões na coleta de dados.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38298>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39188>
* _AC-11592_: [Problema] Permitir apenas preferências válidas durante a configuração:di:compilação
   * _Observação de correção_: o sistema agora lança um erro durante o comando setup:di:compile se uma preferência for criada para uma classe que não existe ou que está especificamente excluída, garantindo que apenas preferências válidas sejam permitidas. Anteriormente, esses cenários falhavam silenciosamente, possivelmente inutilizando todos os plug-ins associados às classes originais.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38517>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/33161>
* _AC-11809_: [Problema] Transmitir atributos personalizados para o link atual via XML
   * _Observação de correção_: o sistema agora permite que atributos personalizados sejam passados para o link atual via XML, garantindo que esses atributos sejam exibidos corretamente mesmo quando o link for a página atual. Anteriormente, os atributos personalizados não eram exibidos para o link da página atual porque o método getAttributesHtml() não estava sendo usado para o link atual.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38500>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/30070>
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
* _AC-12857_: PHP 8.2.15 removeu extensão FTP
   * _Observação de correção_: o sistema agora inclui a extensão FTP como uma dependência no arquivo composer.json, garantindo a configuração bem-sucedida das importações de CSV via FTP. Anteriormente, um erro era gerado ao tentar configurar importações de CSV via FTP porque a extensão FTP estava ausente no pacote PHP.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39083>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_: capacidade de definir Área para comando CLI dev:di:info
   * _Observação de correção_: o sistema agora permite que os desenvolvedores definam uma área para o comando CLI dev:di:info, aprimorando o processo de desenvolvimento e depuração. Anteriormente, esse comando só podia exibir informações da área GLOBAL.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38758>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38759>
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
* _AC-8662_: [Problema] Melhore o log de erros do CRON
   * _Observação de correção_: o sistema agora captura e registra em log STDERR e STDOUT para processos CRN, fornecendo informações de diagnóstico valiosas em cenários em que os processos CRN falham. Anteriormente, qualquer mensagem de erro nos processos cron não era registrada, e STDERR e STDOUT para grupos cron em execução em processos separados eram perdidos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37453>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_: a modificação do comprimento da coluna via db_schema.xml não funciona no caso de chaves estrangeiras
   * _Corrigir observação_: modificar a coluna com chave estrangeira por meio de esquema declarativo agora não gera erros com MariaDB
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: Alguns dos registros de relações são salvos no banco de dados quando o registro de pedido é salvo
   * _Observação de correção_: antes que as consultas UPDATE desnecessárias fossem acionadas, elas poderiam afetar o desempenho. Após a correção, as consultas UPDATE desnecessárias foram eliminadas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [NUVEM] No admin, há muitos erros de javascript no console
   * _Observação de correção_: anteriormente, no painel de administração, havia muitos erros de javascript no console. Agora, no painel de administração, não haverá erros de JavaScript no console e todas as funções padrão do JavaScript serão executadas com êxito sem problemas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: a mensagem da fila foi excluída
   * _Observação de correção_: as mensagens da fila agora estão sendo apagadas corretamente. Antes da correção, considerando que o sistema de fila SQL estava sendo usado, novas mensagens poderiam ter sido excluídas se a mensagem da fila de limpeza estivesse sendo executada ao mesmo tempo.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Estrutura, Estrutura da interface

* _ACP2E-3324_: possibilidade de substituir o valor de configuração mesmo se ele estiver bloqueado
   * _Observação de correção_: antes dessa correção, a configuração de design não podia ser definida por meio do comando bin/magento config:set, e os valores bloqueados podiam ser alterados por manipulação do formulário que os exibia. Após a correção, os valores bloqueados definidos na cli com o — lock-env ou o — lock-conf não poderão mais ser atualizados.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_: as traduções dos atributos de retorno do cliente não são refletidas na API do GraphQL para o respectivo StoreView
   * _Observação de correção_: as traduções dos atributos de retorno do cliente são refletidas na API do GraphQL para o respectivo StoreView.
Anteriormente, os atributos de Retorno do cliente para o respectivo StoreView não eram refletidos na API do GraphQL.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_: [Problema na Nuvem] com Autenticação de Usuário e Acesso a Token entre Sites na Configuração de Vários Sites
   * _Observação de correção_: as consultas de informações do cliente e do carrinho do GraphQl na configuração de vários sites verificam se o cliente está em um site não padrão.
Anteriormente, a consulta funcionava sem verificar se o cliente existe em um site não padrão na configuração de vários sites.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
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

### GraphQL, Pesquisar

* _ACP2E-948_: consulta GraphQL da lista de produtos limitada a total_count apenas 10.000 produtos
   * _Observação de correção_: após a correção, o resultado da pesquisa não fica limitado a 10.000 produtos; será possível obter todos os produtos que correspondam aos critérios da pesquisa, mesmo que a contagem seja superior a 10.000.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, Estrutura de teste

* _ACP2E-3363_: falha no Teste de Integração do Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Nota de correção_: &#39;-
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importar/exportar

* _ACP2E-3172_: botão Importar ausente
   * _Observação de correção_: resolva o problema que falta no botão Importar após as verificações de dados com registros corretos e incorretos no CSV. Anteriormente, o botão Importar não era exibido após as verificações de dados com registros corretos e incorretos no CSV.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: o endereço do cliente exportado não pode ser importado
   * _Observação de correção_: a importação do endereço do cliente continuará conforme esperado. Anteriormente, um arquivo de importação de endereço de cliente não passaria na validação se Compartilhar contas de cliente = Global, e há dois sites em que o site padrão tem uma lista de países restrita, e o endereço que está sendo importado é de outro site em que os países permitidos são diferentes
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Nuvem] A quantidade incorreta no arquivo CSV não deu erro
   * _Observação de correção_: agora a importação de fontes de estoque lançará um erro de validação para valores não numéricos na coluna de quantidade. Anteriormente, a importação de origens de estoque com valor não numérico na coluna de quantidade resultava na definição da quantidade como 0.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_: a exportação de produtos provoca OOM mesmo com limite de memória 4G
   * _Observação de correção_: antes dessa correção, a exportação do produto falhava se os atributos do produto tivessem milhares de valores de opção, mesmo com memória 4G disponível. Após essa correção, a exportação do produto deve concluir a exportação do arquivo csv.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Importação/exportação, desempenho

* _ACP2E-3476_: [Nuvem] O tempo de importação do produto aumentou significativamente
   * _Observação de correção_: antes da correção, a importação de produtos do catálogo com mais de 10.000 entradas tinha uma degradação de tempo significativa. Após a correção, a importação do produto de catálogo é executada em tempo hábil.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/87d012e5>

### Instalar e administrar

* _AC-13242_: falha na atualização do Magento no MariaDB 11.4 + 2.4.8-beta1
   * _Observação de correção_: a atualização deve ter ocorrido sem nenhum erro.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7b336d0a>

### Inventário / MSI

* _ACP2E-3335_: não é possível enviar o pedido quando o repositório de retirada MSI está habilitado
   * _Observação de correção_: melhor desempenho de estoque ao criar remessa no caso de muitas fontes com retirada na loja
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: a reindexação do Cron falha ao atualizar a disponibilidade do produto no front-end
   * _Observação de correção_: anteriormente, os produtos permaneciam indisponíveis no front-end após a atualização do status do backorder por meio da API REST. Agora, depois de atualizar o status do backorder por meio da API REST, os produtos são mostrados como em estoque.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: a adição de imagens ao configurável não funciona quando o MSI está habilitado.
   * _Observação de correção_: o carregamento de imagem para o produto configurável agora funcionará como esperado quando o módulo de estoque for usado. Anteriormente, o upload da imagem não funcionava
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/fdf409aa>

### Inventário / MSI, pesquisa

* _ACP2E-3413_: todos os produtos são indexados com [is_out_of_stock] = 1 quando o SKU não está definido como um atributo pesquisável
   * _Observação de correção_: após a correção, o &quot;is_out_of_stock&quot; no índice de pesquisa do catálogo está correto, mesmo quando o SKU não é pesquisável.
   * _Contribuição de código do GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>

### Pedido

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

* _ACP2E-3233_: o administrador ainda pode fazer o pedido mesmo sem a forma de pagamento
   * _Observação de correção_: anteriormente, o comerciante podia fazer pedidos pelo painel de administração sem selecionar um método de pagamento. Agora, o comerciante precisa de um método de pagamento para continuar com a realização de um pedido.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Outras ferramentas de desenvolvedor

* _AC-12731_: problemas de CSP combinados com dev/css/use_css_critical_path
   * _Observação de correção_: o sistema agora carrega corretamente os arquivos CSS de forma assíncrona nas páginas de check-out, mesmo quando a configuração &quot;dev/css/use_css_critical_path&quot; está habilitada, garantindo que essas páginas sejam renderizadas com os estilos CSS adequados. Anteriormente, uma Política de segurança de conteúdo (CSP) restrita impedia a execução do JavaScript em linha, o que fazia com que os arquivos CSS não fossem carregados conforme esperado.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39020>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: usando o tipo virtual para configurar o plug-in, o método interceptor não pode ser gerado corretamente no comando setup:di:compile
   * _Observação de correção_: o sistema agora gera corretamente métodos interceptores ao usar um tipo virtual para configurar um plug-in, garantindo resultados consistentes, sejam pré-compilados ou compilados em tempo de execução. Anteriormente, o sistema gerava resultados incorretos quando pré-compilado em comparação à compilação em tempo de execução.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/33980>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38141>

### Pagamentos

* _ACP2E-3143_: reembolso de pedido do PayPal resulta em memorando de crédito duplicado
   * _Observação de correção_: correção de um problema de simultaneidade de avisos de crédito criados pelo IPN para o serviço de pagamento do PayPal.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: a regra de preço do carrinho não funciona para Paypal
   * _Observação de correção_: o valor correto é mostrado no PayPal quando o desconto é aplicado pelo método de pagamento
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [Nuvem] Usuários com uma função específica não podem fazer logon
   * _Corrigir observação_: o usuário administrador com função que contém somente acesso à Seção do PayPal agora pode fazer logon sem erros
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/66dea0de>

### Desempenho

* _AC-11932_: Problema de Configurações de Atributo de Produto Padrão
   * _Observação de correção_: o sistema agora permite que os usuários desmarquem uma opção padrão para um atributo de produto, garantindo que o atributo nem sempre tenha um conjunto padrão. Anteriormente, uma vez que um padrão era definido para um atributo de produto, não havia como desmarcá-lo, resultando no atributo sempre ter um conjunto padrão.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38703>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_: suporte para CommandLoaderInterface do Symfony na CLI do Magento
   * _Observação de correção_: essa alteração reduz o tempo de inicialização do aplicativo Magento CLI ao permitir a inicialização adiada de comandos até que eles sejam necessários.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/29266>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/29355>

### Produto

* _AC-13173_: [Problema] Corrigir erro de digitação no bloco PHPDoc
   * _Observação de correção_: o sistema agora remove corretamente uma variável referenciada desconhecida no PHPDoc para a declaração de variável $helper, melhorando a clareza e a precisão do código. Anteriormente, essa variável referenciada desconhecida no PHPDoc estava causando confusão e possíveis imprecisões no código.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38961>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problema] Corrigido o pacote corrompido e o layout de páginas de produto baixáveis no Magento >= 2.4.7
   * _Observação de correção_: o layout das páginas de produto agrupadas e baixáveis foi corrigido, garantindo uma exibição consistente e correta em todos os dispositivos. Anteriormente, essas páginas apresentavam problemas de layout devido a uma reorganização do bloco de mídia de informações do produto.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/39403>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Promoção

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
* _ACP2E-3498_: valor de desconto incorreto quando várias regras de preço de carrinho são aplicadas simultaneamente a produtos com desconto/preço especial
   * _Observação de correção_: antes da correção, o valor fixo para regras de carrinho inteiro não era aplicado corretamente se mais de um estava sendo aplicado. Agora, as regras do carrinho de desconto de valor fixo estão sendo aplicadas corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

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

* _ACP2E-3273_: ReCaptcha V2 é exibido incorretamente no check-out para o idioma alemão
   * _Observação de correção_: anteriormente, a recaptcha em endereço de email do check-out parecia sem estilo para idiomas com palavras longas, como alemão. Depois disso, o recaptcha tem a mesma aparência que todos os elementos recaptcha do resto das áreas.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7377de59>

### Envio

* _ACP2E-3340_: API de Rastreamento FedEx não funciona com credenciais REST
   * _Observação de correção_: anteriormente, a integração FedEx não exigia chaves de API adicionais para a API de rastreamento. Agora, uma nova configuração foi adicionada para oferecer suporte a chaves de API de rastreamento.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Taxas Negociadas por FedEx da {Cloud] não retornadas em REST
   * _Observação de correção_: antes da correção, as taxas específicas da conta FedEx não eram enviadas na resposta, mesmo de acordo com a documentação do FedEx elas deveriam ter sido enviadas. Após a correção, as taxas específicas da conta são enviadas na resposta do alterando a solicitação do nosso lado.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Preparo e visualização

* _ACP2E-3453_: Não é Possível Atualizar a Atualização Agendada ao Usar Atributo de Categoria Personalizada Exclusivo
   * _Observação de correção_: corrigido um problema onde a atualização agendada de uma categoria não era possível se a categoria tivesse um atributo exclusivo
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Imposto

* _ACP2E-3193_: o Imposto Fixo sobre Produtos (FPT) não está funcionando com produtos configuráveis
   * _Observação de correção_: FPT para variações de produtos configuráveis funcionando corretamente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Estrutura de teste

* _AC-13362_: [Problema] correção ortográfica do PHPDoc
   * _Observação de correção_: o sistema agora reconhece corretamente os métodos obsoletos nos IDEs devido a uma correção ortográfica no PHPDoc. Anteriormente, um erro de ortografia no PHPDoc fazia com que os IDEs não reconhecessem determinados métodos como obsoletos.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/31399>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Verificando o comportamento com o carrinho de compras persistente após a sessão expirar
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Nota de correção_: mftfs corrigidos
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Estrutura da interface

* _AC-12432_: Campo De Arquivo Do Componente Da Interface Do Usuário
   * _Observação de correção_: o sistema agora valida corretamente o campo de arquivo em um formulário de componente da interface do usuário, permitindo que o formulário seja enviado sem erros quando um arquivo for selecionado. Anteriormente, a validação falhava mesmo quando um arquivo era selecionado, impedindo o envio do formulário.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38908>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [Problema] Formato de data aprimorado no console js: alternar de 12 horas para 24 horas para...
   * _Observação de correção_: formato de data aprimorado no console js: alternar de 12 horas para 24 horas
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38983>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [Problema] adicione a geração de sourceMap para menos arquivos no modo de desenvolvedor
   * _Observação de correção_: o sistema agora gera mapas de origem para menos arquivos quando está no modo de desenvolvedor, facilitando a identificação da origem de um estilo. Anteriormente, identificar a origem de um estilo era um desafio ao executar o sistema no modo de desenvolvedor com menos compilação no lado do servidor.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/38982>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38977>
* _AC-13459_: Comportamento Inconsistente na Classificação &quot;Fora de Estoque&quot; com Limite Mínimo de Estoque
   * _Observação de correção_: o sistema agora classifica corretamente os produtos no catálogo com base nos níveis de estoque, seguindo o Limite de Estoque Mínimo definido e movendo os itens esgotados para o final da lista de forma consistente. Anteriormente, o comportamento de classificação era inconsistente, com itens nem sempre aparecendo na ordem correta com base em seus níveis de estoque, e as alterações na classificação podiam ocorrer de forma imprevisível após salvar, atualizar ou modificar a hierarquia de categorias.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Sugestão para o relatório de erros aprimorado para problemas de carregamento do require.js
   * _Observação de correção_: esta PR melhora a mensagem de erro quando o required js falha ao carregar um componente.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/36761>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [Problema] Remover o resumo de revisão de scripts desnecessários
   * _Observação de correção_: o sistema agora otimiza o tempo de carregamento da página removendo scripts JavaScript desnecessários da seção de classificação, em vez de usar estilos CSS em linha para obter um código mais eficiente e legível. Anteriormente, o uso de scripts JavaScript para a seção de classificação podia retardar o tempo de carregamento da página.
   * _Problema do GitHub_: <https://github.com/magento/magento2/issues/37776>
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: Cabeçalho do Site | Caracteres especiais quebrando a seção de boas-vindas do cliente
   * _Observação de correção_: após a correção, os caracteres especiais são mostrados corretamente na seção de boas-vindas do cliente.
   * _Contribuição de código do GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
