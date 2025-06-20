---
title: 'ACSD-63578: Clicar no ícone [!UICONTROL Delete] em [!UICONTROL Add to Order by SKU] não remove a SKU'
description: Aplique o patch ACSD-63578 para corrigir o problema do Adobe Commerce em que clicar no ícone [!UICONTROL Delete] em [!UICONTROL Add to Order by SKU] no Admin não remove o SKU.
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578: Clicar no ícone **[!UICONTROL Delete]** em *[!UICONTROL Add to Order by SKU]* não remove o SKU

O patch ACSD-63578 corrige o problema em que clicar no ícone **[!UICONTROL Delete]** em *[!UICONTROL Add to Order by SKU]* no Admin não remove a SKU. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63578. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Clicar no ícone **[!UICONTROL Delete]** em *[!UICONTROL Add to Order by SKU]* no Administrador não remove a SKU do pedido.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e clique em **[!UICONTROL Create New Order]**.
1. Escolha um cliente.
1. Clique em **[!UICONTROL Add to Order by SKU]**.
   * Insira um SKU.
   * Clique no botão **[!UICONTROL Add another]**.
1. Clique no ícone **[!UICONTROL Delete]**.

<u>Resultados esperados</u>:

* Os produtos são adicionados e removidos de um pedido no Admin.

<u>Resultados reais</u>:

* O ícone **[!UICONTROL Delete]** não funciona.
* Há um erro no console:

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
