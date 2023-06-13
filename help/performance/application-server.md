---
title: Servidor de aplicativos para APIs do GraphQL
description: Siga estas instruções para habilitar o Servidor de Aplicativos para APIs do GraphQL na implantação do Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta1" type="informative"
source-git-commit: 28bfc54e0f15ba4f4f941acc7d1fb4825702cdf3
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Servidor de aplicativos para APIs do GraphQL

O Commerce Application Server para APIs do GraphQL permite que o Adobe Commerce mantenha o estado entre as solicitações de API do Commerce GraphQL e diminui o tempo de inicialização de cada solicitação. Ao compartilhar o estado do aplicativo entre os processos, as solicitações de API tornam-se significativamente mais eficientes.

Esta versão beta do Application Server está disponível somente para implantações locais executando PHP 8.1 ou 8.2. Não é compatível com implantações baseadas em nuvem. Ele ainda não oferece suporte à funcionalidade B2B do GraphQL. As solicitações GraphQL podem não funcionar como esperado em implantações locais quando esta versão do servidor de aplicativos PHP estiver configurada.

## Quem pode usar o Servidor de Aplicativos?

O Servidor de Aplicativos está disponível somente para implantações locais do Commerce.

## Habilitar o servidor de aplicativos para APIs do GraphQL

A variável `ApplicationServer` módulo (`Magento/ApplicationServer/`) ativa o servidor de aplicativos para APIs do GraphQL.

A execução do Application Server requer a instalação da extensão Open Swoole e uma pequena alteração no arquivo de configuração Nginx da implantação para executar este servidor de aplicativos localmente.

### Antes de começar

Conclua essas duas tarefas antes de ativar o `ApplicationServer` módulo:

* Configurar Nginx

* Instale e configure a extensão Open Swoole v22

### Configurar Nginx

A implantação específica do Commerce determina como configurar o Nginx. Em geral, o arquivo de configuração do Nginx é nomeado por padrão `nginx.conf` e é colocado em um destes diretórios: `/usr/local/nginx/conf`, `/etc/nginx`ou `/usr/local/etc/nginx`. Consulte [Guia para iniciantes](http://nginx.org/en/docs/beginners_guide.html) para obter mais informações sobre a configuração do Nginx.

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

Você pode instalar a extensão Open Swoole para PHP (v22) e os pacotes do Composer que essa extensão requer com um comando.

### Instalar o Open Swoole

Digite:

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

Durante a instalação, o Adobe Commerce exibe prompts para ativar o suporte para `openssl`, `mysqlnd`, `sockets`, `http2`, e `postgres`. Enter `yes` para todas as opções, exceto `postgres`.

### Confirmar instalação de Open Swoole

Executar `php -m | grep openswoole` para confirmar que a extensão do foi ativada com sucesso.

### Erros comuns na instalação do Open Swoole

Todos os erros que ocorrem durante a instalação do Open Swoole normalmente ocorrem durante o `pecl` instalação. Os erros típicos incluem erros ausentes `openssl.h` e `pcre2.h` arquivos. Para resolver esses erros, verifique se esses dois pacotes estão instalados no sistema local.

* Verificar local de `openssl` executando:

```bash
openssl version -d
```

Este comando mostra o caminho onde `openssl` O está instalado.

* Verificar local de `pcre2` executando:

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

