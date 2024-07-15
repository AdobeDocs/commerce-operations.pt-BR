---
title: Criar ligações simbólicas para MENOS arquivos
description: Saiba como criar symlinks para arquivos LESS.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Criar ligações simbólicas para MENOS arquivos

{{file-system-owner}}

Para criar symlinks para arquivos LESS:

Opções de comando:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Durante o desenvolvimento, este comando cria symlinks para arquivos LESS nas pastas `var/view_preprocessed` e `pub/static`. Esse processo não compila MENOS arquivos em arquivos CSS.

A tabela a seguir explica os parâmetros e valores desse comando.

| Parâmetro | Valor | Obrigatório? |
| --------- | ----- | --------- |
| `--type` | Tipo de arquivos de origem: [less] (padrão: &quot;less&quot;)<br>No momento, LESS é o único tipo de arquivo com suporte. | Não |
| `--locale` | Código da localidade.<br>Para exibir a lista de códigos de localidade, insira `bin/magento info:language:list` | Não |
| `--area` | Área (`adminhtml` para a área administrativa, `frontend` para a loja). | Não |
| `--theme` | Nome do tema no formato `<VendorName>/<theme-name>`. Por exemplo, `Magento/blank` ou `Magento/backend`. | Não |
| `<file>` | Lista separada por espaços de arquivos CSS para conversão em LESS sem a extensão CSS. (O padrão é `css/styles-m css/styles-l`, para o tipo adminhtml `css/styles css/styles-old`) | Não |

Por exemplo, para criar MENOS arquivos para o tema de front-end chamado `VendorName/themeName` na localidade `en_US` usando um arquivo CSS chamado `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, digite o seguinte comando:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

As mensagens a seguir são exibidas para confirmar o sucesso:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Para criar MENOS arquivos para o adminhtml:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
