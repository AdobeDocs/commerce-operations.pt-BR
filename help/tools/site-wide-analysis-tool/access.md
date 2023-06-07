---
title: Como acessar o [!DNL Site-Wide Analysis Tool]
description: Saiba como acessar o [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Como acessar o [!DNL Site-Wide Analysis Tool]

Há duas maneiras de acessar a variável [!DNL Site-Wide Analysis Tool Dashboard].

Você pode acessar o [!DNL dashboard] de qualquer uma das [[!DNL Site-Wide Analysis Tool] Site](https://supportinsights.adobe.com/commerce) diretamente **(somente para Adobe Commerce na infraestrutura em nuvem)** e faça logon com sua Adobe ID ou acesse por meio da [!DNL dashboard] do site da sua loja [!DNL Admin Panel].

A variável [!DNL Site-Wide Analysis Tool] o serviço está disponível em [modo de produção](https://docs.magento.com/user-guide/magento/installation-modes.html) para [!DNL Admin] usuários com permissão para acessar o usuário [recursos da função](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Se você tiver uma instalação local do Adobe Commerce, deverá instalar um [agente](../site-wide-analysis-tool/installation.md) em sua infraestrutura para usar a ferramenta.

![Painel de análise do site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Painel*

## Opção 1: Fazer logon no [!DNL Site-Wide Analysis Tool Dashboard] diretamente do [!DNL Site-Wide Analysis Tool] domínio (somente para Adobe Commerce na infraestrutura em nuvem)

Um **[!DNL Adobe ID]é obrigatório** para acessar um [!DNL Commerce] conta.
Se você já tiver uma [!DNL Commerce] conta, mas você não tem uma [!DNL Adobe ID], você pode criar um durante o processo de logon.

1. Ir para [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Clique em **[!UICONTROL Sign in with Adobe ID]** e siga os prompts.

   ![Painel de análise do site](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]tela de logon*

1. Aceite os termos e condições.

1. **<u>Nota</u>:** Sua conta deve ter direito a **[!DNL Support Permissions]** para acessar [!DNL Site-Wide Analysis Tool Dashboard].
Veja mais detalhes em [Compartilhar um [!DNL Commerce] account](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) em nosso guia do usuário.

## Opção 2: Fazer logon no [!DNL Site-Wide Analysis Tool Dashboard] do site da sua loja [!DNL Admin Panel]

### Etapa 1: verificar permissões

Verifique se [!DNL Admin] a conta de usuário tem permissão para acessar o [!DNL Site-Wide Analysis Tool] através da sua [função de usuário atribuída](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>A variável [!DNL Site-Wide Analysis Tool] o recurso de função (permissão) é **não** atribuído automaticamente. Ela DEVE ser ativada para a função de usuário e para a função atribuída individualmente a cada conta de usuário na [!UICONTROL Admin].

Para a função personalizada que necessita [!DNL Site-Wide Analysis Tool] faça o seguinte:

1. Selecione o **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** recurso de função.

   ![Painel de análise do site](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]permissão selecionada para a função*

1. Clique em **[!UICONTROL Save Role]**.

1. Notifique todos os usuários com essa função atribuída para que saiam do [!DNL Admin]e faça logon novamente.

>[!NOTE]
>
>Se você tiver verificado que a conta do usuário tem permissão para acessar o [!DNL Site-Wide Analysis Tool] e o usuário receber um erro 403 ao tentar acessar a ferramenta do [!DNL Admin], sua instância do Adobe Commerce na infraestrutura em nuvem pode ter o controle de acesso HTTP ativado. A variável [!DNL Site-Wide Analysis Tool] O painel NÃO é suportado se a autenticação HTTP estiver ativada. Para obter mais informações sobre como resolver esse problema, consulte nossa [Artigo de suporte](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Etapa 2: acesso [!DNL Site-Wide Analysis Tool]

1. No *[!UICONTROL Admin]* barra lateral, vá para **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Painel de análise do site](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]localização no [!DNL Admin Panel] no Adobe Commerce*

1. Leia o *Termos de uso* para o [!DNL Site-Wide Analysis Tool] e clique em **[!UICONTROL Accept]** para continuar.

   Cada usuário deve aceitar os Termos de Uso da sessão. Esta etapa é repetida para cada sessão conectada.


1. Na parte superior do painel, clique na guia que deseja ver.

   ![Painel de análise do site](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]informações*

## Gerar relatórios a partir do [!DNL Site-Wide Analysis Tool Dashboard]

1. No canto superior direito do painel, clique em **[!UICONTROL Generate Report]**.

1. Marque a caixa de seleção de cada **[!UICONTROL Type]** e **[!UICONTROL Priority]** que deseja incluir no relatório.

1. Clique em **[!UICONTROL Generate Report]**.

   ![Painel de análise do site](../../assets/tools/swat-report-settings.png)
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
>Após a aplicação de uma recomendação, pode levar alguns dias para que ela seja atualizada no [!DNL Site-Wide Analysis Tool Dashboard] relatório gerado.
