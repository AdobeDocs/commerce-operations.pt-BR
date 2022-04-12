---
title: Como acessar [!DNL Site-Wide Analysis Tool]
description: Saiba como acessar o [!DNL Site-Wide Analysis Tool]
source-git-commit: c7fabdd83e03a288d627b70d48cdf57184d43603
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Como acessar o [!DNL Site-Wide Analysis Tool]

O [!DNL Site-Wide Analysis Tool] está disponível em [modo de produção](https://docs.magento.com/user-guide/magento/installation-modes.html) para [!DNL Admin] usuários com permissão para acessar o usuário [recursos da função](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Se você tiver uma instalação local do Adobe Commerce, instale um [agente](../site-wide-analysis-tool/installation.md) em sua infraestrutura para usar a ferramenta.

![Painel de análise do site](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Painel*

## Etapa 1: Verificar permissões

Verifique se a variável [!DNL Admin] a conta de usuário tem permissão para acessar o [!DNL Site-Wide Analysis Tool] através de [função de usuário atribuída](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>O [!DNL Site-Wide Analysis Tool] recurso de função (permissão) é **not** atribuído automaticamente. ELE DEVE ser ativado para a função de usuário e a função atribuída individualmente a cada conta de usuário no [!UICONTROL Admin].

Para a função personalizada que precisa [!DNL Site-Wide Analysis Tool] , faça o seguinte:

1. Selecione o **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** recurso de função.

   ![Painel de análise do site](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]permissão selecionada para a função*

1. Clique em **[!UICONTROL Save Role]**.

1. Notificar quaisquer usuários aos quais essa função tenha sido atribuída para sair do [!DNL Admin]e entre novamente.

>[!NOTE]
>
>Se tiver verificado que a conta de usuário tem permissão para acessar o [!DNL Site-Wide Analysis Tool] e o usuário recebe um erro 403 ao tentar acessar a ferramenta do [!DNL Admin], sua instância do Adobe Commerce na infraestrutura de nuvem pode ter o controle de acesso HTTP ativado. O [!DNL Site-Wide Analysis Tool] O painel NÃO é compatível se você tiver a autenticação HTTP ativada. Para obter mais informações sobre como resolver esse problema, consulte nossa [Artigo de suporte](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

## Etapa 2: Acesso [!DNL Site-Wide Analysis Tool]

1. No *[!UICONTROL Admin]* barra lateral, vá para **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

1. Leia o *Termos de uso* para [!DNL Site-Wide Analysis Tool] e clique em **[!UICONTROL Accept]** para continuar.

   Cada usuário precisa aceitar os Termos de Uso para a sessão. Esta etapa é repetida para cada sessão conectada.

   ![Painel de análise do site](../../assets/tools/swat-tos.png)
   *Termos de uso*

1. Na parte superior do painel, clique na guia que deseja visualizar.

   ![Painel de análise do site](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]informações*

## Etapa 3: Gerar relatório

1. No canto superior direito do painel, clique em **[!UICONTROL Generate Report]**.

1. Marque a caixa de seleção de cada **[!UICONTROL Type]** e **[!UICONTROL Priority]** que você deseja incluir no relatório.

1. Clique em **[!UICONTROL Generate Report]**.

   ![Painel de análise do site](../../assets/tools/swat-report-settings.png)
   *Configurações do relatório*

| GUIA | DESCRIÇÃO |
| --- | --- |
| Painel | Mostra a integridade do seu sistema com notificações e recomendações atuais por prioridade. |
| Informações | Fornece informações de contato do cliente e um resumo dos tíquetes atuais, com informações detalhadas sobre cada produto Adobe Commerce instalado. |
| Recommendations | Lista recomendações com base nas práticas recomendadas para solucionar problemas detectados no site. |
| Exceções | Lista erros lançados pelo aplicativo causados por condições anormais sem um manipulador de erros. |
| Extensões | Lista todas as extensões de terceiros e bibliotecas de terceiros. |

>[!NOTE]
>
>Depois de aplicar uma recomendação, pode levar alguns dias para que seja atualizada no [!DNL Site-Wide Analysis Tool] Painel ou relatório gerado.
