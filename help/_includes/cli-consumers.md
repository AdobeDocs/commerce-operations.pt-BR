---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# Opções de CLI para consumidores da fila de mensagens

| Nome | Descrição | Valor | Obrigatório |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Determina se os consumidores aguardarão uma mensagem da fila. | 1 - Sim, 0 - Não | Não |

* `0`: Os consumidores processam as mensagens disponíveis na fila, fecham a conexão TCP e terminam. Os consumidores não esperam que mensagens adicionais entrem na fila, mesmo se o número de mensagens processadas for menor que o valor `--max_messages` especificado durante a inicialização de consumidores.

* `1`: Os consumidores continuam a processar mensagens da fila de mensagens até atingir o número máximo de mensagens (o valor especificado para `--max_messages` no comando `queue:consumers:start`) antes de fechar a conexão TCP e encerrar o processo do consumidor. Se a fila ficar vazia antes de atingir `--max_messages`, o consumidor aguarda a chegada de mais mensagens. Se você usar trabalhadores para executar consumidores em vez de usar um trabalho cron, defina essa variável como `1`.

>[!WARNING]
>
>A opção `--consumers-wait-for-messages` é global e não pode ser configurada separadamente para cada consumidor.
