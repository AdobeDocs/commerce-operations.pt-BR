---
title: 'ACSD-63793: Os processos de importação interferem entre si em diferentes guias do navegador'
description: Aplique o patch ACSD-63793 para corrigir o problema do Adobe Commerce em que os processos de importação interferem entre si em diferentes guias do navegador.
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
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
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-63793: Os processos de importação interferem entre si em diferentes guias do navegador

O patch ACSD-63793 corrige o problema em que os processos de importação interferem entre si em diferentes guias do navegador. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-63793. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A importação de dados por meio da interface do Administrador interfere em outra importação, fazendo com que os dados de uma importação sejam processados em outra.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.
1. Definir **[!UICONTROL Entity Type]** como *[!UICONTROL Customers and Addresses] (arquivo único)*.
1. Defina **[!UICONTROL Import Behavior]** como *[!UICONTROL Add/Update]*.
1. Selecione um arquivo válido para importar.
1. Clique no botão **[!UICONTROL Check Data]**.
1. Mantenha essa guia aberta.
1. Abra uma nova guia e repita as etapas com um arquivo contendo dados inválidos (por exemplo, dois emails idênticos para clientes diferentes).
1. Volte para a primeira guia.
1. Clique no botão **[!UICONTROL Import]** na parte inferior.

<u>Resultados esperados</u>:

O processo de importação não deve interferir entre si.

<u>Resultados reais</u>:

O processo de importação é concluído e o arquivo de relatório está disponível para download. Indica um erro na segunda linha e os dados de outra importação são processados, mesmo que a validação inicial tenha sido aprovada sem erros.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
