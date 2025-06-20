---
title: 'ACSD-50512: erro ao atualizar a data de início de uma atualização de preparo de produto baixável'
description: Aplique o patch ACSD-51892 para corrigir o problema de desempenho do Adobe Commerce em que o erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*; isso ocorre ao atualizar a data de início de uma atualização de preparo de produto para download.
feature: Products, Staging
role: Admin
exl-id: 9c3b4d45-c500-46a7-8679-a8aa9e0a66d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512: erro ao atualizar a data de início da atualização de preparo do produto baixável

O patch ACSD-50512 corrige o problema em que o erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*, que ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51502. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*, que ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto para download, com *links para download* e *links de exemplo*.
1. Crie uma atualização agendada para o mesmo produto e salve o produto.
1. Edite a atualização agendada pré-configurada (da etapa 2) e altere a data de início.
1. Salve a atualização programada.

<u>Resultados esperados</u>:

As alterações na atualização agendada foram salvas com êxito.

<u>Resultados reais</u>:

Você recebe o erro: *O link para download não está relacionado ao produto. Verifique o link e tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
