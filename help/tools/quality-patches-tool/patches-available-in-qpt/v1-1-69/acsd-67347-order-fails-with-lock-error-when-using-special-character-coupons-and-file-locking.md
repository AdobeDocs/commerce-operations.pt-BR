---
title: 'ACSD-67347: falha na ordem com o erro "Não é possível adquirir um bloqueio" ao usar códigos de cupom'
description: Aplique o patch ACSD-67347 ao problema do Adobe Commerce em que os pedidos falham com um erro "Não é possível adquirir um bloqueio" quando os códigos de cupom contêm caracteres especiais (por exemplo, BIT/123456) e o bloqueio de arquivo está ativado.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: a439e163-8b09-456c-91bd-6ee67528744e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '394'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os pedidos falham com o erro *Não é possível adquirir um bloqueio* quando cupons com caracteres especiais são usados e o bloqueio de arquivos é habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Instalar o 2.4-develop.
1. Definir a configuração de bloqueio de arquivo no arquivo `env.php`:

   ```text
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

```text
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
