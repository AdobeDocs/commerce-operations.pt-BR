---
title: "ACSD-49502: link baixável não atualizado corretamente após [!DNL staging] atualização"
description: Aplique o patch ACSD-49502 para corrigir o problema do Adobe Commerce em que o link baixável não é atualizado corretamente depois que uma atualização do  [!DNL staging]  é aplicada ao produto baixável.
feature: Staging
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49502: link para download não atualizado corretamente após a atualização [!DNL staging]

O patch ACSD-49502 corrige o problema em que o link baixável não é atualizado corretamente após uma atualização [!DNL staging] ser aplicada ao produto baixável. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49502. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O link baixável não é atualizado corretamente depois que uma atualização [!DNL staging] é aplicada ao produto baixável.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto para download com os links.
1. Crie uma conta de cliente e faça logon.
1. Adicione o produto baixável ao carrinho pela loja.
1. No **[!UICONTROL Admin]**, agende uma nova atualização para o produto baixável e deixe a atualização agendada ser concluída.
1. Conclua o pedido na vitrine.

<u>Resultados esperados</u>:

Os links para download são preservados ao usar atualizações programadas enquanto os produtos adicionados anteriormente estão no carrinho.

<u>Resultados reais</u>:

Links baixáveis estão ausentes no *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) do cliente e nas páginas de exibição de pedidos no **[!UICONTROL Admin]**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
