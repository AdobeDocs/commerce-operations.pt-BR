---
title: Gerenciar extensões de terceiros
description: Siga estas etapas para instalar, habilitar, atualizar e desinstalar extensões de Adobe Commerce.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: f057cf082eeab1e34957e284817c6b93517de21b
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# Gerenciar extensões de terceiros

O código que estende ou personaliza o comportamento do Adobe Commerce é chamado de extensão. Opcionalmente, é possível empacotar e distribuir extensões no [Commerce Marketplace](https://commercemarketplace.adobe.com/) ou em outro sistema de distribuição de extensões.

As extensões incluem:

- Módulos (estenda os recursos do Adobe Commerce)
- Temas (altere a aparência da loja e do administrador)
- Pacotes de idioma (localize a loja e o Administrador)

Este tópico explica como usar a interface de linha de comando para gerenciar extensões de terceiros que você compra do Commerce Marketplace para projetos do _no local_. Para projetos de infraestrutura em nuvem, consulte [Gerenciar extensões](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure-store/extensions).

Você pode usar o mesmo procedimento para instalar a extensão _any_. Tudo o que você precisa é o nome e a versão do Compositor da extensão. Para encontrá-lo, abra o arquivo `composer.json` da extensão e anote os valores de `"name"` e `"version"`.

## Instalar

Antes da instalação, talvez você queira:

1. Faça backup do banco de dados.
1. Habilitar modo de manutenção:

   ```bash
   bin/magento maintenance:enable
   ```

Para instalar uma extensão, você deve:

1. Obtenha uma extensão do Commerce Marketplace ou de outro desenvolvedor de extensão.
1. Se você instalar uma extensão do Commerce Marketplace, verifique se o repositório `repo.magento.com` existe no arquivo `composer.json`:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Obtenha o nome e a versão do Compositor da extensão.
1. Atualize o arquivo `composer.json` em seu projeto com o nome e a versão da extensão.
1. Verifique se a extensão foi instalada corretamente.
1. Ative e configure a extensão.

### Obter informações de extensão

Se você já sabe o nome e a versão do Composer da extensão, ignore esta etapa e continue com [Atualize seu arquivo `composer.json`](#update-composer-dependencies).

Para obter o nome e a versão do Compositor da extensão do Commerce Marketplace:

1. Faça logon em [Commerce Marketplace](https://commercemarketplace.adobe.com/) com o nome de usuário e a senha que você usou para comprar a extensão.

1. No canto superior direito, clique em **Seu nome** > **Meu perfil**.

   ![Acessar sua conta do Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Clique em **Minhas compras**.

   ![Histórico de compras do Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Encontre a extensão que deseja instalar e anote o nome e a versão do componente.

   ![Os detalhes técnicos mostram o nome do Compositor da extensão](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>Como alternativa, você pode encontrar o nome e a versão do Composer da extensão _any_ (seja na compra no Commerce Marketplace ou em outro lugar) no arquivo `composer.json` da extensão.

### Atualizar dependências do Composer

Adicione o nome e a versão da extensão ao arquivo `composer.json`:

1. Navegue até o diretório do projeto e atualize o arquivo `composer.json`.

   ```bash
   composer require <component-name>:<version>
   ```

   Por exemplo,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Insira suas [chaves de autenticação](../prerequisites/authentication-keys.md). Sua chave pública é seu nome de usuário; sua chave privada é sua senha.

1. Aguarde até que o Composer conclua a atualização das dependências do projeto e verifique se não há erros:

   ```
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

### Verificar instalação

Para verificar se a extensão foi instalada corretamente, execute o seguinte comando:

```bash
bin/magento module:status J2t_Payplug
```

Por padrão, a extensão provavelmente está desativada:

```
Module is disabled
```

O nome da extensão está no formato `<VendorName>_<ComponentName>`; esse é um formato diferente do nome do Compositor. Use esse formato para habilitar a extensão. Se não tiver certeza do nome da extensão, execute:

```bash
bin/magento module:status
```

E procure a extensão em &quot;Lista de módulos desativados&quot;.

### Ativar

Algumas extensões não funcionam corretamente, a menos que você limpe primeiro os arquivos de exibição estáticos gerados. Use a opção `--clear-static-content` para limpar arquivos de exibição estáticos quando estiver habilitando uma extensão.

1. Habilite a extensão e limpe os arquivos de exibição estáticos:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Você deve ver a seguinte saída:

   ```
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

1. Recompile o projeto: no modo de Produção, você pode receber uma mensagem para &quot;Execute novamente o comando Magento compile&quot;. O aplicativo não solicita que você execute o comando compile no modo de Desenvolvedor.

   ```bash
   bin/magento setup:di:compile
   ```

1. Verifique se a extensão está ativada:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Você deve ver a saída verificando se a extensão não está mais desativada:

   ```
   Module is enabled
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Configure a extensão no Admin conforme necessário.

>[!TIP]
>
>Se você encontrar erros ao carregar a loja em um navegador, use o seguinte comando para limpar o cache: `bin/magento cache:flush`.

## Atualizar

Para atualizar ou atualizar um módulo ou uma extensão:

1. Baixe o arquivo atualizado do Marketplace ou de outro desenvolvedor de extensão. Anote o nome e a versão do módulo.

1. Exporte o conteúdo para o diretório raiz do aplicativo.

1. Se existir um pacote do Composer para o módulo, execute um dos procedimentos a seguir.

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

## Desinstalar

Você deve entrar em contato com o fornecedor da extensão para obter instruções sobre como remover uma extensão de terceiros. As instruções devem fornecer as seguintes informações:

- Como reverter alterações na tabela do banco de dados
- Como reverter alterações de dados do banco de dados
- Quais arquivos devem ser removidos ou revertidos

>[!CAUTION]
>
>Execute as etapas de desinstalação em um ambiente de não produção _first_ e teste completamente antes de implantar em seu ambiente de produção.

As instruções a seguir fornecem informações gerais para a desinstalação de extensões de terceiros:

1. Remova a extensão do repositório de projetos do Adobe Commerce.

   - Para extensões baseadas no Composer, remova a extensão do arquivo Adobe Commerce `composer.json`.

     ```bash
     composer remove <component-name>
     ```

   - Para extensões não baseadas no Composer, remova os arquivos físicos do repositório do projeto do Adobe Commerce.

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. Se o arquivo `config.php` estiver sob controle do código-fonte no repositório de projetos do Adobe Commerce, remova a extensão do arquivo `config.php`.

1. Teste o banco de dados local para garantir que as instruções fornecidas pelo fornecedor funcionem conforme esperado.

1. Verifique se a extensão está desativada corretamente e se o site funciona conforme esperado em seu ambiente de preparo.

1. Implante as alterações no ambiente de produção.
