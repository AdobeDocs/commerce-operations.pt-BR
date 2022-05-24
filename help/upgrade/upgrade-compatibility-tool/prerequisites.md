---
title: '"[!DNL Upgrade Compatibility Tool] Pré-requisitos"'
description: 'Verifique se o sistema atende aos requisitos necessários para executar o [!DNL Upgrade Compatibility Tool] para seu projeto do Adobe Commerce. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] pré-requisitos

{{commerce-only}}

Os requisitos mínimos para executar o [!DNL Upgrade Compatibility Tool] são:

| **Requisitos** | **Restrições** |
|----------------|-----------------|
| versão PHP | >= 7.3 |
| Composer | nenhum |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Limitações de memória | Pelo menos 2 GB de RAM |
| Chaves de acesso do Adobe Commerce | nenhum |
| Adobe Commerce | nenhum |

Você pode executar o [!DNL Upgrade Compatibility Tool] em vários sistemas operacionais (o Windows não é compatível). Você não precisa executar a variável [!DNL Upgrade Compatibility Tool] onde a instância do Adobe Commerce está localizada.

É necessário [!DNL Upgrade Compatibility Tool] para ter acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalá-lo em um servidor e apontá-lo na instalação do Adobe Commerce em outro servidor. Consulte a [instalar](../upgrade-compatibility-tool/install.md) para obter mais informações.

Se você estiver executando o [!DNL Upgrade Compatibility Tool] em relação a uma instância do Adobe Commerce com módulos e arquivos grandes, a ferramenta pode exigir uma quantidade alta de RAM (pelo menos 2 GB). Você pode usar o `[=MODULE-PATH]` no seu comando para especificar o diretório do caminho do módulo para evitar problemas devido a uma limitação de memória baixa:

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.
- `[=MODULE-PATH]`: Diretório de caminho do módulo específico.
