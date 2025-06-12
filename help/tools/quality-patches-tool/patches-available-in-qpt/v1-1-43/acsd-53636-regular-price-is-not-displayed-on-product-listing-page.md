---
title: 'ACSD-53636: o preço normal não é exibido na página [!UICONTROL Product Listing]'
description: Aplique o patch ACSD-53636 para corrigir o problema do Adobe Commerce em que o preço normal não é exibido nas páginas *[!UICONTROL Product Listing]* para produtos configuráveis que têm produtos secundários com preços especiais.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636: o preço normal não é exibido na página *[!UICONTROL Product Listing]*

O patch ACSD-53636 corrige o problema em que o preço normal não é exibido em *[!UICONTROL Product Listing]* páginas para produtos configuráveis que têm produtos secundários com preços especiais. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 está instalado. A ID do patch é ACSD-53636. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O preço normal não é exibido em *[!UICONTROL Product Listing]* páginas para produtos configuráveis que têm produtos filho com preços especiais.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no administrador do e acesse **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**, e crie ou abra qualquer produto configurável.
2. Abra o produto filho e adicione um preço especial a todos ou a um dos produtos filhos e salve o produto.
3. Vá para o front-end e abra a página **[!UICONTROL Product Detail]** do produto configurável; nas amostras do produto filho com preço especial, você verá o *[!UICONTROL Regular price]* riscado (esperado).
4. Vá para o front-end e abra a página **[!UICONTROL Product Listing]** do produto configurável com preço especial; veja que as alterações da amostra de produto configurável não exibem o preço normal, ao contrário do *[!UICONTROL Product Detail Page]* e de outros produtos simples.

<u>Resultados esperados</u>:

Na página *[!UICONTROL Product Listing]*, o produto configurável mostra o preço normal do produto filho.

<u>Resultados reais</u>:

Na página *[!UICONTROL Product Listing]*, o produto configurável não mostra o preço normal de seu produto filho.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
