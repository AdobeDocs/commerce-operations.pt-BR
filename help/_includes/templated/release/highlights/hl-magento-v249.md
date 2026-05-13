---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Destaques do Magento Open Source (v2.4.9)

## Destaques na v2.4.9

Os destaques a seguir se aplicam à versão 2.4.9 do Magento Open Source.

### APIs

#### Adição de uma possibilidade de manter a herança da galeria de produtos na API REST ao atualizar um produto no nível de exibição da loja

A atualização de produto por meio da API REST em um escopo de armazenamento não faz mais com que imagens e vídeos de produto herdem alterações do escopo global se as entradas media_gallery_entries forem omitidas da carga ou definidas como NULL para evitar alterações na galeria de produtos nesse escopo. Além disso, agora é possível restaurar a herança do escopo de imagens e vídeos do produto por meio da API REST, definindo o campo correspondente como NULL.

_ACP2E-4358 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### Compartimentalização do Google Pay pela área da conta

No Adobe Commerce 2.4.9, os clientes agora podem fazer o Vault dos seus cartões de pagamento Google por meio da área de conta quando o Google Pay Vault está ativado no Braintree. Os cartões com cofre são exibidos em métodos de pagamento armazenados, podem ser usados para compras futuras no check-out e podem ser excluídos pelo cliente. Isso estende o suporte à compartimentação além de Cartões e PayPal ao Google Pay.

_PACOTE-3459_

#### Atualizador de conta em tempo real (RTAU)

O recurso Atualizador de conta em tempo real (RTAU) no Adobe Commerce 2.4.9 para Braintree garante que os detalhes de cartão Visa, Mastercard e Discover com cofre sejam atualizados automaticamente quando os cartões expiram ou são substituídos. Isso minimiza pagamentos com falha, mantém o Magento Vault atualizado e ignora tipos não suportados (pré-pagos, Apple Pay, Google Pay) sem erros.

_PACOTE-3462_

#### Suporte de tipo de cartão ELO para Pagamentos com Cartão Braintree

No Adobe Commerce 2.4.9, o suporte para o tipo de cartão ELO foi adicionado ao Braintree Payments. Agora, os administradores podem ativar o ELO na configuração do cartão de crédito e os clientes podem fazer pedidos com êxito usando cartões ELO na finalização, garantindo transações ininterruptas por meio do Braintree.

_PACOTE-3464_

#### Pagar mediante fatura

Para o Adobe Commerce 2.4.9 (extensão do Braintree), um novo método de pagamento local &quot;Pagar na fatura&quot; foi adicionado para compradores alemães. Pay upon Invoice é uma opção Buy Now, Pay Later (BNPL) possibilitada pelo PayPal + Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) que permite aos clientes receber bens primeiro e pagar a fatura em 30 dias, sem precisar de uma conta do PayPal. Como não se trata de um pagamento imediato, a finalização do pedido é impulsionada por um webhook do lado do servidor do PayPal.

_PACOTE-3475_

#### Adicionar ofertas à folha de pagamento do Google Pay Express

Para a extensão do Braintree no Adobe Commerce 2.4.9, a Folha de Pagamento do Google Pay Express agora é compatível com códigos promocionais/de oferta. Os compradores podem aplicar, visualizar e remover promoções de carrinho do Magento diretamente na folha de pagamento do Google, garantindo que os clientes de check-out expresso recebam os mesmos descontos e incentivos dos fluxos de check-out padrão.

_PACOTE-3476_

#### Adicionar ofertas à folha de pagamento do Apple Pay Express

Para a extensão do Braintree no Adobe Commerce 2.4.9, a Folha de Pagamento do Apple Pay Express agora é compatível com códigos promocionais/de oferta. Os compradores podem aplicar um cupom diretamente na folha de pagamento do Apple, para que os usuários do checkout expresso se beneficiem dos mesmos descontos e campanhas que os fluxos de check-out padrão.

_PACOTE-3477_

#### Pagar com o Apple Pagar no Chrome e no Firefox

Para a extensão do Braintree no Adobe Commerce 2.4.9, o Apple Pay agora pode ser usado no Chrome e no Firefox, não apenas no Safari. Quando o Apple Pay Express está ativado, os botões Apple Pay estão disponíveis nos locais de vitrine suportados e os clientes concluem o pagamento digitalizando um código com sua iPhone.

_PACOTE-3478_

#### Retorno de chamada de envio no lado do servidor

Para a extensão do Braintree no Adobe Commerce 2.4.9, a chamada de retorno do PayPal Express foi movida do lado do cliente para o lado do servidor. Isso fornece métodos de envio dinâmicos, cálculos de custo em tempo real e detalhes precisos no nível do carrinho diretamente no modal do PayPal, melhorando a confiabilidade e estabelecendo a base para recursos futuros, como suporte ao Módulo de Contato, fluxos de troca de aplicativo e Venmo Express.

_PACOTE-3479_

#### Módulo de Contato do PayPal

Para a extensão do Braintree no Adobe Commerce 2.4.9, um novo Módulo de Contato do PayPal é introduzido para comerciantes dos EUA. Quando ativado, os compradores que usam o PayPal Express podem visualizar e atualizar o endereço de email e o número de telefone compartilhados com o comerciante diretamente dentro do modal do PayPal durante os fluxos expresso (PDP, minicarrinho, carrinho, checkout express). Os detalhes de contato escolhidos são armazenados no pedido do Adobe Commerce.

_PACOTE-3480_

#### BLIK (Método de Pagamento Local)

Para a extensão do Braintree no Adobe Commerce 2.4.9, o BLIK foi adicionado como um novo método de pagamento local para compradores poloneses. Isso permite pagamentos SEGUROS BULK com base em bancos dentro do fluxo existente de Métodos de Pagamento Local (LPM) da Braintree, melhorando a conveniência do checkout e a conversão para os clientes na Polônia.

_PACOTE-3481_

#### Política da CSP de atualização da integração cardeal

Para a extensão do Braintree no Adobe Commerce 2.4.9, a Política de segurança de conteúdo (CSP) foi atualizada para oferecer suporte aos requisitos mais recentes de integração do Cardeal (3-D Secure). Isso garante que todos os scripts hospedados pelo Cardeal, iframes e recursos relacionados usados durante fluxos Seguros 3D sejam permitidos pelo CSP do navegador, evitando solicitações bloqueadas e experiências de desafio/verificação quebradas.

_PACOTE-3485_

### Estrutura

#### Atualização da biblioteca web-token/jwt-framework para a versão principal mais recente

Como parte do processo contínuo de revisão de segurança, avaliamos a versão principal mais recente da estrutura JWT para garantir a compatibilidade futura e manter padrões de segurança sólidos. Não há impacto sobre a funcionalidade existente nesta versão.

_AC-13209 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### [Parte 2] - Atualizar toda a biblioteca js e a dependência npm com a versão mais recente disponível

o suporte à versão do compositor era somente para a versão 2.2.x do compositor. Agora, o suporte também foi estendido para a versão 2.4.x.

_AC-13792 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/19844aa0)_

#### Substituir carlos-mg89/oauth pelas funções nativas do PHP

Substituição da biblioteca carlos-mg89/oauth de terceiros por funções OAuth nativas do PHP para melhorar a segurança, reduzir as dependências externas e melhorar a estabilidade da plataforma.

_AC-14075 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Atualizar as bibliotecas jquery/uppy e uppy para a versão mais recente

Atualização da biblioteca de upload de arquivo Uppy para a versão 4.13.4 para aprimorar os recursos de upload de arquivo, melhorar a experiência do usuário e corrigir vulnerabilidades de segurança no manuseio de arquivos na interface do administrador do Adobe Commerce e em componentes de front-end.

_AC-14307 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/eb491c05)_

#### Atualizar biblioteca jquery-validate para a versão mais recente

Atualização da biblioteca jQuery Validate para a versão 1.21.0 para aprimorar os recursos de validação de formulários, melhorar a experiência do usuário e garantir a compatibilidade moderna do navegador em todos os Adobe Commerce Forms nas interfaces de administrador e de front-end.

_AC-14403 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Atualize a biblioteca jquery-ui para a versão mais recente

A biblioteca da interface do usuário jQuery foi atualizada para a versão 1.14.1 para aprimorar os widgets da interface do usuário, melhorar a acessibilidade e garantir a compatibilidade moderna do navegador em todos os componentes de administração e interface de front-end do Adobe Commerce.

_AC-14417 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Atualizar a biblioteca less.js para a versão mais recente

Atualização do pré-processador de CSS Less.js para a versão 4.2.2 para aprimorar o desempenho da compilação de CSS, melhorar o suporte à sintaxe e modernizar o processo de criação de tema em todos os temas de front-end e de administrador do Adobe Commerce.

_AC-14418 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Atualize a biblioteca Moment-Timzone-with-data.js para a versão mais recente

Atualização da biblioteca Fuso horário de momento para a versão 0.5.43 para aprimorar os recursos de manipulação de fuso horário, atualizar os dados de fuso horário com as alterações mais recentes do banco de dados de fuso horário IANA e melhorar a precisão do processamento de data/hora em todas as operações internacionais e de vários fusos horários da Adobe Commerce.

_AC-14419 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Atualizar a biblioteca underscore.js para a versão mais recente

Atualização da biblioteca de utilitários Underscore.js para a versão 1.13.7 para aprimorar os recursos de programação funcional do JavaScript, melhorar o desempenho da manipulação de dados e garantir a compatibilidade moderna do navegador em todos os componentes de front-end e interface de administrador do Adobe Commerce.

_AC-14420 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Atualize a versão allure-framework/allure-phpunit para 3 e remova a dependência nativa em 2.4.9-alpha1

No Adobe Commerce 2.4.9, a dependência allure-framework/allure-phpunit foi atualizada para a versão principal 3, que adiciona suporte para PHP 8.4, PHP 8.5 e moderniza nossa pilha de relatórios de teste com base em Allure. A dependência nativa anteriormente exigida pelas versões mais antigas do Allure PHPUnit foi removida, onde aplicável, simplificando a configuração e a manutenção.

_AC-14548 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Atualizar a dependência do chart.js para a versão mais recente

A dependência do chart.js foi atualizada para a versão mais recente 4.5.0.

_AC-15133 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Adicionar suporte oficial para Symfony 7.4 LTS e PHP 8.5 no Adobe Commerce 2.4.9

Como parte das atualizações da plataforma Adobe Commerce 2.4.9, todas as dependências do Symfony usadas pelo pacote magento/composer foram atualizadas para as versões mais recentes do Symfony LTS 7.4. Isso alinha as ferramentas do Commerce Composer com a linha atual do Symfony LTS e remove as restrições de dependência anteriores relacionadas às versões mais antigas do Symfony. Além disso, todas as classes personalizadas que estendem as classes principais do Symfony atualizaram as declarações de tipo e assinaturas de método alinhadas aos requisitos mais recentes do Symfony antes de atualizar para o Adobe Commerce 2.4.9. Isso evitará problemas de compatibilidade e garantirá uma transição suave para os componentes da estrutura atualizados.

_AC-15170 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### Verifique se a mutação clearCart GraphQL está disponível no Open Source

Com o Adobe Commerce 2.4.9, a mutação clearCart GraphQL agora está disponível para todos os usuários do Open Source. Anteriormente, essa mutação só era acessível no Adobe Commerce, mas agora também faz parte da funcionalidade padrão do carrinho do GraphQL para Open Source.
A documentação da mutação foi atualizada para refletir sua disponibilidade no Open Source versão 2.4.9.
Consulte a [documentação de mutação do clearCart GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/).

_AC-16683 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9] Mesclando lógica de carrinho de convidado e de cliente usando Configuração de administrador

Uma nova opção de configuração de administrador foi introduzida para controlar como os carrinhos de convidado e de cliente são mesclados quando um comprador faz logon. Esse aprimoramento oferece flexibilidade para definir o comportamento de mesclagem de carrinhos que melhor se adapta às suas necessidades comerciais.

_LYNX-889_

#### [AC-2.4.9] Obtendo pedidos históricos com produtos indisponíveis

Os pedidos históricos agora mostram detalhes do produto, mesmo que agora estejam esgotados.

_LYNX-913_

#### [AC-2.4.9] [CE] Implementar ReCaptcha para mutações ausentes do GraphQL

A validação do ReCaptcha é adicionada para as mutações updateCustomer, updateCustomerV2 e contactUs.

_LYNX-941_

### Outro

#### O Captcha/reCAPTCHA não está funcionando para a API/GraphQL

No Adobe Commerce 2.4.9, quando CAPTCHA (ou reCAPTCHA) é ativado para o formulário Criar conta, a mesma validação CAPTCHA agora é imposta para a criação de contas de clientes por meio das APIs REST e GraphQL.

_AC-16245 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

#### ramificação braintree deve ser atualizada com suporte PHP 8.5

A extensão de pagamento do Braintree foi atualizada para suportar o último tempo de execução do PHP 8.5, mantendo a compatibilidade com o PHP 8.4.

_PACOTE-3493_

#### Adicionar operação de limpeza de lista de desejos

Adição de uma nova mutação clearWishlist para oferecer suporte a operações em massa, permitindo que todos os itens sejam removidos de uma lista de desejos em uma única ação.

_LYNX-790_

#### Introduzir mutação exchangeExternalCustomerToken

Introdução do novo GraphQL mutation exchangeExternalCustomerToken, que autentica os usuários por meio de um token de integração e retorna o token do cliente e os dados associados do cliente

_LYNX-815_

#### [AC] Introduzir consultas do GraphQL que retornam IDs de grupos, segmentos e regras de carrinho aplicadas

As consultas do GraphQL são expostas para recuperar a uid codificada do grupo de clientes, dos segmentos de clientes e das regras do carrinho aplicados.

_LYNX-867_

#### [AC-2.4.9] Introduzir campo OrderTotal.grand_total_excl_tax

Um novo campo, OrderTotal.grand_total_excl_tax, foi adicionado à resposta de pedido do GraphQL. Este campo fornece o total geral do pedido excluindo impostos, facilitando o acesso a totais com isenção de impostos diretamente da API.

Benefícios:

- Recupere facilmente o total geral, excluindo impostos, para qualquer pedido por meio do GraphQL.
- Simplifica a integração com sistemas externos que exigem totais de impostos exclusivos.
- Reduz a necessidade de cálculos personalizados no lado do cliente.

_LYNX-892_

### PCI, Segurança

#### Refatore o armazenamento de dados da SRI para ter mais eficiência no desempenho

O armazenamento de hash da SRI agora gera arquivos separados por área, tema e localidade, em vez de um único grande arquivo sri-hashes.json. Essa alteração garante que somente o arquivo de hash relevante seja carregado para cada página, melhorando o desempenho e reduzindo o uso da memória em lojas com vários temas ou localidades.

_AC-16113 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

### Segurança

#### Melhorar o desempenho de solicitações assíncronas/em massa

Correção da degradação de desempenho em pontos de extremidade da Web assíncronos em massa introduzidos após o patch de segurança APSB25-08, resultando em maior tempo de execução.

_AC-14078 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Exigir que apenas um provedor 2FA habilitado seja configurado por usuário

Os usuários administradores agora precisam configurar apenas um dos provedores 2FA habilitados do comerciante (por exemplo, Google Authenticator ou U2F) para acessar o painel Administrador. Provedores ativados adicionais podem ser configurados posteriormente, conforme necessário. Anteriormente, quando vários provedores 2FA eram ativados (por exemplo, Google Authenticator e U2F), cada usuário administrador era solicitado a configurar todos os provedores ativados antes que pudesse fazer logon. Isso criou atrito para usuários que não tinham acesso a todos os fatores (como uma chave de hardware para U2F).

_AC-8253 - [Contribuição de código do GitHub](https://github.com/magento/security-package/commit/71e7936b)_
