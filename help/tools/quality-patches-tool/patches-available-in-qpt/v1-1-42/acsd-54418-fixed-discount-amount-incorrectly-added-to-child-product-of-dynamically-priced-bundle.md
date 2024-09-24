---
title: "ACSD-54418: valor de desconto fixo adicionado incorretamente ao produto filho de pacote com preço dinâmico"
description: Aplique o patch ACSD-54418 para corrigir o problema do Adobe Commerce em que o valor fixo do desconto é aplicado incorretamente a cada produto filho do pacote com preço dinâmico.
feature: Shopping Cart
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-54418: valor de desconto fixo adicionado incorretamente ao produto filho do pacote com preço dinâmico.

O patch ACSD-54418 corrige o problema em que o valor fixo do desconto é aplicado incorretamente a cada produto filho do pacote com preço dinâmico. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.42 está instalado. A ID do patch é ACSD-54418. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor do desconto fixo é aplicado incorretamente a cada produto filho do pacote com preço dinâmico.

<u>Etapas a serem reproduzidas</u>:

1. Crie um **[!UICONTROL bundle product]** com preços dinâmicos e *2* opções de pacote.
1. Crie um **[!UICONTROL cart price rule]** com um código de cupom específico que se aplique apenas ao produto agrupado **[!UICONTROL SKU]** e que tenha um desconto fixo.
1. Adicione o produto incluído ao carrinho.
1. Aplicar o **[!UICONTROL coupon code]**.
1. Marque o desconto aplicado ao carrinho de compras.

<u>Resultados esperados</u>:

O desconto é aplicado apenas uma vez a todo o produto agrupado.

<u>Resultados reais</u>:

O desconto é aplicado a cada produto filho do pacote.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
