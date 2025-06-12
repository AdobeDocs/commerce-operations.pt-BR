---
title: 'ACSD-51528: comportamentos diferentes na formatação de snake_case'
description: Aplique o patch ACSD-51528 para corrigir o problema do Adobe Commerce em que há comportamentos diferentes na formatação de snake_case.
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528: comportamentos diferentes na formatação de snake_case

O patch ACSD-51528 corrige comportamentos diferentes na formatação de snake_case. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-51528. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os diferentes comportamentos na formatação de snake_case.

<u>Etapas a serem reproduzidas</u>:

1. Teste a função `\Magento\Framework\Api\DataObjectHelper::populateWithArray` com uma variedade de nomes de propriedades diferentes.
1. As propriedades com nomes como *NewPName* devem ser transformadas em *new_p_name*, em vez disso, estão sendo transformadas em *new_pname*.
1. Além disso, ao usar a função *getNewPName* no objeto, *null* será retornado porque o *Abstract model* transformará corretamente a chamada para *new_p_name*, tornando ambas as funções incompatíveis entre si.

<u>Resultados esperados</u>

A função **[!UICONTROL populateWithArray]** deve transformar as propriedades de objeto em snake_case corretamente, tornando-a compatível com **[!DNL AbstractModel's]** `Getters` e `Setters`.

<u>Resultados reais</u>

Ao usar a função **[!UICONTROL populateWithArray]**, qualquer propriedade de objeto que contenha duas ou mais letras maiúsculas em uma linha em seu nome fará com que a transformação snake_case fique incorreta na matriz de dados final.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
