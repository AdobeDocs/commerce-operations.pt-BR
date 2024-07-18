---
title: Reverter após falha de atualização do módulo
description: Solucione o problema da atualização do Adobe Commerce depois de encontrar um erro de atualização de módulo.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Reverter após falha de atualização do módulo

Se a atualização do módulo falhar, mensagens semelhantes às seguintes serão exibidas no log do console:

```
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

No exemplo anterior, não há versão de componente para a qual reverter. Entre em contato com o fornecedor do componente ou tente resolver o problema sozinho.

Enquanto isso, você pode reverter para uma versão anterior clicando em **Reverter**, que recupera os dados mesmo que não tenha feito backup anteriormente.
