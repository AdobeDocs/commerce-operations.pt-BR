---
title: Tecnologias de infraestrutura em nuvem
description: Dê uma olhada mais de perto na coleção de tecnologias que usamos para o Adobe Commerce na infraestrutura em nuvem.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Tecnologias

Como mencionamos, a Adobe Commerce utiliza várias soluções de software para suportar a plataforma. Especificamente, no que diz respeito à produção, dividimos algumas das soluções e recursos técnicos incluídos no Adobe Commerce na infraestrutura em nuvem que ajudam a aproveitar ao máximo seu ambiente de produção.

![Diagrama mostrando a Adobe Commerce na tecnologia de infraestrutura de nuvem](../../../assets/playbooks/infrastructure-technology.svg)

## Soluções de software

- **Nginx**—Servidor Web utilizando PHP-FPM. Há uma instância com vários trabalhadores.

- **GlusterFS**—Servidor de arquivos para gerenciar todas as implantações de arquivos estáticos e sincronização com quatro montagens de diretório:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**—Um servidor por VM com apenas um ativo e os outros dois como réplicas.

- **Elasticsearch**—Procure Adobe Commerce versão 2.2.x e posterior.

- **Galera**—Cluster de banco de dados com um banco de dados MariaDB MySQL por nó com uma configuração de incremento automático de três para IDs exclusivas em cada banco de dados.

## Recursos e benefícios

- Com três instâncias dedicadas em um VPC, há um balanceador de carga elástico em três zonas de disponibilidade ou data centers separados.

- Uma maior resiliência é fornecida em relação a eventos que podem causar falha em uma única instância. Por exemplo, uma interrupção de uma zona de disponibilidade ou data center do AWS inteiro.

- Tempo de inatividade zero dimensionando em toda a pilha, incluindo Web, armazenamento em cache, pesquisa e banco de dados, em menos de 15 minutos.
