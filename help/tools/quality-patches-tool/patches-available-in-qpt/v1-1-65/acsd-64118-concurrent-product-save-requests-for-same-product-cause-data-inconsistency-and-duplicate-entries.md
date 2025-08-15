---
title: 'ACSD-64118: solicitações simultâneas de salvamento de produto para o mesmo produto causam inconsistência de dados e entradas duplicadas'
description: Aplique o patch ACSD-64118 para corrigir o problema do Adobe Commerce em que solicitações simultâneas para salvar e atualizar o mesmo produto resultam em inconsistência de dados ou produtos duplicados.
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: e014645e-72b2-4b3d-8b44-3daca502c950
source-git-commit: 5c84dc5c27f6e57b4116bc1a3d4fb001b55b63f1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-64118: solicitações simultâneas de salvamento de produto para o mesmo produto causam inconsistência de dados e entradas duplicadas

O patch ACSD-64118 corrige o problema em que solicitações simultâneas para salvar e atualizar o mesmo produto resultam em inconsistência de dados ou produtos duplicados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACSD-64118. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Solicitações simultâneas para salvar e atualizar o mesmo produto resultam em inconsistência de dados ou produtos duplicados.

<u>Etapas a serem reproduzidas</u>:

1. Configurar vários processos para consumidores em `env.php`:

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. Adicione uma loja adicional e uma nova loja ao site principal.
1. Envie uma solicitação de API em massa para o ponto de extremidade de storeview padrão `/rest/default/async/bulk/V1/products` com a seguinte carga para criar um produto:

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. Use a mesma carga para enviar uma solicitação de API em massa ao novo ponto de extremidade storeview `/rest/store/async/bulk/V1/products` para atualizar o produto.
1. Liberar cache.
1. Execute trabalhos cron.
1. Verifique a tabela `catalog_product_entity` para entradas do produto das etapas anteriores.

<u>Resultados esperados</u>:

* Uma única entrada para o SKU do produto deve estar presente na tabela `catalog_product_entity`.
* A primeira solicitação da API REST deve criar uma entrada de banco de dados, e todas as solicitações subsequentes devem atualizar essa entrada de banco de dados.

<u>Resultados reais</u>:

Várias entradas para o mesmo SKU estão presentes na tabela `catalog_product_entity`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
