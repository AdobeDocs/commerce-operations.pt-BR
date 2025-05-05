---
title: 'ACSD-53239: O indexador de inventário limpa todos os caches'
description: Aplique o patch ACSD-53239 para corrigir o problema do Adobe Commerce em que o indexador de inventário limpa todos os caches no modo [!UICONTROL Update on Schedule].
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: 69e71e2d-8f26-4200-ad4a-6bd9e45627e4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-53239: O indexador de inventário limpa todos os caches no modo [!UICONTROL Update on Schedule]

O patch ACSD-53239 corrige o problema em que o indexador de inventário limpa todos os caches no modo [!UICONTROL Update on Schedule]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36 está instalado. A ID do patch é ACSD-53239. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O indexador de inventário limpa todos os caches no modo [!UICONTROL Update on Schedule].

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** e selecione cerca de *1200* produtos.
2. Atualize *[!UICONTROL Qty]* para um novo valor e clique em **[!UICONTROL Save]**.
3. Executar `bin/magento cron:run` imediatamente após salvar.
4. Execute a seguinte consulta do GraphQL:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Resultados esperados</u>

A consulta é processada dentro do tempo normal.

<u>Resultados reais</u>

A consulta é processada muito lentamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
