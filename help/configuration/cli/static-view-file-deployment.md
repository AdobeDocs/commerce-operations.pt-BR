---
title: Implantar arquivos de visualização estáticos
description: Saiba como gravar arquivos estáticos no sistema de arquivos do Commerce durante o modo de produção.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Implantar arquivos de visualização estáticos

{{file-system-owner}}

O comando de implantação de arquivos de visualização estática permite gravar arquivos estáticos no sistema de arquivos do Commerce quando o software Commerce estiver definido para [modo de produção](../bootstrap/application-modes.md#production-mode).

O termo _arquivo de visualização estática_ refere-se ao seguinte:

- &quot;Estático&quot; significa que pode ser armazenado em cache para um site (ou seja, o arquivo não é gerado dinamicamente). Os exemplos incluem imagens e CSS gerado pelo LESS.
- &quot;Exibir&quot; refere-se à camada de apresentação (de MVC).

Os arquivos de visualização estáticos estão localizados na variável `<magento_root>/pub/static` e alguns são armazenados em cache no `<magento_root>/var/view_preprocessed` também.

A implantação de arquivos de visualização estáticos é afetada pelos modos de aplicativo, como a seguir:

- [Padrão](../bootstrap/application-modes.md#default-mode) e [desenvolvedor](../bootstrap/application-modes.md#developer-mode) modos: O comércio os gera sob demanda, mas o restante é armazenado em cache em um arquivo para acelerar o acesso.
- [Produção](../bootstrap/application-modes.md#production-mode) modo: Os arquivos estáticos são _not_ gerado ou armazenado em cache.

Você deve gravar arquivos de visualização estáticos no sistema de arquivos do Commerce manualmente usando o comando discutido neste tópico; depois disso, você poderá restringir permissões para limitar suas vulnerabilidades e impedir a substituição acidental ou mal-intencionada de arquivos.

>[!WARNING]
>
>_Somente no modo Desenvolvedor_: Ao instalar ou habilitar um novo módulo, ele pode carregar novos JavaScript, CSS, layouts e assim por diante. Para evitar problemas com arquivos estáticos, é necessário limpar os arquivos antigos para garantir que você obtenha todas as alterações para o novo módulo. Você pode limpar arquivos de visualização estática gerados de várias maneiras. Consulte [Tópico de cache de arquivos estáticos limpos para obter detalhes](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) para obter mais informações.

**Para implantar arquivos de visualização estáticos**:

1. Faça logon no servidor do Commerce como ou [mudar para o proprietário do sistema de ficheiros](../../installation/prerequisites/file-system/overview.md).
1. Excluir o conteúdo de `<magento_root>/pub/static`, exceto para o `.htaccess` arquivo. Não exclua este arquivo.
1. Execute a ferramenta de implantação de arquivos de visualização estáticos `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Se você ativar a mesclagem de arquivos de exibição estática no Admin, a variável `pub/static` o sistema de diretório deve ser gravável.

   Opções de comando:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

A tabela a seguir explica os parâmetros e valores desse comando.

| Opção | Descrição | Obrigatório? |
| ------ | ----------- | --------- |
| `<languages>` | Lista separada por espaços de [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) códigos de idioma para os quais os arquivos de visualização estática serão enviados. (O padrão é `en_US`.)<br>Encontre a lista executando: `bin/magento info:language:list` | Não |
| `--language (-l)` | Gere arquivos somente para os idiomas especificados. O padrão, sem opção especificada, é gerar arquivos para todos os códigos de idioma ISO-639. Você pode especificar o nome de um código de idioma por vez. O valor padrão é **all**.<br>Por exemplo: `--language en_US --language es_ES` | Não |
| `--exclude-language` | Gere arquivos para os códigos de idioma especificados. O padrão, sem opção especificada, é não excluir nada. Você pode especificar o nome de um código de idioma ou uma lista separada por vírgulas de códigos de idioma. O valor padrão é **nenhum**. | Não |
| `--theme <theme>` | Temas para os quais implantar conteúdo estático. O valor padrão é **all**.<br>Por exemplo: `--theme Magento/blank --theme Magento/luma` | Não |
| `--exclude-theme <theme>` | Temas a serem excluídos ao implantar conteúdo estático. O valor padrão é **nenhum**.<br>Por exemplo, `--exclude-theme Magento/blank` | Não |
| `--area (-a)` | Gere arquivos somente para as áreas especificadas. O padrão, sem opção especificada, é gerar arquivos para todas as áreas. Os valores válidos são `adminhtml` e `frontend`. O valor padrão é **all**.<br>Por exemplo: `--area adminhtml` | Não |
| `--exclude-area` | Não gerar arquivos para as áreas especificadas. O padrão, sem opção especificada, é não excluir nada. O valor padrão é **nenhum**. | Não |
| `--jobs (-j)` | Habilite o processamento paralelo usando o número especificado de tarefas. O padrão é 0 (não executar em processos paralelos). O valor padrão é **0**. | Não |
| `--symlink-locale` | Crie links simbólicos para os arquivos dessas localidades, que são passados para implantação, mas não têm personalizações. | Não |
| `--content-version=CONTENT-VERSION` | A versão personalizada do conteúdo estático pode ser usada se a implantação for executada em vários nós para garantir que a versão do conteúdo estático seja idêntica e o armazenamento em cache funcione corretamente. | Não |
| `--no-javascript` | Não implante arquivos JavaScript | Não |
| `--no-css` | Não implante arquivos CSS. | Não |
| `--no-less` | Não implante arquivos MENOS. | Não |
| `--no-images` | Não implante imagens. | Não |
| `--no-fonts` | Não implante arquivos de fonte. | Não |
| `--no-html` | Não implante arquivos HTML. | Não |
| `--no-misc` | Não implante outros tipos de arquivos: MD, JBF, CSV, JSON, TXT, HTC, SWF | Não |
| `--no-html-minify` | Não minificar arquivos HTML. | Não |
| `-s <quick\|standard\|compact>` | Defina a estratégia de implantação. Use essas opções somente se tiver mais de um local.<ul><li>Use o [estratégia rápida](static-view-file-strategy.md#quick-strategy) para minimizar o tempo de implantação. Essa é a opção de comando padrão, se não for especificada.</li><li>Use o [estratégia-padrão](static-view-file-strategy.md#standard-strategy) para implantar todos os arquivos de visualização estática para todos os pacotes.</li><li>Use o [estratégia compacta](static-view-file-strategy.md#compact-strategy) para conservar espaço em disco no servidor.</li></ul> | Não |
| `--no-parent` | Não gere arquivos para os temas principais do tema atual. É altamente recomendável usar esse sinalizador se você não usar explicitamente o tema pai do tema atual que está tentando implantar. Isso aumenta significativamente a velocidade do processo. Este sinalizador está disponível no Commerce 2.4.2 | Não |
| `--force (-f)` | Implante arquivos em qualquer modo. (por padrão, a ferramenta de implantação de conteúdo estático pode ser executada somente no modo de produção. Use essa opção para executá-la no modo padrão ou desenvolvedor). | Não |

>[!INFO]
>
>Se você especificar valores para ambos `<languages>` e `--language`, `<languages>` tem precedência.

## Exemplos

A seguir estão alguns exemplos de comandos.

### Excluir um tema e HTML minificação

O comando a seguir implanta conteúdo estático para inglês americano (`en_US`), exclui o tema Luma fornecido com Comércio e não minimiza arquivos HTML.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Exemplo de saída:

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

O comando a seguir implanta somente CSS e LESS com 3 tarefas e uma estratégia de implantação rápida:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Geração de arquivos de visualização estáticos para um tema e uma área

O comando a seguir gera arquivos de visualização estáticos para todos os idiomas, somente a área de primeiro plano, somente o tema do Commerce Luma, sem gerar fontes:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Exemplo de saída:

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

Para fazer isso, execute as seguintes etapas:

1. Executar [`bin/magento app:config:dump`](../cli/export-configuration.md) para exportar a configuração do seu sistema de produção.
1. Copie os arquivos exportados para a base de código de não produção.
1. Implantar arquivos de visualização estáticos: `bin/magento setup:static-content:deploy`

## Solução de problemas da ferramenta de implantação de arquivos de visualização estáticos

[Instale o software Commerce primeiro](../../installation/overview.md); caso contrário, não será possível executar a ferramenta de implantação de arquivos de visualização estáticos.

**Sintoma**: O seguinte erro é exibido quando você executa a ferramenta de implantação de arquivos de visualização estáticos:

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Solução**:

Use as seguintes etapas:

1. Instale o software Commerce usando o [linha de comando](../../installation/composer.md).
1. Faça logon no servidor de aplicativos como ou [alternar para](../../installation/prerequisites/file-system/overview.md), o proprietário do sistema de arquivos.
1. Excluir o conteúdo de `<app_root>/pub/static` , exceto para o `.htaccess` arquivo. Não exclua este arquivo.
1. Implantar arquivos de visualização estáticos: `bin/magento setup:static-content:deploy`

## Dica para desenvolvedores personalizarem a ferramenta de implantação de conteúdo estático

Ao criar uma implementação personalizada da ferramenta de implantação de conteúdo estático, use apenas a gravação de arquivo atômico para arquivos que devem estar disponíveis no cliente. Se você usar a gravação de arquivos não atômicos, esses arquivos poderão ser carregados no cliente com conteúdo parcial.

Uma das opções para torná-la atômica é gravar em arquivos armazenados em um diretório temporário e copiá-los ou movê-los para o diretório de destino (de onde são carregados para o cliente) após o término da gravação. Para obter detalhes sobre como gravar em arquivos, consulte [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
