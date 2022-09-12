---
title: Instalar uma extensão
description: Siga estas etapas para instalar uma extensão Adobe Commerce ou Magento Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Instalar uma extensão

O código que estende ou personaliza o comportamento do Adobe Commerce e do Magento Open Source é chamado de extensão. Opcionalmente, é possível empacotar e distribuir extensões no [Commerce Marketplace](https://marketplace.magento.com) ou outro sistema de distribuição de extensões.

As extensões incluem:

- Módulos (estenda os recursos Adobe Commerce e Magento Open Source)
- Temas (altere a aparência de seu [vitrine](https://glossary.magento.com/storefront) e Administrador)
- Pacotes de idioma (localize a loja e o administrador)

>[!TIP]
>
>Este tópico explica como usar a linha de comando para instalar extensões compradas no Commerce Marketplace. Você pode usar o mesmo procedimento para instalar o _any_ extensão; tudo que você precisa é do [Composer](https://glossary.magento.com/composer) nome e versão. Para encontrá-lo, abra o `composer.json` e observe os valores de `"name"` e `"version"`.

Antes da instalação, você pode desejar:

1. Faça backup do banco de dados.
1. Ativar o modo de manutenção:

   ```bash
   bin/magento maintenance:enable
   ```

Para instalar uma extensão, você deve:

1. Obtenha uma extensão do Commerce Marketplace ou de outro desenvolvedor de extensão.
1. Se você instalar uma extensão do Commerce Marketplace, verifique se a variável `repo.magento.com` o repositório existe em seu `composer.json` arquivo:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Obtenha o nome e a versão do Composer da extensão.
1. Atualize o `composer.json` no seu projeto com o nome e a versão da extensão .
1. Verifique se a extensão foi instalada corretamente.
1. Habilite e configure a extensão.

## Obter o nome e a versão da extensão Composer

Se você já sabe o nome e a versão da extensão do Composer, pule esta etapa e continue com [Atualize seu `composer.json` arquivo](#update-your-composer-file).

Para obter o nome e a versão do Composer da extensão do Commerce Marketplace:

1. Faça logon em [Commerce Marketplace](https://marketplace.magento.com) com o nome de usuário e a senha usados para comprar a extensão do .

1. No canto superior direito, clique em **Seu nome** > **Meu perfil**.

   ![Acessar sua conta do Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Clique em **Minhas compras**.

   ![Histórico de compras do Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Encontre a extensão que deseja instalar e clique em **Detalhes técnicos**.

   ![Detalhes técnicos mostram o nome do Composer da extensão](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>Como alternativa, você pode encontrar o nome e a versão do Composer _any_ extensão (se você a comprou no Commerce Marketplace ou em outro lugar) no `composer.json` arquivo.

## Atualizar o arquivo do Composer

Adicione o nome e a versão da extensão ao `composer.json` arquivo:

1. Navegue até o diretório do projeto e atualize seu `composer.json` arquivo.

   ```bash
   composer require <component-name>:<version>
   ```

   Por exemplo,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Insira seu [chaves de autenticação](../prerequisites/authentication-keys.md). Sua chave pública é seu nome de usuário; sua chave privada é sua senha.

1. Aguarde até que o Composer conclua a atualização das dependências do projeto e verifique se não há erros:

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## Verificar a extensão

Para verificar se a extensão foi instalada corretamente, execute o seguinte comando:

```bash
bin/magento module:status J2t_Payplug
```

Por padrão, a extensão provavelmente está desabilitada:

```terminal
Module is disabled
```

O nome da extensão está no formato `<VendorName>_<ComponentName>`; este é um formato diferente do nome do Composer. Use esse formato para ativar a extensão. Se não tiver certeza do nome da extensão, execute:

```bash
bin/magento module:status
```

E procure a extensão em &quot;Lista de módulos desativados&quot;.

## Habilitar a extensão

Algumas extensões não funcionam corretamente a menos que você limpe os arquivos de visualização estática gerados primeiro. Use o `--clear-static-content` para limpar arquivos de visualização estáticos ao ativar uma extensão.

1. Habilite a extensão e limpe os arquivos de visualização estática:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Você deve ver a seguinte saída:

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. Registre a extensão:

   ```bash
   bin/magento setup:upgrade
   ```

1. Recompile seu projeto: No modo Produção, você pode receber uma mensagem para &quot;Execute novamente o comando Magento compilar&quot;. O aplicativo não solicita que você execute o comando de compilação no modo Desenvolvedor.

   ```bash
   bin/magento setup:di:compile
   ```

1. Verifique se a extensão está ativada:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Você deve ver a saída verificando se a extensão não está mais desabilitada:

   ```terminal
   Module is enabled
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Configure a extensão em Admin, conforme necessário.

>[!TIP]
>
>Se encontrar erros ao carregar a loja em um navegador, use o seguinte comando para limpar o cache: `bin/magento cache:flush`.

## Atualizar uma extensão

Para atualizar ou atualizar um módulo ou extensão:

1. Baixe o arquivo atualizado do Marketplace ou de outro desenvolvedor de extensão. Anote o nome e a versão do módulo.

1. Exporte o conteúdo para o diretório raiz do aplicativo.

1. Se houver um pacote Composer para o módulo, execute um dos seguintes procedimentos.

   Atualizar por nome de módulo:

   ```bash
   composer update vendor/module-name
   ```

   Atualizar por versão:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Execute os seguintes comandos para atualizar, implantar e limpar o cache.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
