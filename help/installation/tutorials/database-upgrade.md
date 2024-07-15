---
title: Atualizar o esquema e os dados do banco de dados
description: Siga estas etapas para atualizar o esquema do banco de dados do Adobe Commerce.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Atualizar o esquema e os dados do banco de dados

Antes de usar este comando, você deve [instalar o aplicativo](../advanced.md).

## Atualizar o esquema e os dados do banco de dados

Sempre que você executar uma ação que faça com que o esquema ou os dados do banco de dados sejam alterados, você deverá atualizá-los executando o comando discutido nesta seção. Uma lista parcial dos motivos a seguir:

* Você atualizou o aplicativo usando a linha de comando
* Você instalou ou atualizou um componente usando a linha de comando
* Você ativou ou desativou um componente usando a linha de comando

>[!NOTE]
>
>Um *componente* pode ser um módulo, tema ou pacote de idiomas; não importa se o componente vem ou não do Commerce Marketplace.

1. Inicie a atualização:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Onde `--keep-generated` é um argumento opcional que não atualiza [arquivos de exibição estáticos](../../configuration/cli/static-view-file-deployment.md). Este argumento opcional é para uso de *somente* em circunstâncias limitadas por integradores de sistema experientes. Ele deve ser usado *somente* no [modo de produção](../../configuration/bootstrap/application-modes.md#production-mode). Ele deve *não* ser usado no [modo de desenvolvedor](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```
