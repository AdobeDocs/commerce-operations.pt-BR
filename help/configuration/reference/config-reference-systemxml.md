---
title: referência system.xml
description: Saiba como o arquivo XML do sistema gerencia a configuração do aplicativo do Commerce.
contributor_name: David Lambauer
contributor_link: https://github.com/DavidLambauer
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '2671'
ht-degree: 0%

---


# referência system.xml

O `system.xml` permite gerenciar a configuração do sistema do Commerce. Use este tópico como referência geral para o `system.xml` arquivo. O `system.xml` O arquivo está localizado em `etc/adminhtml/system.xml` em uma determinada extensão do Commerce 2.

O trecho de código a seguir mostra o esqueleto nu do arquivo:

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Se quiser a validação instantânea *XSD em seu IDE, você pode executar `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Guias // Seções // Grupos // Campos

No `system.xml` , é possível definir quatro tipos diferentes de entidades, que estão relacionadas entre si. A seção a seguir descreve a relação entre guias, seções, grupos e campos. A captura de tela a seguir exibe a Configuração do sistema do Commerce 2 no back-end do Administrador.
Os quadrados vermelhos marcam os diferentes tipos definidos na variável `system.xml` arquivo:

![Captura de tela que exibe uma seção configurada em Admin.](../../assets/configuration/magento2-system-configuration.png)

Guias são usadas para dividir áreas de configuração diferentes semanticamente. Cada guia pode conter uma ou mais seções, que também podem ser mencionadas como submenus. Uma seção contém um ou mais grupos.
Cada grupo lista um ou mais campos. Você também pode usar um grupo para adicionar uma descrição geral para os seguintes campos. Como mencionado, cada grupo pode ter um ou mais campos. Os campos são a menor entidade no contexto de configuração do sistema.

## Guias

A `<tab>`-Marque referências a uma guia existente ou uma nova na configuração do sistema.

### Referência do atributo de guia

A `<tab>`-Tag pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Define o identificador usado que faz referência à seção. | `typeId` | obrigatório |
| `translate` | Define o campo que deve ser traduzível. Fornecer `label` para tornar o rótulo traduzível. | `string` | opcional |
| `type` | Define o tipo de entrada do elemento HTML renderizado — o padrão é `text`. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurram a seção para a parte inferior da página; números baixos empurram a seção para o topo. | `float` | opcional |
| `class` | Adiciona uma classe CSS definida ao elemento HTML da guia renderizada. | `string` | opcional |

### Referência do nó de guia

A `<tab>`-Tag pode ter o seguinte filho:

| Nó | Descrição | Tipo |
|---------|------------------------------------------------------|----------|
| `label` | Define o rótulo que é exibido na frente. | `string` |

### Exemplo: Criar uma guia

O trecho de código a seguir demonstra a criação de uma nova guia com dados de exemplo.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

O trecho acima cria uma nova guia com o identificador `A_UNIQUE_ID`. Como `translate`-attribute é definido e faz referência ao rótulo, a variável `label`-node é traduzível. Durante o processo de renderização, a classe CSS `a-custom-css-class-to-style-this-tab` será aplicado no elemento HTML criado para esta guia.
O `sortOrder`-attribute com o valor de `10` define a posição da guia na lista de todas as guias quando renderizada.

## Seções

A `<section>`-Marque referências a uma seção existente ou a uma nova na configuração do sistema.

### Referência do atributo da seção

A `<section>`-Tag pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define o identificador usado que faz referência à seção. | `typeId` | obrigatório |
| `translate` | Define o campo que deve ser traduzível. Fornecer `label` para tornar o rótulo traduzível. | `string` | opcional |
| `type` | Define o tipo de entrada do elemento HTML renderizado. O padrão é `text`. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurram a seção para a parte inferior da página; números baixos empurrarão a seção para o topo. | `float` | opcional |
| `showInDefault` | Define se a seção é mostrada no escopo de configuração padrão. Especificar `1` para mostrar a seção e `0` para ocultar a seção . | `int` | opcional |
| `showInStore` | Define se a seção é exibida no nível da loja. Especificar `1` para mostrar a seção e `0` para ocultar a seção . | `int` | opcional |
| `showInWebsite` | Define se a seção é mostrada no nível do site. Especificar `1` para mostrar a seção e `0` para ocultar a seção . | `int` | opcional |
| `canRestore` | Define se a seção pode ser restaurada para o padrão. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Ao fornecer um identificador de outra seção, o conteúdo desse nó estenderá a seção referenciada. | `string` | opcional |

### Referência do nó da seção

A `<section>`-Tag pode ter os seguintes filhos:

| Nó | Descrição | Tipo |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Define o rótulo que é exibido na frente. | `string` |
| `class` | Adiciona uma classe CSS definida ao elemento HTML da seção renderizada. | `string` |
| `tab` | Faz referência à guia associada. Espera a ID da guia . | `typeTabId` |
| `header_css` | Nem usado nem avaliado no momento da escrita. | `string` |
| `resource` | Faz referência a um recurso da ACL para fornecer configurações de permissão para esta seção. | `typeAclResourceId` |
| `group` | Defina um ou mais subgrupos. | `typeGroup` |
| `frontend_model` | Especifica um modelo de frontend diferente para alterar a renderização e modificar a saída. | `typeModel` |
| `include` | Usado para incluir `system_include.xsd` arquivos compatíveis. Geralmente usado para estruturar grandes `system.xml` arquivos. | `includeType` |

### Exemplo: Criar uma seção e atribuí-la a uma guia

O trecho de código a seguir demonstra o uso básico da criação de uma nova seção.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

A seção descrita acima define a ID `A_UNIQUE_SECTION_ID`, é visível na visualização de configuração padrão e em um contexto de loja. O `label`-node é traduzível. A seção está associada à guia com a ID `A_UNIQUE_ID`. A seção só pode ser acessada por usuários que tenham as permissões definidas na ACL `VENDOR_MODULE::path_to_the_acl_resource`.

## Grupos

O `<group>`-Tag é usada para agrupar campos.

### Referência de atributo do grupo

A `<group>`-Tag pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define o identificador usado que faz referência ao grupo. | `typeId` | obrigatório |
| `translate` | Define os campos que devem ser traduzíveis. Fornecer `label` para tornar o rótulo traduzível. Vários campos devem ser separados por um espaço. | `string` | opcional |
| `type` | Define o tipo de entrada do elemento HTML renderizado. O padrão é `text`. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurram a seção para a parte inferior da página; números baixos empurrarão a seção para o topo. | `float` | opcional |
| `showInDefault` | Define se o grupo é mostrado no escopo de configuração padrão. Especificar `1` para mostrar o grupo e `0` para ocultar o grupo. | `int` | opcional |
| `showInStore` | Define se o grupo é mostrado no nível da loja. Especificar `1` para mostrar o grupo e `0` para ocultar o grupo. | `int` | opcional |
| `showInWebsite` | Define se o grupo é mostrado no nível do site. Especificar `1` para mostrar o grupo e `0` para ocultar o grupo. | `int` | opcional |
| `canRestore` | Define se o grupo pode ser restaurado para o padrão. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Ao fornecer um identificador de outro grupo, o conteúdo desse nó estenderá a seção referenciada. | `string` | opcional |

### Referência do nó do grupo

A `<group>`-Tag pode ter os seguintes filhos:

| Nó | Descrição | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Define o rótulo que é exibido na frente. | `string` |
| `fieldset_css` | Adiciona uma ou mais classes CSS a um conjunto de campos de grupo. | `string` |
| `frontend_model` | Especifica um modelo de frontend diferente para alterar a renderização e modificar a saída. | `typeModel` |
| `clone_model` | Especifica um determinado modelo para clonar campos. | `typeModel` |
| `clone_fields` | Clonagem de campos ativada ou desativada. | `int` |
| `help_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `more_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `demo_link` | Não extensível. Veja abaixo. | `typeUrl` |
| `comment` | Adiciona um comentário abaixo do rótulo do grupo. Ao usar `<![CDATA[//]]>` HTML pode ser aplicado. | `string` |
| `hide_in_single_store_mode` | Se o grupo deve estar visível no modo de loja única. `1` oculta o grupo; `0` mostra o grupo. | `int` |
| `field` | Defina um ou mais campos que devem estar disponíveis nesse grupo. | `field` |
| `group` | Defina um ou mais subgrupos. | `unbounded` |
| `depends` | Pode ser usado para declarar dependências em outros campos. É usado para mostrar campos/grupos específicos somente quando um determinado campo tem um valor de `1`. Esse nó espera uma `section/group/field`-string. | `depends` |
| `attribute` | Atributos personalizados podem ser usados por modelos de front-end. Geralmente, é usado para tornar um determinado modelo de primeiro plano mais dinâmico. | `attribute` |
| `include` | Usado para incluir `system_include.xsd` arquivos compatíveis. Geralmente usado para estruturar grandes `system.xml` arquivos. | `includeType` |

>[!WARNING]
>
>Os nós `more_url`, `demo_url` e `help_url` são definidos por um modelo de frontend PayPal que é usado apenas uma vez. Esses nós não são reutilizáveis.

### Exemplo: Criar um grupo para uma determinada seção

O trecho de código a seguir demonstra o uso básico da criação de um novo grupo.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

O grupo descrito acima define a ID `A_UNIQUE_GROUP_ID`, é visível na visualização de configuração padrão e em um contexto de loja. Ambos, o `label` e `comment` são marcadas como traduzíveis.

## Campos

O `<field>`-Tag é usada dentro de `<group>`-Tags para definir valores de configuração específicos.

### Referência do atributo de campo

A `<field>`-Tag pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define o identificador usado que faz referência ao campo. | `typeId` | obrigatório |
| `translate` | Define os campos que devem ser traduzíveis. Fornecer `label` para tornar o rótulo traduzível. Vários campos devem ser separados por um espaço. | `string` | opcional |
| `type` | Define o tipo de entrada do elemento HTML renderizado. O padrão é `text`. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurram a seção para a parte inferior da página; números baixos empurram a seção para o topo. | `float` | opcional |
| `showInDefault` | Define se o campo é exibido no escopo de configuração padrão. Especificar `1` para mostrar o campo e `0` para ocultar o campo. | `int` | opcional |
| `showInStore` | Define se o campo é exibido no nível da loja. Especificar `1` para mostrar o campo e `0` para ocultar o campo. | `int` | opcional |
| `showInWebsite` | Define se o campo é exibido no nível do site. Especificar `1` para mostrar o campo e `0` para ocultar o campo. | `int` | opcional |
| `canRestore` | Define se o campo pode ser restaurado para o padrão. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Ao fornecer um identificador de outro campo, o conteúdo desse nó estenderá a seção referenciada. | `string` | opcional |

### Referência do tipo de campo

A `<field>`-Tag pode ter os seguintes valores para a variável `type=""` atributo:

| Tipo | Descrição |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Campo de texto padrão de linha única |
| `textarea` | Bloco de texto |
| `select` | Lista suspensa Normal, pode precisar de um `source_model`. Também usado para `Yes/No` seleções. Consulte `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` para obter um exemplo. |
| `multiselect` | Like `select` mas várias opções são válidas. |
| `button` | Um botão que dispara um evento imediato. Requer um modelo front-end personalizado para definir o texto do botão e a ação. Consulte `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` para obter um exemplo. |
| `obscure` | Campo de texto com o valor criptografado e exibido como `****`. Alterar o tipo usando &quot;Elemento do Inspect&quot; no navegador não revela o valor. |
| `password` | Like `obscure` exceto que o valor oculto não está criptografado e alterar forçosamente o tipo usando &quot;Elemento Inspect&quot; no navegador revela o valor. |
| `file` | Permite que um arquivo seja carregado para processamento. |
| `label` | Exibe um rótulo em vez de um campo editável. Use esse tipo quando um campo puder ser editado somente em escopos específicos, por exemplo, nível de Exibição de loja . |
| `time` | Controle para definir o tempo usando três menus suspensos - Hora, minuto e segundo. |
| `allowspecific` | Uma lista multisseleção de países específicos. Requer um `source_model` como `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Permite que uma imagem seja carregada. |
| `note` | Permite que uma nota informativa seja adicionada à página. Esse tipo requer um `frontend_model` para renderizar a nota. |

Também é possível criar um tipo de campo personalizado. Isso geralmente é feito quando um botão especial, com uma ação, é necessário. Para fazer isso, são necessários dois elementos principais:

- Criação de um bloco no `adminhtml` area
- Definir a `type=""` para o caminho para este bloco

O próprio bloco requer, no mínimo, um `__construct` e um `getElementHtml()` método . O [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) é um exemplo simples de um tipo personalizado.

Por exemplo, no módulo OfflineShipping, o botão Exportar é definido em `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` e a definição do campo tem a seguinte aparência:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Referência do nó do campo

A `<field>`-Tag pode ter os seguintes filhos:

| Nó | Descrição | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Define o rótulo que é exibido na frente. | `string` |
| `comment` | Adiciona um comentário abaixo do rótulo do campo. Ao usar `<![CDATA[//]]>` HTML pode ser aplicado. | `string` |
| `tooltip` | Outro possível elemento de primeiro plano que pode ser usado para descrever o significado desse campo. Exibido como um pequeno ícone ao lado do campo. | `string` |
| `hint` | Exibe informações adicionais. Disponível apenas com `frontend_model`. | `string` |
| `frontend_class` | Adiciona uma classe CSS definida ao elemento HTML da seção renderizada. | `string` |
| `frontend_model` | Especifica um modelo de frontend diferente para alterar a renderização e modificar a saída. | `typeModel` |
| `backend_model` | Especifica um modelo de back-end diferente para modificar os valores configurados. | `typeModel` |
| `source_model` | Especifica um modelo de origem diferente que fornece um conjunto específico de valores. | `typeModel` |
| `config_path` | Pode ser usado para substituir o caminho de configuração genérico de um campo. | `typeConfigPath` |
| `validate` | Defina regras de validação diferentes (separadas por espaço). A lista de referência completa das regras de validação disponíveis está listada abaixo. | `string` |
| `can_be_empty` | Usado quando `type` é `multiselect` para especificar que um campo pode estar vazio. | `int` |
| `if_module_enabled` | Usado para exibir um campo somente quando um determinado módulo está habilitado. | `typeModule` |
| `base_url` | Usado em combinação com `upload_dir` para uploads de arquivo. | `typeUrl` |
| `upload_dir` | Especifique um diretório de destino para uploads. Esse nó tem atributos e nós adicionais. Procure-os antes de usar isto. | `typeUploadDir` |
| `button_url` | Exibe um botão se `button_url` e `button_label` são especificadas. Normalmente usado em combinação com um modelo de frontend personalizado. | `typeUrl` |
| `button_label` | Exibe um botão se `button_label` e `button_url` são especificadas. Normalmente usado em combinação com um modelo de frontend personalizado. | `string` |
| `more_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `demo_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `hide_in_single_store_mode` | Se o grupo deve estar visível no modo de loja única. `1` oculta o grupo; `0` mostra o grupo. | `int` |
| `source_service` | Serviço usado para preencher as opções de seleção. | `complexType` |
| `options` | Não usado. Potencialmente obsoleto. | `complexType` |
| `depends` | Pode ser usado para declarar dependências para outros campos. É usado para mostrar somente campos/grupos específicos quando um determinado campo tem um valor de `1`. Esse nó espera uma `section/group/field`-string. | `complexType` |
| `attribute` | Atributos personalizados podem ser usados por modelos de front-end. Geralmente, é usado para tornar um determinado modelo de primeiro plano mais dinâmico. | `complexType` |
| `requires` | Não extensível. Veja abaixo. | `complexType` |

>[!WARNING]
>
>Os nós `more_url`, `demo_url`, `requires` e `options` são definidos por um modelo de pagamento de base diferente e são utilizados apenas uma vez. Esses nós não são reutilizáveis.

### Exemplo: Criar dois campos em um determinado grupo

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

O exemplo acima cria dois campos, visíveis/configuráveis no padrão e na visualização da loja. Ambos os campos têm um comentário e uma dica de ferramenta para descrever sua finalidade para o usuário. O `label`-node é traduzível.
O campo com o identificador `ANOTHER_UNIQUE_FIELD_ID` é visível quando o módulo especificado na variável `if_module_enabled` é ativado globalmente. O campo também valida seu valor em relação às regras `required-entry` e `no-whitespace`.
O campo com o identificador `A_UNIQUE_FIELD_ID` define um modelo de origem diferente que fornece esses valores `Yes` e `No`.

### Modelos de fonte comum

Os seguintes modelos de origem são fornecidos pelo Commerce 2 Core. Em geral, há muito mais modelos de origem; a lista a seguir descreve as mais comuns. Esteja ciente de que esses modelos de origem precisam do atributo field `type` a ser definido como `select` para funcionar adequadamente.

| Modelo de origem | Descrição |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Fornece os valores `Yes`, `No` e `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Fornece os valores `Enable`, `Disable`. Salva os valores como `0` e `1` no banco de dados. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Fornece os valores `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` e `24 Hours`. Os valores são salvos como números inteiros. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Fornece os valores para o formato de hora (12 h/24 h). |
| `Magento\Cron\Model\Config\Source\Frequency` | Fornece os valores `Daily`, `Weekly` e `Monthly`. Os valores são salvos no banco de dados como `D`, `W` e `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Fornece os valores para um código de 2 letras de um determinado idioma no formato ISO 639-1 (por exemplo, en). |
| `Magento\Config\Model\Config\Source\Locale` | Fornece os valores semelhantes ao acima, mas mantém um código de localidade (por exemplo, en_US). |

### Validação de campo

Um campo pode ter uma ou mais classes validator atribuídas para garantir que a entrada do usuário atenda aos requisitos da extensão. As regras de validação podem ser aplicadas com a variável `<validate>`-Tag.
O exemplo a seguir valida um campo e adiciona várias regras de validação diferentes.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

As seguintes regras de validação estão disponíveis:

| Regra | Descrição |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Permite somente letras, números, espaços ou sublinhados. |
| `integer` | Permite um número não decimal positivo ou negativo. |
| `ipv4` | Permite um endereço IP v4 válido. |
| `ipv6` | Permite um endereço IP v6 válido. |
| `letters-only` | Permite somente letras. Por exemplo, `abcABC`. |
| `letters-with-basic-punc` | Permite somente letras ou pontuação.<br>Deve passar a seguinte expressão: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Permite um número de telefone celular (UK). |
| `no-marginal-whitespace` | Não permite espaços em branco no início ou no fim do valor. |
| `no-whitespace` | Não permite espaços em branco. |
| `phoneUK` | Permite um número de telefone (UK). |
| `phoneUS` | Permite um número de telefone (US). |
| `required-entry` | Não permite um valor vazio (validação equivalente como `validate-no-empty`).<br>Mensagem de falha de validação: &quot;Este é um campo obrigatório.&quot; |
| `time` | Permite um horário válido em formato de 24 horas, entre 00:00 e 23:59. Por exemplo `15`, `15:05` ou `15:05:48`. |
| `time12h` | Permite uma hora válida no formato de 12 horas, entre 12:00 e 11:59:17:00 Por exemplo `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Permite 7 ou mais caracteres, usando numéricos e alfabéticos. |
| `validate-alphanum-with-spaces` | Permite o uso de letras (a-z ou A-Z), números (0-9) ou espaços somente. |
| `validate-clean-url` | Permite um URL válido. Por exemplo, `https://www.example.com` ou `www.example.com`. |
| `validate-currency-dollar` | Permite um valor válido (dólar). Por exemplo, US$ 100,00. |
| `validate-data` | Permite o uso de letras (a-z ou A-Z), números (0-9) ou sublinhados (\_) somente.<br>O primeiro caractere deve ser uma letra.<br>(Deve corresponder à expressão: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Mensagem de falha de validação: &quot;Use apenas letras (a-z ou A-Z), números (0-9) ou sublinhado (\_) neste campo e o primeiro caractere deve ser uma letra.&quot; |
| `validate-date-au` | Implica o seguinte formato de data: dd/mm/aaaa. Por exemplo, 17/03/2006 para o dia 17 de março de 2006. |
| `validate-email` | Permite um endereço de email válido. Por exemplo, johndoe@domain.com. |
| `validate-emailSender` | Permite um endereço de email válido. Por exemplo, johndoe@domain.com. |
| `validate-fax` | Permite um número de fax válido. Por exemplo, 123-456-7890. |
| `validate-no-empty` | Não permite um valor vazio (validação equivalente como `requried-entry`).<br>Mensagem de falha de validação: &quot;Valor vazio.&quot; |
| `validate-no-html-tags` | Não permite o uso de tags HTML. |
| `validate-password` | Permite 6 ou mais caracteres. Espaços à esquerda e à direita serão ignorados. |
| `validate-phoneLax` | Permite um número de telefone válido. Por exemplo, (123) 456-7890 ou 123-456-7890. |
| `validate-phoneStrict` | Permite um número de telefone válido. Por exemplo, (123) 456-7890 ou 123-456-7890. |
| `validate-select` | Implica que a opção de seleção escolhida não tenha uma `null` valor, valor da string de `none` ou comprimento da string de 0. |
| `validate-ssn` | Permite um número de segurança social (EUA) válido. Por exemplo, 123-45-6789. |
| `validate-street` | Permite o uso de letras (a-z ou A-Z), números (0-9), espaços e somente &quot;#&quot;. |
| `validate-url` | Permite um URL válido. O protocolo é necessário (http://, https:// ou ftp://). |
| `validate-xml-identifier` | Permite um identificador XML válido. Por exemplo, algo_1, bloco5, id-4. |
| `validate-zip-us` | Permite um CEP válido (US). Por exemplo, 90602 ou 90602-1234. |
| `vinUS` | Permite o valor do número de identificação (VIN) do veículo (EUA). |

### Valores padrão

Os valores padrão para campos podem ser definidos no `etc/config.xml` , especificando o valor padrão na variável `section/group/field_ID` nó .

#### Exemplo: Definir o valor padrão para `ANOTHER_UNIQUE_FIELD_ID` (Escopo padrão)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Exemplo: Definir o valor padrão para `ANOTHER_UNIQUE_FIELD_ID` (Escopo do site)

Usar o `websites` , especifique o valor padrão de um site específico.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
