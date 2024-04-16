---
title: Executar uma atualização
description: Siga estas etapas para atualizar as implantações locais do Adobe Commerce.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# Executar uma atualização

Você pode atualizar _no local_ implantações do aplicativo Adobe Commerce ou Magento Open Source a partir da linha de comando, se você instalou o software ao:

- Baixando o metapackage do Composer usando o `composer create-project` comando.
- Instalando o arquivo compactado.

>[!NOTE]
>
>- Para projetos de infraestrutura em nuvem do Adobe Commerce, consulte [Atualizar versão do Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) no Guia da nuvem.
>- Não use esse método para atualizar se você clonou o repositório GitHub. Consulte [Atualizar uma instalação baseada em Git](../developer/git-installs.md).

As instruções a seguir mostram como atualizar usando o gerenciador de pacotes do Composer. O Adobe Commerce 2.4.2 introduziu o suporte para o Composer 2. Se você estiver tentando atualizar do &lt;2.4.1, é necessário primeiro atualizar para uma versão compatível com o Composer 2 (por exemplo, 2.4.2) usando o Composer 1 _antes_ atualização para o Composer 2 para atualizações >2.4.2. Além disso, você deve executar um [versão compatível](../../installation/system-requirements.md) do PHP.

>[!WARNING]
>
>O procedimento para atualizar o Adobe Commerce foi alterado. Você deve instalar uma nova versão do `magento/composer-root-update-plugin` pacote (consulte [pré-requisitos](../prepare/prerequisites.md)). Além disso, os comandos para atualização foram alterados de `composer require magento/<package_name>` para `composer require-commerce magento/<package_name>`.

## Antes de começar

Você deve concluir o [pré-requisitos de atualização](../prepare/prerequisites.md) para preparar seu ambiente antes de iniciar o processo de atualização.

## Gerenciar pacotes

>[!NOTE]
>
>Consulte os exemplos no final desta seção para obter ajuda com a especificação de diferentes níveis de versão. Por exemplo, patches de qualidade e patches de segurança. Se não conseguir encontrar esses pacotes no Composer, entre em contato com o Suporte da Adobe Commerce.

1. Alterne para o modo de manutenção para impedir o acesso ao seu armazenamento durante o processo de atualização.

   ```bash
   bin/magento maintenance:enable
   ```

   Consulte [Ativar ou desativar modo de manutenção](../../installation/tutorials/maintenance-mode.md) para obter opções adicionais. Como opção, você pode criar um [página de modo de manutenção personalizado](../troubleshooting/maintenance-mode-options.md).

1. Iniciar o processo de atualização enquanto processos assíncronos, como consumidores de fila de mensagens, estiverem em execução pode causar corrupção de dados. Para evitar a corrupção de dados, desative todos os trabalhos cron.

   _Adobe Commerce na infraestrutura em nuvem:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Inicie todos os consumidores da fila de mensagens manualmente para garantir que todas as mensagens sejam consumidas.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Aguarde a conclusão do trabalho cron. É possível monitorar o status do processo com um visualizador de processos ou executando o `ps aux | grep 'bin/magento queue'` comando várias vezes até que todos os processos sejam concluídos.

1. Crie um backup do `composer.json` arquivo.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Adicione ou remova pacotes específicos com base nas suas necessidades.

   Por exemplo, se estiver atualizando do Magento Open Source para o Adobe Commerce, remova o pacote Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Você também pode atualizar dados de amostra.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. Atualize sua instância usando o seguinte `composer require-commerce` sintaxe do comando:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   As opções de comando incluem:

   - `<product>` —(Obrigatório) O pacote a ser atualizado. Para instalações locais, esse valor deve ser `product-community-edition` ou `product-enterprise-edition`.

   - `<version>` —(Obrigatório) A versão do Adobe Commerce ou Magento Open Source para a qual você está atualizando. Por exemplo, `2.4.3`.

   - `--no-update` — (Obrigatório) Desabilita a atualização automática das dependências.

   - `--interactive-root-conflicts` —(Opcional) Permite exibir e atualizar interativamente quaisquer valores desatualizados de versões anteriores ou quaisquer valores personalizados que não correspondam à versão para a qual você está atualizando.

   - `--force-root-updates` —(Opcional) Substitui todos os valores personalizados conflitantes pelos valores esperados do Commerce.

   - `--help` —(Opcional) Fornece detalhes de uso sobre o plug-in.

   Se nenhuma delas `--interactive-root-conflicts` nem `--force-root-updates` forem especificados, o comando manterá os valores existentes que estiverem em conflito e exibirá uma mensagem de aviso. Para saber mais sobre o plug-in, consulte a [LEIAME de uso do plug-in](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Atualize as dependências.

   ```bash
   composer update
   ```

### Exemplo - listar versões disponíveis

Para ver a lista completa de versões 2.4.x disponíveis:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Exemplo - Correção de qualidade

Os remendos de qualidade contêm principalmente _e_ correções de segurança. No entanto, às vezes eles podem conter recursos novos e compatíveis com versões anteriores. Use o Composer para baixar um patch de qualidade.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Exemplo - Correção de segurança

Os patches de segurança contêm apenas correções de segurança. Elas foram projetadas para tornar o processo de atualização mais rápido e fácil. Os patches de segurança usam a convenção de nomenclatura do Composer `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## Atualizar metadados

1. Atualize o `"name"`, `"version"`, e `"description"` campos no `composer.json` conforme necessário.

   >[!NOTE]
   >
   >Atualização dos metadados no `composer.json` O arquivo é totalmente superficial, não funcional.

1. Aplique atualizações.

   ```bash
   composer update
   ```

1. Limpe a `var/` e `generated/` subdiretórios:

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Se você usar um armazenamento em cache diferente do sistema de arquivos, como Redis ou Memcached, você também deverá limpar manualmente o cache.

1. Atualize o esquema do banco de dados e os dados.

   ```bash
   bin/magento setup:upgrade
   ```

1. Desabilitar modo de manutenção.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Opcional)_ Reinicie o Varnish.

   Se você usar o Varnish para armazenamento em cache de página, reinicie-o:

   ```bash
   service varnish restart
   ```

## Verifique o seu trabalho

Para verificar se a atualização foi bem-sucedida, abra o URL da loja em um navegador da web. Se a atualização não tiver sido bem-sucedida, a loja não será carregada corretamente.

Se o aplicativo falhar com uma  `We're sorry, an error has occurred while generating this email.` erro:

1. Redefinir [propriedade e permissões do sistema de arquivos](../../installation/prerequisites/file-system/configure-permissions.md) como usuário com `root` privilégios.
1. Limpe os seguintes diretórios:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Verifique a vitrine eletrônica no navegador da web novamente.
