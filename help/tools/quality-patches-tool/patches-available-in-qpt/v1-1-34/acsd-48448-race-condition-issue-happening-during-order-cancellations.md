---
title: 'ACSD-48448: Problema de condição de corrida durante cancelamentos de pedidos, causando entrada duplicada na tabela inventory_reservation'
description: Aplique o patch ACSD-48448 para corrigir o problema de desempenho do Adobe Commerce em que o problema de condição de corrida ocorre durante os cancelamentos de pedidos, o que causa entradas duplicadas na tabela inventory_reservation.
feature: Orders, Checkout
role: Admin
exl-id: c1905b60-4607-454c-975b-77b0056661ad
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48448: problema de condição *[!UICONTROL Race]* durante cancelamentos de pedidos, causando entrada duplicada na tabela `inventory_reservation`

O patch ACSD-48448 corrige o problema em que a condição *[!UICONTROL Race]* ocorre durante cancelamentos de pedidos, o que causa entradas duplicadas na tabela `inventory_reservation`. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.34 está instalado. A ID do patch é ACSD-48448. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2 e 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O problema de condição *[!UICONTROL Race]* ocorre durante cancelamentos de pedidos, o que causa entradas duplicadas na tabela `inventory_reservation`.

<u>Etapas a serem reproduzidas</u>:

1. Fazer um pedido.
1. Verifique a tabela `inventory_reservation` para verificar se há um registro para o evento `order_placed`.
1. Execute o script anexado para cancelar o pedido em paralelo (lembre-se de alterar o URL e orderID).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Resultados esperados</u>:

Os registros não são duplicados.

<u>Resultados reais</u>:

Registros duplicados são criados na tabela `inventory_reservation` para `order_canceled`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
