---
title: Visão geral dos dados de amostra
description: Saiba mais sobre como usar dados de amostra para projetos do Adobe Commerce e Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Visão geral dos dados de amostra

Os dados de amostra fornecem uma loja com base no tema Luma equipado com produtos, categorias, registro de clientes e assim por diante. Funciona como uma loja do Commerce e você pode manipular preços, inventário e regras de preços promocionais usando o Administrador.

Você pode instalar dados de amostra antes ou depois de instalar o software Commerce. Quando terminar com os dados de amostra, você pode removê-los ou instalá-los no modo novo, como discutido em [Remover módulos de dados de amostra ou atualizar dados de amostra](remove-or-update.md).

>[!WARNING]
>
>Não é possível desinstalar dados de amostra. Recomendamos que você use dados de amostra somente para saber mais sobre como o Adobe Commerce e o Magento Open Source funcionam. Evite fazer qualquer desenvolvimento em um sistema no qual você instalou dados de amostra.

Você pode instalar dados de amostra opcionais de qualquer uma das seguintes maneiras:

| Método de instalação | Descrição | Nível de habilidade necessário |
|--- |--- |--- |
| Usar o Composer | [Executar `magento sampledata:deploy` para modificar a raiz do aplicativo `composer.json`](composer-packages.md) para habilitar módulos de dados de amostra. | Requer conhecimento do Composer e acesso ao sistema de arquivos do Commerce. |
| Repositórios de clonagem | [Clonar o repositório GitHub](git-repositories.md) e o repositório de dados de amostra, em seguida, vincule-os. | Somente para desenvolvedores contribuidores. Todos os outros devem usar um dos métodos anteriores. |
