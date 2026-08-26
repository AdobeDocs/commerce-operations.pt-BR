---
title: Como acessar [!DNL Adobe Commerce Patching Automation]
description: Saiba como acessar e usar o  [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Como acessar [!DNL Adobe Commerce Patching Automation]

## Pré-requisitos

[!DNL Patching Automation] usa o controle de acesso baseado em função da Adobe Commerce Cloud. Seu nível de acesso no Cloud Console determina o que você pode fazer com o serviço.

### Quem pode usar [!DNL Patching Automation]

* **Administrador do projeto** - Pode aplicar ou reverter patches em todos os ambientes
* **Colaborador** - Pode aplicar ou reverter patches em seus ambientes atribuídos
* **Visualizador** - Só é possível exibir o projeto e os ambientes, nenhuma ação é permitida

### Como solicitar acesso a um projeto

Se você não vir nenhum projeto na interface do usuário do [!DNL Patching Automation], solicite acesso à pessoa apropriada:

* Contate o proprietário da conta ou o administrador do projeto
* Eles concederão a função apropriada por meio do Cloud Console
* Depois de receber o acesso, você pode fazer logon no Cloud Console para usar o serviço

>[!NOTE]
>
>O [!DNL Patching Automation] segue o mesmo modelo de permissão da Adobe Commerce Cloud, portanto, seu nível de acesso no Console da Nuvem determina o que você pode fazer com o serviço.

## Acessando [!DNL Patching Automation]

[!DNL Patching Automation] está disponível como uma guia no painel [!DNL Site-Wide Analysis Tool]. Você pode acessá-lo pelo Painel de Administração acessando **Relatórios** > **Insights do Sistema** > **Ferramenta de Análise do Site** na barra lateral de Administração. Consulte [Como acessar a Ferramenta de Análise do Site](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) para obter os pré-requisitos e a configuração de permissões.

Quando estiver no painel:

1. Clique na guia [!UICONTROL Patching Automation] na interface.
1. Selecione o projeto e o ambiente em que deseja aplicar patches.
1. Revise os patches disponíveis e seu status de compatibilidade.
1. Selecione patches para aplicar ou reverter.

## Acesso ao ambiente de produção

Para ambientes de produção, proteções adicionais se aplicam por padrão:

* **Modo de manutenção** - Deve ser habilitado
* **Trabalhos do Cron** - Devem ser desabilitados
* **Caixa de diálogo de confirmação** - Deve ser concluída antes de continuar

>[!IMPORTANT]
>
>A aplicação de patches no ambiente de produção requer preparação e proteção adequadas para evitar interrupções acidentais.

>[!NOTE]
>
>Você pode ignorar as verificações de modo de manutenção e trabalho cron marcando a caixa de seleção de substituição na interface (*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*). Use-a somente se você entender o risco de corrigir a produção sem essas proteções em vigor.

## Tópicos relacionados

* [Introdução à automação de patches](intro.md)
* [Visão geral do fluxo de trabalho](workflow.md)
* [Integração com o GitHub](github-integration.md)
* [Práticas recomendadas](best-practices.md)
* [Solução de problemas](troubleshooting.md)
