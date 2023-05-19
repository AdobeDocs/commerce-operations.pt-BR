---
title: Práticas recomendadas de configuração de atributos do produto
description: Saiba como otimizar o desempenho do Adobe Commerce limitando o número de atributos de produto, opções de atributo e conjuntos de atributos
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Práticas recomendadas para a configuração do atributo de produto

- Para obter o melhor desempenho, não configure mais do que o número máximo recomendado de atributos de produto ou opções de atributos de produto.

- **Atributos do produto**—
   - Para a versão 2.3.x e 2.4.0 a 2.4.1-p1 do Adobe Commerce, configure no máximo 500 atributos
   - Para a versão 2.4.2 e posterior do Adobe Commerce, configure até 1500 atributos de produto
- **Opções de atributo de produto**-Configurar até 100 opções de atributo para cada atributo
- **Conjuntos de atributos do produto**-Configure no máximo 1.000 conjuntos de atributos _

>[!NOTE]
>
>Os atributos do produto especificam recursos que se aplicam globalmente a todos os produtos. As opções de atributo de produto são personalizações para especificar recursos que se aplicam a produtos específicos.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Reduzir o número de atributos do produto

Para obter o melhor desempenho ao gerenciar produtos do Administrador e recuperar dados do produto na loja:

- Use modelos de produtos diferentes (conjuntos de atributos) para produtos diferentes.
- Aproveitar opções personalizadas e produtos complexos para gerenciamento de variações
- Minimize o número de atributos pesquisáveis.
- Remova as propriedades do produto que não são usadas.
- Armazene e gerencie atributos relacionados ao não comércio em sistemas de gerenciamento de produtos (PMS) externos.

## Reduzir número de opções de atributo de produto

Para obter o melhor desempenho ao gerenciar produtos do Administrador e recuperar dados do produto na loja:

- Use diferentes mecanismos de variação para criar produtos: produtos complexos, opções personalizadas como uma fonte de variações de produtos.
- Crie modelos de produtos específicos com atributos de direcionamento e opções para evitar modelos de produtos e contêineres de opções generalizados.
- Manter uma lista de opções de atributo reais.
- Gerencie informações do produto por meio de um Sistema de gerenciamento de produtos (PMS) externo.

## Reduzir o número de conjuntos de atributos do produto

Remover conjuntos de atributos de produto não utilizados usando o MySQL.

### Revisar configuração do conjunto de atributos

1. [Conectar ao banco de dados do site](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Localizar o número de conjuntos de atributos usando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Remova todos os conjuntos de atributos não utilizados.

## Possíveis impactos no desempenho

Configuração de muitos **atributos do produto** aumenta o tamanho do modelo de produto para cada produto (estrutura EAV) e a quantidade de dados que devem ser recuperados. Esse aumento afeta as operações das seguintes maneiras:

- Aumento no tráfego de consultas SQL relacionadas à recuperação de dados do EAV e à quantidade de dados processados que resulta na diminuição da taxa de transferência do BD
- Aumento significativo no tamanho dos índices do Adobe Commerce e do índice de pesquisa de texto completo
- Atingir limites rígidos de MySQL ao criar um índice FLAT para modelos de produtos grandes e incapacidade de usá-lo

Os aumentos nos dados do produto e nos tamanhos do índice podem afetar o desempenho do site das seguintes maneiras:

- Maior tempo de resposta para a maioria dos cenários de vitrine eletrônica relacionados à navegação de catálogo, pesquisa (rápida e avançada) e navegação em camadas.
- As operações de gerenciamento de produtos no Administrador atrasam significativamente, o que pode levar a tempos limite.
- A funcionalidade Ações em massa do produto pode ser bloqueada.
- O tempo de recriação do índice para catálogos de médio e grande porte não pode ser executado diariamente devido a longos tempos de execução.

Configuração de muitos **opções de atributo** podem afetar o desempenho do site das seguintes maneiras:

- Longos tempos de solicitação e renderização nas páginas de detalhes do produto (PDP) e categoria contendo produtos complexos.
- O tempo de resposta das operações de salvamento do produto do administrador aumenta acima das metas de desempenho ideais.
- Aumento no tempo de renderização do formulário de Edição de produto.
- Check-out lento.

## Informações adicionais

- [Visão geral dos atributos do produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Conjuntos de atributos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Tutoriais de personalização > Personalizar o formulário de criação de produtos](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
