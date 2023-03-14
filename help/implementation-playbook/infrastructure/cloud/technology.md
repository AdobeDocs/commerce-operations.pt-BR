---
title: Tecnologias de infraestrutura em nuvem
description: Veja mais de perto a coleção de tecnologias que usamos para o Adobe Commerce na infraestrutura em nuvem.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: 683ce0a72aca0319ade2e4ccfd7a8e541a228156
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Tecnologias

Como mencionamos, a Adobe Commerce aproveita várias soluções de software para dar suporte à plataforma. Especificamente, como se refere à produção, analisamos algumas das soluções e recursos técnicos incluídos no Adobe Commerce na infraestrutura em nuvem que ajudam a aproveitar ao máximo seu ambiente de produção.

![Diagrama que mostra a Adobe Commerce sobre a tecnologia de infraestrutura em nuvem](../../../assets/playbooks/infrastructure-technology.svg)

## Soluções de software

- **Nginx**—Servidor Web usando PHP-FPM. Há uma instância com vários workers.

- **GlusterFS**— servidor de arquivos para gerenciar todas as implantações de arquivos estáticos e a sincronização com quatro montagens de diretórios:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**— um servidor por VM com apenas um ativo e os outros dois como réplicas.

- **Elasticsearch**—Pesquisa da versão 2.2.x e posterior do Adobe Commerce.

- **OpenSearch**—Pesquisa da versão 2.4.6 e posterior do Adobe Commerce.

- **Galera**—Cluster de banco de dados com um banco de dados MariaDB MySQL por nó com uma configuração de incremento automático de três para IDs exclusivas em cada banco de dados.

## Recursos e benefícios

- Com três instâncias dedicadas em um VPC, há um balanceador de carga elástico em três zonas de disponibilidade ou data centers separados.

- Uma resiliência maior é fornecida em relação a eventos que podem causar falha em uma única instância. Por exemplo, uma interrupção de uma zona de disponibilidade ou de um data center do AWS inteiro.

- Sem tempo de inatividade em toda a pilha, incluindo Web, cache, pesquisa e banco de dados, em menos de 15 minutos.
