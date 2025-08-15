---
title: 'ACSD-65254: notificação por email não enviada após a atualização do email do cliente via updateCustomerEmail [!DNL GraphQL] mutation'
description: Aplique o patch ACSD-65254 para corrigir o problema do Adobe Commerce em que as notificações por email não eram enviadas aos clientes após atualizarem com êxito seus endereços de email em suas contas usando a mutação updateCustomerEmail [!DNL GraphQL] .
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '353'
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

   ```
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

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. Tente atualizar o email do usuário criado anteriormente usando o último token de portador criado:

   ```
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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
