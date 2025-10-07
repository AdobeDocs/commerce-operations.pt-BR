---
title: Como acessar [!DNL Site-Wide Analysis Tool]
description: Saiba como acessar o painel da Ferramenta de análise do site no Painel de administração do Adobe Commerce. Descubra as permissões de usuário e os requisitos de função.
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Como acessar o [!DNL Site-Wide Analysis Tool]

Você pode acessar o painel [!DNL Site-Wide Analysis Tool] no [!UICONTROL Admin Panel] da sua loja.

O serviço [!DNL Site-Wide Analysis Tool] está disponível no [modo de produção](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/tools/developer-tools#operation-modes) para [!UICONTROL Admin] usuários com permissão para acessar os [recursos de função](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/user-accounts/permissions-user-roles) do usuário.

>[!NOTE]
>
>A partir de 23 de abril de 2024, o [!DNL Site-Wide Analysis Tool] foi descontinuado e não está mais disponível para clientes locais do Adobe Commerce.


![Painel de Análise do Site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Painel*

>[!NOTE]
>
>Sua conta deve ter direito a **[!DNL Support Permissions]** para acessar o [!DNL Site-Wide Analysis Tool Dashboard].
>&#x200B;>Veja mais detalhes em [Compartilhar uma [!DNL Commerce] conta](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html?lang=pt-BR) em nosso guia do usuário.

## Fazendo logon em [!DNL Site-Wide Analysis Tool Dashboard] a partir da [!UICONTROL Admin Panel] do seu armazenamento

### Etapa 1: verificar permissões

Verifique se a conta de usuário [!UICONTROL Admin] tem permissão para acessar [!DNL Site-Wide Analysis Tool] por meio de sua [função de usuário atribuída](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/user-accounts/permissions-user-roles).

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
>Se você tiver verificado que a conta de usuário tem permissão para acessar o [!DNL Site-Wide Analysis Tool] e o usuário receber um erro 403 ao tentar acessar a ferramenta a partir do [!UICONTROL Admin], sua instância do Adobe Commerce na infraestrutura em nuvem poderá ter o controle de acesso HTTP habilitado. O Painel [!DNL Site-Wide Analysis Tool] NÃO é suportado se a Autenticação HTTP estiver habilitada. Para obter mais informações sobre como resolver esse problema, consulte nosso [Artigo de suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento).

### Etapa 2: acessar [!DNL Site-Wide Analysis Tool]

1. Na barra lateral *[!UICONTROL Admin]*, vá para **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Painel de Análise do Site](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]local em [!UICONTROL Admin Panel] no Adobe Commerce*

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
