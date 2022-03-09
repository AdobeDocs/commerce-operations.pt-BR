---
title: '"[!DNL Upgrade Compatibility Tool] Pré-requisitos"'
description: 'Verifique se o sistema atende aos requisitos necessários para executar o [!DNL Upgrade Compatibility Tool] para seu projeto do Adobe Commerce. '
source-git-commit: c4769b555df49ed2f0b2fffbeaf458c5a64816ba
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] pré-requisitos

{{commerce-only}}

Executar o [!DNL Upgrade Compatibility Tool] ajuda a identificar o que deve ser feito **before** atualizando sua versão do Adobe Commerce.

Os requisitos mínimos para executar o [!DNL Upgrade Compatibility Tool] são:

| **Requisitos** | **Restrições** |
|----------------|-----------------|
| versão PHP | >= 7.3 |
| Composer | nenhum |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Limitações de memória | Pelo menos 2 GB de RAM |
| Chaves de acesso do Adobe Commerce | nenhum |
| Adobe Commerce | nenhum |

Você pode executar o [!DNL Upgrade Compatibility Tool] em qualquer sistema operacional. Não há necessidade de executar o [!DNL Upgrade Compatibility Tool] onde a instância do Adobe Commerce está localizada.

É necessário [!DNL Upgrade Compatibility Tool] para ter acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalá-lo em um servidor e apontá-lo na instalação do Adobe Commerce em outro servidor. Consulte a [instalar](../upgrade-compatibility-tool/install.md) para obter mais informações.

Se você estiver executando o [!DNL Upgrade Compatibility Tool] em relação a uma instância do Adobe Commerce com módulos e arquivos grandes, a ferramenta pode exigir uma quantidade alta de RAM, pelo menos 2 GB de RAM.
