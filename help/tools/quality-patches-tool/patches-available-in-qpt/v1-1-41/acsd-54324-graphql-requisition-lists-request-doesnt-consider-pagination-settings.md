---
title: 'ACSD-54324: a solicitação requisition_lists do GraphQL não considera as configurações de paginação'
description: Aplique o patch ACSD-54324 para corrigir o problema do Adobe Commerce em que a solicitação "requisition_lists" do GraphQL não considera configurações de paginação e retorna todos os resultados.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-54324: A solicitação `requisition_lists` do GraphQL não considera as configurações de paginação

O patch ACSD-54324 corrige o problema em que a solicitação do GraphQL `requisition_lists` não considera configurações de paginação e retorna todos os resultados. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.41 está instalado. A ID do patch é ACSD-54324. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A solicitação `requisition_lists` do GraphQL não considera configurações de paginação e retorna todos os resultados.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como administrador e navegue até **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Defina *[!UICONTROL Enable Requisition List]* como *Sim*.

1. Faça logon no front-end, vá para **[!UICONTROL My Requisition Lists]** no menu superior ou em **[!UICONTROL My Account]** e crie várias requisições (exemplo: 7).
1. Após gerar um token do cliente, execute a consulta do GraphQL `requisition_lists` para o cliente.

   * Certifique-se de que o tamanho da página seja menor que o número total de listas de requisições criadas por você (exemplo: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Observe que o valor do campo `total_count` mostra 7, quando deveria mostrar 4.

   O número de itens também mostra 7 quando deveria ser igual ao *tamanho da página*.

<u>Resultados esperados</u>:

* O número listado como *tamanho da página* é retornado em `total_count` e não o número total de registros.
* O número de itens é igual ao *tamanho de página*.

<u>Resultados reais</u>:

O número total de registros é retornado em `total_count`, mesmo se *tamanho de página* for mencionado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
