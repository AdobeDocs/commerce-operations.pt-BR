---
title: Criar links simbólicos para arquivos MENOS
description: Saiba como criar links simbólicos para arquivos MENOS.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Criar links simbólicos para arquivos MENOS

{{file-system-owner}}

Para criar links simbólicos para arquivos MENOS:

Opções de comando:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Durante o desenvolvimento, esse comando cria links simbólicos para arquivos MENOS no `var/view_preprocessed` e `pub/static` pastas. Esse processo não compila arquivos LESS em arquivos CSS.

A tabela a seguir explica os parâmetros e valores desse comando.

| Parâmetro | Valor | Obrigatório? |
| --------- | ----- | --------- |
| `--type` | Tipo de arquivos de origem: [less] (padrão: &quot;less&quot;)<br>Atualmente, LESS é o único tipo de arquivo suportado. | Não |
| `--locale` | Código de localidade.<br>Para exibir a lista de códigos de localidade, insira `bin/magento info:language:list` | Não |
| `--area` | Área (`adminhtml` para o domínio administrativo, `frontend` para a loja). | Não |
| `--theme` | Nome do tema em `<VendorName>/<theme-name>` formato. Por exemplo, `Magento/blank` ou `Magento/backend`. | Não |
| `<file>` | Lista de arquivos CSS separados por espaços para conversão em MENOS sem a extensão CSS. (O padrão é `css/styles-m css/styles-l`, para tipo adminhtml `css/styles css/styles-old`) | Não |

Por exemplo, para criar arquivos MENOS para o tema de primeiro plano chamado `VendorName/themeName` no `en_US` localidade usando um arquivo CSS chamado `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, digite o seguinte comando:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

As mensagens a seguir são exibidas para confirmar o sucesso:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Para criar arquivos MENOS para o adminhtml:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
