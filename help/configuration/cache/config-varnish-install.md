---
title: Instalar verniz
description: Consulte os conselhos sobre como instalar o Verniz.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Instalar verniz

A instalação do software Vernish está fora do escopo deste guia. Para obter mais informações sobre a instalação de Verniz, consulte:

- [guia de instalação](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guias de instalação em verniz](https://www.varnish-cache.org/docs)
- [Como instalar o verniz (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

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

Verifique se o [Adobe Commerce oferece suporte](../../installation/system-requirements.md) à versão instalada do Verniz antes de continuar. Se você estiver executando uma versão sem suporte, será necessário atualizar para uma versão com suporte. Consulte a documentação de instalação do Vernish para obter mais informações.
