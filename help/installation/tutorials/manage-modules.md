---
title: Ativar ou desativar módulos
description: Siga estas etapas para gerenciar módulos Adobe Commerce ou Magento Open Source.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: 6e87d68df97adf47b5a61e8b6683ac11f600806c
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# Ativar ou desativar módulos

Esse comando não tem pré-requisitos.

## Status do módulo

Use o seguinte comando para listar módulos habilitados e desabilitados:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Onde

* `--enabled` lista todos os módulos habilitados.
* `--disabled` lista todos os módulos desativados.
* `<module-list>` é uma lista de módulos delimitada por espaços para verificar o status. Se qualquer nome de módulo contiver caracteres especiais, coloque o nome entre aspas simples ou duplas.

>[!NOTE]
>
>Não é possível habilitar ou desabilitar módulos diretamente em projetos na nuvem. Você deve executar esses comandos localmente e depois enviar as alterações para o `app/etc/config.php` arquivo para um ambiente. Consulte [Fluxo de trabalho de projeto Pro: Fluxo de trabalho de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## Módulo ativar, desativar

Para ativar ou desativar os módulos disponíveis, use o seguinte comando:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Onde

* `<module-list>` é uma lista de módulos delimitada por espaços para ativar ou desativar o. Se qualquer nome de módulo contiver caracteres especiais, coloque o nome entre aspas simples ou duplas.
* `--all` para ativar ou desativar todos os módulos ao mesmo tempo.
* `-f` ou `--force` para forçar um módulo a ser ativado ou desativado apesar das dependências. Antes de usar essa opção, consulte [Sobre a ativação e desativação de módulos](#about-enabling-and-disabling-modules).
* `-c` ou `--clear-static-content` limpa [arquivos de visualização estáticos gerados](../../configuration/cli/static-view-file-deployment.md).

  A falha na limpeza de arquivos de exibição estáticos pode resultar em problemas se houver vários arquivos com o mesmo nome e você não limpar todos eles.

  Por outras palavras, devido à [fallback de arquivo estático](../../configuration/cli/static-view-file-deployment.md) regras, se você não limpar arquivos estáticos e houver mais de um arquivo chamado `logo.svg` que são diferentes, o fallback pode fazer com que o arquivo errado seja exibido.

Por exemplo, para desativar o `Magento_Weee` módulo, insira:

```bash
bin/magento module:disable Magento_Weee
```

Para obter informações importantes sobre como ativar e desativar módulos, consulte [Sobre a ativação e desativação de módulos](#about-enabling-and-disabling-modules).

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

O Adobe Commerce e o Magento Open Source permitem ativar ou desativar módulos disponíveis no momento; em outras palavras, qualquer módulo fornecido por Adobe ou qualquer módulo de terceiros disponível no momento.

Determinados módulos têm dependências em outros módulos, nesse caso, você não pode ativar ou desativar um módulo porque ele tem dependências em outros módulos.

Além disso, pode haver *conflitante* módulos que não podem ser ativados ao mesmo tempo.

Exemplos:

* O módulo A depende do módulo B. Você não pode desativar o módulo B a menos que primeiro desative o módulo A.

* O módulo A depende do módulo B, que está desativado. Você deve ativar o módulo B antes de ativar o módulo A.

* O módulo A está em conflito com o módulo B. Você pode desativar os Módulos A e B ou pode desativar os módulos, mas *não é possível* Ative os módulos A e B ao mesmo tempo.

* As dependências são declaradas no `require` no Adobe Commerce e no Magento Open Source `composer.json` para cada módulo. Os conflitos são declarados no `conflict` campo em módulos&#39; `composer.json` arquivos. Usamos essas informações para criar um gráfico de dependências: `A->B` o módulo A depende do módulo B.

* A *cadeia de dependências* é o caminho de um módulo para outro. Por exemplo, se o módulo A depende do módulo B, e o módulo B depende do módulo C, a cadeia de dependência é `A->B->C`.

Se você tentar ativar ou desativar um módulo que depende de outros módulos, o gráfico de dependência é exibido na mensagem de erro.

>[!NOTE]
>
>É possível que o módulo A `composer.json` declara um conflito com o módulo B, mas não o inverso.

*Somente linha de comando:* Para forçar um módulo a ser ativado ou desativado independentemente de suas dependências, use o `--force` argumento.

>[!NOTE]
>
>Usar `--force` O pode desabilitar seu armazenamento e causar problemas ao acessar o Administrador.
