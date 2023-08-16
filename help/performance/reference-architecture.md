---
title: Arquitetura de referência
description: Revise os diagramas da arquitetura de referência recomendada para implantações de Adobe Commerce e Magento Open Source.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Arquitetura de referência

Este tópico descreve uma configuração genérica recomendada para instâncias Adobe Commerce e Magento Open Source usando servidores simples hospedados fisicamente em um data center (não virtualizado) no qual os recursos não são compartilhados com outros usuários. Seu provedor de hospedagem, especialmente se for especializado em hospedagem de alto desempenho do Commerce, pode recomendar uma configuração diferente que seja igualmente ou mais eficaz para seus requisitos.

Para o Adobe Commerce em ambientes de infraestrutura em nuvem, consulte [Arquitetura inicial](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Diagrama da arquitetura de referência

A variável [!DNL Commerce] O diagrama da arquitetura de referência representa a abordagem de práticas recomendadas para configurar uma arquitetura [!DNL Commerce] local.

A cor de cada elemento no diagrama indica se o elemento faz parte do Magento Open Source ou do Adobe Commerce e se é necessário.

* Elementos laranjas são necessários para o Magento Open Source
* Os elementos em cinza são opcionais para o Magento Open Source
* Os elementos azuis são opcionais para o Adobe Commerce

![Diagrama da arquitetura de referência do Commerce](../assets/performance/images/ref-architecture-2.3.png)

As seções a seguir fornecem recomendações e considerações para cada seção do diagrama da Arquitetura de referência do Commerce.

### [!DNL Varnish]

* A [!DNL Varnish] cluster pode ser dimensionado para o tráfego de um site
* Ajuste o tamanho da instância com base no número de páginas de cache necessárias
* Em um site de alto tráfego, use um [!DNL Varnish] Mestre para garantir a liberação de uma solicitação (no máximo) por camada da Web no cache

### Web

* Ativar escala de nós para tráfego e redundância
* Um nó é mestre e executa cron
* Como alternativa, use nós de administrador e trabalhador dedicados

### Cache

* Considere implementar uma instância Redis separada para sessões
* Você pode ter uma instância Redis por cache
* Dimensione sua instância para conter o maior tamanho de cache esperado

### Banco de dados e filas

* Sites de alto tráfego podem ajustar o desempenho do BD com BDs escravos e dividir BDs para pedidos/carrinhos (no Adobe Commerce)
* Considere usar um BD subordinado para habilitar a recuperação rápida e os backups de dados
* Sites de tráfego baixo podem armazenar imagens no BD

### Pesquisar {#search-heading}

* Ajustar o número de instâncias com base no tráfego de pesquisa

### Armazenamento

* Considere usar GFS ou GlusterFS para armazenamento em pub/mídia
* Como alternativa, use o armazenamento do BD para sites de tráfego baixo

### Recomendado [!DNL Varnish] arquitetura de referência

O Magento suporta vários mecanismos de cache de página inteira (File, Memcache, Redis, [!DNL Varnish]) prontas para uso, juntamente com cobertura expandida por meio de extensões. [!DNL Varnish] é o mecanismo de cache de página completa recomendado.  [!DNL Commerce] suporta vários tipos de [!DNL Varnish] configurações.

Para sites que não exigem alta disponibilidade, recomendamos usar um [!DNL Varnish] configuração com terminação SSL do Nginx.

![Simples [!DNL Varnish] Configuração com terminação SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Para sites que exigem alta disponibilidade, recomendamos usar uma camada 2 [!DNL Varnish] configuração com um balanceador de carga de terminação SSL.

![Alta disponibilidade em dois níveis [!DNL Varnish] configuração com o balanceador de carga de terminação SSL](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
