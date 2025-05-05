---
title: referência system.xml
description: Saiba como o arquivo XML do sistema gerencia a configuração do aplicativo do Commerce.
feature: Configuration, System
badge: label="Contribuição de David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2708'
ht-degree: 0%

---

# referência system.xml

O arquivo `system.xml` permite gerenciar a configuração do sistema Commerce. Use este tópico como uma referência geral para o arquivo `system.xml`. O arquivo `system.xml` está localizado em `etc/adminhtml/system.xml` em uma determinada extensão do Commerce 2.

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
>Se quiser validação *XSD instantânea no IDE, você pode executar `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Guias // Seções // Grupos // Campos

No arquivo `system.xml`, é possível definir quatro tipos diferentes de entidades, que estão relacionadas umas às outras. A seção a seguir descreve a relação entre guias, seções, grupos e campos. A captura de tela a seguir exibe a Configuração do sistema Commerce 2 no back-end do administrador.
Os quadrados vermelhos marcam os diferentes tipos definidos no arquivo `system.xml`:

![Captura de tela exibindo uma seção configurada no Administrador.](../../assets/configuration/magento2-system-configuration.png)

As guias são usadas para dividir semanticamente diferentes áreas de configuração. Cada guia pode conter uma ou mais seções, que também podem ser referenciadas como submenus. Uma seção contém um ou mais grupos.
Cada grupo lista um ou mais campos. Você também pode usar um grupo para adicionar uma descrição geral para os campos a seguir. Como mencionado, cada grupo pode ter um ou mais campos. Os campos são a menor entidade
no contexto de configuração do sistema.

## Guias

Uma tag `<tab>` faz referência a uma guia existente ou nova na configuração do sistema.

### Referência de atributo de guia

Uma tag `<tab>` pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Define o identificador usado referenciando a seção. | `typeId` | obrigatório |
| `translate` | Define o campo que deve ser traduzível. Forneça `label` para tornar o rótulo traduzível. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurram a seção para a parte inferior da página; números baixos empurram a seção para a parte superior. | `float` | opcional |
| `class` | Adiciona uma classe CSS definida ao elemento de HTML da guia renderizada. | `string` | opcional |

### Referência do nó de guia

Uma tag `<tab>` pode ter o seguinte filho:

| Nó | Descrição | Tipo |
|---------|------------------------------------------------------|----------|
| `label` | Define o rótulo exibido no front-end. | `string` |

### Exemplo: criar uma guia

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

O trecho acima cria uma nova guia com o identificador `A_UNIQUE_ID`. Como o atributo `translate` é definido e faz referência ao rótulo, o nó `label` é traduzível. Durante o processo de renderização, a classe CSS `a-custom-css-class-to-style-this-tab` será aplicada ao elemento HTML criado para esta guia.
O atributo `sortOrder` com o valor de `10` define a posição da guia na lista de todas as guias quando renderizada.

## Seções

Uma tag `<section>` faz referência a uma seção nova ou existente na configuração do sistema.

### Referência de atributo de seção

Uma tag `<section>` pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define o identificador usado referenciando a seção. | `typeId` | obrigatório |
| `translate` | Define o campo que deve ser traduzível. Forneça `label` para tornar o rótulo traduzível. | `string` | opcional |
| `type` | Define o tipo de entrada do elemento de HTML renderizado. O padrão é `text`. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurrarão a seção para a parte inferior da página; números baixos empurrarão a seção para o topo. | `float` | opcional |
| `showInDefault` | Define se a seção é mostrada no escopo de configuração padrão. Especifique `1` para mostrar a seção e `0` para ocultá-la. | `int` | opcional |
| `showInStore` | Define se a seção é mostrada no nível da loja. Especifique `1` para mostrar a seção e `0` para ocultá-la. | `int` | opcional |
| `showInWebsite` | Define se a seção é exibida no nível do site. Especifique `1` para mostrar a seção e `0` para ocultá-la. | `int` | opcional |
| `canRestore` | Define se a seção pode ser restaurada para o padrão. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Ao fornecer um identificador de outra seção, o conteúdo desse nó estenderá a seção à qual você fez referência. | `string` | opcional |

### Referência do nó da seção

Uma tag `<section>` pode ter os seguintes filhos:

| Nó | Descrição | Tipo |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Define o rótulo exibido no front-end. | `string` |
| `class` | Adiciona uma classe CSS definida ao elemento de HTML da seção renderizada. | `string` |
| `tab` | Faz referência à guia associada. Espera a ID da guia. | `typeTabId` |
| `header_css` | Não usado nem avaliado no momento da escrita deste documento. | `string` |
| `resource` | Faz referência a um recurso de ACL para fornecer configurações de permissão para esta seção. | `typeAclResourceId` |
| `group` | Defina um ou mais subgrupos. | `typeGroup` |
| `frontend_model` | Especifica um modelo de front-end diferente para alterar a renderização e modificar a saída. | `typeModel` |
| `include` | Usado para incluir `system_include.xsd` arquivos adicionais compatíveis. Normalmente usado para estruturar arquivos `system.xml` grandes. | `includeType` |

### Exemplo: criar uma seção e atribuí-la a uma guia

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

A seção descrita acima define a ID `A_UNIQUE_SECTION_ID`, que é visível na exibição de configuração padrão e em um contexto de armazenamento. O nó `label` pode ser traduzido. A seção está associada à guia com a ID `A_UNIQUE_ID`. A seção só pode ser acessada por usuários que tenham as permissões definidas na ACL `VENDOR_MODULE::path_to_the_acl_resource`.

## Grupos

A `<group>`-Tag é usada para agrupar campos.

### Referência de atributo de grupo

Uma tag `<group>` pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define o identificador usado que faz referência ao grupo. | `typeId` | obrigatório |
| `translate` | Define os campos que devem ser traduzíveis. Forneça `label` para tornar o rótulo traduzível. Vários campos devem ser separados por um espaço. | `string` | opcional |
| `type` | Define o tipo de entrada do elemento de HTML renderizado. O padrão é `text`. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurrarão a seção para a parte inferior da página; números baixos empurrarão a seção para o topo. | `float` | opcional |
| `showInDefault` | Define se o grupo é mostrado no escopo de configuração padrão. Especifique `1` para mostrar o grupo e `0` para ocultar o grupo. | `int` | opcional |
| `showInStore` | Define se o grupo é mostrado no nível do armazenamento. Especifique `1` para mostrar o grupo e `0` para ocultar o grupo. | `int` | opcional |
| `showInWebsite` | Define se o grupo é exibido no nível do site. Especifique `1` para mostrar o grupo e `0` para ocultar o grupo. | `int` | opcional |
| `canRestore` | Define se o grupo pode ser restaurado para o padrão. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Ao fornecer um identificador de outro grupo, o conteúdo desse nó estenderá a seção referenciada. | `string` | opcional |

### Referência do nó do grupo

Uma tag `<group>` pode ter os seguintes filhos:

| Nó | Descrição | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Define o rótulo exibido no front-end. | `string` |
| `fieldset_css` | Adiciona uma ou mais classes CSS a um conjunto de campos de grupo. | `string` |
| `frontend_model` | Especifica um modelo de front-end diferente para alterar a renderização e modificar a saída. | `typeModel` |
| `clone_model` | Especifica um determinado modelo para clonar campos. | `typeModel` |
| `clone_fields` | Clonagem de campos ativada ou desativada. | `int` |
| `help_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `more_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `demo_link` | Não extensível. Veja abaixo. | `typeUrl` |
| `comment` | Adiciona um comentário abaixo do rótulo do grupo. É possível aplicar o HTML `<![CDATA[//]]>`. | `string` |
| `hide_in_single_store_mode` | Se o grupo deve estar visível no modo de armazenamento único. `1` oculta o grupo; `0` mostra o grupo. | `int` |
| `field` | Defina um ou mais campos que devem estar disponíveis neste grupo. | `field` |
| `group` | Defina um ou mais subgrupos. | `unbounded` |
| `depends` | Pode ser usado para declarar dependências em outros campos. É usado para mostrar campos/grupos específicos apenas quando um determinado campo tem um valor de `1`. Este nó espera uma cadeia de caracteres `section/group/field`. | `depends` |
| `attribute` | Atributos personalizados podem ser usados por modelos de front-end. Normalmente usado para tornar um determinado modelo de front-end mais dinâmico. | `attribute` |
| `include` | Usado para incluir `system_include.xsd` arquivos adicionais compatíveis. Normalmente usado para estruturar arquivos `system.xml` grandes. | `includeType` |

>[!WARNING]
>
>Os nós `more_url`, `demo_url` e `help_url` são definidos por um modelo de front-end do PayPal que é usado apenas uma vez. Esses nós não são reutilizáveis.

### Exemplo: criar um grupo para uma determinada seção

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

O grupo descrito acima define a ID `A_UNIQUE_GROUP_ID`, que é visível na exibição de configuração padrão e em um contexto de armazenamento. Ambos, o `label` e o `comment` são marcados como traduzíveis.

## Campos

A `<field>`-Tag é usada dentro de `<group>`-Tags para definir valores de configuração específicos.

### Referência do atributo de campo

Uma tag `<field>` pode ter os seguintes atributos:

| Atributo | Descrição | Tipo | Obrigatório |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define o identificador usado referenciando o campo. | `typeId` | obrigatório |
| `translate` | Define os campos que devem ser traduzíveis. Forneça `label` para tornar o rótulo traduzível. Vários campos devem ser separados por um espaço. | `string` | opcional |
| `type` | Define o tipo de entrada do elemento de HTML renderizado. O padrão é `text`. | `string` | opcional |
| `sortOrder` | Define a ordem de classificação da seção. Números altos empurram a seção para a parte inferior da página; números baixos empurram a seção para a parte superior. | `float` | opcional |
| `showInDefault` | Define se o campo é mostrado no escopo de configuração padrão. Especifique `1` para mostrar o campo e `0` para ocultar o campo. | `int` | opcional |
| `showInStore` | Define se o campo é mostrado no nível do armazenamento. Especifique `1` para mostrar o campo e `0` para ocultar o campo. | `int` | opcional |
| `showInWebsite` | Define se o campo é exibido no nível do site. Especifique `1` para mostrar o campo e `0` para ocultar o campo. | `int` | opcional |
| `canRestore` | Define se o campo pode ser restaurado para o padrão. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Ao fornecer um identificador de outro campo, o conteúdo desse nó estenderá a seção referenciada. | `string` | opcional |

### Referência do tipo de campo

Uma tag `<field>` pode ter os seguintes valores para o atributo `type=""`:

| Tipo | Descrição |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Campo de texto padrão de linha única |
| `textarea` | Bloco de texto |
| `select` | Lista suspensa normal, pode precisar de um `source_model` personalizado. Também usado para `Yes/No` seleções. Veja um exemplo em `Magento\Search\Model\Adminhtml\System\Config\Source\Engine`. |
| `multiselect` | Como `select`, mas várias opções são válidas. |
| `button` | Um botão que aciona um evento imediato. Requer um modelo de front-end personalizado para definir o texto do botão e a ação. Veja um exemplo em `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean`. |
| `obscure` | Um campo de texto com o valor criptografado e exibido como `**&#x200B;**`. A alteração do tipo usando &quot;Elemento Inspect&quot; no navegador não revela o valor. |
| `password` | Como `obscure`, exceto que o valor oculto não é criptografado, e a alteração forçada do tipo usando &quot;Elemento Inspect&quot; no navegador revela o valor. |
| `file` | Permite que um arquivo seja carregado para processamento. |
| `label` | Exibe um rótulo em vez de um campo editável. Use esse tipo quando um campo for editável somente em escopos específicos, por exemplo, somente nível de Exibição de Loja. |
| `time` | Controle para definir a hora usando três menus suspensos: hora, minuto e segundo. |
| `allowspecific` | Uma lista multisseleção de países específicos. Requer um `source_model` como `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Permite que uma imagem seja carregada. |
| `note` | Permite que uma nota informativa seja adicionada à página. Este tipo requer um `frontend_model` para renderizar a anotação. |

Também é possível criar um tipo de campo personalizado. Isso geralmente é feito quando um botão especial, com uma ação, é necessário. Para fazer isso, são necessários dois elementos principais:

- Criando um bloco na área `adminhtml`
- Definindo o `type=""` para o caminho para este bloco

O próprio bloco requer, no mínimo, um método `__construct` e um método `getElementHtml()`. O [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) é um exemplo simples de um tipo personalizado.

Por exemplo, no módulo OfflineShipping, o botão Exportar é definido em `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` e a definição do campo é semelhante a:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Referência do nó de campo

Uma tag `<field>` pode ter os seguintes filhos:

| Nó | Descrição | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Define o rótulo exibido no front-end. | `string` |
| `comment` | Adiciona um comentário abaixo do rótulo do campo. É possível aplicar o HTML `<![CDATA[//]]>`. | `string` |
| `tooltip` | Outro elemento de front-end possível que pode ser usado para descrever o significado deste campo. Exibido como um pequeno ícone ao lado do campo. | `string` |
| `hint` | Exibe informações adicionais. Disponível somente com o `frontend_model` específico. | `string` |
| `frontend_class` | Adiciona uma classe CSS definida ao elemento de HTML da seção renderizada. | `string` |
| `frontend_model` | Especifica um modelo de front-end diferente para alterar a renderização e modificar a saída. | `typeModel` |
| `backend_model` | Especifica um modelo de back-end diferente para modificar os valores configurados. | `typeModel` |
| `source_model` | Especifica um modelo de origem diferente que fornece um conjunto específico de valores. | `typeModel` |
| `config_path` | Pode ser usado para substituir o caminho de configuração genérico de um campo. | `typeConfigPath` |
| `validate` | Defina regras de validação diferentes (separadas por espaços). A lista de referência completa das regras de validação disponíveis está listada abaixo. | `string` |
| `can_be_empty` | Usado quando `type` é `multiselect` para especificar que um campo pode estar vazio. | `int` |
| `if_module_enabled` | Usado para exibir um campo somente quando um determinado módulo é ativado. | `typeModule` |
| `base_url` | Usado em combinação com `upload_dir` para carregamentos de arquivo. | `typeUrl` |
| `upload_dir` | Especifique um diretório de destino para uploads. Este nó tem atributos e nós adicionais. Procure-os antes de usar isso. | `typeUploadDir` |
| `button_url` | Exibe um botão se `button_url` e `button_label` forem especificados. Normalmente usado em combinação com um modelo de front-end personalizado. | `typeUrl` |
| `button_label` | Exibe um botão se `button_label` e `button_url` forem especificados. Normalmente usado em combinação com um modelo de front-end personalizado. | `string` |
| `more_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `demo_url` | Não extensível. Veja abaixo. | `typeUrl` |
| `hide_in_single_store_mode` | Se o grupo deve estar visível no modo de armazenamento único. `1` oculta o grupo; `0` mostra o grupo. | `int` |
| `options` | Não usado. Potencialmente obsoleto. | `complexType` |
| `depends` | Pode ser usado para declarar dependências a outros campos. É usado para mostrar apenas campos/grupos específicos quando um determinado campo tem um valor de `1`. Este nó espera uma cadeia de caracteres `section/group/field`. | `complexType` |
| `attribute` | Atributos personalizados podem ser usados por modelos de front-end. Normalmente usado para tornar um determinado modelo de front-end mais dinâmico. | `complexType` |
| `requires` | Não extensível. Veja abaixo. | `complexType` |

>[!WARNING]
>
>Os nós `more_url`, `demo_url`, `requires` e `options` são definidos por um modelo de pagamento principal diferente e são usados apenas uma vez. Esses nós não são reutilizáveis.

### Exemplo: criar dois campos em um determinado grupo

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

O exemplo acima cria dois campos, ambos visíveis/configuráveis no padrão e na exibição de loja. Ambos os campos têm um comentário e uma dica de ferramenta para descrever sua finalidade para o usuário. O nó `label` pode ser traduzido.
O campo com o identificador `ANOTHER_UNIQUE_FIELD_ID` fica visível quando o módulo fornecido em `if_module_enabled` é habilitado globalmente. O campo também valida seu valor em relação às regras `required-entry` e `no-whitespace`.
O campo com o identificador `A_UNIQUE_FIELD_ID` define um modelo de origem diferente que fornece os valores `Yes` e `No`.

### Modelos de origem comuns

Os seguintes modelos de origem são fornecidos pelo Commerce 2 Core. Em geral, há muito mais modelos de origem; a lista a seguir descreve os mais comuns. Saiba que esses modelos de origem precisam do atributo de campo `type` para funcionarem corretamente.`select`

| Modelo do Source | Descrição |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Fornece os valores `Yes`, `No` e `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Fornece os valores `Enable`, `Disable`. Salva os valores como `0` e `1` no banco de dados. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Fornece os valores `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` e `24 Hours`. Os valores são salvos como números inteiros. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Fornece os valores para o formato de hora (12 h/24 h). |
| `Magento\Cron\Model\Config\Source\Frequency` | Fornece os valores `Daily`, `Weekly` e `Monthly`. Os valores são salvos no banco de dados como `D`, `W` e `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Fornece os valores para um código de 2 letras de um determinado idioma no formato ISO 639-1 (por exemplo, en). |
| `Magento\Config\Model\Config\Source\Locale` | Fornece os valores semelhantes ao acima, mas pertencem a um código de localidade (por exemplo, en_US). |

### Validação de campo

Um campo pode ter uma ou mais classes de validador atribuídas para garantir que a entrada do usuário atenda aos requisitos da extensão. Regras de validação podem ser aplicadas com a `<validate>`-Tag.
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
| `mobileUK` | Permite um número de telefone celular (Reino Unido). |
| `no-marginal-whitespace` | Não permite espaços em branco no início ou no fim do valor. |
| `no-whitespace` | Não permite espaços em branco. |
| `phoneUK` | Permite um número de telefone (Reino Unido). |
| `phoneUS` | Permite um número de telefone (EUA). |
| `required-entry` | Não permite um valor vazio (validação equivalente como `validate-no-empty`).<br>Mensagem de falha na validação: &quot;Este campo é obrigatório&quot;. |
| `time` | Permite um horário válido no formato de 24 horas, entre 00:00 e 23:59. Por exemplo `15`, `15:05` ou `15:05:48`. |
| `time12h` | Permite um horário válido no formato de 12 horas, entre 12h e 23h59min. :59: Por exemplo `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Permite 7 ou mais caracteres, usando numéricos e alfabéticos. |
| `validate-alphanum-with-spaces` | Permite o uso de letras (a-z ou A-Z), números (0-9) ou espaços apenas. |
| `validate-clean-url` | Permite um URL válido. Por exemplo, `https://www.example.com` ou `www.example.com`. |
| `validate-currency-dollar` | Permite um valor válido (em dólar). Por exemplo, $100,00. |
| `validate-data` | Permite o uso de letras (a-z ou A-Z), números (0-9) ou sublinhados (\_) apenas.<br>O primeiro caractere deve ser uma letra.<br>(Deve corresponder à expressão: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Mensagem de falha de validação: &quot;Use somente letras (a-z ou A-Z), números (0-9) ou sublinhado (\_) neste campo e o primeiro caractere deve ser uma letra.&quot; |
| `validate-date-au` | Impõe o seguinte formato de data: dd/mm/aaaa. Por exemplo, 03/17/2006 para 17 de março de 2006. |
| `validate-email` | Permite um endereço de email válido. Por exemplo, johndoe@domain.com. |
| `validate-emailSender` | Permite um endereço de email válido. Por exemplo, johndoe@domain.com. |
| `validate-fax` | Permite um número de fax válido. Por exemplo, 123-456-7890. |
| `validate-no-empty` | Não permite um valor vazio (validação equivalente como `requried-entry`).<br>Mensagem de falha de validação: &quot;Valor vazio&quot;. |
| `validate-no-html-tags` | Não permite o uso de tags HTML. |
| `validate-password` | Permite 6 ou mais caracteres. Espaços à esquerda e à direita serão ignorados. |
| `validate-phoneLax` | Permite um número de telefone válido. Por exemplo, (123) 456-7890 ou 123-456-7890. |
| `validate-phoneStrict` | Permite um número de telefone válido. Por exemplo, (123) 456-7890 ou 123-456-7890. |
| `validate-select` | Impõe que a opção de seleção escolhida não tenha um valor `null`, um valor de cadeia de caracteres `none` ou um comprimento de cadeia de caracteres igual a 0. |
| `validate-ssn` | Permite um número de seguro social válido (EUA). Por exemplo, 123-45-6789. |
| `validate-street` | Permite o uso de letras (a-z ou A-Z), números (0-9), espaços e somente &quot;#&quot;. |
| `validate-url` | Permite um URL válido. O protocolo é obrigatório (http://, https:// ou ftp://). |
| `validate-xml-identifier` | Permite um identificador XML válido. Por exemplo, algo_1, bloco5, id-4. |
| `validate-zip-us` | Permite um CEP válido (EUA). Por exemplo, 90602 ou 90602-1234. |
| `vinUS` | Permite o valor do número de identificação do veículo (VIN) (EUA). |

### Valores padrão

Os valores padrão para campos podem ser definidos no arquivo `etc/config.xml` do módulo especificando-se o valor padrão no nó `section/group/field_ID`.

#### Exemplo: Definindo o valor padrão para `ANOTHER_UNIQUE_FIELD_ID` (Escopo padrão)

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

#### Exemplo: Definindo o valor padrão para `ANOTHER_UNIQUE_FIELD_ID` (Escopo do site)

Usando a marca `websites`, especifique o valor padrão para um site específico.

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
