---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Atualizar sistema de produção

**Para atualizar o sistema de produção**:

1. Faça logon no sistema de produção como proprietário do sistema de arquivos.
1. Altere para a raiz do aplicativo e habilite o modo de manutenção.

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   Para obter opções adicionais, como a capacidade de definir uma lista de permissões de endereço IP, consulte [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Interrompa todos os trabalhos em execução definindo de `cron_run` a `false` em `app/etc/env.php` da seguinte maneira:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Atualize a configuração.

   ```shell
   bin/magento app:config:import
   ```

1. Finalmente, `kill` qualquer processo de consumidor ativo.

   ```shell
   kill <PID>
   ```

   Onde `PID` é a ID do processo a ser eliminada, por exemplo:

   ```shell
   kill 1234
   ```

1. Extrair código do controle de origem.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Atualize a configuração.

   ```shell
   bin/magento app:config:import
   ```

1. Limpe o cache.

   ```shell
   bin/magento cache:clean
   ```

1. Encerrar modo de manutenção.

   ```shell
   bin/magento maintenance:disable
   ```
