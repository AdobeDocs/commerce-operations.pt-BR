---
title: 'ACSD-47027: atualização de consulta B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] '
description: Aplique o patch ACSD-47027 para corrigir o problema do Adobe Commerce em que há uma atualização de consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  lenta.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027: atualização de [!DNL GraphQL] de B2B de consulta lenta [!UICONTROL CompanyRole]

O patch ACSD-47027 resolve o problema em que a atualização de consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] lenta não funciona como esperado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23 está instalado. A ID do patch é ACSD-47027. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A atualização de consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] lenta não funciona como esperado.

<u>Pré-requisitos</u>:

Instale o módulo B2B.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** e defina **[!UICONTROL Enable Company]** como _Sim_.
1. Acesse o front-end e crie uma empresa.
1. Depois de fazer logon como usuário da empresa, vá para **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** e adicione uma nova função.
1. Habilitar log de consultas [!UICONTROL dev] usando `bin/magento dev:que:enab`.
1. Agora envie a solicitação [!DNL GraphQL] abaixo (a ID é a ID de função codificada [!UICONTROL base64]):

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Verifique o log de consulta.
1. Você pode ver que a consulta acima é executada. Esta consulta é executada em `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Resultados esperados</u>:

O `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` precisa ser otimizado para evitar o carregamento de todos os dados disponíveis na tabela de BD **[!UICONTROL company_permissions]**.

<u>Resultados reais</u>:

O Adobe Commerce executa uma consulta sem nenhum filtro. Quando há um grande número de registros, leva muito tempo para o Adobe Commerce preparar a coleta de dados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem. 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
