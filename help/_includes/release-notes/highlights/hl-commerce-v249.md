---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Destaques do Adobe Commerce (v2.4.9)

## Destaques na v2.4.9

Os destaques a seguir se aplicam à versão 2.4.9 do Adobe Commerce.

### Alterações na REST API

#### Controle de herança da galeria de produtos da API REST no nível de exibição da loja

Atualizar um produto por meio da API REST em um escopo de armazenamento não faz mais com que imagens e vídeos de produtos herdem alterações do escopo global quando `media_gallery_entries` é omitido da carga ou definido como `NULL`. Agora também é possível restaurar a herança do escopo de imagens e vídeos do produto por meio da API REST, definindo o campo correspondente como `NULL`.

Ao atualizar produtos por meio da API REST no nível de exibição da loja:

- Omitir `media_gallery_entries` ou defini-lo como NULL agora preservará a herança da galeria padrão/global.
- Para restaurar a herança de atributos de galeria específicos (como `label`, `position`, `disabled`, `video_title`, `video_description`), defina esses campos como NULL dentro da matriz `media_gallery_entries`.

Essa alteração garante que as exibições de armazenamento possam manter ou restaurar facilmente os valores padrão da galeria, reduzindo a confusão e tornando o gerenciamento da galeria mais consistente.

_ACP2E-4358 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Alterações na API do GraphQL

#### A mutação do GraphQL `clearCart` agora está disponível no Magento Open Source

A mutação do GraphQL [clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/) agora está disponível para todos os usuários do Magento Open Source. Anteriormente, essa mutação só era acessível no Adobe Commerce.

_AC-16683 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### Mais erros descritivos da mutação do GraphQL `applyGiftCardToCart`

Tratamento de erros aprimorado para a mutação `applyGiftCardToCart`. A mutação agora retorna mensagens de erro específicas para casos como cartões-presente expirados ou com saldo zero, melhorando a experiência do comprador. Além disso, o back-end impede a aplicação de cartões-presente extras a pedidos que já são gratuitos.

_LYNX-787_

#### A nova mutação do GraphQL `clearWishlist` remove todos os itens da lista de desejos de uma só vez

Adição de uma mutação `clearWishlist` que remove todos os itens de uma lista de desejos em uma única chamada.

_LYNX-790_

#### Nova mutação do GraphQL `exchangeExternalCustomerToken` para autenticação baseada em integração

Introdução de uma nova mutação do GraphQL `exchangeExternalCustomerToken` que autentica usuários por meio de um token de integração e retorna o token do cliente e os dados do cliente associados.

_LYNX-815_


#### Novas consultas do GraphQL retornam IDs de grupos de clientes, segmentos e regras de carrinho aplicadas

Novas consultas do GraphQL retornam o `uid` codificado do grupo de clientes, segmentos de clientes e regras de carrinho aplicados.

_LYNX-867_

#### As opções de presente são limpas automaticamente quando o carrinho é esvaziado

Correção de um problema em que as opções de presente persistiam em um carrinho vazio após a remoção de todos os itens. As opções de presentes agora são limpas automaticamente quando o carrinho é esvaziado, correspondendo ao comportamento existente para cupons.

_LYNX-786_

#### As opções de presente são mescladas de forma consistente quando os carrinhos do cliente e do convidado são combinados

As opções de presente aprimoradas são manipuladas durante mesclagens de carrinho para garantir uma experiência do usuário mais consistente. As opções de presentes agora seguem uma lógica de mesclagem priorizada, evitando substituições não intencionais quando um usuário convidado faz logon e seu carrinho é mesclado com um carrinho de cliente existente.

_LYNX-788_

#### Novo campo `grand_total_excl_tax` na resposta `OrderTotal` do GraphQL

Um novo campo, `OrderTotal.grand_total_excl_tax`, foi adicionado à resposta de pedido do GraphQL. Este campo fornece o total geral do pedido excluindo impostos, facilitando o acesso a totais com isenção de impostos diretamente da API.

Benefícios:

- Recupere facilmente o total geral, excluindo impostos, para qualquer pedido por meio do GraphQL.
- Simplifica a integração com sistemas externos que exigem totais de impostos exclusivos.
- Reduz a necessidade de cálculos personalizados no lado do cliente.

_LYNX-892_

#### Os pedidos históricos mostram detalhes de produtos que estão esgotados

Os pedidos históricos agora exibem detalhes completos do produto para itens de linha, mesmo depois que o produto tiver esgotado o estoque, para que os clientes e comerciantes mantenham um registro completo do que foi comprado.

_LYNX-913_

#### Validação do reCAPTCHA adicionada a `updateCustomer`, `updateCustomerV2` e `contactUs` mutações do GraphQL

Quando o reCAPTCHA é habilitado para os formulários de vitrine correspondentes, as mutações do GraphQL `updateCustomer`, `updateCustomerV2` e `contactUs` agora impõem a mesma validação, ajudando a impedir abusos automatizados por meio da API.

_LYNX-941_

#### Validação do reCAPTCHA adicionada à mutação do GraphQL `applyCouponsToCart`

Quando o reCAPTCHA é habilitado para o formulário de cupom, a mutação do GraphQL `applyCouponsToCart` agora impõe a mesma validação, ajudando a impedir a enumeração de código de cupom por meio da API.

_LYNX-942_

#### Campo `customer_id` da API do GraphQL B2B restaurado e com suporte total

O campo `customer_id` na API B2B do GraphQL é restaurado e agora retorna o valor correto em consultas e mutações de gerenciamento da empresa. Anteriormente, o campo era obsoleto e retornava `null`, o que limitava sua utilidade para integrações B2B.

_LYNX-955_

### Interface do administrador

#### Menu de ações da grade de regras de preço do catálogo

A grade **Regras de Preço de Catálogo** no Administrador do Commerce agora inclui um menu **Ações**, permitindo que os comerciantes ativem, desativem ou excluam várias regras de uma só vez. Isso alinha o gerenciamento de regras de preços de catálogo com as ações em massa existentes disponíveis para as **Regras de preço do carrinho**, reduzindo significativamente o tempo necessário para gerenciar grandes conjuntos de regras.

_AC-13916_

#### Visualização do modo de exibição móvel para preparo de conteúdo

O recurso de visualização de preparo no Admin agora renderiza visualizações de dispositivos móveis simuladas em navegadores com precisão, para que os comerciantes possam ver como uma atualização em etapas aparecerá em um dispositivo móvel antes que ele entre em funcionamento.

_ACP2E-3397 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### A nova configuração de administrador controla o comportamento de mesclagem de carrinho de cliente e convidado na entrada

Os comerciantes agora podem escolher como os itens do carrinho são mesclados quando um convidado entra e já tem um carrinho do cliente:

- **Prioridade do Convidado** — Use a quantidade do carrinho de convidado.
- **Prioridade do Cliente** — Use a quantidade de carrinhos do cliente.
- **Mesclar Quantidades** (padrão) — Soma ambas as quantidades.

Configure este comportamento em **Lojas** > **Configuração** > **Vendas** > **Check-out**, na **Preferência de mesclagem de carrinho**. A configuração se aplica a todos os tipos de produtos, fornecendo aos comerciantes total controle sobre como os carrinhos de convidado e de cliente são combinados na entrada.

_LYNX-889_

### Braintree

#### Check-out expresso

- **Ofertas promocionais na folha de pagamento expressa do Google Pay**

  A folha de pagamento do Google Pay Express agora aceita códigos promocionais e de ofertas. Os compradores podem aplicar, visualizar e remover promoções de carrinho do Commerce diretamente na folha de pagamento do Google, de modo que os clientes de check-out expresso recebem os mesmos descontos e incentivos dos fluxos de check-out padrão.

  _PACOTE-3476_

- **Ofertas promocionais na folha de pagamento expressa do Apple Pay**

  A folha de pagamento do Apple Pay Express agora aceita códigos promocionais e de ofertas. Os compradores podem aplicar um cupom diretamente na folha de pagamento do Apple, para que os usuários do checkout expresso se beneficiem dos mesmos descontos e campanhas que os fluxos de check-out padrão.

  _PACOTE-3477_

- **Apple Pay on Chrome e Firefox**

  O Apple Pay agora pode ser usado no Chrome e no Firefox, não apenas no Safari. Quando o Apple Pay Express está ativado, os botões Apple Pay estão disponíveis nas páginas PDP, minicarrinho, carrinho e check-out, e os clientes concluem o pagamento digitalizando um código com sua iPhone.

  _PACOTE-3478_

- **Retorno de chamada de remessa do lado do servidor para PayPal Express**

  A chamada de retorno do PayPal Express foi movida do lado do cliente para o lado do servidor. Isso fornece métodos de envio dinâmicos, cálculos de custo em tempo real e detalhes precisos no nível do carrinho diretamente no modal do PayPal, melhorando a confiabilidade e estabelecendo a base para recursos futuros, como suporte ao Módulo de Contato, fluxos de troca de aplicativo e Venmo Express.

  _PACOTE-3479_

- **Módulo de Contato do PayPal para check-out expresso do comerciante dos EUA**

  Um novo Módulo de Contato do PayPal é introduzido para comerciantes dos EUA. Quando ativado, os compradores que usam o PayPal Express podem visualizar e atualizar o endereço de email e o número de telefone compartilhados com o comerciante diretamente dentro do modal do PayPal durante os fluxos expresso (PDP, minicarrinho, carrinho, checkout express). Os detalhes de contato escolhidos são armazenados no pedido do Commerce.

  _PACOTE-3480_

#### Métodos de pagamento

- **Suporte de tipo de cartão ELO para pagamentos Braintree**

  Adição de suporte para o tipo de cartão ELO no Braintree Payments. Os administradores podem ativar o ELO na configuração do cartão de crédito e os clientes podem pagar com cartões ELO na finalização da compra.

  _PACOTE-3464_

- **Método de pagamento local em BLOCO para compradores poloneses**

  BLIK foi adicionado como um novo método de pagamento local para compradores poloneses. Isso permite pagamentos SEGUROS BULK com base em bancos dentro do fluxo existente de Métodos de Pagamento Local (LPM) da Braintree, melhorando a conveniência do checkout e a conversão para os clientes na Polônia.

  _PACOTE-3481_

- **Pagar mediante Fatura — novo método de pagamento BNPL para a Alemanha**

  Adicionado [!DNL Pay Upon Invoice] como um novo método de pagamento local para compradores alemães. [!DNL Pay Upon Invoice] é uma opção Compre agora, pague mais tarde (BNPL) fornecida pelo PayPal e Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) que permite aos clientes receber mercadorias primeiro e pagar a fatura em 30 dias sem precisar de uma conta do PayPal. Como não se trata de um pagamento imediato, a finalização do pedido é impulsionada por um webhook do lado do servidor do PayPal.

  _PACOTE-3475_

#### Compartimentalização da placa

- **Compartimentalização do Google Pay pela área da conta**

  Os clientes agora podem colocar seus cartões de pagamento Google no Vault por meio da área de conta quando o Google Pay Vault está ativado no Braintree. Os cartões com cofre são exibidos em métodos de pagamento armazenados, podem ser usados para compras futuras no check-out e podem ser excluídos pelo cliente. Isso estende o suporte à compartimentação além de Cartões e PayPal ao Google Pay.

  _PACOTE-3459_

- **Atualizador de conta em tempo real (RTAU) para cartões com cofre do Braintree**

  O recurso Real-Time Account Updater (RTAU) adicionado ao Braintree garante que os detalhes do cartão Visa, Mastercard e Discover com cofre sejam atualizados automaticamente quando os cartões expiram ou são substituídos. Isso minimiza pagamentos com falha, mantém o Commerce Vault atualizado e ignora tipos não suportados (pré-pago, Apple Pay, Google Pay) sem erros.

  _PACOTE-3462_

#### Ferramentas administrativas

- **Vincular ordem do Commerce ao portal do Braintree**

  Um link do Portal do Braintree agora é adicionado aos detalhes do pedido no Administrador do Commerce. Clicar no link abre a transação relacionada no Braintree Portal (em uma nova guia ), usando a ID do comerciante e a ID da transação do pedido do Commerce. Isso permite referência cruzada direta sem fazer logon em ambos os sistemas separadamente.

  _PACOTE-3461_

#### Segurança e compatibilidade

- **Atualização da política de segurança de conteúdo da integração Card para 3D Seguro**

  A Política de segurança de conteúdo (CSP) foi atualizada para oferecer suporte aos mais recentes requisitos de integração do Cardeal (3-D Secure). Isso garante que todos os scripts hospedados pelo Cardeal, iframes e recursos relacionados usados durante fluxos Seguros 3D sejam permitidos pelo CSP do navegador, evitando solicitações bloqueadas e experiências de desafio ou verificação quebradas.

  _PACOTE-3485_

- **Compatibilidade com o PHP 8.5 da extensão de pagamento do Braintree**

  A extensão de pagamento do Braintree foi atualizada para suportar o tempo de execução do PHP 8.5, mantendo a compatibilidade com o PHP 8.4.

  _PACOTE-3493_

### Plataforma e infraestrutura

#### Carregamentos de página mais rápidos em lojas de vários temas e vários locais após o refatoração do armazenamento de hash da SRI

O armazenamento de hash da SRI agora gera arquivos separados por área, tema e localidade, em vez de um único arquivo grande `sri-hashes.json`. Essa alteração garante que somente o arquivo de hash relevante seja carregado para cada página, melhorando os tempos de carregamento da página e reduzindo o uso da memória em lojas com vários temas ou localidades.

_AC-16113 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

#### Adicionar compatibilidade com PHPUnit 12

A dependência do Adobe Commerce Composer foi atualizada para `phpunit/phpunit` 12.x. Todos os testes são atualizados para compatibilidade, melhorando a segurança e o alinhamento com os recursos mais recentes do PHPUnit. Essa atualização mantém o Adobe Commerce pronto para versões futuras do PHP e PHPUnit.

_AC-14808_

#### Adicionar compatibilidade com o RabbitMQ 4.2

O RabbitMQ 4.2 agora é um agente de mensagens compatível. Esta atualização é um caminho de compatibilidade de curto prazo que permite que os comerciantes que dependem do protocolo AMQP continuem usando o RabbitMQ antes do fim do suporte do RabbitMQ 4.1 em fevereiro de 2026, sem uma migração imediata para o STOMP. Para implantações de longo prazo, use o Apache AtiveMQ Artemis como substituto de longo prazo do RabbitMQ.

_AC-16117_

#### O Apache AtiveMQ Artemis é o substituto de longo prazo do RabbitMQ

O Apache AtiveMQ Artemis é o agente de mensagens de longo prazo recomendado para o Adobe Commerce, orientado pelos riscos de fim de suporte associados ao RabbitMQ 4.1. O AtiveMQ Artemis é totalmente compatível com as linhas 2.4.6 a 2.4.9 do Commerce. Na Adobe Commerce Cloud, ele é fornecido como AWS AtiveMQ para implantações nativas em nuvem. Os consumidores e editores da fila podem ser configurados para usar STOMP.


As instalações existentes do RabbitMQ 4 permanecem compatíveis para comerciantes que preferem continuar usando seu serviço de fila de mensagens atual no curto prazo — consulte [Adicionar compatibilidade com o RabbitMQ 4.2](#add-compatibility-with-rabbitmq-42) acima. Planeje uma migração para o AtiveMQ Artemis para suporte a longo prazo.

_AC-14558_

#### Adicionar suporte para Valkey 9.x

O Adobe Commerce 2.4.9 expande o suporte para o Valkey as a Redis-compatible cache backend:

- **Valkey 9.x** — suporte abrangente introduzido no Adobe Commerce 2.4.9, incluindo paridade total de comandos CLI com Redis e opções de configuração de Admin e Cloud atualizadas para instalação simplificada. Esse trabalho é impulsionado pelo fim do suporte e pelas alterações de licenciamento do Redis 7.2, oferecendo aos comerciantes uma alternativa confiável e totalmente compatível com o Redis.

_AC-14103, AC-14604, AC-16122_

#### Adicionar suporte para OpenSearch 3.x

O Adobe Commerce 2.4.9 é totalmente compatível com o OpenSearch 3.x, sendo que a versão secundária mais recente agora é o mecanismo de pesquisa recomendado. Os comerciantes se beneficiam de melhor desempenho, segurança e suporte a longo prazo, enquanto a compatibilidade com versões anteriores do OpenSearch 2.x é mantida.

_AC-11846, AC-16403_

#### Adicionar suporte para MariaDB 11.8 e 12.x

MariaDB 11.8 e 12.x agora são versões de banco de dados compatíveis, permitindo que os comerciantes adotem as versões mais recentes para melhorar o desempenho do SQL e a estabilidade da plataforma a longo prazo.

_AC-16533_

### PHP e Composer

#### Compatibilidade com PHP 8.5

O Adobe Commerce 2.4.9 agora suporta PHP 8.5 e PHP 8.4, permitindo que você execute sua loja nas versões mais recentes seguras e compatíveis do PHP. Todos os recursos principais, extensões agrupadas (incluindo Page Builder, B2B, Braintree e outros) e serviços SaaS Adobe são compatíveis com o PHP 8.5.

- O PHP 8.5 e 8.4 são totalmente suportados.
- O PHP 8.3 é permitido apenas para fins de atualização (não recomendado para produção).
- Garante a conformidade com o PCI e prepara a instalação do Adobe Commerce.

_AC-15615_

#### Suporte ao PHP 8.2 removido

A partir do Adobe Commerce 2.4.9, o PHP 8.2 não é mais suportado. A plataforma agora tem como alvo o PHP 8.3 e posterior, com código principal, dependências e ferramentas atualizadas para rodar de forma limpa e confiável no PHP 8.4 e 8.5.

_AC-15758_

#### Compatibilidade do Composer 2.9 verificada

O Adobe Commerce 2.4.9 é totalmente compatível com o Composer 2.x, incluindo o Composer 2.9. A compatibilidade com versões anteriores do Composer 2.x é preservada, garantindo uma experiência estável de build e implantação para comerciantes e desenvolvedores que usam as versões mais recentes do Composer.

_AC-14481_

### Estrutura

#### Atualização de compatibilidade e segurança da estrutura JWT

Como parte da revisão contínua da segurança da plataforma, a dependência da estrutura JWT de token da Web foi avaliada e atualizada para a versão principal mais recente, garantindo compatibilidade futura e fortes padrões de segurança para autenticação baseada em token em todas as integrações da Commerce. A funcionalidade existente é totalmente preservada.

_AC-13209 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### Estrutura de testes funcionais do Adobe Commerce atualizada para dependências do Symfony LTS

O Adobe Commerce Functional Testing Framework (MFTF) foi atualizado para usar as dependências mais recentes do Symfony LTS, incluindo symfony/config, conforme exigido pela atualização do web-token/jwt-framework. Isso soluciona conflitos de dependência anteriores e garante uma pilha estável e compatível para testes funcionais.

_AC-13244_

#### As funções OAuth do PHP nativo substituem a biblioteca de terceiros

A biblioteca `carlos-mg89/oauth` de terceiros foi substituída por funções OAuth nativas do PHP, melhorando a segurança, reduzindo as dependências externas e melhorando a estabilidade da plataforma.

_AC-14075 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### O componente de cache do Symfony substitui Zend_Cache

A partir do Adobe Commerce 2.4.9, o componente Zend_Cache obsoleto foi substituído pelo componente Symfony Cache. Esta atualização melhora o desempenho e a manutenção do cache, e garante compatibilidade a longo prazo com o PHP 8.x e futuras atualizações de plataforma. Os backends de cache e os comandos de gerenciamento de cache existentes permanecem totalmente compatíveis, sem alterações necessárias para as integrações atuais.

_AC-15823_

#### O editor do WYSIWYG migrou do TinyMCE para o HugeRTE

Devido ao fim do suporte para o TinyMCE 5 e 6 e às incompatibilidades de licenciamento com o TinyMCE 7, o editor do Adobe Commerce WYSIWYG foi migrado para o editor de código aberto [HugeRTE](https://hugerte.org/). Essa migração garante que o Adobe Commerce permaneça em conformidade com o licenciamento de código aberto, evita vulnerabilidades conhecidas do TinyMCE 6 e fornece uma experiência de edição moderna e compatível para comerciantes e desenvolvedores.

_AC-14568_

#### A implementação do MVC nativo substitui o MVC do Laminas

O Adobe Commerce introduziu uma implementação nativa do MVC, substituindo o Laminas MVC legado, para garantir compatibilidade e estabilidade a longo prazo além do PHP 8.5. Essa alteração fortalece o desempenho, reduz as dependências externas e fornece uma base mais pronta para o futuro para o Commerce.

_AC-15160_

#### Suporte oficial ao Symfony 7.4 LTS

Como parte das atualizações da plataforma Adobe Commerce 2.4.9, todas as dependências do Symfony foram atualizadas para as versões mais recentes do Symfony LTS 7.4. Todas as classes personalizadas que estendem as classes principais do Symfony atualizaram as declarações de tipo e assinaturas de método alinhadas com os requisitos mais recentes do Symfony, evitando problemas de compatibilidade e garantindo uma transição suave para os componentes da estrutura atualizados.

_AC-15170 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c127d10b)_

#### Desativar dependência PHPUnit atualizada para a versão 3

A dependência `allure-framework/allure-phpunit` foi atualizada para a versão principal 3, que adiciona suporte para PHP 8.4 e PHP 8.5 e moderniza a pilha de relatórios de teste baseada em Allure. A dependência nativa anteriormente exigida pelas versões mais antigas do Allure PHPUnit foi removida, simplificando a configuração e a manutenção.

_AC-14548 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Relatórios do New Relic atualizados para a API do NerdGraph

O módulo de relatórios do New Relic foi atualizado para oferecer suporte à API de rastreamento de alterações NerdGraph (GraphQL) do New Relic, preservando totalmente a integração do marcador de implantação REST v2 existente. A alteração oferece metadados de implantação mais avançados, suporte a endpoint regional (EUA e UE) e capacidade de configuração por meio das configurações de administrador, sem romper as configurações existentes.

_AC-15461_

#### Atualizações da biblioteca JavaScript

- **Chart.js atualizado para a versão 4.5.0**

  Atualização da biblioteca de gráficos JavaScript Chart.js para a versão 4.5.0 para melhorar o desempenho de renderização do gráfico, aprimorar os recursos visuais e corrigir vulnerabilidades de segurança no painel de administração e nos módulos de relatórios.

  _AC-14304, AC-15133 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/768b4442), [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/657f983e)_

- **Biblioteca de carregamento de arquivo de uppy atualizada para a versão 4.13.4**

  Atualização da biblioteca de upload de arquivo Uppy para a versão 4.13.4 para aprimorar os recursos de upload de arquivo, melhorar a experiência do usuário e corrigir vulnerabilidades de segurança no manuseio de arquivos na interface do administrador do Adobe Commerce e em componentes de front-end.

  _AC-14307 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/eb491c05)_

- Biblioteca **jQuery Validate atualizada para a versão 1.21.0**

  Atualização da biblioteca jQuery Validate para a versão 1.21.0 para aprimorar os recursos de validação de formulários, melhorar a experiência do usuário e garantir a compatibilidade moderna do navegador em todos os Adobe Commerce Forms nas interfaces de administrador e de front-end.

  _AC-14403 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- Biblioteca de interface do usuário do **jQuery atualizada para a versão 1.14.1**

  A biblioteca da interface do usuário jQuery foi atualizada para a versão 1.14.1 para aprimorar os widgets da interface do usuário, melhorar a acessibilidade e garantir a compatibilidade moderna do navegador em todos os componentes de administração e interface de front-end do Adobe Commerce.

  _AC-14417 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/77c589a6)_

- Pré-processador CSS **Less.js atualizado para a versão 4.2.2**

  Atualização do pré-processador de CSS Less.js para a versão 4.2.2 para aprimorar o desempenho da compilação de CSS, melhorar o suporte à sintaxe e modernizar o processo de criação de tema em todos os temas de front-end e de administrador do Adobe Commerce.

  _AC-14418 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Biblioteca Moment Timezone atualizada para a versão 0.5.43**

  Atualização da biblioteca Moment Timezone (`moment-timezone-with-data.js`) para a versão 0.5.43 para aprimorar os recursos de manipulação de fuso horário, atualizar os dados de fuso horário com as alterações mais recentes do Banco de Dados de Fuso Horário IANA e melhorar a precisão do processamento de data e hora em todas as operações internacionais e de vários fusos horários da Adobe Commerce.

  _AC-14419 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Biblioteca de utilitários Underscore.js atualizada para a versão 1.13.7**

  Atualização da biblioteca de utilitários Underscore.js para a versão 1.13.7 para aprimorar os recursos de programação funcional do JavaScript, melhorar o desempenho da manipulação de dados e garantir a compatibilidade moderna do navegador em todos os componentes de front-end e interface de administrador do Adobe Commerce.

  _AC-14420 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

### Segurança

#### Validação de CAPTCHA agora imposta para APIs REST e GraphQL

Quando CAPTCHA (ou reCAPTCHA) é ativado para o formulário Criar conta, a mesma validação CAPTCHA agora é imposta para a criação de contas de clientes por meio de REST e APIs do GraphQL.

_AC-16245_

#### Desempenho de solicitação assíncrona/em massa aprimorado

Essa correção aborda a degradação de desempenho em pontos de extremidade de API da Web assíncronos em massa introduzidos após o patch de segurança APSB25-08, restaurando os tempos de execução esperados.

_AC-14078 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Configuração simplificada da autenticação de dois fatores

Os usuários administradores agora precisam configurar apenas um dos provedores 2FA habilitados do comerciante (por exemplo, Google Authenticator ou U2F) para acessar o painel Administrador. Provedores ativados adicionais podem ser configurados posteriormente, conforme necessário. Anteriormente, quando vários provedores 2FA eram ativados, cada usuário administrador precisava configurar todos eles antes de poder fazer logon, criando atrito para usuários que não tinham acesso a todos os provedores.

_AC-8253 - [Contribuição de código do GitHub](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

### Envio

#### Migrar integração do USPS para APIs RESTful USPS

Para estar em conformidade com a retirada anunciada das APIs herdadas de ferramentas da Web pelo USPS, a Adobe Commerce migrou sua integração do USPS para as novas APIs RESTful do USPS.

Principais melhorias:

- Suporte à API dupla: os usuários administradores agora podem escolher entre a API herdada de Ferramentas da Web e a nova API RESTful USPS por meio das configurações.
- Atualização de autenticação: usa o OAuth 2.0 para acesso seguro à API.
- Formato de dados aprimorado: usa JSON em vez de XML para uma comunicação mais limpa e eficiente.
- Novos campos de administrador:
   - URL REST do gateway (com base no modo: Desenvolvimento ou Ativo)
   - ID do cliente e segredo
   - Tipo de conta, Número da conta
   - CRID, MID, Código de identificação do correio
   - AES/ITN para remessas internacionais
   - Métodos de envio permitidos específicos para REST

Essa migração garante que a Adobe Commerce permaneça em conformidade com os padrões USPS, melhora a confiabilidade do sistema e garante integrações de envio que não se tornarão obsoletas para os comerciantes.

_AC-13257_

#### Migrar integração DHL para APIs RESTful MyDHL

A integração de envio DHL integrada agora suporta APIs MyDHL RESTful, preservando a compatibilidade com a API DHL Express XML herdada. Os comerciantes podem escolher qual API DHL usar no Admin, beneficiando-se dos recursos REST modernos sem romper as configurações existentes baseadas em XML.

_AC-13258_
