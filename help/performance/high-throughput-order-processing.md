---
title: Processamento de Ordem de Alta Throughput
description: Otimize a experiência de posicionamento e check-out do pedido para sua implantação do Adobe Commerce ou Magento Open Source.
source-git-commit: c4c52baa9e04a4e935ccc29fcce2ac2745a454ee
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---


# Processamento de pedidos com alta taxa de transferência

Você pode otimizar a experiência de posicionamento do pedido e check-out configurando o seguinte conjunto de módulos para **processamento de pedidos de alta taxa de transferência**:

- [AsyncOrder](#asynchronous-order-placement)—Processa pedidos de forma assíncrona usando uma fila.
- [Cálculo Total Diferido](#deferred-total-calculation)—Oferece cálculos para totais de pedidos até o início do check-out.
- [Verificação de Inventário no Carregamento da Cotação](#disable-inventory-check)—Escolha ignorar a validação de inventário dos itens do carrinho.

Todos os recursos — AsyncOrder, Cálculo Total Diferido e Verificação de Inventário — funcionam de forma independente. Você pode usar todos os três recursos simultaneamente ou ativar e desativar recursos em qualquer combinação.

## Colocação assíncrona de pedido

O _Ordem assíncrona_ o módulo permite o posicionamento assíncrono do pedido, o que marca o pedido como `received`, coloca o pedido em uma fila e processa pedidos da fila na primeira saída. AsyncOrder é **desativado** por padrão.

Por exemplo, um cliente adiciona um produto ao carrinho e seleciona **[!UICONTROL Proceed to Checkout]**. Eles preenchem a **[!UICONTROL Shipping Address]** , selecione o formulário preferido **[!UICONTROL Shipping Method]**, selecione um método de pagamento e coloque a ordem. O carrinho de compras é limpo, o pedido é marcado como **[!UICONTROL Received]**, mas a quantidade do Produto ainda não foi ajustada, nem um email de venda é enviado ao cliente. O pedido é recebido, mas os detalhes do pedido ainda não estão disponíveis porque o pedido não foi totalmente processado. Permanece na fila até a `placeOrderProcess` O consumidor inicia, verifica o pedido com a variável [verificação de inventário](#disable-inventory-check) (ativado por padrão) e atualiza a ordem da seguinte maneira:

- **Produto disponível**—o status do pedido muda para _Pending_, a quantidade do produto é ajustada, um email com detalhes do pedido é enviado ao cliente e os detalhes do pedido bem-sucedido ficam disponíveis para visualização no **Pedidos e devoluções** lista com opções acionáveis, como reordenar.
- **Produto esgotado ou pouco fornecido**—o status do pedido muda para _Rejeitada_, a quantidade do produto não é ajustada, um email com detalhes do pedido sobre o problema é enviado ao cliente e os detalhes do pedido rejeitado ficam disponíveis na **Pedidos e devoluções** lista sem opções acionáveis.

Use a interface da linha de comando para ativar esses recursos ou edite o `app/etc/env.php` de acordo com os arquivos README correspondentes definidos no [_Guia de referência do módulo_][mrg].

**Para ativar o AsyncOrder**:

Você pode ativar o AsyncOrder usando a interface da linha de comando:

```bash
bin/magento setup:config:set --checkout-async 1
```

O `set` grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Consulte [AsyncOrder] no _Guia de referência do módulo_.

**Para desativar o AsyncOrder**:

>[!WARNING]
>
>Antes de desabilitar o módulo AsyncOrder , você deve verificar se _all_ os processos de pedido assíncronos estão concluídos.

Você pode desativar o AsyncOrder usando a interface da linha de comando:

```bash
bin/magento setup:config:set --checkout-async 0
```

O `set` grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilidade com AsyncOrder

AsyncOrder suporta um conjunto limitado de [!DNL Commerce] recursos.

| Categoria | Recurso suportado |
|---------------- | -----------------------|
| Tipos de check-out | Check-out do OnePage<br>Check-out padrão<br>Cotação Negociável B2B |
| Métodos de pagamento | Pedido de cheque/dinheiro<br>Dinheiro na entrega<br>Braintree<br>PayPal PayFlow Pro |
| Métodos de envio | Todos os métodos de envio são suportados. |

Os seguintes recursos são **not** suportado pelo AsyncOrder, mas continua a funcionar de forma síncrona:

- Métodos de pagamento não incluídos na lista de recursos suportados
- Check-out de vários endereços
- Criação da ordem de administração

#### Suporte à API da Web

Quando o módulo AsyncOrder é ativado, os seguintes pontos de extremidade REST e mutações GraphQL são executados de forma assíncrona:

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL não oferece suporte para colocar pedidos de cotação negociáveis de forma assíncrona.

#### Excluir métodos de pagamento

Os desenvolvedores podem excluir explicitamente determinados métodos de pagamento do posicionamento de pedidos assíncronos, adicionando-os ao `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` matriz. As ordens que usam métodos de pagamento excluídos são processadas de forma síncrona.

### Ordem Assíncrona da Cotação Negociável

O _Ordem Assíncrona da Cotação Negociável_ O módulo B2B permite que você salve itens de ordem de forma assíncrona para o `NegotiableQuote` funcionalidade. Você deve ter AsyncOrder e NegotiableQuote ativadas.

## Cálculo Total Diferido

O _Cálculo Total Diferido_ O módulo otimiza o processo de check-out adiando o cálculo total até que seja solicitado para o carrinho de compras ou durante as etapas de check-out final. Quando ativado, somente o subtotal é calculado como um cliente que adiciona produtos ao carrinho de compras.

DeferredTotalCalculation é **desativado** por padrão. Use a interface da linha de comando para ativar esses recursos ou edite o `app/etc/env.php` de acordo com os arquivos README correspondentes definidos no [_Guia de referência do módulo_][mrg].

**Para ativar DeferredTotalCalculation**:

Você pode ativar DeferredTotalCalculation usando a interface da linha de comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

O `set` grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Desabilitar DeferredTotalCalculation**:

Você pode desativar DeferredTotalCalculation usando a interface da linha de comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

O `set` grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Consulte [DeferredTotalCalculating] no _Guia de referência do módulo_.

### Imposto fixo sobre o produto

Quando DeferredTotalCalculation está ativado, o FPT (Imposto fixo do produto) não é incluído no preço do produto e no subtotal do carrinho do minicarrinho após adicionar o produto ao carrinho de compras. O cálculo de FPT é adiado ao adicionar um produto ao minicarrinho. O FPT é exibido corretamente no carrinho de compras depois de prosseguir para o check-out final.

## Desativar verificação de inventário

O _Ativar Inventário No Carregamento Do Carrinho_ a configuração global determina se é necessário executar uma verificação de inventário ao carregar um produto no carrinho. Desativar o processo de verificação de inventário melhora o desempenho de todas as etapas de finalização, especialmente quando se trata de produtos em massa no carrinho.

Quando desativado, a verificação de inventário não ocorre ao adicionar um produto ao carrinho de compras. Se essa verificação de inventário for ignorada, alguns cenários indisponíveis poderão gerar outros tipos de erros. Uma verificação de inventário _always_ ocorre na etapa de posicionamento do pedido, mesmo quando desabilitado.

**Ativar Verificação de Inventário No Carregamento Do Carrinho** estiver ativado (definido como Sim) por padrão. Para desativar a verificação de inventário ao carregar o carrinho, defina **[!UICONTROL Enable Inventory Check On Cart Load]** para `No` na interface do usuário do administrador **Lojas** > **Configuração** > **Catálogo** > **Inventário** > **Opções de Estoque** seção. Consulte [Configurar opções globais][global] e [Inventário do catálogo][inventory] no _Guia do usuário_.

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://devdocs.magento.com/guides/v2.4//mrg/intro.html
[AsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[DeferredTotalCalculating]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
