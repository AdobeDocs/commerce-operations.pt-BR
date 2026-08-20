---
title: 'MDVA-37234: Adicionar item ao carrinho várias vezes cria item de linha duplicado'
description: O patch MDVA-37234 corrige o problema em que adicionar um item ao carrinho várias vezes (solicitação paralela) para o mesmo SKU cria um item de linha duplicado para a mesma ID de carrinho. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 está instalada. A ID do patch é MDVA-37234. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Orders, Shopping Cart
role: Admin
exl-id: d4e9fca1-7fba-4a33-9c5e-c9695cbfc61c
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-37234: Adicionar item ao carrinho várias vezes cria item de linha duplicado

O patch MDVA-37234 corrige o problema em que adicionar um item ao carrinho várias vezes (solicitação paralela) para o mesmo SKU cria um item de linha duplicado para a mesma ID de carrinho. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3 está instalada. A ID do patch é MDVA-37234. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.6, 2.4.1 e 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.3.7-p1 e 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Adicionar um item ao carrinho várias vezes (solicitação paralela) para o mesmo SKU cria um item de linha duplicado para a mesma ID do carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com SKU = simple1.
1. Crie um cliente.
1. Gere um token do cliente para fazer a solicitação do GraphQL.

   <pre>
    <code class="language-graphql">
    mutation {
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        {
            token
        }
    }
    </code>
    </pre>

1. Use o token mencionado na etapa 3 para criar um carrinho vazio para o cliente.

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

1. Crie um script para fazer duas solicitações `addSimpleProductsToCart` em execução em paralelo. Por exemplo:

   <pre>
    <YOUR_ACCESS_TOKEN><YOUR_CART_ID><YOUR_ACCESS_TOKEN><YOUR_CART_ID>
    </pre>

1. Execute o script.

<u>Resultados esperados</u>:

Somente uma linha de produtos com uma quantidade total (três, neste caso) é criada no carrinho de compras.

<u>Resultados reais</u>:

Duas linhas separadas para o mesmo produto são criadas no carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre correções de qualidade para o Adobe Commerce, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
