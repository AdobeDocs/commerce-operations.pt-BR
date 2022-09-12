---
title: Configure o [!DNL Data Migration Tool]
description: Saiba mais sobre os dois métodos para configurar o [!DNL Data Migration Tool] para transferir dados entre o Magento 1 e o Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# Configure o [!DNL Data Migration Tool]

Depois de instalar o [!DNL Data Migration Tool], o diretório a seguir contém arquivos de mapeamento e configuração:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Configuração e scripts para migração do Magento Open Source 1 para o Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Configuração e scripts para migração do Magento Open Source 1 para o Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Configuração e scripts para migração do Adobe Commerce 1 para o Adobe Commerce 2

Os diretórios anteriores contêm subdiretórios para cada versão suportada.

## Configuração da migração

Há duas maneiras de configurar o [!DNL Data Migration Tool]:

* Configure o [!DNL Data Migration Tool] em um módulo separado (recomendado)
* Altere o [!DNL Data Migration Tool] na configuração do `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` diretório.

Para usar o controle de origem para gerenciar a configuração de migração e usá-la para implantação, você deve criar um módulo separado.
Se você planeja executar a variável [!DNL Data Migration Tool] somente localmente, você pode editar arquivos no `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` diretório diretamente.

### Configurar migração em um módulo separado

Antes de migrar qualquer dado, é necessário criar um módulo de Magento 2.

1. Crie um módulo de Magento 2.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. Copie o `config.xml.dist` arquivo de configuração do diretório apropriado do [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) na `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` arquivo.

   Por exemplo, se você migrar `Magento 1.9.3.6 Community Edition` para `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. No `config.xml` , você deve definir os detalhes de acesso aos bancos de dados M1 e M2 e à chave de criptografia.

1. Se o armazenamento M1 tiver alterações personalizadas, você deverá mapear o restante dos arquivos de configuração para as personalizações de armazenamento do Magento 1. Consulte [Trabalhar com arquivos de configuração e mapeamento](#migration-config).

### Configure a migração em `vendor` pasta

Antes de migrar qualquer dado, é necessário criar um `config.xml` arquivo de configuração da amostra fornecida.

Para configurar o [!DNL Data Migration Tool] para migração:

1. Faça logon no servidor de aplicativos como, ou alterne para, o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

1. Altere para o seguinte diretório:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Digite o seguinte comando para criar um `config.xml` da amostra fornecida:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Abrir `config.xml` em um editor de texto.

1. No mínimo, o arquivo config.xml deve conter detalhes de acesso aos bancos de dados M1 e M2 e chaves de criptografia.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   O &lt;crypt_key> deve conter um valor. Você pode encontrá-lo dentro do `<key>` , que está localizado no arquivo app/etc/local.xml na instância do Magento 1.

   Parâmetros opcionais:

   * Senha do usuário do banco de dados: `password=<password>`
   * Porta personalizada do banco de dados: `port=<port>`
   * Prefixo da tabela: `<source_prefix>`, `<dest_prefix>`

   Por exemplo, se o nome de usuário do proprietário do banco de dados for `root` com senha `pass` e usar o prefixo `magento1` no banco de dados do Magento 1, use o seguinte em `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

Quando terminar, salve as alterações em `config.xml` e saia do editor de texto.

### Conecte-se usando o protocolo TLS

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

## Trabalhar com arquivos de configuração e mapeamento

O [!DNL Data Migration Tool] uses *mapear arquivos* para permitir a execução de mapeamento de banco de dados personalizado entre os bancos de dados Magento 1 e Magento 2, incluindo:

* Alteração de nomes de tabela

* Alteração de nomes de campos

* Ignorando tabelas ou campos

* Adaptar a transferência de dados de um campo para o formato Magento 2

Os arquivos de mapeamento para versões do Magento compatíveis estão localizados em subdiretórios de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

Para usar os arquivos de mapeamento:

1. Copiar de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` para `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` e remova o `.dist` [extensão](https://glossary.magento.com/extension).

1. Atualize o caminho para o arquivo recém-copiado no `<options>` nó de `config.xml`. O caminho atualizado deve ser um dos seguintes:

   1. Caminho absoluto do arquivo, e. g. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. caminho de arquivo relativo do módulo magento/data-migration-tool: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Caminho do arquivo relativo à raiz do Magento: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

O `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` e `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` os diretórios contêm os seguintes arquivos de configuração:

Mesmo que você esteja trabalhando com o `map.xml.dist` Na maioria das vezes, a tabela a seguir discute cada mapeamento e outros arquivos.

| Nome do arquivo de mapeamento | Descrição |
| --- | --- |
| `class-map.xml.dist` | Dicionário de mapeamentos de classe entre Magento 1 e Magento 2 |
| `config.xml.dist` | Arquivo de configuração principal que especifica as configurações do banco de dados Magento 1 e Magento 2, a configuração da etapa e os links para os arquivos de mapeamento |
| *Somente Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Lista de tabelas usadas na etapa de atributos personalizados do cliente. |
| *Somente Adobe Commerce*. `customer-attr-map.xml.dist` | Mapeie o arquivo usado na etapa Atributos personalizados do cliente . |
| `deltalog.xml.dist` | Contém a lista de tabelas necessárias para a configuração de rotinas do banco de dados. |
| `eav-attribute-groups.xml.dist` | Contém a lista de atributos usados na Etapa de manutenção. |
| `eav-document-groups.xml.dist` | Contém a lista de tabelas usadas na etapa Salvar. |
| `log-document-groups.xml.dist` | Contém a lista de tabelas usadas na Etapa de Log. |
| `map-eav.xml.dist` | Mapeie o arquivo usado na Etapa EAV. |
| `map-log.xml.dist` | Arquivo de mapeamento de log. |
| *Somente Adobe Commerce*. `map-sales.xml.dist` | Mapeie o arquivo usado na Etapa SalesOrder. |
| `map.xml.dist` | Arquivo de mapeamento necessário para a etapa do mapa. |
| `settings.xml.dist` | Configuração do arquivo de configuração de migração que especifica as regras necessárias para migrar a variável `core_config_data` tabela. |
| `customer-attribute-groups.xml.dist` | Contém a lista de atributos usados na Etapa de atributos do cliente. |
| `customer-document-groups.xml.dist` | Contém a lista de tabelas usadas na Etapa de atributos do cliente. |
| `map-customer.xml.dist` | Mapeie o arquivo usado na etapa Atributos do cliente . |
| `order-grids-document-groups.xml.dist` | Contém a lista de tabelas usadas na Etapa OrderGrids. |
| `map-document-groups.xml.dist` | Define quais campos são atualizados quando duplicações ocorrem na inserção de dados |
| `map-stores.xml.dist` | Mapeie o arquivo usado na Etapa Lojas. |
| `map-tier-price.xml.dist` | Mapeie o arquivo usado na Etapa de Preço de Camada. |
| *Somente Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Arquivo de mapa usado na etapa do VisualMerchandiser. |
| *Somente Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Contém a lista de atributos usados na Etapa do VisualMerchandiser. |
| *Somente Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Contém a lista de tabelas usadas na Etapa do VisualMerchandiser. |

Você pode se referir a [[!DNL Data Migration Tool] Especificação técnica](technical-specification.md) para obter mais detalhes.
