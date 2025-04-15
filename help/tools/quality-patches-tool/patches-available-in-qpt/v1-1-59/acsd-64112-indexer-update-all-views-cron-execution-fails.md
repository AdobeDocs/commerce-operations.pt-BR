---
title: 'ACSD-64112: a execução do cron "indexer_update_all_views" falha quando "MAGE_INDEXER_THREADS_COUNT" está definido'
description: Aplique o patch ACSD-64112 para corrigir o problema do Adobe Commerce em que a execução do cron "indexer_update_all_views" falha quando "MAGE_INDEXER_THREADS_COUNT" está definido.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
source-git-commit: 0078cf5fb6d6c3a8650762d7cdf5556de642e201
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112: a execução de `indexer_update_all_views` cron falha quando `MAGE_INDEXER_THREADS_COUNT` é definido

>[!NOTE]
>
>Este patch foi substituído por [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) para versões do Adobe Commerce posteriores à 2.4.7.

O patch ACSD-64112 corrige o problema em que a execução do cron `indexer_update_all_views` falha quando `MAGE_INDEXER_THREADS_COUNT` é definido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-64112. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p10

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A execução do cron `indexer_update_all_views` falha quando `MAGE_INDEXER_THREADS_COUNT` é definido com um valor maior que 2, afetando especificamente o indexador [!UICONTROL Customer Segments] com B2B habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma instância limpa com B2B.
1. Habilitar **[!UICONTROL B2B Company]** e **[!UICONTROL Shared Catalog]**.
1. Crie uma categoria.
1. Crie alguns produtos e atribua-os à categoria.
1. Executar um reindexação completo.
1. Definir os seguintes indexadores como **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Vá para o back-end e carregue a categoria recém-criada.
1. Clique em **[!UICONTROL Category Permissions]** e crie um **[!UICONTROL New Permission]** para um grupo de clientes existente.
1. Verifique se o indexador `catalogpermissions_category` tem uma lista de pendências. Execute o seguinte comando para verificar isso:

   ```
   bin/magento indexer:status
   ```

1. Defina a seguinte contagem de threads do indexador em `env.php`:

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. Execute a tarefa cron:

   ```
   bin/magento cron:run
   ```

<u>Resultados esperados</u>:

O trabalho cron deve ser executado sem problemas.

<u>Resultados reais</u>:

O trabalho cron `indexer_update_all_views` encontra o seguinte erro:

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Etapas adicionais necessárias após a instalação do patch

(Esta seção é opcional; pode haver algumas etapas necessárias após a aplicação do patch para corrigir o problema.) 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
