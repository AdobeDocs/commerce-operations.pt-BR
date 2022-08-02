---
title: Ativar criação de perfis
description: Saiba mais sobre como habilitar o MAGE Profiler para usar com suas ferramentas analíticas.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Ativar criação de perfis

Com a criação de perfis do Commerce, você pode:

- Ative um criador de perfis integrado.

   Você pode usar um criador de perfis integrado com o Commerce para executar tarefas como analisar o desempenho. A natureza da criação de perfis depende das ferramentas analíticas que você usa. Oferecemos suporte para vários formatos, incluindo o HTML. Ao ativar o criador de perfis, uma `var/profiler.flag` O arquivo é gerado indicando que o criador de perfis está ativado e as configurações. Quando desativado, este arquivo é excluído.

- Exibir gráficos de dependência em uma página de Comércio.

   A _gráfico de dependências_ é uma lista de dependências de objetos e todas as suas dependências, e todas as dependências dessas dependências, e assim por diante.

   Você deve estar particularmente interessado na lista de _dependências não usadas_, que são objetos que foram criados porque foram solicitados em algum construtor, mas nunca foram usados (ou seja, nenhum de seus métodos foi chamado). Como resultado, o tempo e a memória do processador gastos para criar essas dependências são desperdiçados.

O Commerce fornece a funcionalidade básica em [`Magento\Framework\Profiler`][profiler].

Você pode ativar e configurar o criador de perfis usando uma variável MAGE_PROFILER ou a linha de comando.

## Definir MAGE_PROFILER

Você pode definir o valor de `MAGE_PROFILER` de qualquer uma das formas discutidas no [Definir o valor dos parâmetros de inicialização](../bootstrap/set-parameters.md).

`MAGE_PROFILER` O suporta os seguintes valores:

- `1` para ativar a saída de um perfil específico.

   Você pode usar um dos seguintes valores para ativar um criador de perfil específico:

   - `csvfile` que usa [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Qualquer outro valor (exceto `2`), incluindo um valor vazio, que usa [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` para ativar gráficos de dependência.

   Os gráficos de dependência normalmente são exibidos na parte inferior de uma página. A figura a seguir mostra parte da saída:

   ![Gráficos de dependência](../../assets/configuration/depend-graphs.png)

## Comandos CLI

Você pode ativar ou desativar o criador de perfis usando comandos CLI:

- `dev:profiler:enable <type>` ativa o criador de perfis com `type` de `html` (padrão) ou `csvfile`. Quando ativado, um arquivo sinalizador `var/profiler.flag` é criada.
- `dev:profiler:disable` desativa o criador de perfis. Quando desativado, o arquivo sinalizador `var/profiler.flag` for removido.

Para ativar gráficos de dependência, use a opção de variável .

**Para ativar ou desativar o criador de perfis**:

1. Faça logon no seu servidor do Commerce.
1. Altere para o diretório de instalação do Commerce.
1. Como proprietário do sistema de arquivos, ative o criador de perfis:

   Para ativar o criador de perfis usando o tipo `html` e criar um arquivo sinalizador:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Para ativar o criador de perfis usando o tipo `csvfile` e criar um arquivo sinalizador:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   A saída é salva em `<project-root>/var/log/profiler.csv`. O `profiler.csv` é substituída em cada atualização de página.

   Para desativar o criador de perfis e remover o arquivo sinalizador:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
