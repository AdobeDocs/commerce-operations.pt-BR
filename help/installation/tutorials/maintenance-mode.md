---
title: Ativar ou desativar modo de manutenção
description: Siga estas etapas para personalizar o que os clientes verão quando a implantação do Adobe Commerce ou Magento Open Source estiver inativa para manutenção.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Ativar ou desativar modo de manutenção

O guia a seguir se refere a uma página de modo de manutenção padrão. Se precisar usar uma página de manutenção personalizada, consulte [Criar a página de manutenção personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md) tópico.

Adobe Commerce e Magento Open Source usam [modo de manutenção](../../configuration/bootstrap/application-modes.md#maintenance-mode) para desativar a inicialização. Desativar a inicialização é útil enquanto você mantém, atualiza ou reconfigura o site.

O aplicativo detecta o modo de manutenção da seguinte maneira:

* Se `var/.maintenance.flag` não existir, o modo de manutenção estiver desativado e o aplicativo funcionar normalmente.
* Caso contrário, o modo de manutenção será ativado, a menos que `var/.maintenance.ip` existe.

  `var/.maintenance.ip` pode conter uma lista de endereços IP. Se um ponto de entrada for acessado usando HTTP e o endereço IP do cliente corresponder a uma das entradas nessa lista, o modo de manutenção estará desativado.

## Instalar o aplicativo

Antes de usar este comando para ativar ou desativar o modo de manutenção, você deve [instalar o aplicativo](../advanced.md).

## Ativar ou desativar modo de manutenção

Use o `magento maintenance` Comando da CLI para ativar ou desativar o modo de manutenção.

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

A variável `--ip=<ip address>` é um endereço IP para isentar do modo de manutenção (por exemplo, desenvolvedores que estão fazendo a manutenção). Para isentar mais de um endereço IP no mesmo comando, use a opção várias vezes.

>[!NOTE]
>
>Usar `--ip=<ip address>` com `magento maintenance:disable` O salva a lista de IPs para uso posterior. Para limpar a lista de IPs isentos, use `magento maintenance:enable --ip=none` ou consulte [Manter a lista de endereços IP isentos](#maintain-the-list-of-exempt-ip-addresses).

A variável `bin/magento maintenance:status` exibe o status do modo de manutenção.

Por exemplo, para ativar o modo de manutenção sem isenções de endereço IP:

```bash
bin/magento maintenance:enable
```

Para ativar o modo de manutenção para todos os clientes, exceto 192.0.2.10 e 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Depois de colocar a aplicação no modo de manutenção, você deve interromper todos os processos do consumidor da fila de mensagens.
Uma maneira de encontrar esses processos é executar o `ps -ef | grep queue:consumers:start` e execute o `kill <process_id>` comando para cada consumidor. Em um ambiente com vários nós, repita essa tarefa em cada nó.

## Manter a lista de endereços IP isentos

Para manter a lista de endereços IP isentos, você pode usar o `[--ip=<ip list>]` nos comandos anteriores ou você pode usar o seguinte:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

A variável `<ip address> .. <ip address>` A sintaxe é uma lista opcional delimitada por espaços de endereços IP para isentar.

A variável `--none` A opção limpa a lista.

## Configurações de várias lojas

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Se quiser configurar vários armazenamentos, cada um com um layout diferente e conteúdo localizado, passe a `$_GET['skin']` ao processador pretendido.

No exemplo a seguir, estamos usando uma variável `503` arquivo de modelo de erro do tipo, que requer conteúdo localizado.

O construtor do `Error_Processor` classe aceita um `skin` Parâmetro GET para alterar o layout:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Isso também pode ser adicionado a uma regra de regravação no `.htaccess` arquivo que anexa um `skin` para o URL.

### $_GET[&#39;skin&#39;] parâmetro

Para usar o `skin` parâmetro:

1. Verifique se `.maintenance.flag` existe.
1. Observe o endereço do host, que se refere ao `HTTP_HOST`ou qualquer outra variável, como variáveis ENV.
1. Verifique se `skin` O parâmetro existe.
1. Defina o parâmetro usando as regras de regravação abaixo.

   Estes são alguns exemplos de regras de regravação:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copie os seguintes arquivos:

   * `pub/errors/default/503.phtml` para `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` para `pub/errors/sub/styles.css`

1. Edite esses arquivos para fornecer conteúdo localizado no `503.phtml` estilo de arquivo e personalizado no `styles.css` arquivo.

   Certifique-se de que os caminhos apontem para a `errors` diretório. O nome do diretório deve corresponder ao parâmetro de URL indicado no `RewriteRule`. No exemplo anterior, a variável `sub` que é especificado como um parâmetro na variável `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>A variável [nginx](../../configuration/multi-sites/ms-nginx.md) deve ser adicionada para configurações de várias lojas.
