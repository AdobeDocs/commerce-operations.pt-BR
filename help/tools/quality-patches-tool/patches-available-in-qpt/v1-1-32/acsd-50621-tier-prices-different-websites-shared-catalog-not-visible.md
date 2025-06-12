---
title: 'ACSD-50621: os preços de nível para diferentes sites no catálogo compartilhado não estão visíveis'
description: Aplique o patch ACSD-50621 para corrigir o problema do Adobe Commerce, em que os preços de camada para sites diferentes no catálogo compartilhado não estão visíveis ao editá-los em um ambiente de vários sites.
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621: os preços de nível para diferentes sites no catálogo compartilhado não estão visíveis

O patch ACSD-50621 corrige o problema em que os preços de nível para sites diferentes no catálogo compartilhado não estão visíveis ao editá-los em um ambiente de vários sites. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-50621. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os preços de nível para diferentes sites no catálogo compartilhado não ficam visíveis ao editá-los em um ambiente de vários sites.

<u>Etapas a serem reproduzidas</u>:

1. Defina o **[!UICONTROL Catalog Price Scope]** como **[!UICONTROL Website]**.
1. Crie um site, loja e loja adicionais.
1. Crie um produto simples e o atribua a todos os sites.
1. Crie um catálogo compartilhado personalizado.
1. Vá para **[!UICONTROL Set Pricing and Structure]** para obter o catálogo compartilhado personalizado que você criou.
1. Na Etapa 1: selecione produtos para catálogo. Adicione o produto simples que você criou.
1. Na etapa 2: defina preços personalizados e clique em **[!UICONTROL Configure]**.
1. Defina preços de camada diferentes para sites diferentes.
1. Selecione **[!UICONTROL Done]**, clique em **[!UICONTROL Generate Catalog]** e em **[!UICONTROL Save]**.
1. Execute o cron.
1. Navegue até **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** e verifique o preço da camada.

<u>Resultados esperados</u>:

Todos os preços de camada configurados anteriormente para diferentes sites estão presentes.

<u>Resultados reais</u>:

Os preços de nível que foram configurados anteriormente não estão presentes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
