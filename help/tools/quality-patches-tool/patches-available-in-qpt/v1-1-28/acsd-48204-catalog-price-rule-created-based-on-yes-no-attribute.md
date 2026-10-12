---
title: 'ACSD-48204: a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado'
description: Aplique o patch ACSD-48204 para corrigir o problema do Adobe Commerce em que a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%
---
# ACSD-48204: a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado

O patch ACSD-48204 corrige o problema em que a regra de preço do catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. A ID do patch é ACSD-48204. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites (Padrão e W2).
1. Crie um atributo de produto do tipo *Sim/Não*.
   * Conjunto [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Crie um produto configurável com base em qualquer atributo com duas variações (V1 e V2).
   * Adicionar o atributo *Sim/Não* ao conjunto de atributos de variações configuráveis
   * Para uma das variações (V1), defina o valor como *[!UICONTROL Yes]* no site não padrão (W2)
1. Criar uma regra de catálogo:
   * Aplicado a ambos os sites
   * Condição: *Sim/Não* o valor do atributo é *[!UICONTROL Yes]*
   * Desconto = 50%
1. Abra o produto configurável no site fora do padrão (W2).
1. Verifique se a variação V1 tem o desconto de 50% aplicado.
1. Abra a variação V1 no Administrador do Adobe Commerce.
   * Alternar para o site padrão
   * Não fazer alterações e salvar o produto
1. Atualize a página inicial da loja de produtos configurável.

<u>Resultados esperados</u>:

A variação V1 ainda tem o desconto de 50% aplicado, pois nenhuma alteração foi feita.

<u>Resultados reais</u>:

O desconto desaparece.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
