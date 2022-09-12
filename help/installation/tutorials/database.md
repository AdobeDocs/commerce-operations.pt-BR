---
title: Criar o esquema do banco de dados
description: Siga estas etapas para criar um banco de dados para seu Adobe Commerce ou Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Criar o esquema do banco de dados

Antes de executar este comando, é necessário [Criar ou atualizar a configuração de implantação](deployment.md).

## Configurar o banco de dados e adicionar dados

Uso do comando:

```bash
bin/magento setup:db-schema:upgrade
```

Para ver o status do banco de dados, insira

```bash
bin/magento setup:db:status
```
