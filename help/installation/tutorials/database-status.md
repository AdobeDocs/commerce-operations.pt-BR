---
title: Verificar o status do banco de dados
description: Siga estas etapas para verificar o status do banco de dados do Adobe Commerce ou Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---


# Verificar o status do banco de dados

Antes de executar este comando, é necessário [Criar ou atualizar a configuração de implantação](deployment.md).

## Uso de comandos

Para verificar o status do banco de dados.

```bash
bin/magento setup:db:status
```

Este comando não tem argumentos ou opções.

Exemplo de saída:

```terminal
All modules are up to date.
```

O comando retorna um dos seguintes códigos de saída:

| Código de saída | Descrição | Ação sugerida |
|--------------|--------------|---------------|
| 0 | Normal | Nenhum |
| 1 | Alguns módulos usam versões de código mais recentes ou mais antigas que o banco de dados | Executar [`magento setup:upgrade`](database-upgrade.md) para atualizar o schema do banco de dados e executar `composer update` no diretório raiz do aplicativo para atualizar dependências do componente |
| 2 | `magento setup:upgrade` é obrigatório | [`magento setup:upgrade`](database-upgrade.md) para atualizar o schema do banco de dados |
