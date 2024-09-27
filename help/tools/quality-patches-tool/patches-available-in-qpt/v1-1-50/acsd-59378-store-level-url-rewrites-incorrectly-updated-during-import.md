---
title: "ACSD-59378: nível de armazenamento [!DNL URL] regravações incorretamente atualizadas durante a importação"
description: Aplique o patch ACSD-59378 para corrigir o problema do Adobe Commerce em que as regravações no nível da loja  [!DNL URL]  são atualizadas incorretamente durante a importação.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59378: regravações no nível de armazenamento [!DNL URL] atualizadas incorretamente durante a importação

O patch ACSD-59378 corrige o problema em que as substituições [!DNL URL] no nível de armazenamento são atualizadas incorretamente durante a importação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 está instalado. A ID do patch é ACSD-59378. Observe que esse problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5x (todas as versões da 2.4.5)

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As substituições no nível de repositório [!DNL URL] foram atualizadas incorretamente durante a importação.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com `url_key = key_default` no escopo **Todas as Exibições de Loja**.
1. Defina `url_key = key_store` no escopo **Exibição de Repositório Padrão**.
1. Exporte o produto.
1. Importe um arquivo [!DNL CSV] para este produto com os seguintes dados:
   * A coluna `store_view_code` está definida como *vazia* para que se aplique ao escopo **Todas as Exibições de Repositório**.
   * `url_key` está definido como a chave padrão *`key_default`*.

<u>Resultados Esperados</u>:

[!DNL URL] regravações são apenas regeneradas para exibições de armazenamento onde não há `url_key` substituído (onde o padrão `url_key` se aplica).

<u>Resultados Reais</u>:

`key_store` [!DNL URL] regravações foram excluídas, mas a regravação de [!DNL URL] no nível **Exibição de Loja Padrão** do produto ainda está definida como *`key_store`*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
