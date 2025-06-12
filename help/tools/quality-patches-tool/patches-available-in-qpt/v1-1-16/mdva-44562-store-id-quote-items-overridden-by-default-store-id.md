---
title: 'MDVA-44562: ID de armazenamento para itens de cotação substituídos pela ID de armazenamento padrão'
description: O patch MDVA-44562 corrige o problema em que a ID de armazenamento padrão substitui a ID de armazenamento por itens de cotação para solicitações de GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 está instalada. A ID do patch é MDVA-44562. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562: ID de armazenamento para itens de cotação substituídos pela ID de armazenamento padrão

O patch MDVA-44562 corrige o problema em que a ID de armazenamento padrão substitui a ID de armazenamento por itens de cotação para solicitações de GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 está instalada. A ID do patch é MDVA-44562. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A ID da loja para itens de cotação é substituída pela ID da loja padrão para solicitações de GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma nova exibição de loja.
1. Crie um novo produto simples com nomes diferentes por exibição de loja.
1. Crie um novo cliente.
1. Obtenha o token de autorização do cliente.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Crie uma nova cotação para o cliente usando o token de autorização.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Adicione um produto ao carrinho.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Obtenha o conteúdo do carrinho para a visualização de loja padrão.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Obtenha o conteúdo do carrinho para a nova visualização de loja.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Resultados esperados</u>:

A resposta da exibição de nova loja mostra o nome do produto da exibição de nova loja.

<u>Resultados reais</u>:

A resposta da nova exibição da loja mostra a configuração do nome do produto na exibição da loja padrão.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
