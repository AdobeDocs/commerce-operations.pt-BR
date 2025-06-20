---
title: 'ACSD-57074: *Sim/Não* o atributo personalizado com o prefixo &grave;price_*&grave; no atributo &grave;attribute_code&grave; não funciona com a indexação'
description: Aplique o patch ACSD-57074 para corrigir o problema do Adobe Commerce em que o atributo personalizado *Sim/Não* com o prefixo &grave;price_*&grave; no atributo &grave;attribute_code&grave; não funciona com a indexação.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074: *Sim/Não* o atributo personalizado com prefixo `price_*` no atributo `attribute_code` não funciona com indexação

O patch ACSD-57074 corrige o problema em que o atributo personalizado *Sim/Não* com o prefixo `price_*` no atributo `attribute_code` não funciona com indexação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.47 está instalado. A ID do patch é ACSD-57074. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O atributo personalizado *Sim/Não* com o prefixo `price_*` no atributo `attribute_code` não funciona com indexação.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo de produto personalizado com as seguintes opções:
   * *[!UICONTROL Catalog Input Type]*: *Sim/Não*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Sim*
1. Atribua o atributo ao conjunto de atributos padrão.
1. Crie um produto com o atributo que criamos.
1. Atribua o produto que acabamos de criar a uma categoria.
1. Executar reindexação completa.

<u>Resultados esperados</u>:

O produto é exibido na categoria atribuída.

<u>Resultados reais</u>:

O produto não é exibido na página inicial da categoria.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
