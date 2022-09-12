---
title: Configurar consumidores de mensagem
description: Siga estas etapas para configurar o comportamento dos consumidores de fila de mensagens do Adobe Commerce ou Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---


# Configurar consumidores de mensagem

Antes de executar esse comando, faça o seguinte *ou* você deve [instale o aplicativo](../advanced.md):

* [Criar ou atualizar a configuração de implantação](deployment.md)
* [Criar o esquema do banco de dados](database.md)

## Configurar o comportamento dos consumidores

A configuração do comportamento do consumidor é feita enviando pares de chave/valor na função de configuração:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrições dos parâmetros

{{$include /help/_includes/cli-consumers.md}}
