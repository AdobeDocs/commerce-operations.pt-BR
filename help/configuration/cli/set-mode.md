---
title: Definir o modo de operação
description: Leia sobre como configurar os modos de operação do Adobe Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# Definir o modo de operação

{{file-system-owner}}

Para melhorar a segurança e a facilidade de uso, adicionamos um comando que alterna [modos de aplicativo](../bootstrap/application-modes.md) do desenvolvedor à produção e vice-versa.

O modo de produção tem melhor desempenho, pois os arquivos de visualização estáticos são preenchidos no `pub/static` e devido à compilação de código.

>[!INFO]
>
>Na versão 2.0.6 e posterior, o Commerce não define explicitamente as permissões de arquivo ou diretório quando você alternar entre os modos padrão, desenvolver e produção. Diferente de outros modos, os modos de desenvolvimento e produção são definidos na variável `env.php` arquivo. A infraestrutura em nuvem do Adobe Commerce oferece suporte somente aos modos de produção e manutenção.
>
>Consulte [Propriedade comercial e permissões em desenvolvimento e produção](../deployment/file-system-permissions.md).

Quando você muda para o modo desenvolvedor ou de produção, limpamos o conteúdo dos seguintes diretórios:

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Exceções:

- `.htaccess` os arquivos não são removidos
- `pub/static` contém um arquivo que especifica a versão do conteúdo estático; este arquivo não foi removido

>[!INFO]
>
>Por padrão, o Commerce usa a variável `var` diretórios para armazenar o cache, registros e código compilado. Você pode personalizar este diretório, mas neste guia assume-se que seja `var`.

## Exibir o modo atual

A maneira mais fácil de fazer isso é executar esse comando como o [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html). Caso tenha compartilhado a hospedagem, esse é o usuário que seu provedor oferece para fazer logon no servidor. Se você tiver um servidor privado, normalmente é uma conta de usuário local no servidor do Commerce.

Uso do comando:

```bash
bin/magento deploy:mode:show
```

Uma mensagem semelhante à seguinte é exibida:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

em que:

- **`{mode}`** pode ser `default`, `developer`ou `production`

## Alterar modos

Uso do comando:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

em que:

- **`{mode}`** é obrigatório; pode ser `developer` ou `production`

- **`--skip-compilation`** é um parâmetro opcional que pode ser usado para ignorar [compilação de código](../cli/code-compiler.md) quando você muda para o modo de produção.

Seguem-se exemplos.

### Alterar para modo de produção

```bash
bin/magento deploy:mode:set production
```

Mensagens semelhantes à seguinte exibição:

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or [Sass](https://glossary.magento.com/sass) files
[CSS](https://glossary.magento.com/css) deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### Alterar para o modo de desenvolvedor

Quando você altera da produção para o modo desenvolvedor, deve limpar as classes geradas e as entidades do Gerenciador de objetos, como proxies, para evitar erros inesperados. Depois de fazer isso, você pode alterar os modos. Use as seguintes etapas:

1. Se você estiver mudando do modo de produção para o modo desenvolvedor, exclua o conteúdo do `generated/code` e `generated/metadata` diretórios:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Defina o modo :

   ```bash
   bin/magento deploy:mode:set developer
   ```

   A seguinte mensagem é exibida:

   ```terminal
   Enabled developer mode.
   ```

### Alterar para o modo padrão

```bash
bin/magento deploy:mode:set default
```

A seguinte mensagem é exibida:

```terminal
Enabled default mode.
```

### Executar comandos da CLI de qualquer lugar

[Executar comandos da CLI de qualquer lugar](../cli/config-cli.md#config-install-cli-first).

Se você não tiver adicionado `<Commerce-install-directory>/bin` ao seu sistema `PATH`, é possível esperar um erro ao executar o comando sozinho.
