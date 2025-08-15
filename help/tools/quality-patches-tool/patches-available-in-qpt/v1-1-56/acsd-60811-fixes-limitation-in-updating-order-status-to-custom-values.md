---
title: 'ACSD-60811: corrige a limitação na atualização do status da ordem para valores personalizados'
description: Aplique o patch ACSD-60811 para corrigir o problema do Adobe Commerce em que a atualização do status do pedido com valor ou comentário personalizado só é possível se o status atual for "processando" ou "fraude".
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60811: corrige a limitação na atualização do status da ordem para valores personalizados

O patch ACSD-60811 corrige o problema em que a atualização do status do pedido com um valor ou comentário personalizado só é possível se o status atual for &#39;[!UICONTROL Processing]&#39; ou &#39;[!UICONTROL Suspected Fraud].&#39; Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-60811. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7. 2,4,7-p1, 2,4,7-p2, 2,4,7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A atualização do status do pedido com um valor ou comentário personalizado só será possível se o status atual for *processando* ou *fraude*. O status do pedido permanece inalterado quando um novo status é selecionado e enviado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** para criar um status de pedido personalizado no painel de administração.
1. Clique em **[!UICONTROL Assign Status to State]** para atribuir o status personalizado ao estado do pedido.
1. Altere o status do pedido na página visualização de pedido no painel de administração.

<u>Resultados esperados</u>:

O usuário administrador deve ser capaz de alterar o status do pedido para um status de pedido personalizado no painel de administração.

<u>Resultados reais</u>:

O status do pedido permanece o mesmo quando um novo status de pedido é selecionado e enviado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
