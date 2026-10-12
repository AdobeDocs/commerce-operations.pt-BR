---
title: 'ACSD-66952: o cache é limpo em cada PLP ou visita ao carrinho quando uma regra de destino é definida'
description: Aplique o patch ACSD-66952 para corrigir o problema do Adobe Commerce em que o cache foi limpo em cada PLP ou visita ao carrinho, causando sobrecarga desnecessária de desempenho, quando uma regra de destino foi definida.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '387'
ht-degree: 0%
---
# ACSD-66952: o cache é limpo em cada PLP ou visita ao carrinho quando uma regra de destino é definida

O patch ACSD-66952 corrige o problema em que o cache é limpo em cada PLP ou visita ao carrinho, causando sobrecarga de desempenho quando uma regra de destino é definida. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-66952. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problema em que o cache é limpo em cada PLP ou visita de carrinho, causando sobrecarga de desempenho quando uma regra de destino é definida.

<u>Etapas a serem reproduzidas</u>:

1. Gere um pequeno conjunto de dados de amostra.
1. Crie valores de regra de destino conforme abaixo:
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *Produtos relacionados*
      * **[!UICONTROL Status]** = *Ativo*
      * **[!UICONTROL Apply to]** = *Produtos relacionados*
   1. **[!UICONTROL Products to Match]**
      * Deixe no seu valor padrão.
   1. **[!UICONTROL Products to Display]**
      * Se **ALL** dessas condições forem *true*, defina **[!UICONTROL Product Category]** = *Valor Constante 11111*
1. Comece a monitorar os logs para solicitações de invalidação de cache.
1. Visite a página do produto.
1. Adicione um produto ao carrinho e navegue até a página do carrinho.

<u>Resultados esperados</u>:

O aplicativo não deve invalidar o cache durante a navegação no site.

<u>Resultados reais</u>:

As tags de cache são invalidadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas
