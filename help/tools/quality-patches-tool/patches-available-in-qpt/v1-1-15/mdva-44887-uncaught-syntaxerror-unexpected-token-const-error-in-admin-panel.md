---
title: '"MDVA-44887: erro "Uncaught SyntaxError: Unexpected token const" no painel Admin"'
description: "O patch MDVA-44887 corrige o problema em que o usuário administrador não pode clicar em nenhuma opção de menu. O erro *Uncaught SyntaxError: Unexpected token const* é exibido no painel Admin. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 está instalada. A ID do patch é MDVA-44887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5."
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-44887: erro &quot;Uncaught SyntaxError: Unexpected token const&quot; no painel Admin

O patch MDVA-44887 corrige o problema em que o usuário administrador não pode clicar em nenhuma opção de menu. O erro *Uncaught SyntaxError: Unexpected token const* é exibido no painel Admin. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 está instalada. A ID do patch é MDVA-44887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode clicar em nenhuma opção de menu. O erro *Uncaught SyntaxError: Unexpected token const* é exibido no painel Admin.

<u>Etapas a serem reproduzidas</u>:

1. Habilite o agrupamento JS.
1. Reduza os arquivos JS.
1. Faça logon no painel de Administração do Commerce.

<u>Resultados esperados</u>:

O usuário administrador não pode clicar em nenhuma opção de menu. Há um erro no console do navegador: *SyntaxError não detectado: const de token inesperada*.

<u>Resultados reais</u>:

O painel Administração pode ser acessado por um usuário administrador.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
