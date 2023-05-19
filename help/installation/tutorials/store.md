---
title: Configurar o armazenamento
description: Siga estas etapas para configurar sua Adobe Commerce ou Magento Open Source store.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Configurar o armazenamento

Antes de executar este comando, faça o seguinte *ou* você deve [instalar o aplicativo](../advanced.md):

* [Criar ou atualizar a configuração de implantação](deployment.md)
* [Criar o esquema de banco de dados](database.md)

## Instalação segura

{{$include /help/_includes/secure-install.md}}

## Configurar o armazenamento

Uso do comando:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Onde a tabela a seguir define parâmetros e valores:

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--base-url` | URL base a ser usado para acessar seu administrador e vitrine em qualquer um dos seguintes formatos:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** O regime (`http://` ou `https://`) e uma barra à direita são necessários. `<your install dir>` é o caminho relativo ao docroot no qual instalar o aplicativo. Dependendo de como você configura o servidor Web e os hosts virtuais, o caminho pode ser magento2 ou pode estar em branco.<br><br>Para acessar o aplicativo no host local, você pode usar `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` que representa um URL de base definido por uma configuração de host virtual ou por um ambiente de virtualização como o Docker. Por exemplo, se você configurar um host virtual com o nome de host commerce.example.com, poderá instalar o aplicativo com `--base-url={{base_url}}` e acesse o Administrador com um URL como `http://commerce.example.com/admin`. | Não |
| `--language` | Código de idioma a ser usado no Admin e na loja.<br><br>(Se ainda não tiver feito isso, você poderá exibir a lista de códigos de idioma inserindo `magento info:language:list` do `bin` diretório.) | Não |
| `--currency` | Moeda padrão a ser usada na loja. <br><br>(Se ainda não tiver feito isso, você poderá exibir a lista de moedas informando `magento info:currency:list` do `bin` diretório.) | Não |
| `--timezone` | Fuso horário padrão a ser usado na administração e na loja. (Se ainda não tiver feito isso, você poderá exibir a lista de fusos horários inserindo `magento info:timezone:list` do `bin` diretório.) | Não |
| `--use-rewrites` | `1` significa que você usa regravações do servidor da web para links gerados na loja e no Administrador.<br><br>`0` desativa o uso de regravações do servidor web. Este é o padrão. | Não |
| `--use-secure` | `1` permite o uso da SSL (Secure Sockets Layer) em URLs de vitrine. Antes de selecionar essa opção, verifique se o servidor Web oferece suporte para SSL.<br><br>`0` desativa o uso do SSL. Nesse caso, presume-se que todas as outras opções de URL seguro também sejam 0. Este é o padrão. | Não |
| `--base-url-secure` | URL base seguro a ser usado para acessar seu administrador e vitrine eletrônica no seguinte formato: `http[s]://<host or ip>/<your install dir>/` | Não |
| `--use-secure-admin` | `1` significa que você usa SSL para acessar o Administrador. Antes de selecionar essa opção, verifique se o servidor Web oferece suporte para SSL.<br><br>`0` significa que você não usa SSL com o Administrador. Este é o padrão. | Não |
| `--admin-use-security-key` | `1` faz com que o aplicativo use um valor de chave gerado aleatoriamente para acessar páginas no Admin e em formulários. Esses valores principais ajudam a impedir ataques de falsificação de script entre sites. Este é o padrão.<br/><br/>`0` desativa o uso da chave. | Não |
| `--magento-init-params` | Adicione a qualquer comando para personalizar parâmetros de inicialização de aplicativos<br/><br/>Por exemplo: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Não |
