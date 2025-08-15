---
title: Otimize imagens para um site mais responsivo
description: Saiba mais sobre as etapas para otimizar imagens e usar a otimização de imagem do Fastly para otimizar o tempo de resposta em seus sites do Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

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

Depois de configurar o serviço Fastly para o seu projeto na Adobe Commerce Cloud, consulte [Fastly image otimization](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization) para obter instruções sobre como habilitar e configurar a otimização de imagens.

## Informações adicionais

- [Configurar Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)
- [Imagens mal otimizadas podem causar problemas de desempenho](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
