---
title: Reverter após falha de atualização do módulo
description: Solucione problemas com a atualização do Adobe Commerce ou Magento Open Source após encontrar um erro de atualização de módulo.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Reverter após falha de atualização do módulo

Se a atualização do módulo falhar, mensagens semelhantes às seguintes serão exibidas no log do console:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

No exemplo anterior, não há versão de componente para a qual reverter. Entre em contato com o fornecedor do componente ou tente resolver o problema sozinho.

Enquanto isso, você pode reverter para uma versão anterior clicando em **Reversão**, que recupera os dados mesmo que você não tenha feito backup anteriormente.
