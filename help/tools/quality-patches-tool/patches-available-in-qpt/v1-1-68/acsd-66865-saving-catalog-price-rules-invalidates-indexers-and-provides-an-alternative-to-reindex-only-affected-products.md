---
title: 'ACSD-66865: salvar um [!UICONTROL Catalog Price Rule] invalida indexadores e fornece uma alternativa para reindexar somente produtos afetados'
description: Aplique o patch ACSD-66865 para corrigir o problema do Adobe Commerce em que salvar um [!UICONTROL Catalog Price Rules] invalida os indexadores e fornece uma alternativa para reindexar apenas os produtos afetados.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
exl-id: 68baf176-ee6e-4ba8-8a34-8adb8d1e16fe
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b0d35b91-b9b0-5983-b37c-f35bd2650b53
    internal-label: Price Indexer
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
source-wordcount: '415'
ht-degree: 0%
---
# ACSD-66865: salvar um **[!UICONTROL Catalog Price Rule]** invalida indexadores e fornece uma alternativa para reindexar somente produtos afetados

O patch ACSD-66865 corrige o problema em que salvar um **[!UICONTROL Catalog Price Rule]** invalida indexadores e fornece uma alternativa para reindexar apenas produtos afetados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66865. Observe que esse problema foi corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Salvar um **[!UICONTROL Catalog Price Rule]** faz com que todos os indexadores sejam invalidados, acionando reindexações completas em vez de reindexar somente os produtos afetados.

<u>Etapas a serem reproduzidas</u>:

1. Verifique se o cron não está em execução e se todos os indexadores estão definidos para atualização conforme agendado (exceto `customer_grid`, que pode ser atualizado ao salvar).
2. Executar uma reindexação manual completa usando o comando: `php bin/magento indexer:reindex`.
3. Verifique se todos os índices mostram o status *[!UICONTROL Ready]* com *0* itens na lista de pendências.
4. Na barra lateral Admin, vá para **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**. Crie uma regra de preço de catálogo ativa para um único produto (por exemplo, usando uma condição de *SKU*).
5. Execute o comando: `php bin/magento indexer:status` para verificar o status do indexador.
6. Observe que vários índices são marcados como **[!UICONTROL Reindex Required]** mesmo que apenas um produto seja afetado.

<u>Resultados esperados</u>:

Somente os dados do produto afetado são identificados, e um reindexação parcial é acionado em vez de um reindexação completo em todos os indexadores.

<u>Resultados reais</u>:

Uma reindexação completa é acionada para todos os indexadores, mesmo quando apenas um único produto é afetado pelo **[!UICONTROL Catalog Price Rule]**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
