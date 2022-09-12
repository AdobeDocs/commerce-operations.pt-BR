---
title: Converter arquivos de layout
description: Converta arquivos de layout XML.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Converter arquivos de layout XML

{{file-system-owner}}

Use este comando para atualizar seus arquivos XML de layout se atualizar a folha de estilos XSLT (Extensible Stylesheet Language Transformations) correspondente.

- [Instruções de layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Tipos de arquivo de layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Opções de comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Em que:

- `{xml file}`—é o caminho completo e o nome do arquivo de um arquivo XML de layout a ser convertido (obrigatório)
- `{xslt stylesheet}`—é o caminho completo e o nome de arquivo de um arquivo de folha de estilos XSLT a ser usado para conversão (obrigatório)
- `-o|--overwrite`—inclua esta opção para substituir o arquivo XML existente
