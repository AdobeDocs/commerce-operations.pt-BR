---
title: 'ACSD-48570: corrigindo problema de link de redefinição de senha do administrador com código de loja no URL'
description: Aplique o patch ACSD-48570 para corrigir o problema do Adobe Commerce em que a página de redefinição de senha não podia ser acessada por meio do link de redefinição de senha de Admin quando a configuração [!UICONTROL Add Store Code to URLs] foi habilitada.
feature: Security, User Account
role: Admin, Developer
source-git-commit: a9d7f4f4c2f2e27ff9571de08bcec918b4605b03
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570: corrigindo problema de link de redefinição de senha do administrador com código de loja no URL

O patch ACSD-48570 para corrigir o problema do Adobe Commerce em que a página de redefinição de senha não podia ser acessada por meio do link de redefinição de senha de Admin quando a configuração *[!UICONTROL Add Store Code to URLs]* foi habilitada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-48570. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando a configuração **[!UICONTROL Add Store Code to URLs]** está habilitada, a funcionalidade de redefinição de senha do Administrador não funciona corretamente.
Depois que um usuário administrador solicita uma redefinição de senha e clica no link de recuperação no email, ele é redirecionado para a página de logon ou recebe um erro 404 em vez de ser levado para o formulário de redefinição de senha. Isso impede que os administradores recuperem suas contas sem intervenção manual.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar a configuração **[!UICONTROL Add Store Code to URLs]** em **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**.
1. Faça logoff do painel Admin e clique no link **[!UICONTROL Forgot your password?]** na página de logon Admin.
1. Insira o email do usuário administrador, passe o captcha e clique em **[!UICONTROL Retrieve Password]**.
1. Abra o email de redefinição de senha e clique no link de recuperação de senha.

<u>Resultados esperados</u>:

O formulário de redefinição de senha deve ser exibido.

<u>Resultados reais</u>:

A página de logon ou uma página de erro 404 é exibida em vez do formulário de redefinição de senha.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
