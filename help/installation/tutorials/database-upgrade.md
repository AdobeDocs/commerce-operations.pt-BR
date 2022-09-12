---
title: Atualizar o esquema e os dados do banco de dados
description: Siga estas etapas para atualizar seu esquema de banco de dados Adobe Commerce ou Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Atualizar o esquema e os dados do banco de dados

Antes de usar esse comando, é necessário [instale o aplicativo](../advanced.md).

## Atualizar o esquema e os dados do banco de dados

Sempre que você executar uma ação que causa a variável [esquema de banco de dados](https://glossary.magento.com/database-schema) Para os dados a serem alterados, é necessário atualizá-los executando o comando discutido nesta seção. Uma lista parcial de motivos é exibida a seguir:

* Você atualizou o aplicativo usando a linha de comando
* Você instalou ou atualizou um componente usando a linha de comando
* Você ativou ou desativou um componente usando a linha de comando

>[!NOTE]
>
>A *componente* pode ser um módulo, tema ou pacote de idiomas; não importa se o componente vem do Commerce Marketplace ou não.

1. Inicie a atualização:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Onde `--keep-generated` é um argumento opcional que não é atualizado [arquivos de visualização estática](../../configuration/cli/static-view-file-deployment.md). Esse argumento opcional é para uso *only* em circunstâncias limitadas por integradores de sistema experientes. Deve ser utilizado *only* em [modo de produção](../../configuration/bootstrap/application-modes.md#production-mode). Deveria *not* ser usada em [modo desenvolvedor](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```
