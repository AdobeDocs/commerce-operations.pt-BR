---
title: Converter arquivos de layout
description: Saiba como converter arquivos de layout XML usando ferramentas de linha de comando do Adobe Commerce. Descubra as atualizações da folha de estilos XSLT e os processos de conversão de arquivos.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
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
source-wordcount: '118'
ht-degree: 0%
---
# Converter arquivos de layout XML

{{file-system-owner}}

Use este comando para atualizar seus arquivos XML de layout se você atualizar a folha de estilos XSLT correspondente.

- [Instruções de layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [Tipos de arquivo de layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

Opções de comando:

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Onde:

- `{xml file}` — é o caminho completo e o nome de arquivo de um arquivo XML de layout a ser convertido (obrigatório)
- `{xslt stylesheet}` — é o caminho completo e o nome de arquivo de uma folha de estilos XSLT a ser usada para conversão (obrigatório)
- `-o|--overwrite`—inclua esta opção para substituir o arquivo XML existente
