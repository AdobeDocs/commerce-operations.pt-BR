---
title: 'ACSD-65775: valores "base_row_total" e "row_total" incorretos nos detalhes da ordem da API REST para várias quantidades'
description: Aplique o patch ACSD-65775 para corrigir o problema do Adobe Commerce em que os detalhes da ordem da API REST retornam valores "base_row_total" e "row_total" incorretos quando várias quantidades do mesmo item são solicitadas.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 23c78abaf28f64baf0e91bcaf89bd0e34b5bf78a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-65775: Valores incorretos de `base_row_total` e `row_total` em detalhes de pedido de API REST para várias quantidades

O patch ACSD-65775 corrige o problema em que os detalhes da ordem da API REST retornam valores `base_row_total` e `row_total` incorretos quando várias quantidades do mesmo item são solicitadas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACSD-65775. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O `base_row_total` e `row_total` na resposta da API REST dos detalhes do pedido mostram o preço unitário em vez do preço total quando várias quantidades do mesmo item são solicitadas.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos simples: simple1 com preço de US$ 10 e simple2 com preço de US$ 15.
1. Crie uma nova conta de cliente.
1. Adicione simple1 ao carrinho com a quantidade 2 e simple2 com a quantidade 3.
1. Fazer o pedido usando a conta do cliente.
1. Obtenha um token de administrador enviando uma solicitação POST a `/rest/V1/integration/admin/token` com a seguinte carga:

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. Recupere os detalhes do pedido usando uma solicitação GET para `/rest/default/V1/orders/1`.

<u>Resultados esperados</u>:

`base_row_total` e `row_total` devem refletir o preço total calculado como quantidade multiplicada pelo preço do item (por exemplo, 2 × $10 = $20 para simple1).

<u>Resultados reais</u>:

`base_row_total` e `row_total` retornam apenas o preço unitário (por exemplo, $10 para simple1 em vez de $20).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
