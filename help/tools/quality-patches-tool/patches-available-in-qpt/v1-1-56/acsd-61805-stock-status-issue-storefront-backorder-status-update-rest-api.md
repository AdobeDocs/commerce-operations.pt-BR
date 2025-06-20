---
title: 'ACSD-61805: corrige o problema de estoque na loja após a atualização do status do backorder por meio da API REST'
description: Aplique o patch ACSD-61805 para corrigir o problema do Adobe Commerce em que os produtos permanecem sem estoque na loja depois de atualizar o status do backorder por meio da API REST
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61805: corrige o problema de estoque na loja após a atualização do status do backorder por meio da API REST

O patch ACSD-61805 corrige o problema em que os produtos permanecem sem estoque na loja após a atualização do status do backorder por meio da API REST. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-61805. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos permanecem sem estoque na loja após a atualização do status do backorder por meio da API REST.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma instância limpa com dados de amostra.
1. Crie uma nova origem de inventário.
1. Crie um novo estoque de estoque e atribua a nova origem a ele.
1. Atribua a nova origem ao produto 24-MB01.
1. Defina **[!UICONTROL Source Item Status]** como `In Stock` para ambas as fontes de produtos.
1. Defina a quantidade (**[!UICONTROL QTY]**) como *0* para ambas as quantidades de produtos.
1. Salve o produto.
1. Buscar o token de administrador nesta URL de ponto de extremidade: `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. Atualizar o produto usando o ponto de extremidade: `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. Execute os trabalhos cron duas vezes (uma para criar agendamentos e outra para executar o agendamento):

   ```bash
   bin/magento cron:run
   ```

1. Acesse o front-end e verifique o produto.

<u>Resultados esperados</u>:

O produto deve estar *Em Estoque*.

<u>Resultados reais</u>:

O produto está *esgotado*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
