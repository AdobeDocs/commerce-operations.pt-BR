---
title: Verificar o status do banco de dados
description: Siga estas etapas para verificar o status do banco de dados do Adobe Commerce.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%
---
# Verificar o status do banco de dados

Antes de executar este comando, você deve [Criar ou atualizar a configuração de implantação](deployment.md).

## Uso do comando

Para verificar o status do banco de dados.

```shell
bin/magento setup:db:status
```

Este comando não tem argumentos ou opções.

Este é um exemplo de saída:

```text
All modules are up to date.
```

O comando retorna um dos seguintes códigos de saída:

| Código de saída | Descrição | Ação sugerida |
|--------------|--------------|---------------|
| 0 | Normal | Nenhum |
| 1 | Alguns módulos usam versões de código mais recentes ou mais antigas que o banco de dados | Execute [`magento setup:upgrade`](database-upgrade.md) para atualizar o esquema de banco de dados e execute `composer update` a partir do diretório raiz do aplicativo para atualizar as dependências de componente |
| 2 | `magento setup:upgrade` é obrigatório | [`magento setup:upgrade`](database-upgrade.md) para atualizar o esquema do banco de dados |
