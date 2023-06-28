---
title: Benchmarks de desempenho
description: Analise os resultados do benchmark de desempenho para implementações do Adobe Commerce hospedadas na infraestrutura de nuvem do Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '594'
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

## Métricas principais de desempenho

A figura a seguir mostra a configuração da loja do Commerce para o benchmark de desempenho e as métricas principais de desempenho dos resultados do teste.

![JMeter de benchmark de desempenho e infraestrutura de produção](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Com base em critérios de teste que simulam uma organização B2C corporativa, o sistema pode lidar com o tráfego solicitado e os números de pedido durante os horários de pico, em um fluxo de carga padrão.

### Destaques do desempenho

- **Pedidos**— processou 3.481 pedidos por minuto, mantendo tempos de resposta inferiores a 2 segundos para o 99º percentil (99% das solicitações foram atendidas com um tempo de resposta inferior a 2 segundos).
- **Exibições de página**— manipulava mais de 2 milhões de exibições de página por hora, mantendo tempos de resposta inferiores a 2 segundos para o 99º percentil.
- **SKUs eficazes**—O perfil do cliente incluía 242 milhões de variações de preços diferentes (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKUs</a>) para 250.000 produtos.
- **solicitações do GraphQL**— sistema dimensionado para 10.500 solicitações GraphQL sem cache por minuto, mantendo tempos de resposta inferiores a 2 segundos para o 99º percentil.
- **Usuários administradores simultâneos**— sistema dimensionado para suportar 500 usuários administradores simultâneos, mantendo tempos de resposta inferiores a 2 segundos para o 99º percentil.

## Ambiente de teste

Os resultados do teste de desempenho foram obtidos com testes em uma instância do Adobe Commerce 2.4.5 implantada em um ambiente de nuvem Pro com arquitetura escalonada. Adobe Commerce A instância também tinha os módulos B2B, Inventory management e Adobe Stock Integration instalados, configurados e ativados.

Os dados de teste de desempenho do perfil de teste foram gerados usando o <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Kit de ferramentas de desempenho</a>.

As avaliações de desempenho são baseadas em atividades simuladas de lojas cotidianas para clientes e usuários empresariais. Os valores refletem uma taxa de transferência próxima do máximo para cada caso, mas não refletem modelos de negócios exclusivos, como vendas privadas ou vendas rápidas.

- **Loja LUMA**
   - 3000 usuários simultâneos na loja
   - Definir para taxa de acertos do cache CDN de 30%

     O uso efetivo da camada de cache aumenta o número de exibições de página por hora.

- **API do GraphQL**
   - 250 threads simultâneas
   - Defina como 0% da taxa de acertos do cache do CDN

     Os tempos de resposta melhoram significativamente com uma camada de cache na frente do GraphQL.

- **Web do administrador**
   - 500 usuários simultâneos
   - Defina como 0% da taxa de acertos do cache do CDN

## Especificações do ambiente de teste

O teste de carga foi concluído usando perfis de carga JMeter executados na instância do Adobe Commerce. Três nós da Web e três nós de serviço foram usados durante o teste. A imagem a seguir detalha o ponto de entrada do JMeter e a infraestrutura de produção.

![JMeter de benchmark de desempenho e infraestrutura de produção](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Aplicativo

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> implantado em infraestrutura em nuvem com arquitetura Pro.

### Infraestrutura

Para o benchmark de desempenho, o Adobe Commerce 2.4.5 foi implantado em um [infraestrutura dimensionável](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) com a seguinte capacidade:

- **Especificações do nó da Web**
   - vCPU 216 (72 x 3 nós)
   - Memória 432 GiB (144 x 3 nós)
   - Largura de banda de rede de 768 Gbps (256 x 3 nós)
   - Largura de banda EBS de 57.000 Mbps (19.000 x 3 nós)
   - Armazenamento provisionado de 100 GB

- **Especificações do nó de serviço**
   - vCPU 192 (64 x 3 nós)
   - Memória 768 GiB (256 x 3 nós)
   - Largura de banda de rede de 60 Gbps (20 x 3 nós)
   - Largura de banda EBS de 40.800 Mbps (13.600 x 3 nós)
   - Armazenamento provisionado de 1.100 GB
