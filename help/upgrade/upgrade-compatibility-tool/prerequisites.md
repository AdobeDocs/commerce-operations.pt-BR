---
title: Pré-requisitos da ferramenta de compatibilidade de atualização
description: 'Verifique se o sistema atende aos requisitos necessários para executar a Ferramenta de compatibilidade de atualização para seu projeto do Adobe Commerce. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Pré-requisitos da Ferramenta de Compatibilidade de Atualização

A execução da Ferramenta de Compatibilidade de Atualização ajuda a identificar o que deve ser feito **before** atualizando sua versão do Adobe Commerce.

Os requisitos mínimos para executar a Ferramenta de Compatibilidade de Atualização são:

| **Requisitos** | **Restrições** |
|----------------|-----------------|
| versão PHP | >= 7.3 |
| Composer | nenhum |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Limitações de memória | Pelo menos 2 GB de RAM |
| Chaves de acesso do Adobe Commerce | nenhum |
| Adobe Commerce (fonte aberta ou empresa) | nenhum |

Você pode executar a Ferramenta de compatibilidade de atualização em qualquer sistema operacional. Não há requisito para executar a Ferramenta de Compatibilidade de Atualização, onde a instância do Adobe Commerce está localizada.

É necessário que a Ferramenta de Compatibilidade de Atualização tenha acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalá-lo em um servidor e apontá-lo na instalação do Adobe Commerce em outro servidor. Consulte a [instalar](../upgrade-compatibility-tool/install.md) para obter mais informações.
