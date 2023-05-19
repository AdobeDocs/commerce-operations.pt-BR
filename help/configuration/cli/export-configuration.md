---
title: Exportar definições de configuração
description: Exporte as configurações do Adobe Commerce para os arquivos de configuração, também conhecidos como despejo de configuração.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Exportar definições de configuração

No Commerce 2.2 e posterior [modelo de implantação de pipeline](../deployment/technical-details.md), você pode manter uma configuração consistente em todos os sistemas. Depois de definir as configurações no Administrador no sistema de desenvolvimento, exporte essas configurações para arquivos de configuração usando o seguinte comando:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ é uma lista separada por espaços de tipos de configuração para despejo. Os tipos disponíveis incluem `scopes`, `system`, `themes`, e `i18n`. Se nenhum tipo de configuração for especificado, o comando despeja todas as informações de configuração do sistema.

O exemplo a seguir descarta apenas escopos e temas:

```bash
bin/magento app:config:dump scopes themes
```

Como resultado da execução do comando, os seguintes arquivos de configuração são atualizados:

- `app/etc/config.php`

   Esse é o arquivo de configuração compartilhado para todas as instâncias do Commerce.
Inclua isso no controle de origem para que ele possa ser compartilhado entre os sistemas de desenvolvimento, compilação e produção.

   Consulte [referência config.php](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   Este é o arquivo de configuração específico do ambiente.
Ele contém configurações confidenciais e específicas do sistema para ambientes individuais.

   Fazer _não_ incluir este arquivo no controle de origem.

   Consulte [referência env.php](../reference/config-reference-envphp.md).

## Configurações sensíveis ou específicas do sistema

Para definir as configurações confidenciais gravadas em `env.php`, use o [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) comando.

Os valores de configuração são especificados como confidenciais ou específicos do sistema, fazendo referência a [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) no do módulo [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) arquivo.

Para exportar configurações adicionais do sistema ao usar `config_types`, considere usar o [`bin/magento config:set`](set-configuration-values.md#set-values) comando.
