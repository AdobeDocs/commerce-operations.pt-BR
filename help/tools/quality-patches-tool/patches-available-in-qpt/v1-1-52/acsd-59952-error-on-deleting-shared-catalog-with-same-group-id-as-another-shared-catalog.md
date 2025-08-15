---
title: 'ACSD-59952: erro ao excluir o catálogo compartilhado com a mesma ID de grupo de outro catálogo compartilhado'
description: Aplique o patch ACSD-59952 para corrigir o problema do Adobe Commerce em que um erro é lançado ao excluir um catálogo compartilhado com o mesmo "customer_group_id" como outro catálogo compartilhado.
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952: erro ao excluir o catálogo compartilhado com a mesma ID de grupo de outro catálogo compartilhado

O patch ACSD-59952 corrige o erro lançado ao excluir catálogos compartilhados com o mesmo `customer_group_id` que outro catálogo compartilhado. Isso impede ainda mais que os usuários criem esses catálogos compartilhados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 está instalado. A ID do patch é ACSD-59952. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Não é possível criar um novo catálogo compartilhado com o mesmo `customer_group_id` que outro catálogo compartilhado. No entanto, ao fazer isso, tentar excluir o catálogo compartilhado com o mesmo `customer_group_id` gera um erro.

<u>Pré-requisitos</u>:

Instale os módulos B2B do Adobe Commerce.

<u>Etapas a serem reproduzidas</u>:

1. Crie vários catálogos compartilhados atribuídos ao mesmo `customer_group_id` usando a seguinte chamada de API REST:

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Tente excluir qualquer um dos catálogos compartilhados usando a seguinte chamada de API REST:

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>Resultados esperados</u>:

* Não é possível criar vários catálogos compartilhados atribuídos ao mesmo `customer_group_id`.
* O catálogo compartilhado no caso acima foi excluído com sucesso.

<u>Resultados reais</u>:

* É possível criar vários catálogos compartilhados atribuídos ao mesmo `customer_group_id`.
* O seguinte erro é retornado ao tentar excluir o catálogo compartilhado com o mesmo `customer_group_id`: *Não é possível excluir o catálogo compartilhado*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
