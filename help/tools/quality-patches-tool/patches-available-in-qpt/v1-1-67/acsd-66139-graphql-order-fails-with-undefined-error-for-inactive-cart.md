---
title: 'ACSD-66139: falha no pedido do GraphQL com erro UNDEFINED para carrinho inativo'
description: Aplique o patch ACSD-66139 para corrigir o problema do Adobe Commerce em que, ao fazer um pedido para um carrinho inexistente ou inativo, o GraphQL retorna um código de erro INDEFINIDO em vez de um específico quando as mensagens de erro são traduzidas.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: 5a1a94ca-f274-4098-8b44-d3f1a0ea65a1
source-git-commit: 8681dd706e614f86bbee36c182b47491ec707196
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-66139: falha no pedido do GraphQL com o erro &quot;UNDEFINED&quot; para carrinho inativo

O patch ACSD-66139 corrige o problema em que, ao fazer um pedido para um carrinho inexistente ou inativo, o GraphQL retorna um código de erro *UNDEFINED* em vez de um código específico quando as mensagens de erro são traduzidas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-66139. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para o ícone mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O GraphQL retorna um código de erro *UNDEFINED* em vez de um código específico ao fazer um pedido para um carrinho inexistente ou inativo, caso a mensagem de erro seja traduzida.

<u>Etapas a serem reproduzidas</u>:

1. Adicionar `app/i18n/Magento/de_DE/de_DE.csv` e incluir a seguinte conversão de cadeia de caracteres de erro:

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. No painel Admin, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** > **[!UICONTROL Create Store View]** para criar um modo de exibição de loja.
1. Defina **[!UICONTROL Code]** como *teste*.
1. Atribua o idioma `german` à exibição de repositório recém-criada.
1. Executar `setup:upgrade` e `setup:static-content:deploy -f`.
1. Execute a seguinte consulta GraphQL com o cabeçalho `Store:test`:

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>Resultados esperados</u>:

Resposta de erro correta:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>Resultados reais</u>:

O `error_code` retornado é *UNDEFINED*:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
