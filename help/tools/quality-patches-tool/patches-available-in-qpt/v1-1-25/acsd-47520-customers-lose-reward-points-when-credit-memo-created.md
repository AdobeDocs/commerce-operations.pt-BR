---
title: 'ACSD-47520: os clientes perdem pontos de premiação quando um memorando de crédito é criado'
description: Aplique o patch ACSD-47520 para corrigir o problema do Adobe Commerce em que os clientes perdem pontos de recompensa quando um memorando de crédito é criado.
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
exl-id: 09104451-e9f0-4ddb-b019-8aa34630edb9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-47520: os clientes perdem pontos de premiação quando um memorando de crédito é criado

O patch ACSD-47520 corrige o problema em que os clientes perdem pontos de recompensa quando um memorando de crédito é criado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 está instalado. A ID do patch é ACSD-47520. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes perdem pontos de premiação quando um memorando de crédito é criado.

<u>Etapas a serem reproduzidas</u>:

1. Acesse Administrador do Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Altere a configuração:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Sim_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Sim_
   * **[!UICONTROL Customers May See Reward Points History]** = _Sim_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Não_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Sim_
1. Vá para Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** e clique em **[!UICONTROL Add New Rate]**.
1. Adicione uma nova taxa (1:1) e limpe o cache.
1. Crie um cliente e adicione 10 pontos de premiação a esta conta.
1. Acesse Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Selecione o cliente criado na etapa anterior.
1. Selecione qualquer produto cujo preço seja maior que os pontos de premiação.
1. Fazer um pedido por meio de qualquer método de pagamento e dos pontos de premiação.
1. Criar uma fatura para o pedido.
1. Criar um memorando de crédito, mas não reembolsar os pontos de premiação.

<u>Resultados esperados</u>:

* O Administrador pode reembolsar os pontos de premiação.

* O status do pedido será fechado.

<u>Resultados reais</u>:

* Não há como reembolsar os pontos de recompensa.

* O status do pedido é **[!UICONTROL Completed]**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
