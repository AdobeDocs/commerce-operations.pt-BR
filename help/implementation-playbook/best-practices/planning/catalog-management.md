---
title: Práticas recomendadas de gerenciamento de catálogo
description: Saiba mais sobre as recomendações para configurar limites de carrinho e atributos de produto, listando paginação, opções, promoções e variações.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 0%

---

# Práticas recomendadas de gerenciamento de catálogo

As práticas recomendadas de gerenciamento de catálogo descritas aqui abordam vários problemas, incluindo (mas não se limitando a):

- Limites do carrinho
- Limites de categoria
- Atributos do produto
- Paginação de lista de produtos
- Opções de produto
- Variações de produto
- Promoções

## Limites do carrinho

Para obter o melhor desempenho, use as diretrizes a seguir para gerenciar os limites do carrinho para o Adobe Commerce.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Reduzir o número de itens do carrinho

Use as estratégias a seguir para gerenciar o número de itens do carrinho

- Dividir pedidos em vários pedidos menores com um número menor de linhas usando o recurso [!UICONTROL Add Item by SKU].
- Adicione apenas a lógica personalizada e a personalização do carrinho necessária para carregar uma lista de itens.

## Limites de categoria

Configurar um grande número de categorias pode afetar o desempenho.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Reduzir o número de produtos

Use as seguintes estratégias para reduzir o número de categorias:

- Gerencie recursos exclusivos do produto por meio de atributos e opções personalizadas
- Remover categorias inativas
- Otimizar profundidade do catálogo na navegação

## Atributos do produto

Configurar muitos atributos de produto ou opções de atributos de produto pode afetar o desempenho.

>[!NOTE]
>
>Os atributos do produto especificam recursos que se aplicam globalmente a todos os produtos. As opções de atributo de produto são personalizações para especificar recursos que se aplicam a produtos específicos.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Reduzir o número de atributos

Para obter o melhor desempenho ao gerenciar produtos do Administrador e recuperar dados do produto na loja:

- Use modelos de produtos diferentes (conjuntos de atributos) para produtos diferentes.
- Aproveitar opções personalizadas e produtos complexos para gerenciamento de variações
- Minimize o número de atributos pesquisáveis.
- Remova as propriedades do produto que não são usadas.
- Armazene e gerencie atributos relacionados ao não comércio em sistemas de gerenciamento de produtos (PMS) externos.

### Reduzir o número de opções de atributo

Para obter o melhor desempenho ao gerenciar produtos do Administrador e recuperar dados do produto na loja:

- Use diferentes mecanismos de variação para criar produtos: produtos complexos, opções personalizadas como uma fonte de variações de produtos.
- Crie modelos de produtos específicos com atributos de direcionamento e opções para evitar modelos de produtos e contêineres de opções generalizados.
- Manter uma lista de opções de atributo reais.
- Gerencie informações do produto por meio de um Sistema de gerenciamento de produtos (PMS) externo.

### Reduzir o número de conjuntos de atributos

Remover conjuntos de atributos de produto não utilizados usando o MySQL.

#### Revisar configuração do conjunto de atributos

1. [Conectar ao banco de dados do site](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database).

1. Localizar o número de conjuntos de atributos usando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Remova todos os conjuntos de atributos não utilizados.

### Possível impacto no desempenho

A configuração de muitos **atributos de produto** aumenta o tamanho do modelo de produto para cada produto (estrutura EAV) e a quantidade de dados que devem ser recuperados. Esse aumento afeta as operações das seguintes maneiras:

- Aumento no tráfego de consultas SQL relacionadas à recuperação de dados do EAV e à quantidade de dados processados que resulta na diminuição da taxa de transferência do BD
- Aumento significativo no tamanho dos índices do Adobe Commerce e do índice de pesquisa de texto completo
- Atingir limites rígidos de MySQL ao criar um índice FLAT para modelos de produtos grandes e incapacidade de usá-lo

Os aumentos nos dados do produto e nos tamanhos do índice podem afetar o desempenho do site das seguintes maneiras:

- Maior tempo de resposta para a maioria dos cenários de vitrine eletrônica relacionados à navegação de catálogo, pesquisa (rápida e avançada) e navegação em camadas.
- As operações de gerenciamento de produtos no Administrador atrasam significativamente, o que pode levar a tempos limite.
- A funcionalidade Ações em massa do produto pode ser bloqueada.
- O tempo de recriação do índice para catálogos de médio e grande porte não pode ser executado diariamente devido a longos tempos de execução.

A configuração de muitas **opções de atributo** pode afetar o desempenho do site das seguintes maneiras:

- Longos tempos de solicitação e renderização nas páginas de detalhes do produto (PDP) e categoria contendo produtos complexos.
- O tempo de resposta das operações de salvamento do produto do administrador aumenta acima das metas de desempenho ideais.
- Aumento no tempo de renderização do formulário de Edição de produto.
- Check-out lento.

## Opções de produto

A configuração de muitas opções de produto por produto pode afetar o desempenho.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Reduzir o número de opções

Use as seguintes estratégias para reduzir o número de opções de produtos por produto:

- Configure produtos complexos e opções personalizadas como uma fonte de variações de produtos.
- Em vez de criar modelos de produtos globais e contêineres de opções que se aplicam a todos os produtos, use conjuntos de atributos para criar modelos de produtos específicos com atributos e opções direcionados.
- Gerencie informações do produto por meio de um Sistema de gerenciamento de produtos (PMS) externo.

### Possível impacto no desempenho

A configuração de muitas opções de produtos aumenta a quantidade de dados recuperados para cada produto em todas as operações de leitura e gravação, resultando em:

- O aumento do tráfego de consultas SQL e as operações `JOIN` mais pesadas aumentam a taxa de transferência do banco de dados.
- Aumento do tamanho dos índices do Adobe Commerce e do índice de pesquisa de texto completo.

Os aumentos listados acima podem afetar o desempenho do site das seguintes maneiras:

- Tempo de resposta mais longo para a maioria dos cenários de loja relacionados a produtos contendo muitas opções em atributos.
- Aumentos significativos no tempo necessário para concluir as operações de gerenciamento de produtos no Admin que podem levar a tempos limite, especialmente em cenários relacionados à lista de atributos e recuperação de árvore, incluindo o gerenciamento de regras de promoção.
- Pode bloquear ações em massa que concluem operações em massa assíncronas, como importação e exportação, e atribuir preços personalizados a vários produtos em um catálogo compartilhado.

## Paginação de lista de produtos

A exibição de muitos produtos por página pode afetar o desempenho.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Atualizar a configuração da lista de produtos

Se você tiver muitos produtos em uma categoria, atualize a configuração do catálogo da loja para desabilitar a opção para **Permitir todos os produtos por página**.

Depois que você desativa essa opção, o Adobe Commerce usa os controles de paginação de vitrine eletrônica de produtos para gerenciar o número de produtos exibidos nos componentes da vitrine eletrônica. Para obter instruções, consulte [Configurar controles de paginação](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Limites de SKU do produto

A configuração de muitas SKUs de produtos pode afetar o desempenho, retardando a recuperação de dados do produto e aumentando o tempo para concluir as operações ou indexações de administrador.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Reduzir o número de produtos

Use as seguintes estratégias para reduzir o número de produtos (SKUs):

- Minimizar multiplicadores—
   - A consolidação de sites reduz o multiplicador.
   - Use recursos alternativos do produto para preços personalizados para substituir o catálogo compartilhado e os multiplicadores de grupos de clientes.
   - Os grupos de clientes e o catálogo compartilhado funcionam como multiplicadores do número de SKUs efetivas em uma loja.
- Reestruturar o catálogo —
   - Reduza o número de produtos atribuídos a categorias.
   - Diminua o número de SKUs diminuindo o número de sites, grupos de clientes, catálogos compartilhados, número de produtos ou número de opções de produtos configuráveis
- Forneça mais variações de produtos usando opções personalizadas em vez de criar produtos separados.
- Levando em consideração que um SKU efetivo pode incluir uma série de permutas potenciais de preços, porque os preços podem ser especificados de forma diferente para cada loja ou grupo de clientes.
- Desative ou remova componentes não utilizados do sistema, como módulos. Consulte [Desinstalar módulos](../../../installation/tutorials/uninstall-modules.md).
- Gerenciar produtos em um Sistema de gerenciamento de plataforma (PMS) externo.

## Variações de produto

A configuração de muitas variações por produto pode afetar o desempenho.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Reduzir o número de variações

Para obter o melhor desempenho do site, use as seguintes estratégias para reduzir o número de variações de produtos:

- Reestruturar o catálogo distribuindo o número de variações entre diferentes produtos.
- Remova as opções de atributo configuráveis que não estão em estoque.
- Gerencie variações por meio de recursos alternativos, como opções personalizadas, categorias, produtos relacionados, agrupados e pacotes.

### Possível impacto no desempenho

Exceder o número recomendado de variações de produtos pode afetar o desempenho do site das seguintes maneiras:

- Longos tempos de solicitação e renderização em detalhes do produto e páginas de categoria contendo produtos complexos.
- Maior tempo de resposta para concluir as operações de Salvar no Administrador.
- Mais tempo para renderizar o formulário Edição de produto.
- Check-out lento.

## Promoções

Siga estas práticas recomendadas para configurar vendas e promoções para itens em um carrinho de compras:

- **Regras de vendas (regras de preço do carrinho)**
   - Gerenciar e remover regras não usadas.
   - Adicione condições de regra estritas (como atributo ou filtro de categoria) para a correspondência mais eficiente.
- **Cupons**
   - Remova os cupons não utilizados e expirados.
   - Gere apenas o número de cupons necessários para atender aos requisitos da campanha.

### Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

### Possível impacto no desempenho

Ter mais do que o número máximo recomendado de regras de preço do carrinho ou cupons pode afetar o desempenho do site das seguintes maneiras:

- Maior tempo de resposta quando os produtos são adicionados ao carrinho.
- Aumento do tempo para carregar e renderizar o minicart.
- Mais tempo para renderizar a página do carrinho.
- Mais tempo para renderizar o bloco **Totais** na página Check-out.
