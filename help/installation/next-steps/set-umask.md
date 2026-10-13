---
title: Definir uma máscara (opcional)
description: Melhore a postura de segurança da instalação local do Adobe Commerce restringindo as permissões do sistema de arquivos.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%
---
# Definir uma máscara (opcional)

O grupo de servidores da Web deve ter permissões de gravação em determinados diretórios no sistema de arquivos; no entanto, talvez você queira uma segurança mais rígida, especialmente na produção. Oferecemos a flexibilidade para que você restrinja ainda mais essas permissões usando uma [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Nossa solução é permitir que você crie opcionalmente um arquivo chamado `magento_umask` no diretório raiz do aplicativo que restrinja as permissões para o grupo de servidores Web e todos os outros.

>[!NOTE]
>
>Recomendamos alterar o umask somente em um sistema de hospedagem compartilhado ou de um usuário. Se você tiver um servidor de aplicativos privado, o grupo deverá ter acesso de gravação ao sistema de arquivos; o umask remove o acesso de gravação do grupo.

O umask padrão (sem nenhum `magento_umask` especificado) é `002`, o que significa:

* 775 para diretórios, que significa controle total pelo usuário, controle total pelo grupo e permite que todos naveguem pelo diretório. Normalmente, essas permissões são exigidas por provedores de hospedagem compartilhados.

* 664 para arquivos, que significa gravável pelo usuário, gravável pelo grupo e somente leitura para todos os outros

Uma sugestão comum é usar um valor de `022` no arquivo `magento_umask`, o que significa:

* 755 para diretórios: controle total para o usuário e todos os outros podem percorrer diretórios.
* 644 para arquivos: permissões de leitura/gravação para o usuário e somente leitura para todos os outros.

Para definir `magento_umask`:

1. Em um terminal de linha de comando, faça logon no servidor de aplicativos como [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md).
1. Navegue até o diretório de instalação do aplicativo:

   ```shell
   cd <Application install directory>
   ```

1. Use o seguinte comando para criar um arquivo chamado `magento_umask` e gravar o valor `umask` nele.

   ```shell
   echo <desired umask number> > magento_umask
   ```

   Agora você deve ter um arquivo chamado `magento_umask` no `<Magento install dir>` com o único conteúdo sendo o número `umask`.

1. Saia e faça logon novamente como o [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md) para aplicar as alterações.
