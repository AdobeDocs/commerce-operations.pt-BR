---
title: Permissões de acesso aos sistemas de arquivos
description: Veja como configurar o proprietário ou proprietários do sistema de arquivos do aplicativo Commerce para um sistema de desenvolvimento e produção.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# Permissões de acesso aos sistemas de arquivos

Esta seção discute como configurar o proprietário ou proprietários do sistema de arquivos do Commerce para um sistema de desenvolvimento e produção. Antes de continuar, analise os conceitos discutidos em [Visão geral da propriedade e permissões do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

Este tópico foca em Desenvolvimento de comércio e sistemas de produção. Se você estiver instalando o Commerce, consulte [Definir a propriedade e as permissões da pré-instalação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

As seções a seguir discutem os requisitos de um ou dois proprietários do sistema de arquivos. Isso significa:

- **Um usuário**—Normalmente, é necessário em provedores de hospedagem compartilhada, que permitem acessar somente um usuário no servidor. Esse usuário pode fazer logon, transferir arquivos usando FTP e esse usuário também executa o servidor da Web.

- **Dois usuários**—Recomendamos dois usuários se você executar seu próprio servidor do Commerce: um para transferir arquivos e executar utilitários de linha de comando e um usuário separado para o software do servidor da Web. Sempre que possível, isso é preferível, pois é mais seguro.

   Em vez disso, você tem usuários separados:

   - O usuário do servidor da Web, que executa o Admin e a vitrine.

   - A _usuário da linha de comando_, que é uma conta de usuário local que pode ser usada para fazer logon no servidor. Este usuário executa os trabalhos do Commerce cron e os utilitários de linha de comando.

## Propriedade do sistema de arquivos de produção para hospedagem compartilhada (um usuário)

Para usar a configuração de um proprietário, você deve fazer logon no seu servidor do Commerce como o mesmo usuário que executa o servidor da Web. Isso é típico para hospedagem compartilhada.

Como ter um proprietário de sistema de arquivos é menos seguro, recomendamos que você implante o Commerce na produção em um servidor privado, em vez de na hospedagem compartilhada, se possível.

### Configurar um proprietário para o modo padrão ou de desenvolvedor

No modo padrão ou desenvolvedor, os seguintes diretórios devem ser graváveis pelo usuário:

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

Quando estiver pronto para implantar seu site na produção, você deve remover o acesso de gravação dos arquivos nos seguintes diretórios para melhorar a segurança:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Quaisquer outros recursos estáticos
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Para atualizar componentes, instalar novos componentes ou atualizar o software Commerce, todos os diretórios anteriores devem ser leitura e gravação.

#### Tornar arquivos de código e diretórios somente leitura

Para remover permissões de gravação de arquivos e diretórios do grupo de usuários do servidor da Web:

1. Faça logon no seu servidor do Commerce.

1. Altere para o diretório de instalação do Commerce.

1. Altere para o modo de produção.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Remova as permissões de gravação nos seguintes diretórios.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Tornar a ferramenta de linha de comando executável.

   ```bash
   chmod u+x bin/magento
   ```

#### Tornar arquivos de código e diretórios graváveis

Para tornar os arquivos e diretórios graváveis, para que você possa atualizar os componentes e atualizar o software Commerce:

1. Faça logon no seu servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Insira os seguintes comandos:

   ```bash
   chmod -R u+w .
   ```

### Opcionalmente definida `magento_umask`

Consulte [Opcionalmente, defina uma máscara](https://devdocs.magento.com/guides/v2.4/install-gde/install/post-install-umask.html) no _Guia de instalação_.

## Propriedade do sistema de arquivos de produção para hospedagem privada (dois usuários)

Se você usar seu próprio servidor (incluindo a configuração de servidor privado de um provedor de hospedagem), haverá dois usuários:

- O **usuário do servidor da web**, que executa o Admin e a loja.

   Os sistemas Linux normalmente não fornecem um shell para este usuário; não é possível fazer logon no servidor do Commerce como usuário do servidor da Web ou alterná-lo para ele.

- O **usuário da linha de comando**, que você faz logon no servidor do Commerce como ou alternar para .

   O Commerce usa esse usuário para executar comandos CLI e cron.

   >[!INFO]
   >
   >O usuário da linha de comando também é conhecido como _proprietário do sistema de arquivos_.

Como esses usuários exigem acesso aos mesmos arquivos, recomendamos que você crie uma [grupo compartilhado](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html#mage-owner-about-group) a que ambos pertencem. Os procedimentos a seguir pressupõem que você já fez isso.

Veja uma das seguintes seções:

- Dois proprietários do sistema de arquivos no modo de desenvolvedor ou padrão
- Dois proprietários do sistema de arquivos no modo de produção

### Configurar dois proprietários para o modo padrão ou de desenvolvedor

Os arquivos nos seguintes diretórios devem ser graváveis pelos usuários no modo desenvolvedor e padrão:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Defina as [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) bit em diretórios para que as permissões sempre herdem do diretório pai.

>[!INFO]
>
>`setgid` aplica-se apenas a diretórios, _not_ para arquivos.

Além disso, os diretórios devem ser graváveis pelo grupo de servidores da Web. Como o conteúdo pode existir nesses diretórios, adicione as permissões de forma recursiva.

#### Defina permissões e `setgid`

Para definir `setgid` e permissões para o modo desenvolvedor:

1. Faça logon no servidor do Commerce como proprietário do sistema de arquivos ou alterne para ele.
1. Insira os seguintes comandos na ordem mostrada:

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Dois proprietários do sistema de arquivos no modo de produção

Quando estiver pronto para implantar seu site na produção, você deve remover o acesso de gravação dos arquivos nos seguintes diretórios para melhorar a segurança:

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

Para remover permissões graváveis de arquivos e diretórios do grupo de usuários do servidor da Web:

1. Faça logon no seu servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Como proprietário do sistema de arquivos, insira o seguinte comando para alterar para o modo de produção:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Digite o seguinte comando como um usuário com `root` privilégios:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Tornar arquivos de código e diretórios graváveis

Para tornar os arquivos e diretórios graváveis, para que você possa atualizar os componentes e atualizar o software Commerce:

1. Faça logon no seu servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
