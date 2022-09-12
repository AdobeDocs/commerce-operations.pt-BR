---
title: Configurar o provedor de bloqueio
description: Siga estas etapas para impedir que trabalhos do cron e grupos do cron duplicados sejam executados em sua implantação do Adobe Commerce ou do Magento Open Source.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurar o provedor de bloqueio

Antes de executar esse comando, faça o seguinte *ou* você deve [instale o aplicativo](../advanced.md):

* [Criar ou atualizar a configuração de implantação](deployment.md)
* [Criar o esquema do banco de dados](database.md)

## Instalação segura

{{$include /help/_includes/secure-install.md}}

## Configurar o bloqueio

Configure um provedor de bloqueio para impedir a inicialização de trabalhos cron duplicados e grupos cron. (Requer Adobe Commerce ou Magento Open Source 2.2.x, 2.2.5 e posterior e 2.3.3 e posterior.)

O Adobe Commerce e o Magento Open Source usam o banco de dados para salvar bloqueios por padrão. Se você tiver vários nós em seus servidores, recomendamos usar o Zookeeper como provedor de bloqueio.

Se você estiver executando o Adobe Commerce na infraestrutura de nuvem, não será necessário definir as configurações do provedor de bloqueio. O aplicativo configura o provedor de bloqueio de arquivos para projetos Pro durante o processo de provisionamento. Consulte [Variáveis da nuvem](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Uso de comandos

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrições dos parâmetros

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--lock-provider` | Bloquear nome do provedor: `db`, `zookeeper`ou `file`.<br><br>O provedor de bloqueio padrão: `db` | Não |
| `--lock-db-prefix` | O prefixo específico do db para evitar conflitos de bloqueio ao usar o `db` bloqueio do provedor.<br><br>O valor padrão: `NULL` | Não |
| `--lock-zookeeper-host` | Host e porta para se conectar ao cluster Zookeeper ao usar o `zookeeper` bloqueio do provedor.<br><br>Por exemplo: `127.0.0.1:2181` | Sim, se você definir `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | O caminho onde o Zookeeper salva os bloqueios.<br><br>O caminho padrão é: `/magento/locks` | Não |
| `--lock-file-path` | O caminho onde os bloqueios de arquivo são salvos. | Sim, se você definir `--lock-provider=file` |
