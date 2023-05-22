---
title: Configuração do mecanismo de pesquisa
description: Configure um mecanismo de pesquisa para implantações locais de Adobe Commerce e Magento Open Source.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Configuração do mecanismo de pesquisa

Esta seção discute as configurações mínimas que você deve escolher para testar o Elasticsearch ou o OpenSearch com implantações locais do Adobe Commerce e do Magento Open Source.

>[!TIP]
>
>Nas versões 2.4.4 e 2.4.3-p2, todos os campos rotulados **Elasticsearch** também se aplica ao OpenSearch.
>Quando o suporte para o Elasticsearch 8.x foi introduzido na versão 2.4.6, novos rótulos foram criados para distinguir entre configurações Elasticsearch e OpenSearch.

Para obter detalhes adicionais sobre a configuração do mecanismo de pesquisa, consulte [Guia do usuário](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## Configurar o mecanismo de pesquisa no Admin

>[!TIP]
>
>Para obter instruções sobre como atualizar para uma nova versão do mecanismo de pesquisa, consulte [pré-requisitos de atualização](../../upgrade/prepare/prerequisites.md).

Para configurar seu sistema para usar o Elasticsearch ou o OpenSearch:

1. Faça logon no Admin como administrador.
1. Clique em **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. No **[!UICONTROL Search Engine]** selecione a versão correspondente do mecanismo de pesquisa.

   A tabela a seguir lista as opções necessárias para configurar e testar a conexão com o Commerce. A menos que você tenha alterado as configurações do servidor do mecanismo de pesquisa, os padrões deverão funcionar. Vá para a próxima etapa.

   | Opção | Descrição |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Insira o nome de host ou endereço IP totalmente qualificado da máquina que executa o Elasticsearch ou o OpenSearch.<br>Adobe Commerce na infraestrutura em nuvem: obtenha esse valor de seu sistema de integração. |
   | **[!UICONTROL Server Port]** | Insira a porta do proxy do servidor Web. O padrão é 9200<br>Adobe Commerce na infraestrutura em nuvem: obtenha esse valor de seu sistema de integração. |
   | **[!UICONTROL Index Prefix]** | Insira o prefixo de índice do mecanismo de pesquisa. Se você usar uma única instância para mais de uma instalação do Commerce (ambientes de Preparo e Produção), deverá especificar um prefixo exclusivo para cada instalação. Caso contrário, você poderá usar o prefixo padrão magento2. |
   | **[!UICONTROL Enable HTTP Auth]** | Clique em **[!UICONTROL Yes]** somente se você tiver ativado a autenticação para o servidor do mecanismo de pesquisa. Em caso afirmativo, forneça um nome de usuário e senha nos campos fornecidos. |
   | **[!UICONTROL Server Timeout]** | Insira o tempo (em segundos) de espera ao tentar estabelecer uma conexão com o servidor Elasticsearch ou OpenSearch. |

1. Clique em **[!UICONTROL Test Connection]**.

   Exemplo de resposta:

   ![success](../../assets/configuration/elastic_test-success.png)

   Continuar com:

   - [Configurar o Apache para seu mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Configurar o nginx para seu mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-nginx.md)

   ou você verá:

   ![falhou](../../assets/configuration/elastic_test-fail.png)

Em caso afirmativo, tente o seguinte:

- Verifique se o servidor do mecanismo de pesquisa está em execução.
- Se o servidor estiver em um host diferente do Commerce, faça logon no servidor do Commerce e execute ping no host do mecanismo de pesquisa. Resolva os problemas de conectividade de rede e teste a conexão novamente.
- Examine a janela de comando na qual você iniciou o Elasticsearch ou o OpenSearch para rastreamentos e exceções de pilha. Você deve resolvê-los antes de continuar. Em particular, inicie seu mecanismo de pesquisa como um usuário com `root` privilégios.
- Verifique se [Firewall UNIX e SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) O está desativado ou configurou regras para permitir que o mecanismo de pesquisa e o Commerce se comuniquem entre si.
- Verifique o valor do **[!UICONTROL Server Hostname]** campo. Verifique se o servidor está disponível. Em vez disso, você pode tentar o endereço IP do servidor.
- Use o `netstat -an | grep <listen-port>` para verificar se a porta especificada na variável **[!UICONTROL Server Port]** O campo não está sendo usado por outro processo.

   Por exemplo, para ver se o mecanismo de pesquisa está em execução na porta padrão, use o seguinte comando:

   ```bash
   netstat -an | grep 9200
   ```

   Se estiver sendo executado na porta 9200, será exibido de modo semelhante ao seguinte:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Reindexe a pesquisa de catálogo e atualize o cache de página inteira

Depois de alterar a configuração do mecanismo de pesquisa, você deve reindexar o índice de pesquisa do catálogo e atualizar o cache da página inteira usando a linha de comando Admin ou.

Para atualizar o cache usando o Administrador:

1. Em Admin, clique em **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Marque a caixa de seleção ao lado de **[!UICONTROL Page Cache]**.
1. No **[!UICONTROL Actions]** no canto superior direito, clique em **Atualizar**.

   ![gerenciamento de cache](../../assets/configuration/refresh-cache.png)

Para limpar o cache usando a linha de comando: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Para reindexar usando a linha de comando:

1. Faça logon no servidor do Commerce como ou alterne para a [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Digite qualquer um dos comandos a seguir:

   Informe o seguinte comando para reindexar somente o índice de pesquisa do catálogo:

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
   >Diferentemente do cache, os indexadores são atualizados por um trabalho cron. Verifique se [cron está habilitado](../cli/configure-cron-jobs.md) antes de começar a usar o mecanismo de pesquisa.
