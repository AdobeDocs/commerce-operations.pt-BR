---
title: Relatórios de dependência
description: Crie relatórios que mostram os totais das dependências de módulo, circular e estrutura.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---


# Relatórios de dependência

{{file-system-owner}}

Você pode executar os seguintes tipos de relatórios:

- **Dependências do módulo**: Mostra o número total de dependências entre módulos e se as dependências são permanentes ou suaves.
- **Dependências circulares**: Mostra o número total de cadeias de dependência e o número e a lista de dependências circulares para cada módulo.
- **Dependências de estrutura**: Mostra o número total de dependências na estrutura do Commerce por módulo (incluindo o número total de entradas da estrutura para cada biblioteca).

Uma dependência em um comentário também é uma dependência.

## Executar relatórios de dependência

Opções de comando:

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

A tabela a seguir explica as opções, parâmetros e valores desse comando.

| Parâmetro | Valor | Obrigatório? |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | Relatório de dependências do módulo. | Sim |
| `show-modules-circular` | Relatório de dependências circulares. | Sim |
| `show-framework` | Relatório de dependências de estrutura. | Sim |
| `-d --directory` | Caminho para o diretório base para iniciar a pesquisa de dados do relatório. | Não |
| `-o --output` | Especifica o caminho absoluto do sistema de arquivos e o nome do arquivo de saída do valor separado por vírgulas (csv) para o relatório. | Não |

Se nenhum diretório ou nome de arquivo for passado como um argumento, a seguinte raiz de aplicativo será usada como o diretório padrão e os seguintes nomes de arquivo padrão serão usados:

| Comando | Nome do arquivo |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### Relatório de dependências do módulo de exemplo

A seguir, uma parte da saída de um exemplo de relatório de dependências do módulo:

```terminal
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### Relatório de dependências circulares de exemplo

A seguir, uma parte da saída de um exemplo de relatório de dependências circulares:

```terminal
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### Relatório de dependências da estrutura de exemplo

A seguir, uma parte da saída de um exemplo de relatório de dependências de estrutura:

```terminal
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
