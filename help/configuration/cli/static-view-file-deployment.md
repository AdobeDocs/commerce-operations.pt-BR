---
title: Implantar arquivos de exibição estáticos
description: Saiba como gravar arquivos estáticos no sistema de arquivos do Commerce durante o modo de produção.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 0a72bc492dfec0a9014a518282a97ab21e59f96d
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# Implantar arquivos de exibição estáticos

{{file-system-owner}}

O comando de implantação de arquivos de exibição estática permite gravar arquivos estáticos no sistema de arquivos do Commerce quando o software do Commerce está definido para [modo de produção](../bootstrap/application-modes.md#production-mode).

O termo _arquivo de exibição estático_ refere-se ao seguinte:

- &quot;Estático&quot; significa que ele pode ser armazenado em cache para um site (ou seja, o arquivo não é gerado dinamicamente). Os exemplos incluem imagens e CSS gerados de LESS.
- &quot;Visualização&quot; refere-se à camada de apresentação (do MVC).

Os arquivos de exibição estáticos estão localizados no diretório `<magento_root>/pub/static`, e alguns também são armazenados em cache no diretório `<magento_root>/var/view_preprocessed`.

A implantação de arquivos de visualização estática é afetada pelos modos de aplicativo da seguinte maneira:

- Modos [Padrão](../bootstrap/application-modes.md#default-mode) e [desenvolvedor](../bootstrap/application-modes.md#developer-mode): o Commerce os gera sob demanda, mas o restante é armazenado em cache em um arquivo para acelerar o acesso.
- Modo de [Produção](../bootstrap/application-modes.md#production-mode): os arquivos estáticos são _não_ gerados ou armazenados em cache.

Você deve gravar arquivos de exibição estáticos no sistema de arquivos do Commerce manualmente usando o comando discutido neste tópico; depois disso, você pode restringir permissões para limitar suas vulnerabilidades e impedir a substituição acidental ou mal-intencionada de arquivos.

>[!WARNING]
>
>_Somente modo de desenvolvedor_: quando você instala ou habilita um novo módulo, ele pode carregar novos JavaScript, CSS, layouts e assim por diante. Para evitar problemas com arquivos estáticos, você deve limpar os arquivos antigos para garantir que obtenha todas as alterações para o novo módulo. Você pode limpar arquivos de visualização estáticos gerados de várias maneiras. Consulte [Tópico sobre cache de arquivos estáticos limpos para obter detalhes](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) para obter mais informações.

**Para implantar arquivos de exibição estáticos**:

1. Faça logon no servidor Commerce como ou [alterne para o proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Excluir o conteúdo de `<magento_root>/pub/static`, exceto o arquivo `.htaccess`. Não exclua este arquivo.
1. Execute a ferramenta de implantação de arquivos de exibição estática `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Se você habilitar a mesclagem de arquivos de exibição estática no Administrador, o sistema de diretório `pub/static` deverá ser gravável.

   Opções de comando:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

A tabela a seguir explica os parâmetros e valores desse comando.

| Opção | Descrição | Obrigatório? |
| ------ | ----------- | --------- |
| `<languages>` | Lista separada por espaços de códigos de linguagem [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) para os quais serão gerados arquivos de exibição estáticos. (O padrão é `en_US`.)<br>Localizar a lista executando: `bin/magento info:language:list` | Não |
| `--language (-l)` | Gera arquivos somente para os idiomas especificados. O padrão, sem nenhuma opção especificada, é gerar arquivos para todos os códigos de idioma ISO-639. Você pode especificar o nome de um código de idioma por vez. O valor padrão é **all**.<br>Por exemplo: `--language en_US --language es_ES` | Não |
| `--exclude-language` | Gerar arquivos para os códigos de idioma especificados. O padrão, sem nenhuma opção especificada, é não excluir nada. Você pode especificar o nome de um código de idioma ou uma lista de códigos de idioma separada por vírgulas. O valor padrão é **nenhum**. | Não |
| `--theme <theme>` | Temas para os quais implantar conteúdo estático. O valor padrão é **all**.<br>Por exemplo: `--theme Magento/blank --theme Magento/luma` | Não |
| `--exclude-theme <theme>` | Temas a serem excluídos ao implantar conteúdo estático. O valor padrão é **nenhum**.<br>Por exemplo, `--exclude-theme Magento/blank` | Não |
| `--area (-a)` | Gera arquivos somente para as áreas especificadas. O padrão, sem opção especificada, é gerar arquivos para todas as áreas. Os valores válidos são `adminhtml` e `frontend`. O valor padrão é **all**.<br>Por exemplo: `--area adminhtml` | Não |
| `--exclude-area` | Não gerar arquivos para as áreas especificadas. O padrão, sem nenhuma opção especificada, é não excluir nada. O valor padrão é **nenhum**. | Não |
| `--jobs (-j)` | Habilite o [processamento paralelo](manage-indexers.md#reindexing-in-parallel-mode) usando o número especificado de trabalhos. O padrão é 0 (não executar em processos paralelos). O valor padrão é **0**. | Não |
| `--symlink-locale` | Crie symlinks para os arquivos dessas localidades, que são transmitidos para implantação, mas não têm personalizações. | Não |
| `--content-version=CONTENT-VERSION` | A versão personalizada do conteúdo estático pode ser usada se a implantação estiver em execução em vários nós para garantir que a versão do conteúdo estático seja idêntica e o armazenamento em cache funcione corretamente. | Não |
| `--no-javascript` | Não implantar arquivos do JavaScript | Não |
| `--no-css` | Não implante arquivos CSS. | Não |
| `--no-less` | Não implante MENOS arquivos. | Não |
| `--no-images` | Não implantar imagens. | Não |
| `--no-fonts` | Não implantar arquivos de fonte. | Não |
| `--no-html` | Não implante arquivos HTML. | Não |
| `--no-misc` | Não implante outros tipos de arquivos: MD, JBF, CSV, JSON, TXT, HTC, SWF | Não |
| `--no-html-minify` | Não minifique arquivos HTML. | Não |
| `-s <quick\|standard\|compact>` | Definir a estratégia de implantação. Use essas opções somente se você tiver mais de um local.<ul><li>Use a [estratégia rápida](static-view-file-strategy.md#quick-strategy) para minimizar o tempo de implantação. Esta é a opção de comando padrão, se não for especificada.</li><li>Use a [estratégia padrão](static-view-file-strategy.md#standard-strategy) para implantar todos os arquivos de exibição estáticos para todos os pacotes.</li><li>Use a [estratégia compacta](static-view-file-strategy.md#compact-strategy) para conservar o espaço em disco no servidor.</li></ul> | Não |
| `--no-parent` | Não gerar arquivos para os temas principais do tema atual. É altamente recomendável usar esse sinalizador se você não usar explicitamente o tema principal do tema atual que está tentando implantar. Isso aumenta significativamente a velocidade do processo. Esse sinalizador está disponível no Commerce 2.4.2 | Não |
| `--force (-f)` | Implante arquivos em qualquer modo. (por padrão, a ferramenta de implantação de conteúdo estático pode ser executada somente no modo de produção. Use essa opção para executá-la no modo padrão ou de desenvolvedor). | Não |

>[!INFO]
>
>Se você especificar valores para `<languages>` e `--language`, `<languages>` tem prioridade.

## Exemplos

A seguir estão alguns exemplos de comandos.

### Excluir um tema e minificação de HTML

O comando a seguir implanta conteúdo estático para o idioma inglês dos EUA (`en_US`), exclui o tema Luma fornecido com o Commerce e não minifica arquivos HTML.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Saída de exemplo:

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

O comando a seguir implanta somente o JavaScript, com 4 tarefas, com uma estratégia de implantação padrão:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

O comando a seguir implanta somente CSS e MENOS com 3 tarefas e uma estratégia de implantação rápida:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Geração de arquivos de visualização estáticos para um tema e uma área

O comando a seguir gera arquivos de exibição estáticos para todos os idiomas, somente a área de front-end e somente o tema do Commerce Luma, sem gerar fontes:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Saída de exemplo:

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Implantar arquivos de visualização estáticos sem instalar o Commerce

Você pode executar o processo de implantação em um ambiente separado, não relacionado à produção, para evitar processos de criação em máquinas de produção confidenciais.

Para fazer isso, siga estas etapas:

1. Execute [`bin/magento app:config:dump`](../cli/export-configuration.md) para exportar a configuração do seu sistema de produção.
1. Copie os arquivos exportados para a base de código de não produção.
1. Implantar arquivos de exibição estáticos: `bin/magento setup:static-content:deploy`

## Solução de problemas da ferramenta de implantação de arquivos de visualização estática

[Instale o software do Commerce primeiro](../../installation/overview.md); caso contrário, você não poderá executar a ferramenta de implantação de arquivos de exibição estáticos.

**Sintoma**: o seguinte erro é exibido quando você executa a ferramenta de implantação de arquivos de exibição estática:

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Solução**:

Use as seguintes etapas:

1. Instale o software Commerce usando a [linha de comando](../../installation/composer.md).
1. Faça logon no servidor de aplicativos como, ou [alterne para](../../installation/prerequisites/file-system/overview.md), o proprietário do sistema de arquivos.
1. Exclua o conteúdo do diretório `<app_root>/pub/static`, exceto pelo arquivo `.htaccess`. Não exclua este arquivo.
1. Implantar arquivos de exibição estáticos: `bin/magento setup:static-content:deploy`

## Dica para desenvolvedores personalizarem a ferramenta de implantação de conteúdo estático

Ao criar uma implementação personalizada da ferramenta de implantação de conteúdo estático, use somente a gravação de arquivo atômico para arquivos que devem estar disponíveis no cliente. Se você usar gravação de arquivo não atômico, esses arquivos poderão ser carregados no cliente com conteúdo parcial.

Uma das opções para torná-lo atômico é gravar em arquivos armazenados em um diretório temporário e copiá-los ou movê-los para o diretório de destino (de onde são carregados para o cliente) após a gravação terminar. Para detalhes sobre a gravação em arquivos, veja [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
