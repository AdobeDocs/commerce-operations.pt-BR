---
title: 'ACSD-53118: as regras do carrinho com cupom não funcionam corretamente'
description: Aplique o patch ACSD-53118 para corrigir o problema do Adobe Commerce em que a regra de preço do carrinho é aplicada usando um código de cupom enquanto o produto no carrinho tem um atributo correspondente vazio.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 8957790e-c22b-4a25-939b-94d7a9fb1cc7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53118: as regras do carrinho com cupom não funcionam corretamente

O patch ACSD-53118 corrige o problema em que a regra de preço do carrinho é aplicada usando um código de cupom, enquanto o produto no carrinho tem um atributo correspondente vazio. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41 está instalado. A ID do patch é ACSD-53118. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de preço do carrinho é aplicada usando um código de cupom, enquanto o produto no carrinho tem um atributo correspondente vazio.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo de preço e adicione-o ao conjunto de atributos. Tornar o atributo utilizável em condições de regra promocional.
1. Crie um produto e deixe o novo atributo vazio.
1. Crie uma regra de preço do carrinho com um cupom específico e a seguinte condição:

   * Se um item for ENCONTRADO no carrinho com TODAS essas condições true: Attribute1 é 0.

1. Adicione o produto criado na Etapa 2 ao carrinho.
1. Use o código do cupom para a regra do carrinho criada na Etapa 3.

<u>Resultados esperados</u>:

O desconto não é aplicado ao carrinho de compras.

<u>Resultados reais</u>:

O desconto é aplicado ao carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
