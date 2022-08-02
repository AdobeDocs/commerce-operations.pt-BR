---
title: Configuração do sistema de build
description: Saiba como implantar o Commerce em um sistema de build.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Criar configuração do sistema

Você pode ter um sistema de build que atenda aos seguintes requisitos:

- Todo o código do Commerce está sob controle de origem no mesmo repositório que os sistemas de desenvolvimento e produção
- Certifique-se de que todos os itens a seguir sejam _included_ no controlo-fonte:

   - `app/etc/config.php`
   - `generated` diretório (e subdiretórios)
   - `pub/media` diretory
   - `pub/media/wysiwyg` diretório (e subdiretórios)
   - `pub/static` diretório (e subdiretórios)

- Deve ter uma versão PHP compatível instalada
- Deve ter o Composer instalado
- Ele tem a propriedade do sistema de arquivos e as permissões definidas como discutido em [Pré-requisito para seus sistemas de desenvolvimento, criação e produção](../deployment/technical-details.md).
- O sistema de build não precisa que o Commerce seja instalado, mas o código deve estar disponível para ele.

>[!WARNING]
>
>A conexão do banco de dados não é necessária se já estiver contida em `config.php`; see [Exportar a configuração](../cli/export-configuration.md). Caso contrário, a conexão do banco de dados será necessária.

>[!INFO]
>
>A máquina de build pode estar em seu próprio host ou no mesmo host que um sistema do Commerce instalado.

## Configurar a máquina de compilação

As seções a seguir discutem como configurar a máquina de compilação.

### Instalar o Composer

Primeiro, verifique se o Composer já está instalado:

Em um prompt de comando, insira qualquer um dos seguintes comandos:

- `composer --help`
- `composer list --help`

Se a ajuda de comando for exibida, o Composer já estará instalado.

Se um erro for exibido, use as seguintes etapas para instalar o Composer.

Para instalar o Composer:

1. Altere para ou crie um diretório vazio no seu servidor do Commerce.

1. Insira os seguintes comandos:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Para obter opções adicionais de instalação, consulte o [Documentação de instalação do Composer][composer].

### Instalar PHP

Instalar PHP em [CentOS] ou [Ubuntu].

### Configurar o sistema de build

Para configurar o sistema de build:

1. Faça logon no sistema de build como ou alterne para o proprietário do sistema de arquivos.
1. Recupere o código do Commerce do controle do código-fonte.

   Se você usar o Git, use o seguinte comando:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Altere para o diretório raiz do Commerce e digite:

   ```bash
   composer install
   ```

1. Aguarde as dependências serem atualizadas.
1. Definir proprietário:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Por exemplo,

   ```bash
   chown -R commerce-username:apache .
   ```

1. Se você usar Git, abra `.gitignore` em um editor de texto.
1. Inicie cada uma das seguintes linhas com uma `#` caractere para comentá-los:

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

1. O sistema de build deve usar [modo padrão](../bootstrap/application-modes.md#default-mode) ou [modo desenvolvedor](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` é obrigatório. Pode ser `default` ou `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
