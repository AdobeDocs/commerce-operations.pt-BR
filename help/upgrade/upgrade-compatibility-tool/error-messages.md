---
title: '"[!DNL Upgrade Compatibility Tool] Mensagens de erro"'
description: Saiba mais sobre as mensagens de erro encontradas ao usar o [!DNL Upgrade Compatibility Tool] no seu projeto do Adobe Commerce.
source-git-commit: 9bdf64177b4cecab5dd3562fef0bcc507a57ccf0
workflow-type: tm+mt
source-wordcount: '3816'
ht-degree: 4%

---


# [!DNL Upgrade Compatibility Tool] mensagens de erro

{{commerce-only}}

Essa referência de mensagem de erro fornece informações sobre erros que podem ocorrer durante a execução do [!DNL Upgrade Compatibility Tool].

As mensagens de erro são categorizadas por nível (problemas críticos, erros e avisos) e tipo (código principal, código personalizado e esquemas GraphQL). Cada tipo contém as seguintes informações:

- **Código de erro**: O identificador atribuído pela Adobe Commerce para a mensagem de erro.
- **Descrição do erro**: Uma descrição que resume a causa do erro.
- **Erro de ação sugerida**: Se aplicável, fornece orientação para solucionar e resolver o erro.

## Questões críticas

### Código principal

Esses erros são relatados quando alguns dos arquivos principais estão ausentes ou não correspondem ao original.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 2001 | O ficheiro principal não foi encontrado | Execute o `composer install` do diretório raiz do projeto. |
| 2002 | O arquivo principal foi modificado | Execute o `composer install` do diretório raiz do projeto. |
| 2003 | A dependência do compositor não está instalada | A dependência do compositor ausente pode resultar em problemas. Restaurar dependência executando `composer require package_name`. |
| 2005 | A pasta principal não foi encontrada | Execute o `composer install` do diretório raiz do projeto. |

{style=&quot;table-layout:auto&quot;}

### Código personalizado

Erros críticos são gerados quando o código personalizado faz referência a entidades que não estão presentes na versão de destino do Adobe Commerce. Esses erros são também relatados quando os padrões críticos de codificação foram quebrados.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 1110 | Instanciamento de classe/interface Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. Instanciamento de classe/interface Adobe Commerce inexistente. |
| 111 | Extensão da classe Adobe Commerce inexistente | A classe estendida não está mais presente na base de código. A herança não é uma maneira recomendada de estender a funcionalidade do Adobe Commerce. Atualizar código para usar uma classe marcada como `@api`. |
| 1112 | Importando classe Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. |
| 1113 | Carregando classe Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. |
| 1114 | Uso de classe Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. |
| 1214 | Uso de constante Adobe Commerce inexistente | Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1215 | Substituição da constante Adobe Commerce inexistente | Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1216 | Atribuição de constante Adobe Commerce inexistente | Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1312 | Interface do Adobe Commerce inexistente importada | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1314 | Interface do Adobe Commerce não existente usada | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1317 | Interface herdada não existente do Adobe Commerce | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1318 | Implementação de interface de Adobe Commerce inexistente | Considere remover a herança ou substituí-la pela interface introduzida no escopo da personalização. |
| 1410 | Chamar método Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. |
| 1514 | Uso de propriedade Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. |
| 1515 | Substituição de propriedade não existente do Adobe Commerce | Atualizar código para usar uma classe marcada como `@api`. |
| 1516 | Atribuição de propriedade Adobe Commerce inexistente | Atualizar código para usar uma classe marcada como `@api`. Atualize o nível de acesso da propriedade para private se ele puder ser usado somente em uma única classe. |
| 5002 | A tag PHP de abertura deve ser o primeiro conteúdo do arquivo | Certifique-se de que não haja conteúdo no arquivo antes da tag de abertura do PHP. |
| 5003 | A função foi preterida | Use uma substituição sugerida na mensagem de erro. Se a mensagem não sugerir uma substituição, uma revisão de fechamento será necessária para selecionar uma função alternativa ou implementação. |
| 5005 | Erro de sintaxe PHP | O código deve ser atualizado para estar em conformidade com os padrões de sintaxe PHP. |
| 5072 | Possível violação de design do Magento 2. Detectada uma construção típica de Magento 1.x | Atualize a construção para os padrões Magento 2. |
| 5076 | Não é possível usar no namespace, pois está reservado desde PHP 7 | Substitua a palavra reservada no namespace por uma palavra-chave não reservada. |
| 5077 | Não é possível usar como nome de classe, pois está reservado desde PHP 7 | Substitua o nome da classe reservada por um nome não reservado. |

{style=&quot;table-layout:auto&quot;}

### Esquema GraphQL

Os problemas críticos do Esquema GraphQL são levantados se os itens do esquema não estiverem presentes na versão de destino.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 3101 | O tipo foi removido | Liste todas as queries que fazem referência a esse campo. Verifique se essas consultas são usadas pela implementação de personalização. Atualize o código de cliente para lidar com a interface de consulta alterada. |
| 3102 | Tipo removido da união | Se o tipo de união for usado na construção da solicitação GraphQL ou na implementação do processamento de resposta, talvez seja necessário atualizá-la. |
| 3103 | Campo removido | Verifique se o campo é referenciado na base de código de personalização. Ajuste a implementação para lidar corretamente com o novo tipo de campo. |
| 3105 | Interface implementada removida | Verifique se o tipo que implementa a interface removida é usado na personalização. A implementação pode precisar ser atualizada se depender da interface removida. |
| 3106 | Valor removido de enum | Se o valor de enum removido for usado na construção da solicitação GraphQL ou na implementação do processamento de resposta, talvez seja necessário atualizá-lo. |
| 3107 | Argumento removido | Verifique se o campo é usado na base de código de personalização. Remova o argumento para este campo. |
| 3109 | Diretiva removida | Verifique se a diretiva é usada na base de código de personalização. Ajustar a implementação para suprimir a referência à diretiva. |
| 3110 | Argumento de diretiva removido | Verifique se a diretiva é usada na base de código de personalização. Remova o argumento da diretiva. |
| 3111 | Diretiva removida repetidamente | Verifique se a diretiva é usada na base de código de personalização. Ajuste a implementação para lidar com as alterações da interface. |
| 3112 | Local da diretiva removido | Verifique se a diretiva é usada na base de código de personalização. Ajuste a implementação para lidar com as alterações da interface. |
| 3201 | Tipo alterado | Liste todas as queries que fazem referência a esse campo. Verifique se essas consultas são usadas pela implementação de personalização. Atualize o código de cliente para lidar com a interface de consulta alterada. |
| 3203 | Tipo de alteração de campo | Verifique se o campo é referenciado na base de código de personalização. Ajuste a implementação para lidar corretamente com o novo tipo de campo. |
| 3207 | Argumento alterado | Verifique se o campo é usado na base de código de personalização. Atualize o tipo de argumento para esse campo. |
| 3303 | Campo de entrada necessário adicionado | O campo deve ser adicionado à solicitação se a consulta incluindo esse campo for usada para a personalização. |
| 3307 | Argumento necessário adicionado | Verifique se o campo é usado na base de código de personalização. O novo argumento necessário deve ser especificado ao usar o campo . |
| 3310 | Argumento de diretiva necessário adicionado | Verifique se a diretiva é usada na base de código de personalização. Adicione o argumento da diretiva. |

{style=&quot;table-layout:auto&quot;}

## Erros

### Código personalizado

Erros de código personalizado são gerados quando o código personalizado está usando pontos de entrada do Adobe Commerce que não são considerados/marcados como `@api`. O comportamento preservado desses pontos de entrada não é garantido. A personalização deve basear-se em `@api` em vez disso, pontos de entrada. A funcionalidade baseada em código Adobe Commerce que não seja de API deve ser testada após a atualização. Esses erros são também relatados quando os principais padrões de codificação foram quebrados.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 1104 | Uso de classes que não sejam de API e que herdem a interface de API | Classes que não estão marcadas como `@api` pode ser alterado. Considere atualizar o código para depender da interface marcada como `@api` em vez disso. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1121 | Extensão de classe de API que não seja da Adobe Commerce | A classe estendida não está mais presente na base de código. A herança não é uma maneira recomendada de estender a funcionalidade do Adobe Commerce. Atualizar código para usar uma classe marcada como `@api`. |
| 1122 | Importação de classe de API que não seja da Adobe Commerce | A classe estendida não está mais presente na base de código. Atualizar código para usar uma classe marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1123 | Carregamento de classe de API que não é da Adobe Commerce | A classe estendida não está mais presente na base de código. Atualizar código para usar uma classe marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1124 | Uso de classes de API que não sejam da Adobe Commerce | A classe estendida não está mais presente na base de código. Atualizar código para usar uma classe marcada como `@api`. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1224 | Uso da constante da API que não é da Adobe Commerce | Constantes que não estão marcadas como `@api` pode ser alterado. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1225 | Substituição da constante da API que não é da Adobe Commerce | Constantes que não estão marcadas como `@api` pode ser alterado. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1226 | Atribuição de constante de API que não seja a Adobe Commerce | Constantes que não estão marcadas como `@api` pode ser alterado. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1322 | Interface de API não-Adobe Commerce importada | Interfaces não marcadas como `@api` pode ser alterado. Considere remover essa herança ou substituí-la pela herança da interface do Adobe Commerce que está marcada como `@api` ou uma interface introduzida no escopo do código de personalização. |
| 1324 | Interface de API não-Adobe Commerce usada | Interfaces não marcadas como `@api` pode ser alterado. Considere remover essa herança ou substituí-la pela herança da interface do Adobe Commerce que está marcada como `@api` ou uma interface introduzida no escopo do código de personalização. |
| 1327 | Interface de API herdada que não é da Adobe Commerce | Constantes que não estão marcadas como `@api` pode ser alterado. Considere introduzir e usar uma constante privada do valor necessário no código personalizado. |
| 1328 | Implementação da interface de API sem Adobe Commerce | Interfaces não marcadas como `@api` pode ser alterado. Considere remover essa herança ou substituí-la pela herança da interface do Adobe Commerce que está marcada como `@api` ou uma interface introduzida no escopo do código de personalização. |
| 1420 | Instalação de classes/interfaces de API que não sejam da Adobe Commerce | Classes que não estão marcadas como `@api` pode ser alterado. Considere atualizar o código para depender da interface marcada como `@api` em vez disso. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. Além disso, a maneira recomendada de recuperar uma instância da classe é usar o DI. Considere usar uma fábrica se uma nova instância da classe for necessária. |
| 1428 | Possível dependência nos detalhes de implementação. | Classes que não estão marcadas como `@api` pode ser alterado. Considere atualizar o código para depender da interface marcada como `@api` em vez disso. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1429 | Chamar métodos de API que não sejam da Adobe Commerce | Métodos que não estão marcados como `@api` ou não são declaradas na classe/interface da API podem ser alteradas. Mesmo que a interface do método não seja atualizada na nova versão, seu comportamento ou saída pode ser diferente. Considere confiar em um método de interface. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1449 | Chamar para método não-interface (que está presente na implementação) | Os métodos que não são declarados na interface podem ser alterados. Considere confiar em um método de interface. Caso contrário, a funcionalidade que depende dessa implementação deve ser testada após a atualização. |
| 1524 | Uso de propriedades da API que não são da Adobe Commerce | Valores das propriedades que não estão marcadas como `@api` pode ser alterado. Em vez disso, considere confiar no método da interface da API. |
| 1525 | Substituição de propriedade da API que não é da Adobe Commerce | Valores das propriedades que não estão marcadas como `@api` pode ser alterado. Em vez disso, considere confiar no método da interface da API. |
| 1526 | Atribuição de propriedade de API que não seja da Adobe Commerce | Valores das propriedades que não estão marcadas como `@api` pode ser alterado. Em vez disso, considere confiar no método da interface da API. |
| 5004 | A função sem argumento foi preterida | Passe a entrada para validar como o primeiro argumento da função. |
| 5007 | O uso de determinadas funções é desencorajado | Evite usar essas funções. |
| 5009 | As diretivas de modelo não podem invocar métodos. Somente o acesso à matriz escalar é permitido | Remova invocações de método do modelo. |
| 5010 | Modelo `@vars` bloco de comentários contém JSON inválido | Correção de JSON inválido. |
| 5011 | Modelo `@vars` bloco de comentários contém rótulo inválido | Corrigir etiqueta inválida. |
| 5012 | Modelo `@vars` o bloco de comentário não tem uma variável usada no modelo | Adicione a variável ausente ao bloco de comentários @vars. |
| 5013 | Evite usar uma tag de fechamento automático com um elemento html que não seja nulo | Em vez disso, use fechar tag. |
| 5014 | O `"active"` atributo obsoleto | A lista de módulos ativos é definida na configuração de implantação. |
| 5015 | O `<param>` nó obsoleto | Use `<argument name="..." xsi:type="...">` em vez disso. |
| 5016 | O `<instance>` nó obsoleto | Use `<argument name="..." xsi:type="object">` em vez disso. |
| 5017 | O `<array>` nó obsoleto | Use `<argument name="..." xsi:type="array">` em vez disso. |
| 5018 | O `<item key="...">` nó obsoleto | Use `<item name="..." xsi:type="...">` em vez disso. |
| 5019 | O `<value>` nó obsoleto | Em vez disso, forneça o valor real como um literal de texto. |
| 5020 | Nó obsoleto: `<supported_blocks>` | A substituir por `<supported_containers>`. |
| 5021 | Nó obsoleto: `<block_name>` | A substituir por `<container_name>`. |
| 5022 | Nome de fábrica detectado | O tipo de widget não deve começar com /. |
| 5023 | Estrutura ACL obsoleta detectada na linha | Verifique lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Estrutura de menu obsoleta detectada na linha | Verifique app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Estrutura de configuração do sistema obsoleta detectada no arquivo | Verifique app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Não utilizar `"text/javascript"` atributo de tipo | Use apenas membros públicos. |
| 5028 | Acesso a membros protegidos e privados do `Block` classe obsoleta em modelos phtml | Use apenas membros públicos. |
| 5031 | Contém método obsoleto | Use `getConnection()` em vez disso. |
| 5032 | `loadLayout` método está obsoleto | Use `\Magento\Framework\View\Layout\Builder::build` em vez disso. |
| 5033 | `renderLayout` método está obsoleto | Use `\Magento\Framework\Controller\ResultInterface::renderResult` em vez disso. |
| 5034 | `_redirect` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Redirect::render` em vez disso. |
| 5035 | `_forward` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Forward::forward` em vez disso. |
| 5036 | `_setActiveMenu` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Page::setActiveMenu` em vez disso. |
| 5037 | `_addBreadcrumb` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Page::addBreadcrumb` em vez disso. |
| 5038 | `_addContent` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Page::addContent` em vez disso. |
| 5039 | `_addLeft` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Page::addLeft` em vez disso. |
| 5040 | `_addJs` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Page::addJs` em vez disso. |
| 5041 | `_moveBlockToContainer` método está obsoleto | Use `\Magento\Backend\Model\View\Result\Page::moveBlockToContainer` em vez disso. |
| 5042 | Formato incorreto de referência de classe PHP | Verifique se a classe é referenciada usando somente letras camelCased, números e sem barra à esquerda. |
| 5043 | Formato incorreto de referência de módulo | Verifique se o módulo é referenciado usando apenas letras, números, sublinhados e sem barra à esquerda. |
| 5044 | Classe `Zend_Db_Select` é restrito | Substituição sugerida: `\Magento\Framework\DB\Select`. |
| 5045 | Classe `Zend_Db_Adapter_Pdo_Mysql` é restrito | Substituição sugerida: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Classe `Magento\Framework\Serialize\Serializer\Serialize` é restrito | Substituição sugerida: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Classe `ArrayObject` é restrito | Substituição sugerida: Classe personalizada, estendida de `ArrayObject` com métodos serialize/unserialize substituídos. |
| 5048 | Classe `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` é restrito | Substituição sugerida: Fábrica que cria classe personalizada, estendida a partir de `ArrayObject` com métodos serialize/unserialize substituídos. |
| 5050 | O bloco que está sendo referenciado é removido | Remova a referência ao bloco. |
| 5051 | `output="toHtml"` é obsoleta | Use `output="1"`. |
| 5052 | A classe `\Magento\Framework\View\Element\Text\ListText` não deve mais ser usado no layout | Remover classe `\Magento\Framework\View\Element\Text\ListText` do layout. |
| 5053 | Chamada de método através da instrução de layout `<action>` não é permitido | Evite usar um método ofensivo em `<action>`. |
| 5054 | `helper` atributo contém `/` | Remover `/` do atributo auxiliar. |
| 5055 | `helper` atributo não contém `::` | Adicionar `::` para auxiliar o atributo. |
| 5056 | Os scripts de instalação são obsoletos | Use a abordagem de schema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5057 | Os scripts InstallSchema são obsoletos | Use a abordagem de schema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5058 | Os scripts InstallData são obsoletos | Use a abordagem de patches de dados no dir Configuração/Correção/Dados do módulo. |
| 5059 | Os scripts de instalação são obsoletos | Crie uma classe InstallData na pasta Configuração do módulo. |
| 5060 | Os scripts de atualização são obsoletos | Use a abordagem de schema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5061 | Os scripts UpgradeSchema são obsoletos | Use a abordagem de schema declarativo no arquivo etc/db_schema.xml do módulo. |
| 5062 | Os scripts UpgradeData são obsoletos | Use a abordagem de patches de dados no dir Configuração/Correção/Dados do módulo. |
| 5063 | Os scripts de atualização são obsoletos | Use a abordagem de patches de dados no dir Configuração/Correção/Dados do módulo. |
| 5064 | Os scripts recorrentes são obsoletos | Criar classe Recorrente na pasta Configuração do módulo. |
| 5065 | &#39;data&#39; está em um diretório inválido | Crie um patch de dados na pasta Setup/Patch/Data do módulo para atualizações de dados ou use a abordagem de schema declarativo no arquivo etc/db_schema.xml do módulo para alterações de esquema. |
| 5066 | &#39;sql&#39; está em um diretório inválido | Crie um patch de dados na pasta Setup/Patch/Data do módulo para atualizações de dados ou use a abordagem de schema declarativo no arquivo etc/db_schema.xml do módulo para alterações de esquema. |
| 5067 | Os nós identificados pelo XPath são obsoletos | O XML obsoleto apontado no erro deve ser atualizado. Siga as sugestões da mensagem de erro. |
| 5068 | Diretiva `{{htmlescape}}` é obsoleta | Use `{{var}}` em vez disso. |
| 5069 | Diretiva `{{escapehtml}}` é obsoleta | Use `{{var}}` em vez disso. |
| 5070 | O terceiro parâmetro não é mais necessário para `getChildHtml()` | Remover o terceiro parâmetro da chamada para `getChildHtml()`. |
| 5071 | O quarto parâmetro não é mais necessário para `getChildHtml()` | Remova o quarto parâmetro da chamada para `getChildHtml()`. |
| 5073 | Nomes de tabela herdados com barra devem ser corrigidos para nomes de tabela diretos | Em vez disso, use o nome da tabela direta. |
| 5075 | Os módulos de aplicação não devem utilizar classes a partir de módulos de ensaio | Remova o uso de classes dos módulos de teste. |
| 5078 | A classe deve ser solicitada no construtor; caso contrário, o compilador não poderá localizar e gerar essas classes | Adicionar classe ao construtor. |
| 5079 | O uso de variáveis de classe var é desencorajado | Evite usar &#39;var&#39; para declarar variável de classe. |
| 5080 | Possível instrução SQL bruta detectada | Em vez disso, use repositórios ou patches de dados. |
| 5081 | Não é recomendado o uso de ajuda em modelos | Em vez disso, use ViewModel. |
| 5082 | O uso de $this em modelos está obsoleto | Em vez disso, use $block. |
| 5083 | Constantes não são permitidas como o primeiro argumento da função de tradução | Em vez disso, use literal de string. |
| 5085 | O uso de determinadas funções é desencorajado | Em vez disso, use a função alternativa aconselhada na mensagem. |
| 5087 | Problema de compatibilidade entre versões PHP | Siga as sugestões da mensagem e marque a opção [guia de migração](https://www.php.net/manual/en/migration81.php). |
| 5088 | Parâmetros opcionais encontrados após os necessários | Mova os parâmetros necessários após os opcionais. |
| 5089 | Visibilidade do método `final private` found | Alterar visibilidade do método de `final private` somente para `private`. |
| 5090 | Método mágico `__set_state` não está definido como `static` | Método mágico `__set_state` deve ser definido como `static`. |
| 5091 | Classe com `__toString()` método não herdado de `Stringable` interface | Adicionar `Stringable` interface para classe com `__toString()` método . |
| 5092 | `is_resource()` método usado para funções que agora retornam Objeto | Alterar `is_resource()` para `instanceof` Objeto. |
| 6001 | `jQuery.andSelf()` removido | Use `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` e `$.unbind` estão obsoletas | Use `$.on` e `$.off` em vez disso. |
| 6003 | O método jQuery para assinar o evento está obsoleto e não deve ser usado | Use `.on("event name", fn)` em vez de assinar esse evento. |
| 6003 | O método jQuery para acionar evento está obsoleto e não deve ser usado | Use `.trigger("event name")` em vez de acionar esse evento. |
| 6004 | jQuery `$.delegate` e `$.undelegate` estão obsoletas | Use `$.on` e `$.off` em vez disso. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) foi removido | Use (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`) em vez disso. |
| 6006 | `jQuery.size()` removido | Use `jQuery.length`. |
| 6007 | `jQuery.trim` está obsoleto | Use `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, tema &quot;inlite&quot;, tema &quot;móvel&quot;, tema &quot;moderno&quot;) é removido | Atualize o código para ser compatível com o tinymce5. |
| 6009 | `jQuery.isFunction()` está obsoleto | Na maioria dos casos, pode ser substituído por [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` está obsoleto | Substituir por uma verificação de tipo apropriada, como [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` está obsoleto | Em vez disso, use o método Array.isArray nativo. |
| 6009 | `jQuery.parseJSON()` está obsoleto | Para analisar cadeias de caracteres JSON, use o método JSON.parse nativo. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) está obsoleta | Em vez disso, use jQuery.expr.pseudos. |

{style=&quot;table-layout:auto&quot;}

## Avisos

### Código principal

Esses avisos são reportados quando há pequenas inconsistências na base de código principal.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 2004 | Incompatibilidade de versão de dependência do compositor | O problema indica que a versão de dependência do Composer no etalon e no projeto real é diferente. Atualizar dependência executando `composer update <package_name>`. |

{style=&quot;table-layout:auto&quot;}

### Código personalizado

Os avisos de código personalizado são gerados quando as referências ao código obsoleto são detectadas. Essas referências devem ser substituídas pelos pontos de extensão suportados. Preste atenção ao `@see` anotação de item obsoleto para recomendações. Esses erros são também relatados quando pequenas normas de codificação foram quebradas.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 1131 | Extensão do Adobe Commerce ``@deprecated`` classe | A classe estendida será removida em versões futuras. A herança não é uma maneira recomendada de estender a funcionalidade do Adobe Commerce. Atualizar código para usar uma classe marcada como `@api`. |
| 1132 | Importação do Adobe Commerce `@deprecated` classe | A classe estendida será removida em versões futuras. Considere usar a classe Adobe Commerce marcada como `@api` em vez disso. |
| 1133 | Carregamento do Adobe Commerce `@deprecated` classe | A classe estendida será removida em versões futuras. Considere usar a classe Adobe Commerce marcada como `@api` em vez disso. |
| 1134 | Uso do Adobe Commerce `@deprecated` classe | A classe estendida será removida em versões futuras. Considere usar a classe Adobe Commerce marcada como `@api` em vez disso. |
| 1234 | Uso do Adobe Commerce `@deprecated` constante | A constante obsoleta será removida em versões futuras. Considere usar uma constante marcada como `@api` ou uma constante privada na implementação. |
| 1235 | Substituição do Adobe Commerce `@deprecated` constante | A constante obsoleta será removida em versões futuras. Considere usar uma constante marcada como `@api` ou uma constante privada na implementação. |
| 1236 | Atribuição do Adobe Commerce `@deprecated` constante | A constante obsoleta será removida em versões futuras. Considere usar uma constante marcada como `@api` ou uma constante privada na implementação. |
| 1332 | Adobe Commerce importado `@deprecated` interface | A interface obsoleta será removida em versões futuras. Considere o uso de uma interface ou classe marcada como `@api` em vez disso. |
| 1334 | Adobe Commerce usado `@deprecated` interface | A interface obsoleta será removida em versões futuras. Considere o uso de uma interface ou classe marcada como `@api` em vez disso. |
| 1337 | Herdado do Adobe Commerce `@deprecated` interface | A interface obsoleta será removida em versões futuras. Considere remover a herança da interface, usando uma interface marcada como `@api` ou uma interface introduzida na implementação. |
| 1338 | Implementação do Adobe Commerce `@deprecated` interface | A interface obsoleta será removida em versões futuras. Considere remover a herança da interface, usando uma interface marcada como `@api` ou uma interface introduzida na implementação. |
| 1430 | Chame o método dataobject não declarado | Os métodos mágicos que não são declarados podem ser alterados. Considere confiar em métodos de interface. |
| 1439 | Chame o Adobe Commerce `@deprecated` método | O método obsoleto será removido nas versões futuras. Em vez disso, considere confiar em métodos declarados em interfaces de API. |
| 1534 | Uso do Adobe Commerce `@deprecated` propriedade | O método obsoleto será removido nas versões futuras. Em vez disso, considere confiar em métodos declarados em interfaces de API. |
| 1535 | Substituição do Adobe Commerce `@deprecated` propriedade | A propriedade obsoleta será removida em versões futuras. Considere confiar em métodos declarados em interfaces da API ou usar uma propriedade privada na implementação. |
| 1536 | Atribuição do Adobe Commerce `@deprecated` propriedade | O método obsoleto será removido nas versões futuras. Em vez disso, considere confiar em métodos declarados em interfaces de API. |
| 5006 | Os proxy e interceptores nunca devem ser explicitamente solicitados nos construtores | A classe original deve ser declarada como um tipo do parâmetro do construtor. A classe Interceptor/Proxy será passada pela implementação de injeção de dependência da estrutura. |
| 5074 | Uso de método obsoleto `getResource()` aos dados (salvar/carregar/excluir) detectados. | Em vez disso, use um repositório. |
| 5086 | A visibilidade não é declarada em uma constante | Declare a visibilidade em todas as constantes. |

{style=&quot;table-layout:auto&quot;}

### Esquema GraphQL

Os avisos do Esquema GraphQL são gerados quando os itens adicionais são adicionados ao esquema na nova versão. É recomendável revisar a implementação para ver se ela deve ser usada para solicitações.

| Código de erro | Descrição do erro | Ação sugerida |
| --- | --- | --- |
| 3206 | Valor padrão do argumento alterado | Se o query for usado na personalização, o valor do argumento pode ter de ser especificado explicitamente. |
| 3302 | Tipo adicionado à união | O tipo foi adicionado à união. Verifique o processamento de implementação do resultado do query que retorna esse tipo de união e garanta que ele seja capaz de lidar com o tipo adicionado. |
| 3304 | Campo de entrada opcional adicionado | Campo de entrada opcional adicionado. Verifique a implementação para garantir. |
| 3305 | Interface implementada adicionada | O campo pode aceitar/fornecer mais informações que podem ser consideradas na implementação. |
| 3306 | Valor adicionado ao enum | Um valor foi adicionado a um enum. Se os clientes contiverem uma declaração de alternância no valor do enum e não incluírem um caso padrão, essa alteração poderá causar comportamento inesperado. |
| 3308 | Argumento opcional adicionado | Se o query estiver usando um novo argumento na personalização, talvez seja necessário adicioná-lo à solicitação. |

{style=&quot;table-layout:auto&quot;}
