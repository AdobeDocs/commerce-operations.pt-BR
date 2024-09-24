---
title: "ACSD-49748: convites por email não podem ser enviados"
description: Aplique o patch ACSD-49748 para corrigir o problema do Adobe Commerce em que os usuários não conseguem enviar convites por email.
feature: Admin Workspace, Communications, Marketing Tools
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-49748: Convites por email não podem ser enviados

O patch ACSD-49748 corrige o problema em que os usuários não conseguem enviar convites por email. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49748. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O erro *Algo deu errado ao enviar convites* é exibido ao enviar convites.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin Panel]** > **[!UICONTROL Marketing]** > **[!UICONTROL Private Sales]** > **[!UICONTROL Invitations]**.
1. Crie um convite e salve-o.
1. Vá para **[!UICONTROL Invitation Grid]** e selecione qualquer convite.
1. Envie o convite.

<u>Resultados esperados</u>:

Um convite é enviado ao clicar em *[!UICONTROL Send Invitation]*.

<u>Resultados reais</u>:

O erro *Algo deu errado ao enviar convites* é exibido e o convite não é enviado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].

