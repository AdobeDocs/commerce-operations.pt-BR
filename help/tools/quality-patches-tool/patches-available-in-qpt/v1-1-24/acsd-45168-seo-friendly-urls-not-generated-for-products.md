---
title: 'ACSD-45168: URLs amigáveis para SEO não geradas para produtos que têm atributos url_key substituídos'
description: Aplique o patch ACSD-45168 para corrigir o problema do Adobe Commerce, em que URLs amigáveis para SEO não gerados para produtos que têm atributos url_key substituídos no nível da visualização da loja.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-45168: URLs amigáveis para SEO não geradas para produtos que têm atributos url_key substituídos

O patch ACSD-45168 corrige o problema em que URLs amigáveis para SEO não são gerados para produtos que têm atributos url_key substituídos no nível de visualização da loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-45168. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

URLs compatíveis com SEO não são gerados para produtos que têm atributos url_key substituídos no nível de visualização da loja.

<u>Etapas a serem reproduzidas</u>:

1. Defina a configuração da seguinte maneira acessando **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Sim*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Sim*
1. Limpe o cache de configuração.
1. Crie duas categorias: [!UICONTROL Category 1] e [!UICONTROL Category 2].
1. Crie dois produtos: [!UICONTROL Product 1] em [!UICONTROL Category 1], [!UICONTROL Product 2] em [!UICONTROL Category 1].
1. Alterar o escopo para [!UICONTROL Default Store View] para [!UICONTROL Product 1].
1. Desmarque a URL opcional [!UICONTROL Key] em [!UICONTROL Search Engine Optimization].
1. Salve o produto.
1. Voltar para [!UICONTROL All Store Views].
1. Adicionar [!UICONTROL Product 1] a [!UICONTROL Category 2] e adicionar [!UICONTROL Product 2] a [!UICONTROL Category 2].
1. Verifique a tabela `url_rewrite` ou [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Resultados esperados</u>:

A URL compatível com SEO para [!UICONTROL Category 2] foi criada para [!UICONTROL Product 1].

<u>Resultados reais</u>:

A URL compatível com SEO para [!UICONTROL Category 2] está ausente para [!UICONTROL Product 1] porque ela teve o atributo de chave da URL substituído para o escopo de exibição do armazenamento.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
