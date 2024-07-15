---
title: Ativar a criação de perfil
description: Saiba mais sobre como ativar o MAGE Profiler para uso com suas ferramentas analíticas.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Ativar a criação de perfil

Com a criação de perfil do Commerce, você pode:

- Ative um profiler integrado.

  Você pode usar um profiler integrado com o Commerce para executar tarefas como analisar o desempenho. A natureza da criação de perfil depende das ferramentas analíticas que você usa. Oferecemos suporte para múltiplos formatos, inclusive o HTML. Quando você habilita o profiler, um arquivo `var/profiler.flag` é gerado indicando que o profiler está habilitado e as configurações. Quando desativado, este arquivo é excluído.

- Exiba gráficos de dependência em uma página do Commerce.

  Um _gráfico de dependência_ é uma lista de dependências de objeto e todas as suas dependências, todas as dependências para essas dependências e assim por diante.

  Você deve estar particularmente interessado na lista de _dependências não utilizadas_, que são objetos que foram criados porque foram solicitados em algum construtor, mas nunca foram usados (isto é, nenhum de seus métodos foi chamado). Como resultado, o tempo e a memória do processador gastos para criar essas dependências são desperdiçados.

O Commerce fornece a funcionalidade base em [`Magento\Framework\Profiler`][profiler].

Você pode ativar e configurar o profiler usando uma variável MAGE_PROFILER ou a linha de comando.

## Definir MAGE_PROFILER

Você pode definir o valor de `MAGE_PROFILER` de qualquer uma das formas discutidas em [Definir o valor dos parâmetros de inicialização](../bootstrap/set-parameters.md).

`MAGE_PROFILER` dá suporte aos seguintes valores:

- `1` para habilitar a saída de um criador de perfil específico.

  Você pode usar um dos valores a seguir para ativar um profiler específico:

   - `csvfile` que usa [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Qualquer outro valor (exceto `2`), incluindo um valor vazio, que use [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` para habilitar gráficos de dependência.

  Os gráficos de dependência normalmente são exibidos na parte inferior de uma página. A figura a seguir mostra parte da saída:

  ![Gráficos de dependência](../../assets/configuration/depend-graphs.png)

## Comandos da CLI

Você pode ativar ou desativar o profiler usando comandos CLI:

- `dev:profiler:enable <type>` habilita o criador de perfil com `type` de `html` (padrão) ou `csvfile`. Quando habilitado, um arquivo de sinalizador `var/profiler.flag` é criado.
- `dev:profiler:disable` desabilita o criador de perfil. Quando desabilitado, o arquivo de sinalizador `var/profiler.flag` é removido.

Para ativar gráficos de dependência, use a opção de variável.

**Para habilitar ou desabilitar o criador de perfil**:

1. Faça logon no servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Como proprietário do sistema de arquivos, ative o profiler:

   Para habilitar o criador de perfil usando o tipo `html` e criar um arquivo de sinalizador:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Para habilitar o criador de perfil usando o tipo `csvfile` e criar um arquivo de sinalizador:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   A saída é salva em `<project-root>/var/log/profiler.csv`. O `profiler.csv` é substituído em cada atualização de página.

   Para desativar o profiler e remover o arquivo de sinalização:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
