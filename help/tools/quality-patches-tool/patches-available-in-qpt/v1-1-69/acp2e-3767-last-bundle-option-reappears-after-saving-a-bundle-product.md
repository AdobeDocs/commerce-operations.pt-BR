---
title: 'ACP2E-3767: A última opção de pacote reaparece após salvar um produto de pacote'
description: Aplique o patch ACP2E-3767 para corrigir o problema do Adobe Commerce em que a última opção de pacote em um produto de pacote não pôde ser removida.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 8c0645e3-47ab-4604-a9db-b070c3779e78
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
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
source-wordcount: '354'
ht-degree: 0%
---
# ACP2E-3767: A última opção de pacote reaparece após salvar um produto de pacote

O patch ACP2E-3767 corrige o problema em que a última opção de pacote reaparece após salvar o produto do pacote. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACP2E-3767. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A última opção de pacote em um produto de pacote não pode ser removida.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Selecione **[!UICONTROL Simple Product]** na lista suspensa.
1. Insira os dados necessários e salve.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Selecione **[!UICONTROL Bundle Product]** na lista suspensa.
1. Insira os dados necessários.
1. Em Itens do Pacote, clique em **[!UICONTROL Add Option]**.
1. Adicione um título à nova opção e clique em **[!UICONTROL Add Products to Option]**.
1. Selecione o produto simples criado anteriormente, depois **[!UICONTROL Add Selected Products]**.
1. Salve o produto do pacote.
1. Remova a opção do pacote e salve.

<u>Resultados esperados</u>:

1. A opção de pacote foi removida com sucesso.
1. Uma mensagem será exibida se a remoção não for permitida.

<u>Resultados reais</u>:

1. A opção de pacote permanece ativa.
1. Nenhum erro ou notificação é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
