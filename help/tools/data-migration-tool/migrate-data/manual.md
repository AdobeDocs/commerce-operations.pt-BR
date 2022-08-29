---
title: Dados que exigem migração manual
description: 'Saiba mais sobre os dados que devem ser migrados manualmente durante a migração de dados do Magento 1 para o Magento 2 e como fazê-lo. '
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Dados que exigem migração manual

Há quatro tipos de dados que precisam ser migrados manualmente:

* Mídia

* [Loja](https://glossary.magento.com/storefront) projeto

* [Administrador](https://glossary.magento.com/admin) contas de usuário

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

1. No **Selecionar banco de dados de mídia** clique no nome da sua [armazenamento de mídia](https://glossary.magento.com/media-storage) banco de dados.

1. Clique em **Sincronizar**.

Em seguida, repita as mesmas etapas no painel de administração do Magento 2.

### Arquivos de mídia no sistema de arquivos

Todos os arquivos de mídia (imagens para produtos, categorias, a variável [WYSIWYG](https://glossary.magento.com/wysiwyg) editor e assim por diante) deve ser copiado manualmente do `<your Magento 1 install dir>/media` para `<your Magento 2 install dir>/pub/media`.

No entanto, faça *not* copie a `.htaccess` arquivos localizados no Magento 1 `media` pasta. Magento 2 tem seu próprio `.htaccess` isso deve ser preservado.

## Design da frente de loja

* Design em arquivos (CSS, JS, modelos, [XML](https://glossary.magento.com/xml) layouts) alteração de localização e formato

* [Layout](https://glossary.magento.com/layout) Atualizações armazenadas no banco de dados. Feito pelo administrador do Magento 1 em [CMS](https://glossary.magento.com/cms) Páginas, widgets CMS, [Categoria](https://glossary.magento.com/category) Páginas e páginas do produto

## Listas de Controle de Acesso (ACLs)

Você deve recriar tudo manualmente:

* credenciais para APIs de serviço da Web (SOAP, XML-RPC e REST)

* contas de usuário administrativas e associá-las a privilégios de acesso

>[!NOTE]
>
>Você pode ajustar o fuso horário de uma entidade de banco de dados usando o `\Migration\Handler\Timezone` manipulador. Consulte a [acompanhamento](follow-up.md) para obter mais detalhes.
