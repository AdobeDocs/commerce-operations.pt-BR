---
title: 'ACSD-51890: o botão [!UICONTROL Submit review] pode ser clicado várias vezes'
description: Aplique o patch ACSD-51890 para corrigir o problema do Adobe Commerce em que o botão [!UICONTROL Submit Review] pode ser clicado várias vezes sem a validação [!DNL Google reCAPTCHA v3] .
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890: o botão **[!UICONTROL Submit Review]** pode ser clicado várias vezes sem validação de **[!DNL Google reCAPTCHA v3]**

>[!NOTE]
>
>Este patch foi substituído por [ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

O patch ACSD-51890 corrige o problema em que o botão **[!UICONTROL Submit Review]** pode ser clicado várias vezes sem validação de **[!DNL Google reCAPTCHA v3]**. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 está instalado. A ID do patch é ACSD-51890. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

É possível clicar no botão **[!UICONTROL Submit Review]** várias vezes sem a validação **[!DNL Google reCAPTCHA v3]**.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!DNL Google reCAPTCHA v3]** para a análise do produto.
1. Abra a página do produto, navegue até a seção **[!UICONTROL Review]** e verifique se o [!DNL reCAPTCHA] está visível.
1. Preencha o formulário de revisão e clique no botão **[!UICONTROL Submit Review]** várias vezes o mais rápido possível.
1. Abra a seção **[!UICONTROL Review]** no Admin.

<u>Resultados esperados</u>

Revisões duplicadas não são criadas.

<u>Resultados reais</u>

Revisões duplicadas são criadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](</help/tools/quality-patches-tool/usage.md>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no guia [!DNL Quality Patches Tool].
