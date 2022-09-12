---
title: Definir uma máscara (opcional)
description: Melhore a postura de segurança da instalação do Adobe Commerce ou Magento Open Source no local restringindo as permissões do sistema de arquivos.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Definir uma máscara (opcional)

O grupo de servidores da Web deve ter permissões de gravação em determinados diretórios no sistema de arquivos; no entanto, você pode querer maior segurança, especialmente na produção. Oferecemos flexibilidade para que você restrinja ainda mais essas permissões usando uma [máscara](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Nossa solução é permitir que você crie opcionalmente um arquivo chamado `magento_umask` no diretório raiz do seu aplicativo que restringe as permissões para o grupo de servidores da Web e todos os outros usuários.

>[!NOTE]
>
>Recomendamos alterar a máscara somente em um sistema de hospedagem compartilhado ou com um único usuário. Se você tiver um servidor de aplicativos privado, o grupo deverá ter acesso de gravação ao sistema de arquivos; o umask remove o acesso de gravação do grupo.

A máscara padrão (sem `magento_umask` especificado) é `002`, o que significa:

* 775 para diretórios, o que significa controle total pelo usuário, controle total pelo grupo e permite que todos percorram o diretório. Normalmente, essas permissões são exigidas por provedores de hospedagem compartilhada.

* 664 para arquivos, o que significa gravável pelo usuário, gravável pelo grupo e somente leitura para todos os outros

Uma sugestão comum é usar um valor de `022` no `magento_umask` , o que significa:

* 755 para diretórios: controle total para o usuário e todos os outros podem navegar pelos diretórios.
* 644 para arquivos: permissões de leitura/gravação para o usuário e somente leitura para todos os outros.

Para definir `magento_umask`:

1. Em um terminal de linha de comando, faça logon no servidor de aplicativos como um [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md).
1. Navegue até o diretório de instalação do aplicativo:

   ```bash
   cd <Application install directory>
   ```

1. Use o seguinte comando para criar um arquivo chamado `magento_umask` e escreva o `umask` a ele.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Agora você deve ter um arquivo chamado `magento_umask` no `<Magento install dir>` com o único conteúdo sendo o `umask` número.

1. Faça logoff e login novamente como o [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md) para aplicar as alterações.
