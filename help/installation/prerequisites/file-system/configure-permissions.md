---
title: Configurar a propriedade e as permissões do arquivo
description: Siga estas etapas para configurar permissões do sistema de arquivos para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# Configurar a propriedade e as permissões do arquivo

Este tópico discute como definir permissões de leitura/gravação para o grupo de servidores da Web antes de instalar o Adobe Commerce ou o Magento Open Source. Isso é necessário para que a linha de comando possa gravar arquivos no sistema de arquivos.

O procedimento usado é diferente, dependendo do uso [hospedagem compartilhada](#set-permissions-for-one-user-on-shared-hosting) e tenha um usuário ou se usar um [servidor privado](#set-ownership-and-permissions-for-two-users) e ter dois usuários.

## Definir permissões para um usuário em hospedagem compartilhada

Esta seção discute como definir permissões de pré-instalação se você fizer logon no servidor de aplicativos como o mesmo usuário que também executa o servidor da Web. Esse tipo de configuração é comum em ambientes de hospedagem compartilhada.

Para definir permissões antes de instalar o aplicativo:

1. Faça logon no servidor de aplicativos.
1. Use um aplicativo de gerenciador de arquivos fornecido pelo seu provedor de hospedagem compartilhada para verificar se as permissões de gravação estão definidas nos seguintes diretórios:

   * `vendor` (Composer ou instalação de arquivo compactado)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Quaisquer outros recursos estáticos

1. Se você tiver acesso à linha de comando, insira os seguintes comandos na ordem mostrada:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   Como opção, insira todos os comandos em uma linha, digite o seguinte supondo que o aplicativo esteja instalado em `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Se ainda não tiver feito isso, obtenha o aplicativo de uma das seguintes maneiras:

   * [Metapackeamento do compositor](../../composer.md)
   * [Clonar o repositório (somente desenvolvedores contribuidores)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Depois de definir a propriedade e as permissões do sistema de arquivos, [instale o aplicativo](../../advanced.md)

>[!NOTE]
>
>Para restringir ainda mais as permissões após a instalação do aplicativo, é possível [configurar uma máscara](../../next-steps/set-umask.md).

## Definir a propriedade e as permissões para dois usuários

Esta seção discute como definir a propriedade e as permissões para seu próprio servidor ou uma configuração de hospedagem privada. Nesse tipo de configuração, você normalmente *cannot* fazer logon como usuário do servidor da Web ou alternar para ele. Geralmente, você faz logon como um usuário e executa o servidor da Web como um usuário diferente.

Para definir a propriedade e as permissões de um sistema de dois usuários:

Conclua as seguintes tarefas na ordem mostrada:

* [Sobre o grupo compartilhado](#about-the-shared-group)
* [Crie o proprietário do sistema de arquivos e forneça ao usuário uma senha forte](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Localizar o grupo de usuários do servidor Web](#find-the-web-server-user-group)
* [Coloque o proprietário do sistema de arquivos no grupo do servidor da Web](#put-the-file-system-owner-in-the-web-server-group)
* [Obter o software](#get-the-software)
* [Definir a propriedade e as permissões do grupo compartilhado](#set-ownership-and-permissions-for-the-shared-group)

### Sobre o grupo compartilhado

Para permitir que o servidor da Web grave arquivos e diretórios no sistema de arquivos, mas também para manter *propriedade* pelo proprietário do sistema de arquivos, ambos os usuários devem estar no mesmo grupo. Isso é necessário para que ambos os usuários possam compartilhar o acesso a arquivos (incluindo arquivos criados com o Admin ou outros utilitários baseados na Web).

Esta seção discute como criar um proprietário de sistema de arquivos e colocar esse usuário no grupo do servidor da Web. Você pode usar uma conta de usuário existente, se desejar; recomendamos que o usuário tenha uma senha forte por motivos de segurança.

>[!NOTE]
>
>Ir para [Localizar o grupo de usuários do servidor da Web](#find-the-web-server-user-group) se você planeja usar uma conta de usuário existente.

### Crie o proprietário do sistema de arquivos e forneça ao usuário uma senha forte

Esta seção discute como criar o proprietário do sistema de arquivos. (proprietário do sistema de arquivos é outro termo para o *usuário da linha de comando*.)

Para criar um usuário no CentOS ou Ubuntu, digite o seguinte comando como usuário com `root` privilégios:

```bash
adduser <username>
```

Para fornecer uma senha ao usuário, digite o seguinte comando como usuário com `root` privilégios:

```bash
passwd <username>
```

Siga os prompts na tela para criar uma senha para o usuário.

>[!WARNING]
>
>Se você não tiver `root` no servidor de aplicativos, você pode usar outra conta de usuário local. Certifique-se de que o usuário tenha uma senha forte e continue com [Coloque o proprietário do sistema de arquivos no grupo do servidor da Web](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Por exemplo, para criar um usuário chamado `magento_user` e fornecer uma senha ao usuário, digite:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Como o objetivo da criação desse usuário é fornecer segurança adicional, crie uma [senha forte](https://en.wikipedia.org/wiki/Password_strength).

### Localizar o grupo de usuários do servidor da Web

Para localizar o grupo de usuários do servidor Web:

* CentOS:

   ```bash
   grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
   ```

   ou

   ```bash
   grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
   ```

Normalmente, o nome de usuário e grupo são `apache`.

* Ubuntu: `ps aux | grep apache` para encontrar o usuário do Apache, `groups <apache user>` para localizar o grupo.

Normalmente, o nome de usuário e o nome de grupo são `www-data`.

### Coloque o proprietário do sistema de arquivos no grupo do servidor da Web

Para colocar o proprietário do sistema de arquivos no grupo principal do servidor da Web (supondo o nome de grupo típico do Apache para CentOS e Ubuntu), digite o seguinte comando como um usuário com `root` privilégios:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>O `-a -G` são importantes porque adicionam `apache` ou `www-data` como *secundário* para a conta de usuário, o que preserva o *principal* grupo. Adicionar um grupo secundário a uma conta de usuário ajuda a [restringir a propriedade e as permissões do arquivo](#set-ownership-and-permissions-for-two-users) para garantir que os membros de um grupo compartilhado tenham acesso somente a determinados arquivos.

Por exemplo, para adicionar o usuário `magento_user` para `apache` grupo principal no CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Para confirmar que o usuário é membro do grupo do servidor da Web, digite o seguinte comando:

```bash
groups magento_user
```

A amostra de resultado a seguir mostra o principal do usuário (`magento`) e secundário (`apache`).

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>Normalmente, o nome de usuário e o nome do grupo principal são os mesmos.

Para concluir a tarefa, reinicie o servidor da Web:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Obter o software

Se ainda não tiver feito isso, obtenha o software de uma das seguintes maneiras:

* [Metapackeamento do compositor](../../composer.md)
* [Clonar o repositório (somente desenvolvedores contribuidores)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Definir a propriedade e as permissões do grupo compartilhado

Para definir a propriedade e as permissões antes de instalar o aplicativo:

1. Faça logon no servidor de aplicativos como ou alterne para o proprietário do sistema de arquivos.
1. Insira os seguintes comandos na ordem mostrada:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

Como opção, insira todos os comandos em uma linha, digite o seguinte supondo que o aplicativo esteja instalado em `/var/www/html/magento2` e o nome do grupo do servidor da Web é `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

No sistema de arquivos de eventos, as permissões são definidas incorretamente e não podem ser alteradas pelo proprietário do sistema de arquivos, você pode inserir o comando como um usuário com `root` privilégios:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Mudar para o proprietário do sistema de ficheiros

Depois de executar as outras tarefas neste tópico, insira um dos seguintes comandos para alternar para esse usuário:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Por exemplo,

```bash
su magento_user
```
