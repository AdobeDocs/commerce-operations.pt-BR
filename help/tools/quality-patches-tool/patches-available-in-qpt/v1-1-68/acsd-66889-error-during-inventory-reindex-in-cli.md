---
title: 'ACSD-66889: erro durante a reindexação do inventário na CLI'
description: Aplique o patch ACSD-66889 para corrigir o problema do Adobe Commerce que aciona um erro ao executar o indexador de inventário.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9631e0864b2ad8fc09734aedd476e96852cd70fb
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# ACSD-66889: erro durante a reindexação do inventário na CLI

O patch ACSD-66889 corrige o erro que ocorre ao executar o indexador de inventário. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66889.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p13

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao executar o indexador de inventário, o processo lança um aviso de desativação e falha ao ser concluído devido à sintaxe de sequência de caracteres desatualizada.

<u>Etapas a serem reproduzidas</u>:

1. Execute a reindexação do inventário usando o comando da CLI:

   ```
   php bin/magento indexer:reindex inventory
   ```

<u>Resultados esperados</u>:

A CLI recria o indexador de inventário com êxito.

<u>Resultados reais</u>:

A CLI gera um erro de funcionalidade obsoleta, e os índices de inventário permanecem no estado *Reindexação necessária*:

```
Deprecated Functionality: Using ${var} in strings is deprecated, use {$var} instead in /home/vendor/magento/module-elasticsearch-catalog-permissions/Model/Adapter/FieldMapper/Product/FieldProvider/FieldName/Resolver/CategoryPermission.php on line 24
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
