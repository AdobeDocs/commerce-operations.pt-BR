---
title: Pré-requisitos completos
description: Prepare seu projeto do Adobe Commerce ou Magento Open Source para uma atualização completando essas etapas de pré-requisito.
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---


# Concluir pré-requisitos de atualização

É importante entender o que é necessário para executar o Adobe Commerce ou o Magento Open Source. Você deve primeiro revisar o [requisitos do sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) para a versão para a qual você pretende atualizar.

Depois de revisar os requisitos do sistema, você deve concluir os seguintes pré-requisitos antes de atualizar seu sistema:

- Atualizar todo o software
- Verifique se o Elasticsearch está instalado
- Definir o limite de arquivos abertos
- Verifique se trabalhos do cron estão em execução
- Definir `DATA_CONVERTER_BATCH_SIZE`
- Verificar permissões do sistema de arquivos
- Defina as `pub/` raiz do diretório
- Instalar o plug-in de atualização do Composer

## Atualizar todo o software

O [requisitos do sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) descreva exatamente quais versões de software de terceiros foram testadas com o Adobe Commerce e versões de Magento Open Source.

Certifique-se de ter atualizado todos os requisitos e dependências do sistema em seu ambiente. Consulte PHP [7,4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8,1](https://www.php.net/manual/en/migration81.php)e [configurações PHP necessárias](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html#php-required-set).

## Verifique se o Elasticsearch está instalado

Adobe Commerce e Magento Open Source exigem a instalação do Elasticsearch para usar o software. Antes de atualizar da 2.3.x para a 2.4, você deve verificar se está usando o MySQL, o Elasticsearch ou uma extensão de terceiros como mecanismo de pesquisa de catálogo na instância 2.3.x. O resultado determina o que você deve fazer _before_ atualização para 2.4.

Você pode usar a linha de comando ou o Administrador para determinar o mecanismo de pesquisa do catálogo:

- Insira o `bin/magento config:show catalog/search/engine` comando. O comando retorna um valor de `mysql`, `elasticsearch` (que indica que o Elasticsearch 2 está configurado), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`ou um valor personalizado, indicando que você instalou um mecanismo de pesquisa de terceiros.

- Em Admin, verifique o valor da variável **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** campo.

As seções a seguir descrevem as ações que devem ser tomadas antes de atualizar para a versão 2.4.0.

### MySQL

A partir da versão 2.4, o MySQL não é mais um mecanismo de pesquisa de catálogo compatível. Você deve instalar e configurar o Elasticsearch antes de atualizar. Use os seguintes recursos para ajudar a orientá-lo durante este processo:

- [Instalar e configurar o Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-overview.html)
- [Instalação do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configure o Elasticsearch para funcionar com [nginx](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-nginx.html) ou [Apache](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-apache.html)
- [Configurar o Commerce para usar o Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) e reindexe

Alguns mecanismos de pesquisa de catálogo de terceiros são executados sobre o mecanismo de pesquisa do Adobe Commerce. Entre em contato com seu fornecedor para determinar se você deve atualizar sua extensão.

### Elasticsearch

Você deve instalar e configurar o Elasticsearch antes de atualizar para a versão 2.4.0. O Adobe não é mais compatível com o Elasticsearch 2.x, 5.x e 6.x.

Consulte [Atualização do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obter instruções completas sobre como fazer backup de seus dados, detectar possíveis problemas de migração e testar atualizações antes de implantar na produção. Dependendo da versão atual do Elasticsearch, pode ser ou não necessário reiniciar o cluster completo.

O Elasticsearch requer o JDK 1.8 ou superior. Consulte [Instale o Java Software Development Kit (JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) para verificar qual versão do JDK está instalada.

[Configurar o Magento para usar o Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) descreve as tarefas que devem ser realizadas após atualizar o Elasticsearch 2 para uma versão compatível.

### Extensões de terceiros

Recomendamos que você entre em contato com o fornecedor do mecanismo de pesquisa para determinar se a extensão é totalmente compatível com a versão 2.4.

## Definir o limite de arquivos abertos

A definição do limite de arquivos abertos (ulimit) pode ajudar a evitar a falha de várias chamadas recursivas de longas sequências de consulta ou problemas com o uso da variável `bin/magento setup:rollback` comando. Esse comando é diferente para diferentes shell UNIX. Consulte seu sabor individual para obter detalhes sobre o `ulimit` comando.

O Adobe recomenda configurar os arquivos abertos [ulimit](https://ss64.com/bash/ulimit.html) para um valor de `65536` ou mais, mas você pode usar um valor maior, se necessário. Você pode definir o limite na linha de comando ou torná-lo uma configuração permanente para o shell do usuário.

Para definir o limite da linha de comando:

1. Alterne para [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Defina o limite como 65536.

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > A sintaxe para arquivos abertos depende do UNIX shell usado. A configuração anterior deve funcionar com CentOS e Ubuntu com o shell Bash. No entanto, para o sistema operacional Mac, a configuração correta é ulimit -S 65532. Consulte uma página principal ou uma referência de sistema operacional para obter mais informações.

Para definir o valor no shell Bash:

1. Alterne para [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Abrir `/home/<username>/.bashrc` em um editor de texto.
1. Adicione a seguinte linha:

   ```bash
   ulimit -s 65536
   ```

1. Salve as alterações no `.bashrc` e saia do editor de texto.

>[!IMPORTANT]
>
>Recomendamos que você evite definir um valor para a variável `pcre.recursion_limit` na `php.ini` porque pode resultar em reversões incompletas sem aviso de falha.

## Verifique se trabalhos do cron estão em execução

O agendador de tarefas UNIX `cron` O é essencial para as operações diárias do Adobe Commerce e do Magento Open Source. Ele programa coisas como reindexação, boletins informativos, e-mails, mapas de sites e assim por diante. Vários recursos exigem pelo menos um trabalho cron em execução como proprietário do sistema de arquivos.

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

Consulte [Configurar e executar o cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) para obter mais informações.

## Definir DATA_CONVERTER_BATCH_SIZE

O Adobe Commerce 2.4 inclui aprimoramentos de segurança que exigem que alguns dados sejam convertidos de serializados para JSON. Essa conversão ocorre durante a atualização e pode levar muito tempo, dependendo da quantidade de dados no banco de dados.

As tabelas a seguir são mais afetadas:

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

Se você tiver uma grande quantidade de dados, poderá melhorar o desempenho definindo o valor de uma variável de ambiente, `DATA_CONVERTER_BATCH_SIZE`. Por padrão, o valor é definido como `50,000`.

Para definir a variável de ambiente:

1. Alterne para [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Defina a variável :

   ```bash
   export DATA_CONVERTER_BATCH_SIZE 100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` exige memória; evite configurá-la com um valor grande (aproximadamente 1 GB) sem testá-la primeiro.

1. Após a conclusão da atualização, é possível desdefinir a variável :

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Verificar permissões do sistema de arquivos

Por motivos de segurança, o Adobe Commerce e o Magento Open Source exigem determinadas permissões no sistema de arquivos. As permissões são diferentes de _[propriedade](https://devdocs.magento.com/guides/v2.4/comp-mgr/prereq/prereq_compman-checklist.html#magento-owner-group)_. A propriedade determina quem pode executar ações no sistema de arquivos; determinam o que o usuário pode fazer.

Os diretórios no sistema de arquivos devem ser graváveis pelo [do proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) grupo.

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

- A maioria dos arquivos são `-rw-rw----`, que `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- O proprietário do sistema de arquivos é `magento_user`

Para obter informações mais detalhadas, você pode inserir o seguinte comando:

```bash
ls -la /var/www/html/magento2/pub
```

Como o Adobe Commerce e o Magento Open Source implantam ativos de arquivos estáticos em subdiretórios de `pub`, é uma boa ideia verificar também as permissões e a propriedade.

Para obter mais informações, consulte [Permissões e propriedade do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

## Defina as `pub/` raiz do diretório

Consulte [Modificar ponto para melhorar a segurança](https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html) para obter mais detalhes.

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
