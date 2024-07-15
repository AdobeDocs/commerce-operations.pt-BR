---
title: Visão geral da instalação local
description: Saiba mais sobre o processo de instalação de implantações locais do Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# Visão geral da instalação local

>[!NOTE]
>
>O diagrama a seguir fornece uma visão geral de alto nível das _**instalações locais**_ do Adobe Commerce:

![Como funciona a instalação](../assets/installation/install-diagram-24.svg)

O fluxo geral de instalação é o seguinte:

1. Configurar o ambiente do servidor.

   Instale o software de pré-requisito, incluindo PHP, Apache, MySQL e o mecanismo de pesquisa. Consulte os [requisitos do sistema](system-requirements.md) para obter mais informações.

1. Obtenha [chaves de autenticação](prerequisites/authentication-keys.md) para o repositório do Commerce Composer.

1. Obtenha o software Adobe Commerce.

   * (Recomendado) Obtenha o [metapackage do Composer](composer.md) para gerenciar módulos e suas dependências.

   * Se você deseja contribuir para a base de código do Magento Open Source ou personalizar o aplicativo, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) o repositório do GitHub. Este método requer familiaridade com o GitHub e o Composer.

1. Instale o aplicativo usando a linha de comando.

   Se a etapa falhar porque o software de pré-requisito não está configurado corretamente, verifique os [pré-requisitos](prerequisites/overview.md).

1. [Verifique](next-steps/verify.md) a instalação visualizando a vitrine e o Administrador.
