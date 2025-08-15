---
title: 'ACSD-58685: emails de vendas desativados são enviados ao reativar'
description: Aplique o patch ACSD-58685 para corrigir o problema do Adobe Commerce, em que os emails de vendas iniciados enquanto a comunicação por email está desativada são enviados quando a comunicação por email é reativada.
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685: emails de vendas desativados são enviados ao reativar

O patch ACSD-58685 corrige o problema em que os emails de vendas iniciados enquanto a comunicação por email está desativada são enviados quando a comunicação por email é reativada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-58685. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Emails de vendas iniciados enquanto a comunicação por email está desativada são enviados assim que a comunicação por email é reativada.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** e defina **[!UICONTROL Disable Email Communications]** como *[!UICONTROL No]*.
1. Navegue até **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** e defina **[!UICONTROL Asynchronous Sending]** como *[!UICONTROL Yes]*.
1. Limpe o cache de configuração.
1. Fazer um pedido.
1. Habilitar comunicação por email.
1. Faça outro pedido.
1. Execute o cron.

<u>Resultados esperados</u>:

Somente o email da segunda ordem é enviado.

<u>Resultados reais</u>:

Emails para a primeira e a segunda ordem são enviados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
