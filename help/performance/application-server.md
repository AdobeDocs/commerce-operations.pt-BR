---
title: Servidor de aplicativos GraphQL
description: Siga estas instruções para habilitar o GraphQL Application Server na implantação do Adobe Commerce.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 2f8396a367cbe1191bdf67aec75bd56f64d3fda8
workflow-type: tm+mt
source-wordcount: '2074'
ht-degree: 0%

---


# Servidor de aplicativos GraphQL

O Commerce GraphQL Application Server permite que o Adobe Commerce mantenha o estado entre as solicitações de API do Commerce GraphQL. O GraphQL Application Server, que é criado na extensão Swoole, opera como um processo com threads de trabalho que lidam com o processamento de solicitações. Ao preservar um estado de aplicativo inicializado entre as solicitações de API do GraphQL, o GraphQL Application Server aprimora o manuseio de solicitações e o desempenho geral do produto. As solicitações de API tornam-se significativamente mais eficientes.

O GraphQL Application Server está disponível somente para o Adobe Commerce. Não está disponível para o Magento Open Source. Para projetos do Cloud Pro, você deve [enviar um tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) para habilitar o Servidor de Aplicativos do GraphQL.

>[!NOTE]
>
>No momento, o GraphQL Application Server não é compatível com [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Os clientes do Adobe Commerce na infraestrutura em nuvem que atualmente usam o [!DNL AWS S3] para [armazenamento remoto](../configuration/remote-storage/cloud-support.md) não podem usar o GraphQL Application Server.

## Arquitetura

O GraphQL Application Server mantém o estado entre as solicitações de API do Commerce GraphQL e elimina a necessidade de inicialização. Ao compartilhar o estado do aplicativo entre os processos, as solicitações do GraphQL tornam-se significativamente mais eficientes, reduzindo os tempos de resposta em até 30%.

O modelo de execução do PHP sem compartilhamento oferece um desafio da perspectiva de latência porque cada solicitação requer o bootstrapping da estrutura. Esse processo de inicialização inclui tarefas demoradas, como ler a configuração, configurar o processo de inicialização e criar objetos de classe de serviço.

A transição da lógica de manipulação de solicitações para um loop de eventos no nível do aplicativo parece solucionar o desafio de simplificar o processamento de solicitações em um nível corporativo. Essa abordagem elimina a necessidade de bootstrapping durante o ciclo de vida de execução da solicitação.

## Vantagens

O GraphQL Application Server permite que o Adobe Commerce mantenha o estado entre solicitações consecutivas da API do Commerce GraphQL. O compartilhamento do estado do aplicativo entre solicitações melhora a eficiência da solicitação da API, minimizando a sobrecarga do processamento e otimizando o manuseio de solicitações. Como resultado, o tempo de resposta de solicitação do GraphQL pode ser reduzido em até 30%.

## Requisitos do sistema

A execução do GraphQL Application Server requer o seguinte:

* Commerce versão 2.4.7+
* PHP 8.2 ou superior
* Extensão PHP v5+ Swoole instalada
* RAM e CPU adequados com base na carga esperada

## Ativar e implantar na infraestrutura em nuvem

O módulo `ApplicationServer` (`Magento/ApplicationServer/`) habilita o Servidor de Aplicativos GraphQL.

### Habilitar projetos Pro

>[!NOTE]
>
>O servidor de aplicativos é um recurso de opt-in nas instâncias do Cloud Pro. Para ativá-lo, envie uma solicitação de suporte.

Depois que o recurso Servidor de aplicativos for ativado em seu projeto Pro, conclua as seguintes etapas antes de implantar o Servidor de aplicativos GraphQL:

1. Implante o Adobe Commerce na infraestrutura de nuvem usando o modelo de nuvem da [2.4.7-ramificação appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Verifique se todas as suas personalizações e extensões do Commerce são [compatíveis](https://developer.adobe.com/commerce/php/development/components/app-server/) com o GraphQL Application Server.
1. Clonar o projeto do Commerce Cloud.
1. Ajuste as configurações no arquivo &#39;application-server/nginx.conf.sample&#39; se necessário.
1. Comente a seção &#39;web&#39; ativa totalmente no arquivo `project_root/.magento.app.yaml`.
1. Remova o comentário da seguinte configuração da seção &#39;web&#39; no arquivo `project_root/.magento.app.yaml` que inclui o comando `start` do GraphQL Application Server.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Verifique se `/application-server/start.sh` é executável executando o seguinte comando:

   ```bash
   chmod +x application-server/start.sh
   ```

1. Adicione arquivos atualizados ao índice Git com este comando:

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Confirme suas alterações com este comando:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Implantar projetos Pro

Após concluir as etapas de ativação, envie as alterações para o repositório Git para implantar o GraphQL Application Server:

```bash
git push
```

### Habilitar projetos iniciais

Conclua as seguintes etapas antes de implantar o GraphQL Application Server em projetos iniciais:

1. Implante o Adobe Commerce na infraestrutura de nuvem usando o modelo de nuvem da [2.4.7-ramificação appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Verifique se todas as personalizações e extensões do Commerce são compatíveis com o GraphQL Application Server.
1. Confirme se a variável de ambiente `CRYPT_KEY` está definida para sua instância. Você pode verificar o status dessa variável no Cloud Console.
1. Clonar o projeto do Commerce Cloud.
1. Renomeie `application-server/.magento/.magento.app.yaml.sample` como `application-server/.magento/.magento.app.yaml` e ajuste as configurações em .magento.app.yaml, se necessário.
1. Descomente a configuração da rota a seguir no arquivo `project_root/.magento/routes.yaml` para redirecionar o tráfego `/graphql` para o GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Adicionar arquivos atualizados ao índice Git:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Confirme suas alterações:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Verifique se todas as configurações personalizadas no arquivo raiz `.magento.app.yaml` foram migradas adequadamente para o arquivo `application-server/.magento/.magento.app.yaml`. Depois que o arquivo `application-server/.magento/.magento.app.yaml` for adicionado ao seu projeto, você deverá mantê-lo além do arquivo `.magento.app.yaml` raiz. Por exemplo, se você precisar [configurar o serviço RabbitMQ](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) ou [gerenciar propriedades da Web](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property), adicione a mesma configuração ao `application-server/.magento/.magento.app.yaml` também.

### Implantar projetos iniciais

Após concluir as [etapas](#before-you-begin-a-cloud-starter-deployment) de habilitação, envie as alterações para o repositório Git para implantar o GraphQL Application Server:

```bash
git push
```

### Verificar habilitação em projetos na nuvem

1. Execute uma consulta ou mutação do GraphQL na sua instância para confirmar se o ponto de extremidade `graphql` está acessível. Por exemplo:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   A resposta esperada deve ser semelhante a este exemplo:

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Use SSH para acessar a instância da nuvem. O `project_root/var/log/application-server.log` deve conter um novo registro de log para cada solicitação GraphQL.

1. Você também pode verificar se o GraphQL Application Server está em execução executando o seguinte comando:

   ```bash
   ps aux|grep php
   ```

   Você deve ver um processo `bin/magento server:run` com vários threads.

Se essas etapas de verificação forem bem-sucedidas, o GraphQL Application Server estará em execução e atendendo a `/graphql` solicitações.

## Habilitar projetos locais

O módulo `ApplicationServer` (`Magento/ApplicationServer/`) habilita o GraphQL Application Server para APIs GraphQL.

A execução local do GraphQL Application Server requer a instalação da extensão Swoole e uma pequena alteração no arquivo de configuração Nginx da implantação.

### Pré-requisitos

Conclua as seguintes etapas antes de habilitar o módulo `ApplicationServer`:

* Configurar Nginx
* Instalar e configurar a extensão Swoole v5+

#### Configurar Nginx

A implantação específica do Commerce determina como configurar o Nginx. Em geral, o arquivo de configuração Nginx é nomeado por padrão `nginx.conf` e é colocado em um destes diretórios: `/usr/local/nginx/conf`, `/etc/nginx`, ou `/usr/local/etc/nginx`. Consulte o _[Guia do Iniciante](https://nginx.org/en/docs/beginners_guide.html)_ para obter mais informações sobre a configuração do Nginx.

Exemplo de configuração do Nginx:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Instalar e configurar Swoole

Para executar o GraphQL Application Server localmente, instale a extensão Swoole (v5.0 ou superior). Há várias maneiras de instalar essa extensão.

O procedimento seguinte descreve como instalar a extensão Swoole para PHP 8.2 em sistemas baseados em OSX. É uma das várias maneiras de instalar a extensão Swoole.

```bash
pecl install swoole
```

Durante a instalação, o Adobe Commerce exibe prompts para habilitar o suporte para `openssl`, `mysqlnd`, `sockets`, `http2` e `postgres`. Digite `yes` para todas as opções, exceto `postgres`.

### Verificar a instalação do Swoole

Confirme se a extensão foi ativada com sucesso:

```bash
php -m | grep swoole
```

### Erros comuns na instalação do Swoole

Todos os erros que ocorrem durante a instalação do Swoole normalmente ocorrem durante a fase de instalação do `pecl`. Os erros típicos incluem arquivos `openssl.h` e `pcre2.h` ausentes. Para resolver esses erros, verifique se esses dois pacotes estão instalados no sistema local.

* Verifique o local de `openssl` executando:

```bash
openssl version -d
```

Este comando mostra o caminho onde o `openssl` está instalado.

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

Para resolver problemas relacionados a `openssl`, execute:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Confirme se você está usando o caminho do ambiente `dev` local.

#### Confirmar resolução de problemas relacionados ao openssl

Você pode executar o comando a seguir novamente para verificar se os problemas relacionados ao openssl foram resolvidos:

```bash
pecl install swoole
```

#### Resolver problemas com pcre2.h

Para resolver problemas relacionados a `pcre2.h`, vincule o caminho `pcre2.h` ao diretório de extensão PHP instalado. Sua versão específica instalada do PHP e do `pcr2.h` determina a versão específica do comando que você deve usar.

### Executar o GraphQL Application Server

Iniciar o GraphQL Application Server:

```bash
bin/magento server:run
```

Esse comando inicia uma porta HTTP em 9501. Depois que o GraphQL Application Server é iniciado, a porta 9501 se torna um servidor proxy HTTP para todas as consultas do GraphQL.

Para confirmar se o GraphQL Application Server está em execução na implantação:

```bash
ps aux | grep php
```

Outras maneiras de confirmar que o GraphQL Application Server está em execução incluem:

* Verifique o arquivo `/var/log/application-server.log` para entradas relacionadas a solicitações GraphQL processadas.
* Tente se conectar à porta HTTP em que o GraphQL Application Server é executado. Por exemplo: `curl -g 'http://localhost:9501/graph`.

### Confirme se as solicitações do GraphQL estão sendo processadas

O GraphQL Application Server adiciona o cabeçalho de resposta `X-Backend` com o valor `graphql_server` a cada solicitação processada. Para verificar se um GraphQL Application Server tratou de uma solicitação, verifique esse cabeçalho de resposta.

### Confirmar compatibilidade de extensão e personalização

Os desenvolvedores e comerciantes de extensões devem primeiro verificar se sua extensão e código de personalização seguem as diretrizes descritas em _[Diretrizes técnicas](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_.

Considere estas diretrizes durante a avaliação do código:

* As classes de serviço (ou seja, classes que fornecem comportamento, mas não dados, como `EventManager`) não devem ter estado mutável.
* Evite o acoplamento temporal.

## Desativar o servidor de aplicativos GraphQL

Os procedimentos para desabilitar o GraphQL Application Server variam dependendo se o servidor está sendo executado em uma implantação local ou na nuvem.

### Desabilitar o GraphQL Application Server (nuvem)

1. Remova quaisquer novos arquivos e quaisquer outras alterações de código que tenham sido incluídas na confirmação `AppServer Enabled` durante seus preparativos para a implantação.

1. Confirme as alterações usando este comando:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Implante essas alterações usando este comando:

   ```bash
   git push
   ```

### Desabilitar o GraphQL Application Server (local)

1. Comente a seção `/graphql` do arquivo `nginx.conf` que você adicionou ao habilitar o GraphQL Application Server.
1. Reinicie o nginx.

Esse método de desativação do GraphQL Application Server pode ser útil para testar ou comparar o desempenho rapidamente.

### Confirme se o GraphQL Application Server está desativado

Para confirmar se `php-fpm` está processando solicitações do GraphQL em vez do Servidor de Aplicativos GraphQL, digite este comando: `ps aux | grep php`.

Depois que o GraphQL Application Server for desativado:

* `bin/magento server:run` está inativo.
* `var/log/application-server.log` não contém entradas após solicitações GraphQL.

## Integração e testes funcionais do GraphQL Application Server

Os desenvolvedores de extensão podem executar dois testes de integração para verificar a compatibilidade da extensão com o GraphQL Application Server: `GraphQlStateTest` e `ResetAfterRequestTest`.

### GraphQlStateTest

O `GraphQlStateTest` detecta um estado em objetos compartilhados que não deve ser reutilizado para várias solicitações.

Este teste foi projetado para detectar alterações de estado em objetos de serviço que o `ObjectManager` produz. O teste executa consultas GraphQL idênticas duas vezes e compara o estado do objeto de serviço antes e depois da segunda consulta.

#### Falhas de GraphQlStateTest e possível correção

* **Não é possível adicionar, ignorar ou filtrar uma lista**. Se você vir um erro sobre adicionar, ignorar ou filtrar uma lista, considere se é possível refatorar a classe de uma maneira compatível com versões anteriores para usar as fábricas de classes de serviço que têm estado mutável.

* **A classe exibe um estado mutável**. Se a própria classe exibir um estado mutável, tente reescrever seu código para contornar esse estado. Se o estado mutável for necessário por motivos de desempenho, implemente `ResetAfterRequestInterface` e use `_resetState()` para redefinir o objeto para seu estado construído inicial.

* **A propriedade digitada $x não deve ser acessada antes da mensagem de inicialização**. Falhas com esse tipo de mensagem sugerem que a propriedade especificada não foi inicializada pelo construtor. Esta é uma forma de acoplamento temporal que ocorre porque o objeto não pode ser usado após ser construído inicialmente. Essa combinação ocorre mesmo se a propriedade for privada porque o Coletor que recupera os dados das propriedades está usando o recurso de reflexão do PHP. Nesse caso, tente refatorar a classe para evitar acoplamento temporal e evitar estado mutável. Se essa refatoração não resolver a falha, você poderá alterar o tipo de propriedade para um tipo anulável para que ele possa ser inicializado como nulo.  Se a propriedade for uma matriz, tente inicializar a propriedade como uma matriz vazia.

Executar `GraphQlStateTest` executando `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

O `ResetAfterRequestTest` procura todas as classes que implementam `ResetAfterRequestInterface` e verifica se o método `_resetState()` retorna o estado de um objeto ao mesmo estado que ele manteve após ser construído por `ObjectManager`.  Este teste cria um objeto de serviço com `ObjectManager`, clona esse objeto, chama `_resetState()` e compara ambos os objetos. O teste não chama nenhum método entre a instanciação de objeto e `_resetState()`, portanto, não confirma a redefinição de nenhum estado mutável. Ele não encontra problemas em que um erro ou erro de digitação em `_resetState()` possa definir o estado para algo diferente do que era originalmente.

#### Falhas de ResetAfterRequestTest e possível correção

* **A classe tem valores de propriedade inconsistentes**. Se esse teste falhar, verifique se uma classe foi alterada com o resultado de que o objeto após a construção tem valores de propriedade diferentes dos que tem após a chamada do método `_resetState()`. Se a classe em que você está trabalhando não contiver o método `_resetState()` em si, verifique a hierarquia de classe de uma superclasse que o implemente.

* **A propriedade digitada $x não deve ser acessada antes da mensagem de inicialização**. Esse problema também ocorre com `GraphQlStateTest`.

  Executar `ResetAfterRequestTest` executando: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Teste funcional

ao implantar o GraphQL Application Server, os desenvolvedores de extensão devem executar testes funcionais da WebAPI e quaisquer testes funcionais automatizados ou manuais personalizados para o GraphQL. Esses testes funcionais ajudam os desenvolvedores a identificar possíveis erros ou problemas de compatibilidade.

#### Modo de Monitor de Estado

Durante a execução de testes funcionais (ou testes manuais), o GraphQL Application Server pode ser executado com o `--state-monitor mode` habilitado para ajudar a encontrar classes em que o estado está sendo reutilizado involuntariamente. Inicie o Servidor de Aplicativos normalmente, exceto para adicionar o parâmetro `--state-monitor`.

```
bin/magento server:run --state-monitor
```

Após cada solicitação ser processada, um novo arquivo é adicionado ao diretório `tmp`, por exemplo: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Após concluir o teste, esses arquivos poderão ser mesclados com o comando `bin/magento server:state-monitor:aggregate-output`, que cria dois arquivos mesclados, um em `XML` e um em `JSON`.

Exemplos:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Esses arquivos podem ser inspecionados com qualquer ferramenta usada para exibir XML ou JSON que mostre as propriedades modificadas de objetos de serviço, como o `GraphQlStateTest` faz. O modo `--state-monitor` usa a mesma lista de salto e lista de filtro que GraphQlStateTest.

>[!NOTE]
>
>Não use o modo `--state-monitor` na produção. Ele é projetado apenas para desenvolvimento e teste. Ele cria muitos arquivos de saída e é executado mais lentamente do que o normal.

>[!NOTE]
>
>`--state-monitor` não é compatível com as versões do PHP `8.3.0` - `8.3.4` devido a um erro no coletor de lixo do PHP. Se você estiver usando o PHP 8.3, é necessário atualizar para `8.3.5` ou mais recente para usar este recurso.
