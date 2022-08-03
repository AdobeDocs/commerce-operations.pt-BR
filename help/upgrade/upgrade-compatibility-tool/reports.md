---
title: '"[!DNL Upgrade Compatibility Tool] relatórios"'
description: Siga estas etapas para executar o [!DNL Upgrade Compatibility Tool] no seu projeto do Adobe Commerce.
source-git-commit: 1ce02c3215b01f64e86383938a257514f0e4257c
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Relatórios

{{commerce-only}}

Como resultado da análise, a variável [!DNL Upgrade Compatibility Tool] O pode exportar um relatório que contenha uma lista de problemas para cada arquivo especificando sua gravidade, código de erro e descrição do erro. O [!DNL Upgrade Compatibility Tool] exporta o relatório para dois formatos diferentes:

- A [Arquivo JSON](reports.md#json-file).
- Um [relatório HTML](reports.md#html-report).

Consulte o seguinte exemplo de interface de linha de comando de um relatório:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Verifique a [Referência da mensagem de erro](../upgrade-compatibility-tool/error-messages.md) para obter mais informações sobre os diferentes erros que esse relatório pode produzir.

Este relatório também inclui um resumo detalhado que mostra:

- *Versão atual*: a versão atualmente instalada.
- *Versão de destino*: a versão para a qual você deseja atualizar.
- *Tempo de execução*: o tempo que a análise levou para criar o relatório (mm:ss).
- *Módulos que exigem atualização*: a porcentagem de módulos que contêm problemas de compatibilidade e exigem atualização.
- *Arquivos que exigem atualização*: a porcentagem de arquivos que contêm problemas de compatibilidade e exigem atualização.
- *Total de erros críticos*: o número de erros críticos encontrados.
- *Total de erros*: o número de erros encontrados.
- *Total de avisos*: o número de avisos encontrados.
- *Uso de pico de memória*: a quantidade máxima de memória [!DNL Upgrade Compatibility Tool] foi atingido durante a execução.

Consulte o exemplo de interface da linha de comando a seguir:

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

Você pode obter a saída do arquivo JSON ao executar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando. O `JSON` O arquivo contém exatamente as mesmas informações mostradas no [!DNL Upgrade Compatibility Tool] output:

- Uma lista de problemas identificados.
- Um resumo da análise.

Para cada problema encontrado, o relatório fornece informações detalhadas como a gravidade e a descrição do problema.

Para exportar isso `JSON` em uma pasta de saída diferente:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Diretório de caminho para exportar o `JSON` arquivo de saída.

>[!NOTE]
>
> O caminho padrão da pasta de saída é `var/output/[TIME]-results.json`.

## relatório HTML

Você pode obter o relatório do HTML ao executar a ferramenta em uma interface de linha de comando ou através do [!DNL Site-Wide Analysis Tool]. O relatório HTML também contém:

- Uma lista de problemas identificados.
- Um resumo da análise.

![Relatório HTML - Resumo](../../assets/upgrade-guide/uct-html-summary.png)

Você pode navegar facilmente pelos problemas identificados durante a [!DNL Upgrade Compatibility Tool] análise.

Você pode filtrar os problemas mostrados no relatório de acordo com o nível mínimo de edição (o valor padrão é `WARNING`).

Há uma lista suspensa no canto superior direito que permite selecionar um nível diferente. A lista de problemas identificados é filtrada adequadamente.

![Relatório de HTML - Uso suspenso](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Os problemas com nível de edição inferior são removidos, mas você recebe uma notificação para que esteja sempre ciente dos problemas identificados por módulo.

O relatório HTML também inclui quatro gráficos diferentes:

- **Módulos por gravidade de problema**: Mostra a distribuição de severidade por módulos.
- **Arquivos por gravidade de problema**: Mostra a distribuição de severidade por arquivos.
- **Módulos ordenados pelo número total de problemas**: Mostra os 10 módulos mais comprometidos levando em conta avisos, erros e erros críticos.
- **Módulos com tamanhos e problemas relativos**: Quanto mais arquivos um módulo contiver, maior será seu círculo. Quanto mais problemas um módulo tiver, mais vermelho será o seu círculo.

Esses gráficos permitem identificar os módulos mais comprometidos e os que exigem mais trabalho para executar uma atualização.

![Relatório HTML - Diagramas](../../assets/upgrade-guide/uct-html-diagrams.png)

Os diagramas de relatório de HTML também são atualizados adequadamente, com a única exceção do `Modules with relative sizes and issues`, que é gerado com o `min-issue-level` que foi criado originalmente.

Se quiser ver resultados diferentes para a variável `Modules with relative sizes and issues` no diagrama, é necessário executar novamente o comando, fornecendo outro valor para o `--min-issue-level` opção.

![Relatório HTML - Diagrama do gráfico de bolhas](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Para exportar esse relatório HTML para uma pasta de saída diferente:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: {{site.data.var.ee}} diretório de instalação.
- `[=HTML-OUTPUT-PATH]`: Diretório de caminho para exportar o `.html` arquivo de saída.

>[!NOTE]
>
> O caminho padrão da pasta de saída é `var/output/[TIME]-results.html`.
