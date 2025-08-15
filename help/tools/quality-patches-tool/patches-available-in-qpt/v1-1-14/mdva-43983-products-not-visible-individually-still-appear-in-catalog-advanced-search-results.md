---
title: 'MDVA-43983: Produtos definidos como "Não visível individualmente" aparecem nos resultados da pesquisa'
description: O patch MDVA-43983 resolve o problema em que os produtos definidos como "Não visível individualmente" ainda aparecem nos resultados da pesquisa avançada do catálogo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 está instalada. A ID do patch é MDVA-43983. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983: Produtos definidos como &quot;Não visível individualmente&quot; aparecem nos resultados da pesquisa

O patch MDVA-43983 resolve o problema em que os produtos definidos como &quot;Não visível individualmente&quot; ainda aparecem nos resultados da pesquisa avançada do catálogo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 está instalada. A ID do patch é MDVA-43983. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos definidos como &quot;Não visível individualmente&quot; ainda aparecem nos resultados da pesquisa avançada do catálogo.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo com **Tipo de Entrada de Catálogo para o Proprietário da Loja** como **Suspenso** ou **Amostra Visual** (por exemplo, Cor).
1. Defina **Usar na Pesquisa** como **Sim** e **Visível na Pesquisa Avançada** como **Sim**.
1. Adicione algumas opções de atributo.
1. Crie produtos com **Visibilidade** como **Não visível individualmente**.
1. Atribuir opções de atributo de cor.
1. Vá para a página **Pesquisa avançada de catálogo** na vitrine.
1. Selecione somente a opção Atributo de cor no campo Atributo de cor e deixe o restante dos campos em branco ou como estão.
1. Envie um formulário de pesquisa avançada.
1. Observe os resultados da pesquisa.

<u>Resultados esperados</u>:

Os produtos definidos como &quot;Não visível individualmente&quot; não aparecem nos resultados da pesquisa avançada do catálogo.

<u>Resultados reais</u>:

Os produtos definidos como &quot;Não visível individualmente&quot; aparecem nos resultados da pesquisa avançada do catálogo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
