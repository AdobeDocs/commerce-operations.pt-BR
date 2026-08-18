---
title: Configurar a integração do GitHub para  [!DNL CAPS]
description: Saiba como instalar o [!DNL Cloud Automation Patching Service (CAPS)] Aplicativo GitHub para habilitar operações de patch para projetos da Adobe Commerce Cloud conectados ao GitHub.
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# Configurar a integração do GitHub para [!DNL CAPS]

Se o projeto da Adobe Commerce Cloud estiver conectado a um repositório GitHub, instale o Aplicativo GitHub [!DNL CAPS] antes de usar o [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) para aplicar ou reverter patches. O aplicativo concede a [!DNL CAPS] o acesso necessário para fazer alterações no repositório em seu nome.

## Pré-requisitos

* Uma assinatura ativa da Adobe Commerce Cloud
* Uma [integração com o GitHub](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) já foi configurada para o seu projeto da Adobe Commerce Cloud, com a opção [`fetch-branches` habilitada](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). O [!DNL CAPS] cria e envia ramificações temporárias de ambiente de integração, portanto, as operações de patch não criam o ambiente quando esta opção é desabilitada.
* Um repositório hospedado em [!DNL github.com]. Não há suporte para integrações GitHub configuradas com um domínio personalizado.
* Acesso de proprietário ou administrador à organização ou ao repositório do GitHub

## Instalar o aplicativo GitHub [!DNL CAPS]

1. Abra a [página de instalação do aplicativo CAPS GitHub](https://github.com/apps/adobe-commerce-patching-automation).
1. Clique em **[!UICONTROL Install]**.
1. Selecione a organização do GitHub que é proprietária do repositório do Adobe Commerce.
1. Em **[!UICONTROL Repository access]**, selecione **[!UICONTROL Only select repositories]** e escolha o repositório para seu projeto do Adobe Commerce.
1. Clique em **[!UICONTROL Install]** para confirmar.

Depois de instalado, o [!DNL CAPS] detecta automaticamente sua conexão com o GitHub e usa o aplicativo para todas as operações de patch. Nenhuma configuração adicional é necessária.

## Desinstalar o aplicativo GitHub [!DNL CAPS]

Se você não quiser mais que [!DNL CAPS] acesse seu repositório:

1. No GitHub, abra as configurações da conta que é proprietária da instalação:
   * Para um repositório **de propriedade da organização**: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Para um repositório **pessoal**: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Localize `adobe-commerce-patching-automation` e clique em **[!UICONTROL Configure]**.
1. Clique em **[!UICONTROL Uninstall]** e confirme.

>[!WARNING]
>
>Se qualquer operação CAPS apply or revert ainda estiver em andamento quando o aplicativo GitHub for desinstalado, essas operações poderão falhar. Após desinstalar o aplicativo, os usuários também não podem iniciar novas operações porque os botões de ação ficam inativos.

## Tópicos relacionados

* [Introdução ao CAPS](intro.md)
* [Como acessar o](access.md)
* [Visão geral do fluxo de trabalho](workflow.md)
* [Práticas recomendadas](best-practices.md)
* [Solução de problemas](troubleshooting.md)
