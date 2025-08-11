---
title: 'ACSD-66118: A atualização de [!UICONTROL Store View Code] limpa [!UICONTROL Design Configuration] configurações se [!UICONTROL Configuration Cache] não for atualizado'
description: Aplique o patch ACSD-66118 para corrigir o problema do Adobe Commerce em que a atualização do [!UICONTROL Store View Code] limpa o [!UICONTROL Design Configuration] (tema e configurações personalizadas) se o [!UICONTROL Configuration Cache] não for atualizado corretamente.
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
source-git-commit: ef4d6e420f304b0229c54c8ec7bd5500039bcb6b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# ACSD-66118: A atualização de **[!UICONTROL Store View Code]** limpa **[!UICONTROL Design Configuration]** configurações se **[!UICONTROL Configuration Cache]** não for atualizado

O patch ACSD-66118 corrige o problema em que a atualização de **[!UICONTROL Store View Code]** limpa as configurações de **[!UICONTROL Design Configuration]** se **[!UICONTROL Configuration Cache]** não for atualizado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-66118. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As configurações de **[!UICONTROL Design Configuration]** (como tema e configurações personalizadas) são limpas ao atualizar o campo **[!UICONTROL Store View Code]**, se **[!UICONTROL Configuration Cache]** não for atualizado.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no painel **[!UICONTROL Admin]**.
2. Navegue até **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**.
3. Edite uma exibição de armazenamento que tenha um tema personalizado configurado em **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**.
4. Altere o campo **[!UICONTROL Code]** (por exemplo, de `storeview_1` para `storeview_main`).
5. Clique em **[!UICONTROL Save Store View]** para salvar as alterações.
6. Atualize ou reabra a página **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** do **[!UICONTROL Store View]** atualizado e nenhum tema será selecionado.

<u>Resultados esperados</u>:

Depois de atualizar o **[!UICONTROL Store View Code]**, o **[!UICONTROL Design Configuration]** (incluindo o tema e as configurações personalizadas) deve permanecer intacto.

<u>Resultados reais</u>:

O **[!UICONTROL Design Configuration]** está limpo. O tema reverte para o padrão e as configurações personalizadas são perdidas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
