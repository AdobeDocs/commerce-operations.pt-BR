---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%
---
# Destaques do Adobe Commerce (v2.4.10)

## Destaques na v2.4.10-alpha1

Os destaques a seguir se aplicam à versão 2.4.10-alpha1 do Adobe Commerce.

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

#### Atualização de Componente de Plataforma [2.4.10-alpha1]

O Adobe Commerce 2.4.10-alpha1 inclui um conjunto de atualizações de dependência de plataforma, melhorias de compatibilidade, atualizações de biblioteca de front-end e correções de estabilidade. As seguintes alterações concluídas estão incluídas nesta versão:

- Predis: `predis/predis` atualizado de 2.x para 3.x, melhorando a compatibilidade com ambientes Redis e Valkey e mantendo o cliente Redis alinhado com as versões de dependência mais recentes com suporte.
- Instalador do Magento Composer: correção de um problema no qual o `magento-composer-installer` poderia sair silenciosamente sem concluir o processo de instalação, melhorando a confiabilidade das instalações baseadas no Composer.
- Knockout.js: o arquivo Knockout.js foi atualizado de 3.5.1 para 3.5.3, juntamente com as atualizações de validação e compatibilidade necessárias.
- Chart.js: Atualização do Chart.js de 4.5.0 para 4.5.1, incluindo as atualizações de validação e compatibilidade necessárias.
- Less.js: atualização do Less.js de 4.2.2 para 4.6.4, com atualizações de validação e compatibilidade associadas.
- Uppy: atualização do Uppy de 5.0.0 para 5.2.0, incluindo as alterações necessárias de validação e compatibilidade.
- Interface do usuário do jQuery: interface do usuário do jQuery atualizada de 1.14.1 para 1.14.2, com as atualizações de validação e compatibilidade associadas.
- Compatibilidade do PHP 8.5: resolveu um problema de descontinuação do PHP 8.5 relacionado ao `chr()`, garantindo que a função é fornecida com valores de bytes válidos e melhorando a compatibilidade com o PHP 8.5.
- Pesquisa no catálogo: correção de um problema em que a reindexação do `catalogsearch_fulltext` poderia ser interrompida durante o processamento, melhorando a confiabilidade da indexação da pesquisa no catálogo.
- js-cookie: js-cookie atualizado de 3.0.5 para 3.0.7 ou a versão compatível aplicável, abordando requisitos de dependência e compatibilidade.

_AC-17061_

#### Garantir compatibilidade de B2B 1.5.3-p1/1.5.4-alpha1 com 2.4.10-alpha1, 2.4.9-p1, 2.4.8-p6, 2.4.7-p11 e 2.4.6-p16

O B2B 1.5.4-alpha1 é compatível com as seguintes linhas de versão do Adobe Commerce: 2.4.9, 2.4.8, 2.4.7 e 2.4.6.

_AC-17100_

#### Atualizar e modernizar as dependências de NPM

Atualização das seguintes dependências npm para suas versões seguras mais recentes para solucionar vulnerabilidades de segurança conhecidas:

- sublinhado
- imagemin-svgo
- glob
- servidor estático
- grunt
- menos
- uglify-js
- marcado
- clean-css
- minimista
- trim-newlines
- terser
- css-select
- nth-check
- semver-regex
- http-cache-semantics
- js-yaml
- package-json

Essas atualizações de dependência reduzem as vulnerabilidades de segurança identificadas, mantendo a funcionalidade existente do aplicativo.

_AC-17372_

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

#### [B2B] Ordens de compra não convertidas automaticamente em ordem de venda com AtiveMQ

Correção de um problema em que os pedidos de compra feitos por meio da loja com aprovação automática habilitada não eram convertidos automaticamente em pedidos de venda ao usar o AtiveMQ e executar consumidores por meio do cron (bin/magento cron:run). Anteriormente, as mensagens eram adicionadas à fila do AtiveMQ, mas não eram processadas, a menos que o consumidor fosse iniciado manualmente via CLI. Com essa correção, o consumidor agora processa mensagens conforme esperado após a execução do CRON, garantindo uma conversão de pedido perfeita para comerciantes B2B que usam o AtiveMQ.

_AC-17679_

#### Otimização do cache L2 do Symfony e compatibilidade com versões anteriores do cache herdado

O Adobe Commerce 2.4.10 agora oferece suporte otimizado ao Symfony L2 Cache, mantendo a implementação existente do cache baseado no Zend como padrão.

Os comerciantes que desejam usar o Symfony Cache devem habilitá-lo explicitamente e atualizar a configuração de cache necessária específica para a implementação do Symfony L1/L2. Os comerciantes existentes que continuam usando o cache baseado em Zend não precisam fazer alterações na configuração.

Essa abordagem de cache duplo oferece aos comerciantes a flexibilidade para adotar o Symfony Cache com base em seus requisitos, garantindo, ao mesmo tempo, a compatibilidade com versões anteriores de configurações e implantações de cache.

_AC-17865_

### Outro

#### Gestão administrativa de sub-regiões de países (Estados e províncias)

Os comerciantes agora podem gerenciar sub-regiões do país (como estados e províncias) diretamente na interface do Administrador. Esse novo recurso permite que os comerciantes:

- Exibir, adicionar, editar, desativar ou remover regiões de qualquer país.
- Disponibilize novas regiões instantaneamente como opções suspensas no check-out, em formulários de endereço do cliente e durante a criação do pedido do administrador — não é necessária nenhuma alteração de código.
- Edite nomes de exibição de região (incluindo nomes localizados) e códigos ISO.
- Desative regiões referenciadas por ordens, endereços ou regras de imposto existentes (garantindo que os dados históricos permaneçam precisos), evitando a exclusão forçada dessas regiões.
- Todas as regiões predefinidas permanecem inalteradas e agora estão visíveis e podem ser gerenciadas na nova interface.

Esse recurso é totalmente compatível com versões anteriores e garante que o comportamento do endereço do cliente e da API permaneça consistente.

_AC-16192_

#### Atualizar predis/predis de 2.x para 3.x

O predis/predis da biblioteca cliente Redis foi atualizado da versão 2.x para a 3.x. Essa atualização de versão principal se alinha aos mais recentes padrões de dependência, melhora a compatibilidade e garante a capacidade de manutenção a longo prazo.

_AC-17101 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Atualização do arquivo knockout.js da versão 3.5.1 para 3.5.3

Atualização da biblioteca knockout.js da versão 3.5.1 para 3.5.3. Esta atualização traz correções de erros upstream e melhorias de estabilidade para todos os componentes da interface do usuário usando vínculos Knockout na loja e no administrador.

_AC-17366 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Atualização do verniz para a versão 9 para 2.4.10-alpha1

O Adobe Commerce 2.4.10 é compatível com a versão 9.0 do Varnish.

_AC-17972_
