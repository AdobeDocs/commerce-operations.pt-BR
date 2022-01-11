---
title: Reverter após a falha de atualização do módulo
description: Solucione problemas de atualização do Adobe Commerce ou do Magento Open Source após encontrar um erro de atualização de módulo.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Reverter após a falha de atualização do módulo

Se a atualização do módulo falhar, mensagens semelhantes ao seguinte serão exibidas no log do console:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

No exemplo anterior, não há uma versão de componente para a qual reverter. Entre em contato com o fornecedor do componente ou tente resolver o problema sozinho.

Enquanto isso, você pode reverter para uma versão anterior clicando em **Reversão**, que recupera seus dados mesmo se você não tiver feito backup anteriormente.
