---
title: 'ACSD-66865: salvar um [!UICONTROL Catalog Price Rule] invalida indexadores e fornece uma alternativa para reindexar somente produtos afetados'
description: Aplique o patch ACSD-66865 para corrigir o problema do Adobe Commerce em que  salvar um [!UICONTROL Catalog Price Rules] invalida os indexadores e fornece uma alternativa para reindexar somente os produtos afetados.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
