---
title: 'ACSD-65254: Notificação por email não enviada após a atualização do email do cliente por meio da mutação updateCustomerEmail [!DNL GraphQL]'
description: Aplique o patch ACSD-65254 para corrigir o problema do Adobe Commerce em que as notificações por email não eram enviadas aos clientes após atualizarem com êxito seus endereços de email em suas contas usando a mutação updateCustomerEmail [!DNL GraphQL].
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%
---
# ACSD-65254: notificação por email não enviada após a atualização do email do cliente por meio da mutação `updateCustomerEmail` [!DNL GraphQL]

O patch ACSD-65254 corrige o problema em que as notificações por email não eram enviadas aos clientes após a atualização de seus endereços de email em suas contas usando a mutação `updateCustomerEmail` [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACSD-65254. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Notificações por email não foram enviadas aos clientes após a atualização de seus endereços de email usando a mutação `updateCustomerEmail` [!DNL GraphQL].

<u>Etapas a serem reproduzidas</u>:

1. Criar usuário usando a seguinte mutação:

   ```graphql
   mutation {
       createCustomer(
           input: {
               firstname: "Test"
               lastname: "User"
               email: "test@test.com"
               password: "Admin@123"
               is_subscribed: true
           }
       ) {
           customer {
               created_at
           }
       }
   }
   ```

1. Gere um token para o usuário criado anteriormente e use-o como um token de portador:

   ```graphql
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
       token
   }
   }
   ```

1. Tente atualizar o email do usuário criado anteriormente usando o último token de portador criado:

   ```graphql
   mutation {
       updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
           customer {
               email
           }
       }
   }
   ```

<u>Resultados esperados</u>:

Os clientes devem receber notificações por email depois de atualizar os endereços de email em suas contas.

<u>Resultados reais</u>:

Somente um email de assinatura é enviado para o novo endereço; o email de confirmação da alteração do endereço de email não é enviado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
