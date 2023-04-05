---
title: Migrar alterações
description: Saiba como migrar apenas dados que foram alterados desde a última migração de dados do Magento 1 com o [!DNL Data Migration Tool].
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Migrar alterações

A ferramenta de migração incremental instala tabelas de diálogo (com prefixo `m2_cl_*`) e acionadores (para alterações de rastreamento) no banco de dados do Magento 1 durante a [migração de dados](data.md). Essas tabelas e acionadores de catálogo são essenciais para garantir que você migre somente as alterações feitas na Magento 1 desde a última vez que migrou dados. Essas alterações são:

* Dados que os clientes adicionaram por meio da loja (pedidos criados, revisões e alterações nos perfis do cliente)

* Todas as operações com pedidos, produtos e categorias no painel Administração

>[!NOTE]
>
>Todas as outras entidades novas ou atualizadas inseridas por meio do Administrador, como atributos ou páginas CMS, não estão incluídas na migração incremental e não são migradas.


Antes de começar, execute as seguintes etapas para preparar:

1. Faça logon no servidor de aplicativos como [o proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).
1. Alterar para `/bin` ou verifique se ele foi adicionado ao seu sistema `PATH`.

Consulte a [primeiros passos](overview.md#first-steps) para obter mais detalhes.

## Execute o comando de migração incremental

Para começar a migrar alterações incrementais, execute:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Em que:

* `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração.

* `[-a|--auto]` é um argumento opcional que impede a interrupção da migração quando encontra erros de verificação de integridade.

* `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para `config.xml`; esse argumento é obrigatório.

>[!NOTE]
>
>A migração incremental é um processo contínuo; ele é reiniciado automaticamente a cada 5 segundos. Use CTRL-C para suspender o processo de migração.


## Migrar dados criados por extensões de terceiros

No `Delta` , o [!DNL Data Migration Tool] migra dados criados apenas pelos módulos próprios Magento e não é responsável pelo código ou extensões feitas por desenvolvedores de terceiros. Se essas extensões criaram dados no banco de dados da loja e o comerciante quiser ter esses dados no Magento 2 — os arquivos de configuração do [!DNL Data Migration Tool] deve ser criada e modificada de acordo.

Se uma extensão tiver suas próprias tabelas e você precisar rastrear as alterações para a migração do delta, siga estas etapas:

1. Adicione as tabelas a serem rastreadas no `deltalog.xml` arquivo
1. Crie uma classe delta adicional que estenda a variável `Migration\App\Step\AbstractDelta`
1. Adicione o nome da classe recém-criada à seção do modo delta de `config.xml`
