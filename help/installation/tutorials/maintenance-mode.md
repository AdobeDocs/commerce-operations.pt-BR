---
title: Ativar ou desativar o modo de manutenção
description: Siga estas etapas para personalizar o que os clientes veem quando a implantação do Adobe Commerce ou Magento Open Source está inativa para manutenção.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Ativar ou desativar o modo de manutenção

O guia a seguir se refere a uma página de modo de manutenção padrão. Se precisar usar uma página de manutenção personalizada, consulte [Criar a página de manutenção personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md) tópico.

Adobe Commerce e Magento Open Source use [modo de manutenção](../../configuration/bootstrap/application-modes.md#maintenance-mode) para desativar o bootstrapping. Desativar o bootstrapping é útil enquanto você mantém, atualiza ou reconfigura seu site.

O aplicativo detecta o modo de manutenção da seguinte maneira:

* If `var/.maintenance.flag` não existe, o modo de manutenção está desativado e o aplicativo funciona normalmente.
* Caso contrário, o modo de manutenção estará ativado, a menos que `var/.maintenance.ip` existe.

   `var/.maintenance.ip` pode conter uma lista de endereços IP. Se um ponto de entrada for acessado usando HTTP e o endereço IP do cliente corresponder a uma das entradas nessa lista, o modo de manutenção estará desativado.

## Instalar o aplicativo

Antes de usar este comando para ativar ou desativar o modo de manutenção, é necessário [instale o aplicativo](../advanced.md).

## Ativar ou desativar o modo de manutenção

Use o `magento maintenance` comando CLI para ativar ou desativar o modo de manutenção.

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

O `--ip=<ip address>` é um endereço IP para isentar do modo de manutenção (por exemplo, desenvolvedores que fazem a manutenção). Para isentar mais de um endereço IP no mesmo comando, use a opção várias vezes.

>[!NOTE]
>
>Usando `--ip=<ip address>` com `magento maintenance:disable` salva a lista de IPs para uso posterior. Para limpar a lista de IPs isentos, use `magento maintenance:enable --ip=none` ou veja [Manter a lista de endereços IP isentos](#maintain-the-list-of-exempt-ip-addresses).

O `bin/magento maintenance:status` exibe o status do modo de manutenção.

Por exemplo, para ativar o modo de manutenção sem isenções de endereço IP:

```bash
bin/magento maintenance:enable
```

Para ativar o modo de manutenção para todos os clientes, exceto 192.0.2.10 e 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Depois de colocar o aplicativo no modo de manutenção, você deve parar todos os processos do consumidor da fila de mensagens.
Uma maneira de encontrar esses processos é executar o `ps -ef | grep queue:consumers:start` e, em seguida, execute o `kill <process_id>` para cada consumidor. Em um ambiente de vários nós, repita essa tarefa em cada nó.

## Manter a lista de endereços IP isentos

Para manter a lista de endereços IP isentos, é possível usar a variável `[--ip=<ip list>]` nos comandos anteriores ou você pode usar o seguinte:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

O `<ip address> .. <ip address>` sintaxe é uma lista opcional de endereços IP delimitada por espaços que deve ser isentada.

O `--none` limpa a lista.

## Configurações de várias lojas

Para configurar várias lojas, cada uma com um layout diferente e conteúdo localizado, crie uma capa para cada uma e coloque-a em `pub/errors/{name}` em que `{name}` é o código de armazenamento. Para distinguir entre armazenamentos e sites com a mesma instância, use `pub/errors/{type}-{name}` em que `{type}` é `store` ou `website` e corresponde ao `MAGE_RUN_TYPE` na configuração do servidor.

Outra opção é passar a variável `$_GET['skin']` para o processador pretendido. Esse método requer uma configuração específica no servidor.

No exemplo a seguir, estamos usando um `503` digite o arquivo do modelo de erro, que requer conteúdo localizado.

O construtor do `Error_Processor` classe aceita `skin` GET para alterar o layout:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Isso também pode ser adicionado a uma regra de regravação no `.htaccess` arquivo que anexa um `skin` para o URL.

### $_GET[&quot;pele&quot;] parâmetro

Para usar o `skin` parâmetro:

1. Verifique se a variável `.maintenance.flag` existe.
1. Observe o endereço do host, que se refere à variável `HTTP_HOST`ou qualquer outra variável, como variáveis ENV.
1. Verifique se a variável `skin` existe.
1. Defina o parâmetro usando as regras de regravação abaixo.

   Estes são alguns exemplos de regras de regravação:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copie os seguintes arquivos:

   * `pub/errors/default/503.phtml` para `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` para `pub/errors/sub/styles.css`

1. Edite esses arquivos para fornecer conteúdo localizado na `503.phtml` arquivo e estilo personalizado na `styles.css` arquivo.

   Assegure-se de que seus caminhos apontem para a `errors` diretório. O nome do diretório deve corresponder ao parâmetro de URL indicado na variável `RewriteRule`. No exemplo anterior, a variável `sub` é usado, que é especificado como um parâmetro na função `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>O [nginx](../../configuration/multi-sites/ms-nginx.md) deve ser adicionada para configurações de várias lojas.
