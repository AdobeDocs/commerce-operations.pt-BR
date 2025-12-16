---
title: Migração do RabbitMQ para AtiveMQ
description: Saiba como substituir o agente de fila de mensagens usado para instalações locais do Adobe Commerce.
feature: Services, Configuration
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# Migração para o AtiveMQ

O AtiveMQ (Apache AtiveMQ Artemis) é um agente de mensagens multiprotocolo de alto desempenho que fornece uma alternativa ao RabbitMQ para lidar com filas de mensagens no Adobe Commerce.

A partir de 2.4.8-p3, 2.4.7-p8, 2.4.6-p13 e 2.4.5-p16, o Adobe Commerce oferece suporte ao AtiveMQ como um agente de fila de mensagens. Isso proporciona flexibilidade adicional para que instalações locais escolham entre RabbitMQ e AtiveMQ com base em seus requisitos de infraestrutura e experiência.

## Antes de começar

Antes de iniciar a migração, verifique o seguinte:

1. Examine sua configuração atual do RabbitMQ em `app/etc/env.php`.
1. Faça um backup completo do banco de dados e da base de código.
1. Certifique-se de que sua instalação atenda aos requisitos de sistema do AtiveMQ.
1. Planeje uma janela de manutenção para concluir a migração.

## Caminho de migração

A migração para o AtiveMQ é um processo simples, mas é essencial garantir que todas as mensagens pendentes sejam processadas antes de alternar os agentes.

Essas instruções de migração presumem que o Adobe Commerce é o único aplicativo que utiliza o agente de fila de mensagens.

### Etapa 1: colocar o site no Modo de manutenção

1. Coloque o site em [Modo de Manutenção](../../installation/tutorials/maintenance-mode.md):

   ```bash
   bin/magento maintenance:enable
   ```

1. Verifique se o modo de manutenção está habilitado:

   ```bash
   bin/magento maintenance:status
   ```

### Etapa 2: Verificar contagens de mensagens do RabbitMQ

Antes de continuar, verifique se todas as mensagens no RabbitMQ foram processadas. Use um dos seguintes métodos:

#### Método A: Usando o Painel de Gerenciamento do RabbitMQ

1. Acessar a interface de gerenciamento do RabbitMQ em `http://<host>:15672`
1. Credenciais padrão: `guest/guest`
1. Navegue até a guia **Filas**
1. Verificar se todas as filas mostram **0 mensagens**

   ![Painel de Gerenciamento do RabbitMQ](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### Método B: usar a linha de comando rabbitmqctl

1. Verificar todas as filas e suas contagens de mensagens:

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="Saída CLI do RabbitMQ" width="500" />

1. Verifique as informações detalhadas da fila:

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="Saída detalhada do RabbitMQ CLI" width="500" />

### Etapa 3: Processar mensagens pendentes

Se as mensagens estiverem pendentes em qualquer fila, processe-as antes de continuar.

1. Obtenha a lista de consumidores disponíveis:

   ```bash
   bin/magento queue:consumers:list
   ```

1. Processar consumidores como um grupo ou por fila de mensagens individual:

   - **Processar consumidores como um grupo**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >Se o cron já estiver em execução no sistema, não será necessário executar o `bin/magento cron:run --group=consumers` manualmente. Em vez disso, verifique se as mensagens estão sendo processadas verificando as contagens de mensagens usando os comandos da Etapa 2.

   - **Processar uma fila de mensagens específica**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     Por exemplo, para processar operações assíncronas:

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >O parâmetro `--max-messages` limita o número de mensagens a serem processadas antes que o consumidor pare. Ajuste esse valor com base no tamanho da fila.

   - **Monitorar processamento de mensagens**

     Verificar continuamente as contagens de mensagens até que todas as filas estejam vazias:

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### Etapa 4: verificar se todas as mensagens são processadas

Antes de prosseguir para a próxima etapa, verifique se **todas as filas mostram 0 mensagens**. Execute novamente os comandos de verificação da Etapa 2.

>[!WARNING]
>
>Não avance para a próxima etapa se alguma mensagem permanecer não processada. A perda de dados pode ocorrer se você trocar de corretor enquanto as mensagens ainda estiverem pendentes.

### Etapa 5: Interromper consumidores e trabalhos cron

1. Interromper todos os consumidores de fila de mensagens em execução:

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. Desabilitar trabalhos cron:

   ```bash
   bin/magento cron:remove
   ```

1. Verifique se os trabalhos cron foram removidos:

   ```bash
   crontab -l
   ```

### Etapa 6: Fazer backup da configuração atual

Crie um backup da configuração atual:

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### Etapa 7: opcionalmente, desinstalar o RabbitMQ

Você pode desinstalar o RabbitMQ se ele não for mais necessário.

### Etapa 8: instalar e configurar o AtiveMQ no Adobe Commerce

Para concluir tarefas de instalação e configuração do AtiveMQ, como configuração do protocolo STOMP e verificação da conexão, consulte o [Guia de Instalação e Configuração](../../installation/prerequisites/activemq.md).

### Etapa 9: reinstalar trabalhos cron

1. Após a conclusão bem-sucedida do teste, reinstale os trabalhos cron:

   ```bash
   bin/magento cron:install
   ```

1. Verifique se os trabalhos cron estão agendados:

   ```bash
   crontab -l
   ```

### Etapa 10: Desativar modo de manutenção

1. Depois de verificar se tudo está funcionando corretamente, desative o modo de manutenção:

   ```bash
   bin/magento maintenance:disable
   ```

1. Verifique se o modo de manutenção está desabilitado:

   ```bash
   bin/magento maintenance:status
   ```

### Etapa 11: Monitorar o sistema

Monitore o sistema por 24 a 48 horas após a migração para garantir que todas as operações de fila estejam funcionando corretamente:

- Verifique regularmente a taxa de transferência de mensagens no Console Web do AtiveMQ
- Monitorar logs de aplicativos em busca de erros relacionados à fila
- Verificar se as operações assíncronas (salvamentos de configuração, exportações etc.) estão funcionando
- Verifique os logs CRON para garantir que os consumidores estejam em execução

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## Reversão

Se ocorrerem problemas durante ou após a migração, você poderá reverter para o RabbitMQ:

1. Habilitar modo de manutenção:

   ```bash
   bin/magento maintenance:enable
   ```

1. Parar todos os consumidores e desabilitar cron:

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. Restaurar a configuração anterior:

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. Iniciar RabbitMQ (se parado):

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. Limpar cache:

   ```bash
   bin/magento cache:flush
   ```

1. Reinstalar cron:

   ```bash
   bin/magento cron:install
   ```

1. Desabilitar modo de manutenção:

   ```bash
   bin/magento maintenance:disable
   ```

Não são necessárias mais alterações no valor de configuração após a conclusão da migração.

