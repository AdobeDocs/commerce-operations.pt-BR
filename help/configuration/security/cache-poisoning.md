---
title: Evitar envenenamento de cache
description: Saiba como evitar o envenenamento do cache da página na sua loja da Commerce.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%
---
# Evitar envenenamento de cache

Este tópico discute como evitar o envenenamento de cache se você usa o servidor Web do Microsoft Internet Information Server (IIS). _Intoxicação de cache_ é um método de alterar o conteúdo do cache para incluir páginas diferentes do mesmo site. Por exemplo, é possível inserir uma página de erro HTTP 404 (Não encontrado) no lugar de alguma página benigna (por exemplo, a página inicial da vitrine), que pode levar a uma possível negação de serviço (DoS). As URLs de páginas mal-intencionadas são armazenadas em cache pelo Varnish ou Redis, daí o nome _envenenamento de cache de página_.

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

- Se `Enable_IIS_Rewrites` estiver definido como `0`, os valores dos cabeçalhos serão removidos.
- Se `Enable_IIS_Rewrites` estiver definido como `1`, os valores dos cabeçalhos serão deixados intactos.

>[!WARNING]
>
>Se você definir `Enable_IIS_Rewrites` como `1`, não deverá permitir que os valores dos cabeçalhos anteriores sejam alterados antes que a solicitação chegue ao servidor Web do IIS.
