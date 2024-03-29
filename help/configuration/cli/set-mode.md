---
title: Definir o modo de operação
description: Leia sobre como configurar os modos de operação do Adobe Commerce.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Definir o modo de operação

{{file-system-owner}}

Para melhorar a segurança e a facilidade de uso, adicionamos um comando que alterna [modos de aplicação](../bootstrap/application-modes.md) do desenvolvedor para a produção e vice-versa.

O modo de produção tem melhor desempenho porque os arquivos de exibição estáticos são preenchidos no `pub/static` e devido à compilação de código.

>[!INFO]
>
>Na versão 2.0.6 e posterior, o Commerce não define explicitamente as permissões de arquivo ou diretório ao alternar entre os modos padrão, de desenvolvimento e de produção. Ao contrário de outros modos, os modos de desenvolvedor e de produção são definidos no `env.php` arquivo. O Adobe Commerce na infraestrutura em nuvem oferece suporte apenas aos modos de produção e manutenção.
>
>Consulte [Propriedade e permissões de comércio no desenvolvimento e na produção](../deployment/file-system-permissions.md).

Quando você muda para o modo de desenvolvedor ou de produção, limpamos o conteúdo dos seguintes diretórios:

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
>Por padrão, o Commerce usa a variável `var` diretórios para armazenar o cache, logs e código compilado. Você pode personalizar esse diretório, mas nesse guia, presume-se que seja `var`.

## Exibir o modo atual

A maneira mais fácil de fazer isso é executar esse comando como a [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md). Se você compartilhou uma hospedagem, esse é o usuário que seu provedor lhe dá para fazer logon no servidor. Se você tiver um servidor privado, ele normalmente é uma conta de usuário local no servidor do Commerce.

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

- **`--skip-compilation`** é um parâmetro opcional que pode ser usado para ignorar [compilação de código](../cli/code-compiler.md) ao alterar para o modo de produção.

Os exemplos a seguir.

### Alterar para modo de produção

```bash
bin/magento deploy:mode:set production
```

Mensagens semelhantes a esta são exibidas:

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
Successfully processed LESS and/or Sass files
CSS deployment complete
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

### Alterar para modo de desenvolvedor

Ao mudar do modo de produção para o modo de desenvolvedor, você deve limpar as classes geradas e as entidades do Gerenciador de objetos, como proxies, para evitar erros inesperados. Depois de fazer isso, você pode alterar os modos. Use as seguintes etapas:

1. Se você estiver alterando do modo de produção para o modo de desenvolvedor, exclua o conteúdo da variável `generated/code` e `generated/metadata` diretórios:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Defina o modo:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   A seguinte mensagem é exibida:

   ```terminal
   Enabled developer mode.
   ```

### Alterar para modo padrão

```bash
bin/magento deploy:mode:set default
```

A seguinte mensagem é exibida:

```terminal
Enabled default mode.
```

### Execute comandos da CLI de qualquer lugar

[Execute comandos da CLI de qualquer lugar](../cli/config-cli.md#config-install-cli-first).

Se você não tiver adicionado `<Commerce-install-directory>/bin` ao seu sistema `PATH`, pode ocorrer um erro ao executar o comando sozinho.
