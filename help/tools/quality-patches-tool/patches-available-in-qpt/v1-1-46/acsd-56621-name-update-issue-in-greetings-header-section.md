---
title: 'ACSD-56621: nomes atualizados não exibidos no cabeçalho de saudações para o usuário administrador da empresa'
description: Aplique o patch ACSD-56621 para corrigir o problema do Adobe Commerce em que o nome e o sobrenome atualizados do usuário administrador de empresa não são refletidos na seção do cabeçalho de saudações.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621: nomes atualizados não exibidos no cabeçalho de saudações para o usuário administrador da empresa

O patch ACSD-56621 corrige o problema em que o nome e o sobrenome atualizados do usuário administrador de empresa não são refletidos na seção de cabeçalho de saudações. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 está instalado. A ID do patch é ACSD-56621. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os nomes atualizados não são exibidos no cabeçalho de saudações para usuários administradores de empresas.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até o painel **[!UICONTROL Admin]**.
1. Vá para **[!UICONTROL Stores]** e selecione **[!UICONTROL Configuration]**.
1. Na seção **[!UICONTROL General]**, selecione **[!UICONTROL B2B]** para habilitar a funcionalidade de empresa B2B.
1. Vá para **[!UICONTROL Storefront]** e registre uma nova empresa.
1. Faça logon como o usuário administrador da empresa.
1. Vá para **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** e modifique os campos de nome e sobrenome conforme necessário.

<u>Resultados esperados</u>:

O nome e o sobrenome do usuário na seção de cabeçalho greetings são alterados imediatamente.

<u>Resultados reais</u>:

O nome e o sobrenome do usuário só são alterados quando o usuário faz logoff e logon novamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
