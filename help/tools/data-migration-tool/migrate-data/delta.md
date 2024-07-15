---
title: Migrar alterações
description: Saiba como migrar apenas dados que foram alterados desde a última migração de dados Magento 1 com o  [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Migrar alterações

A ferramenta de migração incremental instala tabelas de catálogo de exclusão (com o prefixo `m2_cl_*`) e acionadores (para alterações de rastreamento) no banco de dados Magento 1 durante a [migração de dados](data.md). Essas tabelas e acionadores de exclusão são essenciais para garantir que você migre apenas as alterações feitas no Magento 1 desde a última vez que migrou os dados. Essas alterações são:

* Dados que os clientes adicionaram por meio da loja (pedidos criados, revisões e alterações nos perfis do cliente)

* Todas as operações com pedidos, produtos e categorias no painel Administrador

>[!NOTE]
>
>Todas as outras entidades novas ou atualizadas inseridas por meio do Administrador, como atributos ou páginas CMS, não são incluídas na migração incremental e não são migradas.


Antes de começar, siga as etapas abaixo para se preparar:

1. Faça logon no servidor de aplicativos como [o proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório `/bin` ou verifique se ele foi adicionado ao sistema `PATH`.

Consulte a seção [primeiras etapas](overview.md#first-steps) para obter mais detalhes.

## Execute o comando de migração incremental

Para começar a migrar alterações incrementais, execute:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Onde:

* `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração.

* `[-a|--auto]` é um argumento opcional que impede que a migração pare quando encontrar erros de verificação de integridade.

* `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para `config.xml`; este argumento é obrigatório.

>[!NOTE]
>
>A migração incremental é um processo contínuo; ela é reiniciada automaticamente a cada 5 segundos. Use CTRL-C para suspender o processo de migração.


## Migrar dados criados por extensões de terceiros

No modo `Delta`, o [!DNL Data Migration Tool] migra dados criados apenas por módulos próprios do Magento e não é responsável pelo código ou pelas extensões feitas por desenvolvedores de terceiros. Se essas extensões criaram dados no banco de dados da loja e o comerciante quiser que esses dados estejam no Magento 2 — os arquivos de configuração do [!DNL Data Migration Tool] devem ser criados e modificados adequadamente.

Se uma extensão tiver suas próprias tabelas e você precisar rastrear suas alterações para migração delta, siga estas etapas:

1. Adicionar as tabelas a serem acompanhadas ao arquivo `deltalog.xml`
1. Criar uma classe delta adicional que estenda a `Migration\App\Step\AbstractDelta`
1. Adicionar o nome da classe recém-criada à seção de modo delta de `config.xml`
