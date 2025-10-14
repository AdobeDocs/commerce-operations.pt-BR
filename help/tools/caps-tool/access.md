---
title: Como acessar [!DNL Cloud Automation Patching Service (CAPS)]
description: Saiba como acessar e usar o  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# Como acessar [!DNL Cloud Automation Patching Service (CAPS)]

## Pré-requisitos

[!DNL CAPS] usa o controle de acesso baseado em função da Adobe Commerce Cloud. Seu nível de acesso no Cloud Console determina o que você pode fazer com o [!DNL CAPS].

### Quem pode usar [!DNL CAPS]

* **Administrador do projeto** - Pode aplicar ou reverter patches em todos os ambientes
* **Colaborador** - Pode aplicar ou reverter patches em seus ambientes atribuídos
* **Visualizador** - Só é possível exibir o projeto e os ambientes, nenhuma ação é permitida

### Como solicitar acesso a um projeto

Se você não vir nenhum projeto na interface do usuário do [!DNL CAPS], será necessário solicitar acesso à pessoa apropriada:

* Contate o proprietário da conta ou o administrador do projeto
* Eles concederão a função apropriada por meio do Cloud Console
* Depois de receber acesso, você pode fazer logon no Cloud Console para usar o [!DNL CAPS]

>[!NOTE]
>
>O [!DNL CAPS] segue o mesmo modelo de permissão da Adobe Commerce Cloud, portanto, seu nível de acesso no Console da Nuvem determina o que você pode fazer com o [!DNL CAPS].

## Acessando [!DNL CAPS]

A ferramenta CAPS está disponível no painel da Ferramenta de Análise do Site em [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/). Na guia Automação de patch, você pode selecionar o projeto e o ambiente.

1. Navegue até a Ferramenta de Análise do Site em [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/).
1. Clique na guia [!UICONTROL Patching Automation] na interface.
1. Selecione o projeto e o ambiente em que deseja aplicar patches.
1. Revise os patches disponíveis e seu status de compatibilidade.
1. Selecione patches para aplicar ou reverter.

## Acesso ao ambiente de produção

Para ambientes de produção, proteções adicionais se aplicam:

* **Modo de manutenção** - Deve ser habilitado
* **Trabalhos do Cron** - Devem ser desabilitados
* **Caixa de diálogo de confirmação** - Deve ser concluída antes de continuar

>[!IMPORTANT]
>
>A aplicação de patches no ambiente de produção requer preparação e proteção adequadas para evitar interrupções acidentais.

## Tópicos relacionados

* [Introdução ao CAPS](intro.md)
* [Fluxo de trabalho (WRK)](workflow.md)
* [Práticas recomendadas](best-practices.md)
* [Solução de problemas](troubleshooting.md)
