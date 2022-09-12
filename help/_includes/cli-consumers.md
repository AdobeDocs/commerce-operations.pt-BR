---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Opções de CLI para consumidores de fila de mensagens

| Nome | Descrição | Valor | Obrigatório |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Determina se os consumidores esperarão por uma mensagem da fila. | 1 - Sim, 0 - Não | Não |

* `0`: Os consumidores processam as mensagens disponíveis na fila, fecham a conexão TCP e encerram. Os consumidores não esperam mensagens adicionais para entrar na fila, mesmo se o número de mensagens processadas for menor que o `--max_messages` valor especificado durante o início dos consumidores.

* `1`: Os consumidores continuam a processar mensagens da fila de mensagens até atingir o número máximo de mensagens (o valor especificado para `--max_messages` no `queue:consumers:start` ) antes de fechar a conexão TCP e encerrar o processo do consumidor. Se a fila estiver vazia antes de chegar `--max_messages` o consumidor espera mais mensagens para chegar. Se você usar trabalhadores para executar consumidores em vez de usar um trabalho cron, defina essa variável como `1`.

>[!WARNING]
>
>O `--consumers-wait-for-messages` é uma opção global e não pode ser configurada separadamente para cada consumidor.
