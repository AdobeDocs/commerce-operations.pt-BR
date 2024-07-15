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

1. Interrompa todos os trabalhos em execução definindo de `cron_run` a `false` em `app/etc/env.php` da seguinte maneira:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Atualize a configuração.

   ```bash
   bin/magento app:config:import
   ```

1. Finalmente, `kill` qualquer processo de consumidor ativo.

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
