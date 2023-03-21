---
title: Pré-requisitos completos
description: Prepare seu projeto do Adobe Commerce para uma atualização completando essas etapas de pré-requisito.
source-git-commit: 5f86717d79569cac3f95a4c10a55b48f92858466
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# Concluir pré-requisitos de atualização

É importante entender o que é necessário para executar o Adobe Commerce. Você deve primeiro revisar o [requisitos do sistema](../../installation/system-requirements.md) para a versão para a qual você pretende atualizar.

Depois de revisar os requisitos do sistema, você deve concluir os seguintes pré-requisitos antes de atualizar seu sistema:

* Atualizar todo o software
* Verifique se um mecanismo de pesquisa suportado está instalado
* Converter formato de tabela de banco de dados
* Definir o limite de arquivos abertos
* Verifique se trabalhos do cron estão em execução
* Definir `DATA_CONVERTER_BATCH_SIZE`
* Verificar permissões do sistema de arquivos
* Defina as `pub/` raiz do diretório
* Instalar o plug-in de atualização do Composer

## Atualizar todo o software

O [requisitos do sistema](../../installation/system-requirements.md) descreva exatamente quais versões de software de terceiros foram testadas com as versões do Adobe Commerce.

Certifique-se de ter atualizado todos os requisitos e dependências do sistema em seu ambiente. Consulte PHP [7,4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8,1](https://www.php.net/manual/en/migration81.php)e [configurações PHP necessárias](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Para projetos do Adobe Commerce on cloud Infrastructure Pro, você deve criar um [Suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) ticket para instalar ou atualizar serviços em ambientes de preparo e produção. Indique as alterações de serviço necessárias e inclua o `.magento.app.yaml` e `services.yaml` arquivos e versão PHP no tíquete. Pode levar até 48 horas para a equipe de infraestrutura da Cloud atualizar o projeto. Consulte [Software e serviços compatíveis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Verifique se um mecanismo de pesquisa suportado está instalado

O Adobe Commerce requer o Elasticsearch ou o OpenSearch para ser instalado a fim de usar o software.

**Se estiver atualizando de 2.3.x para 2.4**, você deve verificar se está usando MySQL, Elasticsearch ou uma extensão de terceiros como seu mecanismo de pesquisa de catálogo na instância 2.3.x. O resultado determina o que você deve fazer _before_ atualização para 2.4.

**Se você estiver atualizando as versões de patch nas linhas de versão 2.3.x ou 2.4.x**, se o Elasticsearch 7.x já estiver instalado, você poderá optar por [migrar para o OpenSearch](opensearch-migration.md).

Você pode usar a linha de comando ou o Administrador para determinar o mecanismo de pesquisa do catálogo:

* Insira o `bin/magento config:show catalog/search/engine` comando. O comando retorna um valor de `mysql`, `elasticsearch` (que indica que o Elasticsearch 2 está configurado), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`ou um valor personalizado, indicando que você instalou um mecanismo de pesquisa de terceiros. Para versões anteriores à 2.4.6, use o `elasticsearch7` para o mecanismo Elasticsearch 7 ou OpenSearch. Para a versão 2.4.6 e posterior, use o `opensearch` para o mecanismo OpenSearch.

* Em Admin, verifique o valor da variável **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** campo.

As seções a seguir descrevem as ações que devem ser tomadas antes de atualizar para a versão 2.4.0.

### MySQL

A partir da versão 2.4, o MySQL não é mais um mecanismo de pesquisa de catálogo compatível. Você deve instalar e configurar o Elasticsearch ou OpenSearch antes de atualizar. Use os seguintes recursos para ajudar a orientá-lo durante este processo:

* [Instalar e configurar o Elasticsearch](../../configuration/search/overview-search.md)
* [Instalação do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Configurar [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) ou [Apache](../../installation/prerequisites/search-engine/configure-apache.md) para trabalhar com seu mecanismo de pesquisa
* [Configurar o Commerce para usar o Elasticsearch](../../configuration/search/configure-search-engine.md) e reindexe

Alguns mecanismos de pesquisa de catálogo de terceiros são executados sobre o mecanismo de pesquisa do Adobe Commerce. Entre em contato com seu fornecedor para determinar se você deve atualizar sua extensão.

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Mecanismo de pesquisa

Você deve instalar e configurar o Elasticsearch 7.6 ou superior ou o OpenSearch 1.2 antes de atualizar para 2.4.0. O Adobe não é mais compatível com o Elasticsearch 2.x, 5.x e 6.x. [Configuração do mecanismo de pesquisa](../../configuration/search/configure-search-engine.md) no _Guia de configuração_ descreve as tarefas que você deve executar após atualizar o Elasticsearch para uma versão compatível.

Consulte [Atualização do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obter instruções completas sobre como fazer backup de seus dados, detectar possíveis problemas de migração e testar atualizações antes de implantar na produção. Dependendo da versão atual do Elasticsearch, pode ser ou não necessário reiniciar o cluster completo.

O Elasticsearch requer o Java Development Kit (JDK) 1.8 ou superior. Consulte [Instale o Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para verificar qual versão do JDK está instalada.

#### OpenSearch

O OpenSearch é uma bifurcação de código aberto do Elasticsearch 7.1 0.2, após a mudança de licenciamento do Elasticsearch. As seguintes versões do Adobe Commerce apresentam suporte para o OpenSearch:

* 2.4.6 (o OpenSearch tem um módulo e configurações separados)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

Você pode [migrar do Elasticsearch para o OpenSearch](opensearch-migration.md) somente se estiver atualizando para uma versão do Adobe Commerce listada acima (ou posterior).

O OpenSearch requer o JDK 1.8 ou superior. Consulte [Instale o Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para verificar qual versão do JDK está instalada.

[Configuração do mecanismo de pesquisa](../../configuration/search/configure-search-engine.md) descreve as tarefas que devem ser realizadas após alterar os mecanismos de pesquisa.

#### Atualizar o Elasticsearch

O suporte para o Elasticsearch 8.x foi introduzido no Adobe Commerce 2.4.6. As instruções a seguir mostram um exemplo de atualização do Elasticsearch de 7.x para 8.x:

1. Atualize o servidor Elasticsearch 7.x para 8.x e verifique se ele está funcionando. Consulte a [Documentação do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Ative o `id_field_data` adicionando a seguinte configuração ao seu `elasticsearch.yml` e reiniciando o serviço Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Para ser compatível com o Elasticsearch 8.x, o Adobe Commerce 2.4.6 não permite a variável `indices.id_field_data` por padrão e usa a variável `_id` no campo `docvalue_fields` propriedade.

1. No diretório raiz do seu projeto do Adobe Commerce, atualize as dependências do Composer para remover o `Magento_Elasticsearch7` e instale o `Magento_Elasticsearch8` módulo.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. Atualize os componentes do projeto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurar Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) no [!DNL Admin].

1. Reindexe o índice de catálogo.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Exclua todos os itens dos tipos de cache ativados.

   ```bash
   bin/magento cache:clean
   ```

#### Descarregar Elasticsearch

Se você atualizar inadvertidamente a versão do Elasticsearch em seu servidor ou determinar que precisa ser baixado por qualquer outro motivo, também será necessário atualizar as dependências do projeto do Adobe Commerce. Por exemplo, para fazer o downgrade do Elasticsearch 8.x para o 7.x

1. Faça o download do servidor Elasticsearch 8.x para 7.x e verifique se ele está funcionando. Consulte a [Documentação do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. No diretório raiz do seu projeto do Adobe Commerce, atualize as dependências do Composer para remover o `Magento_Elasticsearch8` e suas dependências do Composer e instale o `Magento_Elasticsearch7` módulo.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Atualize os componentes do projeto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurar Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) no [!DNL Admin].

1. Reindexe o índice de catálogo.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Exclua todos os itens dos tipos de cache ativados.

   ```bash
   bin/magento cache:clean
   ```

### Extensões de terceiros

Recomendamos que você entre em contato com o fornecedor do mecanismo de pesquisa para determinar se a extensão é totalmente compatível com uma versão do Adobe Commerce.

## Converter formato de tabela de banco de dados

Você deve converter o formato de todas as tabelas de banco de dados de `COMPACT` para `DYNAMIC`. Você também deve converter o tipo de mecanismo de armazenamento de `MyISAM` para `InnoDB`. Consulte [práticas recomendadas](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md).

## Definir o limite de arquivos abertos

A definição do limite de arquivos abertos (ulimit) pode ajudar a evitar a falha de várias chamadas recursivas de longas sequências de consulta ou problemas com o uso da variável `bin/magento setup:rollback` comando. Esse comando é diferente para diferentes shell UNIX. Consulte seu sabor individual para obter detalhes sobre o `ulimit` comando.

O Adobe recomenda configurar os arquivos abertos [ulimit](https://ss64.com/bash/ulimit.html) para um valor de `65536` ou mais, mas você pode usar um valor maior, se necessário. Você pode definir o limite na linha de comando ou torná-lo uma configuração permanente para o shell do usuário.

Para definir o limite da linha de comando:

1. Alterne para [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Defina o limite como `65536`.

   ```bash
   ulimit -n 65536
   ```

Para definir o valor no shell Bash:

1. Alterne para [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Abrir `/home/<username>/.bashrc` em um editor de texto.
1. Adicione a seguinte linha:

   ```bash
   ulimit -n 65536
   ```

1. Salve as alterações no `.bashrc` e saia do editor de texto.

>[!IMPORTANT]
>
>Recomendamos que você evite definir um valor para a variável `pcre.recursion_limit` na `php.ini` porque pode resultar em reversões incompletas sem aviso de falha.

## Verifique se trabalhos do cron estão em execução

O agendador de tarefas UNIX `cron` O é essencial para as operações diárias da Adobe Commerce. Ele programa coisas como reindexação, boletins informativos, e-mails e mapas de sites. Vários recursos exigem pelo menos um trabalho cron em execução como proprietário do sistema de arquivos.

Para verificar se o trabalho do cron está configurado corretamente, verifique o crontab inserindo o seguinte comando como proprietário do sistema de arquivos:

>[!NOTE]
>
>O crontab é o arquivo de configuração responsável pela execução de tarefas do cron.

```bash
crontab -l
```

Resultados semelhantes ao seguinte devem ser exibidos:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Outro sintoma de falha de execução é o seguinte erro no Admin:

![](../../assets/upgrade-guide/cron-not-running.png)

Para ver o erro, clique em **Mensagens do sistema** na parte superior da janela, como se segue:

![](../../assets/upgrade-guide/system-messages.png)

Consulte [Configurar e executar o cron](../../configuration/cli/configure-cron-jobs.md) para obter mais informações.

## Definir DATA_CONVERTER_BATCH_SIZE

O Adobe Commerce 2.4 inclui aprimoramentos de segurança que exigem que alguns dados sejam convertidos de serializados para JSON. Essa conversão ocorre durante a atualização e pode levar muito tempo, dependendo da quantidade de dados no banco de dados.

As tabelas a seguir são mais afetadas:

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

Se você tiver uma grande quantidade de dados, poderá melhorar o desempenho definindo o valor de uma variável de ambiente, `DATA_CONVERTER_BATCH_SIZE`. Por padrão, o valor é definido como `50,000`.

Para definir a variável de ambiente:

1. Alterne para [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Defina a variável :

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` exige memória; evite configurá-la com um valor grande (aproximadamente 1 GB) sem testá-la primeiro.

1. Após a conclusão da atualização, é possível desdefinir a variável :

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Verificar permissões do sistema de arquivos

Por motivos de segurança, o Adobe Commerce exige determinadas permissões no sistema de arquivos. As permissões são diferentes de _[propriedade](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. A propriedade determina quem pode executar ações no sistema de arquivos; determinam o que o usuário pode fazer.

Os diretórios no sistema de arquivos devem ser graváveis pelo [do proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md) grupo.

Para verificar se as permissões do sistema de arquivos estão definidas corretamente, faça logon no servidor de aplicativos ou use o aplicativo gerenciador de arquivos do seu provedor de hospedagem.

Por exemplo, insira o seguinte comando se o aplicativo estiver instalado em `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

Exemplo de saída:

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

Veja o seguinte para uma explicação da saída da amostra:

* A maioria dos arquivos são `-rw-rw----`, que `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* O proprietário do sistema de arquivos é `magento_user`

Para obter informações mais detalhadas, você pode inserir o seguinte comando:

```bash
ls -la /var/www/html/magento2/pub
```

Como o Adobe Commerce implanta ativos de arquivos estáticos em subdiretórios de `pub`Além disso, é uma boa ideia verificar também as permissões e a propriedade.

Para obter mais informações, consulte [Permissões e propriedade do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

## Defina as `pub/` raiz do diretório

Consulte [Modificar ponto para melhorar a segurança](../../installation/tutorials/docroot.md) para obter mais detalhes.

## Instalar o plug-in de atualização do Composer

O [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) O plug-in do Composer resolve as alterações que devem ser feitas no projeto raiz `composer.json` antes de atualizar para um novo requisito do produto.

O plug-in automatiza parcialmente a atualização manual, identificando e ajudando você a resolver conflitos de dependência em vez de exigir que você os identifique e corrija manualmente.

Para instalar o plug-in:

1. Adicione o pacote ao seu `composer.json` arquivo.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Atualize as dependências:

   ```bash
   composer update
   ```
