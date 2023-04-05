---
title: Configurar paradas de pesquisa
description: Saiba como gerenciar palavras de interrupção para Adobe Commerce usando arquivos CSV.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# Configurar paradas de pesquisa

Em geral, _parada_ são palavras comuns que mecanismos de pesquisa filtram após o processamento de texto. Originalmente, quando o espaço em disco e a memória eram extremamente limitados, cada kilobyte salvo significava uma melhoria significativa no desempenho. Portanto, os mecanismos de pesquisa obtiveram ganhos de desempenho ignorando certas palavras e mantendo o índice pequeno.

Embora tenhamos mais armazenamento hoje, o desempenho ainda é importante. O Elasticsearch e o OpenSearch, como outros mecanismos de pesquisa, ainda usam palavras de interrupção para melhorar o desempenho.

Você deve gerenciar suas palavras de parada usando arquivos CSV localizados na `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ou o `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` , dependendo de como você instalou o software Commerce.

Para obter mais informações sobre como o Elasticsearch e o OpenSearch usam palavras de interrupção, consulte os seguintes recursos:

- [Palavras-limite: Desempenho versus precisão](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Vantagens e desvantagens das Palavras de interrupção](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Uso de Palavras-limite](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Palavras-limite e desempenho](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurar paradas

As palavras-chave estão localizadas na variável `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` diretório. O Adobe Commerce e o Magento Open Source são fornecidos com um arquivo CSV contendo senhas para as localidades padrão e um arquivo adicional, `stopwords.csv`, que tem palavras de interrupção para qualquer local que não seja representado por outro arquivo CSV.

O tempo de vida padrão do cache de arquivos de palavras de interrupção é de 15 minutos.

### Editar palavras de interrupção para uma localidade existente

**Para editar palavras-chave**:

1. Faça logon no seu servidor do Commerce ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Use um editor de texto para abrir um arquivo de palavra-chave no `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` diretório.

   Os arquivos CSV usam a convenção de nomenclatura `stopwords_<locale_code>.csv`. Por exemplo, o arquivo de palavra-chave alemão é nomeado `stopwords_de_DE.csv`.

1. Adicione palavras, remova palavras ou altere palavras no arquivo.

   (Cada palavra-chave em um arquivo começa em uma nova linha.)

1. Salve as alterações e saia do editor de texto.
1. Limpe o cache de configuração.

   - Administrador: **Sistema** > Ferramentas > **Gerenciamento de cache**. Selecione o **Configuração** e, na lista acima, clique em **Atualizar**. Clique em **Enviar** para concluir a ação.

   - Linha de comando: Como proprietário do sistema de arquivos, insira o seguinte comando:

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. Verifique os resultados pesquisando termos em sua loja.

### Criar palavras de interrupção para uma nova localidade

**Para adicionar palavras de interrupção a uma localidade**:

1. Faça logon no seu servidor do Commerce ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

1. Usar um editor de texto para criar um arquivo de palavra-chave chamado `stopwords_<locale_code>.csv` no `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` diretório.

   Por exemplo, para criar palavras de interrupção para a localidade italiana, nomeie o arquivo `stopwords_it_IT.csv`.

1. No arquivo de senha, verifique se cada palavra-chave está em uma linha separada.
1. Salve as alterações e saia do editor de texto.
1. No mesmo diretório, abra `esconfig.xml` em um editor de texto.
1. Adicionar uma linha a `esconfig.xml` como se segue:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Por exemplo, para adicionar um arquivo de senha italiano, adicione a seguinte linha:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Salve as alterações em `esconfig.xml` e saia do editor de texto.
1. Limpe o cache de configuração.

   - Administrador: **Sistema** > Ferramentas > **Gerenciamento de cache**. Selecione o **Configuração** e, na lista acima, clique em **Atualizar**. Clique em **Enviar** para concluir a ação.

   - Linha de comando: Como proprietário do sistema de arquivos, insira o seguinte comando:

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. Verifique os resultados pesquisando termos em sua loja.

## Alterar o diretório de palavras irregulares

Esta seção discute como, opcionalmente, alterar o diretório de palavras irrelevantes padrão a partir de um dos seguintes itens:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

A localização depende de como você instalou o software Commerce. Se você clonou o repositório GitHub Magento 2, o caminho está em `app/code`. Se você instalou um arquivo compactado ou um metapackage, o caminho está em `vendor`.

**Para alterar o diretório**:

1. Como proprietário do sistema de arquivos, abra o Elasticsearch `di.xml` em um editor de texto.

   Se você clonou o repositório, ele está localizado em `app/code/Magento/Elasticsearch/etc/di.xml`

   Se você tiver um arquivo ou metapackage, ele estará localizado em `vendor/magento/module-elasticsearch/etc/di.xml`

1. Altere o valor de `stopwordsDirectory` para o diretório desejado:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Salve as alterações em `di.xml` e saia do editor de texto.

## Para alterar o diretório do seu módulo

1. [Criar um módulo](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. No módulo `etc/di.xml` adicione instruções:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. No módulo , crie o diretório `etc/stopwords`, com o arquivo CSV correspondente.

1. Salve as alterações em `di.xml` e saia do editor de texto.
