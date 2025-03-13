---
title: 'ACSD-63323: Resolve a funcionalidade [!UICONTROL Select All] e melhora a paginação e a contagem de registros no pop-up de categoria de produto'
description: Aplique o patch ACSD-63323 para corrigir o problema do Adobe Commerce em que a opção [!UICONTROL Select All] não funciona ao adicionar produtos a uma categoria. Além disso, garante que a paginação e o rótulo de contagem de registros funcionem corretamente ao adicionar produtos a uma categoria por meio da grade pop-up.
feature: Products
role: Admin, Developer
source-git-commit: f3f0cc93adf83b485ca50811adcc561638e3c5c2
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-63323: Resolve a funcionalidade [!UICONTROL Select All] e melhora a paginação e a contagem de registros no pop-up de categoria de produto

O patch ACSD-63323 corrige o problema em que a opção **[!UICONTROL Select All]** não funciona ao adicionar produtos a uma categoria. Além disso, garante que a paginação e o rótulo de contagem de registros funcionem corretamente ao adicionar produtos a uma categoria por meio da grade pop-up. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) é instalado. A ID do patch é ACSD-63323. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que a opção **[!UICONTROL Select All]** não funciona em Admin > **[!UICONTROL Categories]** > escolha uma categoria > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**. Também ajuda a que a paginação e o rótulo de contagem de registros funcionem corretamente ao adicionar produtos a uma categoria por meio da grade pop-up.


<u>Etapas a serem reproduzidas</u>:

1. Gerar produtos *1200* usando o comando:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Abra **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e veja o número de produtos: *1200* registros encontrados.
1. Abra uma Categoria Padrão > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**.
1. Clique em **[!UICONTROL Assign]** > **[!UICONTROL Select All]**.
1. Altere o número de produtos na página para o valor = *5*.


**Resultados esperados**:

*A mensagem deve ser: 1200 registros encontrados (1200 selecionados)*

**Resultados reais**:

* A paginação não funciona.
* A mensagem errada é exibida: *5* registros encontrados (*20* selecionados)

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.


