---
title: Arquitetura de referência global da Adobe Commerce
description: Aproveite ao máximo a nossa implementação do Adobe Commerce utilizando uma arquitetura de referência global.
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Arquitetura de referência global (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

Ao administrar empresas com vários sites para várias marcas em vários mercados locais (com moedas, idiomas, mídia, catálogos compartilhados e carrinhos únicos localizados) e que desejam evitar custos desnecessários para implementar os mesmos recursos e integrações, a Arquitetura de Referência Global (GRA) é sempre uma boa opção.

![Tabela explicando o custo da divergência na arquitetura](../../assets/playbooks/divergent-architecture.svg)

![Tabela explicando o custo da consolidação na arquitetura](../../assets/playbooks/consolidated-architecture.svg)

GRA é:

- Uma abordagem de implementação
- Uma estratégia de implantação
- Um modelo de governança de processos

A GRA não é:

- Um &quot;recurso&quot; do produto
- Exclusivo de qualquer plataforma de comércio
- Somente para casos de uso de negócios globais

Impactos do GRA:

- Como o código é entregue

   - Construídos em torno de repositórios de código específicos por finalidade, que fornecem experiências diferentes.

- Como os sistemas de negócios são integrados

   - Consolida conexões com sistemas de negócios por marca e/ou região.

- Como a personalização é desenvolvida e mantida

   - Garante que as personalizações sejam centralizadas e específicas de domínio para que todo o esforço de personalização seja feito de um ponto de vista holístico para os negócios.

- Como novos mercados são viabilizados

   - Simplifica o lançamento de vários canais e mercados que, de outra forma, custaria muito mais tempo e dinheiro.
