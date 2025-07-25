---
title: 'ACSD-49392: O status da ordem muda para fechado após reembolso parcial'
description: Aplique o patch ACSD-49392 para corrigir o problema do Adobe Commerce em que o status do pedido muda para fechado após um reembolso parcial para um produto empacotado.
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392: O status da ordem muda para fechado após reembolso parcial

>[!NOTE]
>
>O patch ACSD-49392 foi substituído pelo patch [ACSD-57003](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing) para as versões 2.4.6-p7 a 2.4.6-p10.

O patch ACSD-49392 corrige o problema em que o status do pedido muda para fechado após um reembolso parcial para um produto empacotado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.31 está instalado. A ID do patch é ACSD-49392. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.3.7-p4 e 2.4.1 - 2.4.6-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do pedido muda para closed após um reembolso parcial de um produto agrupado.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Adobe Commerce e crie qualquer produto empacotado ou use o produto empacotado existente.
1. Fazer um pedido com este produto agrupado com uma quantidade maior que 1.
1. Vá para o administrador, abra o pedido criado na etapa 2 de **[!UICONTROL Sales]** > **[!UICONTROL Order]** e crie uma fatura. Observe o status do pedido. Estará em processamento.
1. Criar um aviso de crédito parcial (não reembolsar para todos os produtos do pacote).
1. Verifique o status do pedido.

<u>Resultados esperados</u>

Depois de criar um aviso de crédito parcial para o produto agrupado, o status do pedido é em processamento.

<u>Resultados reais</u>

Depois de criar um aviso de crédito parcial para o produto agrupado, o status do pedido é concluído.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
