---
title: .gitignore referência
description: Saiba como adicionar arquivos à lista .gitignore para projetos Adobe Commerce. Descubra o gerenciamento de controle de versão e as práticas recomendadas de exclusão de arquivos.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# .gitignore referência

O Magento Open Source inclui um arquivo base `.gitignore`. Consulte [o arquivo mais recente do Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore). Se você precisar adicionar um arquivo que esteja na lista `.gitignore`, poderá usar a opção `-f` (forçar) ao preparar uma confirmação:

```shell
git add <path/filename> -f
```
