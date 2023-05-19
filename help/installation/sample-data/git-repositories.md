---
title: Clonar repositórios Git de dados de amostra
description: Siga estas etapas para instalar dados de amostra do Adobe Commerce e do Magento Open Source clonando repositórios Git.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Clonar repositórios Git de dados de amostra

Este tópico discute como clonar e adicionar dados de amostra se você tiver clonado o repositório GitHub do Magento Open Source. Esse método é destinado apenas aos desenvolvedores contribuintes (ou seja, desenvolvedores que planejam contribuir com a base de código do Magento Open Source).

Se você não for um desenvolvedor contribuinte, escolha uma das outras opções exibidas no sumário à esquerda da página.

Os desenvolvedores colaboradores podem usar esse método para instalar dados de amostra *somente* se o seguinte for verdadeiro:

* Você usa o Magento Open Source
* Você [clonado o repositório GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Você pode usar dados de amostra com o `develop` (mais atual) ou uma ramificação liberada (como `2.4` (mais estável). Recomendamos que você use uma ramificação lançada porque ela é mais estável. Se estiver contribuindo com código para o repositório e precisar do código mais recente, use o `develop` filial. Independentemente da ramificação escolhida, você deve [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) a ramificação correspondente do repositório GitHub do Magento Open Source. Por exemplo, dados de amostra para a variável `develop` ramificação pode ser usada *somente* com o Magento Open Source `develop` filial.

## Clonar o repositório de dados de amostra

Esta seção discute como instalar dados de amostra clonando o repositório de dados de amostra. Você pode clonar o repositório de dados de amostra de qualquer uma das seguintes maneiras:

* Clonar com o [Protocolo SSH](#clone-with-ssh)
* Clonar com o [Protocolo HTTPS](#clone-with-https)

### Clonar com SSH

Para clonar o repositório GitHub de dados de amostra usando o protocolo SSH:

1. Em um navegador da Web, acesse o [repositório de dados de amostra](https://github.com/magento/magento2-sample-data).
1. Ao lado do nome da ramificação, clique em **SSH** da lista.
1. Clique em **Copiar para a área de transferência**

   A figura a seguir mostra um exemplo.

   ![Clonar o repositório GitHub usando SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Altere para o diretório docroot do servidor Web.

   Normalmente, para o Ubuntu, é `/var/www` e para o CentOS, é `/var/www/html`.

1. Enter `git clone` e cole o valor obtido anteriormente.

   Um exemplo é o seguinte:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Aguarde o repositório clonar no servidor.

   >[!NOTE]
   >
   >Se o erro a seguir for exibido, verifique se [compartilhou sua chave SSH](https://docs.github.com/articles/generating-ssh-keys/) com GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Verifique a ramificação do repositório de dados de amostra que corresponde à ramificação usada no repositório principal `magento2` repositório.

   Por exemplo:

   Se você usou o `2.4-develop` do repositório GitHub Magento Open Source, a ramificação de Dados de amostra deve ser `2.4-develop`.

   Para fazer check-out da ramificação correta, execute o seguinte comando no diretório raiz do repositório de dados de amostra (supondo que você precise da `2.4-develop` ramificação):

   ```bash
   git checkout 2.4-develop
   ```

1. Alterar para `<app_root>`.
1. Digite o seguinte comando para criar vínculos simbólicos entre os arquivos clonados para que os dados de amostra funcionem corretamente:

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

1. Em um navegador da Web, acesse o [repositório de dados de amostra](https://github.com/magento/magento2-sample-data).
1. No lado direito da página, sob a guia **clonar URL** clique em **HTTPS**.
1. Clique em **Copiar para a área de transferência**.

   A figura a seguir mostra um exemplo.

   ![Clonar o repositório GitHub usando HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Altere para o diretório docroot do servidor Web.

   Normalmente, para o Ubuntu, é `/var/www` e para o CentOS, é `/var/www/html`.

1. Enter `git clone` e cole o valor obtido anteriormente.

   Um exemplo é o seguinte:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Aguarde o repositório clonar no servidor.
1. Verifique a ramificação do repositório de dados de amostra que corresponde à ramificação usada no repositório principal `magento2` repositório.

   Por exemplo:

   Se você usou o `2.4-develop` do repositório GitHub Magento Open Source, a ramificação de Dados de amostra deve ser `2.4-develop`.

   Para fazer check-out da ramificação correta, execute o seguinte comando no diretório raiz do repositório de dados de amostra (supondo que você precise da `2.4-develop` ramificação):

   ```bash
   git checkout 2.4-develop
   ```

1. Alterar para `<magento_root>`.
1. Digite o seguinte comando para criar vínculos simbólicos entre os arquivos clonados para que os dados de amostra funcionem corretamente:

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
>Se estiver instalando dados de amostra *após* ao instalar o Adobe Commerce ou o Magento Open Source, você também deve executar o seguinte comando para atualizar o banco de dados e o schema:
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## Definir a propriedade e as permissões do sistema de arquivos

Como a variável `php build-sample-data.php` O script cria symlinks entre o repositório de dados de amostra e o repositório de Magento Open Source, você deve definir as permissões do sistema de arquivos e a propriedade no repositório de dados de amostra. Se isso não for feito, ocorrerão erros ao acessar a loja.

Para definir as permissões e a propriedade do sistema de arquivos no repositório de dados de amostra:

1. Altere para o diretório de clonagem de dados de amostra.
1. Definir propriedade:

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

## Conclua a instalação dos dados de amostra

{{$include /help/_includes/sample-data-complete.md}}
