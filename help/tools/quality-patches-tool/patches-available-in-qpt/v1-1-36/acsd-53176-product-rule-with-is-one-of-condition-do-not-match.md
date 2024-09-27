---
title: '"ACSD-53176: a regra de produto com a condição "é um de" não corresponde"'
description: Aplique o patch ACSD-53176 para corrigir o problema do Adobe Commerce em que a condição "Produtos para correspondência" da regra de produto relacionada "é um de" não funciona corretamente para "Produtos para correspondência".
feature: Marketing Tools
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176: A regra de produto com a condição `is one of` não corresponde

O patch ACSD-53176 corrige o problema em que a condição `is one of` da regra de produto relacionada não funciona corretamente para **Produtos a serem correspondidos**. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. A ID do patch é ACSD-53176. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A condição `is one of` da regra de produto relacionada não funciona corretamente para **Produtos a serem Correspondidos**.

<u>Etapas a serem reproduzidas</u>:

1. Crie de 3 a 4 produtos.
1. Crie uma nova regra de produto relacionada.

   Defina a regra para corresponder a dois ou mais produtos:
   * `SKU is one of "S1,S2".`

   Defina a regra para exibir dois ou mais itens:
   * `Product SKU is one of constant value "S2,S3".`

1. Abra o produto S1 na Loja.

<u>Resultados esperados</u>:

Os produtos relacionados &quot;S2&quot; e &quot;S3&quot; são exibidos nas páginas de produto &quot;S1&quot; e &quot;S2&quot;.

<u>Resultados reais</u>:

Os produtos relacionados não são exibidos nas páginas do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
