---
title: Entender o escopo de atualização
description: Saiba mais sobre alterações incompatíveis com versões anteriores em uma versão que pode afetar módulos personalizados do Adobe Commerce ou extensões de terceiros.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Entender o escopo da atualização

Revise as [notas de versão](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) para entender o escopo de uma versão, incluindo aprimoramentos, correções de erros e problemas conhecidos que podem afetar módulos de terceiros e personalizados.

## Alterações incompatíveis com versões anteriores

As versões do Adobe Commerce podem conter alterações incompatíveis com versões anteriores. Revise nossa documentação de alterações incompatíveis com versões anteriores. Consulte o seguinte:

- **[Destaques de alterações importantes](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)**—Alterações que têm grande impacto e exigem explicação detalhada e instruções especiais para garantir que módulos de terceiros continuem funcionando.
- **[Referência de alteração menor](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** — Documentação de referência gerada a partir da base de código que descreve alterações menores em classes, associação de API, banco de dados, injeção de dependência, interfaces, layouts, sistema e XSD.

## Extensões de terceiros

A nova política de compatibilidade do Adobe Commerce Marketplace garante que _todas_ as extensões listadas sejam compatíveis com a versão mais recente lançada dentro de 30 dias da data de disponibilidade geral. Por isso, é importante obter suas extensões de terceiros, sempre que possível, por meio do Marketplace.

## Módulos personalizados

Todos os módulos personalizados devem ser verificados em relação à versão de destino para a qual você deseja atualizar. Esse é o processo de atualização que consome mais tempo e recursos. Ao avaliar seus módulos personalizados, você deve procurar alterações incompatíveis com versões anteriores e estar ciente das novas práticas, como a decomposição do controlador. Você pode saber mais sobre isso nas [notas de versão](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Além disso, verifique se você está seguindo as [práticas recomendadas](https://developer.adobe.com/commerce/php/best-practices/extensions/) para o desenvolvimento de módulo.

## [!DNL Upgrade Compatibility Tool]

O [!DNL Upgrade Compatibility Tool] é uma ferramenta de linha de comando que analisa sua instância em busca de possíveis problemas de atualização. Ele verifica problemas entre a versão atual instalada e a versão para a qual você está tentando atualizar.

O uso dessa ferramenta reduz o esforço necessário de sua equipe para entender o escopo e o impacto de uma atualização. Ele ajuda a evitar problemas comuns de código ao atualizar e fornece instruções claras sobre como resolver problemas identificados. Também ajuda a priorizar os problemas mais críticos necessários para garantir um upgrade bem-sucedido, economizando tempo e custos ao fazer o upgrade.

Consulte as seções a seguir para começar a usar o [!DNL Upgrade Compatibility Tool]. Consulte o [!DNL Upgrade Compatibility Tool] [guia](../upgrade-compatibility-tool/overview.md) para obter mais detalhes técnicos e casos de uso avançados.

### Baixar a ferramenta

Use o Composer para baixar a ferramenta. Ela requer o PHP 7.3 ou posterior, pelo menos 2 GB de RAM, Node.js (se você estiver verificando a compatibilidade com o GraphQL) e uma licença Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Executar a ferramenta

Para analisar sua instância e verificar erros, avisos e problemas críticos:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> O argumento `<dir>` é o diretório onde a base de código está armazenada. A opção `-c` compara sua base de código com a versão especificada.

Para identificar os problemas mais críticos que sua equipe deve solucionar:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Algumas outras opções para usar com este comando são:

- `--ignore-current-version-compatibility-issues` — Suprime todos os problemas críticos, erros e avisos conhecidos em relação à sua versão atual. Ela só fornece erros em relação à versão que você está tentando atualizar.

- `--min-issue-level` — Permite definir o nível mínimo de problema para ajudar a priorizar apenas os problemas mais importantes da atualização. As opções são aviso, erro e crítico em ordem crescente de gravidade.

- `-m | [=MODULE-PATH]` — Se você quiser analisar apenas um determinado fornecedor, módulo ou diretório, também poderá especificar o caminho como uma opção.

- `--vanilla-dir` — Permite que você verifique o código principal de qualquer implementação não padrão de recursos ou personalizações. É importante que estes sejam limpos antecipadamente. Uma instância padrão da sua versão é baixada automaticamente para referência.

  >[!NOTE]
  >
  > Isso também pode ser feito com o comando `core:code:changes` na ferramenta).

### Analisar a saída

O [!DNL Upgrade Compatibility Tool] exporta um arquivo JSON identificando o código ou os módulos afetados, a gravidade e uma descrição do problema para cada problema encontrado. Ele também gera um relatório de resumo com uma pontuação de complexidade, o que permite que sua equipe entenda basicamente o que é necessário para atualizar para a versão mais recente. Quanto menor a pontuação de complexidade, mais fácil será executar a atualização.

A saída a seguir mostra um exemplo de relatório resumido:

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### Dicas e conselhos

Todos os problemas identificados pela ferramenta são listados no relatório com códigos de erro específicos. Use a [referência da mensagem de erro](../upgrade-compatibility-tool/error-messages.md) para obter mais detalhes sobre cada problema. O Adobe também fornece sugestões para corrigir cada tipo de problema para que você possa planejar suas etapas de correção.

Use o relatório para estimar o esforço necessário para atualizar seu código para a atualização. Com base em sua experiência, você pode estimar o esforço necessário para atualizar com base no número total de problemas identificados e na gravidade dos problemas. Como essa é uma ferramenta de linha de comando, você pode incorporá-la aos conjuntos de teste e verificação de código automatizados e usar a saída JSON para gerar seus relatórios.

Recomendamos salvar os resultados de cada projeto de atualização para que você possa comparar os resultados de atualização futuros com os resultados anteriores. Com o uso contínuo, você começará a desenvolver uma boa noção do nível de esforço necessário para atualizar para a próxima versão apenas a partir do relatório de resumo fornecido pela ferramenta.

Também recomendamos que você execute a ferramenta regularmente enquanto trabalha na atualização para ter visibilidade sobre o seu progresso. O número de problemas deve diminuir à medida que forem corrigidos. Isso também ajuda sua equipe a decidir a melhor abordagem para distribuir o trabalho.

O [!DNL Upgrade Compatibility Tool] continua sendo aprimorado e as próximas versões incluirão recursos como correções automáticas para ajudá-lo a corrigir problemas o mais rápido possível. As melhorias mais recentes lançadas em janeiro de 2022 incluem testes de compatibilidade do PHP 8.1 e recursos de visualização de HTML que ajudam a identificar rapidamente áreas que podem exigir mais esforço para atualização.
