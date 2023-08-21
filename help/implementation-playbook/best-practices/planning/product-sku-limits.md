---
title: Práticas recomendadas de limites de produto
description: Conheça as práticas recomendadas para configurar as Unidades de manutenção de estoque (SKUs) do produto para maximizar o desempenho do site.
role: Admin
feature: Best Practices, Catalog Management
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Práticas recomendadas para a configuração de SKU do produto

Para maximizar o desempenho, o máximo recomendado para unidades de manutenção de estoque (SKUs) de produtos eficazes é de 242 milhões. Esse SKU máximo efetivo do produto é calculado como:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Onde:

- N representa o número de itens para essa categoria
- Os grupos de clientes incluem catálogos compartilhados, pois criam um grupo de clientes adicional.

Ter mais do que o número máximo de SKUs eficazes reduz a recuperação de dados do produto e aumenta o tempo para concluir as operações ou indexações do painel de administração.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Reduzir o número de produtos

Use as seguintes estratégias para reduzir o número de produtos (SKUs):

- Minimizar multiplicadores—
   - A consolidação de sites reduz o multiplicador. Se você tiver 50.000 SKUs, dez sites e dez grupos de clientes, o número efetivo de SKUs será de 5 milhões. A remoção de cinco grupos de clientes reduz as SKUs efetivas para 2,5 milhões.
   - Use recursos alternativos do produto para preços personalizados para substituir o catálogo compartilhado e os multiplicadores de grupos de clientes.
   - Os grupos de clientes e o catálogo compartilhado funcionam como multiplicadores do número de SKUs efetivas em uma loja.
- Reestruturar o catálogo —
   - Reduza o número de produtos atribuídos a categorias.
   - Diminua o número de SKUs diminuindo o número de sites, grupos de clientes, catálogos compartilhados, número de produtos ou número de opções de produtos configuráveis
- Forneça mais variações de produtos usando opções personalizadas em vez de criar produtos separados.
- Levando em consideração que um SKU efetivo pode incluir uma série de permutas potenciais de preços, porque os preços podem ser especificados de forma diferente para cada loja ou grupo de clientes.
- Desative ou remova componentes não utilizados do sistema, como módulos. (Consulte  [Desinstalar módulos](../../../installation/tutorials/uninstall-modules.md).)
- Gerenciar produtos em um Sistema de gerenciamento de plataforma (PMS) externo.

## Informações adicionais

- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Atribuições de produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Trabalhar com catálogos compartilhados](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Infraestrutura em nuvem: [Configurar vários sites e lojas](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- No local: [Vários sites ou lojas](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce na infraestrutura em nuvem: práticas recomendadas para configuração de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
