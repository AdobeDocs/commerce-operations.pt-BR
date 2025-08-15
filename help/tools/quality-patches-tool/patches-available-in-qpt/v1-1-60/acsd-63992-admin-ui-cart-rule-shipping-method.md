---
title: 'ACSD-63992: [!UICONTROL Cart Price Rule] com erro de condição de cupom e método de envio na interface do Administrador'
description: Aplique o patch ACSD-63992 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Cart Price Rule] com um cupom e uma condição baseada em um método de envio não pode ser aplicado corretamente por meio da interface do Administrador.
feature: Price Rules, Admin Workspace
role: Admin, Developer
exl-id: 80f407c7-4552-4cfb-96ae-43773d2ec398
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-63992: [!UICONTROL Cart Price Rule] com erro de condição de cupom e método de envio na interface do Administrador

O patch ACSD-63992 corrige o problema em que o [!UICONTROL Cart Price Rule] com um cupom e uma condição baseados em um método de envio não podem ser aplicados corretamente por meio da interface do usuário do administrador. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 está instalado. A ID do patch é ACSD-63992. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando uma regra de carrinho inclui uma condição para o método de envio na seção **[!UICONTROL Conditions]**, o código de cupom associado não se aplica ao criar um pedido por meio do Painel de Administração. Em vez disso, o sistema exibe o seguinte erro:

_O código do cupom &lt;> não é válido. Verifique o código e tente novamente._

<u>Etapas a serem reproduzidas</u>:

1. Crie uma regra de preço do carrinho e descreva suas condições:
   * Em *[!UICONTROL Conditions]*: adicione uma condição para incluir o método de envio (por exemplo, *[!UICONTROL Flat Rate]*).
   * Em *[!UICONTROL Rule Information]*: Defina **[!UICONTROL Coupon]** como *[!UICONTROL Specific Coupon]* e digite **[!UICONTROL Coupon Code]** como *TEST*.
1. Crie um novo pedido no Painel de Administração e insira o código do cupom *TEST* no campo **[!UICONTROL Apply Coupon]**.

<u>Resultados esperados</u>:

O cupom é aplicado com êxito.

<u>Resultados reais</u>:

A seguinte mensagem de erro é exibida:

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
