---
title: Ativar ou desativar modo de manutenção
description: Siga estas etapas para personalizar o que os clientes veem quando a implantação do Adobe Commerce está inativa para manutenção.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Ativar ou desativar modo de manutenção

O guia a seguir se refere a uma página de modo de manutenção padrão. Se você precisar usar uma página de manutenção personalizada, consulte o tópico [Criar a página de manutenção personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md).

O Adobe Commerce usa o [modo de manutenção](../../configuration/bootstrap/application-modes.md#maintenance-mode) para desabilitar a inicialização. Desativar a inicialização é útil enquanto você mantém, atualiza ou reconfigura o site.

O aplicativo detecta o modo de manutenção da seguinte maneira:

* Se `var/.maintenance.flag` existir, o modo de manutenção está ativado, e o aplicativo retornará uma página de manutenção 503.
* Se `var/.maintenance.ip` existir e o IP do cliente corresponder a uma das entradas de endereço IP nesse arquivo, a página de manutenção será ignorada para a solicitação.

## Instalar o aplicativo

Antes de usar este comando para habilitar ou desabilitar o modo de manutenção, você deve [instalar o aplicativo](../advanced.md).

## Ativar ou desativar modo de manutenção

Use o comando da CLI `magento maintenance` para habilitar ou desabilitar o modo de manutenção.

Uso do comando:

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

A opção `--ip=<ip address>` é um endereço IP para isentar do modo de manutenção (por exemplo, desenvolvedores fazendo a manutenção). Para isentar mais de um endereço IP no mesmo comando, use a opção várias vezes.

>[!NOTE]
>
>Usar `--ip=<ip address>` com `magento maintenance:disable` salva a lista de IPs para uso posterior. Para limpar a lista de IPs isentos, use `magento maintenance:enable --ip=none` ou consulte [Manter a lista de endereços IP isentos](#maintain-the-list-of-exempt-ip-addresses).

O comando `bin/magento maintenance:status` exibe o status do modo de manutenção.

Por exemplo, para ativar o modo de manutenção sem isenções de endereço IP:

```bash
bin/magento maintenance:enable
```

Para ativar o modo de manutenção para todos os clientes, exceto 192.0.2.10 e 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Depois de colocar a aplicação no modo de manutenção, você deve interromper todos os processos do consumidor da fila de mensagens.
Uma maneira de encontrar esses processos é executar o comando `ps -ef | grep queue:consumers:start` e depois executar o comando `kill <process_id>` para cada consumidor. Em um ambiente com vários nós, repita essa tarefa em cada nó.

## Manter a lista de endereços IP isentos

Para manter a lista de endereços IP isentos, você pode usar a opção `[--ip=<ip list>]` nos comandos anteriores ou usar o seguinte:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

A sintaxe `<ip address> .. <ip address>` é uma lista opcional delimitada por espaços de endereços IP para isentar.

A opção `--none` limpa a lista.

## Configurações de várias lojas

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Se quiser configurar vários armazenamentos, cada um com um layout diferente e conteúdo localizado, passe o parâmetro `$_GET['skin']` para o processador pretendido.

No exemplo a seguir, estamos usando um arquivo de modelo de erro do tipo `503`, que requer conteúdo localizado.

O construtor da classe `Error_Processor` aceita um parâmetro de GET `skin` para alterar o layout:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Isso também pode ser adicionado a uma regra de regravação no arquivo `.htaccess` que anexa um parâmetro `skin` à URL.

### Parâmetro $_GET[&#39;skin&#39;]

Para usar o parâmetro `skin`:

1. Verifique se o `.maintenance.flag` existe.
1. Observe o endereço do host, que se refere ao `HTTP_HOST`, ou qualquer outra variável, como as variáveis ENV.
1. Verifique se o parâmetro `skin` existe.
1. Defina o parâmetro usando as regras de regravação abaixo.

   Estes são alguns exemplos de regras de regravação:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copie os seguintes arquivos:

   * `pub/errors/default/503.phtml` a `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` a `pub/errors/sub/styles.css`

1. Edite esses arquivos para fornecer conteúdo localizado no arquivo `503.phtml` e estilo personalizado no arquivo `styles.css`.

   Verifique se os caminhos apontam para o diretório `errors`. O nome do diretório deve corresponder ao parâmetro de URL indicado em `RewriteRule`. No exemplo anterior, o diretório `sub` é usado, que é especificado como um parâmetro em `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>A configuração [nginx](../../configuration/multi-sites/ms-nginx.md) deve ser adicionada para configurações de várias lojas.
