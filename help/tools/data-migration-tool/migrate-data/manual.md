---
title: Dados que exigem migração manual
description: Saiba mais sobre os dados que devem ser migrados manualmente durante a migração de dados do Magento 1 para o Magento 2 e como fazê-lo.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Dados que exigem migração manual

Há quatro tipos de dados que precisam ser migrados manualmente:

* Mídia

* Design da frente de loja

* Contas de usuário administrador

* Listas de Controle de Acesso (ACLs)

## Mídia

Esta seção discute como migrar arquivos de mídia manualmente.

### Arquivos de mídia armazenados no banco de dados

>[!WARNING]
>
>O método de armazenamento de mídia do banco de dados está obsoleto a partir do Magento 2.4.3.


Esta seção se aplica a você *only* se você armazenar arquivos de mídia no banco de dados do Magento. Esta etapa deve ser executada antes de [migração de dados](data.md):

1. Faça logon no Painel de administração do Magento 1 como administrador.

1. Clique em **Sistema** > **Configuração** > AVANÇADO > **Sistema**.

1. No painel direito, role até **Configuração de armazenamento para mídia**.

1. No **Selecionar banco de dados de mídia** , clique no nome do banco de dados de armazenamento de mídia.

1. Clique em **Sincronizar**.

Em seguida, repita as mesmas etapas no painel de administração do Magento 2.

### Arquivos de mídia no sistema de arquivos

Todos os arquivos de mídia (imagens para produtos, categorias, o editor WYSIWYG e assim por diante) devem ser copiados manualmente do `<your Magento 1 install dir>/media` para `<your Magento 2 install dir>/pub/media`.

No entanto, faça *not* copie a `.htaccess` arquivos localizados no Magento 1 `media` pasta. Magento 2 tem seu próprio `.htaccess` isso deve ser preservado.

## Design da frente de loja

* O design em arquivos (CSS, JS, modelos, layouts XML) alterou seu local e formato

* Atualizações de layout armazenadas no banco de dados. Feito pelo administrador do Magento 1 em Páginas CMS, widgets CMS, Páginas de categoria e Páginas de produto

## Listas de Controle de Acesso (ACLs)

Você deve recriar tudo manualmente:

* credenciais para APIs de serviço da Web (SOAP, XML-RPC e REST)

* contas de usuário administrativas e associá-las a privilégios de acesso

>[!NOTE]
>
>Você pode ajustar o fuso horário de uma entidade de banco de dados usando o `\Migration\Handler\Timezone` manipulador. Consulte a [acompanhamento](follow-up.md) para obter mais detalhes.
