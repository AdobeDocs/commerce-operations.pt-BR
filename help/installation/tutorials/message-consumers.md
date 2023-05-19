---
title: Configurar consumidores de mensagem
description: Siga estas etapas para configurar o comportamento dos consumidores de fila de mensagens do Adobe Commerce ou Magento Open Source.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Configurar consumidores de mensagem

Antes de executar este comando, faça o seguinte *ou* você deve [instalar o aplicativo](../advanced.md):

* [Criar ou atualizar a configuração de implantação](deployment.md)
* [Criar o esquema de banco de dados](database.md)

## Configurar o comportamento dos consumidores

A configuração do comportamento do consumidor é feita enviando pares de chave/valor dentro da função de configuração:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrições de parâmetro

{{$include /help/_includes/cli-consumers.md}}
