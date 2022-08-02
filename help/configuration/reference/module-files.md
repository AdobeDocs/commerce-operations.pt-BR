---
title: Arquivos de configuração do módulo
description: Saiba como personalizar um módulo usando tipos de configuração.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '2019'
ht-degree: 0%

---


# Visão geral dos arquivos de configuração do módulo

As responsabilidades da `config.xml` o arquivo de configuração usado em versões anteriores do Commerce agora é dividido entre vários arquivos, localizados em vários diretórios de módulo. Os vários arquivos de configuração do Commerce são carregados sob demanda somente quando um módulo solicita um tipo de configuração específico.

Você pode usar esses arquivos, também conhecidos como _tipos de configuração_—para personalizar aspectos específicos do comportamento do seu módulo.

Vários módulos podem declarar arquivos de configuração que afetam o mesmo tipo de configuração (por exemplo, eventos) e esses vários arquivos de configuração são mesclados.

A seguir estão termos comuns usados neste tópico:

- **Objeto Configuração**—A biblioteca ou classe Commerce responsável por definir e validar o tipo de configuração. Por exemplo, o objeto de configuração para `config.xml` é [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Fase de configuração**—Estágios definidos como _principal_, _global_ e _area_. Cada estágio determina quando o tipo de configuração é carregado e mesclado com os mesmos tipos de configuração nomeados. Por exemplo, `module.xml` os arquivos são mesclados com outros `module.xml` arquivos.

- **Escopo de configuração**—Complementar às etapas de configuração, um escopo define o modelo de tipo de configuração. Por exemplo, `adminhtml` é um escopo de área que é carregado com no estágio com outros módulos. `adminhtml` configurações. Para obter mais informações, consulte [Módulos e áreas](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_and_areas.html).

## Carregamento e mesclagem da configuração

Esta seção discute como os arquivos de configuração são carregados e mesclados.

### Como o Commerce carrega arquivos de configuração

O Commerce carrega arquivos de configuração na seguinte ordem (todos os caminhos são relativos ao seu diretório de instalação do Commerce):

- Configuração primária ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Esse arquivo é usado para inicializar o Commerce.
- Configurações globais a partir de módulos (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Coleta determinados arquivos de configuração de todos os módulos e os mescla.
- Configuração específica da área a partir de módulos (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Coleta arquivos de configuração de todos os módulos e os mescla na configuração global. Algumas configurações específicas de área podem substituir ou estender a configuração global.

em que

- `<your component base dir>` é o diretório base em que seu componente está localizado. Os valores típicos são `app/code` ou `vendor` relativo ao diretório de instalação do Commerce.
- `<vendorname>` é o nome do fornecedor do componente; por exemplo, o nome do fornecedor do Commerce é `magento`.
- `<component-type>` é um dos seguintes:

   - `module-`: Uma extensão ou módulo.
   - `theme-`: Tema.
   - `language-`: Pacote de idioma.

>[!INFO]
>
>Atualmente, os temas estão localizados em `<magento_root>/app/design/frontend` ou `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Nome do seu componente, conforme definido em [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Mesclagem do arquivo de configuração

Os nós nos arquivos de configuração são mesclados com base em seus XPouts totalmente qualificados, que têm um atributo especial definido em `$idAttributes` matriz declarada como seu identificador. Esse identificador deve ser exclusivo para todos os nós aninhados no mesmo nó pai.

Algoritmo de mesclagem de aplicativos de comércio:

- Se os identificadores de nó forem iguais (ou se não houver identificador definido), todo o conteúdo subjacente no nó (atributos, nós filho e conteúdo escalar) será substituído.
- Se os identificadores de nó não forem iguais, o nó será um novo filho do nó pai.
- Se o documento original tiver vários nós com o mesmo identificador, um erro será acionado porque os identificadores não podem ser diferenciados.

Depois que os arquivos de configuração forem mesclados, o documento resultante conterá todos os nós dos arquivos originais.

>[!INFO]
>
>Você pode usar [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) classe para depurar e entender a lógica por trás [carregador de arquivos de configuração](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) e [mesclar configurações](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) processo.

## Tipos, objetos e interfaces de configuração

As seções a seguir fornecem informações sobre os tipos de configuração, os objetos de configuração correspondentes e as interfaces que podem ser usadas para trabalhar com os objetos:

- [Tipos e objetos de configuração](#config-files-classes-objects)
- [Interfaces de configuração](#config-files-classes-int)

### Tipos e objetos de configuração

A tabela a seguir mostra cada tipo de configuração e o objeto de configuração Comércio ao qual ele está relacionado.

| Arquivo de configuração | Descrição | Fase | Objeto Configuração |
| --- | --- | --- | --- |
| `address_formats.xml` | Declaração de formato do endereço | principal, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Lista de Controle de Acesso](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication.html#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Relatórios avançados](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | principal, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Declaração de tipo de cache | principal, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuração dos atributos do catálogo | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` e `env.php` | [Configuração de implantação](../reference/deployment-files.md) | Esses arquivos podem ser lidos/gravados pelo processador de configuração interno. | Não tem objeto, não pode ser personalizado |
| `config.xml` | Configuração do sistema | principal, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Define aspectos do sistema de fila de mensagens](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Configura grupos cron](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Especifica as opções de grupo cron](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Schema declarativo](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Injeção de dependência](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/depend-inj.html) configuração | principal, global, área | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Fornece configuração de atributos EAV | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuração de modelos de email | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Configuração de palavras limites da localidade do mecanismo de pesquisa](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuração do evento/observador | global, área | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Exportar configuração de entidade | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Atributos de extensão](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/attributes.html#extension) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Define conjuntos de campos | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Declara indexadores](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Declara entidades de importação | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Define itens de menu para o Administrador | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Define os dados de configuração do módulo e a dependência suave | principal, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [Configuração do MView](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html#mview-configuration) | principal, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuração do módulo de pagamento | principal, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Persistente](https://devdocs.magento.com/guides/v2.4/mrg/module-persistent.html) arquivo de configuração | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Configurações de PDF | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Fornece configuração de opções do produto | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Define o tipo de produto | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Define a relação entre uma fila existente e seu consumidor](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queueconsumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Define a troca onde um tópico é publicado.](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuepublisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Define as regras de roteamento de mensagens, declara filas e trocas](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuetopologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Relatórios avançados](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Define o recurso do módulo | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Rota](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/routing.html) configuração | area | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Define a configuração total de vendas | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Fornece a configuração do mecanismo de pesquisa | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Define a configuração de pesquisa do catálogo | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Define ações que acionam a invalidação de cache para blocos de conteúdo privado | frontend | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Define opções para a página de configuração do sistema | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Arquivo de configuração de validação do módulo | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Define valores de configuração da exibição do Vendor_Module | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Configura uma API da Web](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/service-contracts/service-to-web-service.html) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Define rotas personalizadas REST](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/webapi/custom-routes.html) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Define widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Define o formato do código postal de cada país | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Interfaces de configuração

Você pode interagir com os arquivos de configuração usando interfaces em [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Você pode usar essas interfaces se [criar um tipo de configuração](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` O fornece as seguintes interfaces:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), que converte o XML em uma representação de matriz na memória das configurações.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), que recupera os dados de configuração em um escopo especificado.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), que identifica o local dos arquivos a serem lidos por [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), que lê os dados de configuração do armazenamento e seleciona o armazenamento do qual lê.

Ou seja, o sistema de arquivos, o banco de dados e outros armazenamentos mesclam os arquivos de configuração de acordo com as regras de mesclagem e valida os arquivos de configuração com os esquemas de validação.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), que localiza o esquema XSD.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), que retorna uma lista de escopos.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), que recupera o estado de validação.
