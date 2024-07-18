---
title: '[!DNL Upgrade Compatibility Tool] relatórios'
description: Siga estas etapas para executar o  [!DNL Upgrade Compatibility Tool] no seu projeto do Adobe Commerce.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# Relatórios

{{commerce-only}}

Como resultado da análise, o [!DNL Upgrade Compatibility Tool] pode exportar um relatório que contém uma lista de problemas para cada arquivo especificando sua gravidade, código de erro e descrição do erro. O [!DNL Upgrade Compatibility Tool] exporta o relatório em dois formatos diferentes:

- Um [arquivo JSON](reports.md#json-file).
- Um [relatório de HTML](reports.md#html-report).

Consulte o seguinte exemplo de interface de linha de comando de um relatório:

```
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Verifique o tópico [Referência da mensagem de erro](../upgrade-compatibility-tool/error-messages.md) para obter mais informações sobre os diferentes erros que este relatório pode produzir.

Esse relatório também inclui um resumo detalhado que mostra:

- *Versão atual*: a versão instalada atualmente.
- *Versão de Destino*: a versão para a qual você deseja atualizar.
- *Tempo de execução*: o tempo que a análise levou para criar o relatório (mm:ss).
- *Módulos que exigem atualização*: a porcentagem de módulos que contêm problemas de compatibilidade e exigem atualização.
- *Arquivos que exigem atualização*: a porcentagem de arquivos que contêm problemas de compatibilidade e exigem atualização.
- *Total de erros críticos*: o número de erros críticos encontrados.
- *Total de erros*: o número de erros encontrados.
- *Total de avisos*: o número de avisos encontrados.
- *Uso máximo de memória*: a quantidade máxima de memória que [!DNL Upgrade Compatibility Tool] atingiu durante a execução.

Consulte o seguinte exemplo de interface de linha de comando:

```
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

Você pode obter a saída do arquivo JSON ao executar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando. O arquivo `JSON` contém exatamente as mesmas informações mostradas na saída [!DNL Upgrade Compatibility Tool]:

- Uma lista de problemas identificados.
- Um resumo da análise.

Para cada problema encontrado, o relatório fornece informações detalhadas, como a gravidade e a descrição do problema.

Para exportar este arquivo `JSON` para uma pasta de saída diferente:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: diretório de instalação do Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Diretório do caminho para exportar o arquivo de saída `JSON`.

>[!NOTE]
>
> O caminho padrão para a pasta de saída é `var/output/[TIME]-results.json`.

## relatório HTML

Você pode obter o relatório de HTML ao executar a ferramenta em uma interface de linha de comando ou por meio do [!DNL Site-Wide Analysis Tool]. O relatório HTML também contém:

- Uma lista de problemas identificados.
- Um resumo da análise.

![Relatório de HTML - Resumo](../../assets/upgrade-guide/uct-html-summary.png)

Navegue facilmente pelos problemas identificados durante a análise [!DNL Upgrade Compatibility Tool].

Você pode filtrar os problemas exibidos no relatório de acordo com o nível mínimo de problema (o valor padrão é `WARNING`).

Há uma lista suspensa no canto superior direito que permite selecionar um nível diferente. A lista de problemas identificados é filtrada de acordo.

![relatório de HTML - Uso suspenso](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Os problemas com nível de problema mais baixo são eliminados, mas você recebe uma notificação para que esteja sempre ciente dos problemas identificados por módulo.

O relatório HTML também inclui quatro gráficos diferentes:

- **Módulos por severidade de problema**: mostra a distribuição de severidade por módulos.
- **Arquivos por severidade de problema**: mostra a distribuição de severidade por arquivos.
- **Módulos ordenados por número total de problemas**: mostra os 10 módulos mais comprometidos levando em conta avisos, erros e erros críticos.
- **Módulos com problemas e tamanhos relativos**: quanto mais arquivos um módulo contiver, maior será seu círculo. Quanto mais problemas um módulo tiver, mais vermelho será seu círculo.

Esses gráficos permitem identificar os módulos mais comprometidos e os que exigem mais trabalho para executar uma atualização.

![Relatório de HTML - Diagramas](../../assets/upgrade-guide/uct-html-diagrams.png)

Os diagramas de relatório de HTML também são atualizados de acordo, com a única exceção de `Modules with relative sizes and issues`, que é gerada com o `min-issue-level` que foi configurado originalmente.

Se quiser ver resultados diferentes para o diagrama `Modules with relative sizes and issues`, execute novamente o comando fornecendo outro valor para a opção `--min-issue-level`.

![Relatório de HTML - Diagrama de Gráfico de Bolhas](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Para exportar esse relatório de HTML para uma pasta de saída diferente:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: diretório de instalação do Adobe Commerce.
- `[=HTML-OUTPUT-PATH]`: Diretório do caminho para exportar o arquivo de saída `.html`.

>[!NOTE]
>
> O caminho padrão para a pasta de saída é `var/output/[TIME]-results.html`.
