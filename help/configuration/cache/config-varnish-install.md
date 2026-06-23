---
title: Instalar verniz
description: Saiba mais sobre os requisitos de instalação do Varnish para o armazenamento em cache do Adobe Commerce. Descubra os recursos de instalação e as orientações de configuração.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 0%

---

# Instalar verniz

{{varnish-config-cloud}}

A instalação do verniz está fora do escopo deste guia. Este tópico presume uma versão compatível do Varnish e um servidor de origem do Adobe Commerce em execução atrás do Varnish. Os exemplos neste guia usam nginx como o servidor Web de origem.

- [guia de instalação](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guias de instalação em verniz](https://www.varnish-cache.org/docs)
- [Como instalar verniz (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Se você pretende instalar módulos Varnish (vmods), como modo saint, você deve instalar o Varnish compilando o código, em vez de instalar a partir de um pacote. Consulte [Modo Saint](config-varnish-advanced.md#saint-mode) para obter mais detalhes.

## Confirmar a versão em verniz

Abra um terminal e insira o seguinte comando para exibir a versão de Verniz:

```shell
varnishd -V
```

Verifique se o [Adobe Commerce oferece suporte](../../installation/system-requirements.md) à versão instalada do Verniz antes de continuar. Se você estiver executando uma versão sem suporte, será necessário atualizar para uma versão com suporte. Consulte a documentação de instalação do Vernish para obter mais informações.
