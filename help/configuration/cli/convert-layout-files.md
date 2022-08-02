---
title: Converter arquivos de layout
description: Converta arquivos de layout XML.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Converter arquivos de layout XML

{{file-system-owner}}

Use este comando para atualizar seus arquivos XML de layout se atualizar a folha de estilos XSLT (Extensible Stylesheet Language Transformations) correspondente.

- [Instruções de layout](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [Tipos de arquivo de layout](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

Opções de comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Em que:

- `{xml file}`—é o caminho completo e o nome do arquivo de um arquivo XML de layout a ser convertido (obrigatório)
- `{xslt stylesheet}`—é o caminho completo e o nome de arquivo de um arquivo de folha de estilos XSLT a ser usado para conversão (obrigatório)
- `-o|--overwrite`—inclua esta opção para substituir o arquivo XML existente
