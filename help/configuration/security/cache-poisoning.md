---
title: Evitar envenenamento de cache
description: Saiba como evitar o envenenamento do cache da página na sua loja do Commerce.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Evitar envenenamento de cache

Este tópico discute como evitar o envenenamento de cache se você usa o servidor Web do Microsoft Internet Information Server (IIS). _Intoxicação de cache_ é um método de alterar o conteúdo do cache para incluir páginas diferentes do mesmo site. Por exemplo, é possível inserir uma página de erro HTTP 404 (Não encontrado) no lugar de alguma página benigna (por exemplo, a página inicial da vitrine), que pode levar a uma possível negação de serviço (DoS). Os URLs de página maliciosos são armazenados em cache por Verniz ou Redis, daí o nome _intoxicação de cache de página_.

Esses tipos de ataques podem ser difíceis de detectar porque não resultam em erros nos logs do servidor da Web.

Essa solução se aplica às seguintes versões do Commerce:

- 2.0.10 e posterior
- 2.1.2 e posterior

>[!INFO]
>
>Este tópico destina-se a administradores experientes do IIS.

## Descrição

O problema ocorre se as regravações de URL estiverem ativadas no servidor IIS e qualquer um dos seguintes cabeçalhos HTTP for alterado antes que a solicitação chegue ao serviço de cache Vernish ou Redis:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Se esses cabeçalhos forem alterados, o URL e o conteúdo resultantes serão armazenados em cache, resultando em possíveis vulnerabilidades.

## Solução

Fornecemos a opção de remover os valores de todos os cabeçalhos anteriores com base na configuração do servidor IIS para `Enable_IIS_Rewrites`.

- Se `Enable_IIS_Rewrites` está definida como `0`, os valores dos cabeçalhos são removidos.
- Se `Enable_IIS_Rewrites` está definida como `1`, os valores dos cabeçalhos são deixados intactos.

>[!WARNING]
>
>Se você definir `Enable_IIS_Rewrites` para `1`, não permita que os valores dos cabeçalhos anteriores sejam alterados antes que a solicitação chegue ao servidor Web do IIS.
