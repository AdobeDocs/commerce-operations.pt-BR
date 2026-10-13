---
title: Dados que exigem migração manual
description: Saiba mais sobre os dados que devem ser migrados manualmente durante uma migração de dados do Magento 1 para o Magento 2 e como fazer isso.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '289'
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
>O método de armazenamento de mídia de banco de dados está obsoleto a partir da Magento 2.4.3.


Esta seção se aplica a você *somente* se você armazenar arquivos de mídia no banco de dados da Magento. Esta etapa deve ser executada antes de [migração de dados](data.md):

1. Faça logon no Painel de administração do Magento 1 como administrador.

1. Clique em **Sistema** > **Configuração** > AVANÇADO > **Sistema**.

1. No painel direito, role até **Configuração de Armazenamento para Mídia**.

1. Na lista **Selecionar Banco de Dados de Mídia**, clique no nome do banco de dados de armazenamento de mídia.

1. Clique em **Sincronizar**.

Em seguida, repita as mesmas etapas no painel de administração do Magento 2.

### Arquivos de mídia no sistema de arquivos

Todos os arquivos de mídia (imagens de produtos, categorias, editor WYSIWYG etc.) devem ser copiados manualmente do `<your Magento 1 install dir>/media` para o `<your Magento 2 install dir>/pub/media`.

No entanto, *não* copie os arquivos `.htaccess` localizados na pasta `media` da Magento 1. O Magento 2 tem seu próprio `.htaccess` que deve ser preservado.

## Design de vitrine

* O design em arquivos (CSS, JS, modelos, layouts XML) alterou seu local e formato

* Atualizações de layout armazenadas no banco de dados. Feito com o Magento 1 Admin em páginas do CMS, CMS Widgets, páginas de categoria e páginas de produto

## Listas de controle de acesso (ACLs)

Você deve recriar manualmente todos os:

* credenciais para APIs de serviço da Web (SOAP, XML-RPC e REST)

* contas de usuário administrativo e associá-las a privilégios de acesso

>[!NOTE]
>
>Você pode ajustar o fuso horário de uma entidade de banco de dados usando o manipulador `\Migration\Handler\Timezone`. Consulte a seção [acompanhamento](follow-up.md) para obter mais detalhes.
