---
title: '[!DNL Upgrade Compatibility Tool] Mensagens de Erro'
description: Saiba mais sobre as mensagens de erro que você encontra ao usar o  [!DNL Upgrade Compatibility Tool] no seu projeto do Adobe Commerce.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] mensagens de erro

{{commerce-only}}

Esta referência de mensagem de erro fornece informações sobre erros que podem ocorrer durante a execução de [!DNL Upgrade Compatibility Tool].

As mensagens de erro são categorizadas por nível (problemas críticos, erros e avisos) e tipo (código principal, código personalizado e esquemas do GraphQL). Cada tipo contém as seguintes informações:

- **Código de erro**: o identificador atribuído pelo Adobe Commerce para a mensagem de erro.
- **Descrição do erro**: uma descrição que resume a causa do erro.
- **Ação sugerida por erro**: se aplicável, fornece orientação para solucionar e resolver o erro.

## Problemas críticos

### Código principal

Esses erros são relatados quando alguns dos arquivos principais estão ausentes ou não correspondem ao original.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 2001 | O arquivo principal não foi encontrado | Execute o comando `composer install` no diretório raiz do projeto. |
| 2002 | O arquivo principal foi modificado | Execute o comando `composer install` no diretório raiz do projeto. |
| 2003 | A dependência do Composer não está instalada | A dependência de compositor ausente pode resultar em problemas. Restaurar dependência executando `composer require package_name`. |
| 2005 | A pasta principal não foi encontrada | Execute o comando `composer install` no diretório raiz do projeto. |

{style="table-layout:auto"}

### Código personalizado

Erros críticos são gerados quando o código personalizado faz referência a entidades que não estão presentes na versão de destino do Adobe Commerce. Esses erros também são relatados quando os padrões de codificação críticos foram quebrados.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 1110 | Instanciando classe/interface Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. Instanciando classe/interface Adobe Commerce inexistente. |
| 1111 | Extensão de classe Adobe Commerce inexistente | A classe estendida não está mais presente na base de código. A herança não é uma maneira recomendada de estender a funcionalidade do Adobe Commerce. Atualizar código para usar uma classe marcada como `@api`. |
| 1112 | Importando classe Adobe Commerce não existente | Atualizar código para usar uma classe marcada como `@api`. |
| 1113 | Carregando classe Adobe Commerce não existente | Atualizar código para usar uma classe marcada como `@api`. |
| 1114 | Uso de classe Adobe Commerce não existente | Atualizar código para usar uma classe marcada como `@api`. |
| 1214 | Uso de constante inexistente do Adobe Commerce | Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1215 | Substituição de constante inexistente do Adobe Commerce | Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1216 | Atribuição de constante Adobe Commerce inexistente | Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1312 | Interface do Adobe Commerce não existente importada | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1314 | Interface do Adobe Commerce usada inexistente | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1317 | Interface do Adobe Commerce herdada e inexistente | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1318 | Interface do Adobe Commerce não existente implementada | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1410 | Chamar método Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. |
| 1514 | Uso de propriedade não existente do Adobe Commerce | Atualizar código para usar uma classe marcada como `@api`. |
| 1515 | Substituição de propriedade Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. |
| 1516 | Atribuição de propriedade Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. Atualize o nível de acesso da propriedade para privado se ele puder ser usado somente em uma única classe. |
| 5002 | A tag de abertura do PHP deve ser o primeiro conteúdo do arquivo | Verifique se não há conteúdo no arquivo antes da tag de abertura do PHP. |
| 5003 | A função foi descontinuada | Use uma substituição sugerida na mensagem de erro. Se a mensagem não sugerir uma substituição, é necessária uma análise detalhada para selecionar uma função ou implementação alternativa. |
| 5005 | Erro de sintaxe do PHP | O código deve ser atualizado para estar em conformidade com os padrões de sintaxe do PHP. |
| 5072 | Possível violação de design do Magento 2. Detectada uma construção típica de Magento 1.x | Atualização da construção para os padrões Magento 2. |
| 5076 | Não é possível usar no namespace porque está reservado desde o PHP 7 | Substituir a palavra reservada no namespace por uma palavra-chave não reservada. |
| 5077 | Não é possível usar como nome de classe pois está reservado desde o PHP 7 | Substitua o nome de classe reservado por um nome não reservado. |

{style="table-layout:auto"}

### Esquema de BD

Problemas críticos do esquema de banco de dados são relatados se as tabelas principais ou colunas removidas forem referenciadas por restrições personalizadas.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 7009 | A restrição personalizada está fazendo referência a uma tabela principal que foi removida na versão de destino | Remover a restrição ou atualizar os atributos referenceTable e referenceColumn |
| 7010 | A restrição personalizada está fazendo referência a uma coluna principal que foi removida na versão de destino | Remover a restrição ou atualizar o atributo referenceColumn |

{style="table-layout:auto"}

### Esquema do GraphQL

Problemas críticos de Esquema do GraphQL são gerados se os itens de esquema não estiverem presentes na versão de destino.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 3101 | O tipo foi removido | Listar todas as consultas que fazem referência a este campo. Verifique se essas consultas são usadas pela implementação de personalização. Atualize o código de cliente para lidar com a interface de consulta alterada. |
| 3102 | Tipo removido da união | Se o tipo de união for usado na construção da solicitação GraphQL ou na implementação do processamento de resposta, talvez seja necessário atualizá-lo. |
| 3103 | Campo removido | Verifique se o campo é referenciado na base de código de personalização. Ajuste a implementação para lidar corretamente com o novo tipo de campo. |
| 3105 | Interface implementada removida | Verifique se o tipo que implementa a interface removida é usado na personalização. A implementação pode precisar ser atualizada se estiver dependendo da interface removida. |
| 3106 | Valor removido de enum | Se o valor de enumeração removido for usado na construção da solicitação GraphQL ou na implementação do processamento de resposta, talvez seja necessário atualizá-lo. |
| 3107 | Argumento removido | Verifique se o campo é usado na base de código de personalização. Remova o argumento desse campo. |
| 3109 | Diretiva removida | Verifique se a diretiva é usada na base de código de personalização. Ajuste a implementação para remover a referência à diretiva. |
| 3110 | Argumento de diretiva removido | Verifique se a diretiva é usada na base de código de personalização. Remova o argumento de diretiva. |
| 3111 | Diretiva repetível removida | Verifique se a diretiva é usada na base de código de personalização. Ajuste a implementação para lidar com as alterações na interface. |
| 3112 | Localização da diretiva removida | Verifique se a diretiva é usada na base de código de personalização. Ajuste a implementação para lidar com as alterações na interface. |
| 3201 | Tipo alterado | Listar todas as consultas que fazem referência a este campo. Verifique se essas consultas são usadas pela implementação de personalização. Atualize o código de cliente para lidar com a interface de consulta alterada. |
| 3203 | Tipo de campo alterado | Verifique se o campo é referenciado na base de código de personalização. Ajuste a implementação para lidar corretamente com o novo tipo de campo. |
| 3207 | Tipo de argumento alterado | Verifique se o campo é usado na base de código de personalização. Atualize o tipo de argumento deste campo. |
| 3303 | Campo de entrada obrigatório adicionado | O campo deve ser adicionado à solicitação se a consulta que inclui esse campo for usada para personalização. |
| 3307 | Argumento obrigatório adicionado | Verifique se o campo é usado na base de código de personalização. O novo argumento necessário deve ser especificado ao usar o campo. |
| 3310 | Argumento de diretiva obrigatório adicionado | Verifique se a diretiva é usada na base de código de personalização. Adicione o argumento de diretiva. |

{style="table-layout:auto"}

## Erros

### Código personalizado

Erros de código personalizado são gerados quando o código personalizado está usando os pontos de entrada do Adobe Commerce que não são considerados/marcados como `@api`. O comportamento preservado desses pontos de entrada não é garantido. Em vez disso, a personalização deve depender de `@api` pontos de entrada. A funcionalidade baseada no código Adobe Commerce não API deve ser testada após a atualização. Esses erros também são relatados quando os principais padrões de codificação são quebrados.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 1104 | Uso de classe não API que está herdando a interface de API | As classes que não estão marcadas como `@api` podem ser alteradas. Considere atualizar o código para depender da interface marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1121 | Extensão da classe de API não-Adobe Commerce | A classe estendida não está mais presente na base de código. A herança não é uma maneira recomendada de estender a funcionalidade do Adobe Commerce. Atualizar código para usar uma classe marcada como `@api`. |
| 1122 | Importação de classe de API não-Adobe Commerce | A classe estendida não está mais presente na base de código. Atualizar código para usar uma classe marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1123 | Carregando classe de API não Adobe Commerce | A classe estendida não está mais presente na base de código. Atualizar código para usar uma classe marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1124 | Uso de classe de API não Adobe Commerce | A classe estendida não está mais presente na base de código. Atualizar código para usar uma classe marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1224 | Uso de constante de API não Adobe Commerce | Constantes que não estão marcadas como `@api` podem ser alteradas. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1225 | Substituição de constante de API não Adobe Commerce | Constantes que não estão marcadas como `@api` podem ser alteradas. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1226 | Atribuição de constante de API não Adobe Commerce | Constantes que não estão marcadas como `@api` podem ser alteradas. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1322 | Interface de API não Adobe Commerce importada | Interfaces não marcadas como `@api` podem ser alteradas. Considere remover essa herança ou substituí-la pela herança da interface do Adobe Commerce marcada como `@api` ou de uma interface introduzida no escopo do código de personalização. |
| 1324 | Interface de API não Adobe Commerce usada | Interfaces não marcadas como `@api` podem ser alteradas. Considere remover essa herança ou substituí-la pela herança da interface do Adobe Commerce marcada como `@api` ou de uma interface introduzida no escopo do código de personalização. |
| 1327 | Interface de API não Adobe Commerce herdada | Constantes que não estão marcadas como `@api` podem ser alteradas. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1328 | Interface de API não Adobe Commerce implementada | Interfaces não marcadas como `@api` podem ser alteradas. Considere remover essa herança ou substituí-la pela herança da interface do Adobe Commerce marcada como `@api` ou de uma interface introduzida no escopo do código de personalização. |
| 1420 | Instanciando classe/interface de API não-Adobe Commerce | As classes que não estão marcadas como `@api` podem ser alteradas. Considere atualizar o código para depender da interface marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. Além disso, a maneira recomendada de recuperar uma ocorrência da classe é usando ID. Considere o uso de um fatory se uma nova instância da classe for necessária. |
| 1428 | Possível dependência dos detalhes de implementação. | As classes que não estão marcadas como `@api` podem ser alteradas. Considere atualizar o código para depender da interface marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1429 | Chamar métodos de API que não sejam do Adobe Commerce | Os métodos que não estão marcados como `@api` ou não são declarados na classe/interface da API podem ser alterados. Mesmo se a interface do método não for atualizada na nova versão, seu comportamento ou saída poderão ser diferentes. Considere confiar em um método de interface. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1449 | Chamada para método sem interface (que está presente na implementação) | Os métodos que não são declarados na interface podem ser alterados. Considere confiar em um método de interface. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1524 | Uso de propriedade de API não-Adobe Commerce | Os valores das propriedades que não estão marcadas como `@api` podem ser alterados. Considere depender do método da interface da API. |
| 1525 | Substituição da propriedade de API que não é do Adobe Commerce | Os valores das propriedades que não estão marcadas como `@api` podem ser alterados. Considere depender do método da interface da API. |
| 1526 | Atribuição de propriedade de API não-Adobe Commerce | Os valores das propriedades que não estão marcadas como `@api` podem ser alterados. Considere depender do método da interface da API. |
| 5004 | A função sem argumento foi preterida | Passe a entrada para validar como o primeiro argumento da função. |
| 5007 | O uso de determinadas funções é desencorajado | Evite usar essas funções. |
| 5009 | As diretivas de modelo não podem invocar métodos. Somente o acesso escalar à matriz é permitido | Remover invocações de método do modelo. |
| 5010 | O bloco de comentários do modelo `@vars` contém JSON inválido | Corrija um JSON inválido. |
| 5011 | O bloco de comentários do modelo `@vars` contém um rótulo inválido | Corrija o rótulo inválido. |
| 5012 | O bloco de comentários do modelo `@vars` não tem uma variável usada no modelo | Adicione a variável ausente ao bloco de comentário @vars. |
| 5013 | Evite usar a tag de fechamento automático com um elemento html não nulo | Em vez disso, use fechar tag. |
| 5014 | O atributo `"active"` é obsoleto | A lista de módulos ativos é definida na configuração de implantação. |
| 5015 | O nó `<param>` está obsoleto | Em vez disso, use `<argument name="..." xsi:type="...">`. |
| 5016 | O nó `<instance>` está obsoleto | Em vez disso, use `<argument name="..." xsi:type="object">`. |
| 5017 | O nó `<array>` está obsoleto | Em vez disso, use `<argument name="..." xsi:type="array">`. |
| 5018 | O nó `<item key="...">` está obsoleto | Em vez disso, use `<item name="..." xsi:type="...">`. |
| 5019 | O nó `<value>` está obsoleto | Em vez disso, forneça o valor real como um literal de texto. |
| 5020 | Nó obsoleto: `<supported_blocks>` | A ser substituído por `<supported_containers>`. |
| 5021 | Nó obsoleto: `<block_name>` | A ser substituído por `<container_name>`. |
| 5022 | Nome de fábrica detectado | O tipo de widget não deve começar com /. |
| 5023 | Estrutura ACL obsoleta detectada na linha | Consulte lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Estrutura de menu obsoleta detectada na linha | Consulte app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Estrutura de configuração de sistema obsoleta detectada no arquivo | Consulte app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Não usar o atributo de tipo `"text/javascript"` | Usar somente membros públicos. |
| 5028 | O acesso a membros protegidos e privados da classe `Block` está obsoleto em modelos phtml | Usar somente membros públicos. |
| 5031 | Contém método obsoleto | Em vez disso, use o método `getConnection()`. |
| 5042 | Formato incorreto de referência de classe PHP | Verifique se a classe é referenciada usando apenas letras camelCased, números e nenhuma barra à esquerda. |
| 5043 | Formato incorreto de referência do módulo | Verifique se o módulo é referenciado usando apenas letras, números, sublinhados e nenhuma barra à esquerda. |
| 5044 | A classe `Zend_Db_Select` é restrita | Substituição sugerida: `\Magento\Framework\DB\Select`. |
| 5045 | A classe `Zend_Db_Adapter_Pdo_Mysql` é restrita | Substituição sugerida: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | A classe `Magento\Framework\Serialize\Serializer\Serialize` é restrita | Substituição sugerida: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | A classe `ArrayObject` é restrita | Substituição sugerida: classe personalizada, estendida de `ArrayObject` com métodos serialize/unserialize substituídos. |
| 5048 | A classe `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` é restrita | Sugestão de substituição: Fábrica que cria classe personalizada, estendida de `ArrayObject` com métodos serialize/unserialize substituídos. |
| 5050 | O bloco que está sendo referenciado foi removido | Remover referência para bloqueio. |
| 5051 | `output="toHtml"` está obsoleto | Usar `output="1"`. |
| 5052 | A classe `\Magento\Framework\View\Element\Text\ListText` não deve mais ser usada no layout | Remover classe `\Magento\Framework\View\Element\Text\ListText` do layout. |
| 5053 | Chamada de método via instrução de layout `<action>` não permitida | Evite usar método ofensivo em `<action>`. |
| 5054 | O atributo `helper` contém `/` | Remover `/` do atributo auxiliar. |
| 5055 | O atributo `helper` não contém `::` | Adicionar `::` ao atributo auxiliar. |
| 5056 | Os scripts de instalação são obsoletos | Use a abordagem de esquema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5057 | Os scripts InstallSchema são obsoletos | Use a abordagem de esquema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5058 | Os scripts InstallData estão obsoletos | Use a abordagem de patches de dados no diretório Setup/Patch/Data do módulo. |
| 5059 | Os scripts de instalação são obsoletos | Crie uma classe InstallData na pasta Setup do módulo. |
| 5060 | Os scripts de atualização estão obsoletos | Use a abordagem de esquema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5061 | Os scripts UpgradeSchema são obsoletos | Use a abordagem de esquema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5062 | Os scripts UpgradeData estão obsoletos | Use a abordagem de patches de dados no diretório Setup/Patch/Data do módulo. |
| 5063 | Os scripts de atualização estão obsoletos | Use a abordagem de patches de dados no diretório Setup/Patch/Data do módulo. |
| 5064 | Os scripts recorrentes estão obsoletos | Crie uma classe Recurring na pasta Setup do módulo. |
| 5065 | &#39;data&#39; está em um diretório inválido | Crie um patch de dados na pasta Configuração/Patch/Data do módulo para atualizações de dados ou use a abordagem de esquema declarativo no arquivo etc/db_schema.xml do módulo para alterações de esquema. |
| 5066 | &#39;sql&#39; está em um diretório inválido | Crie um patch de dados na pasta Configuração/Patch/Data do módulo para atualizações de dados ou use a abordagem de esquema declarativo no arquivo etc/db_schema.xml do módulo para alterações de esquema. |
| 5067 | Os nós identificados pelo XPath são obsoletos | O XML obsoleto apontado no erro deve ser atualizado. Siga as sugestões da mensagem de erro. |
| 5068 | A diretiva `{{htmlescape}}` é obsoleta | Em vez disso, use `{{var}}`. |
| 5069 | A diretiva `{{escapehtml}}` é obsoleta | Em vez disso, use `{{var}}`. |
| 5070 | O terceiro parâmetro não é mais necessário para `getChildHtml()` | Remova o terceiro parâmetro da chamada para `getChildHtml()`. |
| 5071 | O 4º parâmetro não é mais necessário para `getChildHtml()` | Remova o 4º parâmetro da chamada para `getChildHtml()`. |
| 5073 | Nomes de tabela herdados com barra devem ser corrigidos para nomes de tabela diretos | Em vez disso, use o nome direto da tabela. |
| 5075 | Os módulos do aplicativo não devem usar classes de módulos de teste | Remover o uso de classes de módulos de teste. |
| 5078 | A classe deve ser solicitada no construtor, caso contrário, o compilador não poderá localizar e gerar essas classes | Adicionar classe ao construtor. |
| 5079 | O uso de variáveis de classe var não é recomendado | Evite usar &#39;var&#39; para declarar variável de classe. |
| 5080 | Possível instrução SQL bruta detectada | Em vez disso, use repositórios ou patches de dados. |
| 5081 | O uso de auxiliares em modelos não é incentivado | Em vez disso, use ViewModel. |
| 5082 | O uso de $this em modelos está obsoleto | Em vez disso, use $block. |
| 5083 | Constantes não são permitidas como o primeiro argumento da função de tradução | Em vez disso, use o literal da string. |
| 5085 | O uso de determinadas funções é desencorajado | Em vez disso, use a função alternativa aconselhada na mensagem. |
| 5087 | Problema de compatibilidade entre versões do PHP | Siga as sugestões da mensagem e verifique o [guia de migração](https://www.php.net/manual/en/migration81.php). |
| 5088 | Parâmetros opcionais encontrados após os necessários | Mova os parâmetros necessários para depois dos opcionais. |
| 5089 | Visibilidade do método `final private` encontrada | Altere a visibilidade do método de `final private` para somente `private`. |
| 5090 | Método mágico `__set_state` não definido como `static` | O método mágico `__set_state` deve ser definido como `static`. |
| 5091 | A classe com o método `__toString()` não herda da interface `Stringable` | Adicionar interface `Stringable` à classe com método `__toString()`. |
| 5092 | Método `is_resource()` usado para funções que agora retornam Object | Alterar `is_resource()` para Objeto `instanceof`. |
| 6001 | `jQuery.andSelf()` removido | Usar `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` e `$.unbind` estão obsoletos | Em vez disso, use `$.on` e `$.off`. |
| 6003 | O método jQuery para inscrever-se no evento está obsoleto e não deve ser usado | Em vez disso, use o método `.on("event name", fn)` para assinar esse evento. |
| 6003 | O método jQuery para acionar o evento está obsoleto e não deve ser usado | Use o método `.trigger("event name")` para acionar esse evento. |
| 6004 | jQuery `$.delegate` e `$.undelegate` estão obsoletos | Em vez disso, use `$.on` e `$.off`. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) foi removido | Use (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` removido | Usar `jQuery.length`. |
| 6007 | `jQuery.trim` está obsoleto | Usar `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, tema &#39;inlite&#39;, tema &#39;móvel&#39;, tema &#39;moderno&#39;) foi removido | Atualize o código para torná-lo compatível com tinymce5. |
| 6009 | `jQuery.isFunction()` está obsoleto | Na maioria dos casos, ele pode ser substituído por [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` está obsoleto | Substitua com uma verificação de tipo apropriada como [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` está obsoleto | Em vez disso, use o método Array.isArray nativo. |
| 6009 | `jQuery.parseJSON()` está obsoleto | Para analisar cadeias de caracteres JSON, use o método nativo JSON.parse. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) está obsoleto | Em vez disso, use jQuery.expr.pseudos. |

{style="table-layout:auto"}

### Esquema de BD

Erros de Esquema de BD são gerados se as tabelas, colunas, índices ou restrições do banco de dados, adicionadas ou removidas na versão de destino do Adobe Commerce, puderem resultar em conflitos com o esquema de banco de dados personalizado.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 7001 | A versão principal do target apresenta uma tabela com o mesmo nome de uma tabela declarada por um módulo personalizado | Usar a nova tabela principal (se apropriado) ou renomear a tabela personalizada |
| 7002 | A tabela principal estendida por um módulo personalizado foi removida na versão de destino | Todas as referências removidas da tabela principal devem ser removidas da base de código |
| 7003 | A versão principal do target introduz uma coluna com o mesmo nome de uma coluna declarada por um módulo personalizado | Use a nova coluna principal (se apropriado) ou renomeie a coluna personalizada |
| 7004 | A coluna principal estendida por um módulo personalizado foi removida na versão de destino | Todas as referências de coluna principais removidas devem ser removidas da base de código |
| 7005 | A versão principal do target introduz um índice com a mesma referenceId que um índice declarado por um módulo personalizado | Remover (se duplicado para o índice principal introduzido) ou renomear o índice personalizado |
| 7006 | O índice principal estendido por um módulo personalizado foi removido na versão de destino | Todas as referências de índice principal removidas devem ser removidas da base de código |
| 7007 | A versão principal do público-alvo introduz uma restrição com o mesmo nome de uma restrição declarada por um módulo personalizado | Remover (se duplicado para a restrição principal introduzida) ou renomear a restrição personalizada |
| 7008 | A restrição principal estendida por um módulo personalizado foi removida na versão de destino | Usar a nova restrição principal (se apropriado) ou renomear a restrição personalizada |

{style="table-layout:auto"}

## Avisos

### Código principal

Esses avisos são relatados quando há pequenas inconsistências na base de código principal.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 2004 | Incompatibilidade de versão de dependência do compositor | Problema indica que a versão de dependência do Composer no metalon e no projeto real é diferente. Atualizar dependência executando `composer update <package_name>`. |

{style="table-layout:auto"}

### Código personalizado

Os avisos de código personalizado são gerados quando as referências a códigos obsoletos são detectadas. Essas referências devem ser substituídas pelos pontos de extensão compatíveis. Preste atenção à anotação `@see` do item obsoleto para recomendações. Esses erros também são relatados quando padrões de codificação secundários são quebrados.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 1131 | Extensão da classe ``@deprecated`` do Adobe Commerce | A classe estendida será removida nas próximas versões. A herança não é uma maneira recomendada de estender a funcionalidade do Adobe Commerce. Atualizar código para usar uma classe marcada como `@api`. |
| 1132 | Importando classe `@deprecated` do Adobe Commerce | A classe estendida será removida nas próximas versões. Considere usar a classe Adobe Commerce marcada como `@api`. |
| 1133 | Carregando classe `@deprecated` do Adobe Commerce | A classe estendida será removida nas próximas versões. Considere usar a classe Adobe Commerce marcada como `@api`. |
| 1134 | Usando a classe `@deprecated` do Adobe Commerce | A classe estendida será removida nas próximas versões. Considere usar a classe Adobe Commerce marcada como `@api`. |
| 1234 | Usando a constante `@deprecated` do Adobe Commerce | A constante obsoleta será removida nas próximas versões. Considere usar uma constante marcada como `@api` ou uma constante privada em sua implementação. |
| 1235 | Substituindo a constante `@deprecated` do Adobe Commerce | A constante obsoleta será removida nas próximas versões. Considere usar uma constante marcada como `@api` ou uma constante privada em sua implementação. |
| 1236 | Atribuição da constante `@deprecated` do Adobe Commerce | A constante obsoleta será removida nas próximas versões. Considere usar uma constante marcada como `@api` ou uma constante privada em sua implementação. |
| 1332 | Interface `@deprecated` do Adobe Commerce importada | A interface obsoleta será removida nas próximas versões. Considere usar uma interface ou classe marcada como `@api`. |
| 1334 | Interface `@deprecated` do Adobe Commerce usada | A interface obsoleta será removida nas próximas versões. Considere usar uma interface ou classe marcada como `@api`. |
| 1337 | Herdado da interface `@deprecated` do Adobe Commerce | A interface obsoleta será removida nas próximas versões. Considere remover a herança da interface, usando uma interface marcada como `@api` ou uma interface introduzida na implementação. |
| 1338 | Interface `@deprecated` do Adobe Commerce implementada | A interface obsoleta será removida nas próximas versões. Considere remover a herança da interface, usando uma interface marcada como `@api` ou uma interface introduzida na implementação. |
| 1430 | Chamada não declarada para método dataobject | Os métodos mágicos que não são declarados podem ser alterados. Considere depender de métodos de interface. |
| 1439 | Chamar método `@deprecated` do Adobe Commerce | O método obsoleto será removido nas próximas versões. Considere confiar em métodos declarados em interfaces de API. |
| 1440 | Incompatibilidade de assinatura de método | Uma chamada ou substituição do método principal é detectada com parâmetros, argumentos ou tipo de retorno que não corresponde à assinatura do método. |
| 1534 | Usando a propriedade `@deprecated` do Adobe Commerce | O método obsoleto será removido nas próximas versões. Considere confiar em métodos declarados em interfaces de API. |
| 1535 | Substituindo a propriedade `@deprecated` do Adobe Commerce | A propriedade obsoleta será removida nas próximas versões. Considere depender de métodos declarados nas interfaces da API ou usar uma propriedade privada na implementação. |
| 1536 | Atribuição da propriedade `@deprecated` do Adobe Commerce | O método obsoleto será removido nas próximas versões. Considere confiar em métodos declarados em interfaces de API. |
| 5006 | Proxies e interceptores nunca DEVEM ser solicitados explicitamente em construtores | A classe original deve ser declarada como um tipo do parâmetro do construtor. A classe Interceptor/Proxy será passada pela implementação da injeção de dependência de estrutura. |
| 5074 | Uso do método obsoleto `getResource()` para (salvar / carregar / excluir) dados detectados. | Em vez disso, use um repositório. |
| 5086 | Visibilidade não declarada em uma constante | Declarar a visibilidade em todas as constantes. |

{style="table-layout:auto"}

### Esquema do GraphQL

Os avisos do esquema do GraphQL são gerados quando os itens adicionais são adicionados ao esquema na nova versão. É recomendável revisar a implementação para ver se elas devem ser usadas para solicitações.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 3206 | Valor padrão do argumento alterado | Se a query for usada na personalização, talvez o valor do argumento precise ser especificado explicitamente. |
| 3302 | Tipo adicionado à união | O tipo foi adicionado à união. Verifique o processamento da implementação do resultado da consulta que retorna esse tipo de união e verifique se ela é capaz de lidar com o tipo adicionado. |
| 3304 | Campo de entrada opcional adicionado | Campo de entrada opcional adicionado. Verifique a implementação para garantir. |
| 3305 | Interface implementada adicionada | O campo pode aceitar/fornecer mais informações que podem ser consideradas na implementação. |
| 3306 | Valor adicionado à enumeração | Um valor foi adicionado a um enum. Se os clientes contiverem uma instrução switch no valor do enum e não incluírem um caso padrão, essa alteração poderá causar um comportamento inesperado. |
| 3308 | Argumento opcional adicionado | Se a consulta estiver usando um novo argumento na personalização, talvez seja necessário adicioná-lo à solicitação. |

{style="table-layout:auto"}
