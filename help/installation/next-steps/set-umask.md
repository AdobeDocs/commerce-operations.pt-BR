---
title: Definir uma máscara (opcional)
description: Melhore a postura de segurança da instalação local do Adobe Commerce ou do Magento Open Source restringindo as permissões do sistema de arquivos.
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Definir uma máscara (opcional)

O grupo de servidores da Web deve ter permissões de gravação em determinados diretórios no sistema de arquivos; no entanto, talvez você queira uma segurança mais rígida, especialmente na produção. Oferecemos a flexibilidade para que você restrinja ainda mais essas permissões usando um [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Nossa solução é permitir que você crie, opcionalmente, um arquivo chamado `magento_umask` no diretório raiz do aplicativo que restringe as permissões para o grupo de servidores Web e todos os outros.

>[!NOTE]
>
>Recomendamos alterar o umask somente em um sistema de hospedagem compartilhado ou de um usuário. Se você tiver um servidor de aplicativos privado, o grupo deverá ter acesso de gravação ao sistema de arquivos; o umask remove o acesso de gravação do grupo.

A máscara padrão (sem `magento_umask` especificado) é `002`, o que significa:

* 775 para diretórios, que significa controle total pelo usuário, controle total pelo grupo e permite que todos naveguem pelo diretório. Normalmente, essas permissões são exigidas por provedores de hospedagem compartilhados.

* 664 para arquivos, que significa gravável pelo usuário, gravável pelo grupo e somente leitura para todos os outros

Uma sugestão comum é usar um valor de `022` no `magento_umask` arquivo, o que significa:

* 755 para diretórios: controle total para o usuário e todos os outros podem percorrer diretórios.
* 644 para arquivos: permissões de leitura/gravação para o usuário e somente leitura para todos os outros.

Para definir `magento_umask`:

1. Em um terminal de linha de comando, efetue login no servidor do aplicativo como [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md).
1. Navegue até o diretório de instalação do aplicativo:

   ```bash
   cd <Application install directory>
   ```

1. Use o seguinte comando para criar um arquivo chamado `magento_umask` e escreva o `umask` valor para ele.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Agora você deve ter um arquivo chamado `magento_umask` no `<Magento install dir>` com o único conteúdo sendo o `umask` número.

1. Saia e faça logon novamente como a [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md) para aplicar as alterações.
