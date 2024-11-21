---
title: Tipos de configuração
description: Criar ou estender tipos de configuração.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 02c69e890b40643781ab8f48c3133527dd79386a
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Tipos de configuração

## Estender tipos de configuração

Para estender um tipo de configuração existente, você só precisa criar um arquivo de configuração no módulo.

Por exemplo, para adicionar um observador de eventos, você cria `app/code/{VendorName}/{ModuleName}/etc/events.xml` e declara um novo observador.

Como o tipo de configuração do evento existe no Commerce, o carregador e o esquema de validação `events.xsd` já estão presentes e funcionais.

Seu novo `events.xml` é automaticamente coletado de seu módulo e mesclado com outros arquivos `events.xml` para outros módulos.

## Criar tipos de configuração

Para criar um tipo de configuração, você deve adicionar no mínimo:

- Um carregador
- Esquema de validação XSD
- Arquivos de configuração XML

Por exemplo, para introduzir um adaptador para um novo servidor de pesquisa que permita que as extensões configurem como suas entidades são indexadas nesse servidor, crie:

- Um carregador
- Um arquivo de esquema XSD
- Um arquivo de configuração nomeado adequadamente. Por exemplo, `search.xml`. Esse arquivo é lido e validado em relação ao esquema.
- Quaisquer outras classes necessárias para o seu trabalho.

>[!INFO]
>
>Se novos módulos tiverem um arquivo `search.xml`, eles serão mesclados com seu arquivo quando ele for carregado.

### Exemplos de uso

Para criar um tipo de configuração:

1. Crie seu arquivo XSD.
1. Crie seu arquivo XML.
1. Defina o objeto de configuração em `di.xml`.

   O exemplo a seguir do [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) do módulo Magento_Sales ilustra como um objeto de configuração deve ser.

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

   - O primeiro nó de tipo define o nome de arquivo Reader, associado às classes `Converter` e `SchemaLocator`.
   - Em seguida, o nó do tipo virtual `pdfConfigDataStorage` anexa a classe de leitor a uma instância de [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - E finalmente, o último nó de tipo anexa esse tipo de dados virtual de configuração à classe [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php), que é usada para, na verdade, ler valores nesses arquivos [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml).

1. Defina um leitor estendendo a classe [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) e regrave os seguintes parâmetros:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Exemplo:**

```php
<?php
/**
 * Copyright Adobe
 * All Rights Reserved.
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
>Se preferir criar sua própria versão do leitor, você pode fazer isso implementando o `\Magento\Framework\Config\ReaderInterface`. Consulte o [leitor de configuração de Magento_Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Após definir seu leitor, use-o para coletar, mesclar, validar e converter os arquivos de configuração em uma representação interna de matriz.

## Validar um tipo de configuração

Cada arquivo de configuração é validado em relação a um esquema específico para seu tipo de configuração. Exemplo: eventos que, em versões anteriores do Commerce, foram configurados em `config.xml`, agora estão configurados em `events.xml`.

Os arquivos de configuração podem ser validados antes (opcional) e depois de qualquer mesclagem de vários arquivos que afetem o mesmo tipo de configuração. A menos que as regras de validação dos arquivos individuais e mesclados sejam idênticas, você deve fornecer dois esquemas para validar os arquivos de configuração:

- Esquema para validar um indivíduo
- Esquema para validar um arquivo mesclado

Os novos arquivos de configuração devem ser acompanhados por esquemas de validação XSD. Um arquivo de configuração XML e seu arquivo de validação XSD devem ter o mesmo nome.

Se você precisar usar dois arquivos XSD para um único arquivo XML, os nomes dos esquemas deverão ser reconhecíveis e associados ao arquivo XML.
Se você tiver um arquivo `events.xml` e um primeiro arquivo `events.xsd`, os arquivos XSD do arquivo `events.xml` mesclado podem ser nomeados como `events_merged.xsd`.
Para garantir a validação de um arquivo XML pelo arquivo XSD apropriado, você deve adicionar o Uniform Resource Name (URN) ao arquivo XSD no arquivo XML. Por exemplo:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

O IDE pode validar os arquivos de configuração tanto no tempo de execução quanto durante o desenvolvimento.
