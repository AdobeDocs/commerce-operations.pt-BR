---
title: Configurar a integração do GitHub para  [!DNL Adobe Commerce Patching Automation]
description: Saiba como instalar o [!DNL Adobe Commerce Patching Automation] Aplicativo GitHub para habilitar operações de patch para projetos da Adobe Commerce Cloud conectados ao GitHub.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# Configurar a integração do GitHub para [!DNL Patching Automation]

Se o projeto da Adobe Commerce Cloud estiver conectado a um repositório GitHub, instale o Aplicativo GitHub [!DNL Patching Automation] antes de usar o serviço para aplicar ou reverter patches. O aplicativo concede ao serviço o acesso necessário para fazer alterações no repositório em seu nome.

## Pré-requisitos

* Uma assinatura ativa da Adobe Commerce Cloud
* Uma [integração com o GitHub](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) já foi configurada para o seu projeto da Adobe Commerce Cloud, com a opção [`fetch-branches` habilitada](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). O [!DNL Patching Automation] cria e envia ramificações temporárias de ambiente de integração, portanto, as operações de patch não criam o ambiente quando esta opção é desabilitada.
* Um repositório hospedado em [!DNL github.com]. Não há suporte para integrações GitHub configuradas com um domínio personalizado.
* Acesso de proprietário ou administrador à organização ou ao repositório do GitHub

## Instalar o aplicativo GitHub [!DNL Patching Automation]

Você pode iniciar a instalação a partir de [!DNL Patching Automation] clicando em **[!UICONTROL Install GitHub App]** na interface do usuário, que o redireciona para a página de instalação, ou navegando diretamente para a página de instalação.

1. Abra a [página de instalação do Aplicativo GitHub de Automação de Patches](https://github.com/apps/adobe-commerce-patching-automation).
1. Clique em **[!UICONTROL Install]**.
1. Selecione a organização do GitHub que é proprietária do repositório do Adobe Commerce.
1. Em **[!UICONTROL Repository access]**, selecione **[!UICONTROL Only select repositories]** e escolha o repositório para seu projeto do Adobe Commerce.
1. Clique em **[!UICONTROL Install]** para confirmar.

Depois de instalado, o serviço detecta automaticamente a conexão GitHub e usa o aplicativo para todas as operações de patch. Nenhuma configuração adicional é necessária.

## Verificar e gerenciar o status da conexão

A interface do usuário do [!DNL Patching Automation] mostra o status atual da sua conexão GitHub, com ações disponíveis que dependem desse status:

* **[!UICONTROL Refresh]** / **[!UICONTROL Refresh status]** - Verifica novamente o status da conexão sem fazer alterações.
* **[!UICONTROL Reinstall]** - Mostrado se a instalação não é mais válida (por exemplo, se foi suspensa ou se o repositório conectado ao projeto na nuvem foi alterado). Inicia o mesmo fluxo de instalação descrito acima.
* **[!UICONTROL Unlink GitHub App]** - Remove a conexão salva de [!DNL Patching Automation] ao Aplicativo GitHub. Isso faz **não** desinstalar o aplicativo do seu repositório GitHub — para remover totalmente o acesso, consulte a seção Desinstalar abaixo.

## Desinstalar o aplicativo GitHub [!DNL Patching Automation]

Se você não quiser mais que o serviço acesse seu repositório:

1. No GitHub, abra as configurações da conta que é proprietária da instalação:
   * Para um repositório **de propriedade da organização**: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Para um repositório **pessoal**: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Localize `adobe-commerce-patching-automation` e clique em **[!UICONTROL Configure]**.
1. Clique em **[!UICONTROL Uninstall]** e confirme.

>[!WARNING]
>
>Se alguma operação de aplicação ou reversão ainda estiver em andamento quando o aplicativo GitHub for desinstalado, essas operações poderão falhar. Após desinstalar o aplicativo, os usuários também não podem iniciar novas operações porque os botões de ação ficam inativos.

## Tópicos relacionados

* [Introdução à automação de patches](intro.md)
* [Como acessar o](access.md)
* [Visão geral do fluxo de trabalho](workflow.md)
* [Práticas recomendadas](best-practices.md)
* [Solução de problemas](troubleshooting.md)
