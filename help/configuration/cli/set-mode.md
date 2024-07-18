---
title: Definir o modo de operação
description: Leia sobre como configurar os modos de operação do Adobe Commerce.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Definir o modo de operação

{{file-system-owner}}

Para melhorar a segurança e a facilidade de uso, adicionamos um comando que alterna [modos de aplicativo](../bootstrap/application-modes.md) de desenvolvedor para produção e vice-versa.

O modo de produção tem melhor desempenho porque os arquivos de exibição estáticos estão preenchidos no diretório `pub/static` e devido à compilação de código.

>[!INFO]
>
>Na versão 2.0.6 e posterior, o Commerce não define explicitamente as permissões de arquivo ou diretório ao alternar entre os modos padrão, de desenvolvimento e de produção. Ao contrário de outros modos, os modos de desenvolvedor e de produção são definidos no arquivo `env.php`. O Adobe Commerce na infraestrutura em nuvem oferece suporte apenas aos modos de produção e manutenção.
>
>Consulte [Propriedade e permissões do Commerce no desenvolvimento e na produção](../deployment/file-system-permissions.md).

Quando você muda para o modo de desenvolvedor ou de produção, limpamos o conteúdo dos seguintes diretórios:

```
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Exceções:

- `.htaccess` arquivos não foram removidos
- `pub/static` contém um arquivo que especifica a versão do conteúdo estático; este arquivo não foi removido

>[!INFO]
>
>Por padrão, o Commerce usa os diretórios `var` para armazenar o cache, os logs e o código compilado. Você pode personalizar este diretório, mas neste guia, presume-se que seja `var`.

## Exibir o modo atual

A maneira mais fácil de fazer isso é executar este comando como o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md). Se você compartilhou uma hospedagem, esse é o usuário que seu provedor lhe dá para fazer logon no servidor. Se você tiver um servidor privado, ele normalmente é uma conta de usuário local no servidor do Commerce.

Uso do comando:

```bash
bin/magento deploy:mode:show
```

Uma mensagem semelhante à seguinte é exibida:

```
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

em que:

- **`{mode}`** pode ser `default`, `developer` ou `production`

## Alterar modos

Uso do comando:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

em que:

- **`{mode}`** é obrigatório; pode ser `developer` ou `production`

- **`--skip-compilation`** é um parâmetro opcional que você pode usar para ignorar a [compilação de código](../cli/code-compiler.md) quando mudar para o modo de produção.

Os exemplos a seguir.

### Alterar para modo de produção

```bash
bin/magento deploy:mode:set production
```

Mensagens semelhantes a esta são exibidas:

```
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

1. Se você estiver alterando do modo de produção para o modo de desenvolvedor, exclua o conteúdo dos diretórios `generated/code` e `generated/metadata`:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Defina o modo:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   A seguinte mensagem é exibida:

   ```
   Enabled developer mode.
   ```

### Alterar para modo padrão

```bash
bin/magento deploy:mode:set default
```

A seguinte mensagem é exibida:

```
Enabled default mode.
```

### Execute comandos da CLI de qualquer lugar

[Execute comandos CLI de qualquer lugar](../cli/config-cli.md#config-install-cli-first).

Se você não tiver adicionado `<Commerce-install-directory>/bin` ao sistema `PATH`, poderá esperar um erro ao executar o comando sozinho.
