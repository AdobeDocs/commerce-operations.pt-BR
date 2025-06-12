---
title: 'ACSD-59786: o GraphQL retorna um erro ao buscar uma "quote_id" para uma cotação expirada'
description: Aplique o patch ACSD-59786 para corrigir o problema do Adobe Commerce em que uma consulta do GraphQL retorna um erro ao buscar uma "quote_id" para uma cotação expirada.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786: o GraphQL retorna um erro ao buscar um `quote_id` para uma cotação expirada

O patch ACSD-59786 corrige o problema em que uma consulta do GraphQL retorna um erro ao buscar um `quote_id` para uma cotação expirada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 está instalado. A ID do patch é ACSD-59786. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma consulta GraphQL retorna um erro ao buscar um `quote_id` para uma cotação expirada.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL Companies]** e **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** e definir **[!UICONTROL Enable Company]** como *Sim*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** e definir **[!UICONTROL Enable Purchase Orders]** como *Sim*.
1. Crie uma nova empresa e defina **[!UICONTROL Enable Purchase Orders]** como *Sim* para a mesma empresa.
1. Crie um produto simples e atribua-o a uma categoria.
1. Faça logon na Loja usando a conta de Administrador da empresa e crie um novo pedido usando **[!UICONTROL Purchase Order]** como método de pagamento.
1. Altere o **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Execute o comando `bin/magento c:f`.
1. Vá para o BD `quote_table` e altere os valores `created_at` e `updated_at` com um dia no passado.
1. Execute o comando `bin/magento cron:run --group="sales_clean_quotes`.
1. Execute a solicitação GraphQL fornecida abaixo usando um token autorizado para o Administrador que cria o **[!UICONTROL Purchase Order]**:

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>Resultados esperados</u>:

A consulta GraphQL retorna o `quote_id`.

<u>Resultados reais</u>:

A consulta do GraphQL retorna um erro interno do servidor.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
