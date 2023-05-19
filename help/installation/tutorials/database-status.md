---
title: Verificar o status do banco de dados
description: Siga estas etapas para verificar o status do banco de dados Adobe Commerce ou Magento Open Source.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

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
| 1 | Alguns módulos usam versões de código mais recentes ou mais antigas que o banco de dados | Executar [`magento setup:upgrade`](database-upgrade.md) para atualizar o esquema do banco de dados e executar `composer update` do diretório raiz do aplicativo para atualizar dependências de componentes |
| 2 | `magento setup:upgrade` é obrigatório | [`magento setup:upgrade`](database-upgrade.md) para atualizar o esquema do banco de dados |
