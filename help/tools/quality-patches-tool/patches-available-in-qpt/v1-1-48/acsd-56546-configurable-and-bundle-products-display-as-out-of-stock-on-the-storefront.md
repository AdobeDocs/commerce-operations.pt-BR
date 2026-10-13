---
title: 'ACSD-56546: os produtos configuráveis e empacotados são exibidos como esgotados na loja'
description: Aplique o patch ACSD-56546 para corrigir o problema do Adobe Commerce em que os produtos configuráveis e de pacote são exibidos como esgotados na loja quando a opção de configuração *[!UICONTROL Display Out of Stock Products]* está desabilitada.
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%
---
# ACSD-56546: os produtos configuráveis e empacotados são exibidos como esgotados na loja

O patch ACSD-56546 corrige o problema em que os produtos configuráveis e empacotados são exibidos como esgotados na loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. A ID do patch é ACSD-56546. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
