---
title: "ACSD-48058: a reindexação de preço do produto não funciona se o produto empacotado não for atribuído ao site"
description: Aplique o patch ACSD-48058 para corrigir o problema do Adobe Commerce em que a reindexação de preço do produto não está funcionando se o produto incluído não estiver atribuído a nenhum site.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-48058: a reindexação de preço do produto não funciona se o produto empacotado não for atribuído ao site

O patch ACSD-48058 corrige o problema em que a reindexação do preço do produto não funciona se o produto incluído não estiver atribuído a nenhum site. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 está instalado. A ID do patch é ACSD-48058. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação de preço do produto não funcionará se o produto agrupado não for atribuído a nenhum site.

<u>Etapas a serem reproduzidas</u>:

1. Acesse Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e crie um novo produto agrupado ou edite um produto agrupado existente.
   * Clique na guia **[!UICONTROL Product in Websites]** e desmarque todas as caixas de seleção (sites)
   * Salve o produto
1. Executar reindexação.

<u>Resultados esperados</u>:

A reindexação foi executada com sucesso.

<u>Resultados reais</u>:

O seguinte erro é lançado durante a execução do índice de preço do produto:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
