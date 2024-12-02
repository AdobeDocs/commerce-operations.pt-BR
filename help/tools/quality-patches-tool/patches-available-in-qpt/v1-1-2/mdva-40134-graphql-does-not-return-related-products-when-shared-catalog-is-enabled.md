---
title: 'MDVA-40134: o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado'
description: O patch MDVA-40134 corrige o problema em que o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está ativado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-40134. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134: o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado

O patch MDVA-40134 corrige o problema em que o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está ativado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-40134. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado.

<u>Pré-requisitos</u>:

Os módulos B2B devem ser instalados.
A instância deve ser limpa somente com os dados de amostra.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas** > **Configuração** > **Geral** > **Recursos B2B** e habilite a **Empresa e Catálogo Compartilhado**.
1. Vá para **Catálogo** > **Catálogo Compartilhado** e adicione todos os produtos ao **Catálogo Geral**.
1. Use os dados de amostra e modifique o Joust Duffle Bag (SKU 24-MB01).
1. Em **Produtos relacionados**, adicione as duas bolsas Duffle (ID 7 e 13).
1. Enviar uma solicitação **Post**:

<pre>{
  products(filtro: {sku: {eq: "24-MB01"}}, classificar: {name: ASC}) {
    itens {
      related_products {
        uid
        name
      }
    }
  }
}</pre>

<u>Resultados esperados</u>:

Os produtos relacionados são mostrados na resposta da GraphQL.

<u>Resultados reais</u>:

Os usuários recebem o seguinte erro:

<pre>O valor de retorno de Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() deve ser do tipo int, null retornado {"exception":"[object] (GraphQL\\Error\\Error(code: 0): O valor de retorno de Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() deve ser do tipo int, null retornado </pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
