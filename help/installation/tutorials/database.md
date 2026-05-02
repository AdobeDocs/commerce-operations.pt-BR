---
title: Criar o esquema de banco de dados
description: Siga estas etapas para criar um banco de dados para seu projeto do Adobe Commerce.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Criar o esquema de banco de dados

Antes de executar este comando, você deve [Criar ou atualizar a configuração de implantação](deployment.md).

## Configurar o banco de dados e adicionar dados

Uso do comando:

```shell
bin/magento setup:db-schema:upgrade
```

Para ver o status do banco de dados, insira

```shell
bin/magento setup:db:status
```
