---
title: 'MDVA-44044: produto não exibido na página de categoria depois de atribuído ao novo site'
description: O patch MDVA-44044 resolve o problema em que um produto não é exibido na página de categoria depois de ser atribuído a um novo site. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 está instalada. A ID do patch é MDVA-44044. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Categories, Products
role: Admin
exl-id: ae797cdc-5977-40b8-82da-ccf364466bdf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44044: produto não exibido na página de categoria depois de atribuído ao novo site

O patch MDVA-44044 resolve o problema em que um produto não é exibido na página de categoria depois de ser atribuído a um novo site. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 está instalada. A ID do patch é MDVA-44044. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto não é exibido na página de categoria depois de ser atribuído a um novo site.

<u>Etapas a serem reproduzidas</u>:

1. Defina o modo do indexador para o agendamento.
1. Crie um modo de exibição de site, loja e loja secundário.
1. Adicionar um código de armazenamento secundário em `index.php`:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Crie uma nova categoria.
1. Crie um novo produto atribuído à categoria recém-criada. Certifique-se de atribuí-lo somente ao site principal.
1. Execute o cron.
1. Abra a categoria na loja.
1. Atribua o produto ao site secundário.
1. Execute o cron novamente.

<u>Resultados esperados</u>:

O produto é exibido na página da categoria após um indexador agendado.

<u>Resultados reais</u>:

O produto não é exibido na página de categoria até que uma reindexação completa seja feita.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
