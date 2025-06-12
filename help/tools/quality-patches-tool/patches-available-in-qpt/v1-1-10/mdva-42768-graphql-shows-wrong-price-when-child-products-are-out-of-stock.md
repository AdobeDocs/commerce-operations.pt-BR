---
title: 'MDVA-42768: o GraphQL mostra o preço errado quando os produtos infantis estão indisponíveis'
description: O patch MDVA-42768 corrige o problema em que o GraphQL mostra o preço errado quando os produtos secundários de um produto configurável estão indisponíveis. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-42768. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: GraphQL, Orders, Products
role: Admin
exl-id: 9f6ab418-2267-4548-952a-17dc8295f632
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-42768: o GraphQL mostra o preço errado quando os produtos infantis estão indisponíveis

O patch MDVA-42768 corrige o problema em que o GraphQL mostra o preço errado quando os produtos secundários de um produto configurável estão indisponíveis. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-42768. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando os produtos derivados de um produto configurável estiverem esgotados e a configuração Exibir Produtos Não Estocados estiver habilitada, a consulta GraphQL mostrará o preço normal do produto como **0**.

<u>Pré-requisitos</u>:

Dados de amostra estão instalados.

<u>Etapas a serem reproduzidas</u>:

1. Habilite a configuração de produto Fora de Estoque no Administrador do Commerce acessando **Lojas** > **Configuração** > **Catálogo** > **Inventário**.
1. Crie um produto configurável e atribua a ele um produto filho simples.
1. Defina o estoque do produto variante (simples) como **Sem Estoque**.
1. Reindexar.
1. Execute a consulta do GraphQL abaixo:

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. Verifique a seção de resposta `minimum_price` > `regular price`.

<u>Resultados esperados</u>:

O preço regular mínimo não é exibido como 0 em resposta.

<u>Resultados reais</u>:

O preço regular mínimo = 0 em resposta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
