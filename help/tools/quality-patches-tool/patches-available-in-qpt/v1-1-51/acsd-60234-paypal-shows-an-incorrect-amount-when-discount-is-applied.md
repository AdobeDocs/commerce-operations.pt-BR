---
title: 'ACSD-60234: [!DNL PayPal] mostra um valor incorreto quando o desconto é aplicado'
description: Aplique o patch ACSD-60234 para corrigir o problema do Adobe Commerce em que [!DNL PayPal] mostra um valor incorreto quando o desconto é aplicado por meio do método de pagamento.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '423'
ht-degree: 0%
---
# ACSD-60234: [!DNL PayPal] mostra um valor incorreto quando o desconto é aplicado

O patch ACSD-60234 corrige o problema em que [!DNL PayPal] mostra um valor incorreto quando o desconto é aplicado por meio do método de pagamento. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado. A ID do patch é ACSD-60234. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL PayPal] mostra um valor incorreto quando o desconto é aplicado por meio do método de pagamento.

<u>Etapas a serem reproduzidas</u>:

1. Configurar *[!DNL PayPal Express]* em **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**.
   * [!UICONTROL Enable In-Context Checkout] pode ser [!UICONTROL Yes] ou [!UICONTROL NO], o problema se reproduz em ambos os cenários.
1. Criar um *[!UICONTROL Cart Rule]* em **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**.
   * Condição: Se todas essas condições forem verdadeiras: *[!UICONTROL Payment Method]* é *[!DNL PayPal Express Checkout]*.
   * Ações: Qualquer ação.
1. Crie um produto.
1. Vá para a loja, adicione o produto ao carrinho e vá para a etapa **[!UICONTROL Payment Method]** do check-out.
1. Selecione *[!DNL PayPal Express]* e valide se o desconto foi aplicado corretamente.
1. Clique no botão **[!DNL PayPal]**.
1. Faça logon e observe o conteúdo do pop-up.

<u>Resultados esperados</u>:

O valor a ser pago passado para [!DNL PayPal] inclui o desconto como está no carrinho.

<u>Resultados reais</u>:

O valor total a ser pago não inclui o desconto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
