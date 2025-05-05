---
title: 'ACSD-62428: erros de status de estoque no índice de pesquisa do catálogo'
description: Aplique o patch ACSD-62428 para corrigir o problema em que o valor "is_out_of_stock" no índice de pesquisa do catálogo é definido incorretamente quando o SKU não é um atributo pesquisável.
feature: Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 633aa46886d65f45e8b503e3892e47bb24e40fc0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428: erros de status de estoque no índice de pesquisa do catálogo

O patch ACSD-62428 corrige o problema em que `is_out_of_stock` valores no índice de pesquisa do catálogo são definidos como um valor incorreto quando o atributo SKU não é definido como pesquisável. Este patch está disponível com o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. A ID do patch é ACSD-62428. Observe que o problema foi agendado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6-p5

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor `is_out_of_stock` no índice de pesquisa do catálogo está definido como um valor incorreto quando o SKU não está configurado como um atributo pesquisável, resultando em uma representação de estoque imprecisa.

<u>Etapas a serem reproduzidas</u>:

1. Crie um [!UICONTROL Source] e um [!UICONTROL Stock] personalizados.
1. Crie três produtos simples e atribua o inventário ao [!UICONTROL Source] personalizado. Atribua esses produtos a uma categoria.
1. Defina o *[!UICONTROL Inventory (MSI) Indexer]* como *[!UICONTROL Update on Save]* para facilitar a replicação.
1. Defina o *[!UICONTROL Source Item Status]* como *[!UICONTROL In Stock]* e atribua um *[!UICONTROL Quantity]*.
1. Salve o produto.
1. Navegue até **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e abra o atributo **[!UICONTROL SKU]**.
1. Defina *[!UICONTROL Use In]* como *[!UICONTROL No]*.
1. Altere a quantidade do produto (verifique se ela não está definida como 0).
1. Salve o produto.

<u>Resultados esperados</u>:

O valor `is_out_of_stock` reflete com precisão o status do estoque do produto, mesmo quando o SKU não é um atributo pesquisável.

<u>Resultados reais</u>:

O valor `is_out_of_stock` está definido incorretamente como 1, e o atributo SKU está ausente nos dados indexados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
