---
title: 'ACSD-54040: o campo [!UICONTROL Created] está em branco para exibir detalhes da ordem quando os módulos B2B estão habilitados'
description: Aplique o patch ACSD-54040 para corrigir o problema do Adobe Commerce em que o campo [!UICONTROL Created] está em branco na página de detalhes do pedido quando os módulos B2B estão habilitados.
feature: B2B
role: Admin, Developer
exl-id: 09fc1e0f-2e02-4cfc-9a7a-7c6aacd9fee0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-54040: o campo *[!UICONTROL Created]* está em branco para exibir detalhes da ordem quando os módulos B2B estão habilitados.

O patch ACSD-54040 corrige o problema em que o campo *[!UICONTROL Created]* permanece em branco na página de detalhes do pedido quando os módulos B2B são habilitados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 está instalado. A ID do patch é ACSD-54040. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando os módulos B2B são habilitados, o campo *[!UICONTROL Created]* permanece em branco na página de detalhes do pedido.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com o módulo B2B.
1. Crie um novo cliente e faça um pedido.
1. Vá para os detalhes do pedido no front-end e verifique o campo *[!UICONTROL Created]*.

<u>Resultados esperados</u>:

O campo *[!UICONTROL Created]* exibe a data em que o pedido foi criado.

<u>Resultados reais</u>:

O campo *[!UICONTROL Created]* está em branco

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
