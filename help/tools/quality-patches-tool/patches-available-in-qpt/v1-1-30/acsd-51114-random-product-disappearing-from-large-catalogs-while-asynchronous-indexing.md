---
title: 'ACSD-51114: produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada'
description: Aplique o patch ACSD-51114 para corrigir o problema do Adobe Commerce Os produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51114: produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada

>[!NOTE]
>
>Este patch está obsoleto.

O patch ACSD-51114 corrige o problema de produtos aleatórios que desapareciam de catálogos grandes quando a indexação assíncrona estava ativada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 está instalado. A ID do patch é ACSD-51114. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]:página Procurar patches].Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos aleatórios desaparecem de catálogos grandes quando a indexação assíncrona está ativada.

<u>Etapas a serem reproduzidas</u>:

1. Crie um conjunto de 10 produtos.
1. Defina todos os indexadores para o modo **[!UICONTROL Update on Save]**.
1. Crie uma categoria e atribua todos os produtos a ela.
1. Desative todos os produtos.
1. Abra a categoria e verifique se não há produtos lá.
1. Defina todos os indexadores para o modo **[!UICONTROL Update on Schedule]**.
1. Defina o `DEFAULT_BATCH_SIZE` como 2 em `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Ativar produtos na seguinte ordem: 1º, 9º, 2º, 5º, 10º, 3º.
1. Execute o comando cron.
1. Abra a categoria novamente.

<u>Resultados esperados</u>:

Todos os produtos ativados são exibidos.

<u>Resultados reais</u>:

Nem todos os produtos habilitados são mostrados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
