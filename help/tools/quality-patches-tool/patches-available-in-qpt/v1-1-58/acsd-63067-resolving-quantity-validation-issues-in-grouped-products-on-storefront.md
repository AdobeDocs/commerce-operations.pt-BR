---
title: 'ACSD-63067: Resolução de problemas de validação de quantidade em produtos agrupados na loja'
description: Aplique o patch ACSD-63067 para corrigir o problema do Adobe Commerce em que todas as quantidades de produtos em produtos agrupados são incorretamente destacadas como inválidas quando apenas um produto tem uma quantidade incorreta.
feature: Storefront
role: Admin, Developer
exl-id: a497f2c4-8bf0-41da-955a-a58e79f09c08
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067: Resolução de problemas de validação de quantidade em produtos agrupados na loja

O patch ACSD-63067 corrige o problema em que todas as quantidades de produtos em produtos agrupados são destacadas incorretamente como inválidas quando apenas um produto tem uma quantidade incorreta. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63067. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Em produtos agrupados, uma quantidade inválida em um dos subprodutos faz com que todas as quantidades sejam destacadas incorretamente como inválidas. Além disso, uma mensagem de validação é exibida para todos os produtos, em vez de apenas para aquele com a quantidade inválida.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo produto agrupado com pelo menos dois produtos simples como opções.
1. Abra o produto na loja.
1. Informe uma quantidade inválida (Por Exemplo: -1) para uma das opções e uma quantidade válida (Por Exemplo: 1) para as opções restantes.
1. Clique em **[!UICONTROL Add to Cart]**.

<u>Resultados esperados</u>:

Somente o produto com a quantidade inválida é destacado como inválido.

<u>Resultados reais</u>:

Todas as quantidades de produtos são destacadas como inválidas, e a mensagem *Especifique a quantidade de produto(s). é exibido para todos os produtos*.


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
