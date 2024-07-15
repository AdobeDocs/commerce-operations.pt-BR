---
title: Verificar o status do banco de dados
description: Siga estas etapas para verificar o status do banco de dados do Adobe Commerce.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# Verificar o status do banco de dados

Antes de executar este comando, você deve [Criar ou atualizar a configuração de implantação](deployment.md).

## Uso do comando

Para verificar o status do banco de dados.

```bash
bin/magento setup:db:status
```

Este comando não tem argumentos ou opções.

Este é um exemplo de saída:

```terminal
All modules are up to date.
```

O comando retorna um dos seguintes códigos de saída:

| Código de saída | Descrição | Ação sugerida |
|--------------|--------------|---------------|
| 0 | Normal | Nenhum |
| 1 | Alguns módulos usam versões de código mais recentes ou mais antigas que o banco de dados | Execute [`magento setup:upgrade`](database-upgrade.md) para atualizar o esquema de banco de dados e execute `composer update` a partir do diretório raiz do aplicativo para atualizar as dependências de componente |
| 2 | `magento setup:upgrade` é obrigatório | [`magento setup:upgrade`](database-upgrade.md) para atualizar o esquema do banco de dados |
