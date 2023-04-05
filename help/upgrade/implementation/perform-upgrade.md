---
title: Executar uma atualização
description: Siga estas etapas para atualizar um projeto Adobe Commerce ou Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Executar uma atualização

Você pode atualizar seu aplicativo Adobe Commerce ou Magento Open Source da linha de comando se tiver instalado o software:

- Download do metapackage usando o `composer create-project` comando.
- Instalar o arquivo compactado.

>[!NOTE]
>
>Não use esse método para atualizar se tiver clonado o repositório GitHub. Em vez disso, consulte [Atualizar uma instalação baseada em git](../developer/git-installs.md) para obter instruções de atualização.

As instruções a seguir mostram como atualizar usando o Composer. O Adobe Commerce 2.4.2 apresentou suporte para o Composer 2. Se você estiver tentando atualizar de &lt;2.4.1, primeiro deve atualizar para uma versão compatível com o Composer 2 (por exemplo, 2.4.2) usando o Composer 1 _before_ atualização para o Composer 2 para atualizações do >2.4.2. Além disso, você deve executar uma [versão compatível](../../installation/system-requirements.md) do PHP.

>[!WARNING]
>
>O procedimento para atualizar o Adobe Commerce e o Magento Open Source foi alterado. Você deve instalar uma nova versão do `magento/composer-root-update-plugin` (consulte [pré-requisitos](../prepare/prerequisites.md)). Além disso, os comandos para atualização foram alterados de `composer require magento/<package_name>` para `composer require-commerce magento/<package_name>`.

## Antes de começar

Você deve concluir o [pré-requisitos de atualização](../prepare/prerequisites.md) para preparar seu ambiente antes de iniciar o processo de atualização.

## Gerenciar pacotes

>[!NOTE]
>
>Consulte os exemplos no final desta seção para obter ajuda com a especificação de diferentes níveis de versão. Por exemplo, versão secundária, patch de qualidade e patch de segurança. Os clientes da Adobe Commerce podem acessar os patches duas semanas antes da data da Disponibilidade Geral (GA). Os pacotes de pré-lançamento estão disponíveis somente por meio do Composer. Não é possível encontrá-los no Portal de downloads ou no GitHub até GA. Se não conseguir encontrar esses pacotes no Composer, entre em contato com o Suporte da Adobe Commerce.

1. Alterne para o modo de manutenção para impedir o acesso à sua loja durante o processo de atualização.

   ```bash
   bin/magento maintenance:enable
   ```

   Consulte [Ativar ou desativar o modo de manutenção](../../installation/tutorials/maintenance-mode.md) para obter opções adicionais. Opcionalmente, é possível criar uma [página do modo de manutenção personalizado](../troubleshooting/maintenance-mode-options.md).

1. Iniciar o processo de atualização enquanto processos assíncronos, como consumidores de fila de mensagens, estão em execução pode causar corrupção de dados. Para evitar a corrupção de dados, desative todas as tarefas do cron.

   _Adobe Commerce na infraestrutura de nuvem:_

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

   Aguarde a conclusão do trabalho de cron. Você pode monitorar o status da tarefa com um visualizador de processos ou executando o `ps aux | grep 'bin/magento queue'` comando várias vezes até que todos os processos sejam concluídos.

1. Crie um backup do `composer.json` arquivo.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Adicione ou remova pacotes específicos com base em suas necessidades.

   Por exemplo, se estiver atualizando do Magento Open Source para o Adobe Commerce, remova o pacote Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Também é possível atualizar dados de amostra.

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

   - `<product>` —(Obrigatório) O pacote a ser atualizado. Para as instalações no local, este valor deve ser `product-community-edition` ou `product-enterprise-edition`.

   - `<version>` —(Obrigatório) A versão do Adobe Commerce ou Magento Open Source para a qual você está atualizando. Por exemplo, `2.4.3`.

   - `--no-update` —(Obrigatório) Desativa a atualização automática das dependências.

   - `--interactive-root-conflicts` —(Opcional) Permite que você visualize e atualize interativamente quaisquer valores desatualizados de versões anteriores ou quaisquer valores personalizados que não correspondam à versão para a qual você está atualizando.

   - `--force-root-updates` —(Opcional) Substitui todos os valores personalizados conflitantes pelos valores de Magento esperados.

   - `--help` —(Opcional) Fornece detalhes de uso sobre o plug-in.
   Se nem `--interactive-root-conflicts` nor `--force-root-updates` forem especificados, o comando manterá os valores existentes que estão em conflito e exibirá uma mensagem de aviso. Para saber mais sobre o plug-in, consulte [LEIA-ME de Uso de Plug-in](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Atualize as dependências.

   ```bash
   composer update
   ```

### Exemplo - listar versões disponíveis

Para ver a lista completa das versões 2.4.x disponíveis:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Exemplo - Versão secundária

As versões secundárias contêm novos recursos, correções de qualidade e correções de segurança. Use o Composer para especificar uma versão secundária. Por exemplo, para especificar o metapackage do Magento Open Source 2.4.3:

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### Exemplo - Patch de qualidade

Os patches de qualidade contêm principalmente funcionalidade _e_ correções de segurança. No entanto, às vezes, eles podem conter novos recursos compatíveis com versões anteriores. Use o Composer para baixar um patch de qualidade. Por exemplo, para especificar o metapackage do Magento Open Source 2.4.1:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### Exemplo - Correção de segurança

Os patches de segurança contêm apenas correções de segurança. Eles foram projetados para tornar o processo de atualização mais rápido e fácil.

Os patches de segurança usam a convenção de nomenclatura do Composer `2.4.x-px`. Use o Composer para especificar um patch.

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## Atualizar metadados

1. Atualize o `"name"`, `"version"`e `"description"` nos campos `composer.json` conforme necessário.

   >[!NOTE]
   >
   >Atualização dos metadados no `composer.json` O arquivo é totalmente superficial e não funcional.

1. Aplicar atualizações.

   ```bash
   composer update
   ```

1. Limpe o `var/` e `generated/` subdiretórios:

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
   >Se você usar um armazenamento de cache diferente do sistema de arquivos, como Redis ou Memcached, também deverá limpar manualmente o cache lá.

1. Atualize o schema e os dados do banco de dados.

   ```bash
   bin/magento setup:upgrade
   ```

1. Desative o modo de manutenção.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Opcional)_ Reinicie o Varnish.

   Se você usar o Varnish para armazenamento em cache de página, reinicie-o:

   ```bash
   service varnish restart
   ```

## Verificar o seu trabalho

Abra o URL da loja em um navegador da Web para verificar se a atualização foi bem-sucedida. Se a atualização não foi bem-sucedida, a loja não será carregada corretamente.

Se o aplicativo falhar com um  `We're sorry, an error has occurred while generating this email.` erro:

1. Redefinir [propriedade e permissões do sistema de arquivos](../../installation/prerequisites/file-system/configure-permissions.md) como um usuário com `root` privilégios.
1. Limpe os seguintes diretórios:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Verifique sua loja no navegador da Web novamente.
