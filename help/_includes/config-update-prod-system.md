---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---
# Atualizar sistema de produção

**Para atualizar o sistema de produção**:

1. Faça logon no sistema de produção como proprietário do sistema de arquivos.
1. Altere para a raiz do aplicativo e habilite o modo de manutenção.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Para obter opções adicionais, como a capacidade de definir uma lista de permissões de endereço IP, consulte [`magento maintenance:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Interrompa todos os trabalhadores da fila em execução definindo `cron_run` para `false` em `app/etc/env.php` como se segue:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Atualize a configuração.

   ```bash
   bin/magento app:config:import
   ```

1. Por último, `kill` Qualquer processo ativo do consumidor.

   ```bash
   kill <PID>
   ```

   Onde `PID` é a ID do processo que deve ser eliminada, por exemplo:

   ```bash
   kill 1234
   ```

1. Puxe o código do controle de origem.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Atualize a configuração.

   ```bash
   bin/magento app:config:import
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:clean
   ```

1. Encerre o modo de manutenção.

   ```bash
   bin/magento maintenance:disable
   ```
