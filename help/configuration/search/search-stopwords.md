---
title: Configurar palavras irrelevantes de pesquisa
description: Saiba como gerenciar palavras de interrupção para o Adobe Commerce usando arquivos CSV.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Configurar palavras irrelevantes de pesquisa

Em geral, _palavras irrelevantes_ são palavras comuns que os mecanismos de pesquisa filtram após o processamento do texto. Originalmente, quando o espaço em disco e a memória eram extremamente limitados, cada quilobyte economizado significava uma melhoria significativa no desempenho. Portanto, os mecanismos de pesquisa obtiveram ganhos de desempenho ao ignorar determinadas palavras e manter o índice pequeno.

Embora tenhamos mais armazenamento hoje, o desempenho ainda é importante. O Elasticsearch e o OpenSearch, como outros mecanismos de pesquisa, ainda usam palavras de interrupção para melhorar o desempenho.

Você deve gerenciar as palavras irrelevantes usando os arquivos CSV localizados na `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ou o `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` diretório, dependendo de como você instalou o software Commerce.

Para obter mais informações sobre como o Elasticsearch e o OpenSearch usam palavras de interrupção, consulte os seguintes recursos:

- [Palavras de interrupção: desempenho versus precisão](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Vantagens e desvantagens das palavras de interrupção](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Usando Palavras de Interrupção](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Palavras de interrupção e desempenho](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurar palavras irrelevantes

As palavras de interrupção estão localizadas no `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` diretório. O Adobe Commerce e o Magento Open Source são enviados com um arquivo CSV contendo palavras irrelevantes para os locais padrão e um arquivo adicional, `stopwords.csv`, que tem palavras de interrupção para qualquer local que não seja representado por outro arquivo CSV.

O tempo de vida padrão para o cache do arquivo stopwords é de 15 minutos.

### Editar palavras de interrupção para um local existente

**Para editar palavras irrelevantes**:

1. Faça logon no servidor do Commerce ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Use um editor de texto para abrir um arquivo de palavras irrelevantes na `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` diretório.

   Os arquivos CSV usam a convenção de nomenclatura `stopwords_<locale_code>.csv`. Por exemplo, o arquivo de palavra irrelevante alemão é denominado `stopwords_de_DE.csv`.

1. Adicionar palavras, remover palavras ou alterar palavras no arquivo.

   (Cada palavra irrelevante em um arquivo é iniciada em uma nova linha.)

1. Salve as alterações e saia do editor de texto.
1. Limpe o cache de configuração.

   - Administrador: **Sistema** > Ferramentas > **Gerenciamento de cache**. Selecione o **Configuração** e, na lista acima, clique em **Atualizar**. Clique em **Enviar** para concluir a ação.

   - Linha de comando: Como proprietário do sistema de arquivos, digite o seguinte comando:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Verifique os resultados procurando termos na loja.

### Criar palavras de interrupção para um novo local

**Para adicionar palavras irrelevantes para um local**:

1. Faça logon no servidor do Commerce ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

1. Use um editor de texto para criar um arquivo de palavras irrelevantes chamado `stopwords_<locale_code>.csv` no `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` diretório.

   Por exemplo, para criar palavras de interrupção para a localidade italiana, nomeie o arquivo `stopwords_it_IT.csv`.

1. No arquivo de palavras de interrupção, verifique se cada uma está em uma linha separada.
1. Salve as alterações e saia do editor de texto.
1. No mesmo diretório, abra `esconfig.xml` em um editor de texto.
1. Adicionar uma linha a `esconfig.xml` do seguinte modo:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Por exemplo, para adicionar um arquivo de palavras irlandesas, adicione a seguinte linha:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Salvar as alterações em `esconfig.xml` e saia do editor de texto.
1. Limpe o cache de configuração.

   - Administrador: **Sistema** > Ferramentas > **Gerenciamento de cache**. Selecione o **Configuração** e, na lista acima, clique em **Atualizar**. Clique em **Enviar** para concluir a ação.

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

   Se você tiver clonado o repositório, ele estará localizado em `app/code/Magento/Elasticsearch/etc/di.xml`

   Se você tiver um arquivo ou metapackage, ele estará localizado em `vendor/magento/module-elasticsearch/etc/di.xml`

1. Altere o valor de `stopwordsDirectory` para o diretório desejado:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Salvar as alterações em `di.xml` e saia do editor de texto.

## Para alterar o diretório de seu módulo

1. [Criar um módulo](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. No seu módulo `etc/di.xml` adicionar instruções:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. No módulo, crie o diretório `etc/stopwords`, com o arquivo CSV correspondente.

1. Salvar as alterações em `di.xml` e saia do editor de texto.
