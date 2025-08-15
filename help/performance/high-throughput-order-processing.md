---
title: Práticas recomendadas de desempenho de check-out
description: Saiba como otimizar o desempenho das experiências de check-out no site do Adobe Commerce.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# Práticas recomendadas de desempenho de check-out

O processo [check-out](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) no Adobe Commerce é um aspecto crítico da experiência da vitrine eletrônica. Ele depende dos recursos [carrinho](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) e [check-out](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) integrados.

O desempenho é fundamental para manter uma boa experiência do usuário. Você pode otimizar o desempenho do check-out configurando as seguintes opções para **processamento de pedido de alta taxa de transferência**:

- [AsyncOrder](#asynchronous-order-placement) — processa de forma assíncrona pedidos usando uma fila.
- [Cálculo do Total Adiado](#deferred-total-calculation) — Adiar cálculos para totais de pedidos até o início do check-out.
- [Verificação de Inventário na Carga do Carrinho](#disable-inventory-check)—Opte por ignorar a validação de inventário dos itens do carrinho.
- [Balanceamento de carga](#load-balancing)—Habilita conexões secundárias para o banco de dados MySQL e a instância Redis.

As opções de configuração Ordem assíncrona, Cálculo de total adiado e Verificação de inventário no carregamento do carrinho funcionam independentemente. Você pode usar todos os três recursos simultaneamente ou habilitar e desabilitar os recursos em qualquer combinação.

>[!NOTE]
>
>Não use o código PHP personalizado para personalizar o carrinho incorporado e os recursos de check-out. Além de possíveis problemas de desempenho, o uso do código PHP personalizado pode resultar em atualizações complexas e desafios de manutenção. Esses problemas aumentam o custo total de propriedade. Se a personalização do carrinho e do check-out baseados em PHP for inevitável, use somente as [extensões aprovadas pelo Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/). Todas as extensões de marketplace estão sujeitas a [análise abrangente](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) para verificar se atendem aos padrões de codificação e às práticas recomendadas da Adobe Commerce.

## Posicionamento assíncrono de pedidos

O módulo _Ordem assíncrona_ habilita o posicionamento assíncrono de pedidos, que marca a ordem como `received`, coloca a ordem em uma fila e processa pedidos da fila com base no primeiro a entrar, primeiro a sair. AsyncOrder está **desabilitada** por padrão.

Por exemplo, um cliente adiciona um produto ao carrinho de compras e seleciona **[!UICONTROL Proceed to Checkout]**. Eles preenchem o formulário **[!UICONTROL Shipping Address]**, selecionam sua **[!UICONTROL Shipping Method]** preferencial, selecionam um método de pagamento e fazem o pedido. O carrinho de compras está limpo, o pedido está marcado como **[!UICONTROL Received]**, mas a quantidade do produto ainda não está ajustada, nem um email de vendas foi enviado ao cliente. O pedido é recebido, mas os detalhes do pedido ainda não estão disponíveis porque o pedido não foi totalmente processado. Ele permanece na fila até que o consumidor `placeOrderProcess` comece, verifique o pedido com o recurso [verificação de inventário](#disable-inventory-check) (habilitado por padrão) e atualize o pedido da seguinte maneira:

- **Produto disponível**—o status do pedido muda para _Pendente_, a quantidade do produto é ajustada, um email com os detalhes do pedido é enviado ao cliente e os detalhes do pedido bem-sucedido ficam disponíveis para exibição na lista **Pedidos e Devoluções** com opções acionáveis, como reordenar.
- **Produto sem estoque ou com pouca oferta**—o status do pedido muda para _Rejeitado_, a quantidade do Produto não é ajustada, um email com detalhes do pedido sobre o problema é enviado ao cliente e os detalhes do pedido rejeitado ficam disponíveis na lista **Pedidos e Devoluções** sem opções acionáveis.

Use a interface de linha de comando para habilitar esses recursos ou edite o arquivo `app/etc/env.php` de acordo com os arquivos README correspondentes definidos no [_Guia de Referência de Módulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Para habilitar AsyncOrder**:

Você pode habilitar a AsyncOrder usando a interface de linha de comando:

```bash
bin/magento setup:config:set --checkout-async 1
```

O comando `set` grava o seguinte no arquivo `app/etc/env.php`:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Consulte [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) no _Guia de Referência de Módulo_.

**Para desabilitar AsyncOrder**:

>[!WARNING]
>
>Antes de desabilitar o módulo AsyncOrder, você deve verificar se _todos_ os processos de ordem assíncrona foram concluídos.

Você pode desativar a AsyncOrder usando a interface de linha de comando:

```bash
bin/magento setup:config:set --checkout-async 0
```

O comando `set` grava o seguinte no arquivo `app/etc/env.php`:

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
| Tipos de check-out | Check-out de OnePage<br>Check-out Padrão<br>Cotação Negociável B2B |
| Métodos de pagamento | Cheque/Ordem de Pagamento<br>Dinheiro na Entrega<br>Braintree<br>PayPal PayFlow Pro |
| Métodos de envio | Todos os métodos de envio são compatíveis. |

Os seguintes recursos **não** são suportados por AsyncOrder, mas continuam a funcionar de forma síncrona:

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

Os desenvolvedores podem excluir explicitamente determinados métodos de pagamento do posicionamento assíncrono de pedido adicionando-os à matriz `Magento\AsyncOrder\Model\OrderManagement::paymentMethods`. Os pedidos que usam métodos de pagamento excluídos são processados de forma síncrona.

### Ordem Assíncrona de Cotação Negociável

O módulo B2B _Ordem assíncrona de Cotação Negociável_ permite salvar itens de ordem de forma assíncrona para a funcionalidade `NegotiableQuote`. Você deve ter AsyncOrder e NegotiableQuote ativadas.

## Cálculo do Total Diferido

O módulo _Cálculo Total Adiado_ otimiza o processo de check-out adiando o cálculo total até que ele seja solicitado para o carrinho de compras ou durante as etapas finais do check-out. Quando ativado, somente o subtotal é calculado conforme um cliente adiciona produtos ao carrinho de compras.

O Cálculo Total Adiado está **desabilitado** por padrão. Use a interface de linha de comando para habilitar esses recursos ou edite o arquivo `app/etc/env.php` de acordo com os arquivos README correspondentes definidos no [_Guia de Referência de Módulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Para habilitar DeferredTotalCalculation**:

Você pode habilitar DeferredTotalCalculation usando a interface de linha de comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

O comando `set` grava o seguinte no arquivo `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Para desabilitar DeferredTotalCalculation**:

Você pode desabilitar DeferredTotalCalculation usando a interface de linha de comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

O comando `set` grava o seguinte no arquivo `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Consulte [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) no _Guia de Referência de Módulo_.

### Imposto Fixo do Produto

Quando o Cálculo Total Diferido está habilitado, o Imposto Fixo do Produto (FPT) não é incluído no preço do produto e no subtotal do carrinho do minicarrinho depois de adicionar o produto ao carrinho de compras. O cálculo do FPT é adiado ao adicionar um produto ao minicarrinho. O FPT é exibido corretamente no carrinho de compras após prosseguir para a finalização.

## Desabilitar verificação de estoque

A configuração global _Habilitar inventário ao carregar o carrinho_ determina se deve ser executada uma verificação de inventário ao carregar um produto no carrinho. Desativar o processo de verificação de inventário melhora o desempenho de todas as etapas de check-out, principalmente ao lidar com produtos em massa no carrinho.

Quando desativada, a verificação de inventário não ocorre ao adicionar um produto ao carrinho. Se essa verificação de inventário for ignorada, alguns cenários sem estoque poderão gerar outros tipos de erros. Uma verificação de inventário _sempre_ ocorre na etapa de posicionamento do pedido, mesmo quando desabilitada.

**Habilitar a Verificação de Inventário na Carga do Carrinho** está habilitado (definido como Sim) por padrão. Para desabilitar a verificação de estoque ao carregar o carrinho, defina **[!UICONTROL Enable Inventory Check On Cart Load]** como `No` na seção **Lojas** da Interface do Administrador > **Configuração** > **Catálogo** > **Inventário** > **Opções de Estoque**. Consulte [Configurar opções globais](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) e [Inventário de catálogo](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) no _Guia do Usuário_.

## Balanceamento de carga

Você pode ajudar a balancear a carga em diferentes nós, habilitando conexões secundárias para o banco de dados MySQL e a instância Redis.

O Adobe Commerce pode ler vários bancos de dados ou instâncias Redis de forma assíncrona. Se você estiver usando o Commerce na infraestrutura em nuvem, poderá configurar as conexões secundárias editando os valores de [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) e [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) no arquivo `.magento.env.yaml`. Somente um nó precisa manipular o tráfego de leitura e gravação. Portanto, definir as variáveis como `true` resultará na criação de uma conexão secundária para o tráfego somente leitura. Defina os valores como `false` para remover qualquer matriz de conexão somente leitura existente do arquivo `env.php`.

Exemplo do arquivo `.magento.env.yaml`:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
