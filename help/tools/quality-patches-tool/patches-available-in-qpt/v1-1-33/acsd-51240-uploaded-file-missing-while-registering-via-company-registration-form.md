---
title: 'ACSD-51240: arquivo carregado ausente durante o registro por meio do formulário de registro da empresa'
description: Aplique o patch ACSD-51240 para corrigir o problema do Adobe Commerce em que o arquivo carregado está ausente durante o registro por meio do formulário de registro da empresa.
exl-id: 78e339d6-435e-4856-9f57-98bb955d093c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240: arquivo carregado ausente durante o registro por meio do formulário de registro da empresa

>[!NOTE]
>
>Este patch foi substituído por [ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

O patch ACSD-51240 corrige o problema em que o arquivo carregado está ausente durante o registro por meio do formulário de registro da empresa. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 está instalado. A ID do patch é ACSD-51240. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>). Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Problema

O arquivo carregado está ausente durante o registro por meio do formulário de registro da empresa.

<u>Etapas a serem reproduzidas</u>:

1. Definir **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Sim*.
1. Crie um novo atributo de cliente do tipo **[!UICONTROL File]**, defina **[!UICONTROL Show in StoreFront]** = *Sim* e selecione **[!UICONTROL all forms]**.
1. Crie uma nova empresa na Loja e faça upload de uma imagem para o novo atributo.
Abra a empresa e o usuário administrador na Loja.

<u>Resultados esperados</u>:

O arquivo carregado é exibido.

<u>Resultados reais</u>:

O arquivo carregado não é exibido na página da empresa nem na página do cliente administrador no [!UICONTROL Commerce Admin].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
