---
title: Dicionários de tradução e pacotes linguísticos
description: Saiba como gerar dicionários de tradução e criar pacotes de idioma.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# Localização

{{file-system-owner}}

As traduções de comércio permitem personalizar e localizar sua loja para várias regiões e mercados, gerando:

- **Dicionários de tradução**, que são uma maneira conveniente de personalizar ou traduzir _some_ palavras e frases, como para um módulo ou tema personalizado.
- **Pacotes de idioma** que permitem traduzir _qualquer ou todos_ palavras e frases no aplicativo Commerce.

Consulte [Visão geral das traduções].

## Gerar um dicionário de tradução

Você pode gerar um [dicionário de tradução] para personalizar strings existentes, traduzir palavras e frases em um módulo personalizado, localizar um tema ou criar [pacotes de idioma](https://glossary.magento.com/language-package).

Para começar a traduzir, use um comando para gerar um arquivo CSV de dicionário com uma lista coletada de todas as frases e palavras existentes.

Para gerar o dicionário e iniciar a tradução:

1. Extraia palavras e frases traduzíveis de componentes ativados usando o comando coleção de tradução. O conteúdo é extraído em um arquivo CSV.
1. Traduza as palavras e frases existentes. Você pode adicionar termos personalizados adicionais, conforme necessário.

   Você tem opções para usar o dicionário traduzido:

1. Você pode disponibilizar os dicionários de tradução em um pacote de idioma e fornecer o pacote ao administrador da loja de Comércio.

1. No Administrador, o administrador da loja [configura as traduções].

Opções de comando:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

A tabela a seguir explica os parâmetros e valores:

| Parâmetro | Valor | Obrigatório? |
|--- |--- |--- |
| `<path to directory to translate>` | Caminho para um diretório que tenha código traduzível; em outras palavras, arquivos PHP, PHTML ou XML que têm frases para traduzir.<br><br>A ferramenta inicia a pesquisa no caminho inserido e pesquisa todos os arquivos e subdiretórios que ela contém.<br><br>Não use esse parâmetro se usar `-m --magento`. | Sim (dicionários), não (pacotes). |
| `-m --magento` | Necessário para criar um pacote de idioma a partir deste dicionário de tradução. Se usado, o pesquisa os diretórios que contêm bin/magento. Essa opção adiciona temas ou módulos a cada linha do dicionário.<br><br>Uma amostra:<br><br>&quot;Nenhum item encontrado&quot;,&quot;Nenhum item encontrado&quot;, módulo, Magento_Wishlist | Não |
| `-o --output="<path>"` | Especifica o caminho absoluto do sistema de arquivos e o nome do arquivo do arquivo CSV do dicionário de tradução a ser criado. O valor inserido diferencia maiúsculas e minúsculas. O nome do arquivo CSV deve corresponder exatamente ao nome da localidade, incluindo o caso dos caracteres.<br><br>Se você omitir esse parâmetro, a saída será direcionada para stdout. | Não |

>[!INFO]
>
>Para criar um pacote de idiomas a partir de um dicionário de tradução, você _must_ use o `-m|--magento` opção.

### Diretrizes de tradução

Use as seguintes diretrizes ao traduzir palavras e frases:

- Altere somente o conteúdo da segunda coluna. Traduza as frases em inglês (`US`) para o idioma desejado.
- Ao criar dicionários para localidades, use as strings padrão do Commerce.
- Ao traduzir, preste atenção aos espaços reservados: `%1`, `%2`

O Commerce usa os espaços reservados para inserir valores de contexto; são _not_ usado para traduções. Por exemplo:

```text
Product '%1' has been added to shopping cart.
```

Preenche com um valor:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

A frase resultante deve conter pelo menos um de cada espaço reservado. Por exemplo, suponha que haja espaços reservados de `%1` para `%3` na frase original. A tradução pode ter quantos desses espaços reservados, em qualquer ordem, mas deve haver pelo menos uma ocorrência de `%1`, `%2`e `%3`. A tradução não pode conter valores de espaço reservado não presentes no valor original (por exemplo, `%4`, `%5`e assim por diante).

Um exemplo de tradução de uma frase:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Criar um pacote de idioma

Ao contrário de um dicionário de tradução, você pode traduzir qualquer ou todas as palavras e frases no aplicativo Commerce usando um pacote de idiomas. Você pode traduzir um componente específico, como um módulo ou um tema, usando um dicionário de tradução. [Saiba mais sobre pacotes de idioma].

Esta seção discute como criar um pacote de idiomas, que grava arquivos CSV em módulos e temas. Para criar um pacote de idiomas, você deve executar as tarefas discutidas nas seguintes seções:

1. [Coletar e traduzir palavras e frases](#generate-a-translation-dictionary). (O `--magento` é obrigatório.)
1. [Execute o comando do pacote de idiomas](#run-the-language-package-command).
1. [Criar diretórios e arquivos](#create-directories-and-files).
1. (Opcional.) [Configurar vários pacotes para um idioma](#configure-multiple-packages-for-a-language).

### Execute o comando do pacote de idiomas

Uso do comando:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

A tabela a seguir explica os parâmetros e valores do comando language package:

| Parâmetro | Valor | Obrigatório? |
|--- |--- |--- |
| `<source>` | Caminho absoluto do sistema de arquivos e nome do arquivo de um arquivo CSV que contém o dicionário de tradução combinado e as meta-informações necessárias para o detalhamento em um pacote de idioma.<br><br>Use [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) para criar o arquivo CSV, crie o pacote de idiomas conforme discutido em [Criar diretórios e arquivos](#m2devgde-xlate-files). | Sim |
| `<locale>` | [ISO 639-1] (idioma) e [ISO 3166] Identificador (país) do idioma usado como nome de arquivo para todos os arquivos CSV resultantes. Exemplos: `de_DE`, `pt_PT`, `pt_BR`. | Sim |
| `-m --mode` | Se um arquivo de destino existir, especifica se o pacote de idioma existente deve ser substituído ou unido ao novo pacote de idiomas. A mesclagem substitui todas as frases existentes e adiciona novas.<br><br>Valores: mesclar ou substituir (padrão). | Não |
| `-d --allow-duplicates` | Inclua esta opção para permitir duplicatas no pacote de idiomas. Caso contrário, o comando falhará com um erro se encontrar a mesma frase em várias entradas com traduções diferentes. | Não |

### Criar diretórios e arquivos

Os pacotes de idioma estão localizados em um diretório em `app/i18n/<VendorName>` no sistema de arquivos Commerce com o seguinte conteúdo:

- Arquivos de licença necessários
- `composer.json`
- `registration.php` that [registros] o pacote linguístico
- [`language.xml`](#language-package-languagexml) arquivo de informações meta

>[!INFO]
>
>Você deve minúsculas em todo o caminho. Por exemplo, consulte [`de_de`].

Para criar esses arquivos:

1. Crie um diretório em `app/i18n`.

   Por exemplo, os pacotes de idioma comercial estão localizados em `app/i18n/magento`

1. Adicione os arquivos de licença necessários.
1. Adicionar [`composer.json`] que especifica as dependências do seu pacote de idiomas.
1. Registre o pacote de idiomas com [`registration.php`]
1. Adicionar `language.xml` arquivo de informações meta conforme discutido na próxima seção.

#### Language package language.xml

Ao declarar um pacote de idioma no `language.xml` , você deve especificar a sequência da herança do idioma para este pacote.

A herança de idioma permite criar uma tradução chamada de _criança_ com base em uma tradução existente chamada de _parent_. As traduções secundárias substituem o pai. No entanto, se a tradução secundária não conseguir carregar ou exibir ou estiver sem uma frase ou palavra, o Commerce usará o pai [locale](https://glossary.magento.com/locale). [Exemplos de herança do pacote de idioma](#example-of-language-inheritance).

Para declarar um pacote, especifique as seguintes informações:

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

Em que:

- `code`—Local do pacote de idiomas (obrigatório)
- `vendor`—Nome do fornecedor do módulo (obrigatório)
- `package`—Nome do pacote de idioma (obrigatório)
- `sort_order`—Prioridade de carregar um pacote quando houver vários pacotes de idioma disponíveis para uma loja
- `use`—Local do pacote de idioma pai do qual herdar dicionários

Se necessário, é possível especificar vários pacotes principais. Os pacotes principais são aplicados em uma base listada e usada pela primeira vez.

#### Exemplo de herança de idioma

Suponha que um pacote de idioma herde de dois outros pacotes e que esses pacotes também tenham pacotes pai e &quot;avô&quot;.

Se um pacote de idioma herdar de dois pacotes, seu `language.xml` pode ser semelhante ao seguinte:

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

No exemplo anterior:

- `language_package_one` herda de `en_au_package` e `en_au_package` herda de `en_ie_package`
- `language_package_two` herda de `en_ca_package` e `en_ca_package` herda de `en_us_package`

Se o aplicativo Commerce não conseguir encontrar uma palavra ou frase na `en_GB` pacote, ele aparece em outros pacotes na seguinte sequência:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Especificar todas as heranças entre os pacotes de idioma pode resultar na criação de cadeias de herança circular. Use [Magento\Test\Integrity\App\Language\CircularDependencyTest] teste para localizar e corrigir essas cadeias.

### Configurar vários pacotes para um idioma

Para ajudá-lo a tornar sua loja mais flexível, você pode fazer upload de vários pacotes de idioma para o mesmo idioma em sua loja. Assim, você pode usar pacotes personalizados diferentes para partes diferentes da sua loja porque o sistema compila um único pacote de todos os pacotes que estão disponíveis para um idioma.

Para habilitar um pacote adicional para um idioma existente, nomeie o novo pacote com qualquer nome, exceto para um nome de código de idioma existente (para evitar confusão). Especifique as configurações de um pacote no pacote de idioma `language.xml` arquivo de informações meta conforme discutido na próxima seção.

## Exemplos de uso de comandos de tradução

As seções a seguir fornecem exemplos completos do uso dos comandos discutidos neste tópico para criar dicionários de tradução e pacotes de tradução:

### Exemplo: Criar um dicionário de tradução para um módulo ou tema

Para adicionar uma tradução em alemão a um módulo ou tema que você deseja distribuir para outros comerciantes:

1. Colete frases do seu módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >O nome do arquivo CSV deve _correspondência exata_ a localidade, incluindo o caso dos caracteres.

1. Traduza as palavras e frases usando [estas orientações](#translation-guidelines).
1. Se necessário, copiar `xx_YY.csv` para `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` ou para o diretório de tema do módulo (dependendo se o dicionário de tradução é para um módulo ou um tema).

### Exemplo: Criar um pacote de idioma

Semelhante ao exemplo anterior, gere um arquivo CSV, mas em vez de especificar um módulo ou diretório de tema, especifique todo o diretório raiz do aplicativo Commerce. O CSV resultante contém qualquer frase que o comando poderia encontrar no código.

1. Colete frases do seu módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >O nome do arquivo CSV deve _correspondência exata_ a localidade, incluindo o caso dos caracteres.

1. Traduza as palavras e frases usando [estas orientações](#translation-guidelines).
1. Crie o pacote de idioma.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Crie um diretório para o pacote de idioma.

   Por exemplo, `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Nesse diretório, adicione todas as opções a seguir:

   - Uma licença, se necessário
   - `composer.json` (exemplo seguinte)
   - `registration.php` (exemplo seguinte)
   - `language.xml` (exemplo seguinte)

   **Amostra`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **Amostra`registration.php`**:

   ```php
   <?php
   /**
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Amostra`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Visão geral das traduções]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[dicionário de tradução]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[configura as traduções]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[Saiba mais sobre pacotes de idioma]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registros]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&quot;composer.json&quot;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&quot;registration.php&quot;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
