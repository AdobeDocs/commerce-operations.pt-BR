---
title: Ativar ou desativar módulos
description: Siga estas etapas para gerenciar módulos do Adobe Commerce.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
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
* `--disabled` lista todos os módulos desabilitados.
* `<module-list>` é uma lista de módulos delimitada por espaços para verificar o status. Se qualquer nome de módulo contiver caracteres especiais, coloque o nome entre aspas simples ou duplas.

>[!NOTE]
>
>Não é possível habilitar ou desabilitar módulos diretamente em projetos na nuvem. Você deve executar esses comandos localmente e depois enviar as alterações para o arquivo `app/etc/config.php` de um ambiente. Consulte [Fluxo de trabalho do projeto Pro: Fluxo de trabalho de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=pt-BR#deployment-workflow).

## Módulo ativar, desativar

Para ativar ou desativar os módulos disponíveis, use o seguinte comando:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Onde

* `<module-list>` é uma lista de módulos delimitada por espaços para ativar ou desativar. Se qualquer nome de módulo contiver caracteres especiais, coloque o nome entre aspas simples ou duplas.
* `--all` para ativar ou desativar todos os módulos ao mesmo tempo.
* `-f` ou `--force` para forçar um módulo a ser habilitado ou desabilitado apesar das dependências. Antes de usar esta opção, consulte [Sobre habilitação e desabilitação de módulos](#about-enabling-and-disabling-modules).
* `-c` ou `--clear-static-content` limpa [arquivos de exibição estáticos gerados](../../configuration/cli/static-view-file-deployment.md).

  A falha na limpeza de arquivos de exibição estáticos pode resultar em problemas se houver vários arquivos com o mesmo nome e você não limpar todos eles.

  Em outras palavras, devido às regras de [fallback de arquivo estático](../../configuration/cli/static-view-file-deployment.md), se você não limpar os arquivos estáticos e houver mais de um arquivo com o nome `logo.svg` que seja diferente, o fallback poderá fazer com que o arquivo errado seja exibido.

Por exemplo, para desabilitar o módulo `Magento_Weee`, digite:

```bash
bin/magento module:disable Magento_Weee
```

Para obter informações importantes sobre habilitação e desabilitação de módulos, consulte [Sobre habilitação e desabilitação de módulos](#about-enabling-and-disabling-modules).

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

O Adobe Commerce permite ativar ou desativar os módulos disponíveis no momento; em outras palavras, qualquer módulo fornecido por Adobe ou qualquer módulo de terceiros disponível no momento.

Determinados módulos têm dependências em outros módulos, nesse caso, você não pode ativar ou desativar um módulo porque ele tem dependências em outros módulos.

Além disso, pode haver *módulos* conflitantes que não podem ser habilitados ao mesmo tempo.

Exemplos:

* O módulo A depende do módulo B. Você não pode desativar o módulo B a menos que primeiro desative o módulo A.

* O módulo A depende do módulo B, que está desativado. Você deve ativar o módulo B antes de ativar o módulo A.

* O módulo A está em conflito com o módulo B. Você pode desabilitar os Módulos A e B, ou pode desabilitar ambos os módulos, mas *não pode* habilitar os Módulos A e B ao mesmo tempo.

* As dependências são declaradas no campo `require` no arquivo `composer.json` do Adobe Commerce para cada módulo. Conflitos são declarados no campo `conflict` nos arquivos `composer.json` dos módulos. Usamos essas informações para criar um gráfico de dependências: `A->B` significa que o módulo A depende do módulo B.

* Uma *cadeia de dependência* é o caminho de um módulo para outro. Por exemplo, se o módulo A depende do módulo B, e o módulo B depende do módulo C, a cadeia de dependência é `A->B->C`.

Se você tentar ativar ou desativar um módulo que depende de outros módulos, o gráfico de dependência é exibido na mensagem de erro.

>[!NOTE]
>
>É possível que o `composer.json` do módulo A declare um conflito com o módulo B, mas não vice-versa.

*Somente linha de comando:* Para forçar um módulo a ser habilitado ou desabilitado, independentemente de suas dependências, use o argumento `--force` opcional.

>[!NOTE]
>
>Usar o `--force` pode desabilitar seu armazenamento e causar problemas ao acessar o Administrador.
