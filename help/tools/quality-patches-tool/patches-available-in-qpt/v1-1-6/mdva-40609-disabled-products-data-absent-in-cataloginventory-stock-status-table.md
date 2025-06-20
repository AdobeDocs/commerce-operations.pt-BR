---
title: 'MDVA-40609: Dados de produtos desabilitados ausentes na tabela cataloginventory_stock_status'
description: O patch MDVA-40609 resolve o problema em que os dados de produtos desativados não são mostrados na tabela de índice "cataloginventory_stock_status", resultando na exibição de quantidades de produtos incorretas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 está instalada. A ID do patch é MDVA-40609. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
exl-id: e207ee55-b6ce-4065-bae1-2be89dcf5092
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609: Dados de produtos desabilitados ausentes na tabela cataloginventory_stock_status

O patch MDVA-40609 resolve o problema em que os dados de produtos desabilitados não são mostrados na tabela de índice `cataloginventory_stock_status`, resultando na exibição de quantidades incorretas de produtos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 está instalada. A ID do patch é MDVA-40609. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os dados de produtos desabilitados não são mostrados na tabela de índice `cataloginventory_stock_status`, o que resulta na exibição de quantidades incorretas de produtos.

<u>Pré-requisitos</u>:

O módulo de inventário está instalado.

<u>Etapas a serem reproduzidas</u>:

1. Configure dois sites com lojas e visualizações de loja.
1. Criar uma fonte e um estoque adicionais.
1. Adicione um produto simples:
   * Defina Habilitar Produto para *Não*.
   * Atribua duas origens com Status do Item Source = Instock e Qtd. maior que zero.
1. Salve o produto.
1. Verifique a guia **Quantidade de Produtos Vendidos**.

<u>Resultados esperados</u>:

Ambos os estoques inseriram valores maiores que zero.

<u>Resultados reais</u>:

Um estoque tem valor zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
