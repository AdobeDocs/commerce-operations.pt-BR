---
title: Como acessar [!DNL Site-Wide Analysis Tool]
description: Saiba como acessar o  [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Como acessar o [!DNL Site-Wide Analysis Tool]

Há duas maneiras de acessar o [!DNL Site-Wide Analysis Tool Dashboard].

Você pode acessar o [!DNL dashboard] do [[!DNL Site-Wide Analysis Tool] Site](https://supportinsights.adobe.com/commerce) diretamente **(somente para Adobe Commerce na infraestrutura de nuvem)** e fazer logon com sua Adobe ID ou acessar por meio do [!DNL dashboard] do [!DNL Admin Panel] de sua loja.

O serviço [!DNL Site-Wide Analysis Tool] está disponível no [modo de produção](https://docs.magento.com/user-guide/magento/installation-modes.html) para [!DNL Admin] usuários com permissão para acessar os [recursos de função](https://docs.magento.com/user-guide/system/permissions-user-roles.html) do usuário.

>[!NOTE]
>
>Se você tiver uma instalação local do Adobe Commerce, instale um [agente](../site-wide-analysis-tool/installation.md) na infraestrutura para usar a ferramenta.

![Painel de Análise do Site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Painel*

## Opção 1: Fazer logon no [!DNL Site-Wide Analysis Tool Dashboard] diretamente do domínio [!DNL Site-Wide Analysis Tool] (somente para Adobe Commerce na infraestrutura de nuvem)

**[!DNL Adobe ID]é necessário** para acessar uma conta [!DNL Commerce].
Se você já tiver uma conta [!DNL Commerce], mas não tiver uma [!DNL Adobe ID], poderá criar uma durante o processo de entrada.

1. Ir para [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Clique no botão **[!UICONTROL Sign in with Adobe ID]** e siga as instruções.

   ![Painel de Análise do Site](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]tela de logon*

1. Aceite os termos e condições.

1. **<u>Observação</u>:** sua conta deve ter direito a **[!DNL Support Permissions]** para acessar [!DNL Site-Wide Analysis Tool Dashboard].
Veja mais detalhes em [Compartilhar uma [!DNL Commerce] conta](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) em nosso guia do usuário.

## Opção 2: Fazer logon em seu [!DNL Site-Wide Analysis Tool Dashboard] a partir do [!DNL Admin Panel] do seu armazenamento

### Etapa 1: verificar permissões

Verifique se a conta de usuário [!DNL Admin] tem permissão para acessar [!DNL Site-Wide Analysis Tool] por meio de sua [função de usuário atribuída](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>O recurso de função (permissão) [!DNL Site-Wide Analysis Tool] é **não** atribuído automaticamente. Ela DEVE ser ativada para a função de usuário e para a função atribuída individualmente a cada conta de usuário no [!UICONTROL Admin].

Para a função personalizada que precisa de acesso de [!DNL Site-Wide Analysis Tool], faça o seguinte:

1. Selecione o recurso de função **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Painel de Análise do Site](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]permissão selecionada para a função*

1. Clique em **[!UICONTROL Save Role]**.

1. Notifique todos os usuários com essa função atribuída para que saiam do [!DNL Admin] e entrem novamente.

>[!NOTE]
>
>Se você tiver verificado que a conta de usuário tem permissão para acessar o [!DNL Site-Wide Analysis Tool] e o usuário receber um erro 403 ao tentar acessar a ferramenta a partir do [!DNL Admin], sua instância do Adobe Commerce na infraestrutura em nuvem poderá ter o controle de acesso HTTP habilitado. O Painel [!DNL Site-Wide Analysis Tool] NÃO é suportado se a Autenticação HTTP estiver habilitada. Para obter mais informações sobre como resolver esse problema, consulte nosso [Artigo de suporte](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Etapa 2: acessar [!DNL Site-Wide Analysis Tool]

1. Na barra lateral *[!UICONTROL Admin]*, vá para **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Painel de Análise do Site](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]local em [!DNL Admin Panel] no Adobe Commerce*

1. Leia os *Termos de Uso* de [!DNL Site-Wide Analysis Tool] e clique em **[!UICONTROL Accept]** para continuar.

   Cada usuário deve aceitar os Termos de Uso da sessão. Esta etapa é repetida para cada sessão conectada.


1. Na parte superior do painel, clique na guia que deseja ver.

   ![Painel de Análise do Site](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]informações*

## Gerar relatórios a partir de [!DNL Site-Wide Analysis Tool Dashboard]

1. No canto superior direito do painel, clique em **[!UICONTROL Generate Report]**.

1. Marque a caixa de seleção de cada configuração de **[!UICONTROL Type]** e **[!UICONTROL Priority]** que deseja incluir no relatório.

1. Clique em **[!UICONTROL Generate Report]**.

   ![Painel de Análise do Site](../../assets/tools/swat-report-settings.png)
   *Configurações do relatório*

| GUIA | DESCRIÇÃO |
| --- | --- |
| Painel | Mostra a integridade do sistema com notificações atuais e recomendações por prioridade. |
| Informações | Fornece informações de contato do cliente e um resumo dos tíquetes atuais, com informações detalhadas sobre cada produto Adobe Commerce instalado. |
| Recommendations | Lista recomendações com base nas práticas recomendadas para resolver problemas detectados no site. |
| Exceções | Lista os erros lançados pelo aplicativo causados por condições anormais sem um manipulador de erros. |
| Extensões | Lista todas as extensões de terceiros e bibliotecas de terceiros. |

>[!NOTE]
>
>Após aplicar uma recomendação, ela pode levar alguns dias para ser atualizada no [!DNL Site-Wide Analysis Tool Dashboard] ou gerar o relatório.
