---
title: 'ACSD-56546: os produtos configuráveis e empacotados são exibidos como esgotados na loja'
description: Aplique o patch ACSD-56546 para corrigir o problema do Adobe Commerce em que os produtos configuráveis e de pacote são exibidos como esgotados na loja quando a opção de configuração *[!UICONTROL Display Out of Stock Products]* está desabilitada.
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-56546: os produtos configuráveis e empacotados são exibidos como esgotados na loja

O patch ACSD-56546 corrige o problema em que os produtos configuráveis e empacotados são exibidos como esgotados na loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 está instalado. A ID do patch é ACSD-56546. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos configuráveis e agrupados são exibidos como esgotados na loja quando a opção *[!UICONTROL Display Out of Stock Products]* está desativada.

<u>Etapas a serem reproduzidas</u>:

1. Defina a opção **[!UICONTROL Display Out of Stock Products]** como *Não*.
1. Crie um site, uma loja e uma loja.
1. Crie uma fonte e um estoque e atribua-o ao segundo site.
1. Crie um *produto configurável* com dois produtos derivados. Atribua os produtos secundários a fontes e sites.
1. Atualize o primeiro produto filho para ter *qty=0* em ambas as fontes.
1. Atualize o segundo produto filho e desative-o no segundo site.
1. Fazer um reindexação completo.
1. Verifique a categoria que contém o produto configurável no segundo site.

<u>Resultados esperados</u>:

Os produtos configuráveis esgotados não estão visíveis na loja.

<u>Resultados reais</u>:

Os produtos configuráveis esgotados ficam visíveis na loja mesmo quando a opção *[!UICONTROL Display Out of Stock Products]* está desabilitada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
