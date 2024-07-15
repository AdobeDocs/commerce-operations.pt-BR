---
title: Permissões de acesso a sistemas de arquivos
description: Veja como configurar o proprietário ou proprietários do sistema de arquivos do aplicativo Commerce para um sistema de desenvolvimento e produção.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Permissões de acesso a sistemas de arquivos

Esta seção discute como configurar o proprietário ou os proprietários do sistema de arquivos do Commerce para um sistema de desenvolvimento e produção. Antes de continuar, analise os conceitos discutidos em [Visão geral da propriedade e das permissões do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

Este tópico tem como foco os sistemas de desenvolvimento e produção do Commerce. Se você estiver instalando o Commerce, consulte [Definir propriedade e permissões de pré-instalação](../../installation/prerequisites/file-system/configure-permissions.md).

As seções a seguir discutem os requisitos para um ou dois proprietários de sistemas de arquivos. Isso significa que:

- **Um usuário** — Normalmente necessário em provedores de hospedagem compartilhados, que permitem acessar apenas um usuário no servidor. Esse usuário pode fazer logon, transferir arquivos usando FTP e também executa o servidor Web.

- **Dois usuários**—Recomendamos dois usuários se você executar o seu próprio servidor Commerce: um para transferir arquivos e executar utilitários de linha de comando, e um usuário separado para o software do servidor Web. Quando possível, isso é preferível porque é mais seguro.

  Em vez disso, você tem usuários separados:

   - O usuário do servidor Web, que executa o Administrador e a loja.

   - Um _usuário da linha de comando_, que é uma conta de usuário local que você pode usar para fazer logon no servidor. Esse usuário executa tarefas cron do Commerce e utilitários de linha de comando.

## Propriedade do sistema de arquivos de produção para hospedagem compartilhada (um usuário)

Para usar a configuração de um proprietário, você deve fazer logon no servidor do Commerce como o mesmo usuário que executa o servidor Web. Isso é típico para hospedagem compartilhada.

Como ter um proprietário de sistema de arquivos é menos seguro, recomendamos que você implante o Commerce em produção em um servidor privado em vez de em uma hospedagem compartilhada, se possível.

### Configurar um proprietário para modo padrão ou de desenvolvedor

No modo padrão ou de desenvolvedor, os seguintes diretórios devem ser graváveis pelo usuário:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Quaisquer outros recursos estáticos
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

É possível definir essas permissões usando a linha de comando ou um aplicativo do gerenciador de arquivos fornecido pelo seu provedor de hospedagem compartilhada.

### Configurar um proprietário para o modo de produção

Quando estiver pronto para implantar seu site na produção, você deverá remover o acesso de gravação dos arquivos nos seguintes diretórios para melhorar a segurança:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Quaisquer outros recursos estáticos
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Para atualizar componentes, instalar novos componentes ou atualizar o software Commerce, todos os diretórios anteriores devem ser leitura-gravação.

#### Tornar arquivos de código e diretórios somente leitura

Para remover permissões de gravação em arquivos e diretórios do grupo do usuário do servidor Web:

1. Faça logon no servidor do Commerce.

1. Altere para o diretório de instalação do Commerce.

1. Alterar para modo de produção.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Remova as permissões de gravação para os seguintes diretórios.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Torne a ferramenta de linha de comando executável.

   ```bash
   chmod u+x bin/magento
   ```

#### Tornar arquivos de código e diretórios graváveis

Para tornar arquivos e diretórios graváveis para que você possa atualizar componentes e o software Commerce:

1. Faça logon no servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Digite os seguintes comandos:

   ```bash
   chmod -R u+w .
   ```

### Opcionalmente, definir `magento_umask`

Consulte [Definir opcionalmente uma máscara](../../installation/next-steps/set-umask.md) no _Guia de instalação_.

## Propriedade do sistema de arquivos de produção para hospedagem privada (dois usuários)

Se você usar seu próprio servidor (incluindo a configuração do servidor privado de um provedor de hospedagem), há dois usuários:

- O **usuário do servidor Web**, que executa o Administrador e a loja.

  Os sistemas Linux normalmente não fornecem um shell para esse usuário; você não pode fazer login no servidor Commerce como, ou mudar para, o usuário do servidor Web.

- O **usuário da linha de comando**, ao qual você faz logon no servidor do Commerce como ou alterna para.

  O Commerce usa esse usuário para executar comandos CLI e cron.

  >[!INFO]
  >
  >O usuário da linha de comando também é chamado de _proprietário do sistema de arquivos_.

Como esses usuários exigem acesso aos mesmos arquivos, recomendamos que você crie um [grupo compartilhado](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) ao qual ambos pertencem. Os procedimentos a seguir presumem que você já tenha feito isso.

Consulte uma das seguintes seções:

- Dois proprietários de sistema de arquivos no modo de desenvolvedor ou padrão
- Dois proprietários de sistemas de arquivos no modo de produção

### Configurar dois proprietários para o modo padrão ou de desenvolvedor

Os arquivos nos diretórios a seguir devem ser graváveis pelos usuários no modo de desenvolvedor e no modo padrão:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Defina o bit [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) nos diretórios para que as permissões sempre herdem do diretório pai.

>[!INFO]
>
>`setgid` aplica-se somente a diretórios, _não_ a arquivos.

Além disso, os diretórios devem ser graváveis pelo grupo de servidores Web. Como o conteúdo pode existir nesses diretórios, adicione as permissões recursivamente.

#### Definir permissões e `setgid`

Para definir `setgid` e permissões para modo de desenvolvedor:

1. Faça logon no servidor do Commerce como ou alterne para o proprietário do sistema de arquivos.
1. Digite os seguintes comandos na ordem mostrada:

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Dois proprietários de sistemas de arquivos no modo de produção

Quando estiver pronto para implantar seu site na produção, você deverá remover o acesso de gravação dos arquivos nos seguintes diretórios para melhorar a segurança:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Quaisquer outros recursos estáticos
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Tornar arquivos de código e diretórios somente leitura

Para remover permissões graváveis para arquivos e diretórios do grupo do usuário do servidor Web:

1. Faça logon no servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Como proprietário do sistema de arquivos, digite o seguinte comando para alterar para o modo de produção:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Digite o seguinte comando como um usuário com `root` privilégios:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Tornar arquivos de código e diretórios graváveis

Para tornar arquivos e diretórios graváveis para que você possa atualizar componentes e o software Commerce:

1. Faça logon no servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
