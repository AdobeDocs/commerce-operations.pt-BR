---
title: Visão geral dos dados de exemplo
description: Saiba mais sobre como usar dados de amostra para projetos Adobe Commerce e Magento Open Source.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: decaac76955aaae011c308ed1295198abf791abe
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Visão geral dos dados de exemplo

Dados de amostra fornecem uma loja com base no tema Luma equipado com produtos, categorias, registro de clientes e assim por diante. Ele funciona como uma loja do Commerce e você pode manipular preços, inventário e regras de preços promocionais usando o Administrador.

>[!NOTE]
>
>Para revisar e analisar o banco de dados e vários recursos, considere usar dados reais em vez de dados de amostra. Os dados de amostra são projetados como uma simulação de loja pré-gerada, para demonstrar o design do tema e o comportamento básico da loja. Todas as entidades de dados de amostra são gravadas diretamente nas tabelas do banco de dados, enquanto dados de amostra são instalados.

Você pode instalar os dados de amostra antes ou depois de instalar o software Commerce. Quando terminar com os dados de amostra, você pode removê-los ou instalá-los novamente, conforme discutido em [Remover módulos de dados de amostra ou atualizar dados de amostra](remove-or-update.md).

>[!WARNING]
>
>Não é possível desinstalar dados de exemplo. Use dados de amostra apenas para saber como o Adobe Commerce e o Magento Open Source funcionam. Evite fazer qualquer desenvolvimento em um sistema no qual você instalou dados de amostra.

Você pode instalar dados de amostra opcionais de qualquer uma das seguintes maneiras:

| Método de instalação | Descrição | Nível de habilidade necessário |
|--- |--- |--- |
| Uso do Composer | [Executar `magento sampledata:deploy` para modificar a raiz do aplicativo `composer.json`](composer-packages.md) para ativar módulos de dados de amostra. | Requer conhecimento do Composer e acesso ao sistema de arquivos do Commerce. |
| Clonagem de repositórios | [Clonar o repositório GitHub](git-repositories.md) e o repositório de dados de amostra, depois vincule-os. | Somente para desenvolvedores contribuintes. Todos os outros usuários devem usar um dos métodos anteriores. |
