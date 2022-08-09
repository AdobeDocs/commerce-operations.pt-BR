---
title: Instalar o Varnish
description: Consulte os conselhos sobre como instalar o Varnish.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Instalar o Varnish

A instalação do software Varnish está além do escopo deste guia. Para obter mais informações sobre como instalar o Varnish, consulte:

- [guia de instalação](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guias de instalação da Varnish](https://www.varnish-cache.org/docs)
- [Como instalar o Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Este tópico foi escrito para Varnish no CentOS e no Apache 2.4. Se você estiver configurando Varnish em um ambiente diferente, alguns comandos provavelmente serão diferentes. Consulte a documentação anterior para obter mais informações.
>
>Se você pretende instalar módulos Varnish (vmods), como o modo saint, você deve instalar o Varnish ao compilar o código, em vez de instalar a partir de um pacote. Consulte [Modo Saint](config-varnish-advanced.md#saint-mode) para obter mais detalhes.

## Confirme sua versão em Varnish

Abra um terminal e insira o seguinte comando para exibir a versão de Varnish:

```bash
varnishd -V
```

Uma amostra:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Certifique-se de que a versão seja a 6.x antes de continuar. Se você estiver executando uma versão inferior a 6.x, será necessário atualizar para uma versão compatível. Consulte a documentação de instalação da Varnish para obter mais informações.
