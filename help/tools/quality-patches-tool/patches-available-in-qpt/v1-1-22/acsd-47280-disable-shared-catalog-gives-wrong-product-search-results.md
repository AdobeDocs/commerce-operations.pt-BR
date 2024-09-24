---
title: '[!DNL ACSD-47280]: Desabilitar catálogo compartilhado fornece resultados de pesquisa de produto incorretos'
description: Aplique o patch  [!DNL ACSD-47280]  para corrigir a exibição dos resultados de pesquisa corretos quando o recurso de catálogo compartilhado estiver desabilitado.
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: a desabilitação do catálogo compartilhado fornece resultados de pesquisa de produto incorretos

O patch [!DNL ACSD-47280] corrige a exibição dos resultados de pesquisa corretos quando o recurso [!DNL shared catalog] é desabilitado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 está instalado. O [!DNL patch ID] é [!DNL ACSD-47280]. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use [!DNL patch ID] como palavra-chave de pesquisa para localizar o patch.

## Problema

Se você desabilitar [!DNL shared catalog], ocorrerão resultados incorretos na pesquisa de produtos.

<u>Pré-requisitos</u>:

* [!DNL B2B] módulos instalados

<u>Etapas a serem reproduzidas</u>:

1. Crie um segundo site.
1. Atribua um produto ao segundo site.
1. Verificar produtos no **segundo site** usando o [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Habilitar **[!UICONTROL Shared Catalog]** no padrão [!DNL scope].
1. A solicitação [!DNL GraphQL] não mostra mais nenhum produto para o segundo site, que é o resultado correto.
1. Vá para o [!DNL scope] do segundo site e desabilite **[!UICONTROL Company]**.

<u>Resultados esperados</u>:

A solicitação [!DNL GraphQL] ainda deve mostrar produtos para o segundo site.

<u>Resultados reais</u>:

A solicitação [!DNL GraphQL] não mostra nenhum produto para o segundo site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
