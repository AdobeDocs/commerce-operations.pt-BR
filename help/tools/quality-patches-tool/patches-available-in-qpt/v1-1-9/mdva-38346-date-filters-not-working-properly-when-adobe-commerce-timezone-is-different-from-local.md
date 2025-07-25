---
title: 'MDVA-38346: Filtros de data não funcionam quando o fuso horário do Adobe Commerce é diferente do local'
description: O patch MDVA-38346 resolve o problema em que os filtros de data não estão funcionando corretamente quando o fuso horário do Adobe Commerce é diferente do fuso horário do ambiente local. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-38346. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Configuration
role: Admin
exl-id: 6ed909be-81da-4e06-97c7-4eab8be2ddd2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38346: Filtros de data não funcionam quando o fuso horário do Adobe Commerce é diferente do local

O patch MDVA-38346 resolve o problema em que os filtros de data não estão funcionando corretamente quando o fuso horário do Adobe Commerce é diferente do fuso horário do ambiente local. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-38346. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1, 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os filtros de data não estão funcionando corretamente quando o fuso horário do Adobe Commerce é diferente do fuso horário do ambiente local.

<u>Etapas a serem reproduzidas</u>:

1. Altere o fuso horário para Austrália/Sydney.
1. Faça alguns pedidos.
1. Crie faturas para eles.
1. Vá para **Vendas** > **Faturas** e filtre por Data da Fatura (data atual - data atual).
1. Verifique as datas.

<u>Resultados esperados</u>:

A data da fatura exibida e o filtro real correspondem.

<u>Resultados reais</u>:

A data da fatura exibida está um dia antes do filtro real (data atual + 1 dia).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
