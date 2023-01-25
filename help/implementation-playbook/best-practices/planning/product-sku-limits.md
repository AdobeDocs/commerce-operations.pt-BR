---
title: Práticas recomendadas de limites de produto
description: Conheça as práticas recomendadas para configurar as SKUs (Product Stock Keeping Units, unidades de manutenção de estoque) do produto para maximizar o desempenho do site.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e259f9b999566447469200c93db3bc4ba06434c0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Práticas recomendadas para a configuração do SKU do produto

Para maximizar o desempenho, o máximo recomendado para as SKUs (Unidades de armazenamento de produtos) eficazes é 242 milhões. Este SKU de produto efetivo máximo é calculado como:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Em que:

- N significa o número de itens para essa categoria
- Os grupos de clientes incluem catálogos compartilhados, pois criam um grupo de clientes adicional.

Ter mais do que o número máximo de SKUs eficazes retarda a recuperação de dados do produto e aumenta o tempo para concluir as operações ou indexações do painel de administração.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Reduza o número de produtos

Use as seguintes estratégias para reduzir o número de produtos (SKUs):

- Minimizar multiplicadores—
   - A consolidação de sites reduz o multiplicador. Se você tiver 50.000 SKUs, dez sites e dez grupos de clientes, o número efetivo de SKUs é de 5 milhões. Remover cinco grupos de clientes reduz as SKUs efetivas para 2,5 milhões.
   - Use recursos de produto alternativos para preços personalizados para substituir multiplicadores de catálogo compartilhado e de grupos de clientes.
   - Tanto os grupos de clientes quanto o catálogo compartilhado funcionam como multiplicadores para o número de SKUs eficazes em uma loja.
- Reestruturar o catálogo—
   - Reduza o número de produtos atribuídos às categorias.
   - Diminua o número de SKUs diminuindo o número de sites, grupos de clientes, catálogos compartilhados, número de produtos ou o número de opções configuráveis do produto
- Forneça mais variações de produto usando opções personalizadas em vez de criar produtos separados.
- Tendo em conta que um SKU eficaz pode incluir uma série de permutas potenciais de preços, porque os preços podem ser especificados de forma diferente para cada loja ou grupo de clientes.
- Desative ou remova componentes de sistema não utilizados, como módulos. (Consulte  [Desinstalar módulos](../../../installation/tutorials/uninstall-modules.md).)
- Gerencie produtos em um PMS (Platform Management System) externo.

## Informações adicionais

- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Atribuições de produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Como trabalhar com catálogos compartilhados](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Infraestrutura em nuvem: [Configurar vários sites e lojas](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- No local: [Vários sites ou lojas](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce na infraestrutura de nuvem: Práticas recomendadas para configuração de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
