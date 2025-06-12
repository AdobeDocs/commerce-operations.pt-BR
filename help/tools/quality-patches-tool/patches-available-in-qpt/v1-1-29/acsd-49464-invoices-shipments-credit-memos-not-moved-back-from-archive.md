---
title: 'ACSD-49464: NFFs, entregas e avisos de crédito não movidos do arquivo'
description: Aplique o patch ACSD-49464 para corrigir o problema do Adobe Commerce em que NFFs, entregas e avisos de crédito não são movidos de volta do arquivo quando orderId é diferente.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464: NFFs, entregas e avisos de crédito não movidos do arquivo

O patch ACSD-49464 corrige o problema em que faturas, remessas e avisos de crédito não são movidos do arquivo quando orderId é diferente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49464. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

NFFs, entregas e avisos de crédito não são movidos de volta do arquivo quando a orderId é diferente.

<u>Etapas a serem reproduzidas</u>:

1. Ativar arquivamento de ordens, NFFs, entregas e avisos de crédito.
1. Criar e concluir um pedido, incluindo remessa, fatura e aviso de crédito.
1. Certifique-se de que as IDs de remessa, fatura e aviso de crédito não sejam iguais ao número do pedido.
1. Mova a ordem para o arquivo morto.
1. Restaurar a ordem arquivada para o gerenciamento de pedidos.
1. Verifique os detalhes da fatura, da remessa e do memorando de crédito nas respectivas páginas de grade [!UICONTROL Invoice], [!UICONTROL Shipping] e [!UICONTROL Credit Memo].

<u>Resultados esperados</u>:

Os registros relacionados originais são restaurados quando o pedido é movido da lista de arquivamento para o gerenciamento de pedidos.

<u>Resultados reais</u>:

* Nenhum registro para remessa, fatura e avisos de crédito se todas as IDs forem diferentes.
* Se o pedido e os registros relacionados tiverem a mesma ID, os registros serão retornados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
