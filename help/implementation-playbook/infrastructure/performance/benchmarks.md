---
title: Referências de desempenho
description: Analise os resultados do benchmark de desempenho para implementações Adobe Commerce hospedadas na infraestrutura de nuvem de Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: 09a42dc68836b34eab2c9d90879b897729cd1b09
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Resumo do benchmark

Os resultados do benchmark de desempenho do Adobe Commerce 2.4.5 refletem o desempenho medido em uma instância do Adobe Commerce implantada com a seguinte infraestrutura e componentes adicionais.
- [Ambiente de nuvem Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) com [arquitetura dimensionada](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

Não há personalizações adicionais.

As informações a seguir resumem os resultados do benchmark e fornecem informações sobre o ambiente e os dados usados durante os testes.

## Principais métricas de desempenho

A figura a seguir mostra a configuração da loja de Comércio para o benchmark de desempenho e as métricas principais de desempenho dos resultados do teste.

![Benchmark de desempenho JMeter e infraestrutura de produção](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Com base em critérios de teste que imitam uma organização B2C corporativa, o sistema pode manipular o tráfego solicitado e os números de pedido durante os horários de pico, em um fluxo de carga padrão.

### Destaques de desempenho

- **Pedidos**—Processados 3.481 pedidos por minuto, mantendo os tempos de resposta inferiores a 2 segundos para o 99º percentil (99% dos pedidos foram atendidos com um tempo de resposta inferior a 2 segundos).
- **Exibições de página**—Mantido por mais de 2 milhões de visualizações de página por hora, mantendo os tempos de resposta de menos de 2 segundos para o 99º percentil.
- **SKUs eficazes**—O perfil do cliente incluía 242 milhões de variações de preço diferentes (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKUs</a>) para 250.000 produtos.
- **Solicitações do GraphQL**—Sistema dimensionado para 10.500 solicitações não armazenadas em cache do GraphQL por minuto, mantendo tempos de resposta de menos de 2 segundos para o 99º percentil.
- **Usuários administradores simultâneos**—O sistema foi dimensionado para suportar 500 usuários administradores simultâneos, mantendo os tempos de resposta de menos de 2 segundos para o 99º percentil.

## Ambiente de teste

Os resultados de benchmark de desempenho foram obtidos por meio de testes em uma instância do Adobe Commerce 2.4.5 implantada em um ambiente Pro Cloud com arquitetura dimensionada. A instância também tinha os módulos Adobe Commerce B2B, Inventory management e Adobe Stock Integration instalados, configurados e ativados.

Os dados de teste de desempenho do perfil de teste foram gerados usando o <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Kit de ferramentas de desempenho</a>.

As medidas de desempenho são baseadas em atividades de loja diárias simuladas para clientes e usuários comerciais. Os valores refletem uma taxa de transferência próxima do máximo para cada caso, mas não refletem modelos de negócios exclusivos, como vendas privadas ou vendas flash.

- **Loja LUMA**
   - 3000 usuários simultâneos na loja
   - Defina para taxa de ocorrência de cache de 30% CDN

      O uso eficaz da camada de cache aumenta o número de exibições de página por hora.

- **API do GraphQL**
   - 250 threads simultâneos
   - Defina como 0% da taxa de ocorrência do cache CDN

      Os tempos de resposta melhoram significativamente com uma camada de cache na frente do GraphQL.

- **Web de administração**
   - 500 usuários simultâneos
   - Defina como 0% da taxa de ocorrência do cache CDN

## Especificações do ambiente de teste

O teste de carga foi concluído usando perfis de carga JMeter executados na instância do Adobe Commerce. Três nós da Web e três nós de serviço foram usados durante o teste. A imagem a seguir detalha o ponto de entrada da infraestrutura JMeter e Produção.

![Benchmark de desempenho JMeter e infraestrutura de produção](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Aplicativo

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> implantado na infraestrutura em nuvem com arquitetura Pro.

### Infraestrutura

Para o benchmark de desempenho, o Adobe Commerce 2.4.5 foi implantado em um [infraestrutura dimensionável](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) com a seguinte capacidade:

- **Especificações do nó da Web**
   - vCPU 216 (72 x 3 nós)
   - Memória 432 GiB (144 x 3 nós)
   - Largura de banda de rede 768 Gbps (256 x 3 nós)
   - Armazenamento provisionado 100 GB

- **Especificações do nó de serviço**
   - vCPU 192 (64 x 3 nós)
   - Memória 768 GiB (256 x 3 nós)
   - Largura de banda de rede 60 Gbps (20 x 3 nós)
   - Largura de banda EBS 40800 Mbps (13600 x 3 nós)
   - Armazenamento provisionado 1100 GB
