---
title: Práticas recomendadas de configuração de atributos do produto
description: Saiba como otimizar o desempenho do Adobe Commerce limitando o número de atributos de produto, opções de atributo e conjuntos de atributos
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Práticas recomendadas para a configuração do atributo do produto

- Para um melhor desempenho, não configure mais do que o número máximo recomendado de atributos de produto ou opções de atributos de produto.

- **Atributos do produto**—
   - Para Adobe Commerce versão 2.3.x e 2.4.0 para 2.4.1-p1, configure no máximo 500 atributos
   - Para o Adobe Commerce versão 2.4.2 e posterior, configure até 1500 atributos de produto
- **Opções de atributo do produto**-Configure até 100 opções de atributo para cada atributo
- **Conjuntos de atributos do produto**-Configure um máximo de 1000 conjuntos de atributos _

>[!NOTE]
>
>Os atributos do produto especificam recursos que se aplicam globalmente a todos os produtos. As opções de atributos do produto são personalizações para especificar recursos que se aplicam a produtos específicos.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Reduzir o número de atributos do produto

Para obter o melhor desempenho ao gerenciar produtos do Administrador e recuperar dados de produtos na loja:

- Use diferentes modelos de produto (conjuntos de atributos) para diferentes produtos.
- Aproveite as opções personalizadas e os produtos complexos para o gerenciamento de variações
- Minimize o número de atributos pesquisáveis.
- Remova as propriedades do produto que não forem usadas.
- Armazene e gerencie atributos não relacionados ao comércio em sistemas de gerenciamento de produtos externos (PMS).

## Reduzir o número de opções de atributos do produto

Para obter o melhor desempenho ao gerenciar produtos do Administrador e recuperar dados de produtos na loja:

- Use diferentes mecanismos de variação para criar produtos: produtos complexos, opções personalizadas como fonte de variações de produto.
- Crie modelos de produto específicos com atributos e opções de direcionamento para evitar modelos de produto generalizados e contêineres de opções.
- Mantenha uma lista de opções de atributos reais.
- Gerencie informações do produto por meio de um PMS (Product Management System, sistema de gerenciamento de produtos) externo.

## Reduza o número de conjuntos de atributos de produto

Remova conjuntos de atributos de produto não utilizados usando o MySQL.

### Revisar configuração do conjunto de atributos

1. [Conectar-se ao banco de dados do site](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Localizar o número de conjuntos de atributos usando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Remova quaisquer conjuntos de atributos não utilizados.

## Potenciais impactos no desempenho

Configurando muitas **atributos do produto** aumenta o tamanho do modelo do produto para cada produto (estrutura de EAV) e a quantidade de dados que devem ser recuperados. Esse aumento afeta as operações das seguintes maneiras:

- Aumento do tráfego de consultas SQL relacionado à recuperação de dados EAV e da quantidade de dados processados que resulta em redução da taxa de transferência de banco de dados
- Aumento significativo no tamanho dos índices do Adobe Commerce e no índice de pesquisa de texto completo
- Atingir limites rígidos do MySQL ao criar um índice FLAT para modelos de produtos de grande porte e não poder usá-lo

Os aumentos nos dados do produto e tamanhos de índice podem afetar o desempenho do site das seguintes maneiras:

- Aumento do tempo de resposta para a maioria dos cenários de loja relacionados à navegação em catálogos, pesquisa (rápida e avançada) e navegação em camadas.
- As operações de gerenciamento de produtos no Administrador demoram bastante, o que pode resultar em tempos limite.
- A funcionalidade Ações em massa do produto pode ser bloqueada.
- O tempo de reconstrução de índice para catálogos de médio e grande porte não pode ser executado diariamente devido a longos tempos de execução.

Configurando muitas **opções de atributo** pode afetar o desempenho do site das seguintes maneiras:

- Longos tempos de solicitação e renderização nos detalhes do produto (PDP) e nas páginas de categoria contendo produtos complexos.
- O tempo de resposta das operações de salvamento de produtos de administração aumenta acima dos objetivos ideais de desempenho.
- Aumento do tempo de renderização do formulário de edição de produto.
- Check-out lento.

## Informações adicionais

- [Visão geral dos atributos do produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Conjuntos de atributos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Tutoriais de personalização > Personalizar formulário de criação de produto](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)

