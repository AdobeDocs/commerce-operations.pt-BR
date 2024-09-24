---
title: "ACSD-47444: erro _[!UICONTROL Trying to access array offset on value of type bool]_ ao acessar determinados caminhos de categoria não existentes para produtos conhecidos no PHP 7.4"
description: Aplique o patch ACSD-47444 para corrigir o problema do Adobe Commerce onde há um erro _[!UICONTROL Trying to access array offset on value of type bool]_ ao acessar certos caminhos de categorias não existentes para produtos conhecidos, no PHP 7.4.
feature: Categories, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444: erro _[!UICONTROL Trying to access array offset on value of type bool]_ao acessar determinados caminhos de categoria não existentes para produtos conhecidos no PHP 7.4

O patch ACSD-47444 resolve o problema em que você vê o erro _[!UICONTROL Trying to access array offset on value of type bool]_ao acessar certos caminhos de categoria não existentes para produtos conhecidos no PHP 7.4. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 está instalado.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Você enfrenta o seguinte erro: _[!UICONTROL Trying to access array offset on value of type bool]_ao acessar certos caminhos de categoria não existentes para produtos conhecidos, no PHP 7.4.

<u>Pré-requisitos</u>:

PHP 7.4.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo produto - com o nome &quot;test&quot;.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > conjunto **[!UICONTROL Generate "category/product" URL Rewrites]** = _Não_.
1. Acesse a loja e visite o URL como ../abc/test.html (&quot;abc&quot; - não deveria existir).

<u>Resultados esperados</u>:

página 404.

<u>Resultados reais</u>:

Erro 500:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
