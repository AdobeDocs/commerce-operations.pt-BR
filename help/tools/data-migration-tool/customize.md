---
title: Personalizar o  [!DNL Data Migration Tool]
description: Saiba como personalizar o  [!DNL Data Migration Tool]  para transferir dados criados por extensões entre o Magento 1 e o Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Configurar o [!DNL Data Migration Tool]

Às vezes, o formato e a estrutura dos dados criados por [extensões](https://marketplace.magento.com/extensions.html) ou código personalizado são diferentes entre Magento 1 e Magento 2. Use pontos de extensão no [!DNL Data Migration Tool] para migrar esses dados. Se o formato e a estrutura dos dados forem iguais, a ferramenta poderá migrar os dados automaticamente sem a intervenção do usuário.

Durante a migração, a [Etapa do mapa](technical-specification.md#map-step) verifica e compara todas as tabelas de Magento 1 e Magento 2, incluindo aquelas criadas por extensões. Se as tabelas forem iguais, a ferramenta migrará os dados automaticamente. Se as tabelas forem diferentes, a ferramenta será finalizada e notificará o usuário.

>[!NOTE]
>
>Leia a [Especificação Técnica](technical-specification.md) antes de tentar estender o [!DNL Data Migration Tool]. Além disso, consulte o [Guia de Migração](../overview.md) para obter informações gerais sobre o uso da ferramenta de migração.


## Pequenas alterações no formato de dados e na estrutura

Na maioria dos casos, a [Etapa do mapa](technical-specification.md#map-step) resolve suficientemente pequenas alterações de estrutura e formato de dados usando os seguintes métodos no arquivo `map.xml`:

- Alterar nomes de tabela ou campo com regras de mapeamento
- Transformar formatos de dados com manipuladores existentes ou um manipulador personalizado

O exemplo a seguir mostra como usar as regras de mapeamento e um manipulador. Este exemplo usa uma extensão Magento 1 hipotética chamada &quot;GreatBlog&quot; que foi aprimorada para Magento 2.

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- Não migre dados desnecessários da tabela de índice `great_blog_index`.
- A tabela `great_blog_publication` foi renomeada para `great_blog_post` na Magento 2, portanto, os dados são migrados para a nova tabela.
   - O campo `summary` foi renomeado para `title`, portanto, os dados são migrados para o novo campo.
   - O campo `priority` foi removido e não existe mais na Magento 2.
   - Os dados no campo `body` foram alterados e devem ser processados pelo manipulador personalizado: `\Migration\Handler\GreatBlog\NewFormat`.
- Um novo recurso de classificação foi desenvolvido para a extensão &quot;GreatBlog&quot; no Magento 2.
   - Uma nova tabela `great_blog_rating` foi criada.
   - Um novo campo `great_blog_post.rating` foi criado.

### Estender mapeamento em outras etapas

Outras etapas oferecem suporte ao mapeamento, como a [Etapa EAV](technical-specification.md#eav-step) e a Etapa de Atributos do Cliente. Essas etapas migram uma lista predefinida de tabelas de Magento. Por exemplo, suponha que a extensão &quot;GreatBlog&quot; tenha um campo adicional na tabela `eav_attribute` e o nome alterado no Magento 2. Como a tabela é processada pela [Etapa EAV](technical-specification.md#eav-step), as regras de mapeamento devem ser gravadas para o arquivo `map-eav.xml`. Os arquivos `map.xml` e `map-eav.xml` usam o mesmo esquema `map.xsd`, portanto as regras de mapeamento permanecem as mesmas.

## Principais alterações no formato de dados e na estrutura

Além da Etapa Mapear, há outras etapas no arquivo `config.xml` que migram dados com alterações importantes de formato e estrutura, incluindo:

- [Etapa de regravação do URL](technical-specification.md#url-rewrite-step)
- Etapa OrderGrids
- [Etapa EAV](technical-specification.md#eav-step)

Ao contrário da [Etapa do mapa](technical-specification.md#map-step), essas etapas examinam uma lista predefinida de tabelas em vez de todas as tabelas.

Para alterações importantes no formato de dados e na estrutura, crie uma etapa personalizada.

### Criar uma etapa personalizada

Usando o mesmo exemplo de &quot;GreatBlog&quot;, suponha que a extensão tenha uma tabela no Magento 1, mas foi reprojetada para ter duas tabelas no Magento 2.

No Magento 1, havia uma única tabela `greatblog_post`:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Na Magento 2, uma nova tabela para tags `greatblog_post_tags` foi introduzida:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

A tabela Magento 2 `greatblog_post` agora se parece com isto:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Para migrar todos os dados da estrutura de tabelas antigas para uma nova, você pode criar uma etapa personalizada no arquivo `config.xml`. Por exemplo:

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

A ferramenta executa etapas de acordo com sua posição no arquivo `config.xml`; de cima para baixo. No nosso exemplo, o `GreatBlog Step` é executado por último.

As etapas podem incluir quatro tipos de classes:

- Verificação de integridade
- Entrega de dados
- Verificação de volume
- Entrega Delta

>[!NOTE]
>
>Consulte [Configuração](technical-specification.md#configuration), [Etapas internas](technical-specification.md#step-internals), [Estágios](technical-specification.md#step-stages) e [Modos de execução](technical-specification.md#running-modes) para obter mais informações.


Consultas SQL complexas podem ser montadas dentro dessas classes para buscar e migrar dados. Além disso, essas tabelas devem ser &quot;ignoradas&quot; na [Etapa do mapa](technical-specification.md#map-step), pois ela verifica todas as tabelas existentes e tenta migrar os dados, a menos que estejam na marca `<ignore>` do arquivo `map.xml`.

Para verificação de integridade, defina um arquivo de mapa adicional no arquivo `config.xml` para verificar se a estrutura das tabelas é a esperada.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

Arquivo de mapa `map-greatblog.xml`:

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

A classe de verificação de integridade `Vendor\Migration\Step\GreatBlog\Integrity` estende `Migration\App\Step\AbstractIntegrity` e contém o método `perform` onde verificamos a estrutura da tabela:

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

Em seguida, você deve criar uma classe para processar e salvar dados no banco de dados Magento 2 `Vendor\Migration\Step\GreatBlog\Data`:

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

Em uma classe de Volume `Vendor\Migration\Step\GreatBlog\Volume`, verificamos se os dados foram totalmente migrados:

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

Para adicionar a funcionalidade de migração delta, adicione um novo grupo ao arquivo `deltalog.xml`. Em `group`, especifique o nome das tabelas nas quais devem ser verificadas as alterações:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Em seguida, crie a classe `Delta` `Vendor\Migration\Step\GreatBlog\Delta` que estende `Migration\App\Step\AbstractDelta`:

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

Após a implementação da etapa personalizada fornecida nos exemplos, o sistema retira os dados da tabela de Magento 1 único,
processe-o usando a classe `Vendor\Migration\Step\GreatBlog\Data` e armazene os dados em duas tabelas Magento 2. Registros novos e alterados são entregues na migração delta usando a classe `Vendor\Migration\Step\GreatBlog\Delta`.

## Métodos de extensão proibidos

Como o [!DNL Data Migration Tool] e o Magento 2 estão em constante evolução, as etapas e os manipuladores existentes estão sujeitos a alterações. É altamente recomendável não substituir o comportamento de etapas como [Etapa do Mapa](technical-specification.md#map-step), [Etapa de Regravação de URL](technical-specification.md#url-rewrite-step) e manipuladores, estendendo suas classes.

Algumas etapas não suportam mapeamento e não podem ser alteradas sem a alteração do código. Você pode gravar uma etapa extra que altere os dados no final da migração ou criar um [problema do GitHub](https://github.com/magento/data-migration-tool/issues) e solicitar um novo ponto de extensão na etapa existente.
