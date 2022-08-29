---
title: Personalize o [!DNL Data Migration Tool]
description: Saiba como personalizar o [!DNL Data Migration Tool] para transferir dados criados por extensões entre o Magento 1 e o Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---


# Configure o [!DNL Data Migration Tool]

Às vezes, o formato e a estrutura de dados criados por [extensões](https://marketplace.magento.com/extensions.html) ou o código personalizado é diferente entre o Magento 1 e o Magento 2. Use pontos de extensão no [!DNL Data Migration Tool] para migrar esses dados. Se o formato e a estrutura dos dados forem iguais, a ferramenta poderá migrar automaticamente os dados sem a intervenção do usuário.

Durante a migração, a variável [Etapa do mapa](technical-specification.md#map-step) verifica e compara todas as tabelas Magento 1 e Magento 2, incluindo as criadas por extensões. Se as tabelas forem as mesmas, a ferramenta migra os dados automaticamente. Se as tabelas forem diferentes, a ferramenta terminará e notificará o usuário.

>[!NOTE]
>
>Leia o [Especificação técnica](technical-specification.md) antes de tentar estender o [!DNL Data Migration Tool]. Além disso, revise a [Guia de migração](../overview.md) para obter informações gerais sobre o uso da ferramenta de migração.


## Pequenas alterações no formato de dados e na estrutura

Na maioria dos casos, a variável [Etapa do mapa](technical-specification.md#map-step) resolve suficientemente pequenas alterações no formato dos dados e na estrutura usando os seguintes métodos no `map.xml` arquivo:

- Alterar nomes de tabela ou campo com regras de mapeamento
- Transformar formatos de dados com manipuladores existentes ou personalizados

A seguir, há um exemplo de uso de regras de mapeamento e um manipulador. Este exemplo usa uma extensão hipotética do Magento 1 chamada &quot;GreatBlog&quot; que foi aprimorada para o Magento 2.

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

- Não migre dados desnecessários do `great_blog_index` tabela de índice.
- A tabela `great_blog_publication` foi renomeado para `great_blog_post` na Magento 2, portanto, os dados são migrados para a nova tabela.
   - O `summary` campo foi renomeado para `title`, portanto, os dados são migrados para o novo campo.
   - O `priority` O campo foi removido e não existe mais no Magento 2.
   - Os dados no `body` O campo mudou o formato e deve ser processado pelo manipulador personalizado: `\Migration\Handler\GreatBlog\NewFormat`.
- Um novo recurso de classificações foi desenvolvido para a extensão &quot;GreatBlog&quot; no Magento 2.
   - Um novo `great_blog_rating` tabela foi criada.
   - Um novo `great_blog_post.rating` foi criado.

### Estender mapeamento em outras etapas

Outras etapas são compatíveis com o mapeamento, como [Etapa EAV](technical-specification.md#eav-step) e na etapa Atributos do cliente . Essas etapas migram uma lista predefinida de tabelas de Magento. Por exemplo, suponha que a extensão &quot;GreatBlog&quot; tenha um campo adicional na variável `eav_attribute` e o nome foi alterado no Magento 2. Como a tabela é processada pela variável [Etapa EAV](technical-specification.md#eav-step), as regras de mapeamento devem ser gravadas para a variável `map-eav.xml` arquivo. O `map.xml` e `map-eav.xml` os arquivos usam o mesmo `map.xsd` assim, as regras de mapeamento permanecem as mesmas.

## Alterações importantes no formato e na estrutura dos dados

Além da Etapa do mapa, há outras etapas na variável `config.xml` arquivo que migra dados com grandes alterações de formato e estrutura, incluindo:

- [Etapa De Reescrita De Url](technical-specification.md#url-rewrite-step)
- Etapa OrderGrids
- [Etapa EAV](technical-specification.md#eav-step)

Ao contrário do [Etapa do mapa](technical-specification.md#map-step), essas etapas digitalizam uma lista predefinida de tabelas em vez de todas as tabelas.

Para grandes alterações de formato e estrutura de dados, crie uma etapa personalizada.

### Criar uma etapa personalizada

Usando o mesmo exemplo &quot;GreatBlog&quot;, suponhamos que a extensão tenha uma tabela no Magento 1, mas tenha sido reprojetada para ter duas tabelas no Magento 2.

Na Magento 1, havia um único `greatblog_post` tabela:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Na Magento 2, uma nova tabela para tags `greatblog_post_tags` foi introduzido:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento 2 `greatblog_post` agora tem esta aparência:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Para migrar todos os dados da estrutura de tabelas antigas para uma nova, você pode criar uma etapa personalizada no `config.xml` arquivo. Por exemplo:

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

A ferramenta executa etapas de acordo com sua posição na `config.xml` ficheiro; de cima para baixo. Em nosso exemplo, a variável `GreatBlog Step` é executado por último.

As etapas podem incluir quatro tipos de classes:

- Verificação da integridade
- Delivery de dados
- Verificação do volume
- Delivery Delta

>[!NOTE]
>
>Consulte [Configuração](technical-specification.md#configuration), [Etapas internas](technical-specification.md#step-internals), [Estágios](technical-specification.md#step-stages)e [Modos de execução](technical-specification.md#running-modes) para obter mais informações.


Consultas SQL complexas podem ser montadas dentro dessas classes para buscar e migrar dados. Além disso, essas tabelas devem ser &quot;ignoradas&quot; na variável [Etapa do mapa](technical-specification.md#map-step) porque ela verifica todas as tabelas existentes e tenta migrar os dados, a menos que esteja no `<ignore>` da `map.xml` arquivo.

Para a verificação de Integridade, defina um arquivo de mapa adicional no `config.xml` para verificar se a estrutura das tabelas é a esperada.

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

Classe de verificação de integridade `Vendor\Migration\Step\GreatBlog\Integrity` estende `Migration\App\Step\AbstractIntegrity` e contém a variável `perform` método no qual verificamos a estrutura da tabela:

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

Em seguida, você deve criar uma classe para processar e salvar dados no banco de dados do Magento 2 `Vendor\Migration\Step\GreatBlog\Data`:

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

Em uma classe Volume `Vendor\Migration\Step\GreatBlog\Volume`, verificamos se os dados foram totalmente migrados:

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

Para adicionar a funcionalidade de migração de delta, adicione um novo grupo à `deltalog.xml` arquivo. Em `group`, especifique o nome das tabelas que devem ser verificadas para alterações:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Em seguida, crie a `Delta` classe `Vendor\Migration\Step\GreatBlog\Delta` que abrange `Migration\App\Step\AbstractDelta`:

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

Após a implementação da etapa personalizada fornecida nos exemplos, o sistema pega os dados da tabela de Magento 1 único, processa-os usando `Vendor\Migration\Step\GreatBlog\Data` e armazene os dados em duas tabelas Magento 2. Registros novos e alterados são entregues na migração de delta usando o `Vendor\Migration\Step\GreatBlog\Delta` classe .

## Métodos de extensão proibidos

Como a variável [!DNL Data Migration Tool] e o Magento 2 estão em constante evolução, as etapas e manipuladores existentes estão sujeitos a alterações. É altamente recomendável não substituir o comportamento de etapas como [Etapa do mapa](technical-specification.md#map-step), [Etapa de reescrita do URL](technical-specification.md#url-rewrite-step)e manipuladores estendendo suas classes.

Algumas etapas não são compatíveis com o mapeamento e não podem ser alteradas sem alterar o código. Você pode gravar uma etapa extra que altera os dados no final da migração ou criar um [Problema do GitHub](https://github.com/magento/data-migration-tool/issues) e solicite um novo ponto de extensão na etapa existente.
