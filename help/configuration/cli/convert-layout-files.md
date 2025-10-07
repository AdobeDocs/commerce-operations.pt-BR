---
title: Converter arquivos de layout
description: Saiba como converter arquivos de layout XML usando ferramentas de linha de comando do Adobe Commerce. Descubra as atualizações da folha de estilos XSLT e os processos de conversão de arquivos.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '98'
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
