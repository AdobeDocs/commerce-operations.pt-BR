---
title: Configurar consumidores de mensagem
description: Siga estas etapas para configurar o comportamento dos consumidores da fila de mensagens do Adobe Commerce.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
last-update: 2026-04-28T00:00:00Z
source-git-commit: 1166b8fbfeef21a51ad6e4e695aed2b25006230e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Configurar consumidores de mensagem

Antes de executar este comando, você deve fazer o seguinte *ou*. Você deve [instalar o aplicativo](../advanced.md):

* [Criar ou atualizar a configuração de implantação](deployment.md)
* [Criar o esquema de banco de dados](database.md)

## Configurar o comportamento dos consumidores

A configuração do comportamento do consumidor é feita enviando pares de chave/valor dentro da função de configuração:

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrições de parâmetro

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
