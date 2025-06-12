---
title: 'ACSD-54680: a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada'
description: Aplique o patch ACSD-54680 para corrigir o problema do Adobe Commerce em que a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada.
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680: a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada.

O patch ACSD-54680 corrige o problema em que a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.40 está instalado. A ID do patch é ACSD-54680. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** e crie duas novas fontes: **Source 1** e **Source 2**.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** e crie um novo Stock: **Stock A**, atribua-o ao site principal e atribua a ele o **Source 1** e o **Source 2**.
1. Crie um produto Simples, atribua o **Source 1** e o **Source 2** e defina a Quantidade = *2* para cada origem. (a quantidade vendável do produto deve ser *4* como resultado).
1. Crie uma Conta de Empresa.
1. Vá para **[!UICONTROL Storefront]** e faça logon na conta da empresa.
1. Adicionar o produto simples ao carrinho de compras com quantidade = *4*.
1. Abra o *[!UICONTROL Shopping cart]* e clique no botão **[!UICONTROL Request a quote]**.
1. Adicione um comentário e um nome de citação e clique no botão **[!UICONTROL Send a Request]**.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Abrir cotação enviada recentemente.

<u>Resultados esperados</u>:

Os itens cotados contêm o produto solicitado.

<u>Resultados reais</u>:

A seção da página de itens entre aspas está vazia e não é possível processar a cotação.
`var/log/system.log` contém

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
