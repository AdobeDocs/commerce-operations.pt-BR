---
title: Configurar o provedor de bloqueio
description: Siga estas etapas para impedir que os trabalhos cron duplicados e os grupos cron sejam executados na implantação do Adobe Commerce ou Magento Open Source.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Configurar o provedor de bloqueio

Antes de executar este comando, faça o seguinte *ou* você deve [instalar o aplicativo](../advanced.md):

* [Criar ou atualizar a configuração de implantação](deployment.md)
* [Criar o esquema de banco de dados](database.md)

## Instalação segura

{{$include /help/_includes/secure-install.md}}

## Configurar o bloqueio

Configure um provedor de bloqueio para impedir a inicialização de trabalhos cron duplicados e grupos cron. (Exige Adobe Commerce ou Magento Open Source 2.2.x, 2.2.5 e posterior, e 2.3.3 e posterior.)

O Adobe Commerce usa o banco de dados para salvar bloqueios por padrão. Se você tiver vários nós em seus servidores, recomendamos usar o Zookeeper como provedor de bloqueio.

Se você estiver executando o Adobe Commerce na infraestrutura em nuvem, não será necessário definir as configurações do provedor de bloqueio. O aplicativo configura o provedor de bloqueio de arquivo para projetos Pro durante o processo de provisionamento. Consulte [Variáveis da nuvem](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Uso do comando

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrições de parâmetro

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--lock-provider` | Nome do provedor de bloqueio: `db`, `zookeeper`ou `file`.<br><br>O provedor de bloqueio padrão: `db` | Não |
| `--lock-db-prefix` | O prefixo do banco de dados específico para evitar conflitos de bloqueio ao usar o `db` provedor de bloqueio.<br><br>O valor padrão: `NULL` | Não |
| `--lock-zookeeper-host` | Host e porta para conectar-se ao cluster do Zookeeper quando você usa o `zookeeper` provedor de bloqueio.<br><br>Por exemplo: `127.0.0.1:2181` | Sim, se você definir `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | O caminho onde o Zookeeper salva bloqueios.<br><br>O caminho padrão é: `/magento/locks` | Não |
| `--lock-file-path` | O caminho onde os bloqueios de arquivo são salvos. | Sim, se você definir `--lock-provider=file` |
