---
title: Tipos de configuração
description: Crie ou estenda os tipos de configuração.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---


# Tipos de configuração

## Estender tipos de configuração

Para estender um tipo de configuração existente, você precisa apenas criar um arquivo de configuração em [módulo](https://glossary.magento.com/module).

Por exemplo, para adicionar um observador de eventos, você cria `app/code/{VendorName}/{ModuleName}/etc/events.xml` e declarar um novo observador.

Como o tipo de configuração de evento existe em Comércio, o carregador e a variável `events.xsd` a validação do schema já está presente e funcional.

Seu novo `events.xml` é automaticamente coletado do módulo e mesclado com outro `events.xml` arquivos para outros módulos.

## Criar tipos de configuração

Para criar um tipo de configuração, você deve adicionar no mínimo:

- Um carregador
- Esquema de validação XSD
- Arquivos de configuração XML

Por exemplo, para introduzir uma [adaptador](https://glossary.magento.com/adapter) para um novo servidor de pesquisa que permite extensões para configurar como suas entidades são indexadas nesse servidor, crie:

- Um carregador
- Um arquivo de esquema XSD
- Um arquivo de configuração com nome adequado. Por exemplo, `search.xml`. Esse arquivo é lido e validado em relação ao esquema.
- Quaisquer outras classes necessárias para o seu trabalho.

>[!INFO]
>
>Se novos módulos tiverem uma `search.xml` , eles são mesclados com o arquivo quando ele é carregado.

### Exemplos de uso

Para criar um tipo de configuração:

1. Crie seu arquivo XSD.
1. Crie seu arquivo XML.
1. Defina o objeto de configuração em `di.xml`.

   O exemplo a seguir do módulo Magento_Sales [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) ilustra a aparência de um objeto de configuração.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - O primeiro nó do tipo define o nome do arquivo do Reader, associado `Converter` e `SchemaLocator` classes.
   - Então, o `pdfConfigDataStorage` o nó tipo virtual anexa a classe do leitor a uma instância de [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - E finalmente, o último nó de tipo anexa esse tipo virtual de dados de configuração ao [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) classe , que é usada para ler os valores de realmente nesses [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) arquivos.

1. Defina um leitor estendendo [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) e reescreva os seguintes parâmetros:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Exemplo:**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>Se preferir criar sua própria versão do leitor, é possível fazer isso implementando `\Magento\Framework\Config\ReaderInterface`. Consulte [Leitor de configuração do Magento_Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Após definir seu leitor, use-o para coletar, mesclar, validar e converter os arquivos de configuração em uma representação interna da matriz.

## Validar um tipo de configuração

Cada arquivo de configuração é validado em relação a um schema específico para seu tipo de configuração. Exemplo: , que, nas versões anteriores do Commerce, foram configuradas em `config.xml`agora estão configurados em `events.xml`.

Os arquivos de configuração podem ser validados antes (opcional) e depois de qualquer mesclagem de vários arquivos que afetem o mesmo tipo de configuração. A menos que as regras de validação dos arquivos individuais e mesclados sejam idênticas, você deve fornecer dois esquemas para validar os arquivos de configuração:

- Esquema para validar um indivíduo
- Esquema para validar um arquivo mesclado

Os novos arquivos de configuração devem ser acompanhados por esquemas de validação XSD. Um arquivo de configuração XML e seu arquivo de validação XSD devem ter o mesmo nome.

Se você precisar usar dois arquivos XSD para um único arquivo XML, os nomes dos esquemas devem ser reconhecíveis e associados ao arquivo XML.
Se você tiver uma `events.xml` e um primeiro `events.xsd` , os arquivos XSD para a mesclagem `events.xml` arquivo pode ser nomeado `events_merged.xsd`.
Para garantir a validação de um arquivo XML por arquivo XSD apropriado, você deve adicionar o Uniform Resource Name (URN) ao arquivo XSD no arquivo XML. Por exemplo:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Seu IDE pode validar seus arquivos de configuração em tempo de execução e durante o desenvolvimento.
