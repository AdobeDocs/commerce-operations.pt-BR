---
title: Dicionários de tradução e pacotes de idiomas
description: Saiba como gerar dicionários de tradução e criar pacotes de idioma.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# Localização

{{file-system-owner}}

As traduções do Commerce permitem personalizar e localizar sua loja para várias regiões e mercados gerando:

- **Dicionários de tradução**, que são uma maneira conveniente de personalizar ou traduzir _algumas_ palavras e frases, como aquelas de um módulo ou tema personalizado.
- **Pacotes de idiomas** que permitem que você traduza _qualquer uma ou todas_ palavras e frases no aplicativo Commerce.

Consulte [Visão geral das traduções].

## Gerar um dicionário de tradução

Você pode gerar um [dicionário de tradução] para personalizar cadeias de caracteres existentes, traduzir palavras e frases em um módulo personalizado, localizar um tema ou criar pacotes de idioma.

Para começar a traduzir, use um comando para gerar um arquivo CSV de dicionário com uma lista coletada de todas as frases e palavras existentes.

Para gerar o dicionário e iniciar a tradução:

1. Extrair palavras e frases traduzíveis de componentes ativados usando o comando coleção de tradução. O conteúdo é extraído em um arquivo CSV.
1. Traduza as palavras e frases existentes. Você pode adicionar termos personalizados adicionais, conforme necessário.

   Você tem opções para usar o dicionário traduzido:

1. Você pode criar um pacote dos dicionários de tradução em um pacote de idiomas e fornecer o pacote ao administrador da loja da Commerce.

1. No Admin, o administrador de armazenamento [configura as traduções].

Opções de comando:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

A tabela a seguir explica os parâmetros e valores:

| Parâmetro | Valor | Obrigatório? |
|--- |--- |--- |
| `<path to directory to translate>` | Caminho para um diretório que tem código traduzível; em outras palavras, arquivos PHP, PHTML ou XML que têm frases a serem traduzidas.<br><br>A ferramenta inicia a pesquisa no caminho inserido e pesquisa todos os arquivos e subdiretórios que ela contém.<br><br>Não use este parâmetro se você usar `-m --magento`. | Sim (dicionários), não (pacotes). |
| `-m --magento` | Obrigatório para criar um pacote de idioma a partir deste dicionário de tradução. Se usado, pesquisa os diretórios que contêm bin/magento. Essa opção adiciona temas ou módulos a cada linha do dicionário.<br><br>Este é um exemplo:<br><br>&quot;Nenhum item encontrado&quot;,&quot;Nenhum item encontrado&quot;,module,Magento_Wishlist | Não |
| `-o --output="<path>"` | Especifica o caminho absoluto do sistema de arquivos e o nome do arquivo CSV do dicionário de tradução a ser criado. O valor inserido diferencia maiúsculas de minúsculas. O nome do arquivo CSV deve corresponder exatamente ao nome da localidade, incluindo a caixa dos caracteres.<br><br>Se você omitir este parâmetro, a saída será direcionada para stdout. | Não |

>[!INFO]
>
>Para criar um pacote de idiomas de um dicionário de tradução, você _deve_ usar a opção `-m|--magento`.

### Diretrizes de tradução

Use as diretrizes a seguir ao traduzir palavras e frases:

- Altere o conteúdo somente da segunda coluna. Traduza as frases do inglês (`US`) para o idioma desejado.
- Ao criar dicionários para códigos de idiomas, use as strings padrão do Commerce.
- Durante a tradução, preste atenção aos espaços reservados: `%1`, `%2`

O Commerce usa os espaços reservados para inserir valores de contexto; eles são _não_ usados para traduções. Por exemplo:

```text
Product '%1' has been added to shopping cart.
```

Preenche com um valor:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

A frase resultante deve conter pelo menos um de cada espaço reservado. Por exemplo, suponha que haja espaços reservados de `%1` a `%3` na frase original. A tradução pode ter tantos espaços reservados em qualquer ordem, mas deve haver pelo menos uma ocorrência de `%1`, `%2` e `%3`. A conversão não pode conter valores de espaços reservados que não estejam presentes no valor original (por exemplo, `%4`, `%5` e assim por diante).

Um exemplo de tradução de uma frase:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Criar um pacote de idiomas

Ao contrário de um dicionário de tradução, é possível traduzir qualquer uma ou todas as palavras e frases no aplicativo do Commerce usando um pacote de idiomas. Você pode traduzir um componente específico, como um módulo ou um tema, usando um dicionário de tradução. [Saiba mais sobre pacotes de idiomas].

Esta seção discute como criar um pacote de linguagem, que grava arquivos CSV em módulos e temas. Para criar um pacote de idioma, você deve executar as tarefas discutidas nas seguintes seções:

1. [Coletar e traduzir palavras e frases](#generate-a-translation-dictionary). (O parâmetro `--magento` é obrigatório.)
1. [Execute o comando de pacote de idioma](#run-the-language-package-command).
1. [Criar diretórios e arquivos](#create-directories-and-files).
1. (Opcional.) [Configurar vários pacotes para um idioma](#configure-multiple-packages-for-a-language).

### Execute o comando de pacote de idioma

Uso do comando:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

A tabela a seguir explica os parâmetros e valores do comando de pacote de idioma:

| Parâmetro | Valor | Obrigatório? |
|--- |--- |--- |
| `<source>` | Caminho absoluto do sistema de arquivos e nome de um arquivo CSV que contém o dicionário de tradução combinado e as metainformações necessárias para o detalhamento em um pacote de idioma.<br><br>Use [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) para criar o arquivo CSV e, em seguida, crie o pacote de idioma conforme discutido em [Criar diretórios e arquivos](#m2devgde-xlate-files). | Sim |
| `<locale>` | [ISO 639-1] (idioma) e [ISO 3166] (país) identificador do idioma usado como nome de arquivo para todos os arquivos CSV resultantes. Exemplos: `de_DE`, `pt_PT`, `pt_BR`. | Sim |
| `-m --mode` | Se existir um arquivo de destino, especifica se o pacote de idioma existente deve ser substituído ou mesclado com o novo pacote de idioma. A mesclagem substitui todas as frases existentes e adiciona novas.<br><br>Valores: mesclar ou substituir (padrão). | Não |
| `-d --allow-duplicates` | Inclua esta opção para permitir duplicatas no pacote de idioma. Caso contrário, o comando falhará com um erro se encontrar a mesma frase em várias entradas com traduções diferentes. | Não |

### Criar diretórios e arquivos

Os pacotes de idiomas estão localizados em um diretório em `app/i18n/<VendorName>` no sistema de arquivos do Commerce com o seguinte conteúdo:

- Arquivos de licença necessários
- `composer.json`
- `registration.php` que [registra] o pacote de idiomas
- [`language.xml`](#language-package-languagexml) arquivo de metainformações

>[!INFO]
>
>Você deve colocar todo o caminho em minúsculas. Por exemplo, consulte [`de_de`].

Para criar esses arquivos:

1. Crie um diretório em `app/i18n`.

   Por exemplo, os pacotes de idiomas do Commerce estão localizados em `app/i18n/magento`

1. Adicione os arquivos de licença necessários.
1. Adicione [`composer.json`] que especifica dependências para o pacote de idioma.
1. Registrar o pacote de idioma com [`registration.php`]
1. Adicione o arquivo de metainformações `language.xml` conforme discutido na próxima seção.

#### Pacote de idioma language.xml

Ao declarar um pacote de idioma no arquivo de configuração `language.xml`, você deve especificar a sequência da herança de idioma para esse pacote.

A herança de idioma permite criar uma tradução chamada _filho_ com base em uma tradução existente chamada _pai_. As traduções secundárias substituem as principais. No entanto, se a tradução secundária não fizer upload ou exibir uma frase ou palavra, o Commerce usará o local principal. [Exemplos de herança de pacote de idioma](#example-of-language-inheritance).

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

Onde:

- `code` — Local do pacote de idioma (obrigatório)
- `vendor` — Nome de fornecedor do módulo (obrigatório)
- `package` — Nome do pacote de idioma (obrigatório)
- `sort_order` — Prioridade de carregamento de um pacote quando há vários pacotes de idiomas disponíveis para uma loja
- `use` — Local do pacote de idioma pai do qual herdar dicionários

Se necessário, é possível especificar vários pacotes principais. Os pacotes principais são aplicados em uma base listada pela primeira vez e usada.

#### Exemplo de herança de linguagem

Suponha que um pacote de idioma herde de dois outros pacotes e que esses pacotes também tenham pacotes pai e &quot;avô&quot;.

Se um pacote de linguagem herda de dois pacotes, seu `language.xml` pode ser semelhante ao seguinte:

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

Se o aplicativo Commerce não puder encontrar a palavra ou frase no pacote `en_GB`, ele procurará em outros pacotes na seguinte sequência:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Especificar todas as heranças entre os pacotes de idioma pode resultar na criação de cadeias de herança circulares. Use o teste [Magento\Test\Integrity\App\Language\CircularDependencyTest] para localizar e corrigir essas cadeias.

### Configurar vários pacotes para um idioma

Para tornar sua loja mais flexível, você pode carregar vários pacotes de idiomas para o mesmo idioma na loja. Assim, você pode usar diferentes pacotes personalizados para diferentes partes da loja, pois o sistema compila um único pacote de todos os pacotes que estão disponíveis para uma linguagem.

Para ativar um pacote adicional para um idioma existente, nomeie o novo pacote com qualquer nome, exceto para um nome de código de idioma existente (para evitar confusão). Especifique as configurações de um pacote no arquivo de metainformações `language.xml` do pacote de idioma, conforme discutido na próxima seção.

## Exemplos de uso de comandos de tradução

As seções a seguir fornecem exemplos completos do uso dos comandos discutidos neste tópico para criar dicionários de tradução e pacotes de tradução:

### Exemplo: criar um dicionário de tradução para um módulo ou tema

Para adicionar uma tradução em alemão a um módulo ou tema que deseja distribuir para outros comerciantes:

1. Colete frases do módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >O nome do arquivo CSV deve _corresponder exatamente_ à localidade, incluindo a caixa dos caracteres.

1. Traduza as palavras e frases usando [estas diretrizes](#translation-guidelines).
1. Se necessário, copie `xx_YY.csv` em `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` ou no diretório de temas do módulo (dependendo se o dicionário de tradução é para um módulo ou tema).

### Exemplo: criar um pacote de idioma

Semelhante ao exemplo anterior, gere um arquivo CSV, mas em vez de especificar um módulo ou diretório de tema, especifique todo o diretório raiz do aplicativo Commerce. O CSV resultante contém qualquer frase que o comando possa encontrar no código.

1. Colete frases do módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >O nome do arquivo CSV deve _corresponder exatamente_ à localidade, incluindo a caixa dos caracteres.

1. Traduza as palavras e frases usando [estas diretrizes](#translation-guidelines).
1. Crie o pacote de idioma.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Crie um diretório para o pacote de idioma.

   Por exemplo, `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Nesse diretório, adicione todos os itens a seguir:

   - Uma licença, se necessário
   - `composer.json` (exemplo a seguir)
   - `registration.php` (exemplo a seguir)
   - `language.xml` (exemplo a seguir)

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
[configura as traduções]: https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-localize
[Saiba mais sobre pacotes de idiomas]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registros]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&quot;composer.json&quot;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&quot;registration.php&quot;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
