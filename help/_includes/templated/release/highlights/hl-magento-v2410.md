---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%
---
# Destaques do Magento Open Source (v2.4.10)

## Destaques na v2.4.10-alpha1

Os destaques a seguir se aplicam à versão 2.4.10-alpha1 do Magento Open Source.

### Braintree

#### Fastlane

Adição do suporte Fastlane by PayPal para uma experiência de finalização de compra de convidado mais rápida e segura.
Os clientes podem optar por salvar os detalhes de pagamento e envio para compras futuras mais rápidas.
Os clientes que retornam ao Fastlane podem se autenticar usando um código único e recuperar as informações salvas.
Os clientes também podem adicionar ou alterar seus cartões salvos e endereços de envio durante o check-out.
O estilo e as opções de configuração do Fastlane também são compatíveis.

_PACOTE-3521_

#### Braintree Insights

Introdução do Braintree Insights para fornecer aos comerciantes relatórios de desempenho de pagamento centralizado na administração da Magento.
Fornece visibilidade sobre os dados de transação, liquidação, recusa, rejeição de gateway e método de pagamento.
Suporta filtragem por site, intervalo de datas e intervalos diários, semanais ou mensais.
Permite que os comerciantes importem até 13 meses de dados históricos de transações para relatórios.
Inclui retenção de dados e limpeza automatizada para manter até três anos de dados de transações.

_PACOTE-3522_

#### Swish - Método de pagamento local

Introdução do Swish como um novo Método de pagamento local sueco na extensão do Braintree Magento.
O Swish está disponível quando as configurações obrigatórias de comerciante, país, moeda e pagamento da Suécia são atendidas.
Os clientes com um endereço de entrega ou faturamento sueco podem concluir os pagamentos usando o Swish durante o checkout.
Adição de suporte para fluxos de pagamento do Swish bem-sucedidos, cancelados e com falha, com respostas de check-out apropriadas.
O Swish é exibido somente quando todas as condições de configuração necessárias são atendidas.

_PACOTE-3523_

#### Versão atualizada para v4.9.0

Atualização do módulo Braintree da v4.8.0 para v4.9.0.
A atualização inclui as alterações e as melhorias mais recentes do módulo Braintree.
Verificado se o processamento de pagamento e finalização do Braintree continua funcionando como esperado após a atualização.
Os fluxos existentes de finalização de compra do cliente e criação de pedido permanecem funcionais com o módulo atualizado.
Um teste básico de regressão foi realizado para garantir que nenhum problema fosse introduzido pela atualização

_PACOTE-3530_

### Estrutura

#### Atualizar dependência de NPM: underscore.js (1.13.7 → 1.13.8)

Atualização do underscore.js de 1.13.7 para 1.13.8 para incluir as correções de upstream e as melhorias de estabilidade mais recentes.

_AC-17486 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Dependência de NPM de atualização: imagemin-svgo (9.0.0 → 12.0.0)

Atualização do imagemin-svgo de 9.0.0 para 12.0.0 para incluir as correções upstream mais recentes, atualizações de segurança e melhorias de otimização da SVG.

_AC-17657 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Atualizar dependência de NPM: eslint-formatter-junit (8.40.0 → 9.0.1)

Atualização de eslint-formatter-junit de 8.40.0 para 9.0.1 para incluir as correções de upstream mais recentes e melhorias de compatibilidade para relatórios ESLint.

_AC-17659 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Dependência de NPM de upgrade: glob (11.0.0 → 13.0.0)

Atualização do glob de 11.0.0 para 13.0.0 para incluir as correções upstream mais recentes, melhorias de desempenho e aprimoramentos de compatibilidade.

_AC-17660 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Fazer upgrade da dependência de NPM: grunt-eslint (25.0.0 → 26.0.0)

Atualização do grunt-eslint de 25.0.0 para 26.0.0 para incluir as correções de upstream e as melhorias de compatibilidade mais recentes.

_AC-17661 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Dependência de NPM de upgrade: servidor estático (1.16.2 → 2.2.1)

Atualização do server-static de 1.16.2 para 2.2.1 para incluir as correções de upstream, atualizações de segurança e melhorias de compatibilidade mais recentes.

_AC-17662 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Atualizar as dependências de NPM mais recentes para Grunt e Less

Atualização do Grunt e Less para as versões mais recentes compatíveis, melhorando a estabilidade e a compatibilidade da build de front-end.

_AC-17663 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Atualize as dependências de substituição de NPM para as versões mais recentes compatíveis

Atualização de várias dependências de substituição de NPM para as versões mais recentes compatíveis, melhorando a segurança, a estabilidade da build e a compatibilidade.

_AC-17664 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

### Outro

#### Atualizar predis/predis de 2.x para 3.x

O predis/predis da biblioteca cliente Redis foi atualizado da versão 2.x para a 3.x. Essa atualização de versão principal se alinha aos mais recentes padrões de dependência, melhora a compatibilidade e garante a capacidade de manutenção a longo prazo.

_AC-17101 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Atualização do arquivo knockout.js da versão 3.5.1 para 3.5.3

Atualização da biblioteca knockout.js da versão 3.5.1 para 3.5.3. Esta atualização traz correções de erros upstream e melhorias de estabilidade para todos os componentes da interface do usuário usando vínculos Knockout na loja e no administrador.

_AC-17366 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/de7188da)_
