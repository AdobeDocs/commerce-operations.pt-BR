---
title: '[!DNL Upgrade Compatibility Tool] relatórios'
description: Siga estas etapas para executar a [!DNL Upgrade Compatibility Tool] no seu projeto do Adobe Commerce.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Relatórios

{{commerce-only}}

Em resultado da análise, o [!DNL Upgrade Compatibility Tool] O pode exportar um relatório que contém uma lista de problemas para cada arquivo especificando sua gravidade, código de erro e descrição do erro. A variável [!DNL Upgrade Compatibility Tool] O exporta o relatório em dois formatos diferentes:

- A [Arquivo JSON](reports.md#json-file).
- Um [relatório HTML](reports.md#html-report).

Consulte o seguinte exemplo de interface de linha de comando de um relatório:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Verifique a [Referência da mensagem de erro](../upgrade-compatibility-tool/error-messages.md) tópico para obter mais informações sobre os diferentes erros que este relatório pode produzir.

Esse relatório também inclui um resumo detalhado que mostra:

- *Versão atual*: a versão instalada no momento.
- *Versão de destino*: a versão para a qual você deseja atualizar.
- *Tempo de execução*: a quantidade de tempo que a análise levou para criar o relatório (mm:ss).
- *Módulos que exigem atualização*: a porcentagem de módulos que contêm problemas de compatibilidade e exigem atualização.
- *Arquivos que exigem atualização*: a porcentagem de arquivos que contêm problemas de compatibilidade e exigem atualização.
- *Total de erros críticos*: o número de erros críticos encontrados.
- *Total de erros*: o número de erros encontrados.
- *Total de avisos*: o número de avisos encontrados.
- *Uso máximo de memória*: a quantidade máxima de memória do [!DNL Upgrade Compatibility Tool] foi atingido durante a execução.

Consulte o seguinte exemplo de interface de linha de comando:

```terminal
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## Arquivo JSON

Você pode obter a saída do arquivo JSON ao executar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando. A variável `JSON` arquivo contém exatamente as mesmas informações mostradas no [!DNL Upgrade Compatibility Tool] saída:

- Uma lista de problemas identificados.
- Um resumo da análise.

Para cada problema encontrado, o relatório fornece informações detalhadas, como a gravidade e a descrição do problema.

Para exportar este `JSON` em uma pasta de saída diferente:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: diretório de instalação do Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Diretório do caminho para exportar o `JSON` arquivo de saída.

>[!NOTE]
>
> O caminho padrão para a pasta de saída é `var/output/[TIME]-results.json`.

## relatório HTML

Você pode obter o relatório de HTML ao executar a ferramenta em uma interface de linha de comando ou por meio da [!DNL Site-Wide Analysis Tool]. O relatório HTML também contém:

- Uma lista de problemas identificados.
- Um resumo da análise.

![Relatório HTML - Resumo](../../assets/upgrade-guide/uct-html-summary.png)

É possível navegar facilmente pelos problemas identificados durante o [!DNL Upgrade Compatibility Tool] análise.

Você pode filtrar os problemas exibidos no relatório de acordo com o nível mínimo de problema (o valor padrão é `WARNING`).

Há uma lista suspensa no canto superior direito que permite selecionar um nível diferente. A lista de problemas identificados é filtrada de acordo.

![Relatório de HTML - Uso suspenso](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Os problemas com nível de problema mais baixo são eliminados, mas você recebe uma notificação para que esteja sempre ciente dos problemas identificados por módulo.

O relatório HTML também inclui quatro gráficos diferentes:

- **Módulos por gravidade de problema**: mostra a distribuição de severidade por módulos.
- **Arquivos por gravidade de problema**: mostra a distribuição de severidade por arquivos.
- **Módulos ordenados pelo número total de problemas**: mostra os 10 módulos mais comprometidos levando em conta avisos, erros e erros críticos.
- **Módulos com tamanhos relativos e problemas**: Quanto mais arquivos um módulo contiver, maior será o círculo. Quanto mais problemas um módulo tiver, mais vermelho será seu círculo.

Esses gráficos permitem identificar os módulos mais comprometidos e os que exigem mais trabalho para executar uma atualização.

![Relatório de HTML - Diagramas](../../assets/upgrade-guide/uct-html-diagrams.png)

Os diagramas dos relatórios de HTML também são atualizados em conformidade, com a única exceção do `Modules with relative sizes and issues`, que é gerado com o `min-issue-level` que foi originalmente configurado.

Se quiser ver resultados diferentes para o `Modules with relative sizes and issues` diagrama, você deve executar novamente o comando fornecendo outro valor para a variável `--min-issue-level` opção.

![Relatório de HTML - Diagrama de Gráfico de Bolhas](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Para exportar esse relatório de HTML para uma pasta de saída diferente:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: diretório de instalação do Adobe Commerce.
- `[=HTML-OUTPUT-PATH]`: Diretório do caminho para exportar o `.html` arquivo de saída.

>[!NOTE]
>
> O caminho padrão para a pasta de saída é `var/output/[TIME]-results.html`.
