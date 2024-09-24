---
title: "ACSD-53098: os produtos no catálogo compartilhado não refletem no front-end"
description: Aplique o patch ACSD-53098 para corrigir o problema do Adobe Commerce em que os produtos atribuídos a um catálogo compartilhado não refletem no front-end ao executar um índice parcial.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-53098: os produtos no catálogo compartilhado não refletem no front-end

O patch ACSD-53098 corrige o problema em que os produtos atribuídos a um catálogo compartilhado não são refletidos no front-end ao executar um índice parcial. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.38 está instalado. A ID do patch é ACSD-53098. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos atribuídos a um catálogo compartilhado por meio da API não são exibidos no front-end depois que o indexador parcial executa o trabalho cron, seguido pelo cron do consumidor.

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL RabbitMQ] como o serviço de fila.
1. Alternar indexadores para o modo **[!UICONTROL Update on Schedule]**.
1. Crie um catálogo compartilhado e atribua-o a uma empresa.
1. Crie um produto simples e atribua-o a uma categoria. Executar o reindexação parcial:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Use a solicitação de API a seguir para atribuir o produto criado ao catálogo compartilhado.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Execute o seguinte cron para limpar as filas e execute o reindexação parcial:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Faça logon no front-end como o usuário da empresa.
1. Verifique a página de categoria de front-end.

<u>Resultados esperados</u>:

Os produtos recém-atribuídos são exibidos no front-end.

<u>Resultados reais</u>:

Os produtos recém-atribuídos não aparecem no front-end.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
