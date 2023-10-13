---
title: Servidor de aplicativos para APIs do GraphQL
description: Siga estas instruções para habilitar o Servidor de Aplicativos para APIs do GraphQL na implantação do Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b7639e8830b2cab971e3e22285d91105b64e9a6e
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# Servidor de aplicativos para APIs do GraphQL

O Commerce Application Server para APIs do GraphQL permite que o Adobe Commerce mantenha o estado entre as solicitações de API do Commerce GraphQL. O Servidor de Aplicativos, que é construído na extensão Open Swoole, opera como um processo com threads de trabalho que lidam com o processamento de solicitações. Ao preservar um estado de aplicativo inicializado entre as solicitações de API do GraphQL, o Servidor de Aplicativos melhora o manuseio de solicitações e o desempenho geral do produto. As solicitações de API tornam-se significativamente mais eficientes.

O Servidor de Aplicativos é compatível somente com o Cloud Starter e implantações locais. Não está disponível para instâncias do Cloud Pro durante a versão Beta. Não está disponível para implantações de Magento Open Source.

## Visão geral da arquitetura do servidor de aplicativos

O servidor de aplicativos mantém o estado entre as solicitações de API do Commerce GraphQL e elimina a necessidade de inicialização. Ao compartilhar o estado do aplicativo entre os processos, as solicitações do GraphQL tornam-se significativamente mais eficientes, reduzindo os tempos de resposta em até 30%.

O modelo de execução do PHP sem compartilhamento oferece um desafio da perspectiva de latência porque cada solicitação requer o bootstrapping da estrutura. Esse processo de inicialização inclui tarefas demoradas, como ler a configuração, configurar o processo de inicialização e criar objetos de classe de serviço.

A transição da lógica de manipulação de solicitações para um loop de eventos no nível do aplicativo parece solucionar o desafio de simplificar o processamento de solicitações em um nível corporativo. Essa abordagem elimina a necessidade de bootstrapping durante o ciclo de vida de execução da solicitação.

## Vantagens de usar o servidor de aplicativos

O servidor de aplicativos permite que o Adobe Commerce mantenha o estado entre solicitações consecutivas da API do Commerce GraphQL. O compartilhamento do estado do aplicativo entre solicitações melhora a eficiência da solicitação da API, minimizando a sobrecarga do processamento e otimizando o manuseio de solicitações. Como resultado, o tempo de resposta de solicitação do GraphQL pode ser reduzido em até 30%.

## Requisitos do sistema

A execução do Servidor de Aplicativos requer o seguinte:

* PHP 8.2 ou superior
* Open Swoole PHP extension v22+ instalada
* RAM e CPU adequadas com base na carga esperada

## Habilitar Servidor de Aplicativos para Iniciador na Nuvem

A variável `ApplicationServer` módulo (`Magento/ApplicationServer/`) ativa o servidor de aplicativos para APIs do GraphQL. O Servidor de Aplicativos é compatível somente com implantações locais e do Cloud Starter. Não está disponível para instâncias do Cloud Pro durante a versão Beta.

### Antes de iniciar uma implantação do Cloud Starter

Conclua as seguintes tarefas antes de implantar o Servidor de Aplicativos:

1. Confirme se o Adobe Commerce está instalado no Commerce Cloud.
1. Confirme se o `CRYPT_KEY` A variável de ambiente está definida para sua instância. Você pode verificar o status dessa variável no Portal de projetos na nuvem (interface de integração).
1. Clonar o projeto do Commerce Cloud.
1. Criar um `graphql` pasta no seu `project_root` pasta.
1. Adicione o personalizado adicional `.magento.app.yaml` arquivo incluído na [conteúdo do arquivo magento.app.yaml](#magento.app.yaml-file-content) tópico em seu `project_root/graphql` pasta.
1. Edite o `project_root/.magento/routes.yaml` arquivo para incluir estas diretivas:

   ```yaml
   # The routes of the project.
   #
   # Each route describes how an incoming URL is going to be processed.
   
   "http://{default}/":
     type: upstream
     upstream: "mymagento:http"
   
   "http://{default}/graphql":
     type: upstream
     upstream: "graphql:http"
   ```

1. Adicione arquivos atualizados ao índice Git com este comando:

   ```bash
   git add -f php.ini graphql/.magento.app.yaml .magento/routes.yaml swoole.so
   ```

1. Confirme suas alterações com este comando:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Implantar Servidor de Aplicativos no Cloud Starter

Após executar as tarefas de pré-requisito, implante o Servidor de Aplicativos usando este comando:

```bash
git push
```

### Verificar a ativação do servidor de aplicativos no Cloud Starter

1. Abra a interface do usuário do projeto na nuvem. Você deve ver um ponto de acesso SSH adicional para o `graphql` aplicação.

1. Use SSH para acessar a instância da nuvem usando o ponto de acesso do aplicativo graphql e execute o seguinte comando:

   ```bash
   ps aux|grep php
   ```

1. Execute uma consulta ou mutação do GraphQL em relação à sua instância para confirmar que `graphql` o endpoint está acessível. Por exemplo:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   A resposta esperada deve ser semelhante a este exemplo:

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Use SSH para acessar a instância da nuvem por meio do ponto de acesso do aplicativo do GraphQL. A variável `project_root/var/log/magento-server.log` deve conter um novo registro para cada solicitação do GraphQL.

Se essas etapas de verificação forem bem-sucedidas, você poderá prosseguir com a execução do ciclo de testes.


## Habilitar o Servidor de Aplicativos em implantações locais

A variável `ApplicationServer` módulo (`Magento/ApplicationServer/`) ativa o servidor de aplicativos para APIs do GraphQL.

A execução do Application Server requer a instalação da extensão Open Swoole e uma pequena alteração no arquivo de configuração Nginx da implantação para executar este servidor de aplicativos localmente.

### Antes de iniciar uma implantação local

Conclua essas duas tarefas antes de ativar o `ApplicationServer` módulo:

* Configurar Nginx

* Instale e configure a extensão Open Swoole v22

### Configurar Nginx

A implantação específica do Commerce determina como configurar o Nginx. Em geral, o arquivo de configuração do Nginx é nomeado por padrão `nginx.conf` e é colocado em um destes diretórios: `/usr/local/nginx/conf`, `/etc/nginx`ou `/usr/local/etc/nginx`. Consulte [Guia para iniciantes](https://nginx.org/en/docs/beginners_guide.html) para obter mais informações sobre a configuração do Nginx.

Exemplo de configuração do Nginx:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Instalar e configurar o Open Swoole

Para executar o Servidor de Aplicativos localmente, instale a extensão Open Swoole v22. Há várias maneiras de instalar essa extensão.

## Executar Servidor de Aplicativos

Iniciar o servidor de aplicativos:

```bash
bin/magento server:run
```

Esse comando inicia uma porta HTTP em 9501. Depois que o Servidor de Aplicativos é iniciado, a porta 9501 se torna um servidor proxy HTTP para todas as consultas do GraphQL.

## Exemplo: Instalar o Open Swoole (OSX)

Este procedimento ilustra como instalar a extensão Open Swoole no PHP 8.2 para sistemas baseados em OSX. É uma das várias maneiras de instalar a extensão Open Swoole.

### Instalar o Open Swoole

Digite:

```bash
pecl install openswoole-22.0.0
composer require openswoole/core:22.1.1
```

Durante a instalação, o Adobe Commerce exibe prompts para ativar o suporte para `openssl`, `mysqlnd`, `sockets`, `http2`, e `postgres`. Enter `yes` para todas as opções, exceto `postgres`.

### Confirmar instalação de Open Swoole

Executar `php -m | grep openswoole` para confirmar que a extensão do foi ativada com sucesso.

### Erros comuns na instalação do Open Swoole

Todos os erros que ocorrem durante a instalação do Open Swoole normalmente ocorrem durante o `pecl` instalação. Os erros típicos incluem erros ausentes `openssl.h` e `pcre2.h` arquivos. Para resolver esses erros, verifique se esses dois pacotes estão instalados no sistema local.

* Verifique o local de `openssl` executando:

```bash
openssl version -d
```

Este comando mostra o caminho onde `openssl` O está instalado.

* Verifique o local de `pcre2` executando:

```bash
pcre2-config --prefix 
```

Use o Homebrew para instalar os pacotes ausentes se a saída do comando indicar que os arquivos estão ausentes:

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Resolver problemas com o openssl

Para resolver problemas relacionados ao `openssl`, executar:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Confirme se você está usando o caminho do local `dev` ambiente.

#### Confirmar resolução de problemas relacionados ao openssl

Você pode executar o comando a seguir novamente para verificar se os problemas relacionados ao openssl foram resolvidos:

```bash
pecl install openswoole-22.0.0
```

#### Resolver problemas com pcre2.h

Para resolver problemas relacionados ao `pcre2.h`, symlink para o `pcre2.h` caminho para o diretório de extensão PHP instalado. Sua versão específica instalada do PHP e `pcr2.h` determina a versão específica do comando que deve ser usada.

### Confirmar se o servidor de aplicativos está em execução

Para confirmar se o Servidor de Aplicativos está sendo executado na implantação, execute este comando:

```bash
ps aux | grep php
```

Outras maneiras de confirmar que o Servidor de Aplicativos está sendo executado incluem:

* Verifique a `/var/log/magento-server.log` arquivo para entradas relacionadas a solicitações GraphQL processadas.
* Tente se conectar à porta HTTP em que o Servidor de Aplicativos é executado. Por exemplo: `curl -g 'http://localhost:9501/graph`.

### Confirmar se as solicitações do GraphQL estão sendo processadas pelo Servidor de Aplicativos

O Servidor de aplicativos adiciona o `X-Backend` cabeçalho de resposta com o valor `graphql_server` para cada solicitação processada. Para verificar se uma solicitação foi tratada pelo Servidor de Aplicações, verifique esse cabeçalho de resposta.

### Confirmar a compatibilidade de extensão e personalização com o Servidor de Aplicativos

Os desenvolvedores e comerciantes de extensões devem primeiro verificar se a extensão e o código de personalização seguem as diretrizes técnicas descritas em [Diretrizes técnicas](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Considere estas diretrizes durante a avaliação do código:

* Classes de serviço (ou seja, classes que fornecem comportamento, mas não dados, como `EventManager`) não deve ter estado mutável.
* Evite o acoplamento temporal.

## Desabilitar Servidor de Aplicativos

Os procedimentos para desabilitar o Servidor de Aplicativos variam, dependendo se o servidor está sendo executado em uma implantação local ou na Nuvem.

### Desabilitar Servidor de Aplicativos no Cloud Starter

1. Remova quaisquer novos arquivos e quaisquer outras alterações de código que tenham sido incluídos na variável `AppServer Enabled` durante seus preparativos para a implantação.

1. Confirme as alterações usando este comando:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Implante essas alterações usando este comando:

   ```bash
   git push
   ```

### Desabilitar Servidor de Aplicativos

1. Comente a `/graphql` seção de `nginx.conf` arquivo que você adicionou ao ativar o Servidor de Aplicativos.
1. Reinicie o nginx.

Esse método de desativação do Servidor de Aplicativos pode ser útil para testar ou comparar rapidamente o desempenho.

### Confirmar se o Servidor de Aplicativos está desabilitado

Para confirmar se as solicitações do GraphQL estão sendo processadas pelo `php-fpm` em vez do Servidor de Aplicativos, digite este comando: `ps aux | grep php`.

Depois que o Servidor de Aplicativos tiver sido desabilitado:

* `bin/magento server:run` está inativo.
* `var/log/magento-server.log` não contém entradas após as solicitações do GraphQL.

## Integração e testes funcionais para o servidor de aplicativos PHP

Os desenvolvedores de extensão podem executar dois testes de integração para verificar a compatibilidade da extensão com o Servidor de aplicativos: `GraphQlStateTest` e `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` O detecta o estado em objetos compartilhados que não deve ser reutilizado para várias solicitações.

Este teste foi projetado para detectar alterações de estado em objetos de serviço produzidos pelo `ObjectManager`. O teste executa consultas GraphQL idênticas duas vezes e compara o estado do objeto de serviço antes e depois da segunda consulta. 

#### Falhas de GraphQlStateTest e possível correção

* **Não é possível adicionar, ignorar ou filtrar uma lista**. Se você encontrar uma falha que sugira que não é seguro adicionar, ignorar ou filtrar uma lista, considere se a classe pode ser refatorada de uma maneira compatível com versões anteriores para usar as fábricas das classes de serviço que têm estado mutável.

* **A classe exibe um estado mutável**. Se a própria classe exibir um estado mutável, tente reescrever seu código para contornar esse estado. Se o estado mutável for necessário por motivos de desempenho, implemente `ResetAfterRequestInterface` e usar `_resetState()` para redefinir o objeto ao seu estado construído inicial.

* **A propriedade digitada $x não deve ser acessada antes da mensagem de inicialização**. Falhas com esse tipo de mensagem sugerem que a propriedade especificada não foi inicializada pelo construtor. Esta é uma forma de acoplamento temporal que ocorre porque o objeto não pode ser usado após ser construído inicialmente. Essa combinação ocorre mesmo se a propriedade for privada porque o Coletor que recupera os dados das propriedades está usando o recurso de reflexão do PHP. Nesse caso, tente refatorar a classe para evitar acoplamento temporal e evitar estado mutável. Se essa refatoração não resolver a falha, você poderá alterar o tipo de propriedade para um tipo anulável para que ele possa ser inicializado como nulo.  Se a propriedade for uma matriz, tente inicializar a propriedade como uma matriz vazia.

Executar `GraphQlStateTest` executando `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` procura todas as classes que implementam `ResetAfterRequestInterface` e verifica se o `_resetState()` método retorna o estado de um objeto ao mesmo estado que ele manteve após ser construído por `ObjectManager`.  Este teste cria um objeto de serviço com `ObjectManager`O, em seguida, clona esse objeto, chama `_resetState()`, e compara ambos os objetos. O teste não chama nenhum método entre a instanciação de objeto e `_resetState()`, portanto, não confirma a redefinição de nenhum estado mutável. Ele não encontra problemas em que um erro ou erro de digitação `_resetState()` pode definir o estado como algo diferente do que era originalmente.

#### Falhas de ResetAfterRequestTest e possível correção

* **A classe tem valores de propriedade inconsistentes**. Se esse teste falhar, verifique se uma classe foi alterada, com o resultado de que o objeto após a construção tem valores de propriedade diferentes daqueles após a `_resetState()` é chamado. Se a classe em que você está trabalhando não contiver a variável `_resetState()` e, em seguida, verifique a hierarquia de classes para uma superclasse que o implementa.

* **A propriedade digitada $x não deve ser acessada antes da mensagem de inicialização**. Esse problema também ocorre com `GraphQlStateTest`.
 
Executar `ResetAfterRequestTest` executando: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Teste funcional

Os desenvolvedores de extensão devem executar testes funcionais de WebAPI para o GraphQL, bem como quaisquer testes funcionais automatizados ou manuais personalizados para o GraphQL, ao implantar o servidor de aplicativos. Esses testes funcionais ajudam os desenvolvedores a identificar possíveis erros ou problemas de compatibilidade.

## conteúdo do arquivo magento.app.yaml

Consulte [Antes de iniciar uma implantação do Cloud Starter](#Before-you-begin-a-Cloud-Starter-deployment) para obter instruções sobre como adicionar o seguinte código ao `project_root/graphql` pasta.

```yaml
name: graphql
# The toolstack used to build the application.
type: php:8.2
build:
    flavor: none
 
source:
    root: /
dependencies:
    php:
        composer/composer: '2.5.5'
 
# Enable extensions required by Magento 2
runtime:
    extensions:
        - xsl
        - sodium
 
# The relationships of the application with services or other applications.
# The left-hand side is the name of the relationship as it will be exposed
# to the application in the environment variable. The right-hand
# side is in the form `<service name>:<endpoint name>`.
relationships:
    database: "mysql:mysql"
    redis: "redis:redis"
    opensearch: "opensearch:opensearch"
 
# The configuration of app when it is exposed to the web.
web:
    commands:
        start: "php -dopcache.enable_cli=1 -dopcache.validate_timestamps=0 bin/magento server:run -vvv  --port=${PORT:-80} > ${MAGENTO_CLOUD_APP_DIR}/var/log/magento-server.log 2>&1"
    upstream:
        socket_family: tcp
        protocol: http
    locations:
        '/':
            root: "pub"
            passthru: true
 
# The size of the persistent disk of the application (in MB).
disk: 5120
 
# The mounts that will be performed when the package is deployed.
mounts:
    "var": "shared:files/var"
    "app/etc": "shared:files/etc"
    "pub/media": "shared:files/media"
    "pub/static": "shared:files/static"
 
hooks:
    # We run build hooks before your application has been packaged.
    build: |
        set -e
        composer install
        php ./vendor/bin/ece-tools run scenario/build/generate.xml
        php ./vendor/bin/ece-tools run scenario/build/transfer.xml
    # We run deploy hook after your application has been deployed and started.
    deploy: |
        php ./vendor/bin/ece-tools run scenario/deploy.xml
    # We run post deploy hook to clean and warm the cache. Available with ECE-Tools 2002.0.10.
    post_deploy: |
        php ./vendor/bin/ece-tools run scenario/post-deploy.xml
```
