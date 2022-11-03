---
title: Otimizar imagens para um site mais responsivo
description: Aprenda as etapas para otimizar imagens e use a otimização de imagens Fastly para otimizar o tempo de resposta nos sites do Adobe Commerce.
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Otimizar imagens para um site mais responsivo

Para o Adobe Commerce em implantações de infraestrutura em nuvem, melhore o tempo de resposta do site otimizando imagens antes de carregá-las. Em seguida, use a otimização de imagem Fastly para acelerar a entrega de imagens e simplificar a manutenção dos conjuntos de fonte de imagem.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

Adobe Commerce na infraestrutura de nuvem


## Otimizar e compactar imagens

Antes de carregar imagens em seus sites do Commerce, otimize-as e compacte-as para equilibrar o desempenho com a qualidade de visualização. Isso ajuda a aumentar o espaço e reduzir o tempo de carregamento da página.

- O formato PNG fornece imagens de menor tamanho para imagens com grandes áreas de cor sólida.

- O formato JPEG fornece imagens de menor tamanho para todos os outros tipos de imagens. Use a compactação mais alta (sem degradação perceptível). Isso é geralmente de 60 a 80 por cento.

## Ativar e configurar a otimização de imagens com rapidez

Depois de configurar o Serviço rápido para o projeto do Adobe Commerce Cloud, consulte [Otimização rápida de imagens](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) para obter instruções sobre como ativar e configurar a otimização de imagem.

## Informações adicionais

- [Configurar rapidamente](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Imagens mal otimizadas podem levar a problemas de desempenho](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
