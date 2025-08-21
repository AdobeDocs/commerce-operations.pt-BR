---
title: 'ACSD-66139: A solicitar do GraphQL falha com erro INDEFINIDO para carrinho inativos'
description: Aplicar o ACSD-66139 correção corrigir o Adobe Systems Comércio problema em que, ao colocar uma solicitar para uma carrinho inexistente ou inativa, o GraphQL retorna um código de erro NÃO DEFINIDO em vez de um específico quando mensagens de erro são traduzidas.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 16d95ae0d58dfdc88a5fab725a37d353d3ee5c96
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# ACSD-66139: Solicitar do GraphQL falha com erro &#39;NÃO DEFINIDO&#39; para carrinho inativos

O ACSD-66139 correção corrige o problema em que, ao colocar uma solicitar para uma carrinho inexistente ou inativa, o GraphQL retorna um *código de erro NÃO DEFINIDO* em vez de um específico quando mensagens de erro são traduzidas. Essa correção está disponível quando a [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalada. A ID do correção é ACSD-66139. Observe que este problema está programado para ser corrigido na Adobe Systems Comércio 2.4.9.

## Produtos e versões afetados

**A correção é criada para Adobe Systems versão Comércio:**

* Adobe Systems Comércio (todos os métodos de implantação) 2.4.7-p5

**Compatível com versões Adobe Systems Comércio:**

* Adobe Systems Comércio (todos os métodos implantação) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>O correção pode se tornar aplicável a outras versões com novas [!DNL Quality Patches Tool] versões. Para verificar se a correção é compatível com a sua versão de Adobe Systems Comércio, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade com [[!DNL Quality Patches Tool]: Search para patches página](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID da correção como palavra-chave de pesquisa para localizar a correção.

## Questão

O GraphQL retorna um *código de erro NÃO DEFINIDO* em vez de um específico ao colocar uma solicitar para uma carrinho inexistente ou inativa, se a mensagem de erro for traduzida.

<u>Etapas para reproduzir</u>:

1. Adicione `app/i18n/Magento/de_DE/de_DE.csv` e inclua a seguinte tradução em sequência de erros:

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. Criar um visualização de armazenamento no painel Admin. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**. . Clique **[!UICONTROL Create Store View]** e para **[!UICONTROL Code]**, insira o código `test`.
1. Atribua `german` um idioma ao visualização de armazenamento recém-criado.
1. Executar `setup:upgrade` e `setup:static-content:deploy -f`.
1. Execute a seguinte query GraphQL com o cabeçalho &#39;Store:test&#39;:

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

Correto resposta de erro:

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

O `error_code` retorno é *INDEFINIDO*:

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

## Aplicar o correção

Para aplicar patches individuais, use os seguintes links dependendo do método implantação:

* Adobe Systems Comércio ou Magento Open Source no local: [[!DNL Quality Patches Tool] > uso](/help/tools/quality-patches-tool/usage.md) no [!DNL Quality Patches Tool] guia.
* Adobe Systems Comércio no infraestrutura em nuvem: [atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia Comércio on Cloud Infrastructure.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: Um autoatendimento ferramenta para patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) de qualidade no guia de Ferramentas.
