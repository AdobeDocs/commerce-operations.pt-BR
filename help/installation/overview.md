---
title: Visão geral da instalação no local
description: Saiba mais sobre o processo de instalação de implantações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Visão geral da instalação no local

>[!NOTE]
>
>O diagrama a seguir fornece uma visão geral de alto nível de _**no local**_ instalações de Adobe Commerce e Magento Open Source:

![Como a instalação funciona](../assets/installation/install-diagram-24.svg)

O fluxo geral de instalação é o seguinte:

1. Configure seu ambiente de servidor.

   Instale o software de pré-requisito, incluindo PHP, Apache, MySQL e o mecanismo de pesquisa. Consulte a [requisitos do sistema](system-requirements.md) para obter mais informações.

1. Get [chaves de autenticação](prerequisites/authentication-keys.md) para o repositório do Commerce Composer.

1. Obtenha o software Adobe Commerce ou Magento Open Source.

   * (Recomendado) Obtenha o [Metapackeamento do compositor](composer.md) para gerenciar módulos e suas dependências.

   * Se você quiser contribuir com a base de código do Magento Open Source ou personalizar o aplicativo, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) o repositório GitHub. Esse método requer familiaridade com GitHub e Composer.

1. Instale o aplicativo usando a linha de comando.

   Se a etapa falhar porque o software de pré-requisito não está configurado corretamente, revise a [pré-requisitos](prerequisites/overview.md).

1. [Verificar](next-steps/verify.md) a instalação exibindo sua vitrine e o Admin.

