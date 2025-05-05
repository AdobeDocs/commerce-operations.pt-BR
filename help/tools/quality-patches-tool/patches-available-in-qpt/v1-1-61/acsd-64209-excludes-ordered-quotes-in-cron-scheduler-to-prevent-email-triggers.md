---
title: 'ACSD-64209: O agendador Cron recupera cotações negociáveis sem excluir [!UICONTROL Ordered] cotações'
description: Aplique o patch ACSD-64209 para corrigir o problema do Adobe Commerce em que o agendador cron recupera todas as cotações negociáveis sem excluir aquelas com o status [!UICONTROL Ordered], fazendo com que um email ou emails sejam acionados.
feature:  B2B, Communications
role: Admin, Developer
source-git-commit: 6fbe987dca81065071b611bfe0bfd0cb7baf1938
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: O agendador Cron recupera cotações negociáveis sem excluir [!UICONTROL Ordered] cotações

O patch ACSD-64209 corrige o problema em que o agendador cron recupera todas as cotações negociáveis sem excluir aquelas com o status **[!UICONTROL Ordered]**, fazendo com que um email ou emails sejam acionados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-64209. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O agendador cron recupera todas as cotações negociáveis sem excluir aquelas com o status **[!UICONTROL Ordered]**, fazendo com que um email ou emails sejam disparados.

<u>Etapas a serem reproduzidas</u>:


1. Na barra lateral *Admin*, vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** e habilite a Cotação B2B e da Empresa.
1. Definir **[!UICONTROL Default Expiration Period]** como *1* em *Admin* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**.
1. Crie uma empresa, ative-a e faça logon como administrador da empresa.
1. Adicione um produto ao carrinho.
1. Solicitar uma cotação.
1. Na barra lateral *Admin*, vá para **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Selecione a cotação criada e clique em **[!UICONTROL Send]** para enviar a cotação de volta ao comprador.
1. Faça logon como o administrador da empresa na loja.
1. Selecione a cotação e clique em **[!UICONTROL Proceed to checkout]** para concluir a compra.
1. Verifique se o status da cotação é **[!UICONTROL Ordered]** e se não são possíveis mais ações na loja.
1. Acione o trabalho cron `negotiable_quote_send_emails`.


<u>Resultados esperados</u>:

Como a cotação foi solicitada e nenhuma outra ação pode ser tomada, nenhum email sobre a expiração da cotação deve ser enviado.

<u>Resultados reais</u>:

Um email *Cotação expira em breve* é enviado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
