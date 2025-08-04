---
title: 'ACSD-66434: [!UICONTROL Customer ID] ausente das consultas [!DNL GraphQL]  da empresa'
description: Aplique o patch ACSD-66434 para corrigir o problema do Adobe Commerce em que [!UICONTROL Customer ID] está ausente das consultas [!DNL GraphQL]  da empresa.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 422e5a9eb9948032cccaac98415cf4b92895d5a9
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# ACSD-66434: [!UICONTROL Customer ID] ausente das consultas [!DNL GraphQL] da empresa

O patch ACSD-66434 corrige o problema em que **[!UICONTROL Customer ID]** está ausente das consultas da empresa [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-66434. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta de empresa [!DNL GraphQL] retorna `null` para **[!UICONTROL Customer ID]** na estrutura da empresa.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce 2.4-develop com módulos B2B e Inventory.
1. No Administrador do Commerce, ative os recursos B2B e crie uma empresa de teste.
1. Gere um token de portador para o administrador da empresa usando a seguinte mutação [!DNL GraphQL]:

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Use o token gerado para recuperar a estrutura da empresa do cliente com a seguinte consulta [!DNL GraphQL]:

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>Resultados esperados</u>:

**[!UICONTROL Customer ID]** deve ser retornado na consulta da empresa [!DNL GraphQL].

<u>Resultados reais</u>:

**[!UICONTROL Customer ID]** retorna como `null` na consulta da empresa [!DNL GraphQL].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
