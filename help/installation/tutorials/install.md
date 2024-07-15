---
title: Instalar o Adobe Commerce
description: Siga estas etapas para instalar o Adobe Commerce na sua infraestrutura.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '2094'
ht-degree: 0%

---

# Instalar o Adobe Commerce

Antes de começar, conclua as seguintes etapas:

* Verifique se o seu sistema atende aos requisitos discutidos nos [requisitos de sistema](../system-requirements.md).

* Conclua todas as tarefas de [pré-requisito](../prerequisites/overview.md).

* Conclua as primeiras etapas de instalação. Consulte [Caminho de instalação ou atualização](../overview.md).

* Depois de fazer logon no servidor de aplicativos, [alterne para o proprietário do sistema de arquivos](../prerequisites/file-system/overview.md).

* Revise a visão geral da [Introdução à instalação da linha de comando](../composer.md).

>[!NOTE]
>
>Você deve instalar o aplicativo de seu subdiretório `bin`.

Você pode executar o instalador várias vezes com opções diferentes para concluir tarefas de instalação como as seguintes:

* Instalar em fases — Por exemplo, depois de configurar o servidor Web para SSL (Secure Sockets Layer), você pode executar o instalador novamente para definir as opções de SSL.

* Corrigir erros em instalações anteriores.

* Instale o aplicativo em uma instância de banco de dados diferente.

>[!NOTE]
>
>Por padrão, o instalador não substitui o banco de dados se você instalar o software Commerce na mesma instância do banco de dados. Você pode usar o parâmetro `cleanup-database` opcional para alterar esse comportamento.

Consulte também [Atualizar, reinstalar, desinstalar](uninstall.md).

## Instalação segura

{{$include /help/_includes/secure-install.md}}

## Comandos de ajuda do instalador

Você pode executar os seguintes comandos para localizar valores para alguns argumentos necessários:

| Argumento do instalador | Comando |
| ------------------ | ------------------------------- |
| Idioma | `magento info:language:list` |
| Moeda | `magento info:currency:list` |
| Fuso horário | `magento info:timezone:list` |

>[!NOTE]
>
>Se um erro for exibido ao executar esses comandos, verifique se você atualizou as dependências de instalação conforme discutido em [Atualizar dependências de instalação](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Instalar da linha de comando

O comando install usa o seguinte formato:

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

As tabelas a seguir descrevem os nomes e valores das opções de instalação, como comandos de instalação. Consulte [Exemplos de instalações localhost](#sample-localhost-installations).

>[!NOTE]
>
>Qualquer opção que contenha espaços ou caracteres especiais deve estar entre aspas simples ou duplas.

**Credenciais de administrador:**

As opções a seguir especificam as informações e credenciais do usuário administrador.

No Adobe Commerce versão 2.2.8 e posterior, é possível criar o usuário administrador durante ou após a instalação. Se você criar o usuário durante a instalação, todas as variáveis de credencial do administrador serão necessárias. Consulte [Exemplos de instalações localhost](#sample-localhost-installations).

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--admin-firstname` | Nome do usuário administrador. | Sim |
| `--admin-lastname` | Sobrenome do usuário administrador. | Sim |
| `--admin-email` | Endereço de email do usuário administrador. | Sim |
| `--admin-user` | Nome de usuário do administrador. | Sim |
| `--admin-password` | Senha de usuário administrador. A senha deve ter pelo menos 7 caracteres e incluir pelo menos um caractere alfabético e um caractere numérico. Recomendamos uma senha mais longa e complexa. Coloque toda a string de senha entre aspas simples. Por exemplo, `--admin-password='A0b9%t3g'` | Sim |

**Opções de configuração de site e banco de dados:**

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--base-url` | URL base a ser usada para acessar seu Administrador e vitrine em qualquer um dos seguintes formatos:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Observação:** O esquema (http:// ou https://) e uma barra à direita são necessários.<br><br>`<your install dir>` é o caminho relativo de docroot no qual instalar o aplicativo. Dependendo de como você configura o servidor Web e os hosts virtuais, o caminho pode ser magento2 ou pode estar em branco.<br><br>Para acessar o aplicativo em localhost, você pode usar `http://127.0.0.1/<your install dir>/` ou `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` que representa uma URL base definida por uma configuração de host virtual ou por um ambiente de virtualização como o Docker. Por exemplo, se você configurar um host virtual com o nome de host commerce.example.com, poderá instalar o aplicativo com `--base-url={{base_url}}` e acessar o Administrador com uma URL como `http://commerce.example.com/admin`. | Sim |
| `--backend-frontname` | URI (Uniform Resource Identifier) para acessar o Administrador. Você pode omitir este parâmetro para permitir que o aplicativo gere um URI aleatório para você com o seguinte padrão <code>admin_jkhgdfq</code>.<br><br>Recomendamos um URI aleatório para fins de segurança. Um URI aleatório é mais difícil de ser explorado por hackers ou softwares mal-intencionados.<br><br>O URI é exibido no final da instalação. Você pode exibi-lo posteriormente a qualquer momento usando o comando `magento info:adminuri`.<br><br>Se você optar por inserir um valor, recomendamos que não use uma palavra comum como admin, backend. O URI do Administrador pode conter valores alfanuméricos e somente o caractere de sublinhado (`_`). | Não |
| `--db-host` | Use qualquer um dos seguintes:<br><br>- O nome de host ou endereço IP totalmente qualificado do servidor de banco de dados.<br><br>- `localhost` (padrão) ou `127.0.0.1` se o servidor de banco de dados estiver no mesmo host que o servidor Web.localhost significa que a biblioteca de cliente MySQL usa soquetes UNIX para se conectar ao banco de dados. `127.0.0.1` faz com que a biblioteca do cliente use o protocolo TCP. Para obter mais informações sobre soquetes, consulte a [documentação do PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Observação:** você pode especificar opcionalmente a porta do servidor de banco de dados em seu nome de host, como www.example.com:9000 | Sim |
| `--db-name` | Nome da instância do banco de dados em que você deseja instalar as tabelas do banco de dados.<br><br>O padrão é `magento2`. | Sim |
| `--db-user` | Nome de usuário do proprietário da instância do banco de dados.<br><br>O padrão é `root`. | Sim |
| `--db-password` | Senha do proprietário da instância do banco de dados. | Sim |
| `--db-prefix` | Use apenas se estiver instalando as tabelas do banco de dados em uma instância do banco de dados que já tenha tabelas do Adobe Commerce.<br><br>Nesse caso, use um prefixo para identificar as tabelas desta instalação. Alguns clientes têm mais de uma instância do Adobe Commerce em execução em um servidor com todas as tabelas no mesmo banco de dados.<br><br>O prefixo pode ter no máximo cinco caracteres. Ela deve começar com uma letra e pode incluir apenas letras, números e caracteres sublinhados.<br><br>Essa opção permite que esses clientes compartilhem o servidor de banco de dados com mais de uma instalação. | Não |
| `--db-ssl-key` | Caminho para a chave do cliente. | Não |
| `--db-ssl-cert` | Caminho para o certificado do cliente. | Não |
| `--db-ssl-ca` | Caminho para o certificado do servidor. | Não |
| `--language` | Código de idioma a ser usado no Admin e na loja. (Se ainda não tiver feito isso, você poderá exibir a lista de códigos de idioma digitando `magento info:language:list` no diretório bin.) | Não |
| `--currency` | Moeda padrão a ser usada na loja. (Se ainda não tiver feito isso, você poderá exibir a lista de moedas digitando `magento info:currency:list` no diretório bin.) | Não |
| `--timezone` | Fuso horário padrão a ser usado na administração e na loja. (Se você ainda não tiver feito isso, poderá exibir a lista de fusos horários inserindo `magento info:timezone:list` no diretório bin.) | Não |
| `--use-rewrites` | `1` significa que você usa regravações do servidor Web para links gerados na vitrine e no Administrador.<br><br>`0` desabilita o uso de regravações do servidor Web. Este é o padrão. | Não |
| `--use-secure` | `1` habilita o uso de SSL (Secure Sockets Layer) nas URLs de vitrine. Antes de selecionar essa opção, verifique se o servidor Web oferece suporte para SSL.<br><br>`0` desabilita o uso de SSL. Nesse caso, presume-se que todas as outras opções de URL seguro também sejam 0. Este é o padrão. | Não |
| `--base-url-secure` | URL base segura a ser usada para acessar seu Administrador e vitrine eletrônica no seguinte formato: `http[s]://<host or ip>/<your install dir>/` | Não |
| `--use-secure-admin` | `1` significa que você usa SSL para acessar o Administrador. Antes de selecionar essa opção, verifique se o servidor Web oferece suporte para SSL.<br><br>`0` significa que você não usa SSL com o Administrador. Este é o padrão. | Não |
| `--admin-use-security-key` | 1 faz com que o aplicativo use um valor de chave gerado aleatoriamente para acessar páginas no Admin e em formulários. Esses valores principais ajudam a impedir ataques de falsificação de script entre sites. Este é o padrão.<br><br>`0` desabilita o uso da chave. | Não |
| `--session-save` | Use qualquer um dos seguintes:<br><br>- `db` para armazenar dados de sessão no banco de dados. Escolha armazenamento de banco de dados se você tiver um banco de dados clusterizado; caso contrário, pode não haver muito benefício sobre o armazenamento baseado em arquivo.<br><br>- `files` para armazenar dados de sessão no sistema de arquivos. O armazenamento de sessão baseado em arquivo é apropriado, a menos que o acesso ao sistema de arquivos seja lento, você tenha um banco de dados clusterizado ou deseje armazenar dados de sessão em Redis.<br><br>- `redis` para armazenar dados de sessão em Redis. Se você estiver usando Redis para cache padrão ou de página, Redis já deve estar instalado. Consulte Usar Redis para armazenamento de sessão para obter informações adicionais sobre a configuração do suporte para Redis. | Não |
| `--key` | Se você tiver uma, especifique uma chave para criptografar dados confidenciais no banco de dados. Se você não tiver um, o aplicativo gera um para você. | Sim |
| `--cleanup-database` | Para eliminar tabelas de banco de dados antes de instalar a aplicação, especifique este parâmetro sem um valor. Caso contrário, o banco de dados será deixado intacto. | Não |
| `--db-init-statements` | Parâmetro de configuração avançado do MySQL. Usa instruções de inicialização de banco de dados a serem executadas ao conectar-se ao banco de dados MySQL. Consulte uma referência semelhante a esta antes de definir quaisquer valores.<br><br>O padrão é `SET NAMES utf8;`. | Não |
| `--sales-order-increment-prefix` | Especifique um valor da cadeia de caracteres a ser usada como prefixo para ordens de venda. Normalmente, isso é usado para garantir números de pedido exclusivos para processadores de pagamento. | Não |

>[!TIP]
>
>Para habilitar serviços de armazenamento remoto durante a instalação, consulte [Configurar Armazenamento Remoto](../../configuration/remote-storage/remote-storage.md) no _Guia de Configuração_.

**Opções de configuração do mecanismo de pesquisa:**

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--search-engine` | A versão do mecanismo de pesquisa. Os valores possíveis são `elasticsearch7`, `elasticsearch6` e `elasticsearch5`. O padrão é `elasticsearch7`. Se você instalou o OpenSearch como mecanismo de pesquisa, especifique o valor `elasticsearch7`. O Elasticsearch 5 foi descontinuado e não é recomendado. | Não |
| `--elasticsearch-host` | O nome do host ou endereço IP onde o mecanismo de pesquisa está sendo executado. O padrão é `localhost`. | Não |
| `--elasticsearch-port` | A porta para solicitações HTTP de entrada. O padrão é `9200`. | Não |
| `--elasticsearch-index-prefix` | Um prefixo que identifica o índice de pesquisa. O padrão é `magento2`. | Não |
| `--elasticsearch-timeout` | O número de segundos antes de o sistema expirar. O padrão é `15`. | Não |
| `--elasticsearch-enable-auth` | Habilita a autenticação no servidor do mecanismo de pesquisa. O padrão é `false`. | Não |
| `--elasticsearch-username` | A ID do usuário a ser autenticada | Não, a menos que a autenticação esteja habilitada |
| `--elasticsearch-password` | A senha para autenticação | Não, a menos que a autenticação esteja habilitada |

**[!DNL RabbitMQ]opções de configuração:**

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--amqp-host` | Não use as opções de `--amqp`, a menos que já tenha configurado uma instalação do [!DNL RabbitMQ]. Consulte a instalação do [!DNL RabbitMQ] para obter mais informações sobre como instalar e configurar o [!DNL RabbitMQ].<br><br>O nome do host em que [!DNL RabbitMQ] está instalado. | Não |
| `--amqp-port` | A porta a ser usada para conexão com [!DNL RabbitMQ]. O padrão é 5672. | Não |
| `--amqp-user` | O nome de usuário para conexão com [!DNL RabbitMQ]. Não usar o usuário padrão `guest`. | Não |
| `--amqp-password` | A senha para conexão com [!DNL RabbitMQ]. Não usar a senha padrão `guest`. | Não |
| `--amqp-virtualhost` | O host virtual para conexão com [!DNL RabbitMQ]. O padrão é `/`. | Não |
| `--amqp-ssl` | Indica se é necessário conectar a [!DNL RabbitMQ]. O padrão é `false`. Consulte [!DNL RabbitMQ] para obter informações sobre como configurar o SSL para [!DNL RabbitMQ]. | Não |
| `--consumers-wait-for-messages` | Os consumidores devem aguardar uma mensagem da fila? 1 - Sim, 0 - Não | Não |

**Opções de armazenamento remoto:**

| Nome | Descrição | Obrigatório? |
|--- |--- |--- |
| `remote-storage-driver` | Nome do adaptador<br>Valores possíveis:<br>**arquivo**: desabilita o armazenamento remoto e usa o sistema de arquivos local <br>**aws-s3**: Use o [Serviço de Armazenamento Simples da Amazon (Amazon S3)](https://aws.amazon.com/s3/) | Não |
| `remote-storage-bucket` | Armazenamento de objetos ou nome do container | Não |
| `remote-storage-prefix` | Prefixo opcional (local dentro do armazenamento de objetos) | Não |
| `remote-storage-region` | Nome da região | Não |
| `remote-storage-key` | Chave de acesso opcional | Não |
| `remote-storage-secret` | Chave secreta opcional | Não |

**Opções de configuração de bloqueio:**

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--lock-provider` | Nome do provedor de bloqueio.<br><br>Provedores de bloqueio disponíveis: `db`, `zookeeper`, `file`.<br><br>O provedor de bloqueio padrão: `db` | Não |
| `--lock-db-prefix` | O prefixo do banco de dados específico para evitar conflitos de bloqueio ao usar o provedor de bloqueio `db`.<br><br>O valor padrão: `NULL` | Não |
| `--lock-zookeeper-host` | Host e porta para se conectar ao cluster Zookeeper quando você usar o provedor de bloqueio `zookeeper`.<br><br>Por exemplo: `127.0.0.1:2181` | Sim, se você definir `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | O caminho onde o Zookeeper salva bloqueios.<br><br>O caminho padrão é: `/magento/locks` | Não |
| `--lock-file-path` | O caminho onde os bloqueios de arquivo são salvos. | Sim, se você definir `--lock-provider=file` |

**Opções de configuração de consumidores:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Para habilitar ou desabilitar módulos após a instalação do aplicativo, consulte [Habilitar e desabilitar módulos](manage-modules.md).

**Dados confidenciais:**

{{$include /help/_includes/sensitive-data.md}}

### Exemplos de instalações localhost

Os exemplos a seguir mostram os comandos para instalar o Adobe Commerce localmente com várias opções.

#### Exemplo 1 — Instalação básica com conta de usuário administrador

O exemplo a seguir instala o aplicativo com as seguintes opções:

* O aplicativo está instalado no diretório `magento2` relativo ao docroot do servidor Web em `localhost` e o caminho para o Administrador é `admin`; portanto:

  Sua URL de vitrine é `http://127.0.0.1`

* O servidor de banco de dados está no mesmo host que o servidor Web.

  O nome do banco de dados é `magento`, e o nome de usuário e a senha são `magento`

* Usa regravações de servidor

* O administrador tem as seguintes propriedades:

   * O nome e o sobrenome são `Commerce User`
   * Nome de usuário é `admin` e senha é `admin123`
   * O endereço de email é `user@example.com`

* O idioma padrão é `en_US` (inglês americano)
* A moeda padrão é dólares americanos
* O fuso horário padrão é Central dos EUA (América/Chicago)
* O Elasticsearch 7 está instalado em `es-host.example.com` e se conecta na porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Mensagens semelhantes às seguintes são exibidas para indicar uma instalação bem-sucedida:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Exemplo 2 — Instalação básica sem conta de usuário administrador

Você pode instalar o aplicativo sem criar o usuário administrador, conforme mostrado no exemplo a seguir.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Mensagens como as seguintes serão exibidas se a instalação for bem-sucedida:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Após a instalação, você pode criar um usuário administrador usando o comando `admin:user:create`:
[Criar ou editar um administrador](admin.md#create-or-edit-an-administrator)

#### Exemplo 3 — Instalação com opções adicionais

O exemplo a seguir instala o aplicativo com as seguintes opções:

* O Magapplication está instalado no diretório `magento2` relativo ao docroot do servidor Web em `localhost` e o caminho para o Administrador é `admin`; portanto:

  Sua URL de vitrine é `http://127.0.0.1`

* O servidor de banco de dados está no mesmo host que o servidor Web.

  O nome do banco de dados é `magento`, e o nome de usuário e a senha são `magento`

* O administrador tem as seguintes propriedades:

   * O nome e o sobrenome são `Commerce User`
   * Nome de usuário é `admin` e senha é `admin123`
   * O endereço de email é `user@example.com`

* O idioma padrão é `en_US` (inglês americano)
* A moeda padrão é dólares americanos
* O fuso horário padrão é Central dos EUA (América/Chicago)
* O instalador primeiro limpa o banco de dados antes de instalar as tabelas e o esquema
* Você usa um prefixo de incremento de ordem de venda `ORD$` (como ele contém um caractere especial [`$`], o valor deve ser colocado entre aspas duplas)
* Os dados da sessão são salvos no banco de dados
* Usa regravações de servidor
* O Elasticsearch 7 está instalado em `es-host.example.com` e se conecta na porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>Você deve inserir o comando em uma única linha ou, como no exemplo anterior, com um caractere `\` no final de cada linha.

Mensagens como as seguintes serão exibidas se a instalação for bem-sucedida:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>Se você tiver uma conta de usuário para acessar o servidor de aplicativos, consulte [definir uma máscara](../next-steps/set-umask.md). Esse tipo de configuração é típica de hospedagem compartilhada.
