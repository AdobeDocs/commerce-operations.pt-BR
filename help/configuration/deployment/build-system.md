---
title: Configuração do sistema de compilação
description: Saiba como implantar o Commerce em um sistema de compilação.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Configuração do sistema de compilação

Você pode ter um sistema de build que atenda aos seguintes requisitos:

- Todo o código Commerce está sob controle do código-fonte no mesmo repositório dos sistemas de desenvolvimento e produção
- Verifique se todos os itens a seguir estão _incluídos_ no controle do código-fonte:

   - `app/etc/config.php`
   - Diretório `generated` (e subdiretórios)
   - Diretório `pub/media`
   - Diretório `pub/media/wysiwyg` (e subdiretórios)
   - Diretório `pub/static` (e subdiretórios)

- Deve ter uma versão compatível do PHP instalada
- É necessário ter o Composer instalado
- Ele tem a propriedade e as permissões do sistema de arquivos definidas conforme discutido em [Pré-requisito para seus sistemas de desenvolvimento, compilação e produção](../deployment/technical-details.md).
- O sistema de compilação não precisa do Commerce para ser instalado, mas o código deve estar disponível para ele.

>[!WARNING]
>
>A conexão de banco de dados não é necessária se já estiver contida em `config.php`; consulte [Exportar a configuração](../cli/export-configuration.md). Caso contrário, a conexão com o banco de dados será necessária.

>[!INFO]
>
>A máquina de build pode estar em seu próprio host ou no mesmo host de um sistema Commerce instalado.

## Configurar a máquina de compilação

As seções a seguir discutem como configurar a máquina de compilação.

### Instalar o Composer

Primeiro, verifique se o Composer já está instalado:

Em um prompt de comando, digite qualquer um dos comandos a seguir:

- `composer --help`
- `composer list --help`

Se a ajuda do comando for exibida, o Composer já está instalado.

Se um erro for exibido, siga as etapas abaixo para instalar o Composer.

Para instalar o Composer:

1. Altere para ou crie um diretório vazio no servidor do Commerce.

1. Digite os seguintes comandos:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Para obter opções adicionais de instalação, consulte a [documentação de instalação do Composer][composer].

### Instalar PHP

Instale o PHP no [CentOS] ou no [Ubuntu].

### Configurar o sistema de compilação

Para configurar o sistema de criação:

1. Faça logon no sistema de criação como, ou alterne para, o proprietário do sistema de arquivos.
1. Recupere o código Commerce do controle do código-fonte.

   Se você usar o Git, use o seguinte comando:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Altere para o diretório raiz do Commerce e digite:

   ```bash
   composer install
   ```

1. Aguarde até que as dependências sejam atualizadas.
1. Definir propriedade:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Por exemplo,

   ```bash
   chown -R commerce-username:apache .
   ```

1. Se você usa o Git, abra `.gitignore` em um editor de texto.
1. Inicie cada uma das seguintes linhas com um caractere `#` para comentá-las:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Salve as alterações em `.gitignore` e saia do editor de texto.
1. Se você usar o Git, use os seguintes comandos para confirmar a alteração:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Consulte a [`.gitignore` referência](../reference/config-reference-gitignore.md) para obter mais informações.

1. O sistema de compilação deve usar o [modo padrão](../bootstrap/application-modes.md#default-mode) ou o [modo de desenvolvedor](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` é obrigatório. Pode ser `default` ou `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
