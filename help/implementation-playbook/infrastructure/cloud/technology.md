---
title: Tecnologias de infraestrutura em nuvem
description: Dê uma olhada mais de perto na coleção de tecnologia que usamos para o Adobe Commerce na infraestrutura em nuvem.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Tecnologias

Como mencionamos, o Adobe Commerce utiliza várias soluções de software para suportar a plataforma. Especificamente, no que diz respeito à produção, dividimos algumas das soluções e recursos técnicos incluídos no Adobe Commerce on cloud Infrastructure que ajudam a aproveitar ao máximo seu ambiente de produção.

![Diagrama que mostra o Adobe Commerce na tecnologia de infraestrutura em nuvem](../../../assets/playbooks/infrastructure-technology.svg)

## Soluções de software

- **Nginx**—Servidor Web usando PHP-FPM. Há uma instância com vários trabalhadores.

- **GlusterFS** — Servidor de arquivos para gerenciar todas as implantações de arquivos estáticos e sincronização com quatro montagens de diretório:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** — um servidor por VM com apenas um ativo e os outros dois como réplicas.

- **Elasticsearch** — Procure por Adobe Commerce versão 2.2.x e posterior.

- **Galera** — Cluster do banco de dados com um banco de dados MariaDB MySQL por nó com uma configuração de incremento automático de três para IDs exclusivas em cada banco de dados.

## Recursos e benefícios

- Com três instâncias dedicadas em um VPC, há um balanceador de carga elástico em três zonas de disponibilidade ou data centers separados.

- Uma maior resiliência é fornecida em relação a eventos que podem causar falha em uma única instância. Por exemplo, uma interrupção de uma zona de disponibilidade AWS inteira ou data center.

- Tempo de inatividade zero dimensionando em toda a pilha, incluindo Web, armazenamento em cache, pesquisa e banco de dados, em menos de 15 minutos.
