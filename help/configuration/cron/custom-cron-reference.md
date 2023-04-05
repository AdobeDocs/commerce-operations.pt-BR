---
title: Referência de trabalho de cron personalizado e de grupo de cron
description: Saiba como personalizar crons usando grupos cron.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Personalização de referência de crons

Este tópico ajuda a configurar crontabs e, opcionalmente, criar grupos para módulos personalizados. Se o módulo personalizado precisar agendar tarefas periodicamente, você deve configurar um crontab para esse módulo. A _crontab_ é uma configuração de trabalho cron.

Como opção, você pode configurar um grupo personalizado, que, entre outras coisas, permite executar trabalhos cron definidos nesse grupo independentemente de outros trabalhos cron.

Para obter um tutorial passo a passo, consulte [Configurar trabalhos do cron personalizados e grupos do cron (tutorial)](custom-cron-tutorial.md).

Para obter uma visão geral sobre trabalhos do cron, consulte [Configurar trabalhos do cron](../cli/configure-cron-jobs.md).

## Configurar grupos cron

Esta seção discute como, opcionalmente, criar um grupo cron para um módulo personalizado. Se não precisar fazer isso, continue com a próxima seção.

A _grupo cron_ é um grupo lógico que permite executar facilmente o cron por mais de um processo por vez. A maioria dos módulos de Comércio usam o `default` grupo cron; alguns módulos usam o `index` grupo.

Se estiver implementando o cron para um módulo personalizado, você pode optar por usar a variável `default` ou um grupo diferente.

**Para configurar um grupo cron para o seu módulo**:

Crie um `crontab.xml` no diretório do módulo:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

Para um grupo, o arquivo deve ter o seguinte conteúdo:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

Em que:

| Valor | Descrição |
|---|---|
| `group_name` | Nome do grupo cron. O nome do grupo não precisa ser exclusivo. Você pode executar o cron para um grupo de cada vez. |
| `job_name` | ID exclusiva para este trabalho cron. |
| `classpath` | Classe a ser instanciada (classpath). |
| `method` | Método em `classpath` para chamar. |
| `time` | Agendar no formato cron. Omita esse parâmetro se o agendamento estiver definido no banco de dados do Commerce ou em outro armazenamento. |

O resultado `crontab.xml` com dois grupos, pode ser semelhante a:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Como exemplo, consulte [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Especificação de opções de grupo Cron

Você pode declarar um novo grupo e especificar suas opções de configuração (todas executadas no escopo de visualização da loja) por meio do `cron_groups.xml` arquivo, localizado em:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Veja abaixo um exemplo da variável `cron_groups.xml` arquivo:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

Em que:

| Opção | Descrição |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Frequência (em minutos) que os agendamentos são gravados no `cron_schedule` tabela. |
| `schedule_ahead_for` | O tempo (em minutos) antes de as programações serem gravadas no `cron_schedule` tabela. |
| `schedule_lifetime` | Janela de tempo (em minutos) que um trabalho cron deve iniciar ou o trabalho cron é considerado perdido (&quot;muito tarde&quot; para ser executado). |
| `history_cleanup_every` | Tempo (em minutos) que o histórico do cron é mantido no banco de dados. |
| `history_success_lifetime` | O tempo (em minutos) em que o registro de tarefas cron concluídas com êxito é mantido no banco de dados. |
| `history_failure_lifetime` | Tempo (em minutos) que o registro de tarefas cron com falha é mantido no banco de dados. |
| `use_separate_process` | Execute as tarefas deste grupo de cron em um processo de php separado |

## Desativar um trabalho de cron

As tarefas Cron não têm um `disable` como temos para [observadores](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). No entanto, um trabalho cron pode ser desativado usando a seguinte técnica: `schedule` uma hora que contenha uma data que nunca acontecerá.

Por exemplo, desative o `visitor_clean` trabalho cron definido em `Magento_Customer` módulo:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Para desativar o `visitor_clean` tarefa do cron, crie um módulo personalizado e reescreva o `visitor_clean` trabalho cron `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Agora, o `visitor_clean` o trabalho cron foi definido para ser executado às 00:00 no dia 30 de fevereiro - na data que nunca ocorrerá.
