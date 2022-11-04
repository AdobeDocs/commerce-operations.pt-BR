---
title: Clonar dados de amostra Repositórios Git
description: Siga estas etapas para instalar dados de amostra do Adobe Commerce e do Magento Open Source clonando repositórios Git.
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---


# Clonar dados de amostra Repositórios Git

Este tópico discute como clonar e adicionar dados de amostra se você tiver clonado o repositório GitHub do Magento Open Source. Esse método destina-se apenas a contribuidores de desenvolvedores (ou seja, desenvolvedores que planejam contribuir com a base de código do Magento Open Source).

Se você não for um desenvolvedor contribuinte, escolha uma das outras opções exibidas no índice à esquerda da página.

Os desenvolvedores colaboradores podem usar esse método de instalação de dados de amostra *only* se o seguinte for verdadeiro:

* Você usa o Magento Open Source
* Você [clonado o repositório GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Você pode usar dados de amostra com a variável `develop` ramificação (mais atual) ou ramificação lançada (como `2.4` (mais estável). Recomendamos que você use uma ramificação lançada porque ela é mais estável. Se você estiver contribuindo com o código para o repositório e precisar do código mais recente, use o `develop` ramificação. Independentemente da ramificação escolhida, você deve [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) a ramificação correspondente do repositório GitHub do Magento Open Source. Por exemplo, dados de amostra para a variável `develop` ramificação pode ser usada *only* com o Magento Open Source `develop` ramificação.

## Clonar o repositório de dados de amostra

Esta seção discute como instalar dados de amostra clonando o repositório de dados de amostra. Você pode clonar o repositório de dados de amostra de qualquer uma das seguintes maneiras:

* Clonar com o [Protocolo SSH](#clone-with-ssh)
* Clonar com o [Protocolo HTTPS](#clone-with-https)

### Clonar com SSH

Para clonar o repositório GitHub de dados de amostra usando o protocolo SSH:

1. Em um navegador da Web, acesse [exemplo de repositório de dados](https://github.com/magento/magento2-sample-data).
1. Ao lado do nome da ramificação, clique em **SSH** na lista.
1. Clique em **Copiar para a área de transferência**

   A figura a seguir mostra um exemplo.

   ![Clonar o repositório GitHub usando SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Altere para o diretório raiz do servidor da Web.

   Normalmente, para Ubuntu, é `/var/www` e para CentOS é `/var/www/html`.

1. Enter `git clone` e cole o valor obtido anteriormente.

   Um exemplo:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Aguarde até que o repositório clone em seu servidor.

   >[!NOTE]
   >
   >Se o seguinte erro for exibido, verifique se [compartilhou sua chave SSH](https://docs.github.com/articles/generating-ssh-keys/) com GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Verifique a ramificação do repositório de dados de amostra que corresponde à ramificação usada do `magento2` repositório.

   Por exemplo:

   Se você usou o `2.4-develop` ramificação do repositório GitHub do Magento Open Source, a ramificação de dados de amostra deve ser `2.4-develop`.

   Para verificar a ramificação correta, execute o seguinte comando a partir do diretório raiz do repositório de dados de amostra (supondo que você precise do `2.4-develop` ramificação):

   ```bash
   git checkout 2.4-develop
   ```

1. Alterar para `<app_root>`.
1. Digite o seguinte comando para criar links simbólicos entre os arquivos clonados para que os dados de amostra funcionem corretamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Aguarde a conclusão do comando.

1. Consulte [Definir permissões e propriedade do sistema de arquivos](#set-file-system-ownership-and-permissions).

1. Execute o seguinte comando:

   ```bash
   bin/magento setup:upgrade
   ```

### Clonar com HTTPS

Para clonar o repositório GitHub de dados de amostra usando o protocolo HTTPS:

1. Em um navegador da Web, acesse [exemplo de repositório de dados](https://github.com/magento/magento2-sample-data).
1. No lado direito da página, em **clone URL** , clique em **HTTPS**.
1. Clique em **Copiar para a área de transferência**.

   A figura a seguir mostra um exemplo.

   ![Clonar o repositório GitHub usando HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Altere para o diretório raiz do servidor da Web.

   Normalmente, para Ubuntu, é `/var/www` e para CentOS é `/var/www/html`.

1. Enter `git clone` e cole o valor obtido anteriormente.

   Um exemplo:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Aguarde até que o repositório clone em seu servidor.
1. Verifique a ramificação do repositório de dados de amostra que corresponde à ramificação usada do `magento2` repositório.

   Por exemplo:

   Se você usou o `2.4-develop` ramificação do repositório GitHub do Magento Open Source, a ramificação de dados de amostra deve ser `2.4-develop`.

   Para verificar a ramificação correta, execute o seguinte comando a partir do diretório raiz do repositório de dados de amostra (supondo que você precise do `2.4-develop` ramificação):

   ```bash
   git checkout 2.4-develop
   ```

1. Alterar para `<magento_root>`.
1. Digite o seguinte comando para criar links simbólicos entre os arquivos clonados para que os dados de amostra funcionem corretamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Por exemplo,

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Aguarde a conclusão do comando.
1. Consulte a próxima seção.

>[!WARNING]
>
>Se você estiver instalando dados de amostra *after* ao instalar o Adobe Commerce ou o Magento Open Source, você também deve executar o seguinte comando para atualizar o banco de dados e o schema:
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## Definir a propriedade e as permissões do sistema de arquivos

Porque a variável `php build-sample-data.php` O script cria links simbólicos entre o repositório de dados de amostra e o repositório de Magento Open Source, é necessário definir as permissões e a propriedade do sistema de arquivos no repositório de dados de amostra. Se isso não for feito, ocorrerão erros ao acessar a loja.

Para definir permissões e propriedade do sistema de arquivos no repositório de dados de amostra:

1. Altere para o diretório de clone de dados de amostra.
1. Definir proprietário:

   ```bash
   chown -R :<your web server group name> .
   ```

   Exemplos típicos:

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. Definir permissões:

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. Limpar arquivos estáticos:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## Conclua a instalação de dados de amostra

{{$include /help/_includes/sample-data-complete.md}}
