---
source-git-commit: 151272eed6c4bb2e1c2e5138a5c8a3a7e7bd8fe6
workflow-type: tm+mt
source-wordcount: '6079'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.9-alpha3)

## Correção de problemas na v2.4.9-alpha3

Corrigimos 129 problemas no código principal Magento Open Source 2.4.9-alpha3. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

#### Erro de endereço de cobrança ausente no painel do administrador ao criar o pedido por meio da API REST com apenas informações de pagamento

Correção de um problema em que os pedidos podiam ser criados por meio da API sem um endereço de cobrança, causando falhas no painel do administrador.
Agora, os pedidos sem um endereço de faturamento são restritos e não são mais criados.

_AC-14049 - [Problema do GitHub](https://github.com/magento/magento2/issues/39651) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problema de adição de produto ao carrinho na API Rest

Correção de um problema em que os produtos não atribuídos a um site específico ainda podiam ser adicionados ao carrinho e comprados.
Agora, uma mensagem de erro é exibida: &quot;O produto que você está tentando adicionar não está disponível&quot;.

_AC-15054 - [Problema do GitHub](https://github.com/magento/magento2/issues/40029) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f5cc09fc)_

#### O Rótulo De Opção De Atributo É Substituído Ao Atualizar Rótulos De Loja

Correção de um problema em que a atualização de um atributo de produto de multisseleção por meio da API REST substituiria todos os store_labels, removendo os rótulos específicos da loja existente.
Agora, ao atualizar o rótulo da visualização de loja padrão, o Magento mescla os rótulos fornecidos com os existentes, em vez de substituí-los totalmente.
Isso garante que os rótulos específicos da loja para outras exibições da loja permaneçam intactos após as atualizações.

_AC-15208 - [Problema do GitHub](https://github.com/magento/magento2/issues/40093) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### O ponto de extremidade da API REST export-stock-salable-qty retorna itens incorretos total_count

Correção de um problema de paginação na API de quantidade comercializável de estoque da exportação de estoque em que total_count estava incorretamente limitado ao tamanho da página. Anteriormente, ao usar o endpoint /rest/all/V1/inventory/export-stock-salable-qty/website/base com parâmetros de paginação como page_size=5, o campo total_count na resposta retornaria 5 em vez do número total real de produtos que correspondem aos critérios de pesquisa. Após essa correção, o campo total_count agora reflete corretamente o número total de produtos disponíveis, independentemente do parâmetro page_size, garantindo um comportamento de paginação consistente em todos os endpoints da API REST do Magento.

_ACP2E-4086 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### O invasor pode usar a solicitação POST usando a API REST e pode enviar a carga RCE

REST APIs V1/guest-carts/&lt;cartId>/items/ e V1/carts/mine/items/ agora valida &quot;product_options.extension_attributes.custom_options.*.option_id&quot; será option_id válida no SKU do item de carrinho. Anteriormente, essa opção era processada e salva no banco de dados sem qualquer validação.

_ACP2E-4138 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Conta

#### [Problema] Remoção de espaçamento desnecessário na grade de back-end

O sistema agora remove o espaçamento desnecessário na grade do backend. Quando há itens selecionados.

_AC-11579 - [Problema do GitHub](https://github.com/magento/magento2/issues/38502) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32622)_

#### Não é possível limpar o comentário do item da lista de desejos por meio da mutação do GraphQL `updateProductsInWishlist`

Correção de um problema em que os comentários da lista de desejos não eram atualizados por meio de mutações do GraphQL.
Agora, os comentários são atualizados corretamente e refletidos na resposta da API e na loja.

_AC-14682 - [Problema do GitHub](https://github.com/magento/magento2/issues/39911) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Mostrar configuração de prefixo/sufixo ignorada quando definida como Não

Correção de um problema em que o prefixo/sufixo do nome do cliente continuava a ser exibido em pedidos mesmo quando desativado na configuração.
Agora, os valores de prefixo/sufixo são removidos dos detalhes do pedido com base na configuração.

_AC-15074 - [Problema do GitHub](https://github.com/magento/magento2/issues/40036) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Registro de conta de cliente da loja: o formato do endereço de email está sendo convertido com um formato de domínio diferente

Esse erro solucionou um problema em que os emails de clientes com caracteres especiais no domínio (por exemplo, tec55241@adòbe.com) eram convertidos automaticamente para o formato punycode (tec55241@xn--adbe-mqa.com).
No Magento 2.4.9-alpha3, a correção garante que essas IDs de email permaneçam inalteradas e válidas, evitando erros de delivery.

_AC-15177 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Mensagens de validação ausentes (image-error) no formulário de registro

Correção de um problema em que os campos obrigatórios na página de criação da conta do cliente não mostravam mensagens de validação quando deixados em branco.
Agora, as mensagens de erro apropriadas são exibidas para todos os campos vazios ou incorretos.

_AC-15185 - [Problema do GitHub](https://github.com/magento/magento2/issues/40076) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problema após o logon no magento 2.4.8-p1

Correção do problema no Magento 2.4.8-p1 em que o link &quot;Criar uma conta&quot; ainda estava visível na página inicial após o logon.
Agora, o link fica oculto corretamente após o logon, de forma consistente com outras páginas.

_AC-15292 - [Problema do GitHub](https://github.com/magento/magento2/issues/40120)_

### Interface do administrador

#### [Problema] para substituir o escape obsoleto

Esta PR remove a getEscaper() obsoleta e a adiciona por injeção do construtor

_AC-15132 - [Problema do GitHub](https://github.com/magento/magento2/issues/40062) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38135)_

#### Categoria de produto de sobreposição de mensagem de boas-vindas na exibição móvel.

Correção de um problema na interface do usuário em que o nome de boas-vindas se sobrepunha às categorias de produto na exibição móvel, bloqueando cliques.
Agora, as categorias são totalmente visíveis e clicáveis, sem problemas de sobreposição.

_AC-15166 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### &quot;Não é possível resolver as entradas do parâmetro reCAPTCHA&quot; no exception.log para o Painel de Administração do Google reCAPTCHA

Um erro de reCaptcha no arquivo `var/log/exception.log` para o logon de Administrador do reCAPTCHA do Google V3 foi resolvido e nenhuma mensagem de erro foi registrada. Anteriormente, o seguinte erro era gerado a cada poucos segundos quando um usuário administrador definia as configurações de **Configuração** > **Segurança** > **Painel de Administração do Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problema do GitHub](https://github.com/magento/magento2/issues/34975) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contribuição de código do GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

#### O usuário administrador restrito pode salvar/atualizar configurações padrão apesar das Permissões específicas do armazenamento

Correção do problema em que usuários administradores restritos podiam ver e tentar atualizar o escopo &quot;Configuração padrão&quot; apesar de ser atribuído apenas a escopos específicos do site, o que poderia causar confusão.

_ACP2E-4011 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Preço configurável do produto salvo no BD para qualquer escopo de exibição de loja, causando problemas no recurso de classificação Produtos na categoria, onde o preço salvo não tem relevância no front-end

Remoção da caixa de seleção &quot;Usar valor padrão&quot; para um produto configurável quando o preço é configurado por site e uma visualização de loja é selecionada na página de edição do produto configurável pela interface de administrador.

_ACP2E-4036 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]A Política de Senha do Administrador Não Atende à Conformidade com o PCI DSS 4.0 (Mínimo de 12 Caracteres)

Agora, os administradores podem configurar o requisito de comprimento mínimo da senha para usuários administradores em Lojas > Configuração > Avançado > Administração > Segurança. Esse aprimoramento oferece maior flexibilidade de segurança, mantendo as políticas de senha existentes. A validação é aplicada durante a criação/modificação do usuário administrador e salvamentos da configuração, com validação de front-end em tempo real para melhorar a experiência do usuário.

_ACP2E-4044 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Problema de filtro de data quando o idioma da interface do administrador é japonês

O filtro e a coluna de aniversário usarão o formato unificado M/d/y, igual ao filtro/coluna &quot;Cliente desde&quot;

_ACP2E-4052 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

### Interface do Administrador, Imposto

#### Erro na interface do administrador da alíquota do imposto

Esse ticket corrigiu um problema de IU do administrador de taxa de imposto em que a alternância do país (por exemplo, de EUA → Reino Unido) ainda exibia o estado dos EUA selecionado anteriormente, enganando os usuários.
Na versão 2.4.9-alpha3, o campo de estado agora é redefinido para * quando o país selecionado não tem estados.

_AC-8440 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Os produtos-render-info da API Rest retornam o preço final incorreto para o cliente conectado

O tíquete tem uma correção para a API Rest products-render-info retornar o preço final incorreto para o cliente conectado

_AC-5979 - [Problema do GitHub](https://github.com/magento/magento2/issues/35757) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/)_

#### O botão Adicionar à lista de requisições desaparece quando tentamos adicioná-lo a partir da página de categoria

Anteriormente, o botão Adicionar à lista de requisições desaparece quando tentamos adicioná-lo a partir da página de categoria, que agora está corrigida, e podemos ver o botão de requisição na página de categoria

_AC-8575_

### B2B, carrinho e finalização

#### Nenhuma entidade com cartId = X erro é mostrado na Loja quando o usuário da empresa B2B faz logon no recurso de administrador &quot;Logon como cliente&quot;

Agora, o erro &quot;Nenhuma entidade com cartId = X&quot; não é mais visível após fazer logon com êxito no back-end do administrador ao usar o recurso &quot;Logon como cliente&quot;.

_ACP2E-3994 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

### Carrinho e saída

#### [Problema] Adicione EventPrefix e EventObject para verificar o modelo de contrato

O sistema agora inclui EventPrefix e EventObject para o modelo de contrato de check-out, permitindo que os eventos sejam acionados com um prefixo de evento. Esse aprimoramento oferece mais flexibilidade para desenvolvedores ao trabalhar com eventos de contrato de check-out. Anteriormente, o modelo de contrato de check-out não aceitava EventPrefix e EventObject, limitando a capacidade de personalizar a manipulação de eventos.

_AC-13252 - [Problema do GitHub](https://github.com/magento/magento2/issues/32510) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32451)_

#### [Graphql] Não pode retornar nulo para o campo não anulável &quot;SeletedCustomizingOption.label&quot;

O sistema agora não lançará um erro interno do servidor com uma mensagem quando a opção selecionada não existir mais

_AC-14256 - [Problema do GitHub](https://github.com/magento/magento2/issues/39729) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] Não é possível fazer pedidos em que a Cidade tenha dígitos de 0 a 9, E comercial, ponto final ou parêntese no Nome da Cidade

Correção de um problema em que o check-out falhava em nomes de cidades contendo caracteres especiais como . , &amp; ou parênteses.
Agora, os pedidos com esses nomes de cidades são feitos com êxito sem erros de validação.

_AC-14495 - [Problema do GitHub](https://github.com/magento/magento2/issues/39854) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Subseleção de regra de vendas com condição de quantidade Falha ao aplicar

Correção de um problema em que as regras de preço do carrinho com condições de subseleção de produto não eram aplicadas na finalização da compra.
Agora, os descontos são aplicados com êxito de acordo com as regras configuradas.

_AC-14884 - [Problema do GitHub](https://github.com/magento/magento2/issues/39965) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql - O carrinho de mesclagem não funciona corretamente quando a Backorder está ativada

Correção de um problema em que os itens do carrinho de convidado não eram mesclados ao carrinho do cliente durante a mesclagem do carrinho por meio do GraphQL.
Agora, o carrinho do cliente reflete corretamente a quantidade combinada de carrinhos do cliente e do convidado.

_AC-15148 - [Problema do GitHub](https://github.com/magento/magento2/issues/40064) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integração] [Check-out] Diretivas de dependência atualizadas no modelo de email de pagamento com falha

Falha no modelo de email de pagamento atualizado para manipular as diretivas depend corretamente.
A correção garante que o endereço e o método de envio sejam exibidos corretamente quando aplicável.
Anteriormente, esses campos estavam ausentes em emails de pagamentos com falha.

_AC-15363 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### O desconto de envio gratuito da [Cloud] não é removido corretamente quando o carrinho não atende mais aos requisitos

O Subtotal (Excl. Imposto) na regra de preço do carrinho agora incorporará descontos das regras anteriores.

_ACP2E-3973 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Ordem duplicada encontrada para o mesmo cliente no Envio múltiplo

Solicitações simultâneas para fazer pedidos com vários endereços de entrega não resultam mais em pedidos duplicados para o mesmo cliente

_ACP2E-4117 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Carrinho e check-out, pedido, produto

#### O email do Cartão-presente é enviado mesmo se a fatura do pedido falhar

Antes da implementação dessa correção, emails de cartão-presente eram enviados após a criação da fatura. No entanto, após a aplicação da correção, os emails de cartão-presente agora são enviados depois que as faturas são salvas e confirmadas com êxito.

_ACP2E-3905_

### Carrinho e check-out, segurança

#### [NUVEM] Obtendo 404 para arquivo JS na página de check-out na primeira tentativa após a implementação do patch sri

Antes das correções, os mixins não tinham sido carregados no carrinho e o check-out quando a minificação e o empacotamento estavam ativados. Após a correção, todos os mixins devem ser carregados conforme esperado.

_ACP2E-4128 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catálogo

#### Problemas com o escopo de preço e config.php

No Magento 2.4.2, alterar o escopo de preço por meio de config.php não atualiza corretamente o valor is_global em catalog_eav_attribute para o atributo price.
Como resultado, os preços dos produtos permanecem globais e não podem ser salvos por site, mesmo quando o escopo de preços está definido como site.
A solução alternativa requer a atualização manual da coluna is_global no banco de dados, o que não é ideal para ambientes de produção.
Esse comportamento é consistente com o design padrão da Magento, em que o escopo de preço é Global ou Site, mas não por exibição de loja.

_AC-13857 - [Problema do GitHub](https://github.com/magento/magento2/issues/33559)_

#### Depois que a página de troca de armazenamento vem do cache (o alternador de armazenamento não está funcionando) na versão 2.4.8

Correção de um problema em que a alternância de exibições de loja do cabeçalho da loja não funcionava até que o cache fosse limpo manualmente.
Agora, a switching de visualização de armazenamento funciona corretamente sem exigir uma limpeza de cache.

_AC-14426 - [Problema do GitHub](https://github.com/magento/magento2/issues/39806)_

#### Estilos .less ignorados com largura mínima: (@screen__l)

Correção de um problema em que apenas três produtos eram exibidos por linha em páginas de categoria.
Agora, quatro produtos são exibidos por linha, conforme esperado.

_AC-14463 - [Problema do GitHub](https://github.com/magento/magento2/issues/39817) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### A contagem da lista de desejos não é exibida na página inicial/em outras páginas, exceto a página da lista de desejos no menu do cliente

Correção de um problema em que a contagem da lista de desejos aparecia como parênteses vazios em páginas que não eram da lista de desejos.
Agora, a contagem correta do item da lista de desejos é exibida ao lado de &quot;Minha lista de desejos&quot; em todas as páginas.

_AC-14607 - [Problema do GitHub](https://github.com/magento/magento2/issues/39892) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before o observador aciona um erro relacionado à data ao usar a API REST sem valores no nível de armazenamento (problema getFinalPrice())

Esta PR ajusta o processamento de SpecialFromDate para garantir a formatação adequada quando a data for fornecida como uma instância DateTimeInterface. Isso evita que ocorram erros durante a execução de getFinalPrice() em determinados cenários.

_AC-14847 - [Problema do GitHub](https://github.com/magento/magento2/issues/39959) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40003)_

#### URGENTE - Não é possível adicionar o produto ao pacote quando o produto a ser adicionado tem opções personalizáveis

Correção de um problema em que não era possível adicionar produtos com opções personalizáveis a produtos agrupados.
Anteriormente, esses produtos eram excluídos da lista &quot;Adicionar produtos à opção&quot; na criação do pacote.
Agora, os produtos com opções personalizáveis podem ser adicionados aos pacotes sem incluir suas opções personalizadas, permitindo um gerenciamento de estoque adequado.
Isso permite a criação de pacotes sem duplicar produtos ou afetar os níveis de inventário.

_AC-14958 - [Problema do GitHub](https://github.com/magento/magento2/issues/39993)_

#### O rótulo de preço &quot;Tão baixo quanto&quot; é exibido para produtos configuráveis com uma única opção

Correção de um problema em que os produtos configuráveis exibiam o preço com um rótulo &quot;Tão baixo quanto&quot; incorreto no PDP/PLP.
Agora, o produto mostra o preço correto (US$ 500) sem nenhuma etiqueta enganosa.

_AC-15237 - [Problema do GitHub](https://github.com/magento/magento2/issues/40104) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Método incorreto chamado para o botão Adicionar a Comparar

Correção do método usado em \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect().
Anteriormente, getAddToCartButton() era chamado incorretamente em vez de getAddToCompareButton().
Essa alteração garante o comportamento correto para renderizar o botão &quot;Adicionar para comparar&quot; nas listagens de produtos.
Nenhuma alteração de comportamento funcional é introduzida; a atualização melhora a experiência do desenvolvedor e a correção do código.

_AC-15323 - [Problema do GitHub](https://github.com/magento/magento2/issues/39754) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### A geração de imagens dinâmicas gera um grande número de imagens

Após a correção, as imagens serão geradas somente para os sites aos quais o produto está atribuído.

_ACP2E-3927 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### O erro 500 ocorre no front-end, devido à estrutura de layout incorreta ser armazenada em cache no layout

Correção de um problema em que uma página retornava um código de erro 500, devido a uma estrutura de layout incorreta ser armazenada em cache no layout

_ACP2E-4040 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Erro de validação para o campo de valor de desconto da regra de Preço de Catálogo em Atualização Programada

Anteriormente, antes de corrigir esse problema, para a atualização da programação para a regra de preço do catálogo, se a quantia de desconto for by_fixed, então ela não era validada corretamente por causa da regra de intervalo de números de validação. Depois que essa correção for aplicada, a validação funcionará corretamente para a regra de preço fixo do catálogo.

_ACP2E-4054 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Os produtos são exibidos como desativados

Após a correção, os produtos desativados não estarão presentes no widget produtos.

_ACP2E-4136 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Nuvem] Erros com entradas duplicadas (temp_category_descendants_%)

Correção de um problema com entradas duplicadas durante atualizações programadas de criação para ambientes com um alto número de categorias aninhadas

_ACP2E-4159 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Catálogo, GraphQL

#### Cálculo de desconto inválido do GraphQl

O GraphQL agora exibe corretamente as porcentagens de desconto e os preços base quando os preços de catálogo são configurados para incluir imposto. Anteriormente, ocorriam erros de arredondamento, como exibir 19,99% em vez de 20%.

_ACP2E-3993 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catálogo, Produto

#### Produtos relacionados via regra de produto relacionada que não aparecem no PDP via GraphQL

Anteriormente, antes dessa correção ser aplicada, a regra de produto relativa retornava vazia/nula para um produto que correspondia à regra. Depois que essa correção for aplicada, a regra relativa para produtos será retornada com êxito para produtos correspondentes.

_ACP2E-3949_

### Conteúdo

#### graphql (magento 2.4.6-p4 ) - erro ao tentar obter a página do cms com status de inativo

Correção de um problema em que a consulta do GraphQL para uma página do CMS desativada retornava um erro interno do servidor.
Agora, a consulta obtém uma resposta adequada sem erros.

_AC-12302 - [Problema do GitHub](https://github.com/magento/magento2/issues/38877) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Loop infinito de consulta de rota [GraphQl]

Esse ticket corrigiu o problema em que uma consulta de rota do GraphQL com Caminho de solicitação e Caminho de destino idênticos causava um loop infinito e eventualmente expirava.
Na versão 2.4.9-alpha3, o query agora retorna a resposta de erro correta em vez de fazer loop.

_AC-14269 - [Problema do GitHub](https://github.com/magento/magento2/issues/39707) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Altere a constante IMAGE_FILE_NAME_PATTERN para pública visível, para obter mais flexibilidade

A constante IMAGE_FILE_NAME_PATTERN em GenerateRenditions.php foi tornada pública para permitir aos desenvolvedores mais flexibilidade ao trabalhar com representações de imagem. A correção é incluída no Magento 2.4.9-alpha3 com cobertura completa de teste de unidade e integração.

_AC-15338 - [Problema do GitHub](https://github.com/magento/magento2/issues/39733) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### A visualização do preparo de conteúdo não funciona com os resultados da pesquisa

A Pesquisa na Visualização de preparo agora retorna produtos de acordo com o escopo selecionado. Anteriormente, a pesquisa retornava resultados no escopo padrão, ignorando o armazenamento selecionado.

_ACP2E-4095_

#### Page Builder - Problema da lógica de condição do produto (a lógica OR se comporta incorretamente mostrando menos produtos)

O widget Produtos do Page Builder agora retorna o resultado correto quando um atributo com escopo global é usado na condição &quot;Corresponder qualquer&quot;

_ACP2E-4096 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Cliente/ Clientes

#### A validação de valores mínimo e máximo não funciona para o atributo DOB na Loja

Esse bug corrigiu o problema em que a validação da data mínima e máxima para o atributo Data de nascimento (DOB) não funcionava na loja (embora funcionasse no Admin).
Na versão 2.4.9-alpha3, a validação agora bloqueia corretamente o salvamento de clientes com DOB fora do intervalo permitido, mostrando uma mensagem de erro.

_AC-13535 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Carregamento de erro do Ajax 401 na tela Aviso no painel do administrador durante a revogação da permissão Fazer logon como cliente

Esse bug corrigiu um problema em que uma permissão revogada de Logon como Cliente fazia com que um erro Ajax 401 com HTML bruto aparecesse no pop-up de aviso.
Após a correção, o sistema agora exibe corretamente uma mensagem de aviso normal em vez de HTML bruto.
A solução foi fornecida no Magento 2.4.9-alpha3

_AC-15336 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

### Estrutura

#### [Problema] Tornar a assinatura do método consistente com a interface

A assinatura de método para getAttributes agora é consistente com sua interface, evitando erros ao substituir o método. Anteriormente, as inconsistências na assinatura do método causavam erros ao tentar substituir o método getAttributes.

_AC-11578 - [Problema do GitHub](https://github.com/magento/magento2/issues/38501) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/31955)_

#### [Problema] Corrigir regra de validação de emails para o componente da interface do usuário

O sistema agora valida corretamente vários endereços de email inseridos nos componentes da interface do usuário, garantindo que cada email seja reduzido e validado corretamente. Anteriormente, o sistema usava um método incorreto para cortar endereços de email, o que poderia levar a erros de validação.

_AC-11719 - [Problema do GitHub](https://github.com/magento/magento2/issues/38528) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problema] Remover métodos redundantes

Qualidade do código: removeu métodos redundantes em operações assíncronas e componentes de vendas que chamavam apenas métodos principais sem adicionar funcionalidade, melhorando a manutenção do código.

_AC-11915 - [Problema do GitHub](https://github.com/magento/magento2/issues/29748) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/29147)_

#### a validação de xsd falha em arquivos etc/adminhtml/system.xml que contêm comentários abaixo de itens de campo.

Esta PR corrige as definições do esquema XML no phpstorm para o nó comment

_AC-12945 - [Problema do GitHub](https://github.com/magento/magento2/issues/39148) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39867)_

#### O Magento 2.4.8 usa pacotes dev que não seguem o controle de versão semântico

Magento 2.4.8 requer versões dev de pdepend/pdepend e phpmd/phpmd (3.x-dev) para compatibilidade com PHP 8.4.
Essas versões de desenvolvimento entram em conflito com ferramentas de terceiros que esperam pacotes compatíveis com o SemVer, impedindo algumas atualizações.
Uma solução alternativa temporária é criar um alias para as versões dev no composer.json (por exemplo, &quot;3.x-dev as 3.99.0&quot;), permitindo compatibilidade enquanto satisfaz o controle de versão semântico.
Isso garante o suporte ao PHP 8.4 e evita conflitos até que versões estáveis sejam disponibilizadas.

_AC-14519 - [Problema do GitHub](https://github.com/magento/magento2/issues/39796)_

#### API Rest: Chamada para uma função membro getVideoProvider() em nulo

Correção de um problema em que chamar a API filho do produto configurável retornava um Erro interno do servidor 500 se um produto filho tivesse apenas um vídeo YouTube e nenhuma outra imagem.
O erro foi causado por uma referência nula em ExternalVideoEntryConverter.
Agora, a API retorna corretamente os produtos secundários com entradas de galeria de mídia, incluindo dados de vídeo externos, sem gerar erros.
Isso garante a recuperação adequada de todos os tipos de mídia para produtos derivados por meio da API REST.

_AC-15046 - [Problema do GitHub](https://github.com/magento/magento2/issues/40021)_

#### [Problema] Corrija alguns erros de digitação nos comentários do PHPDoc

Esta PR corrige alguns erros de digitação no phpdoc

_AC-15075 - [Problema do GitHub](https://github.com/magento/magento2/issues/40042) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38809)_

#### [Problema] Remover o uso do sprintf em chamadas de frase

Essa PR remove o uso de sprintf na chamada de função de frase no núcleo do Magento.

_AC-15183 - [Problema do GitHub](https://github.com/magento/magento2/issues/40050) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40033)_

#### Não é possível reindexar todos os inválidos em indexadores de vários threads com bloqueio de aplicativo ativo

Esse problema corrigia uma falha do indexador de vários threads quando use_application_lock era habilitado.
Anteriormente, os bloqueios de BD eram perdidos durante o processamento paralelo, fazendo com que os indexadores permanecessem no estado &quot;funcionando&quot; e emitissem erros de SQL (tabela não encontrada).
No Magento 2.4.9-alpha3, a correção garante que os indexadores reindexem corretamente com o bloqueio de aplicativo ativado.

_AC-15270 - [Problema do GitHub](https://github.com/magento/magento2/issues/40102) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Atualizar os arquivos Readmes do módulo e corrigir links de documentos

_AC-15340 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ec9459d0)_

#### [Problema] registrar plug-in não declarado apenas se não estiver desabilitado

Esta PR corrige e registra o plug-in que na verdade não está declarado e não é usado (instância ativada e ausente).

_AC-15386 - [Problema do GitHub](https://github.com/magento/magento2/issues/40086) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, magento/framework versão 103.0.8-p2: classe EmailMessage chamando um método não existente

_AC-15446 - [Problema do GitHub](https://github.com/magento/magento2/issues/40170) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Patches de Dados/Esquemas getAliases() causam erros durante `setup:upgrade`

getAliases() causa erros durante a configuração:upgrade, essa PR corrigindo o mesmo

_AC-15559 - [Problema do GitHub](https://github.com/magento/magento2/issues/31396) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38239)_

#### Tipo esperado &#39;Magento\Customer\Api\Data\GroupInterface&#39;. Encontrado &#39;Magento\Customer\Model\Group&#39;.

Correção de um problema em que salvar um grupo de clientes por meio de GroupRepositoryInterface usando GroupFactory causava um erro de tipo.
Anteriormente, o repositório esperava GroupInterface, mas as instâncias de modelo de Grupo foram transmitidas, resultando em um erro fatal.
Agora, os grupos de clientes podem ser salvos com êxito por meio do repositório, garantindo a implementação adequada da interface.
Isso soluciona avisos do IDE e erros de tempo de execução ao criar ou atualizar programaticamente grupos de clientes.

_AC-6909 - [Problema do GitHub](https://github.com/magento/magento2/issues/36269)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8349 - [Problema do GitHub](https://github.com/magento/magento2/issues/37266) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8350 - [Problema do GitHub](https://github.com/magento/magento2/issues/37265) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8359 - [Problema do GitHub](https://github.com/magento/magento2/issues/37262) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8362 - [Problema do GitHub](https://github.com/magento/magento2/issues/37259) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problema] Remover a marca `@author` proibida de `Magento_Backup` e `Magento_Bundle`

Esta PR remove a tag `@author` da base de código

_AC-8367 - [Problema do GitHub](https://github.com/magento/magento2/issues/37244) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36979)_

#### [Problema] Corrigir o nome da variável na pesquisa do catálogo

O sistema agora nomeia corretamente as variáveis no módulo do mecanismo de pesquisa, melhorando a clareza e a capacidade de manutenção do código. Anteriormente, um nome de variável irrelevante, $defaultCountry, era usado no módulo do mecanismo de pesquisa, causando confusão.

_AC-9215 - [Problema do GitHub](https://github.com/magento/magento2/issues/37810) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]Problema de Servidor Potencialmente Causado por Chave de Acesso S3 Inválida

Credenciais incorretas do AWS S3 não fazem mais com que as páginas sejam carregadas infinitamente na loja.

_ACP2E-3890 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js não está funcionando

Os seguintes arquivos JS agora são totalmente e corretamente minificados quando a minificação JS é ativada: mage/backend/tabs.min.j, jquery/jquery.validate.min.js e Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Como resultado, a validação do campo de classe CSS do Page Builder funciona conforme esperado.

_ACP2E-3925 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### O trabalho Cron não está limpando a tabela do banco de dados - causando interrupção devido a falha do Galera

A limpeza de tabelas de log de alteração agora está sendo executada em lotes para evitar operações de exclusão intensas.

_ACP2E-3995 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### JS não minificado às vezes carrega ignorando &quot;ativar minificações de js&quot;

Antes da correção, mesmo que a minificação estivesse ativada, alguns arquivos JS eram solicitados sem o prefixo &quot;min&quot;, resultando no código de status 404. Após a correção, quando a minificação estiver ativada, não há solicitações de recursos JS não minificados.

_ACP2E-4058 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### O atributo de data no grupo de atributos personalizado não mostra o Datepicker no Admin

Correção de um problema em que o pop-up de calendário para atributos de data aparecia fora da tela quando atribuído a grupos de atributos personalizados.

_ACP2E-4060 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### GraphQL de Pedido de Cliente : recuperar categorias de produto para o produto associado &quot;não está visível individualmente&quot;

Antes da correção, se o pedido continha um produto oculto, suas categorias exibiriam uma matriz vazia na resposta GraphQl do pedido do cliente.
Agora, após a correção, as categorias de produtos são incluídas na resposta de uma solicitação GraphQl de pedido do cliente, mesmo que o produto esteja oculto.

_ACP2E-3945 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [Cloud] getRemoteAddress retorna 127.0.0.1 na produção

Antes dessa correção, o endereço remoto não era determinado corretamente quando o servidor de aplicativos era usado. Após a correção, o endereço remoto é corretamente determinado combinado com a configuração adequada do cabeçalho no nginx e na configuração do cabeçalho.

_ACP2E-3991 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] Confirmar reversão de comportamento de manipulação de exceção de posicionamento de pedido GQL

Alteração incompatível com versões anteriores endereçada para a mutação placeOrder.

_ACP2E-4031 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Mapeamento de problema da mensagem traduzida para o código de erro ao fazer o pedido via GraphQL

Correção de um problema em que a mensagem de exceção traduzida era usada para mapear o código de erro para solicitações GraphQL, causando códigos de erro desconhecidos para erros conhecidos.

_ACP2E-4033 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### O filtro de Ordem do Cliente da [NUVEM] não está funcionando para Datas

Após a correção, a recuperação de pedidos por meio do GraphQL usando um filtro de intervalo de datas retorna o resultado correto.

_ACP2E-4090 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Abordar as questões suscitadas no documento ACP2E-4031

Antes da correção, a posição do nó de erro não fornecia compatibilidade perfeita com as versões 2.4.7 e 2.4.9. Agora, após a correção, o nó de erro é colocado corretamente para acomodar ambas as versões.

_ACP2E-4115 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Pacote pai mostrando Fora de estoque mesmo que o filho tenha estoque na chamada Graphql

Após a correção, solicitar uma lista de produtos usando o GraphQL retorna o status de estoque correto para produtos de pacote.

_ACP2E-4168 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Inventário / MSI

#### Discrepâncias de mutação do GraphQL mergeCart

Após a correção, a solicitação GraphQL dos carrinhos de mesclagem verifica corretamente a quantidade do produto, levando em conta a configuração de estoque.

_ACP2E-4184 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Segurança

#### A redefinição da senha do cliente por meio do GraphQL não respeita as restrições

Solução de um problema em que as solicitações de redefinição de senha do cliente feitas por meio do GraphQL Mutations não cumpriam as restrições de redefinição de senha configuradas em Loja > Configuração > Clientes > Configuração do cliente > Opções de senha. Essas configurações agora são aplicadas corretamente.

_ACP2E-3992 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importar/exportar

#### Importação de produto Csv: não é possível desfazer a definição de uma imagem de amostra

Antes da correção, você não podia atualizar a imagem de amostra de um produto por meio da importação do produto. Agora, após a correção, se você marcar a coluna de imagem da amostra de produto com o marcador vazio configurado, a imagem será definida como oculta.

_ACP2E-3972 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### A importação do produto gera URLs vazios para o escopo de armazenamento

A chave de URL do produto na exibição de armazenamento agora herdará o valor definido no escopo padrão se url_key tiver um valor vazio na fonte de dados de importação. Anteriormente, definir url_key como um valor vazio na fonte de dados de importação para um registro de exibição de armazenamento levaria a url_key a ser substituída por um valor vazio nesse escopo.

_ACP2E-4038 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### O processo de importação de produtos encontra um erro se um atributo de seleção múltipla estiver configurado conforme necessário

Solução de um problema em que as importações de produto falhavam se um atributo obrigatório de multisseleção de tipo fosse incluído. A validação de dados agora é aprovada corretamente, permitindo que o processo de importação do produto seja concluído com êxito.

_ACP2E-4057 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [NUVEM] Os produtos sem backorders selecionados no estoque de gerenciamento ainda permitem que os clientes solicitem mais de nossos níveis de estoque quando importados

Após a correção, não será mais possível importar um valor inaceitável para o atributo &quot;allow_backorders&quot; do produto.

_ACP2E-4116 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Falha na importação do produto devido ao comprimento da descrição exceder a validação de 65.536 caracteres

Após a correção, é possível importar atributos de produto com texto de tipo cujos valores excedem 65.536 caracteres.

_ACP2E-4119 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Inventário / MSI

#### A operação de exclusão de estoque não está sendo concluída

Após a correção, a exclusão de um item de origem não resulta em uma reindexação completa e atualiza apenas os produtos afetados, aumentando o desempenho.

_ACP2E-3917 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] Não há nenhuma indicação no administrador se o cliente foi notificado de forma assíncrona sobre o Pedido está pronto para retirada

Adicionado à notificação do histórico do pedido sobre a notificação assíncrona do cliente de que o pedido está pronto para retirada

_ACP2E-3968 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### Consultas de status de estoque duplicadas no carregamento da cotação

Correção da execução duplicada da consulta cataloginventory_stock_status ao carregar uma cotação na loja, causando chamadas de DB redundantes.

_ACP2E-4102 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/fc15a9ae)_

#### ACP2E-4118 Pós-Patch: A Alteração do Limite do Estoque no Administrador Causa Quantidades Negativas de Vendas e Incompatibilidade do Status do Estoque

O status do estoque de estoque agora é ajustado automaticamente quando as configurações de estoque global Quantidade, Backorders e Limite de Falta de Estoque são atualizadas por meio da importação.

_ACP2E-4142 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### Pedido

#### Magento 2.4.8 GraphQL - Formatação incorreta dos itens do pedido order_date

Correção de um problema em que o campo order_date na resposta do GraphQL retornava no formato aaaa-mm-dd.
Agora, a order_date é exibida corretamente no formato dd-mm-yyyy.

_AC-14431 - [Problema do GitHub](https://github.com/magento/magento2/issues/39805) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Email de remessa não enviado quando enviado da visualização de Pedido de administrador apesar de estar ativado na configuração da loja

O sistema agora envia um email de confirmação de remessa, pois ele é ativado na configuração da loja onde o pedido foi feito.

_AC-14563 - [Problema do GitHub](https://github.com/magento/magento2/issues/39861) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39897)_

#### A filtragem na data não funciona devido a nomes de campo ambíguos

No Magento 2.4.7-p6, a filtragem da grade do pedido por data relatou causar um erro devido a associações com módulos do Braintree.
A emissão envolveu consultas unindo tabelas braintree_transaction_details e sales_order ao aplicar filtros de data.
A equipe de engenharia da Adobe Commerce analisou o caso, mas não conseguiu reproduzir o erro no ambiente.
O comportamento esperado é que a filtragem por data deve retornar ordens correspondentes ao filtro sem erros.

_AC-15037 - [Problema do GitHub](https://github.com/magento/magento2/issues/40024)_

#### Magento2: Não é possível criar regra de promoção

Essas correções de PR, nós obtemos
Modelo \Magento\Catalog\Model\ResourceModel\Eav\Attribute em vez de \Magento\Catalog\Model\ResourceModel\Eav\Attribute no método \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problema do GitHub](https://github.com/magento/magento2/issues/12176) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/30479)_

#### Cancelar redirecionamentos de fatura para 404

O cancelamento da fatura feita com o tipo Não capturar não resulta mais na página 404.

_ACP2E-4001 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Os processos do Cron do arquivo de vendas estão causando problemas de bloqueio do BD

Antes da correção, as consultas não vinculadas do DELETE localizadas na ordem do cron de arquivamento estavam causando problemas com o Galera. Agora, após a atualização, as consultas de exclusão são executadas com limites.

_ACP2E-4010_

#### Problema com pedidos atualizados com opções configuráveis usando a API REST

Preservar as opções de produto existentes nos itens da ordem de venda ao atualizar uma ordem por meio dos pontos de extremidade da api de descanso.

_ACP2E-4061 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Outras ferramentas de desenvolvedor

#### [Problema] Limpando código não utilizado.

O sistema agora remove o código não utilizado em relação às importações não utilizadas.

_AC-10980 - [Problema do GitHub](https://github.com/magento/magento2/issues/38424) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33499)_

#### [Acessibilidade] do problema: o aninhamento de funções WAI-ARIA está incorreto no menu

O sistema agora gera acessibilidade de farol sem o aninhamento de funções WAI-ARIA incorreto no erro de menu e o relatório deve estar verde

_AC-15082 - [Problema do GitHub](https://github.com/magento/magento2/issues/40045) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38617)_

#### Erro de console na pré-visualização de email no administrador do Magento

O sistema não emitirá nenhum erro de console quando estivermos visualizando o modelo de email

_AC-9245 - [Problema do GitHub](https://github.com/magento/magento2/issues/37820) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37933)_

### Pagamentos

#### IPNs desconhecidos do PayPal abusam do processador IPN do aplicativo

O manipulador IPN agora ignora tipos IPN desconhecidos ou sem suporte. Em vez de retornar um erro 500, ele registra o problema e continua o processamento sem interrupção.

_ACP2E-4049 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Falha no pagamento do token de cartão salvo do PayflowPro

As IDs de transação do PayPal PayFlow Pro (PNREFs) agora são válidas para uso em Transações de referência por um período fixo de 12 meses. Depois de expirado, o cartão salvo não será mais exibido e deverá ser adicionado novamente. Anteriormente, a validade era determinada pela data de expiração do cartão de pagamento usado na transação original.

_ACP2E-4064 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

### Desempenho

#### [Problema] Atualizar usa controle de cache imutável para site estático

Esta PR adiciona melhoria de desempenho ao não validar o conteúdo estático em cada carregamento de página até e a menos que seja alterado.

_AC-15171 - [Problema do GitHub](https://github.com/magento/magento2/issues/39486) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39484)_

#### [NUVEM] Não é possível adicionar produtos às categorias

Desempenho aprimorado ao adicionar produto à categoria por meio do Visual Merchandiser.

_ACP2E-3946 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### [Nuvem] cache_invalidate com mais de 10K logs

Anteriormente, o cache era limpo em cada visita de PLP ou carrinho, causando sobrecarga desnecessária no desempenho. O cache da regra de destino não é mais invalidado nessas páginas, melhorando a eficiência da navegação.

_ACP2E-4059_

### Preços

#### O produto está sendo salvo mesmo quando a Data de Preço Especial - De é posterior à Data Até usando a ação em massa

Correção de um problema em que os produtos podiam ser salvos sem validação com um intervalo de datas de preço especial inválido.
Agora, uma mensagem de erro é exibida: &quot;Certifique-se de que a data Até seja posterior ou igual à data De.&quot;

_AC-15252 - [Problema do GitHub](https://github.com/magento/magento2/issues/40113) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Os detalhes de envio não correspondem depois de concluir o checkout expresso do paypal para uma cotação negociável.

Esse problema corrigiu uma incompatibilidade de custos de envio ao concluir um Check-out do PayPal Express para uma cotação negociável aprovada.
Antes da correção, o frete foi incorretamente dobrado (mostrando US$ 10 em vez de US$ 5), resultando em totais inflados.
A correção no Magento 2.4.9-alpha3 garante que o custo de envio correto seja aplicado

_AC-15280_

#### O preço especial não entra em vigor com sites criados com fusos horários diferentes

Antes da correção, a validade da data do preço especial era criada no escopo do carimbo de data e hora da loja atual. Agora, após a correção, o fuso horário de armazenamento padrão é levado em consideração.

_ACP2E-4002_

#### O preço normal não é visível, mesmo quando um preço especial é aplicado.

Correção de um problema em que o preço normal não era exibido quando um preço especial era aplicado. O preço normal agora aparece corretamente ao lado do preço especial, conforme esperado.

_ACP2E-4100 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

### Produto

#### A etiqueta &quot;Tão baixo quanto&quot; ainda é exibida para um Produto configurável para o caso de teste AC-6158

Produtos configuráveis implementados e verificados (P1-P7) com as respectivas variações e atribuições de categoria. Garantia de exibição correta do preço da loja e do comportamento de etiqueta &quot;Tão baixo quanto&quot; para produtos da Categoria C.

_AC-10847 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Falha No Registro Extra Ao Solicitar Um Produto Por Meio Do Repositório

Mensagens de erro aprimoradas para ProductRepository::get e getById quando um SKU ou ID não é encontrado.
Anteriormente, as exceções não forneciam contexto sobre qual SKU ou ID causava o erro.
Agora, a mensagem de exceção inclui o SKU ou a ID ausente, ajudando na depuração e melhorando a experiência do desenvolvedor.
Essa alteração não afeta nenhum comportamento funcional da API.

_AC-15199 - [Problema do GitHub](https://github.com/magento/magento2/issues/40090) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Produtos simples não atribuídos quando o produto configurável é editado por função limitada

Antes dessa correção, se um usuário administrador restrito salvasse um produto configurável que continha produtos simples aos quais o usuário administrador não tinha acesso, eles seriam removidos do produto configurável ao salvar. Após a correção, o produto configurável é preservado, salvo de um administrador com todos os direitos.

_ACP2E-4081_

#### O desempenho de geração do Mapa de Site da [Nuvem] foi significativamente reduzido

A geração de mapas do site para produtos com imagens não apresenta mais lentidão exponencial. Anteriormente, a geração de mapas de site para lojas com inclusão de imagem ativada resultava em tempos de processamento longos.

_ACP2E-4153 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Promoção

#### Erro ao obter descontos do item da ordem apply_to para ordem do cliente por meio de solicitação GraphQl do cliente

Anteriormente, quando os descontos aplicados em ordem do cliente por meio do GraphQl, o erro do servidor interno de solicitação do cliente foi observado, o que agora é fixo, e os dados adequados da ordem do cliente com desconto aplicado são obtidos

_AC-14888 - [Problema do GitHub](https://github.com/magento/magento2/issues/39963) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Erro ao obter o código do cupom do item da ordem para a ordem do cliente por meio da solicitação de cliente GraphQl

Correção de um problema em que a busca de pedidos com detalhes de cupom por meio do GraphQL retornava um erro interno do servidor.
Agora, o query é executado com sucesso e retorna as informações corretas do cupom na resposta.

_AC-14889 - [Problema do GitHub](https://github.com/magento/magento2/issues/39962) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### Chave de matriz indefinida em ProductRepository getById

O problema ocorria quando ProductRepository::getById() era chamado com uma ID inválida, como 123abc, resultando em um erro &quot;Chave de matriz indefinida&quot;.
Após a correção no Magento 2.4.9-alpha3, essas solicitações agora retornam corretamente uma página 404, em vez de lançar uma exceção.
O controle de qualidade foi confirmado com IDs válidas e malformadas e nenhum outro problema foi observado.

_AC-15345 - [Problema do GitHub](https://github.com/magento/magento2/issues/40146) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Geração de mapa de site [Cloud] nunca termina

Antes da correção, não era possível concluir com êxito a geração do mapa de site se o catálogo contivesse mais de um milhão de produtos. Após a correção, a geração do mapa de site será concluída com uma alocação de memória mais baixa e com até um milhão de produtos por loja.

_ACP2E-3902 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### O alternador de armazenamento da [Cloud] não está funcionando do EN para o FR na página de perguntas frequentes

Correção de um problema em que a alternância entre exibições de loja redirecionava os usuários para a página inicial em vez da página do CMS traduzida correspondente. O alternador de loja agora verifica as substituições de URL no armazenamento de destino para garantir o redirecionamento correto (por exemplo, página de perguntas frequentes em inglês → página de perguntas frequentes em francês).

_ACP2E-4112_

### Preparo e visualização

#### A visualização da atualização de preparo é interrompida na finalização ao usar um domínio de administrador diferente

Um cliente pode fazer logon e visualizar seu carrinho no modo de visualização da loja quando o URL de base da loja é diferente do URL de administração.

_ACP2E-3906_

#### Painel de preparação de conteúdo Exibição de tempo incorreta

Agora, os filtros de data &quot;Hora de início&quot; e &quot;Hora de término&quot; no &quot;Painel de preparo de conteúdo&quot; mostram a data e a hora corretas. Anteriormente, a data e a hora incorretas eram exibidas após selecionar a data e a hora no seletor de datas

_ACP2E-3969_

#### O escopo está mostrando diferentes Visualizações da Loja durante a Visualização de produtos e categorias de atualizações agendadas

Antes dessa correção, o link de visualização para categorias e produtos não era gerado para a loja correta. Após essa correção, o link de visualização selecionará automaticamente a loja em que a visualização foi criada.

_ACP2E-4053_

### Estrutura da interface

#### [Problema] Remover a marca `@author` proibida de `Magento_Backend`

Esta PR remove a tag `@author` da base de código

_AC-8814 - [Problema do GitHub](https://github.com/magento/magento2/issues/37522) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36976)_
