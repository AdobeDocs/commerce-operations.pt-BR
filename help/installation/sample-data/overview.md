---
title: Visão geral dos dados de exemplo
description: Saiba mais sobre como usar dados de amostra para projetos do Adobe Commerce.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Visão geral dos dados de exemplo

Dados de amostra fornecem uma loja com base no tema Luma equipado com produtos, categorias, registro de clientes e assim por diante. Ele funciona como uma loja da Commerce e você pode manipular preços, inventário e regras de preços promocionais usando o Administrador.

>[!NOTE]
>
>Para revisar e analisar o banco de dados e vários recursos, considere usar dados reais em vez de dados de amostra. Os dados de amostra são projetados como uma simulação de loja pré-gerada, para demonstrar o design do tema e o comportamento básico da loja. Todas as entidades de dados de amostra são gravadas diretamente nas tabelas do banco de dados, enquanto dados de amostra são instalados.

Você pode instalar os dados de amostra antes ou depois de instalar o software Commerce. Quando terminar de usar os dados de exemplo, você poderá removê-los ou instalá-los novamente, conforme discutido em [Remover módulos de dados de exemplo ou atualizar dados de exemplo](remove-or-update.md).

>[!WARNING]
>
>Não é possível desinstalar dados de exemplo. Use dados de amostra somente para saber como o Adobe Commerce funciona. Evite fazer qualquer desenvolvimento em um sistema no qual você instalou dados de amostra.

Você pode instalar dados de amostra opcionais de qualquer uma das seguintes maneiras:

| Método de instalação | Descrição | Nível de habilidade necessário |
|--- |--- |--- |
| Uso do Composer | [Execute `magento sampledata:deploy` para modificar a raiz do aplicativo `composer.json`](composer-packages.md) para habilitar módulos de dados de exemplo. | Requer conhecimento sobre o Composer e acesso ao sistema de arquivos do Commerce. |
| Clonagem de repositórios | [Clonar o repositório GitHub](git-repositories.md) e o repositório de dados de exemplo e vinculá-los. | Somente para desenvolvedores contribuintes. Todos os outros usuários devem usar um dos métodos anteriores. |
