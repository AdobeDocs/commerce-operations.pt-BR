---
title: 'ACSD-59083: Erros de tabela ou exibição base não encontrados durante atualizações simultâneas do mview'
description: Aplique o patch ACSD-59083 para corrigir o problema do Adobe Commerce em que determinadas operações de atualização de banco de dados falham com o erro "Tabela ou exibição base não encontrada".
feature: System
role: Admin, Developer
source-git-commit: 7f091ff8db7973c4290e0412d19e9088f1220cef
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-59083: *Tabela ou exibição base não encontrada* erros durante atualizações `mview` simultâneas

O patch ACSD-59083 corrige o problema em que determinadas operações de atualização do banco de dados falham com o erro &#39;Tabela base ou exibição não encontrada&#39; quando as atualizações do `mview` são executadas simultaneamente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-59083. Observe que o problema foi corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Certas operações de atualização de banco de dados resultam em erros de &#39;Tabela ou exibição base não encontrada&#39; quando as atualizações `mview` são executadas simultaneamente.

<u>Etapas a serem reproduzidas</u>:

1. Defina o modo do indexador como **[!UICONTROL Update on Schedule]**.
1. Inserir registros em `cl` tabelas usando os seguintes comandos SQL:

   ```
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. Instale o perfil `setup/performance-toolkit/profiles/ce/small.xml`.
1. Adicione um ponto de interrupção no arquivo `magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php` na linha 72.
1. Limpe o cache.
1. Clique em **[!UICONTROL Add to Cart]** em qualquer produto.
1. Iniciar o trabalho cron quando a execução atingir o ponto de interrupção.
1. Retome o processo após iniciar o trabalho cron.

<u>Resultados esperados</u>:

As operações do banco de dados são executadas com êxito sem erros.

<u>Resultados reais</u>:

Ocorre um erro durante a execução:

```
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
