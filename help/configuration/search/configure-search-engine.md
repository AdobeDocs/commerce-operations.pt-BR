---
title: Configuração do mecanismo de pesquisa
description: Configure um mecanismo de pesquisa com Adobe Commerce e Magento Open Source.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Configuração do mecanismo de pesquisa

Esta seção discute as configurações mínimas que você deve escolher para testar o Elasticsearch ou o OpenSearch com o Adobe Commerce e o Magento Open Source. Desde as versões 2.4.4 e 2.4.3-p2, todos os campos são rotulados **Elasticsearch** também se aplicam ao OpenSearch.

Para obter detalhes adicionais sobre como configurar seu mecanismo de pesquisa, consulte o [Guia do usuário](https://docs.magento.com/user-guide/catalog/search-elasticsearch.html).

## Configure seu mecanismo de pesquisa pelo Administrador

Para configurar seu sistema para usar o Elasticsearch ou OpenSearch:

1. Faça logon em Admin como administrador.
1. Clique em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo** > **Pesquisa no catálogo**.
1. No **Mecanismo de pesquisa** selecione a versão correspondente do seu mecanismo de pesquisa Se você estiver usando o OpenSearch, deverá selecionar Elasticsearch7.

   A tabela a seguir lista as opções de configuração necessárias para configurar e testar a conexão com o Commerce.
A menos que você tenha alterado as configurações do servidor do seu mecanismo de pesquisa, os padrões devem funcionar. Pule para a próxima etapa.

   | Opção | Descrição |
   |--- |--- |
   | **Nome do host do servidor Elasticsearch** | Insira o nome do host ou endereço IP totalmente qualificado da máquina que está executando o Elasticsearch ou o OpenSearch.<br>Adobe Commerce na infraestrutura de nuvem: Obtenha esse valor do seu sistema de integração. |
   | **Porta do Servidor Elasticsearch** | Insira a porta proxy do servidor da Web. O padrão é 9200<br>Adobe Commerce na infraestrutura de nuvem: Obtenha esse valor do seu sistema de integração. |
   | **Prefixo de Índice de Elasticsearch** | Insira o prefixo do índice do mecanismo de pesquisa. Se você usar uma única instância para mais de uma instalação do Commerce (ambientes de preparo e produção), deverá especificar um prefixo exclusivo para cada instalação. Caso contrário, você poderá usar o prefixo padrão magento2. |
   | **Habilitar Autenticação HTTP do Elasticsearch** | Clique em **Sim** somente se você ativou a autenticação para o servidor do mecanismo de pesquisa. Nesse caso, forneça um nome de usuário e senha nos campos fornecidos. |

1. Clique em **Testar conexão**.

   Resposta de exemplo:

   ![success](../../assets/configuration/elastic_test-success.png)

   Continue com:

   - [Configurar o Apache para seu mecanismo de pesquisa](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html)
   - [Configurar o nó do mecanismo de pesquisa](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html)

   ou você verá:

   ![falha](../../assets/configuration/elastic_test-fail.png)

Em caso positivo, tente o seguinte:

- Verifique se o servidor do mecanismo de pesquisa está em execução.
- Se o servidor estiver em um host diferente do Commerce, faça logon no servidor do Commerce e execute o ping no host do mecanismo de pesquisa. Resolva problemas de conectividade de rede e teste a conexão novamente.
- Examine a janela de comando na qual você iniciou o Elasticsearch ou o OpenSearch para rastreamentos e exceções de pilha. Você deve resolvê-los antes de continuar. Em particular, certifique-se de ter iniciado seu mecanismo de pesquisa como um usuário com `root` privilégios.
- Certifique-se de que [Firewall UNIX e SELinux](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#firewall-selinux) estão desativadas ou configuram regras para permitir que o mecanismo de pesquisa e o Commerce se comuniquem entre si.
- Verifique o valor da variável **Nome do host do servidor Elasticsearch** campo. Verifique se o servidor está disponível. Em vez disso, tente o endereço IP do servidor.
- Use o `netstat -an | grep <listen-port>` para verificar se a porta especificada no **Porta do Servidor Elasticsearch** não está sendo usado por outro processo.

   Por exemplo, para ver se o mecanismo de pesquisa está sendo executado em sua porta padrão, use o seguinte comando:

   ```bash
   netstat -an | grep 9200
   ```

   Se estiver sendo executado na porta 9200, será exibido de maneira semelhante ao seguinte:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Reindexando pesquisa de catálogo e atualizando o cache de página completo

Após alterar a configuração do mecanismo de pesquisa, é necessário reindexar o índice de pesquisa do catálogo e atualizar o cache de página completo usando o Administrador ou a linha de comando.

Para atualizar o cache usando o Administrador:

1. Em Admin, clique em **Sistema** > **Gerenciamento de cache**.
1. Marque a caixa de seleção ao lado de **Cache de página**.
1. No **Ações** no canto superior direito, clique em **Atualizar**.

   ![gerenciamento de cache](../../assets/configuration/refresh-cache.png)

Para limpar o cache usando a linha de comando: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Para reindexar usando a linha de comando:

1. Faça logon no seu servidor do Commerce como, ou alterne para, a variável [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Insira qualquer um dos seguintes comandos:

   Digite o seguinte comando para reindexar somente o índice de pesquisa do catálogo:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Digite o seguinte comando para reindexar todos os indexadores:

   ```bash
   bin/magento indexer:reindex
   ```

1. Aguarde até que a reindexação seja concluída.

   >[!INFO]
   >
   >Diferentemente do cache, os indexadores são atualizados por um trabalho cron. Certifique-se de [cron está ativado](../cli/configure-cron-jobs.md) antes de começar a usar seu mecanismo de pesquisa.

