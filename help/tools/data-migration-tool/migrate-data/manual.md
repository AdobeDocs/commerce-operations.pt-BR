---
title: Dados que exigem migração manual
description: Saiba mais sobre os dados que devem ser migrados manualmente durante a migração de dados de Magento 1 para Magento 2 e como fazer isso.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Dados que exigem migração manual

Há quatro tipos de dados que precisam ser migrados manualmente:

* Mídia

* Design de vitrine

* Contas de usuário administrador

* Listas de controle de acesso (ACLs)

## Mídia

Esta seção discute como migrar arquivos de mídia manualmente.

### Arquivos de mídia armazenados no banco de dados

>[!WARNING]
>
>O método de armazenamento de mídia de banco de dados está obsoleto a partir do Magento 2.4.3.


Esta seção se aplica a você *somente* se você armazenar arquivos de mídia no banco de dados Magento. Esta etapa deve ser executada antes de [migração de dados](data.md):

1. Faça logon no Painel de administração do Magento 1 como administrador.

1. Clique em **Sistema** > **Configuração** > AVANÇADO > **Sistema**.

1. No painel direito, role até **Configuração de Armazenamento para Mídia**.

1. Na lista **Selecionar Banco de Dados de Mídia**, clique no nome do banco de dados de armazenamento de mídia.

1. Clique em **Sincronizar**.

Em seguida, repita as mesmas etapas no painel Administrador do Magento 2.

### Arquivos de mídia no sistema de arquivos

Todos os arquivos de mídia (imagens de produtos, categorias, o editor WYSIWYG etc.) devem ser copiados manualmente do `<your Magento 1 install dir>/media` para o `<your Magento 2 install dir>/pub/media`.

No entanto, *não* copie os arquivos `.htaccess` localizados na pasta Magento 1 `media`. Magento 2 tem seu próprio `.htaccess` que deve ser preservado.

## Design de vitrine

* O design em arquivos (CSS, JS, modelos, layouts XML) alterou seu local e formato

* Atualizações de layout armazenadas no banco de dados. Feito através do Magento 1 Admin em páginas CMS, widgets CMS, páginas de categoria e páginas de produto

## Listas de controle de acesso (ACLs)

Você deve recriar manualmente todos os:

* credenciais para APIs de serviço da Web (SOAP, XML-RPC e REST)

* contas de usuário administrativo e associá-las a privilégios de acesso

>[!NOTE]
>
>Você pode ajustar o fuso horário de uma entidade de banco de dados usando o manipulador `\Migration\Handler\Timezone`. Consulte a seção [acompanhamento](follow-up.md) para obter mais detalhes.
