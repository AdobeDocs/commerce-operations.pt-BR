---
title: "MDVA-39482: o produto sai do estoque se importado com a quantidade '0' com ordens pendentes habilitadas"
description: O MDVA-39482 corrige o problema em que o produto sai do estoque se importado com a quantidade "0" quando o MSI e os backorders estão habilitados e o Limite de Indisponibilidade é definido como um valor menos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 está instalada. A ID do patch é MDVA-39482. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482: o produto sai do estoque se importado com a quantidade &quot;0&quot; com ordens pendentes ativadas

O MDVA-39482 corrige o problema em que o produto sai do estoque se importado com a quantidade &quot;0&quot; quando o MSI e os backorders estão habilitados e o Limite de Indisponibilidade é definido como um valor menos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 está instalada. A ID do patch é MDVA-39482. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto fica indisponível se for importado com a quantidade &quot;0&quot; quando o MSI e os pedidos pendentes estiverem ativados e o Limite de indisponibilidade for definido como um valor menos.

<u>Pré-requisitos</u>:

1. O MSI e os dados de amostra devem ser instalados.
1. Ir para **Lojas** > **Configurações** > **Catálogo** > **Inventário**:
   * Definir Backorders para &quot;Permitir Qtd. Abaixo de 0&quot;
   * Definir limite de indisponibilidade para &quot;-10&quot;

<u>Etapas a serem reproduzidas</u>:

1. Verifique se o SKU está **Em Estoque** e se tem a quantidade **24-MB01**.
1. Importe o CSV das origens de estoque. Certifique-se de selecionar &quot;Fontes de estoque&quot; em Tipo de entidade:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Verifique o status do estoque do produto após a importação das Fontes de estoque.

<u>Resultados esperados</u>:

24-MB01 está **No Estoque** na Loja.

<u>Resultados reais</u>:

24-MB01 está **Sem Estoque** na Loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
