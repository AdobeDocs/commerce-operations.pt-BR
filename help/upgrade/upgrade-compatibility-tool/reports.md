---
title: '"[!DNL Upgrade Compatibility Tool] relatórios"'
description: Siga estas etapas para executar o [!DNL Upgrade Compatibility Tool] no seu projeto do Adobe Commerce.
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Relatórios

{{commerce-only}}

Como resultado da análise, a variável [!DNL Upgrade Compatibility Tool] exporta um relatório que contém uma lista de problemas para cada arquivo especificando sua gravidade, código de erro e descrição do erro.

Veja o exemplo abaixo:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Verifique a [Referência da mensagem de erro](../upgrade-compatibility-tool/error-messages.md) para obter mais informações.

O relatório também inclui um resumo detalhado que mostra:

- *Versão atual*: a versão atualmente instalada.
- *Versão de destino*: a versão para a qual você deseja atualizar.
- *Tempo de execução*: o tempo que a análise levou para criar o relatório (mm:ss).
- *Módulos que exigem atualização*: a porcentagem de módulos que contêm problemas de compatibilidade e exigem atualização.
- *Arquivos que exigem atualização*: a porcentagem de arquivos que contêm problemas de compatibilidade e exigem atualização.
- *Total de erros críticos*: o número de erros críticos encontrados.
- *Total de erros*: o número de erros encontrados.
- *Total de avisos*: o número de avisos encontrados.

Veja o exemplo abaixo:

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>Por padrão, a variável [!DNL Upgrade Compatibility Tool] exporta o relatório para dois formatos diferentes: `json` e `html`.

## Arquivo JSON

O arquivo JSON contém exatamente as mesmas informações mostradas na saída:

- Lista dos problemas identificados.
- Resumo da análise.

Para cada problema encontrado, o relatório fornece informações detalhadas como a gravidade e a descrição do problema.

Para exportar este relatório para uma pasta de saída diferente, execute:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Diretório de caminho para exportar o `.json` arquivo de saída.

>[!NOTE]
>
>O caminho padrão da pasta de saída é `var/output/[TIME]-results.json`.

## relatório HTML

O arquivo HTML também contém o resumo da análise e a lista de problemas identificados. Você pode obter o relatório do HTML ao executar a ferramenta em uma interface de linha de comando ou através do [!DNL Site-Wide Analysis Tool].

![Relatório HTML - Resumo](../../assets/upgrade-guide/uct-html-summary.png)

Você pode navegar facilmente pelos problemas identificados durante a [!DNL Upgrade Compatibility Tool] análise:

![Relatório HTML - Detalhes](../../assets/upgrade-guide/uct-html-details.png)

O relatório HTML também inclui quatro gráficos diferentes:

- **Módulos por gravidade de problema**: Mostra a distribuição de severidade por módulos.
- **Arquivos por gravidade de problema**: Mostra a distribuição de severidade por arquivos.
- **Módulos ordenados pelo número total de problemas**: Mostra os 10 módulos mais comprometidos levando em conta avisos, erros e erros críticos.
- **Módulos com tamanhos e problemas relativos**: Quanto mais arquivos um módulo contiver, maior será seu círculo. Quanto mais problemas um módulo tiver, mais vermelho será o seu círculo.

Esses gráficos permitem identificar (imediatamente) as partes mais comprometidas e as que exigem mais trabalho para executar uma atualização.

![Relatório HTML - Diagramas](../../assets/upgrade-guide/uct-html-diagrams.png)

Você pode filtrar os problemas mostrados no relatório de acordo com o nível mínimo de edição. O valor padrão é `WARNING`.

Há uma lista suspensa no canto superior direito que permitirá selecionar outra de acordo com suas necessidades. A lista de problemas identificados será filtrada adequadamente.

![Relatório de HTML - Uso suspenso](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

Observe que os problemas com nível de problema mais baixo são eliminados, mas você recebe uma notificação para que esteja sempre ciente dos problemas identificados por módulo.

Os diagramas também são atualizados adequadamente, com a única exceção da variável `Modules with relative sizes and issues`, que é gerado com o `min-issue-level` configurada originalmente.

Se quiser ver resultados diferentes, será necessário executar novamente o comando fornecendo outro valor para a variável `--min-issue-level` opção.

![Relatório HTML - Diagrama do gráfico de bolhas](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Para exportar este relatório para uma pasta de saída diferente, execute:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Onde os argumentos são os seguintes:

- `<dir>`: {{site.data.var.ee}} diretório de instalação.
- `[=HTML-OUTPUT-PATH]`: Diretório de caminho para exportar o `.html` arquivo de saída.

>[!NOTE]
>
> O caminho padrão da pasta de saída é `var/output/[TIME]-results.html`.
