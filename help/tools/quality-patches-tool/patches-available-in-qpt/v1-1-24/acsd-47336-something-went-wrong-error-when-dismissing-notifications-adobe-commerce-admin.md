---
title: 'ACSD-47336: erro [!UICONTROL Something went wrong] ao descartar notificações no Adobe Commerce Admin'
description: Aplique o patch ACSD-47336 para corrigir o problema do Adobe Commerce em que o usuário vê o erro [!UICONTROL Something went wrong] ao dispensar notificações no  [!DNL Commerce] Administrador.
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47336: erro _[!UICONTROL Something went wrong]_&#x200B;ao descartar notificações no Adobe Commerce Admin

O patch ACSD-47336 corrige o problema em que o usuário vê o erro _[!UICONTROL Something went wrong]_&#x200B;ao dispensar notificações no administrador [!DNL Commerce]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-47336. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário vê o erro _[!UICONTROL Something went wrong]_&#x200B;ao dispensar notificações no Administrador [!DNL Commerce].

<u>Etapas a serem reproduzidas</u>:

1. Executar uma operação em massa (por exemplo, atualização em massa dos atributos do produto na grade de produtos).
1. Conclua a operação (por exemplo, execute `bin/magento queue:consumer:start product_action_attribute.update`).
1. Atualize a página de Administrador [!DNL Commerce], expanda a seção de notificação de administrador e clique no link **[!UICONTROL Dismiss All Completed Tasks]**.

<u>Resultados esperados</u>:

O erro _[!UICONTROL Something went wrong]_&#x200B;não deve ser exibido ao limpar as tarefas concluídas.

<u>Resultados reais</u>:

O erro _[!UICONTROL Something went wrong]_&#x200B;é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
