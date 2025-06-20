---
title: 'MDVA-43726: Falha na aplicação da regra de preço do catálogo após reindexação parcial'
description: O patch MDVA-43726 corrige o problema em que a regra de preço do catálogo com base na correspondência de atributos no nível do armazenamento falha ao ser aplicada após a reindexação parcial. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-43726. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
exl-id: db536749-eb89-4bb5-9c69-f448f74497b8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726: Falha na aplicação da regra de preço do catálogo após reindexação parcial

O patch MDVA-43726 corrige o problema em que a regra de preço do catálogo com base na correspondência de atributos no nível do armazenamento falha ao ser aplicada após a reindexação parcial. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-43726. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de preço do catálogo com base na correspondência de atributo de nível de armazenamento não é aplicada após a reindexação parcial.

<u>Etapas a serem reproduzidas</u>:

1. Defina o modo do indexador para ser executado de acordo com a programação.
1. Crie dois atributos de produto configuráveis. Por exemplo: Cor (amostra visual) e Tamanho (amostra de texto).
1. Crie um produto configurável usando ambos os atributos criados na Etapa 2.
1. Depois de criar os produtos, crie um atributo de tipo **Sim/Não** e torne-o visível nas condições da regra.
1. Adicionar este atributo ao conjunto de atributos padrão.
1. Crie uma regra de preço de catálogo a ser aplicada quando este atributo for definido como **Sim**.
1. Abra um dos produtos simples relacionados ao produto configurável.
1. Altere o escopo para exibição de armazenamento e atualize o valor do atributo para **Sim**.
1. Execute o `CRON` e verifique o preço no front-end.
1. Executar uma reindexação completa. Novamente, verifique o preço no front-end.
1. Atualize a categoria de produto configurável.
1. Execute o `CRON` e verifique o preço novamente no front-end.

<u>Resultados esperados</u>:

A regra do catálogo se aplica corretamente sem uma reindexação completa usando indexadores incrementais.

<u>Resultados reais</u>:

A regra de catálogo não se aplica sem executar um reindex completo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
