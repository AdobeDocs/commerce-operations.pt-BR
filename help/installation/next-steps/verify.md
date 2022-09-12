---
title: Verifique a instalação
description: Siga estas etapas para confirmar que a instalação local do Adobe Commerce ou do Magento Open Source foi bem-sucedida.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Verifique a instalação

Vá para o [vitrine](https://glossary.magento.com/storefront) em um navegador da Web. Por exemplo, se a base de instalação [URL](https://glossary.magento.com/url) é `http://www.example.com`, insira-o no endereço ou na barra de localização do navegador.

A figura a seguir mostra uma página de loja de exemplo. Se for exibido da seguinte maneira, sua instalação foi um sucesso!

![Loja com o tema Luma](../../assets/installation/install-success_store-luma.png)

## Verificar a loja (sem dados de amostra)

Vá para a loja em um navegador da Web. Por exemplo, se o URL de base da instalação for `http://www.example.com`, insira-o no endereço ou na barra de localização do navegador.

A figura a seguir mostra uma página de loja de exemplo. Se for exibido da seguinte maneira, sua instalação foi um sucesso!

![Loja que verifica uma instalação bem-sucedida](../../assets/installation/install-success_store.png)

Se a página exibir um `404 (Not Found)` ou não exibe estilos, consulte [solução de problemas](https://support.magento.com/hc/en-us/articles/360032994352).

## Verificar o administrador

Vá para o [Administrador](https://glossary.magento.com/magento-admin) em um navegador da Web. Por exemplo, se o URL de base da instalação for `http://www.example.com`e o URI do administrador é `admin_au1nT`, insira `http://www.example.com/admin_au1nT` na barra de endereço ou localização do navegador.

(O [Administrador](https://glossary.magento.com/admin) O URI é especificado pelo valor da variável `backend-frontname` parâmetro de instalação.)

Quando solicitado, faça logon como administrador.

A figura a seguir mostra um exemplo de página de Administração. Se for exibido da seguinte maneira, sua instalação foi um sucesso!

![Administrador que verifica uma instalação bem-sucedida](../../assets/installation/install_success_admin.png)

Se a página não exibir estilos, consulte [solução de problemas](https://support.magento.com/hc/en-us/articles/360032994352).

Se você receber um erro 404 (Não encontrado) semelhante ao seguinte, consulte [Erro de versão PHP ou 404 ao acessar o Adobe Commerce no navegador](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
