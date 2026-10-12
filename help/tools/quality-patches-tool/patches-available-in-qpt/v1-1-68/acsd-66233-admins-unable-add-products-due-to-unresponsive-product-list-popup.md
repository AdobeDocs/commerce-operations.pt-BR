---
title: 'ACSD-66233: Os administradores não conseguem adicionar produtos devido ao pop-up de lista de produtos sem resposta'
description: Aplique o patch ACSD-66233 para corrigir o problema do Adobe Commerce em que os administradores não podem adicionar produtos às categorias porque o pop-up [!UICONTROL Add Product] no Visual Merchandiser é carregado indefinidamente.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
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
source-wordcount: '377'
ht-degree: 0%
---
# ACSD-66233: Administradores incapazes de adicionar produtos devido à pop-up de lista de produtos sem resposta

O patch ACSD-66233 corrige um problema em que os administradores não conseguem adicionar produtos a categorias porque o pop-up [!UICONTROL Add Product] no Visual Merchandiser é carregado indefinidamente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66233. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problema em que o pop-up [!UICONTROL Add Product] no Visual Merchandiser é carregado indefinidamente, impedindo que administradores adicionem produtos a categorias.

<u>Etapas a serem reproduzidas</u>:

1. Instale e habilite os módulos de inventário.
1. Crie um grande número de origens de inventário (por exemplo, 700).
1. Crie vários estoques de inventário (por exemplo, 12) e atribua as origens de inventário a eles.
1. Crie alguns produtos e atribua-os às origens de inventário.
1. Crie uma categoria.
1. Expanda a seção [!UICONTROL Products in Category].
1. Clique no botão [!UICONTROL Add Product].
1. Observe a janela pop-up com a lista de produtos.

<u>Resultados esperados</u>:

A lista de produtos é carregada no pop-up dentro de um tempo razoável.

<u>Resultados reais</u>:

O pop-up é carregado indefinidamente e não exibe a lista de produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
