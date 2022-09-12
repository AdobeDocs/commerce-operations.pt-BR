---
title: Ativar ou desativar módulos
description: Siga estas etapas para gerenciar módulos Adobe Commerce ou Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Ativar ou desativar módulos

Este comando não tem pré-requisitos.

## Status do módulo

Use o seguinte comando para listar os módulos ativados e desativados:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Onde

* `--enabled` lista todos os módulos ativados.
* `--disabled` lista todos os módulos desativados.
* `<module-list>` é uma lista de módulos delimitada por espaços para verificar o status. Se algum [módulo](https://glossary.magento.com/module) contém caracteres especiais, coloque o nome entre aspas simples ou duplas.

## Ativar módulo, desativar

Para ativar ou desativar os módulos disponíveis, use o seguinte comando:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Onde

* `<module-list>` é uma lista de módulos delimitada por espaços para ativar ou desativar. Se algum [módulo](https://glossary.magento.com/module) contém caracteres especiais, coloque o nome entre aspas simples ou duplas.
* `--all` para ativar ou desativar todos os módulos ao mesmo tempo.
* `-f` ou `--force` para forçar um módulo a ser ativado ou desativado apesar das dependências. Antes de usar essa opção, consulte [Sobre a ativação e desativação de módulos](#about-enabling-and-disabling-modules).
* `-c` ou `--clear-static-content` limpadores [arquivos de visualização estática gerados](../../configuration/cli/static-view-file-deployment.md).

   A falha na limpeza de arquivos de visualização estática pode resultar em problemas se houver vários arquivos com o mesmo nome e você não limpar todos eles.

   Em outras palavras, por causa do [fallback de arquivo estático](../../configuration/cli/static-view-file-deployment.md) se você não limpar arquivos estáticos e houver mais de um arquivo chamado `logo.svg` que são diferentes, o fallback pode fazer com que o arquivo incorreto seja exibido.

Por exemplo, para desativar o `Magento_Weee` módulo, digite:

```bash
bin/magento module:disable Magento_Weee
```

Para obter informações importantes sobre a ativação e desativação de módulos, consulte [Sobre a ativação e desativação de módulos](#about-enabling-and-disabling-modules).

## Atualizar o banco de dados

Se você ativou um ou mais módulos, execute o seguinte comando para atualizar o banco de dados:

```bash
bin/magento setup:upgrade
```

Em seguida, limpe o cache:

```bash
bin/magento cache:clean
```

## Sobre a ativação e desativação de módulos

O Adobe Commerce e o Magento Open Source permitem que você ative ou desative os módulos atualmente disponíveis; em outras palavras, qualquer módulo fornecido pelo Adobe ou qualquer módulo de terceiros que esteja disponível no momento.

Determinados módulos têm dependências em outros módulos, nesse caso, talvez você não consiga habilitar ou desabilitar um módulo porque ele tem dependências em outros módulos.

Além disso, pode haver *conflitante* módulos que não podem ser habilitados ao mesmo tempo.

Exemplos:

* O módulo A depende do módulo B. Não é possível desativar o Módulo B a menos que você desative primeiro o Módulo A.

* O módulo A depende do módulo B, ambos desativados. Você deve habilitar o módulo B antes de habilitar o módulo A.

* O Módulo A está em conflito com o Módulo B. Você pode desativar o Módulo A e o Módulo B, ou pode desativar qualquer um dos módulos, mas *cannot* ativar simultaneamente os módulos A e B.

* As dependências são declaradas na variável `require` no Adobe Commerce e no Magento Open Source `composer.json` para cada módulo. Os conflitos são declarados no `conflict` em módulos&#39; `composer.json` arquivos. Usamos essas informações para criar um gráfico de dependência: `A->B` significa que o módulo A depende do módulo B.

* A *cadeia de dependência* é o caminho de um módulo para outro. Por exemplo, se o módulo A depende do módulo B e o módulo B depende do módulo C, a cadeia de dependência é `A->B->C`.

Se você tentar ativar ou desativar um módulo que depende de outros módulos, o gráfico de dependência será exibido na mensagem de erro.

>[!NOTE]
>
>É possível que o módulo A `composer.json` declara um conflito com o módulo B, mas não o contrário.

*Somente linha de comando:* Para forçar um módulo a ser ativado ou desativado, independentemente de suas dependências, use o `--force` argumento .

>[!NOTE]
>
>Usando `--force` O pode desativar a loja e causar problemas ao acessar o Administrador.
