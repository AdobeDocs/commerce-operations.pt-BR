---
title: 'ACSD-67347: falha na ordem com o erro "Não é possível adquirir um bloqueio" ao usar códigos de cupom'
description: Aplique o patch ACSD-67347 ao problema do Adobe Commerce em que os pedidos falham com um erro "Não é possível adquirir um bloqueio" quando os códigos de cupom contêm caracteres especiais (por exemplo, BIT/123456) e o bloqueio de arquivo está ativado.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347: Falha na ordem com *Não é possível adquirir um erro de bloqueio* ao usar códigos de cupom

O patch ACSD-67347 corrige o problema em que os pedidos falham com um erro *Não é possível adquirir um bloqueio* quando os códigos de cupom contêm caracteres especiais (por exemplo, BIT/123456) e o bloqueio de arquivo está habilitado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-67347. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p12

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os pedidos falham com o erro *Não é possível adquirir um bloqueio* quando cupons com caracteres especiais são usados e o bloqueio de arquivos é habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Instalar o 2.4-develop.
1. Definir a configuração de bloqueio de arquivo no arquivo `env.php`:

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. Crie uma regra de carrinho com um cupom usando o formato de código do cupom: *BIT/123456*.
1. Crie um produto simples.
1. Adicione o produto ao carrinho e aplique o código do cupom.
1. Prossiga para o check-out e faça o pedido.

<u>Resultados esperados</u>:

Os pedidos são feitos com êxito porque não há restrições à criação de códigos de cupom.

<u>Resultados reais</u>:

O pedido não pode ser feito. O seguinte erro aparece: *Não é possível adquirir bloqueio.*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
