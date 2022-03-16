---
title: Otimização de desempenho
description: Saiba tudo sobre a otimização de desempenho e as etapas a serem seguidas para analisar o desempenho de sua implementação do Adobe Commerce.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Otimização de desempenho

O desempenho é um grande tópico. Quando os usuários experimentam um site lento ou sem resposta, isso afeta a conversão. Recomendamos seguir essas etapas para otimizar o desempenho do Adobe Commerce na implementação da infraestrutura de nuvem:

- Avalie o problema
- Medir desempenho
- Identificar parte do sistema essencial para melhorar o desempenho
- Modificar parte do sistema para remover o gargalo
- Meça o desempenho após a modificação
- Se melhor, adote-a ou reverta

## Problemas típicos de desempenho

O impacto de uma experiência lenta é geralmente definido por dois indicadores, e cada fator pode ser causado por toneladas de motivos.

O TTFB (High-time-to-first-byte) geralmente é considerado um indicador que define a velocidade de resposta do servidor. O tempo não apenas provém da execução do código-fonte para lidar com a solicitação, mas também pode ser afetado pelos seguintes fatores:

- Pesquisa de DNS
- Consultas lentas da camada de banco de dados
- Tempo de CPU de cada camada de aplicativo
- Limitação de memória
- A espera de E/S pode afetar a partir da leitura e gravação de arquivos, conectar o serviço via soquete
- Configurações de software (nginx, PHP, MySQL, Redis, Varnish)
- Largura de banda de rede
- Armazenamento em cache incorreto
- Código inválido
- Abordagem de integração incorreta
- Dependência de resposta lenta de serviço de terceiros
- Arquitetura sem escalabilidade

Os recursos de carregamento lento geralmente são considerados como um indicador que define o recurso estático (CSS, JavaScript, imagens, vídeos, resposta de chamada do Ajax de terceiros).

A Adobe Commerce pode ser dimensionada com sua empresa através de seus recursos:

![Diagrama que mostra os recursos escaláveis do Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Há também fatores fundamentais que determinam a escala no comércio, o que também afeta o desempenho geral.

- Catálogo de produtos complexo e grande
- Grande número de administradores
- Lojas globais
- Tráfego de alta variável
- Expandir pontos de contato
- Transações de alto volume

Para arquiteturas em camadas e em cache criadas para escala, você pode usar esse gráfico como referência.

![Diagrama que mostra como usar a API GraphQL da Adobe Commerce em uma arquitetura armazenável em cache](../../../assets/playbooks/cacheable-architecture.svg)
