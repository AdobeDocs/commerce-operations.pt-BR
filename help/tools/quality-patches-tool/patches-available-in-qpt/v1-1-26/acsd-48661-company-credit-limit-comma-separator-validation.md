---
title: 'ACSD-48661: problema de validação do separador de vírgula do limite de crédito da empresa'
description: Aplique o patch ACSD-48661 para corrigir o problema do Adobe Commerce em que, quando o limite de crédito da empresa é maior que 999, o separador de vírgulas impede o salvamento da empresa devido a um erro de validação.
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
exl-id: 7115226e-5942-4a8f-9dec-b1b6f665eef8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-48661: problema de validação do separador de vírgula do limite de crédito da empresa

O patch ACSD-48661 corrige o problema em que, quando o limite de crédito da empresa é maior que 999, o separador de vírgulas impede o salvamento da empresa devido a um erro de validação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 está instalado. A ID do patch é ACSD-48661. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando o limite de crédito da empresa é maior que 999, o separador de vírgulas impede que a empresa seja salva devido a um erro de validação.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar o recurso da empresa em **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Crie uma empresa e adicione um limite de crédito maior que 999 na guia **[!UICONTROL Company Credit]**.
1. Salve a empresa.
1. Edite a empresa e tente salvá-la novamente.

<u>Resultados esperados</u>:

Você pode salvar a empresa sem fixar o limite de crédito. A vírgula não é compatível com campos de entrada para valores e preços.

<u>Resultados reais</u>:

Você não pode salvar a empresa devido a um erro de validação no campo *[!UICONTROL Credit Limit]*. O Adobe Commerce adiciona automaticamente separadores de vírgula para limites de crédito mesmo que o campo [!UICONTROL Credit Limit] não aceite vírgulas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
