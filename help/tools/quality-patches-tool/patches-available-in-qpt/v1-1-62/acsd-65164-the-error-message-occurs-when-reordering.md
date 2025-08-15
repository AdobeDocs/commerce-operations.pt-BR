---
title: 'ACSD-65164: mensagem de erro ao reorganizar o produto configurável com uma única opção personalizada de caixa de seleção selecionada'
description: Aplique o patch ACSD-65164 para corrigir o problema do Adobe Commerce em que a mensagem de erro *Algumas das opções de item selecionadas não estão disponíveis no momento* ocorre ao reordenar um produto configurável com uma única opção personalizada de caixa de seleção selecionada.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164: mensagem de erro ao reorganizar o produto configurável com uma única opção personalizada de caixa de seleção selecionada

O patch ACSD-65164 corrige o problema em que a mensagem de erro *Algumas das opções de item selecionadas não estão disponíveis no momento* ocorre ao reordenar um produto configurável com uma única opção personalizada de caixa de seleção selecionada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 está instalado. A ID do patch é ACSD-65164. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao reordenar um produto configurável com uma única opção personalizada de caixa de seleção selecionada, o sistema retorna uma mensagem de erro: *Algumas das opções de item selecionadas não estão disponíveis no momento*.

### Etapas para replicar:

1. No Painel de Administração, vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**.
1. Em **[!UICONTROL Customizable Options]**, adicione uma opção *Checkbox*.
   * Defina a opção de caixa de seleção como *Obrigatório*.
   * Adicione dois valores de opção.
1. Navegue até a Loja e faça logon como um cliente registrado.
1. Adicione o produto ao carrinho com uma opção de caixa de seleção marcada.
1. Vá para **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**.
1. Vá para **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]** para adicionar o mesmo produto.

**Resultados esperados:**

O produto deve ser adicionado ao carrinho com êxito.

**Resultados Reais:**

Uma mensagem de erro é exibida:

*Não foi possível adicionar o produto com o SKU &quot;24-MB01&quot; ao carrinho de compras: algumas das opções de item selecionadas não estão disponíveis no momento.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
