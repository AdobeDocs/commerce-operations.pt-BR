---
title: Entender o escopo de atualização
description: Saiba mais sobre as alterações incompatíveis com o passado em uma versão que podem afetar os módulos personalizados do Adobe Commerce ou Magento Open Source ou extensões de terceiros.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# Entender o escopo da atualização

Revise o [notas de versão](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) para compreender o escopo de uma versão, incluindo aprimoramentos, correções de bugs e problemas conhecidos que podem afetar módulos de terceiros e personalizados.

## Alterações retroativas incompatíveis

As versões do Adobe Commerce e do Magento Open Source podem conter alterações incompatíveis com o passado. Revise nossa documentação de alterações incompatíveis com o passado, consulte o seguinte:

- **[Principais destaques das mudanças](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)**—Alterações que tenham grande impacto e exijam explicações detalhadas e instruções especiais para garantir que os módulos de terceiros continuem funcionando.
- **[Referência de pequenas alterações](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)**—Documentação de referência gerada a partir da base de código que descreve pequenas alterações nas classes, associação à API, banco de dados, injeção de dependência, interfaces, layouts, sistema e XSD.

## Extensões de terceiros

A nova política de compatibilidade do Adobe Commerce Marketplace garante que _all_ as extensões listadas são compatíveis com a versão mais recente lançada dentro de 30 dias da data do GA. Por isso, é importante obter suas extensões de terceiros, sempre que possível, por meio do Marketplace.

## Módulos personalizados

Todos os módulos personalizados devem ser verificados em relação à versão de destino para a qual você deseja atualizar. Esse é o processo que utiliza mais tempo e recursos de uma atualização. Ao avaliar seus módulos personalizados, você deve procurar alterações incompatíveis com o passado e estar ciente de novas práticas, como a decomposição do controlador. Você pode saber mais sobre isso na seção [notas de versão](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Além disso, verifique se você está seguindo [práticas recomendadas](https://devdocs.magento.com/guides/v2.4/ext-best-practices/extension-coding/common-programming-bp.html) para desenvolvimento de módulo.

## Ferramenta de compatibilidade de atualização

A Ferramenta de compatibilidade de atualização é uma ferramenta de linha de comando que analisa sua instância para possíveis problemas de atualização. Verifica se há problemas entre a versão atual que você instalou e a versão para a qual você está tentando atualizar.

Usar essa ferramenta reduz o esforço necessário de sua equipe para entender o escopo e o impacto de uma atualização. Ajuda a evitar problemas comuns de código ao atualizar e fornece uma direção clara sobre como resolver problemas identificados. Também ajuda a priorizar os problemas mais críticos necessários para garantir uma atualização bem-sucedida, economizando tempo e custos ao atualizar.

Consulte as seções a seguir para começar a usar a Ferramenta de compatibilidade de atualização. Consulte a Ferramenta de compatibilidade de atualização [guia](../upgrade-compatibility-tool/overview.md) para obter mais detalhes técnicos e casos de uso avançado.

### Download da ferramenta

Use o Composer para baixar a ferramenta. Ele requer PHP 7.3 ou posterior, pelo menos 2 GB de RAM, Node.js (se você estiver verificando a compatibilidade de GraphQL) e uma licença Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Executar a ferramenta

Para analisar sua instância e verificar se há erros, avisos e problemas críticos:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> O `<dir>` argumento é o diretório onde sua base de código é armazenada. O `-c` compara sua base de código com a versão especificada (por exemplo, 2.4.4).

Para identificar os problemas mais críticos que sua equipe deve abordar:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Mais algumas opções a serem usadas com este comando são:

- `--ignore-current-version-compatibility-issues`—Suprime todos os problemas críticos, erros e avisos conhecidos em relação à sua versão atual. Ela só fornece erros em relação à versão que você está tentando atualizar.

- `--min-issue-level`—Permite definir o nível mínimo de problema para ajudar a priorizar apenas os problemas mais importantes com sua atualização. As opções são aviso, erro e crítico em ordem crescente de gravidade.

- `-m | [=MODULE-PATH]`—Se você quiser analisar apenas um determinado fornecedor, módulo ou diretório par, também poderá especificar o caminho como uma opção.

- `--vanilla-dir`—Permite verificar o código principal para qualquer implementação não padrão de recursos ou personalizações. É importante que estas sejam previamente limpas. Uma instância baunilha da sua versão é baixada automaticamente para referência.

   >[!NOTE]
   >
   > Isso também pode ser feito com o `core:code:changes` na ferramenta).

### Analisar a saída

A Ferramenta de compatibilidade de atualização exporta um arquivo JSON identificando o código ou módulos afetados, a severidade e uma descrição do problema para cada problema encontrado. Ele também gera um relatório resumido com uma pontuação de complexidade, que permite que sua equipe entenda aproximadamente o que é necessário para atualizar para a versão mais recente. Quanto menor a pontuação de complexidade, mais fácil será executar a atualização.

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

Todos os problemas identificados pela ferramenta são listados no relatório com códigos de erro específicos. Use o [referência da mensagem de erro](../upgrade-compatibility-tool/error-messages.md) para obter mais detalhes sobre cada problema. O Adobe também fornece sugestões para corrigir cada tipo de problema para que você possa planejar suas etapas de correção.

Use o relatório para estimar a quantidade de esforço que será necessário para atualizar seu código para a atualização. Com base na sua experiência, você pode estimar o esforço necessário para atualizar com base no número total de problemas identificados e na gravidade dos problemas. Como essa é uma ferramenta de linha de comando, você pode incorporar isso em testes automatizados e conjuntos de verificação de código e usar a saída JSON para gerar seus relatórios.

Recomendamos salvar os resultados de cada projeto de atualização para que você possa comparar resultados de atualização futuros com resultados anteriores. Com o uso contínuo, você começará a desenvolver um bom senso do nível de esforço necessário para atualizar para a próxima versão a partir do relatório resumido fornecido pela ferramenta.

Também recomendamos que você execute a ferramenta regularmente enquanto trabalha na atualização para ter visibilidade sobre seu progresso. O número de problemas deve diminuir à medida que você os corrige. Isso também ajuda sua equipe a decidir a melhor abordagem para distribuir trabalho.

As versões futuras da ferramenta incorporarão testes de compatibilidade e autocorreções do PHP 8.1 para ajudar você a corrigir problemas o mais rápido possível.
