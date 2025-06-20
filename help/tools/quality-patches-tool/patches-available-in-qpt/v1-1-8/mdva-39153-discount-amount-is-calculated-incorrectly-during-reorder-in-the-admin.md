---
title: 'MDVA-39153: o valor do desconto é calculado incorretamente durante o reordenamento no Administrador'
description: O patch MDVA-39153 corrige o problema em que o valor do desconto é calculado incorretamente durante o novo pedido no Administrador. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 está instalada. A ID do patch é MDVA-39153. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153: o valor do desconto é calculado incorretamente durante o reordenamento no Administrador

O patch MDVA-39153 corrige o problema em que o valor do desconto é calculado incorretamente durante o novo pedido no Administrador. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 está instalada. A ID do patch é MDVA-39153. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor do desconto é calculado incorretamente durante o reordenamento no Administrador.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Admin** > **Lojas** > **Configuração** > **Vendas** > **Impostos**.
1. Ativar o imposto para entrega exibindo o imposto no Carrinho de Compras.
1. Habilite e configure o método de envio com taxa de tabela ($15).
1. Crie uma regra de imposto para alíquota de imposto embutida (para CA).
1. Crie uma regra de preço do carrinho com um desconto fixo de US$ 5 aplicado ao carrinho inteiro e à quantia de envio.
1. Adicione um produto com um preço de US$ 12 ao carrinho e vá para a página Carrinho de compras.
1. Aplique o desconto ao carrinho.
1. Defina o método de envio na seção &quot;estimativas&quot; como &quot;Taxa única&quot;.
1. Prossiga com o check-out até as etapas de revisão (não faça o pedido).
1. Vá para a página inicial e volte ao Carrinho de Compras.
1. Altere o método de envio na seção &quot;estimativas&quot; para &quot;Taxa de tabela&quot;.

<u>Resultados esperados</u>:

O desconto permanece o mesmo - US$ 5.

<u>Resultados reais</u>:

O desconto é de US$ 6,31.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
