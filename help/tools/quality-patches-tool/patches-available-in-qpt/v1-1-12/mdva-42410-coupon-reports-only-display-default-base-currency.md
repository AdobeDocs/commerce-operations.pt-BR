---
title: 'MDVA-42410: os relatórios de cupom exibem somente a moeda base padrão'
description: O patch MDVA-42410 corrige o problema em que os relatórios de cupom exibem apenas a moeda base. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-42410. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Orders
role: Admin
exl-id: 97b4d9cf-12fd-4659-ad71-914c8422da37
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42410: os relatórios de cupom exibem somente a moeda base padrão

O patch MDVA-42410 corrige o problema em que os relatórios de cupom exibem apenas a moeda base. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-42410. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os relatórios de cupom exibem somente a moeda base padrão.

<u>Etapas a serem reproduzidas</u>:

1. Crie um Site, Loja e Exibição de Loja adicionais.
1. Defina uma moeda diferente para este novo site. Por exemplo, Euro.
1. Acesse **Lojas** > **Taxas de Moeda** e configure as taxas de moeda para **Euro**.
1. Crie uma **Regra de Preço do Carrinho** com um cupom específico - **Teste**.
1. Acesse o front-end e faça um pedido com o cupom **Test** no novo site.
1. Vá para **Relatórios** > **Vendas** > **Cupons**.
1. Selecione o novo site na lista suspensa Escopo.
1. Atualizar estatísticas e executar relatórios.

<u>Resultados esperados</u>:

Os relatórios de cupom exibem a moeda do novo site como Euro.

<u>Resultados reais</u>:

A moeda base padrão (USD, neste caso) é usada em relatórios de cupom para o novo site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
