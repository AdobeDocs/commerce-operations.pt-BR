---
title: "ACSD-53204: erro *O produto não pode ser salvo* em solicitações simultâneas para adicionar imagens à galeria"
description: Aplique o patch ACSD-53204 para corrigir o problema do Adobe Commerce, em que *O produto não pode ser salvo*, o erro é lançado ao fazer solicitações simultâneas para adicionar imagens à galeria de produtos usando o ponto de extremidade rest/V1/products/&lt;sku&gt;/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-53204: Erro &quot;*O produto não pode ser salvo*&quot; nas solicitações simultâneas para adicionar imagens à galeria

O patch ACSD-53204 corrige o problema em que o erro &quot;*O produto não pode ser salvo*&quot; é lançado ao serem feitas solicitações simultâneas para adicionar imagens à galeria de produtos usando o ponto de extremidade `rest/V1/products/<sku>/media`. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.39 está instalado. A ID do patch é ACSD-53204. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O erro &quot;*O produto não pode ser salvo*&quot; é lançado ao serem feitas solicitações simultâneas para adicionar imagens à galeria de produtos usando o ponto de extremidade `rest/V1/products/<sku>/media`.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Painel de administração.
1. Crie um produto com SKU p1.
1. Faça várias solicitações simultâneas para o ponto de extremidade `rest/V1/products/<sku>/media` para carregar várias imagens simultaneamente.

<u>Resultados esperados</u>:

As imagens são salvas sem erros.

<u>Resultados reais</u>:

O erro &quot;*O produto não pode ser salvo*&quot; é retornado ocasionalmente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
