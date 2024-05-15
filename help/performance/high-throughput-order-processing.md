---
title: Práticas recomendadas de desempenho de check-out
description: Saiba como otimizar o desempenho das experiências de check-out no site do Adobe Commerce.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Práticas recomendadas de desempenho de check-out

A variável [check-out](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) no Adobe Commerce é um aspecto crítico da experiência da loja. Depende do modelo integrado [carrinho](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) e [check-out](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) recursos.

O desempenho é fundamental para manter uma boa experiência do usuário. Revise o [resumo do benchmark de desempenho](../implementation-playbook/infrastructure/performance/benchmarks.md) para saber mais sobre as expectativas de desempenho. Você pode otimizar o desempenho da finalização de compra configurando as seguintes opções para **processamento de pedido com alto rendimento**:

- [AsyncOrder](#asynchronous-order-placement)—Processar pedidos de forma assíncrona usando uma fila.
- [Cálculo do Total Diferido](#deferred-total-calculation)—Adiar cálculos para totais de pedido até o início do check-out.
- [Verificação de inventário na carga do carrinho](#disable-inventory-check)—Opte por ignorar a validação de inventário dos itens do carrinho.
- [Balanceamento de carga](#load-balancing)—Habilita conexões secundárias para o banco de dados MySQL e a instância Redis.

As opções de configuração Ordem assíncrona, Cálculo de total adiado e Verificação de inventário no carregamento do carrinho funcionam independentemente. Você pode usar todos os três recursos simultaneamente ou habilitar e desabilitar os recursos em qualquer combinação.

>[!NOTE]
>
>Não use o código PHP personalizado para personalizar o carrinho incorporado e os recursos de check-out. Além de possíveis problemas de desempenho, o uso do código PHP personalizado pode resultar em atualizações complexas e desafios de manutenção. Esses problemas aumentam o custo total de propriedade. Se a personalização do carrinho e do checkout baseada em PHP for inevitável, use [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)somente extensões aprovadas pelo. Todas as extensões do marketplace estão sujeitas a [análise extensiva](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) para verificar se eles atendem aos padrões de codificação e às práticas recomendadas da Adobe Commerce.

## Posicionamento assíncrono de pedidos

A variável _Ordem assíncrona_ permite a colocação assíncrona de pedidos, o que marca o pedido como `received`O coloca o pedido em uma fila e processa os pedidos da fila em uma base de primeiro a entrar, primeiro a sair. AsyncOrder é **desabilitado** por padrão.

Por exemplo, um cliente adiciona um produto ao carrinho de compras e seleciona **[!UICONTROL Proceed to Checkout]**. Eles preenchem o **[!UICONTROL Shipping Address]** formulário, selecione sua preferência **[!UICONTROL Shipping Method]**, selecione um método de pagamento e faça o pedido. O carrinho de compras está desmarcado, a ordem é marcada como **[!UICONTROL Received]**, mas a quantidade do Produto ainda não foi ajustada, nem um email de vendas foi enviado ao cliente. O pedido é recebido, mas os detalhes do pedido ainda não estão disponíveis porque o pedido não foi totalmente processado. Ele permanece na fila até que o `placeOrderProcess` O consumidor começa, verifica a ordem com o [verificação de inventário](#disable-inventory-check) (ativado por padrão) e atualiza a ordem da seguinte maneira:

- **Produto disponível**—o status do pedido muda para _Pending_, a quantidade do produto é ajustada, um email com detalhes do pedido é enviado ao cliente e os detalhes do pedido bem-sucedido ficam disponíveis para visualização na **Pedidos e Devoluções** com opções acionáveis, como reordenar.
- **Produto sem estoque ou com pouca oferta**—o status do pedido muda para _Rejeitado_, a quantidade do Produto não é ajustada, um email com detalhes do pedido sobre o problema é enviado ao cliente e os detalhes do pedido rejeitado ficam disponíveis no **Pedidos e Devoluções** sem opções acionáveis.

Use a interface de linha de comando para habilitar esses recursos ou edite o `app/etc/env.php` de acordo com os arquivos README correspondentes definidos no [_Guia de referência de módulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Para habilitar AsyncOrder**:

Você pode habilitar a AsyncOrder usando a interface de linha de comando:

```bash
bin/magento setup:config:set --checkout-async 1
```

A variável `set` O comando grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Consulte [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) no _Guia de referência de módulo_.

**Para desativar AsyncOrder**:

>[!WARNING]
>
>Antes de desabilitar o módulo AsyncOrder, você deve verificar se _all_ os processos de pedido assíncrono estão concluídos.

Você pode desativar a AsyncOrder usando a interface de linha de comando:

```bash
bin/magento setup:config:set --checkout-async 0
```

A variável `set` O comando grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilidade com AsyncOrder

O AsyncOrder oferece suporte a um conjunto limitado de recursos do Adobe Commerce.

| Categoria | Recurso suportado |
|------------------|--------------------------------------------------------------------------|
| Tipos de check-out | Check-out do OnePage<br>Check-out padrão<br>Cotação Negociável B2B |
| Métodos de pagamento | Cheque/Ordem de pagamento<br>Dinheiro na entrega<br>Braintree<br>PayPal PayFlow Pro |
| Métodos de envio | Todos os métodos de envio são compatíveis. |

Os seguintes recursos são **não** suportado pelo AsyncOrder, mas continua a funcionar de forma síncrona:

- Métodos de pagamento não incluídos na lista de recursos compatíveis
- Check-out de vários endereços
- Criação do pedido do administrador

#### Suporte à API da Web

Quando o módulo AsyncOrder está habilitado, os seguintes endpoints REST e mutações GraphQL são executados de forma assíncrona:

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>O GraphQL não oferece suporte a pedidos de cotação negociáveis de forma assíncrona.

#### Excluindo métodos de pagamento

Os desenvolvedores podem excluir explicitamente determinados métodos de pagamento do posicionamento assíncrono do pedido adicionando-os ao `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` matriz. Os pedidos que usam métodos de pagamento excluídos são processados de forma síncrona.

### Ordem Assíncrona de Cotação Negociável

A variável _Ordem Assíncrona de Cotação Negociável_ O módulo B2B permite salvar itens de pedido de forma assíncrona para o `NegotiableQuote` funcionalidade. Você deve ter AsyncOrder e NegotiableQuote ativadas.

## Cálculo do Total Diferido

A variável _Cálculo do Total Diferido_ O módulo otimiza o processo de check-out adiando o cálculo total até que ele seja solicitado para o carrinho de compras ou durante as etapas finais de check-out. Quando ativado, somente o subtotal é calculado conforme um cliente adiciona produtos ao carrinho de compras.

O Cálculo Total Diferido é **desabilitado** por padrão. Use a interface de linha de comando para habilitar esses recursos ou edite o `app/etc/env.php` de acordo com os arquivos README correspondentes definidos no [_Guia de referência de módulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Para habilitar DeferredTotalCalculation**:

Você pode habilitar DeferredTotalCalculation usando a interface de linha de comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

A variável `set` O comando grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Para desativar o DeferredTotalCalculation**:

Você pode desabilitar DeferredTotalCalculation usando a interface de linha de comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

A variável `set` O comando grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Consulte [CálculoTotalDiferido](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) no _Guia de referência de módulo_.

### Imposto Fixo do Produto

Quando o Cálculo Total Diferido está habilitado, o Imposto Fixo do Produto (FPT) não é incluído no preço do produto e no subtotal do carrinho do minicarrinho depois de adicionar o produto ao carrinho de compras. O cálculo do FPT é adiado ao adicionar um produto ao minicarrinho. O FPT é exibido corretamente no carrinho de compras após prosseguir para a finalização.

## Desabilitar verificação de estoque

A variável _Ativar inventário ao carregar o carrinho_ a configuração global determina se deve ser executada uma verificação de inventário ao carregar um produto no carrinho. Desativar o processo de verificação de inventário melhora o desempenho de todas as etapas de check-out, principalmente ao lidar com produtos em massa no carrinho.

Quando desativada, a verificação de inventário não ocorre ao adicionar um produto ao carrinho. Se essa verificação de inventário for ignorada, alguns cenários sem estoque poderão gerar outros tipos de erros. Uma verificação de inventário _sempre_ ocorre na etapa de colocação do pedido, mesmo quando desativado.

**Habilitar Verificação De Inventário Na Carga Do Carrinho** está ativado (definido como Sim) por padrão. Para desativar a verificação de inventário ao carregar o carrinho, defina **[!UICONTROL Enable Inventory Check On Cart Load]** para `No` na interface do usuário do administrador **Lojas** > **Configuração** > **Catálogo** > **Inventário** > **Opções de estoque** seção. Consulte [Configurar opções globais](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) e [Inventário do catálogo](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) no _Guia do usuário_.

## Balanceamento de carga

Você pode ajudar a balancear a carga em diferentes nós, habilitando conexões secundárias para o banco de dados MySQL e a instância Redis.

O Adobe Commerce pode ler vários bancos de dados ou instâncias Redis de forma assíncrona. Se estiver usando o Commerce na infraestrutura em nuvem, você poderá configurar as conexões secundárias editando o [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) e [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) valores no `.magento.env.yaml` arquivo. Somente um nó precisa lidar com tráfego de leitura-gravação, portanto, definir as variáveis como `true` resulta na criação de uma conexão secundária para tráfego somente leitura. Defina os valores como `false` para remover qualquer matriz de conexão somente leitura existente do `env.php` arquivo.

Exemplo de `.magento.env.yaml` arquivo:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
