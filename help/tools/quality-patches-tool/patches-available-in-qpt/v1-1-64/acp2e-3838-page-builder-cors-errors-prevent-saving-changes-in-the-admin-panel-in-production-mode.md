---
title: 'ACP2E-3838: [!DNL Page Builder] Os erros do CORS impedem que as alterações sejam salvas no painel de administração no modo de produção'
description: Aplique o patch ACP2E-3838 para corrigir o problema do Adobe Commerce em que os  [!DNL Page Builder] erros do CORS impedem que as alterações sejam salvas no painel de administração no modo de produção.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
source-git-commit: 1b9c721c8200f38b6ce5d1b4de87b1f10e07e8d2
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACP2E-3838: [!DNL Page Builder] Erros do CORS impedem que alterações sejam salvas no painel de administração no modo de produção

O patch ACP2E-3838 corrige o problema em que [!DNL Page Builder] erros do CORS impedem que alterações sejam salvas no painel de administração no modo de produção. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACP2E-3838. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL Page Builder] Erros do CORS impedem que alterações sejam salvas no painel de administração no modo de produção.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no painel de administração.
1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Clique em **[!UICONTROL Add New Page]** ou selecione uma página CMS existente e clique em **[!UICONTROL Edit]**.
1. Clique em **[!UICONTROL Edit with Page Builder]** para adicionar um novo bloco de conteúdo ou editar um bloco existente.
1. Faça alterações no conteúdo, como adicionar texto, imagens ou outros elementos.
1. Clique no botão **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

O conteúdo da página deve ser salvo com sucesso sem erros.

<u>Resultados reais</u>:

1. Falha ao salvar as alterações de [!DNL Page Builder].
1. O console do navegador registra erros relacionados ao CORS.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
