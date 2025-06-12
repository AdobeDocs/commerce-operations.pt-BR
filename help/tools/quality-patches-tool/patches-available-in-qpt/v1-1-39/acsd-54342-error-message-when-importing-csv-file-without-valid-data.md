---
title: 'ACSD-54342: Mensagem de erro ao importar arquivo CSV sem dados válidos'
description: Aplique o patch ACSD-54342 para corrigir o problema do Adobe Commerce em que ocorre uma mensagem de erro incorreta ao importar um arquivo CSV sem dados válidos.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 34324a18-45af-462b-a6e6-6b6a02d4d331
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54342: Mensagem de erro ao importar arquivo CSV sem dados válidos

O patch ACSD-54342 corrige o problema em que uma mensagem de erro incorreta ocorre ao importar um arquivo CSV sem dados válidos. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.39 está instalado. A ID do patch é ACSD-54342. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma mensagem de erro incorreta ocorre ao importar um arquivo CSV sem dados válidos.

<u>Etapas a serem reproduzidas</u>:

1. Crie um arquivo de importação somente com dados inválidos (Exemplos: [!DNL SKUs] que não existem, campos de endereço de cliente inválidos ou endereços de email de cliente malformados).
1. Importe o arquivo, selecionando para ignorar os erros de validação.

<u>Resultados esperados</u>:

A validação falha com a mensagem `There are no valid rows to import`.

<u>Resultados reais</u>:

A validação foi aprovada, mas a importação falhou com a mensagem `Error in data structure: values are mixed`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
