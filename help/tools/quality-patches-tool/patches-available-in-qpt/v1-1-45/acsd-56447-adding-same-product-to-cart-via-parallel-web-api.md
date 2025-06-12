---
title: 'ACSD-56447: Adicionar o mesmo produto ao carrinho por meio da API REST da Web paralela resulta em dois itens separados no carrinho'
description: Aplique o patch ACSD-56447 para corrigir o problema do Adobe Commerce em que adicionar o mesmo produto ao carrinho por meio de solicitações paralelas de API REST da Web resulta em dois itens separados no carrinho.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: ef0b2ce7-74f5-47b6-a44c-bda898c444b2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56447: Adicionar o mesmo produto ao carrinho por meio da API REST da Web paralela resulta em dois itens separados no carrinho

O patch ACSD-56447 corrige o problema em que adicionar o mesmo produto ao carrinho por meio de solicitações paralelas de API REST da Web resulta em dois itens separados no carrinho. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 está instalado. A ID do patch é ACSD-56447. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Adicionar o mesmo produto ao carrinho por meio de solicitações paralelas de API REST da Web resulta em dois itens separados no carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Gere um token de cliente para fazer a solicitação de chamadas de API REST usando [!DNL Postman].
1. Crie um carrinho de compras para o cliente.
1. Use o token gerado acima para criar um carrinho vazio para o cliente.
1. Use o CURL para fazer duas solicitações `AddProductsToCart` executadas em paralelo. Siga as instruções no [Tutorial de processamento de pedidos](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) na documentação do desenvolvedor.

<u>Resultados esperados</u>:

Itens com várias quantidades são mostrados em uma linha.

<u>Resultados reais</u>:

Os mesmos SKUs são mostrados em vários itens de linha.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
