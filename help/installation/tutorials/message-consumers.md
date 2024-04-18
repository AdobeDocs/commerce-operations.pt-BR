---
title: Configurar consumidores de mensagem
description: Siga estas etapas para configurar o comportamento dos consumidores da fila de mensagens do Adobe Commerce.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
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
