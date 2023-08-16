---
title: Etapas pós-lançamento
description: Use nossa lista de verificação pós-lançamento para garantir uma implementação tranquila do site do Adobe Commerce.
exl-id: 0c3162d9-6475-4b34-9278-e5aea39bd0f9
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---

# Etapas pós-lançamento

Quando o site estiver ativo, essas atividades serão executadas o mais rápido possível para garantir que o site tenha sido iniciado corretamente:

- Ative a ferramenta de monitoramento de tempo de atividade (New Relic), ative as verificações e monitore o site para garantir que todos os serviços e o acesso estejam em verde
- Ativar a verificação de segurança do Adobe Commerce periodicamente
- Marque o cluster como ativo e crie um tíquete de suporte para ativar o monitoramento de Alto SLA
- O CSE (Customer Success Engineer, Engenheiro especializado na fidelização de clientes) e o TAM (Technical Account Manager, Gerente técnico de conta) executam as seguintes tarefas assim que a transferência é concluída:
   - Marque o cluster como Alto SLA para o cliente Adobe Commerce e crie um tíquete de suporte para ativá-lo
   - Ativar as verificações de PKingdom para nomes de domínio
   - Revise o estado do monitoramento e verifique se todos os itens estão em verde
   - Mantenha as partes interessadas informadas sobre a duração e os parâmetros da garantia por email no dia de ativação

![Diagrama que mostra a fase 4 do processo de lançamento](../../assets/playbooks/launch-steps-4.svg)
