---
title: Especificação técnica '[!DNL Data Migration Tool]'
description: Saiba mais sobre os detalhes de implementação do  [!DNL Data Migration Tool]  e como estender ao transferir dados entre o Magento 1 e o Magento 2.
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# Especificação técnica do [!DNL Data Migration Tool]

Esta seção descreve os detalhes de implementação do [!DNL Data Migration Tool] e como estender sua funcionalidade.

## Repositórios

Para acessar o código-fonte [!DNL Data Migration Tool], consulte o [repositório](https://github.com/magento/data-migration-tool) do GitHub.

## Requisitos do sistema

Os [requisitos de sistema](../../installation/system-requirements.md) para [!DNL Data Migration Tool] são os mesmos da Magento 2.

## Estrutura interna

### Estrutura de diretório

O diagrama a seguir representa a estrutura de diretório de [!DNL Data Migration Tool]:

```
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## Ponto de entrada

O script que executa o processo de migração está localizado em: `magento-root/bin/magento`.

## Configuração

O esquema do arquivo de configuração `config.xsd` está localizado no diretório `etc/`. O arquivo de configuração padrão (`config.xml.dist`) é criado para cada versão do Magento 1.x. Está localizado em um diretório separado em `etc/`.

O arquivo de configuração padrão pode ser substituído por um personalizado (consulte [sintaxe do comando](migrate-data/overview.md#command-syntax)).

O arquivo de configuração tem a seguinte estrutura:

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* etapas - descreve todas as etapas processadas durante a migração

* origem - configuração da origem de dados. Tipos de origem disponíveis: banco de dados

* destino - configuração para destino de dados. Tipos de destino disponíveis: banco de dados

* opções - lista de parâmetros. Contém os parâmetros obrigatórios (map_file, settings_map_file, bulk_size) e opcionais (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file)

Altere a opção de prefixo caso o Magento tenha sido instalado com prefixo em tabelas de banco de dados. Ele pode ser definido para bancos de dados Magento 1 e Magento 2. Use as opções de configuração &quot;source_prefix&quot; e &quot;dest_prefix&quot; adequadamente.

Os dados de configuração estão acessíveis com a classe `\Migration\Config`.

## Etapas de operações disponíveis

| Documento | Campo |
|---|---|
| `step` | Nó de segundo nível dentro do nó Etapas. A descrição da etapa relevante deve ser especificada no atributo `title`. |
| `integrity` | Especifica a classe PHP responsável pela verificação de integridade. Compara os nomes de campos, tipos e outras informações da tabela para verificar a compatibilidade entre as estruturas de dados Magento 1 e 2. |
| `data` | Especifica a classe PHP responsável pela verificação de dados. Transfere os dados, tabela por tabela, do Magento 1 para o Magento 2. |
| `volume` | Especifica a classe PHP responsável pela verificação de volume. Compara o número de registros entre tabelas para verificar se a transferência foi bem-sucedida. |
| `delta` | Especifica a classe PHP responsável pela verificação delta. Transfere o delta do Magento 1 para o Magento 2 após a migração completa de dados. |

## Atributos de informações do banco de dados Source

| Documento | Campo | Obrigatório? |
|---|---|---|
| `name` | Nome do banco de dados do servidor Magento 1. | sim |
| `host` | Endereço IP do host do servidor Magento 1. | sim |
| `port` | Número da porta do servidor Magento 1. | não |
| `user` | Nome de usuário do servidor de banco de dados Magento 1. | sim |
| `password` | Senha do servidor de banco de dados Magento 1. | sim |
| `ssl_ca` | Caminho para o arquivo da Autoridade de certificação SSL. | não |
| `ssl_cert` | Caminho para o arquivo de certificado SSL. | não |
| `ssl_key` | Caminho para o arquivo da chave SSL. | não |

## Atributos de informações do banco de dados de destino

| Documento | Campo | Obrigatório? |
|---|---|---|
| `name` | Nome do banco de dados do servidor Magento 2. | sim |
| `host` | Endereço IP do host do servidor Magento 2. | sim |
| `port` | Número da porta do servidor Magento 2. | não |
| `user` | Nome de usuário do servidor de banco de dados Magento 2. | sim |
| `password` | Senha do servidor de banco de dados Magento 2. | sim |
| `ssl_ca` | Caminho para o arquivo da Autoridade de certificação SSL. | não |
| `ssl_cert` | Caminho para o arquivo de certificado SSL. | não |
| `ssl_key` | Caminho para o arquivo da chave SSL. | não |

## Conectar-se usando o protocolo TLS

Você também pode se conectar a um banco de dados usando o protocolo TLS (ou seja, usando chaves criptográficas públicas/privadas). Adicione os seguintes atributos opcionais ao elemento `database`:

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Por exemplo:

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Etapa interna

O processo de migração consiste em etapas.

A etapa é uma unidade que fornece a funcionalidade necessária para a migração de alguns dados separados. A etapa pode consistir em um ou mais estágios (verificação de integridade, dados, verificação de volume e delta).

Por padrão, há várias etapas ([Map](#map-step), [EAV](#eav), [Regravações de URL](#url-rewrite-step) e assim por diante). Opcionalmente, também é possível adicionar suas próprias etapas.

As classes relacionadas às etapas estão localizadas no diretório src/Migration/Step.

Para executar uma classe Step, a classe deve ser definida no arquivo config.xml.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

Cada classe de estágio deve implementar StageInterface.

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

Se o estágio de dados suportar reversão, ele deverá implementar a interface `RollbackInterface`.

A visualização da etapa em execução é fornecida pelo componente ProgressBar do Symfony (consulte [Barra de progresso](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Acesse esse componente em uma etapa como LogLevelProcessor.

Os principais métodos de uso são:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Etapas

### Verificação de integridade

Cada etapa deve verificar se a estrutura da fonte de dados (Magento 1 por padrão) e a estrutura do destino de dados (Magento 2) são compatíveis. Caso contrário, um erro será exibido com entidades incompatíveis. Caso os campos tenham tipos de dados diferentes (o mesmo campo tem tipo de dados decimal em Magento 1 e inteiro em Magento 2), uma mensagem de aviso é exibida (exceto quando foi abordado no Arquivo de mapa ).

### Transferência de dados

Caso a verificação de integridade seja aprovada, a transferência de dados está em execução. Se ocorrerem erros, a reversão será executada para reverter ao estado anterior do Magento 2. Se uma classe de etapa implementa a interface `RollbackInterface`, o método de reversão é executado quando há um erro.

### Verificação de volume

Após a migração dos dados, a Verificação de volume fornece uma verificação adicional para confirmar se todos os dados foram transferidos corretamente.

### Entrega delta

A funcionalidade Delta é responsável por fornecer o restante dos dados adicionados após a migração principal.

## Modos de execução

A ferramenta deve ser executada em três modos diferentes, em ordem específica:

1. configurações - migração de configurações do sistema
1. dados - principal migração de dados
1. delta - migração do restante dos dados que foram adicionados após a migração principal

Cada modo tem sua própria lista de etapas a serem executadas. Consulte config.xml

### Modo de migração de configurações

O modo de migração de configurações desta ferramenta é usado para transferir as seguintes entidades:

1. Sites, lojas, visualizações de loja.
1. Configuração de armazenamento (principalmente Lojas->Configuração em M2 ou Sistema->Configuração em M1)

Toda configuração de armazenamento mantém os dados na tabela core_config_data no banco de dados. o arquivo settings.xml contém regras para essa tabela que são aplicadas durante o processo de migração. Este arquivo descreve configurações que devem ser ignoradas, renomeadas ou devem alterar seus valores. o arquivo settings.xml tem a seguinte estrutura:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

No nó `<key>` há regras que funcionam com a coluna &#39;path&#39; na tabela `core_config_data`. `<ignore>` regras impedem que a ferramenta transfira algumas configurações. Os curingas podem ser usados neste nó. Todas as outras configurações não listadas no nó `<ignore>` são migradas. Se o caminho para uma configuração tiver sido alterado no Magento 2, ele deverá ser adicionado ao nó `//key/rename`, onde o caminho antigo indica no nó `//key/rename/path` e o novo caminho indica no nó `//key/rename/to`.

No nó `<value>`, há regras que funcionam com a coluna &#39;value&#39; na tabela `core_config_data`. Essas regras têm como objetivo transformar o valor das configurações por manipuladores (classes que implementam `Migration\Handler\HandlerInterface`) e adaptá-lo para o Magento 2.

### Modo de migração de dados

Nesse modo, a maioria dos dados é migrada. Antes da migração de dados, os estágios de verificação de integridade são executados para cada etapa. Se a verificação de integridade for aprovada, o [!DNL Data Migration Tool] instalará tabelas deltalog (com prefixo `m2_cl_*`) e gatilhos correspondentes para o banco de dados Magento 1 e executará o estágio de migração de dados das etapas. Quando a migração for concluída sem erros, a verificação de volume verificará a consistência dos dados. Ele pode mostrar uma mensagem de aviso se você migrar a loja em tempo real. Não se preocupe, a migração delta cuida desses dados incrementais. As etapas de migração mais valiosas são Mapa, Reescrita de URL e EAV.

#### Etapa do mapa

A etapa do mapa é responsável pela transferência da maioria dos dados do Magento 1 para o Magento 2. Esta etapa lê as instruções do arquivo map.xml (localizado no diretório `etc/`). O arquivo descreve as diferenças entre as estruturas de dados de origem (Magento 1) e destino (Magento 2). Se o Magento 1 contiver tabelas ou campos que pertençam a alguma extensão que não exista no Magento 2, essas entidades poderão ser colocadas aqui para ignorá-las pela Etapa do mapa. Caso contrário, exibirá uma mensagem de erro.

O arquivo de mapa tem o formato seguinte:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

Áreas:

* *origem* - contém regras do banco de dados de origem

* *destino* - contém regras do banco de dados de destino

Opções:

* *ignorar* - documento, campo ou tipo de dados marcado com esta opção é ignorado

* *renomear* - descreve as relações de nome entre documentos com nomes diferentes. Em um caso em que o nome do documento de destino não é o mesmo que o documento de origem, você pode usar a opção de renomear para definir o nome do documento de origem como o nome da tabela de destino

* *mover* - define a regra para mover o campo especificado do documento de origem para o documento de destino. OBSERVAÇÃO: o nome do documento de destino deve ser igual ao nome do documento de origem. Se os nomes do documento de origem e de destino forem diferentes - será necessário usar a opção de renomeação para o documento que contém o campo movido

* *transform* - é uma opção que permite que o usuário migre campos de acordo com o comportamento descrito nos manipuladores

* *manipulador* - descreve o comportamento de transformação dos campos. Para chamar o manipulador, você precisa especificar um nome de classe de manipulador em uma marca `<handler>`. Use a marca `<param>` com os dados de nome e valor do parâmetro para passá-la para o manipulador

**Source** operações disponíveis:

| Documento | Campo |
|--- |--- |
| ignorar renomeação | ignorar transformação de movimentação |

**Destino** operações disponíveis:

| Documento | Campo |
|--- |--- |
| ignorar | ignorar transformação |

#### Curingas

Para ignorar documentos com partes semelhantes (`document_name_1`, `document_name_2`), você pode usar a funcionalidade curinga. Coloque o símbolo `*` em vez da parte repetitiva (`document_name_*`) e esta máscara cobrirá todos os documentos de origem ou destino que atendam a essa máscara.

#### Etapa de regravação de URL

Esta etapa é complexa porque existem vários algoritmos diferentes desenvolvidos no Magento 1 que não são compatíveis com o Magento 2. Para versões diferentes do Magento 1, pode haver algoritmos diferentes. Assim, na pasta Step/UrlRewrite, há classes que foram desenvolvidas para algumas versões específicas do Magento e Migration\Step\UrlRewrite\Version191to2000 é uma delas. Ele pode transferir dados de regravação de URL do Magento 1.9.1 para o Magento 2.

#### Etapa EAV

Esta etapa transfere todos os atributos (produto, cliente, RMA) do Magento 1 para o Magento 2. Ele usa o arquivo map-eav.xml que contém regras semelhantes às do arquivo map.xml para casos específicos de processamento de dados.

Algumas das tabelas que são processadas na etapa:

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Modo de migração delta

Após a migração principal, dados adicionais poderiam ter sido adicionados ao banco de dados Magento 1 (por exemplo, por clientes na loja). Para rastrear esses dados, a ferramenta configura os acionadores de banco de dados para tabelas no início do processo de migração. Para obter mais informações, consulte [Migrar dados criados por extensões de terceiros](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Fontes de dados

Para acessar as fontes de dados de Magento 1 e Magento 2 e operar com seus dados (selecionar, atualizar, inserir, excluir) há muitas classes na pasta Recursos. Migration\ResourceModel\Source e Migration\ResourceModel\Destination são classes principais. Todas as etapas de migração o usam para operar com dados. Esses dados estão contidos em classes como Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure, etc.

Este é um diagrama de classes dessas classes:

![Estrutura de Dados da Ferramenta de Migração](../../assets/data-migration/MmigrationToolDataStructure.png)

## Logs

Para implementar a saída do processo de migração e controlar todos os níveis possíveis PSR logger, que é usado em Magento, é aplicado. A classe `\Migration\Logger\Logger` foi implementada para fornecer funcionalidade de log. Para usar o agente de log, você deve inseri-lo por meio da injeção de dependência do construtor.

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

Depois disso, você poderá usar essa classe para registrar alguns eventos:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Há uma possibilidade de personalizar onde as informações de log devem ser gravadas. Você pode fazer isso adicionando manipulador ao agente de log usando o método pushHandler() do agente de log. Cada manipulador deve implementar a interface `\Monolog\Handler\HandlerInterface`. Como por enquanto, há dois manipuladores:

* ConsoleHandler: grava mensagens no console

* FileHandler: grava mensagens no arquivo de log que foi definido na opção de configuração &quot;log_file&quot;

Também é possível implementar qualquer manipulador adicional. Há um conjunto de manipuladores na estrutura Magento. Exemplo de adição de manipuladores ao agente de log:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Para definir dados adicionais para o logger (modo atual, nome da tabela) você pode usar processadores de logger. Há um processador existente (MessageProcessor). Ele é criado para adicionar dados &quot;extras&quot; para registrar mensagens e é chamado sempre que o método de log é executado. MessageProcessor protegeu $extra var, que contém valores vazios para &quot;mode&quot;, &quot;stage&quot;, &quot;step&quot; e &quot;table&quot;. Os dados extras podem ser passados para o processador como um segundo parâmetro (contexto) para o método de log. Atualmente, conjuntos de dados adicionais para o processador no método AbstractStep->runStage (passe o modo atual, o estágio e a etapa para o processador) e classes de dados onde foram usados logger->debug method (passe o nome da tabela de migração). Exemplo de adição de processadores ao logger:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Há uma possibilidade de definir o nível de verbosidade. Por enquanto, existem três níveis:

* `ERROR` (grava somente erros no log)
* `INFO` (somente informações importantes são gravadas no log, valor padrão)
* `DEBUG` (tudo está escrito)

O nível de log de detalhamento pode ser definido separadamente para cada manipulador, chamando o método `setLevel()`. Se quiser definir o nível de detalhamento por meio do parâmetro de linha de comando, altere a opção &quot;verbose&quot; na inicialização do aplicativo.

Você pode formatar mensagens de log com o formatador de monólogo. Para que a funcionalidade do formatador funcione, você deve especificar o manipulador de log usando o método `setFormatter()`. Atualmente, temos uma classe de formatador (`MessageFormatter`) que define determinado formato (depende do nível de verbosidade) durante o manuseio de mensagens (por meio do método `format()` executado a partir do manipulador).

Manipular o agente de log (adicionando manipuladores e processadores) e processar em modo detalhado é executado no método `process()` da classe `Migration\Logger\Manager`. O método é chamado quando o aplicativo é iniciado.

## Testes automáticos

Há três tipos de testes no [!DNL Data Migration Tool]:

* Estático
* Unidade
* Integração

Eles estão localizados no diretório `tests/` da ferramenta, que é o mesmo tipo de teste (testes de unidade estão localizados no diretório `tests/unit`). Para iniciar o teste, você deve ter o phpunit instalado. Altere o diretório atual para o diretório de teste e inicie phpunit. Por exemplo:

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
