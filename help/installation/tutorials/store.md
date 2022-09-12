---
title: Configurar a loja
description: Siga estas etapas para configurar sua Adobe Commerce ou Magento Open Source Store.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Configurar a loja

Antes de executar esse comando, faça o seguinte *ou* você deve [instale o aplicativo](../advanced.md):

* [Criar ou atualizar a configuração de implantação](deployment.md)
* [Criar o esquema do banco de dados](database.md)

## Instalação segura

{{$include /help/_includes/secure-install.md}}

## Configurar a loja

Uso do comando:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Onde a tabela a seguir define parâmetros e valores:

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--base-url` | URL base a ser usado para acessar o Administrador e a loja em qualquer um dos seguintes formatos:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Observação:** O regime (`http://` ou `https://`) e uma barra à direita são necessárias. `<your install dir>` é o caminho relativo ao docroot no qual o aplicativo será instalado. Dependendo de como você configurou seu servidor da Web e hosts virtuais, o caminho pode ser o magento2 ou pode estar em branco.<br><br>Para acessar o aplicativo no host local, você pode usar `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` que representa um URL básico definido por uma configuração de host virtual ou por um ambiente de virtualização como o Docker. Por exemplo, se você configurar um host virtual com o nome de host commerce.example.com, você poderá instalar o aplicativo com `--base-url={{base_url}}` e acessar o Administrador com um URL como `http://commerce.example.com/admin`. | Não |
| `--language` | Código de idioma para usar na loja e na Administração.<br><br>(Se ainda não tiver feito isso, você poderá exibir a lista de códigos de idioma digitando `magento info:language:list` do `bin` diretory.) | Não |
| `--currency` | Moeda padrão a ser usada na loja. <br><br>(Se ainda não tiver feito isso, poderá exibir a lista de moedas inserindo `magento info:currency:list` do `bin` diretory.) | Não |
| `--timezone` | Fuso horário padrão para usar em Admin e loja. (Se ainda não tiver feito isso, é possível exibir a lista de fusos horários inserindo `magento info:timezone:list` do `bin` diretory.) | Não |
| `--use-rewrites` | `1` significa que você usa regravações do servidor da Web para links gerados na loja e no Administrador.<br><br>`0` desativa o uso de regravações do servidor da web. Este é o padrão. | Não |
| `--use-secure` | `1` permite o uso de SSL (Secure Sockets Layer) em URLs de loja. Certifique-se de que o servidor da Web seja compatível com SSL antes de selecionar essa opção.<br><br>`0` desativa o uso de SSL. Nesse caso, todas as outras opções de URL seguro também são consideradas 0. Este é o padrão. | Não |
| `--base-url-secure` | URL de base segura a ser usado para acessar o Administrador e a loja no seguinte formato: `http[s]://<host or ip>/<your install dir>/` | Não |
| `--use-secure-admin` | `1` significa usar SSL para acessar o Administrador. Certifique-se de que o servidor da Web seja compatível com SSL antes de selecionar essa opção.<br><br>`0` significa que você não usa SSL com o Administrador. Este é o padrão. | Não |
| `--admin-use-security-key` | `1` faz com que o aplicativo use um valor de chave gerado aleatoriamente para acessar páginas no Administrador e nos formulários. Esses valores-chave ajudam a impedir ataques de falsificação de scripts entre sites. Este é o padrão.<br/><br/>`0` desativa o uso da chave. | Não |
| `--magento-init-params` | Adicionar a qualquer comando para personalizar os parâmetros de inicialização do aplicativo<br/><br/>Por exemplo: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Não |
