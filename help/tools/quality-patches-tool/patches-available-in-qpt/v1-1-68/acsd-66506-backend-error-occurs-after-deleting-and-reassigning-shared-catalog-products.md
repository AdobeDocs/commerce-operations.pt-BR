---
title: 'ACSD-66506: Ocorre um erro de backend após a exclusão e reatribuição de produtos do Catálogo compartilhado'
description: Aplique o patch ACSD-66506 para corrigir o problema do Adobe Commerce em que o back-end lança o erro *O produto solicitado não existe. Verifique o produto e tente novamente* após excluir os produtos atribuídos anteriormente e atribuir novos a um Catálogo compartilhado.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506: Ocorre um erro de backend após a exclusão e reatribuição de produtos do Catálogo compartilhado

O patch ACSD-66506 corrige o problema em que o back-end lança o erro *O produto solicitado não existe. Verifique o produto e tente novamente* depois de excluir os produtos atribuídos anteriormente e atribuir novos a um Catálogo compartilhado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66506. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Após excluir os produtos atribuídos anteriormente e atribuir novos produtos a um **[!UICONTROL Shared Catalog]**, o back-end retorna o seguinte erro: *O produto solicitado não existe. Verifique o produto e tente novamente*

<u>Etapas a serem reproduzidas</u>:

1. Criar alguns produtos usando o kit de ferramentas de desempenho: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Vá para a Configuração de **[!UICONTROL [!DNL B2B] Features]** e Defina **[!UICONTROL Enable Company]** e **[!UICONTROL Enable Shared Catalog]** como `Yes`.
1. Crie um novo Catálogo compartilhado.
1. Atribua todos os produtos gerados ao Catálogo compartilhado recém-criado.
1. Use **[!UICONTROL Product Import]** para excluir um produto atribuído ao Catálogo Compartilhado.
   1. Exportar um produto filtrado por SKU.
   1. Selecione **[!UICONTROL Import Behavior: Delete]** e importe o mesmo arquivo.
1. Abra o **[!UICONTROL Shared Catalog]** e configure os preços e a estrutura.
   1. Selecione **[!UICONTROL Set Pricing and Structure]**.
   1. Clique em **[!UICONTROL Next]** e depois em **[!UICONTROL Generate Catalog]**.
   1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

Nenhum erro ocorre e os produtos permanecem no Catálogo compartilhado mesmo se ocorrer um erro.

<u>Resultados reais</u>:

Erro: *O produto solicitado não existe. Verifique o produto e tente novamente*, e todos os produtos serão removidos do Catálogo Compartilhado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
