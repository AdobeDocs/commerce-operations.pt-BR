---
title: 'ACSD-45675: a exportação de produtos usa nomes de categoria do escopo de exibição de loja padrão'
description: O patch ACSD-45675 corrige o problema em que a exportação de produto usa nomes de categoria do escopo de exibição de loja padrão. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 está instalada. A ID do patch é ACSD-45675. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
source-git-commit: b1f7739688a538b25b738efc337fa81f15a5bac8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-45675: a exportação de produtos usa nomes de categoria do escopo de exibição de loja padrão

O patch ACSD-45675 corrige o problema em que a exportação de produto usa nomes de categoria do escopo de exibição de loja padrão. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 está instalado. A ID do patch é ACSD-45675. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exportação de produtos usa nomes de categorias do escopo de exibição de loja padrão.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma exibição de repositório personalizada **[!UICONTROL Thai]** dentro do repositório principal.
1. Torne **[!UICONTROL Thai]** a exibição de armazenamento padrão do site principal.
1. Crie a seguinte estrutura de categoria em **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Selecione a categoria **[!UICONTROL Tea]** e altere **[!UICONTROL Scope]** para **[!UICONTROL Thai]**.
1. Defina o **[!UICONTROL Category Name]** como **[!UICONTROL ชาดำ]**.
1. Crie um produto simples **[!UICONTROL SP001]** e atribua a categoria **[!UICONTROL Black]**.
1. Certifique-se de que o cron não seja executado.
1. Fazer uma exportação de produto. Filtre por SKU e selecione **[!UICONTROL SP001]**.
1. Verifique a coluna **[!UICONTROL categories]** no CSV exportado.

<u>Resultados esperados</u>:

Como nenhum armazenamento foi selecionado durante a exportação, você deve obter um caminho de categoria como o seguinte: *[!UICONTROL Default Category/Tea/Black]*.

<u>Resultados reais</u>:

O caminho da categoria tem linguagens mistas: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tools] > Uso](/help/tools/quality-patches-tool/usage.md) no guia Ferramenta de Patches de Qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
