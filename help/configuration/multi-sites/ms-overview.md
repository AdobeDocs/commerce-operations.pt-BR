---
title: Vários sites ou lojas
description: Saiba como iniciar vários sites ou implementar visualizações de loja com diferentes opções, domínios e conteúdo.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Vários sites ou lojas

Uma única instância do software Adobe Commerce permite iniciar vários sites ou armazenar exibições que usam atributos e conteúdo diferentes, como:

- Idiomas padrão
- Nomes de domínio
- Categorias
- Produtos
- Moedas

Essa solução flexível permite que uma base de código do Commerce e o Administrador administrem e exibam diferentes lojas. Você configura os sites, lojas e visualizações de loja no Administrador. Use determinadas variáveis em hosts virtuais para iniciar o aplicativo Commerce usando esses sites ou exibições de loja.

Um uso típico é configurar lojas com opções diferentes em domínios diferentes. Por exemplo, você pode ter um conjunto de categorias e produtos em um domínio e outro conjunto de categorias e produtos em um domínio separado em um idioma diferente.

Você configura os sites, lojas e visualizações de loja no Administrador de comércio. Use o `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` em hosts virtuais para iniciar o aplicativo Commerce usando esses sites ou exibições de loja.

Considere os seguintes termos:

- **Site**—é o contêiner de nível superior para sites, métodos de delivery, métodos de pagamento e muito mais. Para criar sites completamente separados que não compartilham carrinho, métodos de entrega ou outros, você deve criar sites separados.

   As contas de clientes do site podem ser compartilhadas entre vários sites em uma única instância do Commerce. Um site contém pelo menos uma loja. Os preços do catálogo devem ser gerenciados no nível do site.

- **Loja**—está contido em um site. Por sua vez, um armazenamento contém pelo menos um *exibição de loja*.

   Várias lojas podem compartilhar carrinho, sessões de usuário, gateways de pagamento e muito mais, mas têm estruturas de catálogo separadas e preço do catálogo.

   Não é possível gerenciar a Quantidade do Catálogo (inventário) no nível da loja. O inventário é gerenciado somente no nível do site ou Global.

   As exibições de loja mudam a maneira como as páginas são apresentadas e são normalmente usadas para exibir uma loja com diferentes layouts ou idiomas. É possível gerenciar moedas diferentes por visualização de loja.

   Cada site e cada exibição de loja deve ter um identificador exclusivo. Esse identificador é necessário para usar o `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` variáveis da seguinte maneira:

- `MAGE_RUN_TYPE` pode ser `store` ou `website`

   - Use `website` para carregar um site em sua loja.
   - Use `store` para carregar qualquer visualização de loja em sua loja.

- `MAGE_RUN_CODE` é o único código de visualização de site ou loja que corresponde a `MAGE_RUN_TYPE`

Este é um resumo das tarefas que você deve executar:

1. [Configure sites, lojas e visualizações de loja no Administrador.](ms-admin.md)
1. Crie um host virtual para carregar vários sites ou um host virtual por site do Commerce ou exibição de loja para permitir diretivas específicas para cada loja.
1. Passe os valores de `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` ao servidor da Web.
