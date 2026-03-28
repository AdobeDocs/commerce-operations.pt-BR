---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '24355'
ht-degree: 0%

---
# Magento Open Source corrigiu problemas (v2.4.9-beta1)

## Correção de problemas na v2.4.9-beta1

Corrigimos 501 problemas no código principal do Magento Open Source 2.4.9-beta1. Um subconjunto dos problemas corrigidos incluídos nesta versão está descrito abaixo.

### APIs

#### O Preço Especial Acumulado foi validado incorretamente em applySpecialPrice

O sistema está funcionando sem problemas com relação ao Preço especial e o Preço especial do produto expirará na data definida pelo administrador ou sistema de terceiros pela API REST

_AC-13130 - [Problema do GitHub](https://github.com/magento/magento2/issues/39169) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39690)_

#### Confirmação de email do cliente do [WebAPI] via paradoxo da WebAPI

Correção de um problema em que os clientes não podiam ativar suas contas por meio da WebAPI devido a um paradoxo de autorização que exigia um token antes da confirmação. A atualização permite que clientes não confirmados ativem suas contas com êxito por meio da API, garantindo um fluxo de confirmação consistente e funcional.

_AC-13281 - [Problema do GitHub](https://github.com/magento/magento2/issues/39255) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

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

#### [Problema] Opção de atributo esclarecido já existe resposta

O sistema agora substituiu a frase incômoda &quot;Obter novo nome de arquivo se o mesmo já existir&quot; por uma versão mais clara e gramaticalmente correta: &quot;Obter um novo nome de arquivo se já existir&quot;. Isso melhora a legibilidade e a compreensão do usuário.
O mesmo para a resposta da opção de atributo.

_AC-15473 - [Problema do GitHub](https://github.com/magento/magento2/issues/39943) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39941)_

#### Erro interno do servidor no ponto de extremidade da API /V1/products/special-price

Correção de um problema em que solicitações malformadas para /V1/products/special-price e APIs de preço relacionadas retornavam um Erro interno de servidor 500 devido a um TypeError nulo.
Agora, as APIs validam corretamente a entrada e retornam um erro 400 para cargas inválidas, melhorando o tratamento de erros e a confiabilidade da API.

_AC-6419 - [Problema do GitHub](https://github.com/magento/magento2/issues/35934) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Erro interno do servidor no ponto de extremidade de API `/V1/order/&lbrace;orderId&rbrace;/ship`

O Sistema agora corrige o Erro Interno do Servidor no Ponto de Extremidade da API `/V1/order/{orderId}/ship` e Retorna um erro 400, pois a solicitação está malformada.

_AC-6420 - [Problema do GitHub](https://github.com/magento/magento2/issues/35931) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38282)_

#### Erro interno do servidor no ponto de extremidade da API /V1/creditmemo

Correção de um problema em que solicitações malformadas para a API /V1/creditmemo retornavam um Erro interno 500 do servidor.
Agora, a API valida corretamente a solicitação e retorna um erro 400 para cargas inválidas, melhorando o tratamento e a estabilidade de erros.

_AC-6422 - [Problema do GitHub](https://github.com/magento/magento2/issues/35924) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### A API Rest e o back-end do Magento usam diferentes métodos de validação para attribute_code ao criar novos atributos

Correção de uma inconsistência em que o administrador do Magento permitia letras maiúsculas em attribute_code, mas a API REST as rejeitava durante a criação do atributo de produto.
Agora, a API de Administração e a REST seguem a mesma validação, permitindo a criação bem-sucedida de atributos com letras maiúsculas.

_AC-6660 - [Problema do GitHub](https://github.com/magento/magento2/issues/33138) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Validação diferente entre criação e atualização de atributo por meio da API REST

Correção de um problema em que a validação inconsistente durante a criação do atributo por meio da API REST resultava na atribuição incorreta de um backend_type.
Agora, o sistema define o tipo de backend correto quando válido, lança uma exceção para valores inválidos ou retorna adequadamente se não for fornecido, garantindo um comportamento de atributo consistente.

_AC-6885 - [Problema do GitHub](https://github.com/magento/magento2/issues/36327) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Corpo de solicitação ou parâmetros malformados causam &quot;Erro interno do servidor&quot;

Os corpos de solicitação ou parâmetros malformados agora retornam uma resposta clara de &quot;400 solicitação incorreta&quot;.
Anteriormente, o envio de corpos de solicitação ou parâmetros malformados para vários endpoints de API REST (como /V1/carts/search, /V1/orders, /V1/products, etc.) resultava em um &quot;Erro interno de servidor&quot; genérico (500), dificultando o diagnóstico de problemas de entrada.
Agora, o Adobe Commerce retorna uma resposta &quot;400 Solicitação inválida&quot;, fornecendo feedback mais claro quando as solicitações são inválidas.

_AC-746 - [Problema do GitHub](https://github.com/magento/magento2/issues/32784) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### O ponto de extremidade `/orders` (ou `/orders/:id`) não tem campos de &quot;estado&quot; e &quot;status&quot;

Correção de um problema em que as respostas da API `/orders` e `/orders/{id}` omitiam os campos de estado e status quando os valores do banco de dados eram nulos.
Agora, ambos os campos são retornados consistentemente na resposta, garantindo a conformidade com a documentação da API e melhorando a confiabilidade dos dados.

_AC-9244 - [Problema do GitHub](https://github.com/magento/magento2/issues/37807) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

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

#### A ordem &quot;base_row_total&quot; e &quot;row_total&quot; mostra o preço de item único na resposta da API REST

A resposta da API REST para detalhes do pedido agora contém valores corretos para os atributos &quot;base_row_total&quot; e &quot;row_total&quot; caso vários itens iguais tenham sido solicitados

_ACP2E-3874 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### O ponto de extremidade da API REST export-stock-salable-qty retorna itens incorretos total_count

Correção de um problema de paginação na API de quantidade comercializável de estoque da exportação de estoque em que total_count estava incorretamente limitado ao tamanho da página. Anteriormente, ao usar o endpoint /rest/all/V1/inventory/export-stock-salable-qty/website/base com parâmetros de paginação como page_size=5, o campo total_count na resposta retornaria 5 em vez do número total real de produtos que correspondem aos critérios de pesquisa. Após essa correção, o campo total_count agora reflete corretamente o número total de produtos disponíveis, independentemente do parâmetro page_size, garantindo um comportamento de paginação consistente em todos os endpoints da API REST do Magento.

_ACP2E-4086 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Problema de validação com IDs de opção personalizadas nas APIs REST do item de carrinho.

As APIs REST V1/guest-carts/&lt;cartId>/items/ e V1/carts/mine/items/ agora validam &quot;product_options.extension_attributes.custom_options.*.option_id&quot; para garantir que faça referência a um option_id válido para a SKU do item de carrinho. Anteriormente, esse parâmetro era processado e salvo no banco de dados sem validação.

_ACP2E-4138 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Ao buscar o produto do carrinho e alterar o idioma do cabeçalho da loja, não é possível alterar

A consulta do carrinho de cliente do GraphQL agora retorna valores de atributo de produto de acordo com o valor do cabeçalho da loja. Anteriormente, alterar o idioma do cabeçalho da loja ao recuperar um produto do carrinho por meio do GraphQL não refletia o idioma atualizado, resultando em localização inconsistente.

_ACP2E-4227 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### Falha na API REST /ponto de extremidade de mídia para produtos de Cartão-presente - retorna &quot;O produto não pode ser salvo&quot;

Antes da correção, você tinha permissão para criar produtos de cartão-presente que não incluíam uma quantidade no escopo global. Com a correção, foi adicionada uma validação que verifica os valores no escopo global.

_ACP2E-4395 - [Problema do GitHub](https://mcstaging.panini.it/shp_ita_it/)_

### APIs, carrinho e check-out

#### Para Informações de Entrega, a Validação no Servidor não está funcionando usando a API REST

Correção de um problema na API REST em que a validação das informações do endereço de entrega não aderia à configuração do atributo definida no back-end do administrador. A validação agora segue adequadamente as configurações definidas.

_ACP2E-4156 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### APIs, Catálogo

#### Excluir site/loja padrão interrompe o ponto de extremidade da API de preços de camada

Anteriormente, excluir o site base padrão e usar o site secundário como o site padrão resultava em um erro ao tentar atualizar o preço da camada para o site secundário. No entanto, após a aplicação dessa correção, o preço da camada pode ser atualizado com sucesso mesmo se o site base for excluído ou desativado.

_ACP2E-4334 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### APIs, Estrutura

#### Exceção RedisRequestLogger\RedisClient (limitador de taxa) no servidor de aplicativos

Após a correção, o recurso de limitação de taxa pode ser usado junto com o servidor de aplicativos GraphQL nos casos em que a extensão redis do PHP estiver instalada.

_ACP2E-4237 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e885088b)_

### APIs, Importar / exportar

#### A API de reembolso de fatura assíncrona cria reembolsos off-line em vez de reembolsos on-line

Correção de operações assíncronas de reembolso em que as solicitações de reembolso com o parâmetro `is_online` não eram processadas corretamente.

_ACP2E-4394 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

### APIs, Ordem

#### [NUVEM] Problema de informações do pedido com aparência total da linha para o pedido 000075568

Corrige o problema em que o valor row_total_incl_tax na resposta da API do pedido era retornado como um valor residual próximo de zero em vez de 0,00 quando um item era totalmente descontado.

_ACP2E-3950 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Conta

#### [Problema] Corrigir erros de digitação nas opções de modelo do Widget de catálogo

O Sistema agora corrige os erros de digitação nas opções do modelo do Dispositivo de catálogo.

_AC-11576 - [Problema do GitHub](https://github.com/magento/magento2/issues/38185) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38178)_

#### [Problema] Remoção de espaçamento desnecessário na grade de back-end

O sistema agora remove o espaçamento desnecessário na grade do backend. Quando há itens selecionados.

_AC-11579 - [Problema do GitHub](https://github.com/magento/magento2/issues/38502) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32622)_

#### O código de grupo de clientes salvo não corresponde à entrada ao usar caracteres multibyte

Correção de um problema em que os códigos de grupo de clientes que usavam caracteres multibyte eram truncados e não correspondiam ao valor inserido. A atualização garante que a entrada completa seja salva corretamente, permitindo a criação precisa de grupos de clientes com nomes multibyte.

_AC-13335 - [Problema do GitHub](https://github.com/magento/magento2/issues/39342) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Problema ao atualizar o email do cliente no Painel de administração com o domínio ö e .swiss

O Painel de administração agora aceita emails de clientes com caracteres especiais e domínios .swiss.
Anteriormente, a atualização de um email do cliente para um endereço como max@möstermann.swiss falhava com erros sobre nomes de host e TLDs inválidos.
AC-13409

_AC-13409 - [Problema do GitHub](https://github.com/magento/magento2/issues/39394) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### A opção habilitada para assinatura do informativo não está funcionando por site/loja

O sistema lida corretamente com a assinatura com o boletim informativo quando temos vários sites/lojas quando ele foi desativado em nível global

_AC-14283 - [Problema do GitHub](https://github.com/magento/magento2/issues/39751) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39752)_

#### [Problema] Remoção de divulgação de email

O Sistema agora mostra Exibir uma mensagem de erro indicando um email incorreto se o email inserido não for necessário para confirmar a conta, independentemente de o cliente existir ou não.

_AC-14561 - [Problema do GitHub](https://github.com/magento/magento2/issues/39574) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39570)_

#### Não é possível limpar o comentário do item da lista de desejos por meio da mutação do GraphQL `updateProductsInWishlist`

Correção de um problema em que os comentários da lista de desejos não eram atualizados por meio de mutações do GraphQL.
Agora, os comentários são atualizados corretamente e refletidos na resposta da API e na loja.

_AC-14682 - [Problema do GitHub](https://github.com/magento/magento2/issues/39911) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### O produto removido do dispositivo móvel ainda aparece na seção Mini Compare da Web até que você faça logon novamente

O sistema agora remove o produto imediatamente desaparecer de todas as visualizações de comparação em dispositivos móveis e na Web, incluindo a seção mini comparação.

_AC-14703 - [Problema do GitHub](https://github.com/magento/magento2/issues/39905) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40023)_

#### Mostrar configuração de prefixo/sufixo ignorada quando definida como Não

Correção de um problema em que o prefixo/sufixo do nome do cliente continuava a ser exibido em pedidos mesmo quando desativado na configuração.
Agora, os valores de prefixo/sufixo são removidos dos detalhes do pedido com base na configuração.

_AC-15074 - [Problema do GitHub](https://github.com/magento/magento2/issues/40036) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Registro de conta de cliente da loja: o formato do endereço de email está sendo convertido com um formato de domínio diferente

Esse erro solucionou um problema em que os emails de clientes com caracteres especiais no domínio (por exemplo, òbe.com) eram convertidos automaticamente para o formato punycode (tec55241@xn--adbe-mqa.com).
No Magento 2.4.9-alpha3, a correção garante que essas IDs de email permaneçam inalteradas e válidas, evitando erros de delivery.

_AC-15177 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Mensagens de validação ausentes (image-error) no formulário de registro

Correção de um problema em que os campos obrigatórios na página de criação da conta do cliente não mostravam mensagens de validação quando deixados em branco.
Agora, as mensagens de erro apropriadas são exibidas para todos os campos vazios ou incorretos.

_AC-15185 - [Problema do GitHub](https://github.com/magento/magento2/issues/40076) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Título Modal De Cancelamento De Pedido Sem Tradução

O sistema agora corrige uma tradução ausente no modal de cancelamento de pedido na loja. Quando um cliente clica no botão &quot;Cancelar&quot; da página Minha conta > Meus pedidos, é exibido um modal solicitando um motivo de cancelamento. No entanto, o título modal era anteriormente codificado e não traduzível. Essa alteração garante que o título modal use um método de tradução adequado.

_AC-15260 - [Problema do GitHub](https://github.com/magento/magento2/issues/40098) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40100)_

#### Problema após o logon no magento 2.4.8-p1

Correção do problema no Magento 2.4.8-p1 em que o link &quot;Criar uma conta&quot; ainda estava visível na página inicial após o logon.
Agora, o link fica oculto corretamente após o logon, de forma consistente com outras páginas.

_AC-15292 - [Problema do GitHub](https://github.com/magento/magento2/issues/40120)_

#### [Problema] Defina isSecureArea antes de excluir o cliente

O sistema está funcionando bem e esse PR define isSecureArea para o processo de exclusão, e o cliente pode se registrar novamente com sucesso.

_AC-15723 - [Problema do GitHub](https://github.com/magento/magento2/issues/40211) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38462)_

#### A operação de exclusão da [Nuvem] é proibida para o erro de área atual durante a criação da conta do cliente

Após a correção, salvar um cliente com um endereço inválido retorna uma mensagem descrevendo o motivo da invalidez em vez de &quot;A operação de exclusão é proibida para a área atual&quot; irrelevante.

_ACP2E-3791 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### As solicitações da Webapi [B2B] executam um loop infinito para clientes conectados quando o cache &quot;eav&quot; está desabilitado

Após a correção, desativar o cache eav não resulta em um loop infinito durante determinadas solicitações REST.

_ACP2E-4191 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Erro ao carregar algum local

Correção de um problema em que a criação de uma conta de cliente falhava ao usar a localidade árabe e o atributo Data de nascimento estava definido para exibição na loja. A conta agora pode ser criada com sucesso nessa configuração.

_ACP2E-4311 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Erro Data inválida ao atualizar informações da conta

Agora, os clientes podem atualizar sua conta com êxito ao usar o locale árabe. Anteriormente, o tentava salvar as informações da conta, a data de nascimento falhava devido a um erro de data inválida.

_ACP2E-4344 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Conta, interface do administrador

#### [Nuvem] Nenhuma entidade com cartId

Solução de um problema em que usar o Logon como cliente com duas contas de administrador de empresa na mesma sessão causava um erro &quot;Nenhuma entidade com cartId&quot;.

_ACP2E-4137 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### As mensagens de erro do formulário criado pelo cliente não são traduzidas

Correção de um problema em que as mensagens de erro de validação do cliente não eram traduzidas e formatadas corretamente em interfaces diferentes. Os erros de validação agora exibem mensagens traduzidas corretamente em todas as áreas do aplicativo: storefront, adminhtml, rest api e graphql.

_ACP2E-4354 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Interface do administrador

#### A Grade de Produtos da Categoria > as Colunas Status e Visibilidade ficam vazias ao classificar por nome

Correção de um problema em que as colunas Status e Visibilidade apareciam vazias na grade Produtos da categoria ao classificar por nome de produto.
A grade agora exibe corretamente todos os dados da coluna após a classificação, garantindo informações precisas do produto no painel de administração.

_AC-10659 - [Problema do GitHub](https://github.com/magento/magento2/issues/38233) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### Alternador de armazenamento de modelo de email

Correção de um problema em que o alternador de armazenamento na pré-visualização do modelo de email do boletim informativo não era aberto quando clicado devido ao código jQuery obsoleto. A atualização do evento de carregamento restaurou a funcionalidade adequada, permitindo que os usuários acessem o alternador de armazenamento conforme esperado.

_AC-12334 - [Problema do GitHub](https://github.com/magento/magento2/issues/38892) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Os valores de FPT na página do carrinho e na página do produto são diferentes para as mesmas configurações de produto simples

Os valores de FPT agora são consistentes entre as páginas do carrinho e do produto para produtos simples.
Anteriormente, os valores de Imposto fixo sobre o produto (FPT) podiam diferir em casas decimais entre o carrinho e as páginas do produto, mesmo quando as mesmas configurações eram aplicadas.
AC-13066

_AC-13066 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### As opções de atributo de seleção múltipla não podem ser salvas quando os módulos Amostras estão desativados

As opções de atributo de seleção múltipla agora podem ser salvas quando os módulos Amostras estão desativados.
Anteriormente, a desativação dos módulos Amostras causava exceções ao criar novas opções de atributo de seleção múltipla/seleção.
AC-13071

_AC-13071 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Os valores de FPT na página do carrinho e na página do produto são diferentes para as mesmas configurações de um produto dinâmico

Os valores de FPT agora são consistentes entre as páginas do carrinho e do produto para produtos dinâmicos.
Anteriormente, os valores de FPT (Fixed Product Tax) podiam diferir em casas decimais entre o carrinho e as páginas de produto para as mesmas configurações.
AC-13075

_AC-13075 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Formato de data não respeitado no componente da interface do usuário de data

Solução de um problema em que o componente da interface de data ignorava o formato configurado e exibia valores incorretos. A correção garante que o campo de data agora respeite o formato especificado (por exemplo, Y-m-d) para exibição e entrada.

_AC-13174 - [Problema do GitHub](https://github.com/magento/magento2/issues/39218) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Nenhuma opção disponível para excluir origens

Adicionada uma opção de exclusão para fontes de inventário na interface do administrador, permitindo que os administradores removam fontes extras em vez de apenas ativá-las ou desativá-las. Esse aprimoramento melhora o gerenciamento do inventário ao fornecer melhor controle sobre fontes não utilizadas.

_AC-13354 - [Problema do GitHub](https://github.com/magento/magento2/issues/32362) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### A árvore de categorias no administrador não é expandida para mostrar todas as categorias aninhadas selecionadas do nível 3

Correção de um problema em que a árvore de categoria do administrador não se expandia para exibir categorias aninhadas selecionadas além do nível 3. Após a correção, todas as categorias selecionadas são expandidas automaticamente, melhorando a visibilidade e a usabilidade entre as condições relacionadas à categoria.

_AC-13363 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problema] Melhore a experiência do usuário com a árvore de funções

Essa solicitação de pull adiciona botões para recolher tudo, expandir tudo e expandir ramificações com itens selecionados. Essa funcionalidade é semelhante à fornecida na árvore de categorias (Catálogo -> Inventário -> Categorias)

_AC-14020 - [Problema do GitHub](https://github.com/magento/magento2/issues/39654) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36511)_

#### Os logs de ação de importação/exportação não são criados em Sistema > Logs de ação > Grade de relatório

Implementação do registro para ações de Administração de importação/exportação para que apareçam em Sistema > Logs de ação > Relatório. Isso garante um melhor rastreamento de auditoria, registrando atividades de importação que estavam ausentes anteriormente.

_AC-14266 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: o cabeçalho &quot;Remetente&quot; deve ser uma instância de &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (obteve &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

O Adobe Commerce agora envia emails de registro com êxito quando um endereço de caminho de retorno personalizado é configurado para SMTP. Anteriormente, no Adobe Commerce 2.4.8 padrão com system/smtp/set_return_path definido como 2 e system/smtp/return_path_email definido como um endereço personalizado, o registro do cliente foi concluído, mas o email de registro não foi enviado, e a Adobe Commerce registrou este erro: Symfony\Component\Mime\Exception\LogicException: O cabeçalho &quot;Remetente&quot; deve ser uma instância de &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (obteve &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;).

_AC-14520 - [Problema do GitHub](https://github.com/magento/magento2/issues/39823) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1e14bd72) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1514117f)_

#### A ordem de atualização não obtém os dados de atributo personalizado mais recentes

Correção de um problema em que atualizar a página do pedido não exibia os dados mais recentes do atributo personalizado do cliente; após a correção, os valores de atributo atualizados agora são refletidos sem a necessidade de cancelar e recriar o pedido.

_AC-14690 - [Problema do GitHub](https://github.com/magento/magento2/issues/30301)_

#### [Problema] para substituir o escape obsoleto

O getEscaper() obsoleto foi removido e adicionado via injeção do construtor.

_AC-15132 - [Problema do GitHub](https://github.com/magento/magento2/issues/40062) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38135)_

#### Categoria de produto de sobreposição de mensagem de boas-vindas na exibição móvel

Correção de um problema na interface do usuário em que o nome de boas-vindas se sobrepunha às categorias de produto na exibição móvel, bloqueando cliques.
Agora, as categorias são totalmente visíveis e clicáveis, sem problemas de sobreposição.

_AC-15166 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### O botão Redefinir Formulário da Interface do Usuário não está funcionando como esperado

O sistema agora está funcionando bem ao clicar no botão Redefinir sem recarregar a página inteira, os dados do formulário serão redefinidos.

_AC-15204 - [Problema do GitHub](https://github.com/magento/magento2/issues/40092) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40094)_

#### [Problema] PageCache/AccessList: adicionar suporte a CIDR

O sistema agora aceita solicitações de limpeza em uma rede; é mais fácil fornecer apenas um intervalo CIDR.

_AC-15804 - [Problema do GitHub](https://github.com/magento/magento2/issues/39953) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37809)_

#### [Problema] Adicione títulos explicativos aos botões de gerenciamento de cache

O sistema agora adiciona títulos explicativos aos botões de gerenciamento de cache ao mover o cursor

_AC-16212 - [Problema do GitHub](https://github.com/magento/magento2/issues/38607) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38598)_

#### Fornecer um recurso para excluir alíquotas de imposto em massa usando a grade

Os usuários administradores agora podem excluir simultaneamente várias alíquotas de imposto da grade Alíquotas de imposto administrativas.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [Problema do GitHub](https://github.com/magento/magento2/issues/33399) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33484) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_

#### A cor de foco não é aplicada em grades estáticas no admin

As cores de focalização agora são aplicadas conforme esperado nas linhas de grades estáticas de Administração.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problema do GitHub](https://github.com/magento/magento2/issues/35358) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/35384)_

#### &quot;Não é possível resolver as entradas do parâmetro reCAPTCHA&quot; no exception.log para o Painel de Administração do Google reCAPTCHA

Um erro de reCaptcha no arquivo `var/log/exception.log` para o logon de Administrador do reCAPTCHA do Google V3 foi resolvido e nenhuma mensagem de erro foi registrada. Anteriormente, o seguinte erro era gerado a cada poucos segundos quando um usuário administrador definia as configurações de **Configuração** > **Segurança** > **Painel de Administração do Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problema do GitHub](https://github.com/magento/magento2/issues/34975) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contribuição de código do GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

#### A regra de preço do carrinho com a condição SKU não considera os &quot;zeros à esquerda&quot; no SKU (sku: 01234 é o mesmo que 1234)

Agora o sistema lida corretamente com a regra de preço do carrinho com a SKU de condição. Considere os &quot;zeros à esquerda&quot; na SKU

_AC-9428 - [Problema do GitHub](https://github.com/magento/magento2/issues/37919) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39525)_

#### Problema com o Comportamento do Valor da Opção de Atributo Padrão para Multisseleção

Antes da correção, os valores padrão para o atributo de várias opções não eram salvos corretamente. Agora, após a correção, os valores são armazenados corretamente no banco de dados.

_ACP2E-3523 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Problema ao mover a quantidade do produto do administrador para o carrinho de compras

Ao criar um pedido do administrador, os produtos no carrinho do cliente na barra lateral não desaparecerão quando adicionados ao pedido.

_ACP2E-3563 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### [Preparo2] Os cartões armazenados não estão visíveis no painel Administrador

Corrige o problema em que a opção de pagamento &quot;Cartão armazenado&quot; não aparecia mais no formulário de posicionamento de pedido de back-end após uma atualização.

_ACP2E-3830 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

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

_ACP2E-4052 - [Problema do GitHub](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Blocos brancos aparecem em ambos os lados do cabeçalho da grade de administração

Correção de um problema de alinhamento visual nas grades de administração. Anteriormente, ao rolar horizontalmente pelas grades de produtos no painel de administração, os blocos brancos apareciam desalinhados nos lados esquerdo e direito do cabeçalho da grade. Os elementos de cabeçalho de grade agora mantêm o alinhamento vertical adequado ao rolar a tela, fornecendo uma experiência visual mais limpa para administradores que gerenciam catálogos de produtos grandes.

_ACP2E-4104 - [Problema do GitHub](https://mcprod.pap-store.acer.com/index.html)_

#### O componente fileUploader da UI não está funcionando corretamente no 2. 4. 8- p1/ 2. 4- develop

Upload de arquivo aprimorado para o componente de interface do usuário personalizada com seleção múltipla para permitir upload ao clicar na área de upload.

_ACP2E-4162 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [No Local] Pedidos/Empresas/Clientes Recém-Criados Incluídos Automaticamente no Escopo &quot;Selecionar Tudo&quot; Durante o Processo de Seleção

Correção do problema em que a seleção manual de todos os registros em uma página de grade de administração obsoleta excluía involuntariamente todos os registros ao executar ações em massa. Anteriormente, a grade alternava automaticamente para o modo &quot;selecionar tudo&quot; internamente quando o número de itens selecionados correspondia à contagem total, fazendo com que as ações em massa afetassem todos os registros, em vez de apenas os explicitamente selecionados.

_ACP2E-4202 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### Solução de ACP2E-3362 funciona lentamente em MariaDB 10.6

Melhor desempenho da página de pesquisa de front-end em caso de um grande número de solicitações de pesquisa históricas.

_ACP2E-4225 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### O Filtro de Data não funciona de acordo com o fuso horário de armazenamento na grade Avisos de Crédito

Antes das listas de filtragem de correções por atributos de data estavam causando a ausência de itens devido a diferenças de fuso horário entre a data selecionada e as datas armazenadas Agora, após os filtros de data de correção são aplicados corretamente.

_ACP2E-4239 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### A caixa de diálogo do carregador de arquivos é aberta duas vezes quando o pagebuilder é instalado

Antes do botão Corrigir upload de componente personalizado, acionava duas vezes. Após a correção, o botão Upload funciona conforme esperado.

_ACP2E-4241 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### Erros de validação em atributos excluídos do cliente ao alterar dados do cliente.

Antes da correção, o salvamento do cliente e do endereço do cliente falharia se eles incluíssem várias opções de atributo que tinham sido excluídas. Após a correção, ambos podem ser salvos com êxito, mesmo quando várias opções de atributo ainda estiverem presentes.

_ACP2E-4281 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Aviso JS no painel do administrador: &quot;Esperava-se iniciar o carregador, mas não encontrou um no dom&quot;

Corrigido o aviso do JavaScript que aparecia no console do navegador quando os Gráficos eram ativados para o painel do administrador. Anteriormente, ao acessar o painel do administrador com os gráficos ativados, uma verificação de depuração obsoleta avisava incorretamente &quot;Esperava-se iniciar o carregador, mas não encontrou um no dom&quot;, mesmo que a funcionalidade estivesse funcionando corretamente.

_ACP2E-4336 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Configuração da [NUVEM] com configuração de dependência editável ao usar configuração de armazenamento com check-in padrão

Correção do problema em que os campos de Configuração do sistema podiam ser renderizados após o carregamento da página, apesar da opção &quot;Usar padrão/site&quot; estar marcada.

_ACP2E-4337 - [Problema do GitHub](https://mcstaging.pap-store.acer.com) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### O gráfico de ordem do painel do administrador é animado no tamanho final

O gráfico de ordem do painel do administrador será exibido imediatamente, sem a necessidade de uma animação de redimensionamento desnecessária.

_ACP2E-4398 - [Problema do GitHub](https://github.com/magento/magento2/issues/38860) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### O Page Builder não consegue salvar o conteúdo na visualização móvel devido a um erro JS (TypeError: não é possível ler propriedades de indefinido)

Correção de um problema que impedia salvar páginas no Page Builder ao adicionar banners na exibição móvel.

_ACP2E-4399 - [Problema do GitHub](https://github.com/magento/magento2/issues/38565) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### Interface do administrador, B2B

#### O logon B2B como cabeçalho do cliente ainda tem a marca Magento

Anteriormente, o cabeçalho da loja exibe &quot;Agora você está conectado como &lt;nome do cliente> na &lt;nome da loja>&quot; com a marca Magento. Que agora foi corrigida e o cabeçalho é exibido com a marca ADOBE.

_AC-14361 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### Interface do administrador, Catálogo

#### O salvamento do produto falha quando a Regra de catálogo está ativa e o modo em tempo real está ativado

Correção de um problema em que a indexação da regra de catálogo podia falhar com um erro de transação de DDL durante operações de salvamento do produto ao dissociar a indexação da Regra de Catálogo da transação do produto.

_ACP2E-4378 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Interface do administrador, Conteúdo

#### Exceção &quot;Não é possível criar representação para caminhos de ativos de mídia&quot; durante a inserção da imagem

Após remover os valores de Largura máxima e Altura máxima da configuração de Otimização de imagem da Galeria de mídia, o erro não ocorre mais durante o processo de otimização de imagem.

_ACP2E-3781 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Interface do administrador, Ordem

#### Criação de pedido de administrador: estouro no tamanho da sessão ao adicionar mais de 20 produtos (o tamanho da sessão excedeu o limite de 256 KB)

Solução de um estouro de tamanho de sessão durante a criação do pedido do administrador, impedindo que respostas grandes do HTML fossem armazenadas na sessão para solicitações JSON, garantindo que as adições de produtos em massa funcionassem sem problemas, sem fazer logout do administrador.

_AC-15893_

### Interface do administrador, Segurança

#### Gerenciamento de Senhas Fracas

O usuário administrador não pode ser salvo ao usar a mesma senha. Anteriormente, ele era salvo com sucesso sem uma validação adequada.

_ACP2E-3657 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Interface do Administrador, Imposto

#### Erro na interface do administrador da alíquota do imposto

Esse ticket corrigiu um problema de IU do administrador de taxa de imposto em que a alternância do país (por exemplo, de EUA → Reino Unido) ainda exibia o estado dos EUA selecionado anteriormente, enganando os usuários.
Na versão 2.4.9-alpha3, o campo de estado agora é redefinido para * quando o país selecionado não tem estados.

_AC-8440 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analytics/Relatórios

#### [Problema] adicionou o incluo na lista de permissões scp para o Analytics se você só usa o Google Analytics

Essa PR adiciona uma lista de permissões de CSP ao módulo do Google Analytics, permitindo que ele funcione de forma independente sem uma dependência do Google Adwords. O Google Analytics agora funciona corretamente mesmo quando o módulo Google Adwords está desativado.

_AC-16311 - [Problema do GitHub](https://github.com/magento/magento2/issues/40051) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40032)_

#### Cabeçalhos de arquivo duplicados em arquivos CSV de relatórios avançados, causando relatórios vazios

Após a correção, os relatórios gerados para o recurso de relatórios avançado não contêm mais linhas de cabeçalho duplicadas nos casos em que a contagem de linhas excede o tamanho do lote.

_ACP2E-4187 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### O relatório de carrinho abandonado contém caracteres inválidos

O Relatório de carrinho abandonado exportado como arquivo CSV agora contém caracteres renderizados corretamente para símbolos de moeda como rupia indiana quando aberto no MS Excel.

_ACP2E-4288 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Atualização para MDVA-19640 para compatibilidade com a versão 2.4.8

A correção move as tarefas de trabalho cron do Analytics do grupo padrão para o grupo do Analytics

_ACP2E-4309 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### As receitas não são exibidas em Pedidos/Relatórios de fatura no site/moeda Admin for Canada

Alguns relatórios relacionados a pedidos não estavam aplicando taxas de moeda de armazenamento. Após a correção, os relatórios aplicam corretamente as taxas de armazenamento configuradas.

_ACP2E-4361 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### falha na validação de campo da empresa para check-out do convidado

O check-out de convidado agora valida corretamente o campo da empresa.
Anteriormente, quando o atributo da empresa era obrigatório, o check-out do convidado falhava com o erro: &quot;A empresa é um valor obrigatório&quot;, mesmo quando o campo era preenchido.
AC-14987

_AC-14987 - [Problema do GitHub](https://github.com/magento/magento2/issues/40011) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Os produtos-render-info da API Rest retornam o preço final incorreto para o cliente conectado

O tíquete tem uma correção para a API Rest products-render-info retornar o preço final incorreto para o cliente conectado

_AC-5979 - [Problema do GitHub](https://github.com/magento/magento2/issues/35757)_

### B2B, carrinho e finalização

#### Nenhuma entidade com cartId = X erro é mostrado na Loja quando o usuário da empresa B2B faz logon no recurso de administrador &quot;Logon como cliente&quot;

Agora, o erro &quot;Nenhuma entidade com cartId = X&quot; não é mais visível após fazer logon com êxito no back-end do administrador ao usar o recurso &quot;Logon como cliente&quot;.

_ACP2E-3994 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### O endereço de faturamento ausente impede a realização do pedido com o método de envio &quot;Entrega na loja&quot;

Solução de um problema em que o endereço de cobrança não era preenchido automaticamente durante o check-out quando a opção Coleta na loja era selecionada como o método de entrega. Sem um endereço de cobrança, o check-out não poderia ser concluído.

_ACP2E-4030 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/42d23211)_

### Carrinho e saída

#### Atualização (mini)carrinho do Magento 2.4.7 sem quantidade decimal permitida

Agora, o Magento lida corretamente ao atualizar a quantidade com decimais do minicarrinho quando a localidade era NL (Holandês)

_AC-13238 - [Problema do GitHub](https://github.com/magento/magento2/issues/39236) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39669)_

#### [Problema] Adicione EventPrefix e EventObject para verificar o modelo de contrato

O sistema agora inclui EventPrefix e EventObject para o modelo de contrato de check-out, permitindo que os eventos sejam acionados com um prefixo de evento. Esse aprimoramento oferece mais flexibilidade para desenvolvedores ao trabalhar com eventos de contrato de check-out. Anteriormente, o modelo de contrato de check-out não aceitava EventPrefix e EventObject, limitando a capacidade de personalizar a manipulação de eventos.

_AC-13252 - [Problema do GitHub](https://github.com/magento/magento2/issues/32510) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32451)_

#### Experiência do desenvolvedor [Problema]: estilo de código AbstractItem de cotação (SOP-348 de SwiftOtter)

Esta Solicitação Pull corrige declarações de método enganosas para métodos Item Abstrato.

_AC-13334 - [Problema do GitHub](https://github.com/magento/magento2/issues/39340)_

#### As validações de quantidade de front-end de produto agrupado estão ausentes

Agora o sistema está funcionando bem e exibindo um erro de validação quando estamos tentando adicionar uma quantidade negativa e uma quantidade máxima

_AC-13524 - [Problema do GitHub](https://github.com/magento/magento2/issues/39479) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39480)_

#### [Problema] Atualizar subtotal.phtml

O sistema atualiza o subtotal.phtml com o espaçamento correto

_AC-13907 - [Problema do GitHub](https://github.com/magento/magento2/issues/39619) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39612)_

#### Não é possível fazer o pedido com o convidado

O Adobe Commerce agora permite que os compradores convidados façam pedidos com êxito quando o campo do nome do meio estiver configurado como obrigatório no Administrador. Anteriormente, no Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4), a configuração do nome do meio como necessário e o check-out como convidado impediam a colocação de pedidos mesmo quando um nome do meio era fornecido, bloqueando a conclusão do check-out. AC-14241

_AC-14241 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql] Não pode retornar nulo para o campo não anulável &quot;SeletedCustomizingOption.label&quot;

O sistema agora não lançará um erro interno do servidor com uma mensagem quando a opção selecionada não existir mais

_AC-14256 - [Problema do GitHub](https://github.com/magento/magento2/issues/39729) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39888)_

#### O GraphQL addWishlistItemsToCart não atualiza a quantidade de itens existentes do carrinho quando um item da lista de desejos é inválido (Magento 2.4.7-p3)

Correção de um problema em que a mutação addWishlistItemsToCart do GraphQL parava de ser processada quando um produto configurável inválido era encontrado. Após a correção, os itens válidos da lista de desejos são adicionados ao carrinho e as quantidades são atualizadas, enquanto os itens inválidos são ignorados e os erros apropriados são retornados.

_AC-14464 - [Problema do GitHub](https://github.com/magento/magento2/issues/39820) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] Não é possível fazer pedidos em que a Cidade tenha dígitos de 0 a 9, E comercial, ponto final ou parêntese no Nome da Cidade

Correção de um problema em que o check-out falhava em nomes de cidades contendo caracteres especiais como . , &amp; ou parênteses.
Agora, os pedidos com esses nomes de cidades são feitos com êxito sem erros de validação.

_AC-14495 - [Problema do GitHub](https://github.com/magento/magento2/issues/39854) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Prefixo de convidado não salvo no endereço de cotação 2.4.8

O prefixo de cliente convidado (Sr./Sra) agora é salvo durante a finalização da compra.
Anteriormente, as saudações selecionadas por clientes convidados eram perdidas antes de atingir o pedido final, enquanto todos os outros campos de endereço eram transferidos corretamente.
AC-14705

_AC-14705 - [Problema do GitHub](https://github.com/magento/magento2/issues/39915) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Subseleção de regra de vendas com condição de quantidade Falha ao aplicar

Correção de um problema em que as regras de preço do carrinho com condições de subseleção de produto não eram aplicadas na finalização da compra.
Agora, os descontos são aplicados com êxito de acordo com as regras configuradas.

_AC-14884 - [Problema do GitHub](https://github.com/magento/magento2/issues/39965) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### [Problema]: remover espaço no atributo de classe

O Sistema agora remove um espaço extra no atributo de classe

_AC-14939 - [Problema do GitHub](https://github.com/magento/magento2/issues/39977) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39970)_

#### Graphql - O carrinho de mesclagem não funciona corretamente quando a Backorder está ativada

Correção de um problema em que os itens do carrinho de convidado não eram mesclados ao carrinho do cliente durante a mesclagem do carrinho por meio do GraphQL.
Agora, o carrinho do cliente reflete corretamente a quantidade combinada de carrinhos do cliente e do convidado.

_AC-15148 - [Problema do GitHub](https://github.com/magento/magento2/issues/40064) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integração] [Check-out] Diretivas de dependência atualizadas no modelo de email de pagamento com falha

Falha no modelo de email de pagamento atualizado para manipular as diretivas depend corretamente.
A correção garante que o endereço e o método de envio sejam exibidos corretamente quando aplicável.
Anteriormente, esses campos estavam ausentes em emails de pagamentos com falha.

_AC-15363 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### A página [Carrinho] do carrinho de compras não é carregada quando o Imposto fixo do produto está habilitado

Correção de um problema em que a página do carrinho de compras entrava no carregamento infinito quando o Imposto Fixo do Produto (FPT) era ativado. O problema era causado por cálculos incorretos de subtotais devido ao imposto ser incluído no mesmo elemento HTML como o preço do item, levando a uma incompatibilidade entre os subtotais central e sumariado. Após a correção, o carrinho é carregado corretamente e exibe totais precisos.

_AC-16096 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Regra de preço do carrinho Ação &quot;Preço no carrinho&quot; condição, aplicando quando não deveria

Correção de um problema em que as regras de preço do carrinho com a condição &quot;Preço no carrinho menor que&quot; eram aplicadas incorretamente a produtos inelegíveis.
Agora, os cupons são validados e rejeitados corretamente quando os preços de itens do carrinho não atendem às condições configuradas da regra.

_AC-6997 - [Problema do GitHub](https://github.com/magento/magento2/issues/36433) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### [Problema] Definir preço em item de cotação em vez de base_price

O sistema manipula corretamente o preço do item da cota definido como base_price em vez do preço se você tiver várias moedas em um site no front-end

_AC-9985 - [Problema do GitHub](https://github.com/magento/magento2/issues/38094) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36878)_

#### Cotações persistentes expiradas não são excluídas por um trabalho cron sales_clean_quotes

As aspas persistentes expiradas agora são apagadas quando a tarefa cron &#39;persistent_clear_expired&#39; é executada. Anteriormente, as aspas persistentes expiradas não eram apagadas por nenhum outro trabalho cron.

_ACP2E-3493 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Erro &quot;Algo deu errado&quot; no check-out para empresa inativa

Antes da correção, a ação de logout não era concluída corretamente na página do carrinho se a empresa do usuário conectada não estava mais habilitada. Agora, se a empresa não estiver mais disponível, o logout será executado corretamente.

_ACP2E-3541 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### A seleção de endereços não é salva quando &quot;Fazemos check-out com vários endereços&quot;

Antes da correção ao cancelar a opção de envio múltiplo, o endereço não era pré-selecionado ao reverter para o envio múltiplo. Agora, o endereço padrão é substituído por uma das seleções feitas na tela de envio múltiplo.

_ACP2E-3646 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### [Cloud] Ordens recentes não aparecem na exibição de outra loja se as ordens forem criadas em uma exibição de loja

Solução de um problema em que a página &quot;Minha conta&quot; não exibia pedidos recentes de outras Exibições da loja na mesma loja. A lógica de recuperação do pedido foi atualizada para garantir uma visibilidade consistente do pedido em todas as Exibições da loja, alinhada ao comportamento da página &quot;Meus pedidos&quot;.

_ACP2E-3807 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### qtd. exibida como  0 na seção carrinho de compras do cliente administrador ao adicionar produtos do PACOTE  

A seção Carrinho de compras em Atividades do cliente agora exibe a quantidade correta. Anteriormente, a quantidade era mostrada como 0.

_ACP2E-3872 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

#### O desconto de envio gratuito da [Cloud] não é removido corretamente quando o carrinho não atende mais aos requisitos

O Subtotal (Excl. Imposto) na regra de preço do carrinho agora incorporará descontos das regras anteriores.

_ACP2E-3973 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Ordem duplicada encontrada para o mesmo cliente no Envio múltiplo

Solicitações simultâneas para fazer pedidos com vários endereços de entrega não resultam mais em pedidos duplicados para o mesmo cliente

_ACP2E-4117 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### A mensagem de notificação de limite de estoque excedido da [Nuvem] é exibida duas vezes quando o Limite de Falta de Estoque é atingido

Correção do problema em que as atualizações do carrinho podiam mostrar banners de erro duplicados. Anteriormente, após um erro de validação do AJAX, o backend adicionava a mesma mensagem novamente durante o envio do formulário, de modo que os compradores viam dois alertas idênticos. Agora, deixamos de adicionar a mensagem de backend extra, mantendo a página do carrinho em um único banner de erro claro.

_ACP2E-4192 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Para informações de faturamento, a validação no lado do servidor não está funcionando usando a API REST das informações de envio

A validação de dados de endereço do cliente foi aprimorada para ser mais consistente entre REST e GraphQl para check-out.

_ACP2E-4223 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Problema relacionado ao preço do produto na &lbrace;Cloud] na página do carrinho

Correção do problema de preço do produto no pacote na página do carrinho para lojas de várias moedas

_ACP2E-4245 - [Problema do GitHub](https://www.techbuyer.com/) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Gerenciar problemas de escopo de armazenamento do carrinho de compras

Agora, os erros do carrinho de compras serão exibidos para o usuário administrador ao gerenciar o carrinho de compras de um cliente atribuído a um site não padrão. Anteriormente, os erros não eram exibidos.

_ACP2E-4348 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### O cupom times_used é redefinido após o cancelamento parcial da NFF

A contagem times_used do cupom agora é atualizada corretamente quando um pedido é parcialmente cancelado.

_ACP2E-4365 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Carrinho e check-out, GraphQL

#### Erro ao mapear a mensagem para o código de erro ao fazer o pedido via GraphQL

As chamadas do GraphQL para fazer um pedido de um carrinho inexistente ou inativo agora retornam corretamente os códigos de erro CART_NOT_ATIVE ou CART_NOT_FOUND em todas as exibições de loja, corrigindo um problema em que as mensagens de erro traduzidas anteriormente resultavam em um código INDEFINIDO.

_ACP2E-3942 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQl] problema de desconto de item do carrinho de consulta em cotações virtuais

Solução de um problema em que a consulta do carrinho do GraphQL retornava um valor de desconto incorreto para cotações virtuais. Anteriormente, os descontos eram aplicados incorretamente a determinados produtos virtuais que não eram qualificados.

_ACP2E-4248 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2 cria outro problema

Quando uma solicitação de graphQL para um item com quantidade insuficiente é feita, uma mensagem de erro apropriada com um código de erro é retornada e, se a quantidade solicitada estiver disponível, a atualização do carrinho foi bem-sucedida.

_ACP2E-4404 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Carrinho e check-out, GraphQL, inventário/MSI

#### O atributo is_available em CartItemInterface retorna false mesmo quando o estoque comercializável está alto

O atributo is_available retorna true quando o estoque vendável está alto. Anteriormente, retornava sempre falso.

_ACP2E-3885 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Carrinho e check-out, inventário/MSI

#### Erro 414 no ponto de extremidade &#39;Procurar localização de retirada&#39; com tamanhos de carrinho grande

Selecionar uma loja durante a finalização da compra usando &quot;Escolher na loja&quot; não falha mais devido a URLs longos quando muitos produtos estão no carrinho.
Anteriormente, isso acionava um erro 414 causado por URLs excessivamente longos gerados durante a seleção da loja, impedindo que os clientes concluíssem o check-out.

_ACP2E-4266 - [Problema do GitHub](https://mcstaging.casamyers.com.mx/) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/ae1f272f)_

### Carrinho e check-out, promoção

#### Exibir saldo no Cartão-presente não é restrito pelo Escopo do Site

Restrição da verificação de saldo do Cartão-presente com o Escopo do site atribuído.

_ACP2E-4379 - [Problema do GitHub](https://www.panini.it)_

### Carrinho e check-out, segurança

#### [NUVEM] Obtendo 404 para arquivo JS na página de check-out na primeira tentativa após a implementação do patch sri

Antes das correções, os mixins não tinham sido carregados no carrinho e o check-out quando a minificação e o empacotamento estavam ativados. Após a correção, todos os mixins devem ser carregados conforme esperado.

_ACP2E-4128 - [Problema do GitHub](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Carrinho e check-out, envio

#### [Linha principal] A regra de preço do carrinho não respeita o envio múltiplo

Antes da implementação desta correção, a regra de preço do carrinho para produtos de vários envios não era aplicada corretamente quando as condições de subseleção eram aplicadas e o frete gratuito era ativado. No entanto, desde que a correção foi aplicada, a regra de preço do carrinho para carrinhos de vários envios agora funciona conforme esperado.

_ACP2E-3666 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo

#### Duplicar fpc de cache para a mesma página com a mesma consulta

O sistema agora identifica corretamente e usa o mesmo Cache de página cheia (FPC) para páginas com os mesmos parâmetros de consulta, independentemente da ordem ou dos caracteres à direita. Isso evita o aumento desnecessário do tamanho da pasta de cache da página. Anteriormente, o sistema criaria um identificador FPC diferente para a mesma página se a ordem dos parâmetros de consulta fosse diferente ou se houvesse caracteres à direita, resultando em um aumento no tamanho da pasta de cache da página.

_AC-10722 - [Problema do GitHub](https://github.com/magento/magento2/issues/38269) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38270)_

#### Indexação de colunas necessárias ausente na tabela catalog_product_entity_int

Adição da indexação ausente das colunas necessárias na tabela catalog_product_entity_int

_AC-10844 - [Problema do GitHub](https://github.com/magento/magento2/issues/38315) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38316)_

#### Erro de escopo no recurso de URL do catálogo (_getCategories)

Essa PR adiciona um fallback ao escopo padrão se não houver um valor definido no escopo de armazenamento no recurso de URL de categoria.

_AC-11011 - [Problema do GitHub](https://github.com/magento/magento2/issues/38393) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problema] Verifique se o OpenGraph pode mostrar o preço

O sistema está funcionando bem quando usamos plug-in que oculta o preço e com esse preço de alteração não está visível na tag OG.

_AC-11635 - [Problema do GitHub](https://github.com/magento/magento2/issues/38512) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38510)_

#### Problema de arredondamento nos preços ao adicionar imposto à exibição de preços

O Sistema agora corrige o problema de arredondamento nos preços ao adicionar imposto para exibir preços

_AC-11725 - [Problema do GitHub](https://github.com/magento/magento2/issues/18025) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/35730)_

#### [Problema] Permitir condições de regra de catálogo personalizado

Correção de um problema que impedia o uso de condições de regra de catálogo personalizadas devido à verificação de tipo estrita. A correção substitui a verificação de igualdade de classe por instanceof, permitindo que as classes de condição personalizadas funcionem corretamente e permitindo a validação e a indexação bem-sucedidas da regra.

_AC-13338 - [Problema do GitHub](https://github.com/magento/magento2/issues/39339) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Opções configuráveis de perda de produtos quando adicionadas à lista de desejos

Correção de um problema em que as opções configuráveis do produto eram perdidas após adicionar o produto à lista de desejos. Agora, as opções selecionadas são mantidas, permitindo que o produto seja adicionado ao carrinho sem problemas, sem solicitar que os usuários selecionem novamente as opções.

_AC-13373 - [Problema do GitHub](https://github.com/magento/magento2/issues/39363) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### O preço especial não é exibido corretamente para o produto secundário do produto configurável (produto simples)

Correção de um problema em que o preço especial do produto filho (simples) de um produto configurável não era exibido corretamente na página da lista de produtos quando &quot;Usado na lista de produtos&quot; estava definido como Não. Agora, o preço especial é mostrado corretamente juntamente com o preço normal, garantindo uma exibição consistente dos preços em todos os tipos de produtos.

_AC-13594 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### API REST [Bug]: a opção Atualizar preços especiais não define valores para todas as exibições de loja

A REST API agora atualiza preços especiais para todas as visualizações de loja em um site.
Anteriormente, a atualização de preços especiais por meio da API REST afetava somente a visualização de loja especificada, não todas as visualizações de loja no site.
AC-13671

_AC-13671 - [Problema do GitHub](https://github.com/magento/magento2/issues/39521) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Problemas com o escopo de preço e config.php

No Magento 2.4.2, alterar o escopo de preço por meio de config.php não atualiza corretamente o valor is_global em catalog_eav_attribute para o atributo price.
Como resultado, os preços dos produtos permanecem globais e não podem ser salvos por site, mesmo quando o escopo de preços está definido como site.
A solução alternativa requer a atualização manual da coluna is_global no banco de dados, o que não é ideal para ambientes de produção.
Esse comportamento é consistente com o design padrão do Magento, em que o escopo de preço é Global ou Site, mas não por exibição de loja.

_AC-13857 - [Problema do GitHub](https://github.com/magento/magento2/issues/33559)_

#### Erro PHP [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] despercebido

Alteração do nome de uma variável de loop para adicionar corretamente os dados &quot;_cache_instance_product_ids&quot; no produto em questão para serem usados em chamadas subsequentes.

_AC-14159 - [Problema do GitHub](https://github.com/magento/magento2/issues/39641) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39642)_

#### A Pesquisa Elástica interfere na ordem de classificação padrão dos produtos (alterando primeiro o mais recente para o mais antigo primeiro)

O Sistema agora classifica Os produtos mais recentes no banco de dados (aquele com a entity_id mais alta) são mostrados primeiro

_AC-14411 - [Problema do GitHub](https://github.com/magento/magento2/issues/31043) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36900)_

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

#### Uma cadeia de consulta `?p=` negativa causa uma exceção do Elasticsearch

O Sistema agora aborda o valor ?p= negativo na paginação Categoria, que atualmente resulta em exceção e é considerado uma solicitação válida

_AC-15191 - [Problema do GitHub](https://github.com/magento/magento2/issues/40079) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40080)_

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

#### O preço incorreto do produto é exibido no carrinho de compras com diferentes moedas em diferentes visualizações da loja

Correção de um problema em que os preços incorretos do produto eram exibidos no carrinho de compras ao usar moedas diferentes nas exibições da loja. Após a correção, o carrinho agora mostra o preço convertido correto com base na moeda configurada, garantindo a consistência entre a página do produto e o carrinho.

_AC-15385 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Exibição de preço &quot;Tão baixo quanto&quot; incorreta para produtos configuráveis quando o FPT está habilitado

Confirmado que o preço incorreto &quot;Tão baixo quanto&quot; para produtos configuráveis quando o FPT foi ativado era causado pela aplicação dupla do imposto; a correção garante que o cálculo de preço final respeita a configuração do imposto e agora exibe o preço correto.

_AC-15718 - [Problema do GitHub](https://github.com/magento/magento2/issues/40171) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### A complexidade de tempo de _loadAttributes em Eav\Model\Entity\Collection\AbstractCollection aumenta com o número de produtos no carrinho e nos atributos

Este _loadAttributes otimizado de PR no Eav\Model\Entity\Collection\AbstractCollection, substituindo loops aninhados por união de matriz (+) e reduzindo as chamadas para _setItemAttributeValue, melhorando o desempenho de carrinhos de produtos grandes.

_AC-15833 - [Problema do GitHub](https://github.com/magento/magento2/issues/40216) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40217)_

#### Interação Registrada entre o Cache de Coleção e a Galeria de Produtos Configuráveis

Solução de um problema de armazenamento em cache com galerias de produtos configuráveis adicionando uma verificação de tipo defensiva para garantir que media_gallery_images seja sempre tratado como uma coleção, evitando erros fatais causados por dados de cache corrompidos.

_AC-16066 - [Problema do GitHub](https://github.com/magento/magento2/issues/33965) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

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

#### [Linha Principal] [NUVEM] O redimensionamento de imagens consome mais de 400 GB de espaço em disco

Após a correção, o comando `catalog:images:resize` usado com o sinalizador `--skip_hidden_images` não gerará caches de imagem para sites em que não há imagens.

_ACP2E-3869 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### A geração de imagens dinâmicas gera um grande número de imagens

Após a correção, as imagens serão geradas somente para os sites aos quais o produto está atribuído.

_ACP2E-3927 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### A ID do país fornecida não existe - Irlanda (IE)

Após a correção, os códigos postais da Irlanda estão disponíveis para procurar locais de coleta.

_ACP2E-3932 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### O erro 500 ocorre no front-end, devido à estrutura de layout incorreta ser armazenada em cache no layout

Correção de um problema em que uma página retornava um código de erro 500, devido a uma estrutura de layout incorreta ser armazenada em cache no layout

_ACP2E-4040 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Relatório de exibições de produto incorreto - Contagem menor em comparação à disponibilidade geral

Correção de um erro em que a tabela report_viewed_product_index não mostrava o número correto de exibições da página do produto.

_ACP2E-4045 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### Erro de validação para o campo de valor de desconto da regra de Preço de Catálogo em Atualização Programada

Anteriormente, antes de corrigir esse problema, para a atualização da programação para a regra de preço do catálogo, se a quantia de desconto for by_fixed, então ela não era validada corretamente por causa da regra de intervalo de números de validação. Depois que essa correção for aplicada, a validação funcionará corretamente para a regra de preço fixo do catálogo.

_ACP2E-4054 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Falha na validação de IVA devido ao limitador de taxa da API de IVA - aciona alteração de grupo de clientes falso positivo

Otimização dos pedidos para a ferramenta de validação Europa Vat, que resulta em menos erro &quot;limitador de taxa&quot;

_ACP2E-4072 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Exclusão em Massa no Indexador Principal Acionando Erro de Tamanho Máximo do Conjunto de Gravação na Produção

Otimiza a limpeza do índice de produto da regra de catálogo implementando duas estratégias de exclusão com base no volume de dados.

_ACP2E-4085 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### Os produtos são exibidos como desativados

Após a correção, os produtos desativados não estarão presentes no widget produtos.

_ACP2E-4136 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Nuvem] Erros com entradas duplicadas (temp_category_descendants_%)

Correção de um problema com entradas duplicadas durante atualizações programadas de criação para ambientes com um alto número de categorias aninhadas

_ACP2E-4159 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [NUVEM] Comparar problema de incompatibilidade de Contagem de Produtos para diferentes armazenamentos

A lista de produtos de comparação agora funciona corretamente após alternar para outra loja

_ACP2E-4249 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Não há opção para &quot;usar padrão&quot; em &quot;Imagens e vídeos&quot; para a atribuição da função de imagem

As opções &quot;Usar valor padrão&quot; foram adicionadas à seção de imagens e vídeos do produto, permitindo a herança das configurações do escopo padrão.

_ACP2E-4280 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Produtos da categoria restrita ainda contados na lista de desejos após a atualização do grupo do cliente

Antes da correção, as permissões de categoria não eram aplicadas corretamente aos itens da lista de desejos do cliente. Agora, após a correção, os itens da lista de desejos são exibidos e paginados corretamente na Web e no GraphQL.

_ACP2E-4294 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### [Problema de preço de produto de pacote na &lbrace;Cloud] em PDP e PLP

Preço do pacote O produto com preço normal é mostrado corretamente na PDP/PLP para moeda não padrão

_ACP2E-4298 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### O cliente pode fazer o pedido de um produto inacessível após a alteração do grupo de clientes

Anteriormente, ao alterar o grupo de clientes de administrador, o catálogo e o carrinho de front-end não refletiam as alterações nas permissões do catálogo. No entanto, depois de aplicar essa correção, a cotação de front-end agora muda de acordo com as permissões do catálogo atualizadas quando o grupo de clientes é alterado de administrador.

_ACP2E-4300 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Reindexação paralisada devido ao alto uso de memória

Correção do problema em que o indexador de regras de catálogo consumia muita memória e não era concluído, causando instabilidade e erros de memória insuficiente.

_ACP2E-4303 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### O Link de Visualização de Atualização Agendada do [CMS] redireciona para a Página de Manutenção

A Visualização de atualização programada do link da página inicial com produtos configuráveis exibe corretamente a lista de produtos. Anteriormente, ele redirecionava os usuários para a página de manutenção

_ACP2E-4401 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Catálogo, GraphQL

#### Cálculo de desconto inválido do GraphQl

O GraphQL agora exibe corretamente as porcentagens de desconto e os preços base quando os preços de catálogo são configurados para incluir imposto. Anteriormente, ocorriam erros de arredondamento, como exibir 19,99% em vez de 20%.

_ACP2E-3993 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### O campo GetCart GraphQL Media Gallery retorna dados vazios após a liberação de cache

Após a correção, a galeria_de_mídia do produto é retornada conforme esperado na resposta da GraphQL para a solicitação do carrinho.

_ACP2E-4185 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Catálogo, GraphQL, Pesquisa

#### O graphql de produtos retornou categorias desabilitadas nas agregações de categorias

Após a correção, as categorias desativadas não são retornadas para a solicitação de GraphQl de produtos.

_ACP2E-2885 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo, Desempenho

#### As categorias no administrador estão carregando muito lentamente

O desempenho do carregamento da categoria foi significativamente melhorado. Anteriormente, levava muito tempo para carregar a categoria que causava um problema de tempo limite.

_ACP2E-3891 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catálogo, Preços

#### Desconto de regra de preço de catálogo incorreto aplicado ao produto filho

Corrige o problema em que a regra de preço de catálogo para a variação é substituída pelo produto configurável principal, caso ambas as regras tenham a mesma prioridade.

_ACP2E-3693 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### Problema de preço de produto do pacote [Cloud]

Preço do pacote O produto com preço especial é mostrado corretamente na PDP/PLP para moeda não padrão

_ACP2E-4110 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6e134409)_

### Catálogo, Produto

#### [Bug Aleatório] A biblioteca Fotorama não está carregada

O sistema agora garante que a biblioteca Fotorama seja carregada corretamente, permitindo que todas as imagens anexadas sejam exibidas na galeria de imagens, conforme esperado. Anteriormente, somente a primeira imagem estava visível devido a um problema com a biblioteca Fotorama não carregando corretamente.

_AC-12124 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### O link &quot;Adicionar produtos manualmente&quot; deve estar sempre visível

Correção de um problema em que o link &quot;Adicionar produtos manualmente&quot; não estava visível ao criar um produto configurável sem configurações existentes. O link agora é sempre exibido, permitindo que os administradores associem produtos simples facilmente sem criar configurações fictícias.

_AC-13866 - [Problema do GitHub](https://github.com/magento/magento2/issues/39595) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Editar um produto no backend Remove casas decimais extras do preço de opções do produto

Correção de um problema em que a edição de um produto no preço de opção de produto truncado pelo administrador era feita em duas casas decimais. O sistema agora preserva os preços com maior precisão decimal, garantindo que os valores precisos sejam retidos após salvar.

_AC-14050 - [Problema do GitHub](https://github.com/magento/magento2/issues/39655) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

### Catálogo, Pesquisa

#### Solicitação RestApi &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; falha com erro de tempo limite

As solicitações de API REST de categoria não falham mais com erros de tempo limite.
Anteriormente, as solicitações para /rest/default/V1/categories?searchCriteria[page_size]=1 podiam falhar com um tempo limite após determinadas alterações de código.
AC-13358

_AC-13358 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Conteúdo

#### graphql (magento 2.4.6-p4 ) - erro ao tentar obter a página do cms com status de inativo

Correção de um problema em que a consulta do GraphQL para uma página do CMS desativada retornava um erro interno do servidor.
Agora, a consulta obtém uma resposta adequada sem erros.

_AC-12302 - [Problema do GitHub](https://github.com/magento/magento2/issues/38877) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### O formulário de compartilhamento da lista de desejos permite código aleatório nos campos de nome

Correção de uma vulnerabilidade crítica de Injeção de modelo do lado do servidor (SSTI) no formulário de compartilhamento de lista de desejos, em que os códigos mal-intencionados podiam ser inseridos no campo de mensagem e enviados por email. A atualização adiciona validação de entrada para bloquear diretivas de modelo e padrões não seguros, agora mostrando uma mensagem de erro quando conteúdo inválido é detectado.

_AC-12730 - [Problema do GitHub](https://github.com/magento/magento2/issues/39024) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### A inserção de csp_whitelist.xml no tema não funciona e cria um problema intermitente

Implementação do armazenamento em cache da lista de permissões da CSP por área do site.

_AC-13069 - [Problema do GitHub](https://github.com/magento/magento2/issues/38933) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39672)_

#### Depois da atualização para o magento 2.4.7 p2, não é possível visualizar a galeria de mídia de arquivos recém-carregados

Os arquivos carregados recentemente agora aparecem na Galeria de mídia após a atualização.
Anteriormente, após a atualização para o Magento 2.4.7 p2, as imagens recém-carregadas não eram exibidas na Galeria de mídia até que uma sincronização manual fosse executada.
AC-13262

_AC-13262 - [Problema do GitHub](https://github.com/magento/magento2/issues/39275)_

#### A galeria de mídia exibe imagens incorretas de diretórios com nomes idênticos, mas com letras maiúsculas e minúsculas diferentes

O Sistema agora aborda um problema em que os arquivos carregados em um diretório específico na Galeria de mídia também ficam visíveis em diretórios com nomes semelhantes, mas com letras maiúsculas e minúsculas diferentes.

_AC-13489 - [Problema do GitHub](https://github.com/magento/magento2/issues/39382) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39502)_

#### A remoção completa de uma imagem de galeria da be mantém as funções/tipos de escopo definidos (base/pequeno/miniatura) e, após adicionar novamente as funções/tipos &quot;antigos&quot;, são exibidas

O sistema está funcionando como esperado nos escopos de armazenamento. As imagens herdam as funções/tipos da nova imagem adicionada de acordo com o escopo padrão

_AC-13556 - [Problema do GitHub](https://github.com/magento/magento2/issues/39481) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Pequeno Erro] O Filtro do Painel de Administração `listing component` não pode ser acessado quando o valor do campo contém `\`

O sistema está funcionando bem ao filtrar o título da página com uma barra (por exemplo: Magento\Store)

_AC-13661 - [Problema do GitHub](https://github.com/magento/magento2/issues/39513) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39535)_

#### Erro: erro de script para &quot;Magento_Catalog/js/validate-product&quot; para pagebuilder do conteúdo administrativo com carregamento de produtos

Esta PR corrige o erro de script para catalogAddToCart ao editar o pagebuilder com a condição de produtos

_AC-13891 - [Problema do GitHub](https://github.com/magento/magento2/issues/39604) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39677)_

#### Erro de script catalogAddToCart ao configurar o Widget de produto.

Correção de um erro de script que ocorria ao configurar o widget Produtos com a &quot;Combinação de condições&quot; no Page Builder. O problema era causado pela ausência de arquivos JS de front-end, resultando em erros de console. Após a correção, o widget é carregado corretamente sem erros no console.

_AC-13892 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Bloquear seleção em widgets com o mesmo identificador

O Sistema agora lida corretamente com a seleção de blocos ao criar widgets quando temos os mesmos blocos de identificador

_AC-14132 - [Problema do GitHub](https://github.com/magento/magento2/issues/39692) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39722)_

#### &quot;A página do CMS com a ID &quot;0&quot; não existe&quot; inundação de log

O sistema está funcionando como esperado depois de criar um usuário administrador e ao criar uma nova página, system.log não tem mensagens de erro

_AC-14254 - [Problema do GitHub](https://github.com/magento/magento2/issues/39743) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39746)_

#### Loop infinito de consulta de rota [GraphQl]

Esse ticket corrigiu o problema em que uma consulta de rota do GraphQL com Caminho de solicitação e Caminho de destino idênticos causava um loop infinito e eventualmente expirava.
Na versão 2.4.9-alpha3, o query agora retorna a resposta de erro correta em vez de fazer loop.

_AC-14269 - [Problema do GitHub](https://github.com/magento/magento2/issues/39707) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### O mapa de site inexistente responde com a imagem do produto

O Sistema agora corrige quando acessamos o mapa de site inexistente responde com a imagem do produto com a Resposta: 404 NÃO ENCONTRADO

_AC-14295 - [Problema do GitHub](https://github.com/magento/magento2/issues/39756) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40135)_

#### Os widgets de link do catálogo usam URL incorreto

O Sistema agora lida corretamente com widgets após adicionar link de produto de catálogo e link de categoria de catálogo e também mostra urls corretos na fonte html

_AC-14437 - [Problema do GitHub](https://github.com/magento/magento2/issues/39464) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39710)_

#### O prefixo da tabela não é levado em conta

Agora, o Adobe Commerce respeita corretamente os prefixos de tabela do banco de dados ao carregar a grade de tema Design > Configuração no Admin. Anteriormente, no Adobe Commerce 2.4.8 com um prefixo de tabela configurado em app/etc/env.php, navegar até Conteúdo > Design > Configuração resultava em um erro porque o prefixo da tabela não era levado em conta e a grade de temas não era renderizada.

_AC-14556 - [Problema do GitHub](https://github.com/magento/magento2/issues/39847) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Altere a constante IMAGE_FILE_NAME_PATTERN para pública visível, para obter mais flexibilidade

A constante IMAGE_FILE_NAME_PATTERN em GenerateRenditions.php foi tornada pública para permitir aos desenvolvedores mais flexibilidade ao trabalhar com representações de imagem. A correção está incluída no Magento 2.4.9-alpha3 com cobertura total de teste de unidade e integração.

_AC-15338 - [Problema do GitHub](https://github.com/magento/magento2/issues/39733) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Método de envio incorreto é exibido na página de revisão de pedido para envio múltiplo

Correção de um problema na finalização de remessa múltipla em que a página revisar pedido exibia um custo de envio incorreto (5 INR em vez de 10 INR); a atualização garante que a quantidade de envio correta seja mostrada para cada endereço.

_AC-15664 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### falha na configuração bin/magento:show(ou set) design/theme/theme_id

Correção de um problema em que os comandos CLI bin/magento config:show e config:set falhavam para o caminho design/theme/theme_id apesar da configuração estar presente.
Agora, os comandos são executados com êxito e permitem visualizar e definir a ID do tema sem erros.

_AC-5915 - [Problema do GitHub](https://github.com/magento/magento2/issues/35751) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Não é possível carregar a imagem com largura relativamente pequena

O sistema não falha mais ao redimensionar a imagem com largura relativamente pequena até sua altura.

_ACP2E-3558 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### O componente de Produto do Page Builder não funciona se o usuário não tiver permissão de Widget

Antes da correção, ao acessar um widget sem permissões, a página gerava um erro genérico e exibia um GIF &quot;carregando&quot;. Agora, após a correção, uma janela modal é exibida com &quot;Desculpe, você precisa de permissões para visualizar este conteúdo&quot;. mensagem.

_ACP2E-3664 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Caminho de configuração incorreto para configuração de estilo de caminho de armazenamento remoto

Após a correção, definir a configuração de estilo do caminho de armazenamento remoto afetará a configuração real de estilo do caminho AWS S3.

_ACP2E-3734 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### A ordem do Widget de produto do Page Builder não é aplicada no GraphQL

Corrige o problema em que a resposta de consulta de &quot;rota&quot; do GraphQL não retornava produtos na ordem de classificação correta em um tipo de conteúdo de Produtos do Page Builder.

_ACP2E-3898 - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problema na exibição de preços em vitrines em outros idiomas devido à versão da biblioteca ICU

Após a correção, o preço do produto é exibido corretamente no local Hebraico (Israel).

_ACP2E-3938 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Atualizando configuração de design limpa do código da loja

Correção do problema em que a atualização do código de exibição de armazenamento limpava as configurações de Design devido à atualização incorreta do cache de configuração.

_ACP2E-3941 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Page Builder - Problema da lógica de condição do produto (a lógica OR se comporta incorretamente mostrando menos produtos)

O widget Produtos do Page Builder agora retorna o resultado correto quando um atributo com escopo global é usado na condição &quot;Corresponder qualquer&quot;

_ACP2E-4096 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### O carrossel de produtos adiciona produtos incorretos ao Page Builder

Antes da correção, um produto configurável teria sido incluído automaticamente nas listagens do carrossel de produtos do PageBuilder se qualquer um de seus filhos tivesse atendido às condições de filtragem. Agora, após a correção, o produto principal será incluído somente se o produto secundário não estiver visível por conta própria.

_ACP2E-4341 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### O widget Lista de produtos retorna um resultado incorreto se várias categorias forem listadas na condição de categoria

O widget &quot;Lista de produtos do catálogo&quot; agora exibirá resultados precisos quando várias categorias forem listadas na condição &quot;Categoria é uma das&quot;. Anteriormente, somente a primeira categoria na lista era processada.

_ACP2E-4353 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a3b7032) - [Contribuição de código do GitHub](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [Nuvem] A criação de pastas da Galeria de Mídia exige a permissão delete_folder na Galeria de Mídia Nova - as funções com apenas create_folder não podem criar pastas

Anteriormente, antes da implementação dessa correção, um usuário administrador com permissão apenas para criar pasta de conteúdo não podia criar uma pasta na galeria de mídia do CMS. No entanto, após a correção, os criadores de conteúdo na galeria de mídia agora podem criar pastas com somente a permissão criar pasta.

_ACP2E-4376 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS] Duplicando uma página do CMS

Antes dessa correção, a duplicação de uma página cms com atualização de layout personalizada teria falhado. Agora, as páginas do CMS com Atualizações de layout personalizadas podem ser duplicadas sem erros.

_ACP2E-4449 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Cliente/ Clientes

#### Exceção na loja quando o administrador adiciona o bloco CustomerCustomAttribute por meio do conteúdo da página do CMS

Correção de um problema em que a adição do bloco CustomerCustomAttribute por meio do conteúdo da página do CMS causava uma exceção de vitrine e impedia o carregamento da página.
A loja agora é exibida normalmente e mostra uma mensagem significativa quando o conteúdo não pode ser renderizado, evitando erros críticos.

_AC-11004_

#### A Grade Admin On-Line Dos Clientes Agora Mostra Linhas Duplicadas Sempre Que Um Usuário Faz Logon, Sair E Entrar

Correção de um problema em que a grade de administração de Clientes agora online exibia linhas duplicadas quando um cliente fazia logoff e logon novamente.
A grade agora atualiza o registro existente com a atividade mais recente em vez de criar entradas duplicadas, garantindo um rastreamento preciso da sessão do cliente.

_AC-11511 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/528af81a)_

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

#### Código de conclusão do módulo desabilitado.

Este escape de solicitação de pull desativava os módulos antes da compilação do código.

_AC-10933 - [Problema do GitHub](https://github.com/magento/magento2/issues/38241) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39723)_

#### Erro ao executar a configuração do comando :upgrade com o gatilho DB personalizado

Os gatilhos de banco de dados personalizados não causam mais erros durante a instalação:upgrade.
Anteriormente, executar a instalação bin/magento:upgrade com um gatilho de banco de dados personalizado (por exemplo, APÓS INSERT na tabela de armazenamento) poderia resultar no erro:
&quot;Aviso: Tentando acessar deslocamento de matriz no valor do tipo nulo em vendor/magento/framework/Mview/View/Subscription.php na linha 357&quot;
AC-11487

_AC-11487 - [Problema do GitHub](https://github.com/magento/magento2/issues/38481)_

#### [Problema] Tornar a assinatura do método consistente com a interface

A assinatura de método para getAttributes agora é consistente com sua interface, evitando erros ao substituir o método. Anteriormente, as inconsistências na assinatura do método causavam erros ao tentar substituir o método getAttributes.

_AC-11578 - [Problema do GitHub](https://github.com/magento/magento2/issues/38501) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/31955)_

#### O formulário de entidade de site/grupo/loja não pode ser estendido com elemento de formulário de vários valores para atributos de extensão

Essa PR permite que elementos de formulário multivalor enviem dados para o formulário de site/grupo/loja.

_AC-11657 - [Problema do GitHub](https://github.com/magento/magento2/issues/24070) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problema] Corrigir regra de validação de emails para o componente da interface do usuário

O sistema agora valida corretamente vários endereços de email inseridos nos componentes da interface do usuário, garantindo que cada email seja reduzido e validado corretamente. Anteriormente, o sistema usava um método incorreto para cortar endereços de email, o que poderia levar a erros de validação.

_AC-11719 - [Problema do GitHub](https://github.com/magento/magento2/issues/38528) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problema] Remover uso do resolvedor de escopo

Esta PR resolve as configurações de URL do Administrador globalmente em vez do armazenamento atual

_AC-11736 - [Problema do GitHub](https://github.com/magento/magento2/issues/38566) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38554)_

#### [Problema] Remover métodos redundantes

Qualidade do código: removeu métodos redundantes em operações assíncronas e componentes de vendas que chamavam apenas métodos principais sem adicionar funcionalidade, melhorando a manutenção do código.

_AC-11915 - [Problema do GitHub](https://github.com/magento/magento2/issues/29748) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/29147)_

#### Modelo Magento_Theme title.phtml inválido para PHP 8.2

Esta solicitação pull corrige um problema quando a página do CMS criada com o cabeçalho nulo como no Php 8.x transmitindo null para trim() gera uma exceção: funcionalidade obsoleta: trim(): transmitindo null para o parâmetro #1 ($string) do tipo string

_AC-12856 - [Problema do GitHub](https://github.com/magento/magento2/issues/39092) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39398)_

#### a validação de xsd falha em arquivos etc/adminhtml/system.xml que contêm comentários abaixo de itens de campo.

Esta PR corrige as definições do esquema XML no phpstorm para o nó comment

_AC-12945 - [Problema do GitHub](https://github.com/magento/magento2/issues/39148) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39867)_

#### Exposição da versão do Magento por meio da rota de configuração com a configuração padrão do Nginx

O sistema agora está funcionando como esperado e não expõe a versão exata do Magento que o site está executando

_AC-13205 - [Problema do GitHub](https://github.com/magento/magento2/issues/39227) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problema] Descompacte argumentos de objeto como parâmetros nomeados

O sistema agora utiliza o recurso do PHP 8.1 de desempacotar array com parâmetros nomeados, o que elimina a necessidade de chamadas de array_values e potencialmente melhora o desempenho geral. Anteriormente, o sistema exigia chamadas de array_values para argumentos de objeto de desempacotamento.

_AC-13210 - [Problema do GitHub](https://github.com/magento/magento2/issues/39233) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37411)_

#### [Problema] refatorar endereço de cotação fazer validar método

Esta PR inclui melhorias de legibilidade para o método doValidate.

_AC-13214 - [Problema do GitHub](https://github.com/magento/magento2/issues/38230) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38219)_

#### opção do Magento — magento-init-params nunca usado ao executar a cli?

A opção —magento-init-params agora é usada ao executar comandos CLI.
Anteriormente, transmitir —magento-init-params para comandos CLI não tinha efeito em parâmetros como MAGE_MODE.
AC-13231

_AC-13231 - [Problema do GitHub](https://github.com/magento/magento2/issues/39248) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### declaração de tipo incorreto de getItemsByColumnValue

O sistema agora define corretamente o parâmetro de entrada $value como um tipo primitivo, não uma matriz, na função getItemsByColumnValue, garantindo que a função retorne a coleção esperada. Anteriormente, se uma matriz com um único valor fosse usada como o parâmetro de entrada, a função retornaria como nulo e os IDEs a marcariam como um erro.

_AC-13240 - [Problema do GitHub](https://github.com/magento/magento2/issues/33070) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33120)_

#### Ao usar o armazenamento de arquivos para o provedor de bloqueio, obtemos um diretório de arquivos em constante crescimento sem que ocorra qualquer limpeza

Este pull request apresenta um novo cronjob que é executado uma vez por dia e procura por arquivos bloqueados que não foram modificados nas últimas 24 horas e que podem, portanto, ser removidos com segurança. Isso manterá o conteúdo do diretório de arquivos de bloqueio sob controle.
Este cronjob somente executará algo quando o provedor de bloqueio estiver configurado para usar arquivos, não quando um dos outros for usado (banco de dados - o padrão, zookeeper ou cache)

_AC-13367 - [Problema do GitHub](https://github.com/magento/magento2/issues/39369) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39372)_

#### [Limpeza de problema]: não use o valor de retorno nulo das chamadas de método.

Essa PR faz uma limpeza mínima. Às vezes, chamamos métodos que não retornavam nada (void) e, em seguida, usamos esse valor de resultado. O que não é realmente necessário.

_AC-13664 - [Problema do GitHub](https://github.com/magento/magento2/issues/39524) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39516)_

#### Chaves de cache associadas ao FPC em implementações de várias lojas do Magento 2.4.7

Correção de um problema em que as chaves de cache de Full Page Cache (FPC) nas configurações de várias lojas não incluíam MAGE_RUN_CODE e MAGE_RUN_TYPE, causando um comportamento inconsistente da chave de cache em comparação às versões anteriores. Agora, as chaves de cache incluem corretamente o contexto do armazenamento, garantindo o isolamento adequado do cache entre os armazenamentos.

_AC-13719 - [Problema do GitHub](https://github.com/magento/magento2/issues/39456) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problema] [PHPDOC] Corrigir phpdoc inválido para Magento\Framework\Message\ManagerInterface

Esta PR corrige o phpdoc inválido para \Magento\Framework\Message\ManagerInterface e remove todos os phpdoc duplicados em \Magento\Framework\Message\Manager (use a sintaxe inheritdoc).

_AC-14312 - [Problema do GitHub](https://github.com/magento/magento2/issues/39593) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39153)_

#### A indexação parcial parou de funcionar para clientes com um grande número de atualizações

A indexação parcial agora funciona para clientes com um grande número de atualizações.
Anteriormente, atingir o valor máximo para a coluna version_id na tabela changelog fazia com que as atualizações de índice parassem.
AC-14424

_AC-14424 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### O Magento 2.4.8 usa pacotes dev que não seguem o controle de versão semântico

Magento 2.4.8 requer versões dev de pdepend/pdepend e phpmd/phpmd (3.x-dev) para compatibilidade com PHP 8.4.
Essas versões de desenvolvimento entram em conflito com ferramentas de terceiros que esperam pacotes compatíveis com o SemVer, impedindo algumas atualizações.
Uma solução alternativa temporária é criar um alias para as versões dev no composer.json (por exemplo, &quot;3.x-dev as 3.99.0&quot;), permitindo compatibilidade enquanto satisfaz o controle de versão semântico.
Isso garante o suporte ao PHP 8.4 e evita conflitos até que versões estáveis sejam disponibilizadas.

_AC-14519 - [Problema do GitHub](https://github.com/magento/magento2/issues/39796)_

#### O mecanismo do MView ignora erros silenciosamente na execução do acionador

O mecanismo de visualização agora relata corretamente os erros na execução do acionador.
Anteriormente, os erros durante a execução do acionador eram ignorados silenciosamente, o que podia resultar em atualizações de índice ausentes sem nenhuma notificação.
AC-14567

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

#### [Problema] Incluir construtor como parte da API `CommandListInterface`, estender documentação integrada

Essa atualização de PR marca Magento\Framework\Console\CommandList como uma API e introduz o construtor ao CommandListInterface para obter uma melhor extensibilidade. Também melhora a documentação em linha para aprimorar a clareza e a capacidade de manutenção para desenvolvedores que estendem os comandos do console.

_AC-14680 - [Problema do GitHub](https://github.com/magento/magento2/issues/31102) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37901)_

#### [Problema] Remover código relacionado ao Microsoft IIS

Essa PR limpa o código relacionado ao Microsoft IIS de acordo com a documentação de Requisitos do Sistema do Magento, que declara que o sistema operacional Microsoft Windows não é compatível

_AC-14702 - [Problema do GitHub](https://github.com/magento/magento2/issues/39910) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39894)_

#### Erro de sintaxe da Magnifier.js

A funcionalidade da Lupa do sistema deve continuar funcionando da maneira que funcionava antes, e a lupaOptions não deve estar disponível no escopo global

_AC-14722 - [Problema do GitHub](https://github.com/magento/magento2/issues/36200) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39321)_

#### Modo Detalhado de Backport no comando da CLI `setup:db:status`

O comando da CLI `setup:db:status` agora dá suporte ao modo detalhado.
Anteriormente, era difícil entender as alterações no banco de dados necessárias para os upgrades. Agora, a execução de `bin/magento setup:db:status -v` fornece informações detalhadas sobre as diferenças de esquema e dados.
AC-14807

_AC-14807 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Envio de email SMTP com tls e 2.4.8

O envio de email SMTP com TLS agora funciona conforme esperado.
Anteriormente, o envio de emails via SMTP com TLS resultava no erro: erro:1408F10B:rotinas SSL:ssl3_get_record:número de versão incorreto.
AC-14883

_AC-14883 - [Problema do GitHub](https://github.com/magento/magento2/issues/39947) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problema] Corrigir problema de simultaneidade na implantação de conteúdo estático

Esta PR corrige um erro em que vários processos simultâneos são gerados para lidar com o mesmo pacote de tema, dependendo de como os temas são definidos com seus pais.

_AC-14944 - [Problema do GitHub](https://github.com/magento/magento2/issues/39990) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problema] Remover código de compatibilidade herdado para versões do PHP &lt; 8.1

Este pull request remove o código que foi projetado para ser executado no PHP &lt;8.1.
Além disso, a remoção verifica a disponibilidade de contato do PHP_VERSION_ID, uma vez que está disponível em todas as versões do PHP

_AC-14971 - [Problema do GitHub](https://github.com/magento/magento2/issues/39891) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39882)_

#### O FPC não funciona ao fazer logon

O Full Page Cache (FPC) agora funciona corretamente para clientes conectados.
Anteriormente, após fazer logon, a página inicial não era carregada do cache e o cabeçalho x-magento-cache-debug mostrava MISS em vez de HIT.
AC-14999

_AC-14999 - [Problema do GitHub](https://github.com/magento/magento2/issues/40007)_

#### Adicione tipos genéricos em certas classes php, para melhorar o suporte à análise estática

O sistema agora usa a definição de tipo genérico para melhorar isso significativamente, tendo-a interpretado como a classe exata que uma chamada de método retorna

_AC-15013 - [Problema do GitHub](https://github.com/magento/magento2/issues/40017) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40119)_

#### [Problema]: melhorar a manipulação de erros do SchemaBuilder

Essa PR melhora a manipulação de mensagens de erro do esquema db. Isso nos ajuda a identificar o problema sem uma depuração pesada.

_AC-15020 - [Problema do GitHub](https://github.com/magento/magento2/issues/39816) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39799)_

#### API Rest: Chamada para uma função membro getVideoProvider() em nulo

Correção de um problema em que chamar a API filho do produto configurável retornava um Erro interno do servidor 500 se um produto filho tivesse apenas um vídeo YouTube e nenhuma outra imagem.
O erro foi causado por uma referência nula em ExternalVideoEntryConverter.
Agora, a API retorna corretamente os produtos secundários com entradas de galeria de mídia, incluindo dados de vídeo externos, sem gerar erros.
Isso garante a recuperação adequada de todos os tipos de mídia para produtos derivados por meio da API REST.

_AC-15046 - [Problema do GitHub](https://github.com/magento/magento2/issues/40021)_

#### [W3C] Remover texto/javascript da declaração de marca de script de cookie

Essa PR removeu o atributo type=&quot;text/javascript&quot; desnecessário da tag de script de cookie para conformidade com a HTML5.

_AC-15061 - [Problema do GitHub](https://github.com/magento/magento2/issues/39982) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39983)_

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

#### Tipos de retorno não claros/inválidos em Magento\Framework\Escaper

O sistema aceitará tipos de métodos de escape ao executar análise estática usando phpstan no nível 5

_AC-15272 - [Problema do GitHub](https://github.com/magento/magento2/issues/40012) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40114)_

#### [Problema] Permitir que a configuração específica da fila exceda o valor padrão de max-messages

O sistema agora Permite que a configuração específica da fila exceda o valor padrão de max-messages

_AC-15284 - [Problema do GitHub](https://github.com/magento/magento2/issues/40121) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40110)_

#### [Problema] FPC de cache duplicado para a mesma página com a mesma consulta ao usar verniz

Essa PR corrige entradas de cache de página inteira duplicadas ao usar o Varnish, normalizando a ordem dos parâmetros de consulta, garantindo chaves de cache consistentes para solicitações idênticas.
Melhora a taxa de acertos do cache e o desempenho de URLs com os mesmos parâmetros em sequências diferentes.

_AC-15325 - [Problema do GitHub](https://github.com/magento/magento2/issues/39706) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39704)_

#### Os temas da comunidade contêm recursos para módulos de edição do Commerce

Remoção dos recursos de estilo somente do Commerce dos temas da comunidade, realocando-os para seus respectivos diretórios de módulo. Isso impede que o CSS não utilizado seja incluído na Community Edition, reduzindo o conteúdo desnecessário e eliminando regras de estilo inativas, garantindo o estilo adequado quando os módulos do Commerce são ativados.

_AC-15347 - [Problema do GitHub](https://github.com/magento/magento2/issues/21446) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9bcd880a)_

#### [Problema] Adicionar código de armazenamento a URLs deve ser Global

Esta PR aborda o problema, garantindo que a configuração &quot;Adicionar código de armazenamento a URLs&quot; seja recuperada usando o escopo global no código principal

_AC-15365 - [Problema do GitHub](https://github.com/magento/magento2/issues/40069) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40065)_

#### [Problema] registrar plug-in não declarado apenas se não estiver desabilitado

Esta PR corrige e registra o plug-in que na verdade não está declarado e não é usado (instância ativada e ausente).

_AC-15386 - [Problema do GitHub](https://github.com/magento/magento2/issues/40086) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40081)_

#### [Problema] Pequena limpeza, chaves duplicadas removidas da matriz

O sistema agora fez uma pequena limpeza e nenhum erro encontrado relacionado à matriz tem 2 chaves duplicadas com o valor &#39;Peso (e superior)&#39;

_AC-15414 - [Problema do GitHub](https://github.com/magento/magento2/issues/39851) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, magento/framework versão 103.0.8-p2: classe EmailMessage chamando um método não existente

A classe EmailMessage agora lida corretamente com a recuperação do corpo do email.
Anteriormente, no Magento 2.4.8-p2 com magento/framework versão 103.0.8-p2, a classe Magento\Framework\Mail\EmailMessage tentou chamar um método inexistente (getTextBody) no objeto de mensagem de email Symfony. Isso causava erros quando módulos ou personalizações de terceiros dependiam desse método para processamento de email.
Agora, a classe EmailMessage não chama mais métodos indefinidos, evitando esses erros. AC-15446

_AC-15446 - [Problema do GitHub](https://github.com/magento/magento2/issues/40170) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Patches de Dados/Esquemas getAliases() causam erros durante `setup:upgrade`

getAliases() causa erros durante a configuração:upgrade, essa PR corrigindo o mesmo

_AC-15559 - [Problema do GitHub](https://github.com/magento/magento2/issues/31396) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38239)_

#### Combinação ilegal de agrupamentos para operação

_AC-15614 - [Problema do GitHub](https://github.com/magento/magento2/issues/40138) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### [Problema] [PHPDOC] Corrigir phpdoc incorreto Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()

Essa PR atualiza o PHPDoc para \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs() para refletir corretamente que o parâmetro $alias pode ser nulo, além da string. Isso resolve problemas do PHPStan no nível 5+ e melhora a compatibilidade das ferramentas de qualidade do código.

_AC-15626 - [Problema do GitHub](https://github.com/magento/magento2/issues/39598) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39581)_

#### Mistura ilegal de agrupamentos no módulo urlrewrite

_AC-15647 - [Problema do GitHub](https://github.com/magento/magento2/issues/40189) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### A condição nunca foi atendida em `\Magento\Framework\Escaper::escapeScriptIdentifiers`

Correção de uma condição inacessível em \Magento\Framework\Escaper::escapeScriptIdentifiers, substituindo a verificação para falso por nulo, alinhando-a com valores de retorno preg_replace e melhorando a precisão do código sem afetar a funcionalidade.

_AC-15667 - [Problema do GitHub](https://github.com/magento/magento2/issues/40195) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### Verniz 7.3 (versão mais recente) - Links de subcategorias / opções de categoria Padrão não são exibidos na página inicial da Loja

Confirmado que os links de subcategoria ausentes na página inicial da loja ao usar o Varnish 7.3 eram causados pelo manuseio de solicitações ESI e pela configuração do servidor em vez de um defeito de código Magento; o problema é resolvido por meio de ajustes de configuração recomendados do Varnish, sem a necessidade de alterações no código principal.

_AC-15674 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3cf1a106) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9a62604c)_

#### [Problema] Adicione dados de depuração extras ao log `cache_invalidate`

Essa PR aprimorou o log cache_invalidate para incluir o contexto da solicitação e o rastreamento de pilha para remoções completas de cache, melhorando a depuração e a visibilidade.
Isso ajuda a identificar a origem de invalidações inesperadas do cache completo sem alterar a funcionalidade existente.

_AC-15719 - [Problema do GitHub](https://github.com/magento/magento2/issues/40204) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40196)_

#### [Problema] Melhorou um pouco a lista de exclusão do carregador automático do compositor.

Esse PR refina as exclusões do carregador automático do Composer para ignorar classes de teste, reduzindo entradas desnecessárias do mapa de classe e evitando avisos PSR-4.

_AC-15743 - [Problema do GitHub](https://github.com/magento/magento2/issues/40109) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40107)_

#### [Problema] Impedir que declarações `db_schema.xml` com `comment=""` interrompam zero implantações de tempo de inatividade

O sistema agora impede que declarações db_schema.xml com comment=&quot;&quot; interrompam zero implantações de tempo de inatividade

_AC-15980 - [Problema do GitHub](https://github.com/magento/magento2/issues/40254) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40242)_

#### Não é possível limpar o cache `\Magento\Framework\Filesystem\Glob::glob(...)`

Esta atualização de PR apresenta uma maneira de limpar o cache estático interno usado pelo \Magento\Framework\Filesystem\Glob, garantindo resultados novos e precisos quando as estruturas de arquivo são alteradas. Ele melhora a confiabilidade e a experiência do desenvolvedor, especialmente em cenários de teste e processos de longa duração, nos quais os resultados globais devem permanecer atualizados.

_AC-15989 - [Problema do GitHub](https://github.com/magento/magento2/issues/35741) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/35742)_

#### O URL do link Líderes do ReadME tem um redirecionamento permanente

Atualização do link Líderes README, substituindo o URL redirecionado e expirado permanentemente pelo links de trabalho corretos, garantindo que as páginas dos colaboradores e mantenedores sejam abertas corretamente.

_AC-16046 - [Problema do GitHub](https://github.com/magento/magento2/issues/40292) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problema] [PHPDOC] Corrigir phpdoc inválido Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

Anotações PHPDoc corrigidas para joinLeft() na Coleção de atributos para permitir definições de matriz apropriadas, melhorando a correção de código e a compatibilidade com ferramentas como o PHPStan.

_AC-16187 - [Problema do GitHub](https://github.com/magento/magento2/issues/40354) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39155)_

#### Certifique-se de que uma única falha de comando registre o erro (arquivo ou stderr) sem interromper a execução de comandos subsequentes da CLI.

O sistema agora garante que uma única falha de comando registre o erro (arquivo ou stderr) sem interromper a execução de comandos CLI subsequentes

_AC-16244 - [Problema do GitHub](https://github.com/magento/magento2/issues/40006) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40063)_

#### [Problema] Adicione o tipo int a $maxAge no Kernel do PageCache

Esta PR garante que o parâmetro $maxAge no kernel do PageCache seja digitado estritamente como um número inteiro para melhorar a segurança do tipo e evitar erros de análise estática/PHPStan no manuseio do cache.

_AC-16313 - [Problema do GitHub](https://github.com/magento/magento2/issues/40438) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36600)_

#### Adicionar ao evento do carrinho: preços vazios

Correção de um problema em que os preços do produto eram retornados como nulos no observador de eventos checkout_cart_product_add_after durante o processo de adição ao carrinho.
Agora, o preço base e os valores de preço relacionados são recuperados corretamente, garantindo que dados precisos estejam disponíveis para observadores e implementações personalizadas.

_AC-5966 - [Problema do GitHub](https://github.com/magento/magento2/issues/35638) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Bugfix do tipo PHP8.1

Os produtos associados agora são inicializados em uma matriz vazia em vez de false quando o modo de processamento estrito não está ativo ou quando as informações do produto estão disponíveis. Essa alteração garante que a lógica subsequente de manuseio de produtos associados se comporte de forma consistente, melhorando a estabilidade e a previsibilidade no processo de preparação do produto.

_AC-6017 - [Problema do GitHub](https://github.com/magento/magento2/issues/35808) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/35842)_

#### Tipo esperado &#39;Magento\Customer\Api\Data\GroupInterface&#39;. Encontrado &#39;Magento\Customer\Model\Group&#39;.

Correção de um problema em que salvar um grupo de clientes por meio de GroupRepositoryInterface usando GroupFactory causava um erro de tipo.
Anteriormente, o repositório esperava GroupInterface, mas as instâncias de modelo de Grupo foram transmitidas, resultando em um erro fatal.
Agora, os grupos de clientes podem ser salvos com êxito por meio do repositório, garantindo a implementação adequada da interface.
Isso soluciona avisos do IDE e erros de tempo de execução ao criar ou atualizar programaticamente grupos de clientes.

_AC-6909 - [Problema do GitHub](https://github.com/magento/magento2/issues/36269)_

#### Validação de campos em avisos de crédito

Correção de um problema em que a validação de campo na página de memorando de crédito impedia o envio mesmo após os campos personalizados obrigatórios serem preenchidos.
Agora, a validação funciona corretamente e o botão enviar é ativado depois que todos os campos obrigatórios são preenchidos.

_AC-8308 - [Problema do GitHub](https://github.com/magento/magento2/issues/37182) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### [Problema] Remover a marca `@author` proibida da estrutura (parte 3)

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8343 - [Problema do GitHub](https://github.com/magento/magento2/issues/37270) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problema]: usar promoção de propriedade de construtor no módulo enviar gráfico amigo ql

O sistema agora utiliza a promoção de propriedade do construtor no módulo GraphQL &quot;enviar amigo&quot;, melhorando a legibilidade do código e reduzindo a complexidade. Anteriormente, o módulo usava propriedades que ocupavam várias linhas, tornando o código mais complexo e menos legível.

_AC-8346 - [Problema do GitHub](https://github.com/magento/magento2/issues/37235) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8349 - [Problema do GitHub](https://github.com/magento/magento2/issues/37266) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8350 - [Problema do GitHub](https://github.com/magento/magento2/issues/37265) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problema] Remover a marca `@author` proibida de `Magento_Downloadable`

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8355 - [Problema do GitHub](https://github.com/magento/magento2/issues/37251) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade e a consistência do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8358 - [Problema do GitHub](https://github.com/magento/magento2/issues/37264) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8359 - [Problema do GitHub](https://github.com/magento/magento2/issues/37262) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8360 - [Problema do GitHub](https://github.com/magento/magento2/issues/37261) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, garantindo um código mais limpo e padronizado. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8361 - [Problema do GitHub](https://github.com/magento/magento2/issues/37260) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problema] Remover a marca `@author` proibida

Esta PR remove a tag `@author` da base de código

_AC-8362 - [Problema do GitHub](https://github.com/magento/magento2/issues/37259) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problema] Remover a marca `@author` proibida

O sistema agora segue os padrões de codificação, removendo a tag `@author` proibida de determinados módulos, melhorando a qualidade geral do código. Anteriormente, a presença dessa tag em alguns módulos violava os padrões de codificação estabelecidos.

_AC-8363 - [Problema do GitHub](https://github.com/magento/magento2/issues/37258) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37008)_

#### [Problema] Remover a marca `@author` proibida de `Magento_Backup` e `Magento_Bundle`

Esta PR remove a tag `@author` da base de código

_AC-8367 - [Problema do GitHub](https://github.com/magento/magento2/issues/37244) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36979)_

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

#### [Problema] Corrigir o nome da variável na pesquisa do catálogo

O sistema agora nomeia corretamente as variáveis no módulo do mecanismo de pesquisa, melhorando a clareza e a capacidade de manutenção do código. Anteriormente, um nome de variável irrelevante, $defaultCountry, era usado no módulo do mecanismo de pesquisa, causando confusão.

_AC-9215 - [Problema do GitHub](https://github.com/magento/magento2/issues/37810) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generation deve ser definido por meio da variável de ambiente

Após a correção, a variável de ambiente &quot;MAGENTO_DC_CACHE_ALLOW_PARALLEL_GENERATION&quot; pode ser usada para definir a configuração &quot;allow_parallel_generation&quot;.

_ACP2E-3673 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Nuvem] A alteração do tipo de coluna da tabela de Int para Decimal usando o arquivo db_schema.xml no Magento 2 resulta em erros

A alteração do tipo de dados da coluna não está funcionando corretamente. Anteriormente, ele emitia um erro: o atributo &quot;identidade&quot; não era permitido.

_ACP2E-3709 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Novo suporte a moeda (XCG) no Adobe

Caribbean Guilder (XCG) é adicionado à lista de moedas.

_ACP2E-3790 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Problema com a atualização 2.4.7-p5 devido à adição de uma nova validação

Correção de um problema na classe SchemaBuilder em que uma &quot;coluna&quot; de chave de matriz indefinida causava uma falha durante a criação ou as atualizações do esquema. Isso ocorria ao processar dados da tabela que não incluíam uma chave de &quot;coluna&quot;.

_ACP2E-3871 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]Problema de Servidor Potencialmente Causado por Chave de Acesso S3 Inválida

Credenciais incorretas do AWS S3 não fazem mais com que as páginas sejam carregadas infinitamente na loja.

_ACP2E-3890 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js não está funcionando

Os seguintes arquivos JS agora são totalmente e corretamente minificados quando a minificação JS é ativada: mage/backend/tabs.min.j, jquery/jquery.validate.min.js e Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Como resultado, a validação do campo de classe CSS do Page Builder funciona conforme esperado.

_ACP2E-3925 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Erro de descontinuação do PHP8.4: E_USER_ERROR após a atualização para o Adobe Commerce 2.4.8

*NÃO SÃO NECESSÁRIAS NOTAS DE VERSÃO*
Os cenários voltados para o cliente não são afetados pela correção.

_ACP2E-3963 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### O trabalho Cron não está limpando a tabela do banco de dados - causando interrupção devido a falha do Galera

A limpeza de tabelas de log de alteração agora está sendo executada em lotes para evitar operações de exclusão intensas.

_ACP2E-3995 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### JS não minificado às vezes carrega ignorando &quot;ativar minificações de js&quot;

Antes da correção, mesmo que a minificação estivesse ativada, alguns arquivos JS eram solicitados sem o prefixo &quot;min&quot;, resultando no código de status 404. Após a correção, quando a minificação estiver ativada, não há solicitações de recursos JS não minificados.

_ACP2E-4058 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### O atributo de data no grupo de atributos personalizado não mostra o Datepicker no Admin

Correção de um problema em que o pop-up de calendário para atributos de data aparecia fora da tela quando atribuído a grupos de atributos personalizados.

_ACP2E-4060 - [Problema do GitHub](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### A verificação de permissão de ACL de produção causou degradação de desempenho - o método populateAcl é o afunilamento

Processamento de regras de ACL otimizado

_ACP2E-4114 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### O check-out não é carregado na versão mais recente com AC-15867 + ACP2E-4296 e SCD compacto

Antes da correção, ter javascripts personalizados carregados pela seção head poderia causar problemas. Após a introdução da nova configuração, esses scripts podem ser automaticamente adiados, garantindo maior compatibilidade com a estrutura do Magento 2.

_ACP2E-4319 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1c547060)_

#### Aviso de descontinuação: use Moment.updateLocale(localeName, config) para alterar um local existente. Moment.defineLocale(localeName, config)

Antes da correção, um aviso obsoleto era lançado no console do navegador. Agora, após a correção, esse aviso não é mais exibido.

_ACP2E-4338 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Incompatibilidade com MariaDB 10.11

Anteriormente, a instalação da versão mais recente do Magento 2 falhava ao usar o MariaDB 10.11, impedindo a conclusão do processo de configuração. Esse problema foi resolvido atualizando o tratamento de compatibilidade do banco de dados para oferecer suporte ao MariaDB 10.11.x durante a instalação.

_ACP2E-4367 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Framework, Search

#### Opensearch 2.19.1 invalid_argument_exception em categorias com um preço

O Opensearch não está mais gerando um invalid_argument_exception nas categorias que contêm todos os produtos com o mesmo preço. Anteriormente, ele tinha esta exceção &quot;[do] parâmetro não pode ser negativo&quot;.

_ACP2E-3896 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### Fazer um pedido no GraphQL é bem-sucedido com um método de envio inválido

Correção de um problema em que os pedidos podiam ser feitos via GraphQL usando um método de envio desativado ou inválido.
Agora, o sistema valida o método de envio selecionado e retorna um erro se ele não estiver disponível, impedindo que o pedido seja criado.

_AC-10472 - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38268) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Exceção gerada ao executar a consulta GraphQl

Correção de um problema em que uma consulta GraphQL exibia uma exceção devido a um parâmetro de classificação inválido; após a correção, a consulta é executada com êxito sem gerar erros ou logs de exceção.

_AC-14835 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Erro interno do servidor ao adicionar o produto Gift Card ao carrinho por meio da mutação AddProductsToCart incluindo custom_attributesV2

Correção de um erro interno de servidor acionado ao adicionar produtos de cartão-presente (e opções personalizadas semelhantes) ao carrinho por meio do GraphQL com custom_attributesV2; a correção lida corretamente com valores de atributo complexos, permitindo que os produtos sejam adicionados sem erros.

_AC-15856 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7fa400a7)_

#### Campos nulos na consulta `Country`

Correção de um problema em que os pedidos contendo itens virtuais, reembolsados e remetidos permaneciam no processamento, garantindo que os itens virtuais fossem incluídos nos cálculos de quantidade remetida, permitindo que o estado do pedido mudasse corretamente para conclusão.

_AC-7731 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### A consulta do GraphQL &quot;customerOrders&quot; com o atributo &quot;number&quot; causa um erro interno do servidor

Correção de um problema em que a consulta customerOrders do GraphQL retornava um erro interno do servidor ao solicitar o campo de número.
Agora, o resolvedor retorna corretamente a ID de incremento da ordem, permitindo que a consulta seja executada com êxito e recupere o número da ordem.

_AC-8949 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### O GraphQL Response for Order placement não inclui a mensagem de exceção

Revertida a alteração anterior que retornava erros em um formato diferente. Agora, os erros em potencial são retornados de maneira consistente, sem quebrar o esquema do GraphQL. Isso deve ser adicionado como BIC conhecido, aprovado pelo PM aqui: https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

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

#### GraphQL de Pedido de Cliente : recuperar categorias de produto para o produto associado &quot;não está visível individualmente&quot;

Antes da correção, se o pedido continha um produto oculto, suas categorias exibiriam uma matriz vazia na resposta GraphQl do pedido do cliente.
Agora, após a correção, as categorias de produtos são incluídas na resposta de uma solicitação GraphQl de pedido do cliente, mesmo que o produto esteja oculto.

_ACP2E-3945 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Os itens da lista de desejos não são compartilhados entre visualizações de lojas em um site na solicitação do GraphQL

Antes da correção, os itens da lista de desejos eram filtrados pela ID da loja. Agora, após a correção, os itens da lista de desejos são filtrados por site.

_ACP2E-3987 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

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

#### Exceção do GraphQL no SWAT

Após a correção, as respostas das solicitações do GraphQL são alinhadas às especificações do GraphQL sobre HTTP. Um código de resposta 4XX é retornado quando é impossível analisar a solicitação, a solicitação não está autorizada ou há outro problema geral com a solicitação. Se a solicitação for analisada e puder ser processada, um código de resposta 200 será retornado.

_ACP2E-4194 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### O produto não será removido da lista de comparação depois que a lista for atribuída ao cliente

Depois que a lista de comparação de um usuário convidado é atribuída a uma conta de cliente, os produtos adicionados como convidado agora podem ser removidos pelo cliente.
Anteriormente, as operações de remoção falhavam porque os itens adicionados pelo convidado não eram vinculados corretamente à conta do cliente após a atribuição.

_ACP2E-4244 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### resposta de erro incorreta do updateCartItems GraphQL

Anteriormente, quando uma solicitação de graphQL para um item com quantidade insuficiente era feita, uma mensagem de erro adequada com um código de erro era retornada, juntamente com o cálculo de preço e quantidade solicitados, mesmo que o item não estivesse disponível. Depois que essa correção for aplicada, uma mensagem de erro adequada com um código de erro será retornada e a quantidade do item será definida como seu valor antigo se não estiver disponível na resposta.

_ACP2E-4283 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Erro de atribuição de solicitação de convidado entre sites no plug-in MergeGuestOrder

Antes da correção, uma atribuição de cliente de pedido de convidado não estava considerando opções de compartilhamento de conta. Agora, após a correção, um pedido é atribuído a um cliente se o cliente e a loja de pedidos corresponderem (considerando que a opção de compartilhamento de conta do cliente está definida como &quot;Por site&quot;).

_ACP2E-4312 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, Inventário / MSI

#### Problema com only_x_left_in_stock no Magento 2 GraphQL - Cálculo incorreto ao usar limites

Correção de um problema em que o campo GraphQL only_x_left_in_stock retornava null devido à dedução dupla incorreta de MinQty; o cálculo foi corrigido para que agora retornasse o valor do estoque preciso com base nos limites.

_AC-15832 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/35458c7f)_

#### Discrepâncias de mutação do GraphQL mergeCart

Após a correção, a solicitação GraphQL dos carrinhos de mesclagem verifica corretamente a quantidade do produto, levando em conta a configuração de estoque.

_ACP2E-4184 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Produto

#### Falta media_type no graphql do produto em MediaGalleryInterface

A solicitação do MediaGallery GraphQL agora inclui o campo &quot;tipos&quot; para tipos de imagem de produto. Anteriormente, esse campo &quot;tipos&quot; não existia na solicitação do MediaGallery GraphQL.

_ACP2E-3880 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, Segurança

#### A redefinição da senha do cliente por meio do GraphQL não respeita as restrições

Solução de um problema em que as solicitações de redefinição de senha do cliente feitas por meio do GraphQL Mutations não cumpriam as restrições de redefinição de senha configuradas em Loja > Configuração > Clientes > Configuração do cliente > Opções de senha. Essas configurações agora são aplicadas corretamente.

_ACP2E-3992 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importar/exportar

#### [Problema] Tipo de parâmetro Fix

Correção de uma incompatibilidade de tipo de parâmetro no módulo Importação/Exportação em que um valor definido anteriormente como uma string agora é definido corretamente como uma matriz. Isso se alinha à entrada esperada do controlador de exportação e evita avisos de análise estática.

_AC-11665 - [Problema do GitHub](https://github.com/magento/magento2/issues/38529) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64823f95)_

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

#### Exportar filtros para o produto Sim-Não Atributos não funcionam como esperado

Após a correção, os produtos exportados filtrados por um atributo Sim/Não contêm os produtos esperados que respeitam os filtros aplicados.

_ACP2E-4160 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Problema com o preço de opção do pacote de Atualização por site via Importação

Agora é possível exportar e importar preços de seleção de opção de pacote por site

_ACP2E-4243 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Não é possível importar um cliente com um endereço de email em maiúsculas

Correção de um erro indefinido de chave de matriz ao importar clientes com emails em maiúsculas quando o Compartilhamento de conta estava definido como Global. A normalização de email agora é consistente em todo o processo de importação, garantindo que os clientes possam ser importados independentemente do caso do email. O comportamento de compartilhamento de conta no nível do site permanece inalterado.

_ACP2E-4373 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Importação / exportação, Cliente / Clientes

#### O administrador pode importar o cliente com uma data de nascimento posterior à data atual

Correção de um problema em que os administradores podiam importar clientes com uma data de nascimento definida no futuro. O sistema agora valida o DOB durante a importação, mostra um erro para registros inválidos e impede que clientes com datas de nascimento futuras sejam importados, garantindo dados precisos do cliente.

_AC-13641 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

### Inventário / MSI

#### A retirada de armazenamento não respeita o raio máximo de pesquisa quando o endereço é alterado no check-out

Agora, a loja pré-selecionada em &quot;Separar na loja&quot; será atualizada se o endereço de entrega mudar. Anteriormente, uma vez que uma loja era pré-selecionada, ela não era alterada mesmo se o novo endereço de entrega não estivesse dentro do raio da loja selecionada

_ACP2E-3728 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/07620383)_

#### Nenhuma loja está disponível após o redirecionamento para a página inicial e o check-out

A loja selecionada anteriormente será pré-selecionada na remessa &quot;Separar na loja&quot; se o cliente navegar até a página de pagamento, retornar à página inicial e finalmente retornar à página de check-out. Anteriormente, após retornar repetidamente à página de check-out, a loja selecionada em &quot;Selecionar na loja&quot; era apagada.

_ACP2E-3793 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

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

#### O Relatório de administração da [NUVEM] não mostra detalhes quando o estoque é atualizado

As alterações na origem do inventário do produto agora estão sendo registradas pelo módulo de registro. Antes da correção, ao salvar um produto e executar alterações relacionadas ao inventário, os detalhes não eram registrados.

_ACP2E-4167 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### O produto do pacote não pode ser adicionado ao carrinho enquanto está marcado como em estoque

O status do pacote de estoque de produtos agora reflete corretamente as reservas de produtos secundários e os limites de indisponibilidade.
Anteriormente, os produtos em pacote eram marcados como &quot;em estoque&quot; mesmo quando um ou mais produtos secundários não tinham quantidade suficiente comercializável. Isso levava a erros de &quot;Itens insuficientes para venda&quot; ao adicionar o pacote ao carrinho.

_ACP2E-4220 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### O produto agrupado é exibido incorretamente como Fora de estoque no PDP após a importação do CSV quando o filho é atribuído à origem/estoque personalizado (corrigido após a reindexação manual)

Após a correção, a criação de um produto composto usando importar executa automaticamente a reindexação do estoque, disponibilizando o produto sem a necessidade de reindexação manual.

_ACP2E-4233 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98f028ab) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] Testes MFTF com falha relacionados às alterações principais mais recentes.

Antes de os clientes convidados consertados que optavam pela Coleta na loja sem um endereço de entrega, o endereço de cobrança era preenchido automaticamente com o endereço da loja, que não podia ser alterado, resultando em detalhes de fatura incorretos. Depois que o endereço de cobrança fixo agora pode ser editado neste cenário, permitindo que os convidados insiram seus próprios detalhes. Os usuários registrados verão o endereço de cobrança salvo em vez do da loja.

_ACP2E-4260 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ab891304) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/13e432a6)_

#### Reserva de estoque incorreta criada para cartões-presente virtuais

Antes da implementação dessa correção, a quantidade de um cartão-presente virtual contendo vários itens não refletia com precisão na reserva do estoque. No entanto, após a aplicação da correção, a quantidade da reserva de estoque e os estoques se sincronizaram.

_ACP2E-4267 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### Falha do Comando de Compensação de Reserva de Inventário com Referências de Produto Nulas e Não Existentes

Correção de um problema em que a CLI de compensação de reserva de estoque gerava uma exceção se a combinação processada tivesse uma ID de pedido ausente

_ACP2E-4301 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### O produto está esgotado depois de alterar o caso do SKU

Modificar o caso do SKU não faz mais com que o produto fique indisponível na loja.

_ACP2E-4375 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/0836c2ed)_

#### Ordenar por preço/aspectos de preço com dados inválidos

Antes da correção, os preços de pacote não eram indexados corretamente quando os produtos secundários estavam em estoque em fontes personalizadas. Agora, após a correção, os preços de pacote são indexados corretamente, independentemente da atribuição de estoque de produtos secundários.

_ACP2E-4380 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1c547060) - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/1f83ed24)_

### Pedido

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) quebra customAttributes

Os atributos personalizados em endereços agora são manipulados corretamente durante as operações de check-out e API.
Anteriormente, usar $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes) poderia interromper a manipulação de atributos personalizados, fazendo com que os valores de atributo fossem estruturados incorretamente.
AC-10568

_AC-10568 - [Problema do GitHub](https://github.com/magento/magento2/issues/31644)_

#### Quando o cliente está definido para a ordem de cotação ainda é uma ordem de convidado

_AC-11689 - [Problema do GitHub](https://github.com/magento/magento2/issues/38540)_

#### O pedido não está concluído ao misturar itens virtuais, reembolsados e remetidos

Correção de um problema em que os pedidos contendo itens virtuais, reembolsados e remetidos permaneciam no processamento, garantindo que os itens virtuais fossem incluídos nos cálculos de quantidade remetida, permitindo que o estado do pedido mudasse corretamente para conclusão.

_AC-11691 - [Problema do GitHub](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento reorder -1 números de ordem

O sistema está funcionando como esperado e, após reordenar a partir do backend, o número do pedido será exclusivo de 8 dígitos

_AC-12854 - [Problema do GitHub](https://github.com/magento/magento2/issues/39089) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39399)_

#### Perdendo o upload do arquivo de opção personalizada do produto ao fazer check-out com o método de pagamento com cartão de crédito do Adobe

Os uploads de arquivo de opção personalizada do produto agora são retidos ao fazer check-out com o método de pagamento com cartão de crédito do Adobe.
Anteriormente, os uploads de arquivo eram perdidos ao usar este método de pagamento, mas funcionavam com outras pessoas.
AC-14306

_AC-14306 - [Problema do GitHub](https://github.com/magento/magento2/issues/39647)_

#### Pedidos do administrador - não é possível procurar Will

Correção de um problema em que a pesquisa de pedidos por nome de cliente (por exemplo, &quot;Solicitará&quot;) na grade Pedidos de administrador não retornava resultados. Após a correção, os pedidos relevantes são exibidos corretamente quando filtrados pelo nome do cliente.

_AC-14360 - [Problema do GitHub](https://github.com/magento/magento2/issues/36596) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL - Formatação incorreta dos itens do pedido order_date

Correção de um problema em que o campo order_date na resposta do GraphQL retornava no formato aaaa-mm-dd.
Agora, a order_date é exibida corretamente no formato dd-mm-yyyy.

_AC-14431 - [Problema do GitHub](https://github.com/magento/magento2/issues/39805) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Não é possível retornar nulo para campo não anulável \&quot;AppliedCoupon.code\&quot; problema inesperado

O Adobe Commerce agora retorna corretamente os códigos de cupom aplicados por meio do GraphQL ao consultar pedidos de clientes. Anteriormente, no Adobe Commerce 2.4.8, a busca de um pedido com o campo apply_coupons.code (por exemplo, por meio da consulta customer.orders) poderia falhar com um erro de servidor interno e a mensagem Não é possível retornar nulo para o campo não anulável &quot;AppliedCoupon.code&quot;, e apply_coupons foi retornada como [null] em vez de uma lista contendo o código do cupom. AC-14484

_AC-14484 - [Problema do GitHub](https://github.com/magento/magento2/issues/39841) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

#### Email de remessa não enviado quando enviado da visualização de Pedido de administrador apesar de estar ativado na configuração da loja

O sistema agora envia um email de confirmação de remessa, pois ele é ativado na configuração da loja onde o pedido foi feito.

_AC-14563 - [Problema do GitHub](https://github.com/magento/magento2/issues/39861) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39897)_

#### A filtragem na data não funciona devido a nomes de campo ambíguos

No Magento 2.4.7-p6, a filtragem da grade do pedido por data relatou causar um erro devido a associações com módulos do Braintree.
A emissão envolveu consultas unindo tabelas braintree_transaction_details e sales_order ao aplicar filtros de data.
A equipe de engenharia da Adobe Commerce analisou o caso, mas não conseguiu reproduzir o erro no ambiente.
O comportamento esperado é que a filtragem por data deve retornar ordens correspondentes ao filtro sem erros.

_AC-15037 - [Problema do GitHub](https://github.com/magento/magento2/issues/40024)_

#### A criação de pedidos em backoffice com vários produtos, dos quais pelo menos um contém opções personalizadas, resulta na adição de produtos extras indesejados ao pedido

Correção de um problema em que a criação de um pedido no backoffice com vários produtos, incluindo um com opções personalizadas, produtos extras adicionados involuntariamente e que causava erros. O sistema agora adiciona somente os produtos selecionados, permitindo que os pedidos sejam criados sem itens inesperados.

_AC-15286 - [Problema do GitHub](https://github.com/magento/magento2/issues/40122) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2: Não é possível criar regra de promoção

Essas correções de PR, nós obtemos
Modelo \Magento\Catalog\Model\ResourceModel\Eav\Attribute em vez de \Magento\Catalog\Model\ResourceModel\Eav\Attribute no método \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problema do GitHub](https://github.com/magento/magento2/issues/12176) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/30479)_

#### O Magento alterou o tipo de entidade de $order depois de chamar $Invoice = $this->_InvoiceService->prepareInvoice($order);

Correção de um problema em que a edição de uma atualização agendada existente para uma subcategoria aumentava incorretamente o child_count para categorias pai no banco de dados. O problema causou dados imprecisos da hierarquia de categoria após salvar as atualizações. Após a correção, a contagem de filhos permanece correta e não é mais incrementada inesperadamente.

_AC-15401 - [Problema do GitHub](https://github.com/magento/magento2/issues/40154)_

#### A ordem permanece com o status &#39;em processamento&#39; após o envio, se os itens forem parcialmente reembolsados

Correção de um problema em que os pedidos permaneciam no status Processando após o reembolso parcial de itens e o envio do restante. O status do pedido agora é atualizado corretamente para Concluído assim que as quantidades totais entregues e reembolsadas correspondem à quantidade faturada, garantindo um gerenciamento preciso do ciclo de vida do pedido.

_AC-15419 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### Enviar um email de vendas do back-end sempre dá sucesso - também quando desativado

Correção da notificação por email de vendas de back-end para exibir mensagens precisas, validando o resultado do serviço de email e garantindo que os usuários fossem informados quando os emails de pedido ou de fatura fossem desativados e não enviados.

_AC-16059 - [Problema do GitHub](https://github.com/magento/magento2/issues/40309) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### O preço personalizado de 0 é redefinido para o preço original na reorganização.

Correção de um problema em que os produtos com um preço personalizado de 0 eram revertidos para o preço original durante o novo pedido.
Agora, o preço personalizado é retido corretamente, garantindo preços precisos ao reordenar os itens.

_AC-8147 - [Problema do GitHub](https://github.com/magento/magento2/issues/36970) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Fazer pedido com método de pagamento desativado funcionando

Correção de um problema em que os pedidos podiam ser feitos usando um método de pagamento desativado via GraphQL.
Agora, um erro é retornado ao tentar definir ou usar um método de pagamento indisponível, impedindo que o pedido seja criado.

_AC-9605 - [Problema do GitHub](https://github.com/magento/magento2/issues/37983) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Status do pedido paralisado no processamento

Antes da correção, ao solicitar um produto combinado com a opção &quot;Enviar juntos&quot; ativada, o status do pedido não alternava automaticamente para &quot;Concluído&quot; após a fatura e o envio. Agora, após a correção, o status do pedido muda automaticamente para &quot;concluído&quot; depois que o pedido é faturado e enviado.

_ACP2E-3947 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Código OOTB da ]Magento da &lbrace;Cloud- Problema de configuração de modelo de email

Antes da correção, ao usar o envio assíncrono de email, os emails de remessa eram inconsistentes com a ordem da loja. Agora, após a correção, a ordem de e-mail de envio da loja correta é entregue.

_ACP2E-3998 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Cancelar redirecionamentos de fatura para 404

O cancelamento da fatura feita com o tipo Não capturar não resulta mais na página 404.

_ACP2E-4001 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Problema com pedidos atualizados com opções configuráveis usando a API REST

Preservar as opções de produto existentes nos itens da ordem de venda ao atualizar uma ordem por meio dos pontos de extremidade da api de descanso.

_ACP2E-4061 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Vendas assíncronas por inserção de id limitadas a 100 entradas por execução cron

Processamento da inserção assíncrona da grade de vendas aprimorado. Uma execução de cron agora insere todas as linhas pendentes em lotes, em vez de 100 por execução.

_ACP2E-4360 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Mensagem de erro &quot;O produto com a ID &quot;1&quot; não existe.&quot; está sendo repetidamente registrado no exception.log

Antes da correção, erros críticos eram registrados quando produtos excluídos eram encontrados na seção Últimos itens solicitados. Após a correção, os comerciantes podem configurar se os produtos excluídos devem ser registrados ou ignorados por meio do parâmetro `skipDeletedProductLogging` em di.xml. Por padrão, o comportamento permanece inalterado para compatibilidade com versões anteriores, mas os comerciantes podem definir o parâmetro como `true` para ignorar silenciosamente os produtos excluídos e evitar ruído de log.

_ACP2E-4366 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Dupla tributação no segundo reembolso de aviso de crédito

Correção do cálculo de imposto incorreto em avisos de crédito ao criar uma restituição parcial a partir de uma NFF depois que um aviso de crédito anterior era criado a partir da página de exibição do pedido.

_ACP2E-4384 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Ordem, Preços

#### O administrador exibe um símbolo de moeda incorreto na ao criar a devolução

Em uma configuração de vários sites com moedas diferentes (EUR/USD/GBP), a página de seleção de produto de devolução no admin agora exibe o símbolo de moeda correto. Anteriormente, ele exibia o símbolo de moeda padrão.

_ACP2E-3658 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Ordem, Devoluções

#### Erro ao criar aviso de crédito para reembolso offline

Correção de um problema em que a criação de um memorando de crédito falhava para produtos de pacote com a configuração Preço dinâmico = Não. Os avisos de crédito agora podem ser criados com sucesso sem erros.

_ACP2E-4157 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Outras ferramentas de desenvolvedor

#### [Problema] Dica de tipo incorreta para o membro protegido $_urlHelper

O sistema agora Corrige a dica de tipo errado com a correta, que também é usada no construtor

_AC-10716 - [Problema do GitHub](https://github.com/magento/magento2/issues/32503) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32496)_

#### [Problema] Limpando código não utilizado.

O sistema agora remove o código não utilizado em relação às importações não utilizadas.

_AC-10980 - [Problema do GitHub](https://github.com/magento/magento2/issues/38424) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33499)_

#### Falha de acessibilidade do Lighthouse

O sistema agora é aprovado com uma pontuação de acessibilidade de 100

_AC-12783 - [Problema do GitHub](https://github.com/magento/magento2/issues/39054) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39164)_

#### Desativar a configuração captcha storefont ainda carrega os arquivos captcha js

O Sistema agora não carrega arquivos captcha js quando desativamos o captcha
para storefont

_AC-14267 - [Problema do GitHub](https://github.com/magento/magento2/issues/32987) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39154)_

#### [Acessibilidade] do problema: o aninhamento de funções WAI-ARIA está incorreto no menu

O sistema agora gera acessibilidade de farol sem o aninhamento de funções WAI-ARIA incorreto no erro de menu e o relatório deve estar verde

_AC-15082 - [Problema do GitHub](https://github.com/magento/magento2/issues/40045) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38617)_

#### Erro de console na pré-visualização de email no administrador do Magento

O sistema não emitirá nenhum erro de console quando estivermos visualizando o modelo de email

_AC-9245 - [Problema do GitHub](https://github.com/magento/magento2/issues/37820) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37933)_

### Métodos de pagamento

#### A mensagem do Paylater não é exibida na loja enquanto configurada com sucesso no back-end

Correção de um problema em que a mensagem PayPal Pay Later não era exibida nas páginas inicial e carrinho, apesar de estar configurada no back-end. O banner falhou ao ser renderizado quando o país comprador era nulo para convidados ou clientes sem um endereço padrão. Após a correção, a mensagem Pagar mais tarde é exibida corretamente na loja.

_AC-12335 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/528af81a)_

### Pagamentos

#### [Problema] Corrigir captura de fatura offline (404)

Ele corrige o erro de página 404 ao capturar faturas de métodos de pagamento offline do administrador do Magento

_AC-13336 - [Problema do GitHub](https://github.com/magento/magento2/issues/39298) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39297)_

#### IPNs desconhecidos do PayPal abusam do processador IPN do aplicativo

O manipulador IPN agora ignora tipos IPN desconhecidos ou sem suporte. Em vez de retornar um erro 500, ele registra o problema e continua o processamento sem interrupção.

_ACP2E-4049 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Falha no pagamento do token de cartão salvo do PayflowPro

As IDs de transação do PayPal PayFlow Pro (PNREFs) agora são válidas para uso em Transações de referência por um período fixo de 12 meses. Depois de expirado, o cartão salvo não será mais exibido e deverá ser adicionado novamente. Anteriormente, a validade era determinada pela data de expiração do cartão de pagamento usado na transação original.

_ACP2E-4064 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Problema com o cartão com vaso ao fazer o pedido ao administrador

Colocar um pedido com cartão de crédito armazenado em um site com uma configuração de ação de pagamento diferente não resulta mais em um erro ou tipo de transação incorreto

_ACP2E-4270 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] O cartão salvo do PayflowPro (Cofre) com os últimos 4 dígitos não é exibido na ordem

As informações do cartão agora são devidamente persistidas e exibidas ao usar cartões salvos com a ação de pagamento Vendas, correspondendo ao comportamento ao usar a ação de pagamento Autorização para PayflowPro.

_ACP2E-4346 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Desempenho

#### [Problema] ao atualizar Store.php

Esta PR melhora o desempenho, ignorando a resolução de loja atual.

_AC-14791 - [Problema do GitHub](https://github.com/magento/magento2/issues/39949) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/38717)_

#### [Problema] Atualizar usa controle de cache imutável para site estático

Esta PR adiciona melhoria de desempenho ao não validar o conteúdo estático em cada carregamento de página até e a menos que seja alterado.

_AC-15171 - [Problema do GitHub](https://github.com/magento/magento2/issues/39486) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39484)_

#### [Problema] Armazene em cache os resultados das chamadas isCacheable para melhorar o desempenho

Esta PR adiciona o armazenamento em cache para o método isCacheable(), resultando no processo de renderização de layout para reduzir as verificações redundantes e melhorar o desempenho geral da renderização da página.

_AC-16054 - [Problema do GitHub](https://github.com/magento/magento2/issues/40156) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40112)_

#### [Problema] Pequena melhoria de desempenho do processamento de grade de ordem assíncrona

Esta PR apresenta uma otimização de desempenho para o processamento de grade de ordem assíncrona do Magento, substituindo a pesquisa last_updated_at baseada em cache transitória por um sinalizador persistente com backup em BD armazenado na tabela de sinalizador. Isso garante que o sistema retenha consistentemente o último carimbo de data e hora processado, mesmo após liberações ou implantações do cache, evitando verificações desnecessárias de tabela completa em grandes conjuntos de dados sales_order. Como resultado, as atualizações de grade assíncronas se tornam mais eficientes e previsíveis, especialmente em lojas de alto volume com atividade frequente de pedidos.

_AC-16109 - [Problema do GitHub](https://github.com/magento/magento2/issues/40282) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40271)_

#### [NUVEM] Não é possível adicionar produtos às categorias

Desempenho aprimorado ao adicionar produto à categoria por meio do Visual Merchandiser.

_ACP2E-3946 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### Problema de desempenho de limpeza do log de alterações após ACP2E-3995

Após a correção, o trabalho cron indexer_clean_all_changelogs limpa totalmente os logs de alteração, mantendo o agrupamento em vigor.

_ACP2E-4211 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [NUVEM] O cache do Fastly não está funcionando após a atualização para a versão 2.4.8

Solução de um problema em que as páginas armazenáveis em cache não eram armazenadas ou fornecidas corretamente do cache do Fastly, resultando em um comportamento inconsistente de armazenamento em cache e desempenho reduzido.

_ACP2E-4324 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Investigue os motivos do aumento da criação de chaves redis e de chaves de cache

Antes da correção, as chaves de cache usadas para metadados de armazenamento remoto não estavam expirando. Agora, após a correção, você pode definir um TTL para essas chaves de cache por meio de injeção de dependência.

_ACP2E-4345 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Preços

#### O preço é sempre 0 para itens de produto agrupados sem preço dinâmico na API rest de ordem

A API REST do pedido agora retorna os preços corretos para itens de produto agrupados sem preço dinâmico.
Anteriormente, ao exportar pedidos por meio da API REST, o preço dos itens de produto agrupados sem preço dinâmico era sempre retornado como 0, em vez do preço real mostrado na página do pacote.
AC-11925

_AC-11925 - [Problema do GitHub](https://github.com/magento/magento2/issues/38687) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7da46f52)_

#### Escopo incorreto atribuído aos atributos de preço na criação

Correção de um problema em que os atributos de preço recém-criados eram atribuídos incorretamente ao escopo Exibição de armazenamento, independentemente da configuração; após a correção, o escopo do atributo agora se alinha à configuração Escopo do preço de catálogo (Global ou Site) por padrão.

_AC-14945 - [Problema do GitHub](https://github.com/magento/magento2/issues/39986) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### O produto está sendo salvo mesmo quando a Data de Preço Especial - De é posterior à Data Até usando a ação em massa

Correção de um problema em que os produtos podiam ser salvos sem validação com um intervalo de datas de preço especial inválido.
Agora, uma mensagem de erro é exibida: &quot;Certifique-se de que a data Até seja posterior ou igual à data De.&quot;

_AC-15252 - [Problema do GitHub](https://github.com/magento/magento2/issues/40113) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### O preço normal não é visível, mesmo quando um preço especial é aplicado.

Correção de um problema em que o preço normal não era exibido quando um preço especial era aplicado. O preço normal agora aparece corretamente ao lado do preço especial, conforme esperado.

_ACP2E-4100 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/47721be6)_

### Produto

#### Produto configurável com mau comportamento no front-end

Correção de um problema em que os produtos configuráveis exibiam um comportamento de front-end incorreto quando um atributo de amostra de cor era incluído, fazendo com que os preços, o layout suspenso e os indicadores de campo obrigatórios fossem exibidos incorretamente.
Agora, os produtos configuráveis são renderizados corretamente com preços adequados, menus suspensos alinhados e o comportamento esperado da interface do usuário.

_AC-1014 - [Problema do GitHub](https://github.com/magento/magento2/issues/14296) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Incompatibilidade de cadeia de caracteres de declaração de preço quando o Produto configurável é atribuído ao Estoque de teste e ao Site de teste com a opção de exibir produtos indisponíveis habilitada

Atualização do teste de falha para alinhar-se ao comportamento de preço real para produtos configuráveis quando todos os produtos secundários têm o mesmo preço.
A asserção agora valida corretamente o preço exibido, evitando falhas falsas de teste sem afetar a funcionalidade.

_AC-10843 - [Contribuição de código do GitHub](https://github.com/magento/inventory/commit/1ccc786b)_

#### A etiqueta &quot;Tão baixo quanto&quot; ainda é exibida para um Produto configurável para o caso de teste AC-6158

Produtos configuráveis implementados e verificados (P1-P7) com as respectivas variações e atribuições de categoria. Garantia de exibição correta do preço da loja e do comportamento de etiqueta &quot;Tão baixo quanto&quot; para produtos da Categoria C.

_AC-10847 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Desconto percentual na regra de preço de camada e de catálogo calculado no preço original sem opções selecionadas.

Descontos percentuais nas regras de preço de camada e preço de catálogo agora incluem opções personalizadas selecionadas.
Anteriormente, os descontos percentuais eram calculados no preço original do produto sem considerar as opções personalizadas selecionadas, resultando em preços finais incorretos.
AC-12004

_AC-12004 - [Problema do GitHub](https://github.com/magento/magento2/issues/38750)_

#### [A classificação de validação do problema] não está funcionando, o seletor da classificação de revisão foi alterado

Correção de um problema em que a validação da classificação de revisão não era acionada devido a uma alteração no seletor. Anteriormente, as análises podiam ser salvas sem selecionar uma classificação. Após a correção, a validação funciona corretamente e impede salvar uma revisão, a menos que uma classificação seja selecionada.

_AC-12686 - [Problema do GitHub](https://github.com/magento/magento2/issues/33424) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Quantidade de pedidos de produtos ausentes permitidos no Magento 2.4.7 min

O sistema está funcionando bem e a origem da página está mostrando corretamente a quantidade mínima do produto

_AC-12909 - [Problema do GitHub](https://github.com/magento/magento2/issues/39142) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39480)_

#### Coleção de produtos - addMediaGalleryData chama getSize quando a coleção pode ou será carregada (Pode usar count para evitar uma consulta DB extra)

Esta PR reduz a chamada de consulta extra usando count() se a coleção de produtos já estiver carregada ao chamar o Graphql do produto com o campo media_gallery incluído.

_AC-13055 - [Problema do GitHub](https://github.com/magento/magento2/issues/39111) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39681)_

#### Manuseio de SKU inválido para produtos vinculados no Magento

Correção de um problema em que os produtos com SKU &quot;0&quot; não podiam ser vinculados como itens relacionados, venda adicional ou venda cruzada devido à validação inválida de SKU. A atualização garante que esses produtos possam ser vinculados com sucesso, permitindo que o produto seja salvo sem erros.

_AC-13311 - [Problema do GitHub](https://github.com/magento/magento2/issues/39329) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Problema com a grade de Opções personalizáveis na página do produto no painel de administração

O sistema está funcionando como esperado quando estamos criando opções personalizáveis com a lista suspensa de tipos

_AC-14003 - [Problema do GitHub](https://github.com/magento/magento2/issues/39640) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39694)_

#### Erro de página de produto do administrador quando todos os atributos de produto são definidos como escopo global

Correção de um problema em que a página de edição do produto de administrador exibia um erro quando todos os atributos do produto eram definidos como escopo global. O erro foi causado por uma consulta vazia ao banco de dados, tornando a página inutilizável. Após a correção, a página do produto é renderizada corretamente e os produtos podem ser criados sem problemas.

_AC-14011 - [Problema do GitHub](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] Nenhum retorno de chamada encontrado para o trabalho cron catalog_product_alert

agora, o Adobe Commerce impede corretamente que trabalhos de cron de catalog_product_alert incorretos sejam agendados depois que o trabalho cron de alerta do produto for renomeado para product_alert. Anteriormente, no Adobe Commerce 2.4.8, a configuração de Lojas > Configuração > Catálogo > Catálogo > Configurações de execução de alertas de produto fazia com que uma entrada catalog_product_alert do cron fosse criada em core_config_data e, quando o cron executava, registrava o erro Magento_Cron.CRITICAL: Exceção: Nenhum retorno de chamada encontrado para o trabalho cron catalog_product_alert, mesmo que os trabalhos product_alert válidos estivessem sendo executados corretamente.

_AC-14494 - [Problema do GitHub](https://github.com/magento/magento2/issues/39800) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### A [Lista de Comparação de Produtos] não poderá ser usada

Correção de um problema em que a lista de comparação ficava inutilizável quando o mesmo produto era adicionado de diferentes exibições da loja; após a correção, a lista de comparação era carregada corretamente e exibia itens com base na loja específica.

_AC-14885 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Falha No Registro Extra Ao Solicitar Um Produto Por Meio Do Repositório

Mensagens de erro aprimoradas para ProductRepository::get e getById quando um SKU ou ID não é encontrado.
Anteriormente, as exceções não forneciam contexto sobre qual SKU ou ID causava o erro.
Agora, a mensagem de exceção inclui o SKU ou a ID ausente, ajudando na depuração e melhorando a experiência do desenvolvedor.
Essa alteração não afeta nenhum comportamento funcional da API.

_AC-15199 - [Problema do GitHub](https://github.com/magento/magento2/issues/40090) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Erro O conjunto de atributos não existe quebra a página

Correção de um problema em que inserir uma ID de conjunto de atributos inválida no URL causava um erro fatal; o sistema agora exibe uma mensagem de erro apropriada informando que o conjunto de atributos não existe em vez de quebrar a página.

_AC-15753 - [Problema do GitHub](https://github.com/magento/magento2/issues/40213) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Restituição com quantidade negativa sempre restituição descontada

Correção de um problema em que a criação de um aviso de crédito com uma quantidade negativa reembolsava incorretamente o valor do desconto.
Agora, os descontos não são reembolsados para quantidades negativas e a quantidade de restituição é definida corretamente como zero.

_AC-9424 - [Problema do GitHub](https://github.com/magento/magento2/issues/37917) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### A consulta lenta é executada quando o widget do produto é incluído pelo pagebuilder

A Consulta para a criação de widgets de produtos, incluindo SKUs de produtos, é otimizada.

_ACP2E-3449 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Imagens de produto não redimensionadas quando adicionadas como produto configurável

Anteriormente, as imagens adicionadas por meio das Configurações no painel de administração não seguiam o limite de tamanho máximo do upload, o que poderia levar a inconsistências e desafios de gerenciamento. Agora, uma correção foi implementada para garantir que as imagens sejam redimensionadas automaticamente durante o upload para atender ao limite de tamanho máximo, simplificando o processo e mantendo os padrões do sistema.

_ACP2E-3504 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Todos os itens das listas de comparação de outros clientes são atribuídos ao cliente depois de fazer logon por meio do administrador

Anteriormente, quando um administrador usava o recurso &quot;Fazer logon como cliente&quot; no back-end, os produtos da lista de comparação de um cliente conectado anteriormente eram atribuídos incorretamente ao cliente representado no momento.  Depois da correção, a lista de comparação é carregada corretamente para o cliente conectado corretamente.

_ACP2E-3818 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### [B2B] O Salvamento Do Catálogo Compartilhado Retorna Um Erro De Funcionalidade Obsoleta

O administrador pode cancelar a atribuição de produtos do Catálogo compartilhado.
Cancelar a atribuição de produtos com um grande número de SKUs de produtos longos do Catálogo compartilhado resultava em erro

_ACP2E-4097 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### O desempenho de geração do Mapa de Site da [Nuvem] foi significativamente reduzido

A geração de mapas do site para produtos com imagens não apresenta mais lentidão exponencial. Anteriormente, a geração de mapas de site para lojas com inclusão de imagem ativada resultava em tempos de processamento longos.

_ACP2E-4153 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Produto, Imposto

#### O Imposto Fixo sobre o Produto (FPT) não é exibido separadamente com os produtos configuráveis

Correção de um problema em que o FPT (Fixed Product Tax) não era exibido separadamente para produtos configuráveis após selecionar uma opção. Agora, o detalhamento do FPT aparece corretamente na lista de produtos e nas páginas de detalhes, correspondendo ao formato de exibição de produtos simples.

_AC-13171 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

### Promoção

#### Comprar X Obter Y regra de preço do carrinho adiciona desconto incorreto quando outra regra já foi aplicada

Correção de um problema em que a regra de preço do carrinho Comprar X Obter Y calculava descontos usando o preço original do produto mesmo após outra regra já tê-lo reduzido. A atualização garante que a segunda regra agora aplique o desconto ao preço ajustado, resultando em descontos totais precisos quando várias promoções estão ativas.

_AC-12325 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Erro ao obter descontos do item da ordem apply_to para ordem do cliente por meio de solicitação GraphQl do cliente

Anteriormente, quando os descontos aplicados em ordem do cliente por meio do GraphQl, o erro do servidor interno de solicitação do cliente foi observado, o que agora é fixo, e os dados adequados da ordem do cliente com desconto aplicado são obtidos

_AC-14888 - [Problema do GitHub](https://github.com/magento/magento2/issues/39963) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Erro ao obter o código do cupom do item da ordem para a ordem do cliente por meio da solicitação de cliente GraphQl

Correção de um problema em que a busca de pedidos com detalhes de cupom por meio do GraphQL retornava um erro interno do servidor.
Agora, o query é executado com sucesso e retorna as informações corretas do cupom na resposta.

_AC-14889 - [Problema do GitHub](https://github.com/magento/magento2/issues/39962) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### `[Cloud][experienceleague]` Regra de preço de catálogo não aplicada

Antes das regras de preço fixo do catálogo não se aplicavam quando `special_price` era definido somente no nível do site (não em &quot;Todas as Exibições da Loja&quot;). Depois que as regras de preço fixo do catálogo agora se aplicam corretamente quando `special_price` é definido no nível do site, verificando primeiro a loja padrão do site.

_ACP2E-4372 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath() não tem filtragem entity_type, fazendo com que as páginas do CMS sejam tratadas como produtos em URLs de categoria

Correção de um problema em que o DynamicStorage não filtrava por entity_type, fazendo com que as páginas do CMS fossem tratadas incorretamente como produtos em URLs de categoria; URLs malformados agora retornam corretamente um 404 em vez de veicular conteúdo do CMS.

_AC-14991 - [Problema do GitHub](https://github.com/magento/magento2/issues/39996) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Habilitar o caminho de categoria nos urls do produto interrompe o alternador de loja de várias maneiras

Correção de um problema em que a ativação de caminhos de categoria em URLs de produtos causava falha do alternador de loja; a alternância de loja agora resolve corretamente os URLs de produto nas visualizações da loja sem redirecionar para a página inicial ou retornar erros.

_AC-15110 - [Problema do GitHub](https://github.com/magento/magento2/issues/40037) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Chave de matriz indefinida em ProductRepository getById

O problema ocorria quando ProductRepository::getById() era chamado com uma ID inválida, como 123abc, resultando em um erro &quot;Chave de matriz indefinida&quot;.
Após a correção no Magento 2.4.9-alpha3, essas solicitações agora retornam corretamente uma página 404, em vez de lançar uma exceção.
O controle de qualidade foi confirmado com IDs válidas e malformadas e nenhum outro problema foi observado.

_AC-15345 - [Problema do GitHub](https://github.com/magento/magento2/issues/40146) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### O produto de comparação da loja cria um erro de SEO do Google - Os links não são rastreáveis

Solução de um problema de SEO em que o link &quot;Comparar produtos&quot; da loja não era rastreável por mecanismos de pesquisa devido a um atributo href ausente ou incorretamente vinculado. A atualização garante que o link agora contenha um URL rastreável válido, melhorando a descoberta do site e ajudando a passar nas auditorias de SEO da Google.

_AC-15547 - [Problema do GitHub](https://github.com/magento/magento2/issues/40185) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Atualizar a url_key do produto por meio da API REST não gera uma Reescrita de URL 301

Ao atualizar a chave de URL do produto por meio da API REST, com a configuração &quot;Criar redirecionamento permanente para URLs se a chave de URL mudar&quot; definida como Sim, as substituições de URL do produto serão criadas para redirecionar do URL antigo para um novo.

_ACP2E-3900 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Geração de mapa de site [Cloud] nunca termina

Antes da correção, não era possível concluir com êxito a geração do mapa de site se o catálogo contivesse mais de um milhão de produtos. Após a correção, a geração do mapa de site será concluída com uma alocação de memória mais baixa e com até um milhão de produtos por loja.

_ACP2E-3902 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### O alternador de armazenamento da [Cloud] não está funcionando do EN para o FR na página de perguntas frequentes

Correção de um problema em que a alternância entre exibições de loja redirecionava os usuários para a página inicial em vez da página do CMS traduzida correspondente. O alternador de loja agora verifica as substituições de URL no armazenamento de destino para garantir o redirecionamento correto (por exemplo, página de perguntas frequentes em inglês → página de perguntas frequentes em francês).

_ACP2E-4112 - [Problema do GitHub](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [Nuvem] Desativar a geração de mapa de site antiga

Uma nova opção de configuração agora está disponível para alternar entre o processo padrão de geração de mapa de site e um modo de lote recém-implementado. Esse aprimoramento permite maior flexibilidade e escalabilidade nos fluxos de trabalho de criação de mapas do site.

_ACP2E-4132 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Solicitações suspeitas estão gerando exceções no exception.log

Correção de um problema em que solicitações de URL mal-intencionadas ou malformadas estavam causando erros de agrupamento do banco de dados e preenchendo logs de exceção.
Anteriormente, quando solicitações suspeitas contendo codificações de caracteres inválidas ou caracteres não suportados eram recebidas, o sistema tentava decodificá-las e processá-las, resultando em conflitos de agrupamento MySQL.

_ACP2E-4328 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2687b487)_

### Vendas

#### Quando a mensagem de presente está ativada no nível do pedido, mas o usuário não insere dados e faz o pedido, então ainda Do nome e Até o nome no administrador, mostrando o nome e sobrenome do cliente.

Correção de um problema em que os campos de remetente e destinatário da mensagem de presente eram preenchidos automaticamente com nomes de clientes, mesmo quando nenhuma mensagem de presente era inserida; os campos agora permanecem vazios, a menos que o usuário forneça os detalhes.

_AC-15140 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

### Pesquisar

#### &quot;Confirmar reenvio do formulário&quot; na pesquisa do catálogo com &quot;Lembrar paginação de categoria&quot;

Navegar de volta de uma página de produto para a página Resultados da pesquisa no catálogo depois de modificar as configurações da barra de ferramentas não acionará mais a caixa de diálogo &quot;Confirmar reenvio do formulário&quot; quando a opção &quot;Lembrar paginação de categoria&quot; estiver ativada.
Anteriormente, os usuários encontravam um erro no navegador ou um aviso sobre o reenvio de formulário ao retornar à página de resultados da pesquisa após alterar parâmetros da barra de ferramentas, como ordem de classificação.

_ACP2E-4208 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### O campo de pesquisa agregada &quot;_search&quot; não é mais usado na consulta de pesquisa

Agora, a pesquisa de texto completo retorna produtos correspondentes se a condição mínima de correspondência for atendida em todos os campos pesquisáveis coletivamente, em vez de exigir que a condição seja atendida por um único campo.

_ACP2E-4285 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cbca0396)_

### Segurança

#### Erro interno do servidor

A Magento agora adiciona produtos com sucesso ao carrinho de um cliente ao usar o endpoint REST assíncrono POST /rest/default/async/V1/carts/mine/items. Anteriormente, essa solicitação assíncrona de &quot;adicionar ao carrinho&quot; resultava em um Erro de Servidor Interno, e o Magento registrava o seguinte erro: Erro: Chamada para uma função de membro setFinalPrice() em nulo em app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162.

_AC-16344 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### JS agrupado/mesclado que não faz parte dos hashes da SRI

Antes da correção, os arquivos gerados ou mesclados não eram adicionados à lista de hashes SRI. Agora, os arquivos estão sendo adicionados corretamente aos hashes SRI.

_ACP2E-3854 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### [NUVEM] Problema de permissão gravável na newrelic

Antes da correção, os registros estavam desorganizados com exceções. Após aplicar a correção, os logs agora estão limpos e sem exceções.

_ACP2E-4296 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Envio

#### Quantidade incorreta para remessa após alguns avisos de crédito

Correção de um problema em que o valor de Qtd. para Entrega era calculado incorretamente após vários avisos de crédito, permitindo a entrega de itens reembolsados.
Agora, o sistema atualiza com precisão a quantidade entregável remanescente com base nos itens entregues e reembolsados, evitando entregas inválidas.

_AC-1479 - [Problema do GitHub](https://github.com/magento/magento2/issues/34289) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Possível problema de desempenho no carregamento de métodos de envio

Otimização do processo de carregamento dos métodos de envio, garantindo que apenas as transportadoras ativas sejam carregadas quando solicitado. Anteriormente, as fábricas para todos os métodos de envio eram inicializadas, causando sobrecarga desnecessária no desempenho. A correção melhora a eficiência ao carregar condicionalmente apenas transportadoras ativas, reduzindo o tempo de carga e o uso de recursos.

_AC-15415 - [Problema do GitHub](https://github.com/magento/magento2/issues/40153) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### [Problema] Destino comercial não deve ser tratado como residencial

Correção de um problema na integração de envio UPS REST em que destinos comerciais eram tratados incorretamente como residenciais. O ResidentialAddressIndicator agora está incluído na solicitação de taxa de UPS somente para endereços residenciais, evitando sobretaxas residenciais não intencionais e garantindo taxas de envio comerciais precisas.

_AC-16285 - [Problema do GitHub](https://github.com/magento/magento2/issues/40314) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/40307)_

#### Exceção ao criar rótulo de remessa UPS

Aviso fixo: conversão de matriz em sequência de caracteres durante a criação do rótulo de remessa UPS

_ACP2E-3676 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - O módulo principal Magento_Fedex verifica se há um token ativo válido antes de enviar uma solicitação para obter um novo?

A Adobe Commerce não faz mais muitas solicitações ao serviço de API FedEx para o token de acesso. Anteriormente, mesmo que o token de acesso ainda seja válido, o Adobe Commerce sempre faz novas solicitações à API FedEx, o que causou um problema de limitação de taxa.

_ACP2E-3930 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Preparo e visualização

#### O preço do produto no carrinho afetado pela regra de preço do catálogo não é alterado quando a regra é ajustada pela atualização de preparo

Correção de um problema em que os preços do produto no carrinho não eram totalmente atualizados após a modificação de uma regra de preço de catálogo por meio de uma atualização em preparo. Anteriormente, o preço atualizado aparecia somente na seção de resumo, enquanto o bloco do carrinho central mostrava o valor antigo. Agora, a regra revisada atualiza corretamente o preço do produto em todo o carrinho.

_AC-15304 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Quando a atualização programada para a categoria é excluída, a quantidade de filhos não é diminuída para a categoria pai

Correção de um problema em que a exclusão de uma atualização agendada para uma categoria não reduzia a contagem de filhos da categoria pai, garantindo as atualizações de contagem corretas quando as atualizações ou subcategorias agendadas são removidas.

_AC-15670 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Ao editar a atualização agendada para categorias, ele adiciona o valor filho à categoria pai

Correção de um problema em que a edição de uma atualização agendada existente para uma subcategoria aumentava incorretamente o child_count para categorias pai no banco de dados. O problema causou dados imprecisos da hierarquia de categoria após salvar as atualizações. Após a correção, a contagem de filhos permanece correta e não é mais incrementada inesperadamente.

_AC-16239 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Visualizar uma atualização agendada abre a primeira exibição de loja em ordem alfabética em vez da exibição de loja de interesse

Antes da correção, a visualização de uma atualização agendada era aberta na primeira exibição da loja em ordem alfabética, em vez da exibição da loja atribuída.
Após a correção, a pré-visualização agora é aberta corretamente na visualização de loja atribuída à atualização de preparo de bloco do CMS.

_ACP2E-3671 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### Não é possível visualizar a Atualização de produto agendada com as Permissões de categoria ativadas

Antes da correção, um futuro produto a ser ativado não era exibido no modo de visualização. Agora ele será exibido mesmo se o status atual estiver desativado.

_ACP2E-3786 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Validação ausente para o campo de valor de desconto da regra de Preço de Catálogo

Anteriormente, o campo discount_amount na atualização da programação de preparo não era validado corretamente com as regras de validação atuais. No entanto, após a aplicação da correção, o campo discount_amount será validado adequadamente.

_ACP2E-3867 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### O pacote de produtos com atualizações agendadas remove a opção de itens de pacote na ação de salvamento do produto

A remoção das opções de pacote de produtos ou dos produtos associados na atualização agendada não afeta mais as opções de pacote originais e os produtos associados, e vice-versa. Além disso, a remoção de opções de produção agrupadas no produto original e a substituição por outras opções após o agendamento de uma atualização não resulta mais na remoção das opções adicionadas recentemente

_ACP2E-4212 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Não é possível navegar entre sites na visualização da Atualização da programação

Antes dessa correção, a visualização da atualização agendada falhava ao tentar visualizar o conteúdo de lojas com domínios personalizados. Após essa correção, os domínios de armazenamento personalizados podem ser visualizados como estão e navegados no iframe de visualização. A correção abrange produtos, categorias, páginas do CMS e blocos do CMS, além de oferecer suporte a links de navegação usando as marcas de marcação `{{store url}}`, conforme documentado em [Variáveis e Marcas de Marcação do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/variables/markup-tags).

_ACP2E-4308 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Imposto

#### Total da ordem errada, a rodada não é aplicada ao cálculo de preço.

O sistema agora é manipulado corretamente ao calcular o price_after_discount, o discount_amount e o valor dos impostos.
o total real do pedido

_AC-11389 - [Problema do GitHub](https://github.com/magento/magento2/issues/38455) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/39687)_

#### [Correção de Problema]: o Valor de base_weee_tax_plied_row_amnt dos Itens do Aviso de Crédito está Incorreto

Corrigido o cálculo do aviso de crédito usando o configurador adequado para base_wee_tax_plied_row_amnt, garantindo que o valor do imposto refletisse somente a quantidade reembolsada. Anteriormente, o valor da linha usava incorretamente o valor total da ordem em vez do valor parcial do aviso de crédito.

_AC-12049 - [Problema do GitHub](https://github.com/magento/magento2/issues/38765) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Os itens no minicarrinho exibem preços em moeda estrangeira sem conversão

O minicarrinho agora converte a moeda corretamente e exibe o valor preciso com base nas taxas de conversão configuradas.

_ACP2E-4364 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Estrutura de teste

#### [Problema] Remova uma marca &lt;severity> duplicada do teste MFTF AdminSetUpWatermarkForSwatchImageTest

O sistema agora inclui apenas uma única tag de severidade no AdminSetUpWatermarkForSwatchImageTest, melhorando a clareza e a consistência do código. Anteriormente, esse teste continha duas tags de gravidade idênticas, o que era desnecessário e poderia causar confusão.

_AC-11873 - [Problema do GitHub](https://github.com/magento/magento2/issues/38504) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/31862)_

#### [Problema] Ignore lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

O sistema agora ignora o arquivo &#39;env.php&#39; que é gerado ao executar testes de unidade, garantindo que o status do Git permaneça limpo após a execução dos testes. Anteriormente, a execução de testes de unidade gerava um novo arquivo &quot;env.php&quot;, fazendo com que o status do Git mostrasse um novo arquivo encontrado e o sujasse.

_AC-13293 - [Problema do GitHub](https://github.com/magento/magento2/issues/39304) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problema] Corrigir problema de teste de integração com o interceptor

O sistema agora identifica e lida corretamente com o \Magento\TestFramework\App\Config\Interceptor no teste de integração, garantindo que o teste possa acessar os dados necessários mesmo quando existir um plug-in na classe. Anteriormente, o sistema não levava em conta a possibilidade de o \Magento\TestFramework\App\Config ser um \Magento\TestFramework\App\Config\Interceptor, resultando em um erro ao tentar acessar a propriedade $data.

_AC-13305 - [Problema do GitHub](https://github.com/magento/magento2/issues/39324) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problema] MFTF: Enviando Email para Formulário Amigo com captcha habilitado

O caso de teste aborda a funcionalidade do formulário &quot;Enviar email para um amigo&quot; quando o CAPTCHA está ativado, garantindo que o processo de envio do formulário funcione corretamente com valores CAPTCHA incorretos e corretos.

_AC-13492 - [Problema do GitHub](https://github.com/magento/magento2/issues/39462) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/32830)_

#### Os caminhos fixos codificados falham nas compilações do Composer

_AC-16488_

#### [Problema] magento/magento2#: mutação GraphQl. Cobertura de teste adicional para configurações de storeConfig do cliente.

O Sistema agora adiciona a cobertura de teste adicional para as próximas opções storeConfig do cliente:
required_character_classes_number
minimum_password_length

_AC-9370 - [Problema do GitHub](https://github.com/magento/magento2/issues/37915) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/28761)_

#### Falhas nos testes de unidade específicos do ambiente em AC 2.4.7-p3

Esse problema corrige falhas de teste de unidade que não estão se reproduzindo em todas as versões e ambientes. Antes da correção, alguns testes de unidade falhavam devido a diferentes versões de biblioteca ou devido à falta de funcionalidade adicionada em uma versão posterior.

_ACP2E-3712 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

### Estrutura da interface

#### [Problema] Remova as variáveis duplicadas de um dos arquivos a menos

O sistema agora remove as variáveis duplicadas de menos arquivos, garantindo um código mais limpo e eficiente. Anteriormente, essas variáveis duplicadas estavam presentes nos menos arquivos, resultando em redundância desnecessária no código.

_AC-11743 - [Problema do GitHub](https://github.com/magento/magento2/issues/31154) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/31150)_

#### O WYSIWYG está vazio em linhas dinâmicas

Os campos do WYSIWYG em linhas dinâmicas agora são inicializados e preenchidos corretamente.
Anteriormente, os campos do WYSIWYG em linhas dinâmicas (como em formulários de configuração de design) podiam parecer vazios ou perder seu conteúdo após determinadas ações, exigindo intervenção manual para restaurar dados.
AC-12336

_AC-12336 - [Problema do GitHub](https://github.com/magento/magento2/issues/38893) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problema] Corrigir erro de tipo MIME

O sistema manipula e corrigiu corretamente o tipo MIME e o erro de digitação da imagem gif

_AC-8001 - [Problema do GitHub](https://github.com/magento/magento2/issues/36899) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problema] Remover a marca `@author` proibida de `Magento_Backend`

Esta PR remove a tag `@author` da base de código

_AC-8814 - [Problema do GitHub](https://github.com/magento/magento2/issues/37522) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/36976)_

#### [Problema] Evite acesso direto à lista de revisões do Ajax

O sistema manipula corretamente e Evita acesso direto à lista de revisões do Ajax

_AC-9381 - [Problema do GitHub](https://github.com/magento/magento2/issues/37920) - [Contribuição de código do GitHub](https://github.com/magento/magento2/pull/33876)_

#### Cabeçalho Logon/Logout não atualizado na configuração de várias lojas com cookies compartilhados

O cabeçalho de logon é atualizado corretamente no logout, de acordo com as configurações. O customer-data.js usará um cookie para armazenar o valor &quot;mage-customer-login&quot; se as contas do cliente forem compartilhadas globalmente. Caso contrário, o armazenamento local será usado.

_ACP2E-4149 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### O [Mobile] Fotorama pode abrir o Mini Carrinho na ação de fechamento do Visualizador de Imagem

Correção do problema com a Fotorama. Anteriormente, um Minicarrinho era aberto na ação de fechamento do Visualizador de imagem

_ACP2E-4231 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Os arquivos js mesclados não são gerados corretamente em projetos com muitas lojas.

A mesclagem de arquivos do JavaScript agora funciona corretamente quando vários armazenamentos são configurados.
Anteriormente, os arquivos às vezes não eram mesclados corretamente em configurações de várias lojas, resultando em resultados incompletos ou inconsistentes.

_ACP2E-4246 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/ab891304)_

### Atualizações - Ferramenta de compatibilidade de atualização

#### Funcionalidade obsoleta: criação de propriedade dinâmica Magento\Framework\Acl::$_roleRegistry

Os erros de funcionalidade obsoleta não impedem mais o acesso ao painel de administração após a atualização.
Anteriormente, após a atualização para o Magento 2.4.6, tentar acessar o painel de administração podia resultar no erro:
&quot;Funcionalidade obsoleta: a criação da propriedade dinâmica Magento\Framework\Acl::$_roleRegistry está obsoleta em vendor/magento/framework/Session/SessionManager.php na linha 186&quot;
Isso impedia que os administradores fizessem logon.
AC-12343

_AC-12343 - [Problema do GitHub](https://github.com/magento/magento2/issues/37469)_
