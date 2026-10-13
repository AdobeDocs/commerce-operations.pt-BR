---
title: Compilador de código
description: Saiba como executar o compilador de código Adobe Commerce a partir da linha de comando. Descubra processos de compilação e técnicas de otimização.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%
---
# Compilador de código

{{file-system-owner}}

A compilação de código inclui o seguinte (sem ordem específica):

- Geração de código de aplicativo (fábricas, proxies)
- Agregação de configuração de área (configurações otimizadas de injeção de dependência por área)
- Geração de interceptores (geração otimizada de códigos de interceptores)
- Geração de cache de interceptação
- Geração de código de repositórios (código gerado para APIs)
- Geração de atributos de dados de serviço (classes de extensão geradas para objetos de dados)

Você pode encontrar classes de compilação de código no namespace [\Magento\Setup\Module\Di\App\Task\Operation](https://github.com/magento/magento2/blob/2.4.8/setup/src/Magento/Setup/Module/Di/App/Task/Operation).

Para executar o compilador de locatário único:

```shell
bin/magento setup:di:compile
```

```text
Generated code and dependency injection configuration successfully.
```

Para compilar o código antes de instalar o aplicativo Commerce:

Em alguns casos, convém compilar o código antes de instalar o aplicativo do Commerce.

1. Habilite os módulos.

   ```shell
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Use a opção `[-c|--clear-static-content]` para limpar o conteúdo estático. Isso é necessário se você tiver ativado ou desativado módulos anteriormente e precisar limpar o conteúdo estático gerado anteriormente para eles.

   Consulte [Habilitar módulos](../../installation/tutorials/manage-modules.md).

1. Compile o código.

   ```shell
   bin/magento setup:di:compile
   ```

   ```text
   Generated code and dependency injection configuration successfully.
   ```

Para compilar o código sem um banco de dados, consulte [Implantar arquivos de exibição estáticos sem instalar o Magento](../cli/static-view-file-deployment.md).

