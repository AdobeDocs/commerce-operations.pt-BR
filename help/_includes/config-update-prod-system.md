---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
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

   Para obter opções adicionais, como a capacidade de definir uma lista de permissões de endereço IP, consulte [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Interromper todos os trabalhadores em execução configurando `cron_run` para `false` in `app/etc/env.php` do seguinte modo:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Atualize a configuração.

   ```bash
   bin/magento app:config:import
   ```

1. Por último, `kill` quaisquer processos ativos do consumidor.

   ```bash
   kill <PID>
   ```

   Onde `PID` é a ID do processo a ser eliminada, por exemplo:

   ```bash
   kill 1234
   ```

1. Extrair código do controle de origem.

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

1. Encerrar modo de manutenção.

   ```bash
   bin/magento maintenance:disable
   ```
