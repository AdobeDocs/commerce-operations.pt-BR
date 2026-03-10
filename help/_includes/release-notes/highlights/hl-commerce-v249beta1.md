---
source-git-commit: fd421e8c2455a2b45d3f3cc93573d2a609e4936d
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 0%

---
# Destaques do Adobe Commerce (v2.4.9-beta1)

## Destaques na v2.4.9-beta1

Os destaques a seguir se aplicam à versão 2.4.9-beta1 do Adobe Commerce.

### APIs

#### Controle de herança da galeria de produtos da API REST no nível de exibição da loja

Atualizar um produto por meio da API REST em um escopo de armazenamento não faz mais com que imagens e vídeos de produtos herdem alterações do escopo global quando `media_gallery_entries` é omitido da carga ou definido como `NULL`. Agora também é possível restaurar a herança do escopo de imagens e vídeos do produto por meio da API REST, definindo o campo correspondente como `NULL`.

_ACP2E-4358 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Interface do administrador

#### Menu de ações da grade de regras de preço do catálogo

A grade Regras de preço de catálogo no Commerce Admin agora inclui um menu Ações, permitindo que os comerciantes ativem, desativem ou excluam várias regras de preço de catálogo de uma só vez. Isso alinha o gerenciamento de regras de preços de catálogo com as ações em massa disponíveis para as Regras de preço do carrinho, reduzindo significativamente o tempo necessário para gerenciar grandes conjuntos de regras.

_AC-13916_

#### Visualização do modo de exibição móvel para preparo de conteúdo

O recurso de visualização de preparo no Admin agora permite que as visualizações do dispositivo móvel simuladas em navegadores sejam renderizadas com precisão, fornecendo uma representação visual de como uma atualização de preparo será exibida em um dispositivo móvel.

_ACP2E-3397 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### Check-out expresso

- **Ofertas promocionais na folha de pagamento expressa do Google Pay**

  A Folha de Pagamento do Google Pay Express agora oferece suporte a códigos promocionais e de ofertas. Os compradores podem aplicar, visualizar e remover promoções de carrinho do Commerce diretamente na folha de pagamento do Google, garantindo que os clientes de check-out expresso recebam os mesmos descontos e incentivos dos fluxos de check-out padrão.

  _PACOTE-3476_

- **Ofertas promocionais na folha de pagamento expressa do Apple Pay**

  A Folha de Pagamento do Apple Pay Express agora oferece suporte a códigos promocionais e de ofertas. Os compradores podem aplicar um cupom diretamente na folha de pagamento do Apple, para que os usuários do checkout expresso se beneficiem dos mesmos descontos e campanhas que os fluxos de check-out padrão.

  _PACOTE-3477_

- **Apple Pay on Chrome e Firefox**

  O Apple Pay agora pode ser usado no Chrome e no Firefox, não apenas no Safari. Quando o Apple Pay Express está ativado, os botões Apple Pay estão disponíveis nos locais de vitrine suportados e os clientes concluem o pagamento digitalizando um código com sua iPhone.

  _PACOTE-3478_

- **Retorno de chamada de remessa do lado do servidor para PayPal Express**

  A chamada de retorno do PayPal Express foi movida do lado do cliente para o lado do servidor. Isso fornece métodos de envio dinâmicos, cálculos de custo em tempo real e detalhes precisos no nível do carrinho diretamente no modal do PayPal, melhorando a confiabilidade e estabelecendo a base para recursos futuros, como suporte ao Módulo de Contato, fluxos de troca de aplicativo e Venmo Express.

  _PACOTE-3479_

- **Módulo de Contato do PayPal para check-out expresso do comerciante dos EUA**

  Um novo Módulo de Contato do PayPal é introduzido para comerciantes dos EUA. Quando ativado, os compradores que usam o PayPal Express podem visualizar e atualizar o endereço de email e o número de telefone compartilhados com o comerciante diretamente dentro do modal do PayPal durante os fluxos expresso (PDP, minicarrinho, carrinho, checkout express). Os detalhes de contato escolhidos são armazenados no pedido do Commerce.

  _PACOTE-3480_

#### Métodos de pagamento

- **Suporte de tipo de cartão ELO para pagamentos Braintree**

  Adição do suporte para o tipo de cartão ELO ao Braintree Payments. Agora, os administradores podem ativar o ELO na configuração do cartão de crédito e os clientes podem fazer pedidos com êxito usando cartões ELO na finalização, garantindo transações ininterruptas por meio do Braintree.

  _PACOTE-3464_

- **Método de pagamento local em BLOCO para compradores poloneses**

  BLIK foi adicionado como um novo método de pagamento local para compradores poloneses. Isso permite pagamentos SEGUROS BULK com base em bancos dentro do fluxo existente de Métodos de Pagamento Local (LPM) da Braintree, melhorando a conveniência do checkout e a conversão para os clientes na Polônia.

  _PACOTE-3481_

- **Pagar mediante Fatura — novo método de pagamento BNPL para a Alemanha**

  Adicionado um novo método de pagamento local, Pagamento mediante NFF para compradores alemães. Pay upon Invoice é uma opção Buy Now, Pay Later (BNPL) possibilitada pelo PayPal e Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) que permite aos clientes receber mercadorias primeiro e pagar a fatura em 30 dias, sem precisar de uma conta do PayPal. Como não se trata de um pagamento imediato, a finalização do pedido é impulsionada por um webhook do lado do servidor do PayPal.

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

#### Suporte ao OpenSearch 3.x

O Adobe Commerce 2.4.9-beta1 é totalmente compatível com o OpenSearch 3.x. Essa atualização permite que os comerciantes se beneficiem de melhor desempenho, segurança e suporte a longo prazo, mantendo a compatibilidade com versões anteriores do OpenSearch 2.x.

_AC-11846_

#### Suporte completo ao Valkey 8.x

O Adobe Commerce 2.4.9-beta1 adiciona suporte abrangente para o Valkey 8.x como um back-end de cache compatível com o Redis, incluindo paridade completa de comandos CLI com o Redis. As opções de configuração de Administração e Nuvem foram atualizadas para uma configuração perfeita do Valkey. Esse suporte é impulsionado pelo fim do suporte e alterações de licenciamento do Redis 7.2, oferecendo aos comerciantes uma alternativa confiável e totalmente compatível com o Redis nas linhas de versão 2.4.5 a 2.4.9-beta1 da Commerce.

_AC-14103, AC-14604_

#### O suporte ao Apache AtiveMQ Artemis substitui o RabbitMQ

Adição de suporte para o Apache AtiveMQ Artemis como uma alternativa estratégica ao RabbitMQ, impulsionada pelos riscos de fim de suporte associados ao RabbitMQ 4. O AtiveMQ Artemis agora é totalmente compatível com as linhas de versão 2.4.6 a 2.4.9-beta1 do Commerce, incluindo a Adobe Commerce Cloud com AWS AtiveMQ para implantações nativas em nuvem e oferece suporte à configuração STOMP para consumidores e editores de fila. As instalações existentes do RabbitMQ 4 permanecem compatíveis para os comerciantes que preferem continuar usando seu serviço atual de fila de mensagens.

_AC-14558_

### PHP e Composer

#### Compatibilidade com PHP 8.5

A partir do Adobe Commerce 2.4.9-beta1, a plataforma é totalmente compatível com o PHP 8.5, mantendo o suporte para o PHP 8.4 e permitindo o PHP 8.3 para cenários somente de atualização. Este trabalho moderniza o código principal, dependências e ferramentas para que os comerciantes possam mudar com segurança para versões PHP mais recentes antes do fim do suporte ao PHP 8.4, mantendo a conformidade com o PCI e a integridade da plataforma a longo prazo.

_AC-15615_

#### Suporte ao PHP 8.2 removido

A partir do Adobe Commerce 2.4.9-beta1, o PHP 8.2 não é mais suportado. A plataforma agora tem como alvo o PHP 8.3 e posterior, com código principal, dependências e ferramentas atualizadas para rodar de forma limpa e confiável no PHP 8.4 e 8.5.

_AC-15758_

#### Compatibilidade do Composer 2.9 verificada

O Adobe Commerce 2.4.9-beta1 é totalmente compatível com o Composer 2.x, incluindo o Composer 2.9. Esse alinhamento preserva a compatibilidade com versões anteriores e garante uma experiência estável de build e implantação para comerciantes e desenvolvedores que usam as versões mais recentes do Composer.

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

A partir do Adobe Commerce 2.4.9-beta1, o componente Zend_Cache obsoleto foi substituído pelo componente Symfony Cache. Esta atualização melhora o desempenho e a manutenção do cache, e garante compatibilidade a longo prazo com o PHP 8.x e futuras atualizações de plataforma. Os backends de cache e os comandos de gerenciamento de cache existentes permanecem totalmente compatíveis, sem alterações necessárias para as integrações atuais.

_AC-15823_

#### O editor do WYSIWYG migrou do TinyMCE para o HugeRTE

Devido ao fim do suporte para o TinyMCE 5 e 6 e às incompatibilidades de licenciamento com o TinyMCE 7, o editor do Adobe Commerce WYSIWYG foi migrado para o editor de código aberto [HugeRTE](https://hugerte.org/). Essa migração garante que o Adobe Commerce permaneça em conformidade com o licenciamento de código aberto, evita vulnerabilidades conhecidas do TinyMCE 6 e fornece uma experiência de edição moderna e compatível para comerciantes e desenvolvedores.

_AC-14568_

#### A implementação do MVC nativo substitui o MVC do Laminas

O Adobe Commerce introduziu uma implementação nativa do MVC, substituindo o Laminas MVC legado, para garantir compatibilidade e estabilidade a longo prazo além do PHP 8.5. Essa alteração fortalece o desempenho, reduz as dependências externas e fornece uma base mais pronta para o futuro para o Commerce.

_AC-15160_

#### Suporte oficial ao Symfony 7.4 LTS

Como parte das atualizações da plataforma Adobe Commerce 2.4.9-beta1, todas as dependências do Symfony foram atualizadas para as versões mais recentes do Symfony LTS 7.4. Todas as classes personalizadas que estendem as classes principais do Symfony atualizaram as declarações de tipo e assinaturas de método alinhadas com os requisitos mais recentes do Symfony, evitando problemas de compatibilidade e garantindo uma transição suave para os componentes da estrutura atualizados.

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

Os usuários administradores agora precisam configurar apenas um dos provedores 2FA habilitados do comerciante (por exemplo, Google Authenticator ou U2F) para acessar o painel Administrador. Provedores ativados adicionais podem ser configurados posteriormente, conforme necessário. Anteriormente, quando vários provedores 2FA eram ativados, cada usuário administrador precisava configurar todos os provedores ativados antes que pudesse fazer logon, criando atrito para usuários que não tinham acesso a todos os fatores.

_AC-8253 - [Contribuição de código do GitHub](https://github.com/magento/security-package/commit/71e7936b)_

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
