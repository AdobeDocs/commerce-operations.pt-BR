---
title: Compilador de código
description: Saiba como executar o compilador de código a partir da linha de comando.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Compilador de código

{{file-system-owner}}

A compilação de código inclui o seguinte (sem ordem específica):

- Geração de código de aplicativo (fábricas, proxies)
- Agregação de configuração de área (configurações otimizadas de injeção de dependência por área)
- Geração de interceptores (geração otimizada de códigos de interceptores)
- Geração de cache de intercepção
- Geração de código de repositórios (código gerado para APIs)
- Geração de atributos de dados de serviço (classes de extensão geradas para objetos de dados)

Você pode encontrar classes de compilação de código no [\Magento\Setup\Module\Di\App\Task\Operation][operation] namespace.

Para executar o compilador de único locatário:

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Para compilar o código antes de instalar o aplicativo do Commerce:

Em alguns casos, talvez você queira compilar o código antes de instalar o aplicativo Commerce.

1. Ative os módulos.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Use o `[-c|--clear-static-content]` para limpar o conteúdo estático. Isso é necessário se você ativou ou desativou os módulos anteriormente e precisa limpar o conteúdo estático gerado anteriormente para eles.

   Consulte [Ativar módulos](../../installation/tutorials/manage-modules.md).

1. Compile o código.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Para compilar o código sem um banco de dados, consulte [Implantar arquivos de visualização estáticos sem instalar o Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
