---
title: Converter arquivos de layout
description: Converter arquivos de layout XML.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Converter arquivos de layout XML

{{file-system-owner}}

Use este comando para atualizar seus arquivos XML de layout se você atualizar a folha de estilos XSLT correspondente.

- [Instruções de layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Tipos de arquivos de layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Opções de comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Onde:

- `{xml file}` — é o caminho completo e o nome de arquivo de um arquivo XML de layout a ser convertido (obrigatório)
- `{xslt stylesheet}` — é o caminho completo e o nome de arquivo de uma folha de estilos XSLT a ser usada para conversão (obrigatório)
- `-o|--overwrite`—inclua esta opção para substituir o arquivo XML existente
