---
title: 'ACSD-58008: editar a data final como *vazia* faz com que a atualização da programação desapareça'
description: Aplique o patch ACSD-58008 para corrigir o problema do Adobe Commerce em que editar a data de término como *vazia* faz com que a atualização de agendamento desapareça.
feature: Staging, Page Content
role: Admin, Developer
exl-id: 6d2279e5-6580-4325-b0a8-ed62a95da3c2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%
---
# ACSD-58008: Editar a data final como *vazia* faz com que a atualização da programação desapareça

O patch ACSD-58008 corrige o problema em que editar a data de término como *vazia* faz com que a atualização de agendamento desapareça. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. A ID do patch é ACSD-58008. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Editar a data de término como *vazia* faz com que a atualização da agenda desapareça

<u>Etapas a serem reproduzidas</u>:

1. Fazer logon como [!UICONTROL Admin].
1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** e crie uma página.
1. Selecione a página criada e clique em **[!UICONTROL Schedule New Update]**. *(Navegue até o canto superior direito da página)*.
1. Crie quatro atualizações. *(Por exemplo, como um incremento de* 2 *minutos)*.
1. Atualize a *atualização 2* e altere o horário para um horário que esteja à frente da última *atualização 4*.
1. Salve as atualizações feitas.

<u>Resultados esperados</u>:

A atualização da agenda mostra a *atualização 3*.

<u>Resultados reais</u>:

A atualização da agenda não mostra a *atualização 3*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
