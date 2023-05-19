---
title: Criar o esquema de banco de dados
description: Siga estas etapas para criar um banco de dados para seu Adobe Commerce ou Magento Open Source.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# Criar o esquema de banco de dados

Antes de executar este comando, você deve [Criar ou atualizar a configuração de implantação](deployment.md).

## Configurar o banco de dados e adicionar dados

Uso do comando:

```bash
bin/magento setup:db-schema:upgrade
```

Para ver o status do banco de dados, insira

```bash
bin/magento setup:db:status
```
