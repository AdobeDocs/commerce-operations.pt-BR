---
title: 'ACSD-55427: um administrador não pode cancelar a atribuição do produto a **[!UICONTROL Product in Shared Catalogs]** na página do produto'
description: Aplique o patch ACSD-55427 para corrigir o problema do Adobe Commerce em que um produto não pode ser desatribuído de **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-55427: um administrador não pode cancelar a atribuição do produto de **[!UICONTROL Product in Shared Catalogs]** na página do produto

O patch ACSD-55427 corrige o problema em que não é possível desatribuir um produto de **[!UICONTROL Product in Shared Catalogs]** na página do produto no catálogo no Administrador do Commerce. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 está instalado. A ID do patch é ACSD-55427. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Não é possível cancelar a atribuição de um produto a **[!UICONTROL Product in Shared Catalogs]** na página do produto no catálogo do Administrador do Commerce.

<u>Etapas a serem reproduzidas</u>:

Pré-requisitos: Adobe Commerce instalado com B2B e **[!UICONTROL Shared Catalogs]** habilitados.
1. Crie um produto.
1. Navegue até o painel do catálogo compartilhado e abra o catálogo compartilhado padrão.
1. Atribuir o produto ao catálogo padrão e definir um preço inferior ao preço do produto.
1. Salve o catálogo compartilhado.
1. Execute o [!UICONTROL CRON] para atualizar os consumidores/indexadores.
1. Abra o produto e remova-o da seção **[!UICONTROL Product in Shared Catalogs]**.

<u>Resultados esperados</u>:

O produto deve ser removido da seção **[!UICONTROL Product in Shared Catalogs]**.

<u>Resultados reais</u>:

O produto ainda é exibido na seção **[!UICONTROL Product in Shared Catalogs]**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
