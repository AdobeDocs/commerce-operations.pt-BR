---
title: 'MDVA-31763: as regras de preço do catálogo são revertidas até a reindexação manual'
description: O patch MDVA-31763 resolve o problema em que as regras de preço do catálogo são revertidas até a reindexação manual. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 está instalada. A ID do patch é MDVA-31763. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763: as regras de preço do catálogo são revertidas até a reindexação manual

O patch MDVA-31763 resolve o problema em que as regras de preço do catálogo são revertidas até a reindexação manual. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 está instalada. A ID do patch é MDVA-31763. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando o indexador parcial `catalogrule_product` é executado em produtos configuráveis, as regras de catálogo desaparecem.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no back-end do Administrador.
1. Vá para **Lojas** > **Atributos** > **Produto** e procure o atributo &quot;fabricante&quot;.
   * Adicione algumas opções e defina &quot;Usar para Condições de Regra Promocional&quot; como *Sim*.
1. Vá para **Lojas** > **Atributos** > **Conjuntos de Atributos**.
   * Selecione o conjunto de atributos padrão e adicione o atributo &quot;fabricante&quot; a ele.
1. Crie um produto configurável com algumas variações.
1. Defina o valor do atributo &quot;fabricante&quot; para o produto configurável criado anteriormente.
1. Criar regras de catálogo:
   * Ativo = Sim
   * Sites = Site Principal
   * Grupos de Clientes = NÃO CONECTADO
   * Condições: fabricante = \&lt;valor selecionado para o produto configurável>
   * Ações: Qualquer desconto
1. Fazer um índice completo.
1. Verifique o preço do produto no PDP e certifique-se de que o preço esteja correto.
1. Atualize o atributo &quot;weight&quot; do produto configurável criado.
1. Verifique o preço do produto no PDP.

<u>Resultados esperados</u>:

As regras de preço de catálogo definidas nos produtos configuráveis não são removidas durante a reindexação parcial.

<u>Resultados reais</u>:

As regras de preço de catálogo definidas em produtos configuráveis desaparecem durante a reindexação parcial.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
