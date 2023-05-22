---
title: Instalar verniz
description: Consulte os conselhos sobre como instalar o Verniz.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Instalar verniz

A instalação do software Vernish está fora do escopo deste guia. Para obter mais informações sobre a instalação de Verniz, consulte:

- [guia de instalação](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guias de instalação em verniz](https://www.varnish-cache.org/docs)
- [Como instalar verniz (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Este tópico foi escrito para Verniz no CentOS e Apache 2.4. Se você estiver configurando o Verniz em um ambiente diferente, alguns comandos provavelmente serão diferentes. Consulte a documentação anterior para obter mais informações.
>
>Se você pretende instalar módulos Varnish (vmods), como modo saint, você deve instalar o Varnish compilando o código, em vez de instalar a partir de um pacote. Consulte [Modo Saint](config-varnish-advanced.md#saint-mode) para obter mais detalhes.

## Confirmar a versão em verniz

Abra um terminal e insira o seguinte comando para exibir a versão de Verniz:

```bash
varnishd -V
```

A seguir, há uma amostra:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Verifique se a versão é a 6.x antes de continuar. Se você estiver executando uma versão anterior à 6.x, será necessário atualizar para uma versão compatível. Consulte a documentação de instalação do Vernish para obter mais informações.
