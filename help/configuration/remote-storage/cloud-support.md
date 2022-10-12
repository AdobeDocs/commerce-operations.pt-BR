---
title: Armazenamento remoto para o Commerce na infraestrutura em nuvem
description: Consulte as orientações sobre como configurar o armazenamento remoto para o Adobe Commerce na infraestrutura em nuvem.
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Configurar o armazenamento remoto para o Commerce on Cloud Infrastructure

Se você optar por usar a solução de armazenamento remoto com um projeto Adobe Commerce em infraestrutura em nuvem, use o [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) orientações na _Rápido_ documentação para garantir que a Otimização de imagem rápida funcione com o AWS S3.

Esteja preparado com seu [Credenciais rápidas](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#cloud-fastly-creds). Em projetos Pro, use o SSH para se conectar ao seu servidor e obter as credenciais do Fastly da `/mnt/shared/fastly_tokens.txt` arquivo. Os ambientes de preparo e produção têm credenciais exclusivas. Você deve obter as credenciais para cada ambiente.

Continue configurando o armazenamento remoto para projetos em nuvem com as seguintes tarefas:

1. Configure um [Integração rápida de backend](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Criar lógica de VCL para [Autenticação AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Criar lógica de VCL para [solicitações de backend para o bucket do AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
