---
title: Arquitetura de referência
description: Analise diagramas da arquitetura de referência recomendada para implantações do Adobe Commerce e do Magento Open Source.
source-git-commit: 065c56f20ba5b1eef8c331c5c2f5649902f1442b
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# Arquitetura de referência

Este tópico descreve uma configuração genérica recomendada para instâncias do Adobe Commerce e do Magento Open Source usando servidores simples hospedados fisicamente em um data center (não virtualizado) no qual os recursos não são compartilhados com outros usuários. Seu provedor de hospedagem, especialmente se for especializado em hospedagem de alto desempenho do Commerce, pode recomendar uma configuração diferente, igualmente ou mais eficaz para suas necessidades.

Para o Adobe Commerce em ambientes de infraestrutura em nuvem, consulte [Arquitetura inicial](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Diagrama da arquitetura de referência

O [!DNL Commerce] O diagrama da arquitetura de referência representa a abordagem de práticas recomendadas para configurar um [!DNL Commerce] site.

A cor de cada elemento no diagrama indica se o elemento faz parte do Magento Open Source ou Adobe Commerce e se é necessário.

* Elementos laranja são necessários para o Magento Open Source
* Elementos cinza são opcionais para Magento Open Source
* Elementos azuis são opcionais para o Adobe Commerce

![Diagrama da arquitetura de referência de comércio](../assets/performance/images/ref-architecture-2.3.png)

As seções a seguir fornecem recomendações e considerações para cada seção do diagrama da arquitetura de referência do comércio.

### [!DNL Varnish]

* A [!DNL Varnish] o cluster pode ser dimensionado para o tráfego de um site
* Ajuste o tamanho da instância com base no número de páginas de cache necessárias
* Em um site de alto tráfego, use um [!DNL Varnish] Principal para garantir a liberação em cache de uma solicitação (no máximo) por camada da Web

### Web

* Habilitar escala de nós para tráfego e redundância
* Um nó é principal e executa o cron
* Como alternativa, use um Admin dedicado e nós de trabalho

### Cache

* Considere implementar uma instância Redis separada para sessões
* Você pode ter uma instância de Redis por cache
* Dimensione sua instância para conter o maior tamanho de cache esperado

### Banco de dados e filas

* Sites de alto tráfego podem ajustar o desempenho de BD com BDs escravos e dividir BDs para pedidos/carrinhos (em Adobe Commerce)
* Considere o uso de um banco de dados escravo para permitir recuperação rápida e backups de dados
* Sites de tráfego baixo podem armazenar imagens no banco de dados

### Pesquisar {#search-heading}

* Ajustar o número de instâncias com base no tráfego de pesquisa

### Armazenamento

* Considere o uso do GFS ou GlusterFS para armazenamento de pub/mídia
* Como alternativa, use o armazenamento de banco de dados para sites de baixo tráfego

### Recomendado [!DNL Varnish] arquitetura de referência

O Magento suporta vários mecanismos completos de armazenamento em cache de página (Arquivo, Memcache, Redis, [!DNL Varnish]) imediatamente, juntamente com a cobertura expandida por meio de extensões. [!DNL Varnish] é o mecanismo de cache de página completo recomendado.  [!DNL Commerce] suporta vários [!DNL Varnish] configurações.

Para sites que não exigem alta disponibilidade, recomendamos usar um [!DNL Varnish] configuração com terminação Nginx SSL.

![Simples [!DNL Varnish] Configuração com a terminação SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Para sites que exigem alta disponibilidade, recomendamos usar um [!DNL Varnish] configuração com um balanceador de carga de terminação SSL.

![Alta disponibilidade em duas camadas [!DNL Varnish] configuração com balanceador de carga de terminação de SSL](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
