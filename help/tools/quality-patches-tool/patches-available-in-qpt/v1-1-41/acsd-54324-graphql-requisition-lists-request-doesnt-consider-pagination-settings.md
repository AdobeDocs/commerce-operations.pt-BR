---
title: 'ACSD-54324: a solicitação requisition_lists do GraphQL não considera as configurações de paginação'
description: Aplique o patch ACSD-54324 para corrigir o problema do Adobe Commerce em que a solicitação "requisition_lists" do GraphQL não considera configurações de paginação e retorna todos os resultados.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '453'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A solicitação `requisition_lists` do GraphQL não considera configurações de paginação e retorna todos os resultados.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como administrador e navegue até **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Defina *[!UICONTROL Enable Requisition List]* como *Sim*.

1. Faça logon no front-end, vá para **[!UICONTROL My Requisition Lists]** no menu superior ou em **[!UICONTROL My Account]** e crie várias requisições (exemplo: 7).
1. Após gerar um token do cliente, execute a consulta do GraphQL `requisition_lists` para o cliente.

   * Certifique-se de que o tamanho da página seja menor que o número total de listas de requisições criadas por você (exemplo: 4)

   ```graphql
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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
