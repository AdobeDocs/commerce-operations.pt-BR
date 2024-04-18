---
title: Configurar a propriedade e as permissões do arquivo
description: Siga estas etapas para configurar permissões do sistema de arquivos para instalações locais do Adobe Commerce.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Configurar a propriedade e as permissões do arquivo

Este tópico discute como definir permissões de leitura e gravação para o grupo de servidores Web antes de instalar o Adobe Commerce. Isso é necessário para que a linha de comando possa gravar arquivos no sistema de arquivos.

O procedimento usado é diferente, dependendo se você usa [hospedagem compartilhado](#set-permissions-for-one-user-on-shared-hosting) e tiver um usuário ou se você usar um [servidor privado](#set-ownership-and-permissions-for-two-users) e têm dois usuários.

## Definir permissões para um usuário na hospedagem compartilhada

Esta seção discute como definir permissões de pré-instalação se você efetuar login no servidor de aplicativos como o mesmo usuário que também executa o servidor Web. Esse tipo de configuração é comum em ambientes de hospedagem compartilhados.

Para definir permissões antes de instalar o aplicativo:

1. Faça logon no servidor de aplicativos.
1. Use um aplicativo gerenciador de arquivos fornecido pelo seu provedor de hospedagem compartilhada para verificar se as permissões de gravação estão definidas nos seguintes diretórios:

   * `vendor` (Instalação do Composer ou de arquivos compactados)
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

   Para informar opcionalmente todos os comandos em uma linha, informe o seguinte, considerando que o aplicativo esteja instalado em `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Se ainda não tiver feito isso, obtenha o aplicativo de uma das seguintes maneiras:

   * [Metapackage do compositor](../../composer.md)
   * [Clonar o repositório (somente para desenvolvedores contribuintes)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Depois de definir a propriedade e as permissões do sistema de arquivos, [instalar o aplicativo](../../advanced.md)

>[!NOTE]
>
>Para restringir ainda mais as permissões após a instalação do aplicativo, é possível [configurar uma máscara](../../next-steps/set-umask.md).

## Definir propriedade e permissões para dois usuários

Esta seção discute como definir a propriedade e as permissões de seu próprio servidor ou de uma configuração de hospedagem privada. Nesse tipo de configuração, você normalmente *não é possível* efetue login como, ou alterne para, o usuário do servidor Web. Normalmente, você faz logon como um usuário e executa o servidor Web como um usuário diferente.

Para definir a propriedade e as permissões de um sistema de dois usuários:

Conclua as seguintes tarefas na ordem mostrada:

* [Sobre o grupo compartilhado](#about-the-shared-group)
* [Crie o proprietário do sistema de arquivos e forneça ao usuário uma senha forte](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Localizar o grupo do usuário do servidor Web](#find-the-web-server-user-group)
* [Colocar o proprietário do sistema de arquivos no grupo de servidores Web](#put-the-file-system-owner-in-the-web-server-group)
* [Obter o software](#get-the-software)
* [Definir propriedade e permissões para o grupo compartilhado](#set-ownership-and-permissions-for-the-shared-group)

### Sobre o grupo compartilhado

Para permitir que o servidor Web grave arquivos e diretórios no sistema de arquivos, mas também mantenha *propriedade* pelo proprietário do sistema de arquivos, ambos os usuários devem estar no mesmo grupo. Isso é necessário para que ambos os usuários possam compartilhar acesso a arquivos (incluindo arquivos criados usando o Administrador ou outros utilitários baseados na Web).

Esta seção discute como criar um proprietário do sistema de arquivos e colocar esse usuário no grupo do servidor Web. Se desejar, você poderá usar uma conta de usuário existente; recomendamos que o usuário tenha uma senha forte por motivos de segurança.

>[!NOTE]
>
>Pular para [Localizar o grupo de usuários do servidor Web](#find-the-web-server-user-group) se você planeja usar uma conta de usuário existente.

### Crie o proprietário do sistema de arquivos e forneça ao usuário uma senha forte

Esta seção discute como criar o proprietário do sistema de arquivos. (O proprietário do sistema de arquivos é outro termo para o *usuário da linha de comando*.)

Para criar um usuário no CentOS ou Ubuntu, digite o seguinte comando como usuário com `root` privilégios:

```bash
adduser <username>
```

Para fornecer uma senha ao usuário, digite o seguinte comando como usuário com `root` privilégios:

```bash
passwd <username>
```

Siga as instruções na tela para criar uma senha para o usuário.

>[!WARNING]
>
>Se você não tiver `root` no servidor de aplicativos, é possível usar outra conta de usuário local. Verifique se o usuário tem uma senha forte e continue com [Colocar o proprietário do sistema de arquivos no grupo de servidores Web](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Por exemplo, para criar um usuário chamado `magento_user` e fornecer uma senha ao usuário, digite:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Como o objetivo da criação desse usuário é fornecer segurança adicional, crie um [senha forte](https://en.wikipedia.org/wiki/Password_strength).

### Localizar o grupo de usuários do servidor Web

Para localizar o grupo do usuário do servidor Web:

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  ou

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

Normalmente, o nome do usuário e do grupo são `apache`.

* Ubuntu: `ps aux | grep apache` para encontrar o usuário Apache, `groups <apache user>` para encontrar o grupo.

Normalmente, o nome de usuário e o nome do grupo são `www-data`.

### Colocar o proprietário do sistema de arquivos no grupo de servidores Web

Para colocar o proprietário do sistema de arquivos no grupo principal do servidor Web (supondo o nome de grupo típico do Apache para CentOS e Ubuntu), digite o seguinte comando como usuário com `root` privilégios:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>A variável `-a -G` opções são importantes porque adicionam `apache` ou `www-data` as a *secundário* grupo para a conta do usuário, o que preserva o *principal* grupo. Adicionar um grupo secundário a uma conta de usuário ajuda [restringir a propriedade e as permissões do arquivo](#set-ownership-and-permissions-for-two-users) para garantir que os membros de um grupo compartilhado tenham acesso somente a determinados arquivos.

Por exemplo, para adicionar o usuário `magento_user` para o `apache` grupo principal no CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Para confirmar se o usuário é membro do grupo de servidores Web, digite o seguinte comando:

```bash
groups magento_user
```

O exemplo de resultado a seguir mostra o principal (`magento`) e secundário (`apache`) grupos.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>Normalmente, o nome de usuário e o nome do grupo principal são iguais.

Para concluir a tarefa, reinicie o servidor Web:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Obter o software

Se ainda não tiver feito isso, obtenha o software de uma das seguintes maneiras:

* [Metapackage do compositor](../../composer.md)
* [Clonar o repositório (somente para desenvolvedores contribuintes)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Definir propriedade e permissões para o grupo compartilhado

Para definir a propriedade e as permissões antes de instalar o aplicativo:

1. Efetue login no servidor de aplicativos como, ou alterne para, o proprietário do sistema de arquivos.
1. Digite os seguintes comandos na ordem mostrada:

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

Para informar opcionalmente todos os comandos em uma linha, informe o seguinte, considerando que o aplicativo esteja instalado em `/var/www/html/magento2` e o nome do grupo do servidor web é `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Caso as permissões do sistema de arquivos sejam definidas incorretamente e não possam ser alteradas pelo proprietário do sistema de arquivos, você pode inserir o comando como um usuário com `root` privilégios:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Alternar para o proprietário do sistema de arquivos

Após executar as outras tarefas neste tópico, insira um dos seguintes comandos para alternar para esse usuário:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Por exemplo,

```bash
su magento_user
```
