---
title: Configurar palavras irrelevantes de pesquisa
description: Saiba como gerenciar palavras de interrupção para o Adobe Commerce usando arquivos CSV.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Configurar palavras irrelevantes de pesquisa

Em geral, as _palavras irrelevantes_ são palavras comuns que os mecanismos de pesquisa filtram após processar o texto. Originalmente, quando o espaço em disco e a memória eram extremamente limitados, cada quilobyte economizado significava uma melhoria significativa no desempenho. Portanto, os mecanismos de pesquisa obtiveram ganhos de desempenho ao ignorar determinadas palavras e manter o índice pequeno.

Embora tenhamos mais armazenamento hoje, o desempenho ainda é importante. O Elasticsearch e o OpenSearch, como outros mecanismos de pesquisa, ainda usam palavras de interrupção para melhorar o desempenho.

Você deve gerenciar suas palavras irrelevantes usando arquivos CSV localizados no diretório `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ou no diretório `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`, dependendo de como você instalou o software Commerce.

Para obter mais informações sobre como o Elasticsearch e o OpenSearch usam palavras de interrupção, consulte os seguintes recursos:

- [Palavras de Interrupção: Desempenho Versus Precisão](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Vantagens e desvantagens das palavras de interrupção](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Usando Palavras de Interrupção](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Palavras de Interrupção e Desempenho](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurar palavras irrelevantes

As palavras de interrupção estão localizadas no diretório `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`. A Adobe Commerce vem com um arquivo CSV contendo palavras de interrupção para as localidades padrão e um arquivo adicional, `stopwords.csv`, que tem palavras de interrupção para qualquer localidade que não seja representada por outro arquivo CSV.

O tempo de vida padrão para o cache do arquivo stopwords é de 15 minutos.

### Editar palavras de interrupção para um local existente

**Para editar palavras irrelevantes**:

1. Faça logon no servidor Commerce ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Use um editor de texto para abrir um arquivo de palavras irrelevantes no diretório `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Arquivos CSV usam a convenção de nomenclatura `stopwords_<locale_code>.csv`. Por exemplo, o arquivo de palavras irrelevantes em alemão é nomeado como `stopwords_de_DE.csv`.

1. Adicionar palavras, remover palavras ou alterar palavras no arquivo.

   (Cada palavra irrelevante em um arquivo é iniciada em uma nova linha.)

1. Salve as alterações e saia do editor de texto.
1. Limpe o cache de configuração.

   - Administrador: **Sistema** > Ferramentas > **Gerenciamento de Cache**. Marque a caixa de seleção **Configuração** e, na lista acima, clique em **Atualizar**. Clique em **Enviar** para concluir a ação.

   - Linha de comando: Como proprietário do sistema de arquivos, digite o seguinte comando:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Verifique os resultados procurando termos na loja.

### Criar palavras de interrupção para um novo local

**Para adicionar palavras de interrupção a uma localidade**:

1. Faça logon no servidor Commerce ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

1. Use um editor de texto para criar um arquivo de palavras irrelevantes chamado `stopwords_<locale_code>.csv` no diretório `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Por exemplo, para criar palavras de interrupção para a localidade italiana, nomeie o arquivo `stopwords_it_IT.csv`.

1. No arquivo de palavras de interrupção, verifique se cada uma está em uma linha separada.
1. Salve as alterações e saia do editor de texto.
1. No mesmo diretório, abra `esconfig.xml` em um editor de texto.
1. Adicione uma linha a `esconfig.xml` da seguinte maneira:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Por exemplo, para adicionar um arquivo de palavras irlandesas, adicione a seguinte linha:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Salve as alterações em `esconfig.xml` e saia do editor de texto.
1. Limpe o cache de configuração.

   - Administrador: **Sistema** > Ferramentas > **Gerenciamento de Cache**. Marque a caixa de seleção **Configuração** e, na lista acima, clique em **Atualizar**. Clique em **Enviar** para concluir a ação.

   - Linha de comando: Como proprietário do sistema de arquivos, digite o seguinte comando:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Verifique os resultados procurando termos na loja.

## Alterar o diretório de palavras irrelevantes

Esta seção discute como alterar opcionalmente o diretório de palavras irrelevantes default de uma das seguintes opções:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

O local depende de como você instalou o software Commerce. Se você clonou o repositório GitHub Magento 2, o caminho está em `app/code`. Se você instalou um arquivo compactado ou um metapackage, o caminho está em `vendor`.

**Para alterar o diretório**:

1. Como proprietário do sistema de arquivos, abra o Elasticsearch `di.xml` em um editor de texto.

   Se você clonou o repositório, ele está localizado em `app/code/Magento/Elasticsearch/etc/di.xml`

   Se você tiver um arquivo morto ou o metapackage, ele estará localizado em `vendor/magento/module-elasticsearch/etc/di.xml`

1. Altere o valor de `stopwordsDirectory` para o diretório desejado:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Salve as alterações em `di.xml` e saia do editor de texto.

## Para alterar o diretório de seu módulo

1. [Criar um módulo](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. No módulo `etc/di.xml`, adicione instruções:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Em seu módulo, crie o diretório `etc/stopwords`, com o arquivo CSV correspondente.

1. Salve as alterações em `di.xml` e saia do editor de texto.
