---
title: 'MDVA-43731: Os sinônimos de pesquisa não funcionam quando o valor é adicionado em "Termos mínimos para correspondência"'
description: O patch MDVA-43731 corrige o problema em que os Sinônimos de pesquisa param de funcionar quando um valor é adicionado em "Termos mínimos para correspondência". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-43731. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%
---
# MDVA-43731: Os sinônimos de pesquisa não funcionam quando o valor é adicionado em &quot;Termos mínimos para correspondência&quot;

O patch MDVA-43731 corrige o problema em que os Sinônimos de pesquisa param de funcionar quando um valor é adicionado em &quot;Termos mínimos para correspondência&quot;. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-43731. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os Sinônimos de pesquisa param de funcionar quando um valor é adicionado em &quot;Termos mínimos para correspondência&quot;.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com dados de amostra.
1. Configure o Elasticsearch7 como mecanismo de pesquisa.
1. Procure a palavra &quot;Jaqueta&quot;. Uma lista de produtos será exibida.
1. Adicione o parâmetro [4&lt;60%] em **Configuração** > **Catálogo** > **Pesquisa de Catálogo** > **Termos Mínimos para Correspondência**.
1. Limpe o cache de configuração e faça uma reindexação.
1. Pesquise novamente a palavra &quot;Jacket&quot; e observe que uma lista de produtos é exibida.
1. Vá para **Marketing** > **SEO e Pesquisa** > **Pesquisar Sinônimos**.
1. Crie Sinônimos de Pesquisa adicionando os seguintes sinônimos: jaqueta, bagtecs, express plus.
1. Faça uma reindexação.
1. Faça uma pesquisa de produto usando qualquer um dos sinônimos. Por exemplo, jaqueta.

<u>Resultados esperados</u>:

Você obtém a mesma lista de produtos de antes nos resultados da pesquisa.

<u>Resultados reais</u>:

Nenhum produto é mostrado nos resultados da pesquisa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
