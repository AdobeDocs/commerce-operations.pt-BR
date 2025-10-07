---
title: Arquivos de configuração de módulo
description: Saiba como personalizar módulos usando tipos de configuração no Adobe Commerce. Descubra as práticas recomendadas de gerenciamento de arquivos de configuração e personalização de módulo.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 0%

---

# Visão geral dos arquivos de configuração do módulo

As responsabilidades do arquivo de configuração `config.xml` usado em versões anteriores do Commerce agora são divididas entre vários arquivos, localizados em vários diretórios de módulo. Vários arquivos de configuração do Commerce são carregados sob demanda somente quando um módulo solicita um tipo de configuração específico.

Você pode usar esses arquivos, também conhecidos como _tipos de configuração_, para personalizar aspectos específicos do comportamento do módulo.

Vários módulos podem declarar arquivos de configuração que afetam o mesmo tipo de configuração (por exemplo, eventos), e esses vários arquivos de configuração são mesclados.

Os termos a seguir são comuns usados neste tópico:

- **Objeto de configuração** — A biblioteca ou classe de Commerce responsável por definir e validar o tipo de configuração. Por exemplo, o objeto de configuração para `config.xml` é [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Estágio de configuração**—Os estágios estão definidos como _principal_, _global_ e _área_. Cada estágio determina quando o tipo de configuração é carregado e mesclado com tipos de configuração com o mesmo nome. Por exemplo, `module.xml` arquivos são mesclados com outros `module.xml` arquivos.

- **Escopo de configuração** — Complementar aos estágios de configuração, um escopo define o modelo de tipo de configuração. Por exemplo, `adminhtml` é um escopo de área que é carregado com no estágio com as configurações `adminhtml` de outros módulos. Para obter mais informações, consulte [Módulos e áreas](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Carregamento e mesclagem de configuração

Esta seção discute como os arquivos de configuração são carregados e mesclados.

### Como o Commerce carrega arquivos de configuração

O Commerce carrega os arquivos de configuração na seguinte ordem (todos os caminhos são relativos ao diretório de instalação do Commerce):

- Configuração primária ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Esse arquivo é usado para inicializar o Commerce.
- Configurações globais dos módulos (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Coleta determinados arquivos de configuração de todos os módulos e os mescla.
- Configuração específica de área dos módulos (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Coleta arquivos de configuração de todos os módulos e os mescla à configuração global. Algumas configurações específicas de área podem substituir ou estender a configuração global.

onde

- `<your component base dir>` é o diretório base no qual seu componente está localizado. Os valores típicos são `app/code` ou `vendor` relativos ao diretório de instalação do Commerce.
- `<vendorname>` é o nome do fornecedor do componente; por exemplo, o nome do fornecedor da Commerce é `magento`.
- `<component-type>` é um dos seguintes:

   - `module-`: Uma extensão ou um módulo.
   - `theme-`: Tema.
   - `language-`: Pacote de idioma.

>[!INFO]
>
>Atualmente, os temas estão localizados em `<magento_root>/app/design/frontend` ou `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Nome do seu componente conforme definido em [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Mesclagem do arquivo de configuração

Os nós nos arquivos de configuração são mesclados com base em seus XPaths totalmente qualificados, que têm um atributo especial definido na matriz `$idAttributes` declarada como seu identificador. Esse identificador deve ser exclusivo para todos os nós aninhados no mesmo nó principal.

algoritmo de mesclagem de aplicativos do Commerce:

- Se os identificadores de nó forem iguais (ou se não houver um identificador definido), todo o conteúdo subjacente no nó (atributos, nós secundários e conteúdo escalar) será substituído.
- Se os identificadores de nó não forem iguais, o nó será um novo filho do nó pai.
- Se o documento original tiver vários nós com o mesmo identificador, um erro será acionado porque os identificadores não podem ser diferenciados.

Depois que os arquivos de configuração forem mesclados, o documento resultante conterá todos os nós dos arquivos originais.

>[!INFO]
>
>Você pode usar a classe [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) para depurar e entender a lógica por trás do processo [carregador de arquivos de configuração](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) e [configurações de mesclagem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144).

## Tipos, objetos e interfaces de configuração

As seções a seguir fornecem informações sobre tipos de configuração, seus objetos de configuração correspondentes e interfaces que você pode usar para trabalhar com os objetos:

### Tipos e objetos de configuração

A tabela a seguir mostra cada tipo de configuração e o objeto de configuração do Commerce com o qual ele está relacionado.

| Arquivo de configuração | Descrição | Estágio | Objeto de configuração |
| --- | --- | --- | --- |
| `address_formats.xml` | Declaração de formato de endereço | principal, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Lista de Controle de Acesso](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Relatórios avançados](https://developer.adobe.com/commerce/php/development/advanced-reporting/data-collection/) | principal, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Declaração de tipo de cache | principal, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuração de atributos do catálogo | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` e `env.php` | [Configuração de implantação](../reference/deployment-files.md) | Esses arquivos podem ser lidos/gravados pelo processador de configuração interno. | Não tem objeto, não pode ser personalizado |
| `config.xml` | Configuração do sistema | principal, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Define aspectos do sistema de fila de mensagens](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Configura grupos cron](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Especifica as opções do grupo CRON](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Esquema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | Configuração de [injeção de dependência](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) | principal, global, área | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Fornece a configuração de atributos EAV | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuração de modelos de email | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Configuração de palavras irrelevantes de localidade do mecanismo de pesquisa](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuração de evento/observador | global, área | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Exportar configuração da entidade | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Atributos de extensão](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Define conjuntos de campos | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Declara indexadores](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Declara entidades de importação | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Define itens de menu para o Administrador | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Define os dados de configuração do módulo e a dependência suave | principal, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [Configuração do MView](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | principal, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuração do módulo de pagamento | principal, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | Arquivo de configuração [Magento_Persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Configurações do PDF | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Fornece configuração de opções de produto | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Define o tipo de produto | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Define a relação entre uma fila existente e seu consumidor](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Define a troca em que um tópico é publicado.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Define as regras de roteamento de mensagens, declara filas e trocas](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Relatórios avançados](https://developer.adobe.com/commerce/php/development/advanced-reporting/report-xml/) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Define o recurso do módulo | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | Configuração de [Rota](https://developer.adobe.com/commerce/php/development/components/routing/) | área | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Define a configuração total de vendas | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Fornece a configuração do mecanismo de pesquisa | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Define a configuração de pesquisa do catálogo | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Define ações que acionam a invalidação de cache para blocos de conteúdo privado | front-end | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Define opções para a página de configuração do sistema | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Arquivo de configuração de validação de módulo | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Define valores de configuração de visualização de Vendor_Module | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Configura uma API da Web](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Define as rotas personalizadas REST](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Define widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Define o formato de código postal de cada país | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Interfaces de configuração

Você pode interagir com arquivos de configuração usando interfaces em [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Você pode usar essas interfaces se [criar um tipo de configuração](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` fornece as seguintes interfaces:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), que converte o XML em uma representação de matriz na memória das configurações.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), que recupera os dados de configuração em um escopo especificado.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), que identifica o local dos arquivos a serem lidos por [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), que lê os dados de configuração do armazenamento e seleciona o armazenamento do qual lê.

Ou seja, o sistema de arquivos, o banco de dados e outros armazenamentos mesclam os arquivos de configuração de acordo com as regras de mesclagem e validam os arquivos de configuração com os esquemas de validação.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), que localiza o esquema XSD.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), que retorna uma lista de escopos.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), que recupera o estado de validação.
