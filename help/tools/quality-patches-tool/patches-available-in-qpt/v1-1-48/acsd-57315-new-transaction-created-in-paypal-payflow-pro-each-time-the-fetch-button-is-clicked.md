---
title: 'ACSD-57315: Nova transação criada em  [!DNL PayPal Payflow Pro]  sempre que o botão Buscar é clicado'
description: Aplique o patch ACSD-57315 para corrigir o problema do Adobe Commerce em que uma nova transação é criada no  [!DNL PayPal Payflow Pro]  sempre que o botão buscar é clicado na tela exibir transação no [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315: Uma nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão Buscar é clicado

O patch ACSD-57315 corrige o problema em que uma nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão buscar é clicado na tela exibir transação no [!UICONTROL Admin]. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.48 está instalado. A ID do patch é ACSD-57315. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão Buscar é clicado na tela exibir transação no [!UICONTROL Admin].

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL PayPal Payflow Pro].
1. Defina o método de transação como *[!UICONTROL Sale]*.
1. Faça um pedido usando o *Cartão de Crédito*.
1. Abra a transação de [!UICONTROL Admin].
1. Clique no botão **[!UICONTROL Fetch]**.
1. Verificar a conta [!DNL PayPal] para transações relacionadas ao pedido feito.

<u>Resultados esperados</u>:

Não é criada uma nova transação de pagamento.

<u>Resultados reais</u>:

Uma nova transação de pagamento é criada para um pedido que já foi pago.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
