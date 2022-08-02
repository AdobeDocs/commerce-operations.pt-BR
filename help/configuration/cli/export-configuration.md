---
title: Exportar configurações
description: Exporte as configurações do Adobe Commerce para os arquivos de configuração, também conhecidos como despejo de configuração.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Exportar configurações

No Commerce 2.2 e posterior [modelo de implantação de pipeline](../deployment/technical-details.md), é possível manter uma configuração consistente em todos os sistemas. Depois de definir as configurações no Administrador em seu sistema de desenvolvimento, exporte essas configurações para os arquivos de configuração usando o seguinte comando:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ é uma lista de tipos de configuração separada por espaços para despejar. Os tipos disponíveis incluem `scopes`, `system`, `themes`e `i18n`. Se nenhum tipo de configuração for especificado, o comando despejará todas as informações de configuração do sistema.

O exemplo a seguir despeja apenas escopos e temas:

```bash
bin/magento app:config:dump scopes themes
```

Como resultado da execução do comando, os seguintes arquivos de configuração são atualizados:

- `app/etc/config.php`

   Esse é o arquivo de configuração compartilhado para todas as instâncias do Commerce.
Inclua isso no controle de origem para que possa ser compartilhado entre os sistemas de desenvolvimento, criação e produção.

   Consulte [referência config.php](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   Esse é o arquivo de configuração específico do ambiente.
Ele contém configurações confidenciais e específicas do sistema para ambientes individuais.

   Do _not_ inclua esse arquivo no controle de origem.

   Consulte [referência env.php](../reference/config-reference-envphp.md).

## Configurações sensíveis ou específicas do sistema

Para definir as configurações confidenciais gravadas em `env.php`, use o [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) comando.

Os valores de configuração são especificados como confidenciais ou específicos do sistema, fazendo referência a [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) no [`di.xml`](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/configuration/sensitive-and-environment-settings.html#how-to-specify-values-as-sensitive-or-system-specific) arquivo.

Para exportar configurações de sistema adicionais ao usar `config_types`, considere usar o [`bin/magento config:set`](set-configuration-values.md#set-values) comando.
