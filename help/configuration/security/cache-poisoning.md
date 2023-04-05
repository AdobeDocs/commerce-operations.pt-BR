---
title: Evitar envenenamento do cache
description: Saiba como evitar envenenamento ao cache de página em sua loja do Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Evitar envenenamento do cache

Este tópico discute como evitar envenenamento por cache se você usar o servidor da Web do Microsoft Internet Information Server (IIS). _Envenenamento de cache_ é um método de alterar o conteúdo do cache para incluir páginas diferentes do mesmo site. Por exemplo, é possível inserir uma página de erro HTTP 404 (Not Found) no lugar de alguma página benigna (por exemplo, a página inicial da loja), que pode levar a uma possível negação de serviço (DoS). Os URLs de página mal-intencionados são armazenados em cache pelo Varnish ou Redis, portanto, o nome _envenenamento do cache de página_.

Esses tipos de ataques podem ser difíceis de detectar porque não resultam em erros nos logs do servidor da Web.

Essa solução se aplica às seguintes versões do Commerce:

- 2.0.10 e posterior
- 2.1.2 e posterior

>[!INFO]
>
>Este tópico destina-se a administradores experientes do IIS.

## Descrição

O problema resulta se as regravações de URL são ativadas no servidor IIS e qualquer um dos seguintes cabeçalhos HTTP é alterado antes que a solicitação atinja o serviço de armazenamento em cache Varnish ou Redis:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Se esses cabeçalhos forem alterados, o URL e o conteúdo resultantes serão armazenados em cache, resultando em possíveis vulnerabilidades.

## Solução

Fornecemos a opção de remover os valores de todos os cabeçalhos anteriores com base na configuração do servidor IIS para `Enable_IIS_Rewrites`.

- If `Enable_IIS_Rewrites` está definida como `0`, os valores dos cabeçalhos são removidos.
- If `Enable_IIS_Rewrites` está definida como `1`, os valores dos cabeçalhos permanecem intactos.

>[!WARNING]
>
>Se você definir `Enable_IIS_Rewrites` para `1`, você não deve permitir que os valores dos cabeçalhos anteriores sejam alterados antes que a solicitação chegue ao servidor da Web do IIS.
