---
title: 'ACSD-60538: os atributos não são exibidos corretamente se o produto estiver desabilitado no [!UICONTROL All Store Views]'
description: Aplique o patch ACSD-60538 para corrigir o problema do Adobe Commerce em que, se um produto estiver desativado em *Todas as exibições da loja* e ativado apenas em escopos específicos de exibição da loja, os atributos do produto não são exibidos corretamente na resposta do GraphQL, fazendo com que o produto não seja exibido corretamente.
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538: os atributos não são exibidos corretamente se o produto estiver desabilitado no *[!UICONTROL All Store Views]*

O patch ACSD-60538 corrige o problema em que, se um produto estiver desabilitado no *[!UICONTROL All Store Views]* e habilitado somente em escopos de exibição de loja específicos, os atributos do produto não serão exibidos corretamente na resposta do GraphQL, fazendo com que o produto não seja exibido corretamente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 está instalado. A ID do patch é ACSD-60538. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Se um produto estiver desabilitado no *[!UICONTROL All Store Views]* e habilitado apenas em escopos de exibição de loja específicos, os atributos do produto não serão exibidos corretamente na resposta do GraphQL, fazendo com que o produto não seja exibido corretamente.

<u>Pré-requisitos</u>:

O módulo de inventário está instalado.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com o atributo *color* e três produtos derivados (*blue*, *black* e *brown*).
1. Desabilitar dois produtos derivados associados (*blue* e *black*) no escopo *[!UICONTROL All Store Views]*.
1. Ir para o escopo **[!UICONTROL Store View]**.
1. Habilitar produtos filho (*blue* e *black*) no escopo *[!UICONTROL Store View]*.
1. Execute a solicitação do GraphQL abaixo:

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>Resultados esperados</u>:

A resposta do GraphQL inclui os valores de atributo do produto associado filho que está desabilitado em *[!UICONTROL All Store Views]* e habilitado no escopo *[!UICONTROL Store View]*.

<u>Resultados reais</u>:

A resposta do GraphQL tem valores de atributo vazios para o produto associado filho quando o produto está desabilitado em *[!UICONTROL All Store Views]* e habilitado no escopo *[!UICONTROL Store View]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
