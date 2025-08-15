---
title: 'ACSD-63329: Atributos de data e hora não são definidos ao criar produtos com a API REST'
description: Aplique o patch ACSD-63329 para corrigir o problema do Adobe Commerce em que os valores padrão não são definidos para os campos de data e hora ao criar produtos com a API REST.
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329: Os valores padrão para campos de data e hora não são definidos ao criar produtos com a API REST

O patch ACSD-63329 corrige o problema em que os valores padrão não eram definidos para os campos de data e hora ao criar um novo produto usando a API REST: `/rest/default/V1/products`. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63329. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os valores padrão não são definidos para os campos de data e hora ao criar produtos com a API REST: `/rest/default/V1/products`

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo **[!UICONTROL Product]**, defina seu valor padrão como `12/31/2020` e defina **[!UICONTROL Catalog Input Type for Store Owner]** como ***[!UICONTROL Date]*** ou ***[!UICONTROL Date and Time]**.
1. Crie outro atributo de tipo de texto e defina o valor padrão como ***valor de teste***.
1. Crie um novo produto usando uma solicitação POST da API REST para `/rest/all/V1/products/`.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. Verifique os valores salvos para os atributos mencionados acima.

<u>Resultados esperados</u>:

O valor padrão deve ser salvo nos atributos de tipo **[!UICONTROL Date/Datetime]** ao criar um produto usando a API.

<u>Resultados reais</u>:

O valor padrão é salvo para o atributo **[!UICONTROL Text]**, mas não para o atributo **[!UICONTROL Date type]**. O valor do atributo **[!UICONTROL Date]** está vazio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
