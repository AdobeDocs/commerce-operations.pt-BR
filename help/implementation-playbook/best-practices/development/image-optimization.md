---
title: Otimize imagens para um site mais responsivo
description: Saiba mais sobre as etapas para otimizar imagens e usar a otimização de imagem do Fastly para otimizar o tempo de resposta em seus sites do Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# Otimize imagens para um site mais responsivo

Para o Adobe Commerce em implantações de infraestrutura em nuvem, melhore o tempo de resposta do site, otimizando as imagens antes de carregá-las. Em seguida, use a Otimização de imagem do Fastly para acelerar a entrega de imagens e simplificar a manutenção de conjuntos de fontes de imagem.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

Adobe Commerce na infraestrutura em nuvem


## Otimizar e compactar imagens

Antes de carregar imagens para seus sites do Commerce, otimize-as e compacte-as para equilibrar o desempenho com a qualidade de visualização. Isso ajuda a aumentar o espaço e reduzir o tempo de carregamento da página.

- O formato PNG fornece imagens de tamanho menor para imagens com grandes áreas de cor sólida.

- O formato JPEG fornece imagens de tamanho menor para todos os outros tipos de imagem. Use a compactação mais alta (sem degradação visível). Isso geralmente é de 60 a 80 por cento.

## Ativar e configurar a otimização de imagem do Fastly

Depois de configurar o serviço Fastly para o seu projeto na Adobe Commerce Cloud, consulte [Fastly image otimization](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly-image-optimization) para obter instruções sobre como habilitar e configurar a otimização de imagens.

## Informações adicionais

- [Configurar o Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)
- [Imagens mal otimizadas podem causar problemas de desempenho](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)
