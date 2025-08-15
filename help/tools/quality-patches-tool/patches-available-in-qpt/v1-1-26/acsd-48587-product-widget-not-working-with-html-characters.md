---
title: 'ACSD-48587: o widget do produto não funciona com SKUs que contêm caracteres HTML'
description: Aplique o patch ACSD-48587 para corrigir o problema do Adobe Commerce em que caracteres especiais do HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
exl-id: c3e31835-03be-46b4-a080-09edf55b5b4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587: o widget do produto não funciona com SKUs que contêm caracteres HTML

O patch ACSD-48587 corrige o problema em que caracteres especiais do HTML nas regras de correspondência do widget produtos impedem que eles exibam produtos correspondentes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 está instalado. A ID do patch é ACSD-48587. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O widget do produto não está funcionando com SKUs contendo símbolos *&quot;&amp;&quot;*.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto contendo *&quot;&amp;&quot;* na SKU (por exemplo, s000&amp;01).
1. Edite o conteúdo de uma página do CMS no *Page Builder*.
1. Adicionar um widget Produtos.
1. Edite o widget e defina **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Insira a SKU que contém *&quot;&amp;&quot;* no campo SKUs do produto.
1. Salve o conteúdo e a página do CMS.
1. Verifique o conteúdo da *Página do CMS* para a *visualização do Page Builder* e a vitrine do produto.

<u>Resultados esperados</u>:

O produto com *&quot;&amp;&quot;* na SKU é exibido na pré-visualização do Page Builder e na vitrine.

<u>Resultados reais</u>:

O produto com *&quot;&amp;&quot;* na SKU não é exibido na visualização do Page Builder.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
