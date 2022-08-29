---
title: '"[!DNL Data Migration Tool] especificação técnica"'
description: '"Saiba mais sobre os detalhes de implementação do [!DNL Data Migration Tool] e como estender ao transferir dados entre Magento 1 e Magento 2."'
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '2091'
ht-degree: 0%

---


# [!DNL Data Migration Tool] especificação técnica

Esta seção descreve [!DNL Data Migration Tool] detalhes de implementação e como estender sua funcionalidade.

## Repositórios

Para acessar o [!DNL Data Migration Tool] código fonte, consulte o GitHub [repositório](https://github.com/magento/data-migration-tool).

## Requisitos do sistema

O [requisitos do sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) para [!DNL Data Migration Tool] são iguais ao Magento 2.

## Estrutura interna

### Estrutura do diretório

O diagrama a seguir representa a estrutura de diretório de [!DNL Data Migration Tool]:

```terminal
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
│       ├── ResourceModel                   --- contains [adapter](https://glossary.magento.com/adapter) for connection to data storage and classes to work with structured data
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
│       ├── [Exception](https://glossary.magento.com/exception).php
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

O esquema da configuração `config.xsd` O arquivo está localizado na `etc/` diretório. O arquivo de configuração padrão (`config.xml.dist`) é criada para cada versão do Magento 1.x. Está localizado em um diretório separado em `etc/`.

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

* etapas - descreve todas as etapas que são processadas durante a migração

* source - configuração para a fonte de dados. Tipos de origem disponíveis: banco de dados

* destination - configuração for data destination. Tipos de destino disponíveis: banco de dados

* opções - lista de parâmetros. Contém parâmetros obrigatórios (map_file, settings_map_file, bulk_size) e opcionais (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file)

Altere a opção de prefixo caso o Magento tenha sido instalado com prefixo nas tabelas do banco de dados. Ele pode ser definido para bancos de dados Magento 1 e Magento 2. Use as opções de configuração &quot;source_prefix&quot; e &quot;dest_prefix&quot; de acordo.

Os dados de configuração podem ser acessados com a variável `\Migration\Config` classe .

## Etapas de operações disponíveis

| Documento | Campo |
|---|---|
| `step` | Nó de segundo nível dentro do nó Etapas . A descrição da etapa relevante deve ser especificada no `title` atributo. |
| `integrity` | Especifica a classe PHP responsável pela verificação de integridade. Compara os nomes, tipos e outras informações dos campos da tabela para verificar a compatibilidade entre as estruturas de dados Magento 1 e 2. |
| `data` | Especifica a classe PHP responsável pela verificação de dados. Transfere os dados, tabela por tabela de Magento 1 para Magento 2. |
| `volume` | Especifica a classe PHP responsável pela verificação de volume. Compara o número de registros entre tabelas para verificar se a transferência foi bem-sucedida. |
| `delta` | Especifica a classe PHP responsável pela verificação delta. Transfere o delta do Magento 1 para o Magento 2 após a migração completa de dados. |

## Atributos de informações do banco de dados de origem

| Documento | Campo | Obrigatório? |
|---|---|---|
| `name` | Nome do banco de dados do servidor Magento 1. | sim |
| `host` | Endereço IP do host do servidor Magento 1. | sim |
| `port` | Número da porta do servidor Magento 1. | não |
| `user` | Nome de usuário do servidor de banco de dados do Magento 1. | sim |
| `password` | Senha do servidor de banco de dados do Magento 1. | sim |
| `ssl_ca` | Caminho para o arquivo da autoridade de certificação SSL. | não |
| `ssl_cert` | Caminho para o arquivo de certificado SSL. | não |
| `ssl_key` | Caminho para o arquivo de chave SSL. | não |

## Atributos de informações do banco de dados de destino

| Documento | Campo | Obrigatório? |
|---|---|---|
| `name` | Nome do banco de dados do servidor Magento 2. | sim |
| `host` | Endereço IP do host do servidor Magento 2. | sim |
| `port` | Número da porta do servidor Magento 2. | não |
| `user` | Nome de usuário do servidor de banco de dados do Magento 2. | sim |
| `password` | Senha do servidor de banco de dados do Magento 2. | sim |
| `ssl_ca` | Caminho para o arquivo da autoridade de certificação SSL. | não |
| `ssl_cert` | Caminho para o arquivo de certificado SSL. | não |
| `ssl_key` | Caminho para o arquivo de chave SSL. | não |

## Conecte-se usando o protocolo TLS

Você também pode se conectar a um banco de dados usando o protocolo TLS (ou seja, usando chaves criptográficas públicas/privadas). Adicione os seguintes atributos opcionais à `database` elemento:

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

## Etapas internas

O processo de migração consiste em etapas.

Etapa é uma unidade que fornece a funcionalidade necessária para a migração de alguns dados separados. A etapa pode consistir em um ou mais estágios (verificação de integridade, dados, verificação de volume e delta).

Por padrão, há várias etapas ([Mapa](#map-step), [EAV](#eav), [Substituições de URL](#url-rewrite-step)e assim por diante). Opcionalmente, também é possível adicionar suas próprias etapas.

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

Toda classe stage deve implementar StageInterface.

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

Se o estágio de dados suportar reversão, ele deverá implementar a variável `RollbackInterface` interface.

A visualização da etapa em execução é fornecida pelo componente ProgressBar do Symfony (consulte [Barra de progresso](http://symfony.com/doc/current/components/console/helpers/progressbar.html)). Acesse este componente em uma etapa como LogLevelProcessor.

Os principais métodos de uso são:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Etapas da etapa

### Verificação de integridade

Cada etapa deve verificar se a estrutura da fonte de dados (Magento 1 por padrão) e a estrutura do destino de dados (Magento 2) são compatíveis. Caso contrário, um erro será exibido com entidades que não são compatíveis. Caso os campos tenham tipos de dados diferentes (o mesmo campo tem tipo de dados decimal na Magento 1 e número inteiro na Magento 2), uma mensagem de aviso é exibida (exceto quando foi coberto no arquivo Mapa).

### Transferência de dados

Caso a verificação de integridade tenha sido aprovada, a transferência de dados está em execução. Se os erros forem exibidos, a reversão será executada para reverter para o estado anterior do Magento 2. Se uma classe Step implementar o `RollbackInterface` , o método de reversão é executado quando há um erro.

### Verificação de volume

Após a migração dos dados, a Verificação de Volume fornece verificação adicional de que todos os dados foram transferidos corretamente.

### Delivery delta

A funcionalidade Delta é responsável por fornecer o resto dos dados adicionados após a migração principal.

## Modos de execução

A ferramenta deve ser executada em três modos diferentes, em particular, na ordem:

1. configurações - migração das configurações do sistema
1. dados - principal migração de dados
1. delta - migração do restante dos dados adicionados após a migração principal

Cada modo tem sua própria lista de etapas a serem executadas. Consulte config.xml

### Modo de migração de configurações

O modo de migração de configurações desta ferramenta é usado para transferir as seguintes entidades:

1. Sites, lojas, visualizações de loja.
1. Configuração de armazenamento (principalmente Lojas->Configuração no M2 ou Sistema->Configuração no M1)

Toda configuração de armazenamento mantém seus dados na tabela core_config_data no banco de dados. o arquivo settings.xml contém regras para essa tabela que são aplicadas durante o processo de migração. Este arquivo descreve as configurações que devem ser ignoradas, renomeadas ou devem alterar seus valores. o arquivo settings.xml tem a seguinte estrutura:

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

No nó `<key>` há regras que funcionam com a coluna &quot;caminho&quot; na `core_config_data` tabela. `<ignore>` As regras impedem que a ferramenta transfira algumas configurações. Os curingas podem ser usados neste nó. Todas as outras configurações não listadas na `<ignore>` são migrados. Se o caminho para uma configuração for alterado no Magento 2, ele deverá ser adicionado a `//key/rename` , onde o caminho antigo indica em `//key/rename/path` o nó e o novo caminho indicam em `//key/rename/to` nó .

No nó `<value>`, há regras que funcionam com a coluna &quot;valor&quot; na `core_config_data` tabela. Essas regras têm como objetivo transformar o valor das configurações por manipuladores (classes que implementam `Migration\Handler\HandlerInterface`) e adaptá-la para a Magento 2.

### Modo de migração de dados

Nesse modo, a maioria dos dados é migrada. Antes da migração de dados, os estágios de verificação de integridade são executados para cada etapa. Se a verificação de integridade for bem-sucedida, a variável [!DNL Data Migration Tool] instala tabelas do deltalog (com prefixo `m2_cl_*`) e acionadores correspondentes ao banco de dados do Magento 1 e executa o estágio de migração de dados das etapas. Quando a migração é concluída sem erros, a verificação de volume verifica a consistência dos dados. Ela pode mostrar uma mensagem de aviso se você migrar a loja ao vivo. Não se preocupe, a migração delta cuida desses dados incrementais. As etapas de migração mais valiosas são Mapa, Reescrita de URL e EAV.

#### Etapa do mapa

A etapa do mapa é responsável por transferir a maioria dos dados do Magento 1 para o Magento 2. Esta etapa lê as instruções do arquivo map.xml (localizado na `etc/` diretório). O arquivo descreve as diferenças entre as estruturas de dados de origem (Magento 1) e de destino (Magento 2). Caso o Magento 1 contenha tabelas ou campos que pertencem a alguns [extensão](https://glossary.magento.com/extension) que não existe na Magento 2, então essas entidades podem ser colocadas aqui para ignorá-las por meio da Etapa do mapa. Caso contrário, exibe uma mensagem de erro.

O arquivo de mapa tem o próximo formato:

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

* *source* - contém regras do banco de dados de origem

* *destino* - contém regras do banco de dados de destino

Opções:

* *ignorar* - o documento, campo ou tipo de dados marcado com esta opção é ignorado

* *renomear* - descreve as relações de nomes entre documentos com um nome diferente. Em um caso em que o nome do documento de destino não seja o mesmo com o documento de origem, você pode usar a opção renomear para definir o nome do documento de origem como o nome da tabela de destino

* *mover* - define a regra para mover o campo especificado do documento de origem para o documento de destino. OBSERVAÇÃO: o nome do documento de destino deve ser o mesmo com o nome do documento de origem. Se os nomes dos documentos de origem e de destino forem diferentes - é necessário usar a opção de renomear para o documento que contém o campo movido

* *transformação* - é uma opção que permite ao usuário migrar campos de acordo com o comportamento descrito em manipuladores

* *manipulador* - descreve o comportamento de transformação dos campos. Para chamar o manipulador, é necessário especificar um nome de classe de manipulador em um `<handler>` . Use o `<param>` adicione uma tag com o nome do parâmetro e os dados de valor para passá-los ao manipulador

**Origem** operações disponíveis:

| Documento | Campo |
|--- |--- |
| ignorar renomear | ignorar transformação de movimentação |

**Destino** operações disponíveis:

| Documento | Campo |
|--- |--- |
| ignorar | ignorar transformação |

#### Curingas

Para ignorar documentos com partes semelhantes (`document_name_1`, `document_name_2`), você pode usar a funcionalidade curinga. Put `*` símbolo em vez de parte repetitiva (`document_name_*`) e essa máscara cobre todos os documentos de origem ou de destino que atendem a essa máscara.

#### Etapa de reescrita de URL

Essa etapa é complexa porque há muitos algoritmos diferentes desenvolvidos no Magento 1 que não são compatíveis com o Magento 2. Para diferentes versões do Magento 1, pode haver algoritmos diferentes. Assim, na pasta Step/UrlRewrite , há classes que foram desenvolvidas para algumas versões específicas do Magento e Migration\Step\UrlRewrite\Version191to2000 is one of them. Ele pode transferir dados de regravações de URL do Magento 1.9.1 para o Magento 2.

#### Etapa EAV

Esta etapa transfere todos os atributos (produto, cliente, RMA) do Magento 1 para o Magento 2. Ele usa o arquivo map-eav.xml que contém regras semelhantes às do arquivo map.xml para casos específicos de dados de processamento.

Algumas das tabelas que são processadas na etapa :

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Modo de migração delta

Após a migração principal, dados adicionais podem ter sido adicionados ao banco de dados do Magento 1 (por exemplo, por clientes na loja). Para rastrear esses dados, a ferramenta configura os acionadores do banco de dados para tabelas no início do processo de migração. Para obter mais informações, consulte [Migrar dados criados por extensões de terceiros](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Fontes de dados

Para acessar as fontes de dados do Magento 1 e do Magento 2 e operar com seus dados (selecione, atualize, insira, exclua) existem muitas classes na pasta Recurso. Migration\ResourceModel\Source and Migration\ResourceModel\Destination são classes principais. Todas as etapas de migração o utilizam para operar com dados. Esses dados estão contidos em classes como Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure etc.

Este é um diagrama de classe dessas classes:

![Estrutura de dados da ferramenta de migração](../../assets/data-migration/MmigrationToolDataStructure.png)

## Registro

Para implementar a saída do processo de migração e controlar todos os níveis possíveis do logger PSR, que é usado no Magento, é aplicado. `\Migration\Logger\Logger` A classe foi implementada para fornecer funcionalidade de registro. Para usar o agente de log, você deve injetá-lo por meio do construtor [injeção de dependência](https://glossary.magento.com/dependency-injection).

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

Há a possibilidade de personalizar onde as informações de log devem ser gravadas. Você pode fazer isso adicionando o manipulador ao agente de log usando o método pushHandler() do agente de log. Cada manipulador deve implementar `\Monolog\Handler\HandlerInterface` interface. Por enquanto, há dois manipuladores:

* ConsoleHandler: grava mensagens no console

* FileHandler: grava mensagens no arquivo de log que foi definido na opção de configuração &quot;log_file&quot;

Além disso, é possível implementar qualquer manipulador adicional. Há um conjunto de manipuladores na estrutura Magento. Exemplo de adição de manipuladores ao agente de log:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Para definir dados adicionais para o logger (modo atual, nome da tabela), você pode usar processadores de logger. Há um processador existente (MessageProcessor). Ele é criado para adicionar dados &quot;extras&quot; para registrar mensagens e é chamado sempre que o método de log é executado. MessageProcessor protegeu $extra var, que contém valores vazios para &#39;mode&#39;, &#39;stage&#39;, &#39;step&#39; e &#39;table&#39;. Os dados extras podem ser passados para o processador como um segundo parâmetro (contexto) para o método de log. Atualmente, os conjuntos de dados adicionais para o processador no método AbstractStep->runStage (passar o modo atual, o estágio e a etapa para o processador) e as classes de dados onde foi usado o método logger->debug (passar o nome da tabela de migração). Exemplo de adição de processadores ao logger:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Há a possibilidade de definir o nível de verbosidade. Por enquanto, há três níveis:

* `ERROR` (grava somente erros no log)
* `INFO` (somente informações importantes são gravadas no log, valor padrão)
* `DEBUG` (tudo está escrito)

O nível de log de verbosidade pode ser definido para cada manipulador separadamente, chamando `setLevel()` método . Se quiser definir o nível de verbosidade por meio do parâmetro de linha de comando, altere a opção &#39;verbose&#39; na inicialização do aplicativo.

Você pode formatar mensagens de log com o formatador de monólogo. Para que a funcionalidade do formatador funcione, é necessário especificar o manipulador de log usando o `setFormatter()` método . Atualmente, temos uma classe de formatador (`MessageFormatter`) que define determinado formato (depende do nível de verbosidade) durante o manuseio de mensagens (por meio da variável `format()` método executado do manipulador).

A manipulação do logger (adição de manipuladores e processadores) e do processamento no modo detalhado é executada na `process()` do método `Migration\Logger\Manager` classe . O método é chamado quando o aplicativo é iniciado.

## Testes automáticos

Há três tipos de testes na [!DNL Data Migration Tool]:

* Estático
* Unidade
* Integração

Eles estão localizados no `tests/` , que é o mesmo que o tipo de teste (os testes de unidade estão localizados na seção `tests/unit` diretório). Para iniciar o teste, você deve ter a unidade phpunit instalada. Altere o diretório atual para o diretório de teste e inicie o phpunit. Por exemplo:

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
