---
title: 'ACSD-66041: códigos postais da Irlanda (IE) não pesquisáveis por locais de coleta devido à falta de CountryID'
description: Aplique o patch ACSD-66041 para corrigir o problema do Adobe Commerce, em que os códigos postais da Irlanda (IE) não eram pesquisáveis por locais de coleta devido a uma CountryID ausente.
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 4c33da14-38b2-4a3c-a680-849b62dfb896
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-66041: Códigos postais da Irlanda (IE) não pesquisáveis para locais de retirada devido à falta de `CountryID`

O patch ACSD-66041 corrige o problema em que os códigos postais da Irlanda (IE) não são pesquisáveis por locais de coleta devido a um `CountryID` ausente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACSD-66041. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os códigos postais da Irlanda (IE) não podem ser pesquisados por locais de retirada devido a um `CountryID` ausente.

<u>Etapas a serem reproduzidas</u>:

1. Execute a seguinte consulta do GraphQL:

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. Use as seguintes variáveis:

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u>Resultados esperados</u>:

Os códigos postais da Irlanda estão disponíveis para procurar locais de coleta.

<u>Resultados reais</u>:

* Um *Erro Interno do Servidor* foi retornado.
* `var/log/exception.log` contém o seguinte erro:

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
