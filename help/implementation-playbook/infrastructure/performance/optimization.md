---
title: Otimização do desempenho
description: Saiba tudo sobre a otimização de desempenho e as etapas a serem seguidas para analisar o desempenho da implementação do Adobe Commerce.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Otimização do desempenho

Desempenho é um grande tópico. Quando os usuários experimentam um site lento ou sem resposta, isso afeta a conversão. Recomendamos seguir estas etapas para otimizar o desempenho da sua implementação do Adobe Commerce na infraestrutura em nuvem:

- Avaliar o problema
- Medir desempenho
- Identificar parte do sistema essencial para a melhoria do desempenho
- Modificar parte do sistema para remover o afunilamento
- Medir o desempenho após a modificação
- Se for melhor, adote-a ou reverta

## Problemas de desempenho típicos

O impacto de uma experiência lenta é geralmente definido por dois indicadores, e cada fator pode ser causado por toneladas de motivos.

O TTFB (time-to-first-byte) alto geralmente é considerado um indicador que define a velocidade de resposta do servidor. O tempo não é proveniente apenas da execução do código-fonte para lidar com a solicitação, mas também pode ser afetado pelos seguintes fatores:

- Pesquisa de DNS
- Consultas lentas da camada do banco de dados
- Tempo de CPU de cada camada de aplicativo
- Limitação de memória
- A espera de I/O pode afetar a leitura e gravação de arquivos e o serviço de conexão via soquete
- Configurações de software (nginx, PHP, MySQL, Redis, Varnish)
- Largura de banda de rede
- Armazenamento em cache incorreto
- Código incorreto
- Abordagem de integração incorreta
- Dependência de resposta lenta de serviço de terceiros
- Arquitetura sem escalabilidade

Os recursos de carregamento lento são geralmente considerados como um indicador que define o recurso estático (CSS, JavaScript, imagens, vídeos, resposta de chamada Ajax de terceiros).

A Adobe Commerce pode acompanhar sua empresa por meio de seus recursos:

![Diagrama que mostra os recursos escalonáveis do Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Há também fatores-chave que impulsionam a escala no comércio, que também afetam o desempenho geral.

- Catálogo de produtos complexo e grande
- Grande número de administradores
- Lojas de discos globais
- Tráfego de alta variável
- Expandir pontos de contato
- Transações de alto volume

Para arquiteturas em camadas e em cache criadas para escala, é possível usar esse gráfico como uma referência.

![Diagrama que mostra como usar a API do GraphQL do Adobe Commerce em uma arquitetura que pode ser armazenada em cache](../../../assets/playbooks/cacheable-architecture.svg)
