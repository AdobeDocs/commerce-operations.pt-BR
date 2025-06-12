---
title: 'ACSD-51739: Erro ao solicitar "structure_id" na solicitação do GraphQL de "CompanyTeam"'
description: Aplique o patch ACSD-51739 para corrigir o problema do Adobe Commerce em que um erro é retornado quando o "structure_id" é solicitado em uma solicitação do GraphQL "CompanyTeam".
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: Erro ao solicitar `structure_id` em `CompanyTeam` solicitação GraphQL

O patch ACSD-51739 corrige o problema em que um erro é retornado quando o `structure_id` é solicitado em uma solicitação do GraphQL `CompanyTeam`. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 está instalado. A ID do patch é ACSD-51739. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um erro é retornado quando o `structure_id` é solicitado em uma solicitação GraphQL `CompanyTeam`.

<u>Etapas a serem reproduzidas</u>

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** e defina *[!UICONTROL Enable Company]* como *Sim*.
1. Crie uma empresa junto com um usuário administrador de empresa.
1. Crie um novo cliente (*customer1*) e atribua a empresa (criada acima) a este cliente.
1. No front-end, faça logon como o usuário administrador da empresa.
1. Crie uma equipe de empresa e atribua *customer1* à equipe usando o recurso arrastar e soltar.
1. Executar a seguinte consulta GraphQl da empresa, que inclui `CompanyTeam` com `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Verifique a resposta do GraphQL.

<u>Resultados esperados</u>:

Nenhum erro é retornado e todos os dados solicitados estão presentes na resposta do GraphQL.

<u>Resultados reais</u>:

* A resposta contém um *Erro interno do servidor*.
* `var/log/exception.log` contém:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
