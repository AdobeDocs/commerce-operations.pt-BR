---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* definido como Sim sem a opção *[!UICONTROL Use in Search]*'
description: Aplique o patch ACSD-50887 para corrigir o problema do Adobe Commerce em que a propriedade de atributo de produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definida como *Sim* sem que a opção *[!UICONTROL Use in Search]* também seja definida como *Sim*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '461'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
