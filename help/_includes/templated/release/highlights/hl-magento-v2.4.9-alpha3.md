---
source-git-commit: 233ff6d5de2f4da3d477e70d066dd5cd46c771ee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.9-alpha3)

## Destaques na v2.4.9-alpha3

Os destaques a seguir se aplicam à versão 2.4.9-alpha3 do Magento Open Source.

### Braintree

#### Compartimentalização do Google Pay pela área da conta

No Magento 2.4.9-alpha3, os clientes agora podem fazer o vault dos seus cartões de pagamento Google por meio da área de conta quando o Google Pay Vault está ativado no Braintree. Os cartões com cofre são exibidos em métodos de pagamento armazenados, podem ser usados para compras futuras no check-out e podem ser excluídos pelo cliente. Isso estende o suporte à compartimentação além de Cartões e PayPal ao Google Pay.

_PACOTE-3459_

#### Vincular o pedido do Magento ao pedido do portal do Braintree

No Magento 2.4.9-alpha3, um Link do portal do Braintree agora é adicionado aos detalhes do pedido no Administrador do Magento. Clicar no link abre a transação relacionada no Braintree Portal (em uma nova guia ), usando a ID do comerciante e a ID da transação do pedido do Magento. Isso permite referência cruzada direta sem fazer logon em ambos os sistemas separadamente.

_PACOTE-3461_

#### Atualizador de conta em tempo real (RTAU)

O recurso Real Time Account Updater (RTAU) no Magento 2.4.9-alpha3 para Braintree garante que os detalhes de cartão com vault Visa, Mastercard e Discover sejam atualizados automaticamente quando os cartões expiram ou são substituídos. Isso minimiza pagamentos com falha, mantém o Magento Vault atualizado e ignora tipos não suportados (pré-pagos, Apple Pay, Google Pay) sem erros.

_PACOTE-3462_

#### Suporte de tipo de cartão ELO para Pagamentos com Cartão Braintree

No Magento 2.4.9-alpha3, o suporte para o tipo de cartão ELO foi adicionado ao Braintree Payments. Agora, os administradores podem ativar o ELO na configuração do cartão de crédito e os clientes podem fazer pedidos com êxito usando cartões ELO na finalização, garantindo transações ininterruptas por meio do Braintree.

_PACOTE-3464_

### Estrutura

#### Migração do RabbitMQ para o Apache AtiveMQ

_AC-14558_

#### Atualizar a dependência do chart.js para a versão mais recente

A dependência do chart.js foi atualizada para a versão mais recente 4.5.0

_AC-15133 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Migração do Laminas MVC

O Adobe Commerce introduziu uma implementação nativa do MVC, substituindo o Laminas MVC legado, para garantir compatibilidade e estabilidade a longo prazo além do PHP 8.5. Essa alteração fortalece o desempenho, reduz as dependências externas e fornece uma base mais pronta para o futuro do Commerce

_AC-15160_
