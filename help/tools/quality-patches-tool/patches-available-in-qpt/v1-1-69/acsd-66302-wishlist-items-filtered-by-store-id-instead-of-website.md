---
title: 'ACSD-66302: itens da lista de desejos filtrados pela ID da loja em vez do site'
description: Aplique o patch ACSD-66302 para corrigir o problema do Adobe Commerce em que os itens da lista de desejos são filtrados pela ID da loja em vez do site em  [!DNL GraphQL] solicitações.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7f9a13a9a8cc666c8aa9d964da8aaff01913d35f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---


# ACSD-66302: itens da lista de desejos filtrados pela ID da loja em vez do site

O patch ACSD-66302 corrige o problema em que os itens da lista de desejos são filtrados pela ID de armazenamento em vez do site em solicitações [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-66302. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os itens da lista de desejos são filtrados incorretamente pela ID da loja em vez de pelo site.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Crie uma loja adicional.
1. No Admin, vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]** e defina **[!UICONTROL Enable Multiple Wish Lists]** como `Yes`.
1. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]** e defina **[!UICONTROL Add Store Code to Urls]** como `Yes`.
1. Crie uma conta de cliente.
1. Use uma solicitação [!DNL GraphQL] para recuperar o token de autenticação do cliente.
1. Faça logon como o cliente.
1. Selecione o **[!UICONTROL Default Store View]** e adicione o produto à lista de desejos.
1. Alternar exibição de repositório para *teste*.
1. Confirme se o produto ainda está na lista de desejos (comportamento correto).
1. Executar a seguinte consulta [!DNL GraphQL]:

```
{
  customer {
    wishlists {
      id
      name
      items_count
      items_v2 {
        items {
          id
          product {
            uid
            name
            sku
          }
        }
      }
    }
  }
}
```

1. Execute o query na loja padrão - o produto é exibido conforme esperado.
1. Execute a mesma consulta no armazenamento de teste - o produto não é exibido.

<u>Resultados esperados</u>:

O produto deve estar visível em todas as exibições da loja no mesmo site por meio de [!DNL GraphQL] consultas.

<u>Resultados reais</u>:

O produto desaparece da lista de desejos ao alternar visualizações da loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
