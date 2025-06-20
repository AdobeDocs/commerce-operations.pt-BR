---
title: 'ACSD-63574: Adicionar a listagem [!UICONTROL Bundle Product] ao bloqueio via [!DNL Page Builder]  resulta em erro'
description: Aplique o patch ACSD-63574 para corrigir o problema do Adobe Commerce em que adicionar **[!UICONTROL Bundle Product]** com as opções "Caixa de seleção" ou "Multisseleção" a um bloco via [!DNL Page Builder]  resulta em um erro.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574: Adicionar a listagem [!UICONTROL Bundle Product] ao bloqueio via [!DNL Page Builder] resulta em erro

O patch ACSD-63574 corrige o problema em que a adição de **[!UICONTROL Bundle Product]** com `Checkbox` ou `Multi Select` opções a um bloco via [!DNL Page Builder] resulta em um erro. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-63574. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4-p10

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao adicionar **[!UICONTROL Bundle Product]** a um bloco usando [!DNL Page Builder], a visualização do widget do produto é interrompida e mostra a mensagem de erro *Ocorreu um erro ao gerar este conteúdo*. Esse problema ocorre especificamente quando o produto do pacote inclui os tipos de opção `Checkbox` ou `Multi Select` e `indexer dimension mode` está definido como `website_and_customer_group`. O log de exceções mostra o seguinte erro:

    &quot;
    report.CRITICAL: PDOException: SQLSTATE[42S02]: Tabela ou exibição base não encontrada: 1146 A tabela &#39;db_name.catalog_product_index_price_cg0_ws0&#39; não existe em /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    &quot;

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Catalog]** e selecione **[!UICONTROL Catalog]** nas opções abaixo.
1. Role para baixo até a seção **[!UICONTROL Price]** e defina **[!UICONTROL Catalog Price Scope]** como **[!UICONTROL Global]**.
1. Defina `Indexer dimension mode` como `website_and_customer_group` usando o comando abaixo:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. Crie um **[!UICONTROL Bundle Product]** com um tipo de opção de pacote `Checkbox` ou `Multi Select` e atribua o produto a uma categoria.
1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**.
1. Selecione a categoria à qual o produto criado está atribuído e tente **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

Produto adicionado sem erros.

<u>Resultados reais</u>:

Não é possível adicionar um produto por meio de [!DNL Page Builder] quando o tipo de opção **[!UICONTROL Bundle Product]** é `Checkbox` ou `Multi Select` e `indexer dimension mode` está definido como `website_and_customer_group`. Ele emite o erro: *Ocorreu um erro ao gerar este conteúdo*.


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
