---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* definido como Sim sem a opção *[!UICONTROL Use in Search]*'
description: Aplique o patch ACSD-50887 para corrigir o problema do Adobe Commerce em que a propriedade de atributo de produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definida como *Sim* sem que a opção *[!UICONTROL Use in Search]* também seja definida como *Sim*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* definido como *Sim* sem a opção *[!UICONTROL Use in Search]*

O patch ACSD-50887 corrige o problema em que a propriedade de atributo de produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definida como *Sim* sem que a opção *[!UICONTROL Use in Search]* também seja definida como *Sim*. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. A ID do patch é ACSD-50887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A propriedade de atributo de produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definida como *Sim* sem que a opção *[!UICONTROL Use in Search]* também seja definida como *Sim*.

Essas configurações foram projetadas para serem usadas juntas. Com o patch aplicado, quando a opção *[!UICONTROL Use in Search]* está definida como *Não*, a opção *[!UICONTROL Use in Search Results Layered Navigation]* fica oculta para funcionar como se também estivesse definida como *Não*.

<u>Etapas a serem reproduzidas</u>:

1. No Admin, navegue até **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** e crie um atributo com o tipo de multisseleção e defina o seguinte:

   * *[!UICONTROL Use in Search]= Não*
   * *[!UICONTROL Use in Layered Navigation]= (Qualquer opção)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Sim*
   * *Nome = Test_attribute*
   * *Opções*:
      * *Adesivo*
      * *Seletor*

1. Adicione o novo atributo ao conjunto de atributos padrão.
1. Crie dois produtos:

   1. Primeiro produto:
      * Nome = Adesivo
      * Definir Preço, QTD., Peso como 1
      * Test_attribute = selecione a opção *Sticker*

   1. Segundo produto:
      * Nome = Seletor
      * Definir Preço, QTD., Peso como 1
      * Test_attribute = selecionar ambas as opções

1. Executar reindexação de `catalogsearch_fulltext`:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Pesquise pela palavra *adesivo* na vitrine.

<u>Resultados esperados</u>:

Somente o produto *Adesivo* é retornado, porque [!DNL Elasticsearch] não indexará Test_attribute quando *[!UICONTROL Use in Search]* tiver sido definido como *Não*.

<u>Resultados reais</u>:

Ambos os produtos são devolvidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
