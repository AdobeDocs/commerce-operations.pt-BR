---
title: Vários sites ou lojas
description: Saiba como iniciar vários sites ou implementar exibições de loja com opções, domínios e conteúdo diferentes.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Vários sites ou lojas

Uma única instância do software Adobe Commerce permite que você inicie vários sites ou armazene exibições que usam atributos e conteúdo diferentes, como:

- Idiomas padrão
- Nomes de domínio
- Categorias
- Produtos
- Moedas

Essa solução flexível permite que uma base de código do Commerce e um Administrador administrem e exibam diferentes lojas. Você configura os sites, lojas e visualizações de loja no Administrador. Use determinadas variáveis em hosts virtuais para iniciar o aplicativo do Commerce usando esses sites ou exibições de loja.

Um uso típico é configurar lojas com diferentes opções em domínios diferentes. Por exemplo, você pode ter um conjunto de categorias e produtos em um domínio e outro conjunto de categorias e produtos em um domínio separado em um idioma diferente.

Você configura os sites, lojas e visualizações de loja no Administrador do Commerce. Use as variáveis `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` em hosts virtuais para iniciar o aplicativo do Commerce usando esses sites ou exibições de armazenamento.

Considere os seguintes termos:

- **Site**—é o contêiner de nível superior para sites, métodos de entrega, métodos de pagamento e muito mais. Para criar sites completamente separados que não compartilhem carrinho, métodos de entrega ou outros, você deve criar sites separados.

  As contas de cliente do site podem ser compartilhadas entre vários sites em uma única instância do Commerce. Um site contém pelo menos uma loja. Os preços dos catálogos devem ser geridos ao nível do sítio Web.

- **Armazenamento**—está contido em um site. Uma loja contém pelo menos uma *exibição de loja*.

  Várias lojas podem compartilhar carrinho, sessões de usuários, gateways de pagamento e muito mais, mas têm estruturas de catálogo separadas e preço de catálogo.

  A Quantidade do Catálogo (inventário) não pode ser gerenciada no nível da loja. O inventário é gerenciado somente no nível do Site ou Global.

  As visualizações da loja mudam a forma como as páginas são apresentadas e são normalmente usadas para exibir uma loja com layouts ou idiomas diferentes. É possível gerenciar moedas diferentes por exibição de loja.

  Cada site e exibição de loja deve ter um identificador exclusivo. Esse identificador é necessário para usar as variáveis `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` da seguinte maneira:

- `MAGE_RUN_TYPE` pode ser `store` ou `website`

   - Use o `website` para carregar um site em sua vitrine eletrônica.
   - Use `store` para carregar qualquer exibição de loja em sua vitrine eletrônica.

- `MAGE_RUN_CODE` é o código exclusivo de exibição de site ou loja que corresponde a `MAGE_RUN_TYPE`

Este é um resumo das tarefas que você deve executar:

1. [Configurar sites, lojas e visualizações de loja no Administrador.](ms-admin.md)
1. Crie um host virtual para carregar vários sites ou um host virtual por site ou exibição de armazenamento do Commerce para permitir diretivas específicas para cada armazenamento.
1. Passe os valores de `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` para o servidor Web.
