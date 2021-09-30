---
title: Arquitetura de referência global do Adobe Commerce
description: Aproveite ao máximo a sua implementação do Adobe Commerce, aproveitando uma arquitetura de referência global.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Arquitetura de referência global (GRA)

Ao executar empresas que têm vários sites para várias marcas em vários mercados locais (com moedas, idiomas, mídia, catálogos compartilhados e carrinhos únicos localizados) e que desejam evitar custos desnecessários para implementar o mesmo recurso e integrações. A Arquitetura de Referência Global (GRA) é sempre uma boa opção.

![Quadro que explica o custo da divergência na arquitetura](../../assets/playbooks/divergent-architecture.svg)

![Quadro que explica o custo da arquitetura consolidada](../../assets/playbooks/consolidated-architecture.svg)

O GRA é:

- Uma abordagem de implementação
- Uma estratégia de implantação
- Um modelo de governança de processos

A ARG não é:

- Um &quot;recurso&quot; de produto
- Exclusivo de qualquer plataforma de comércio
- Somente para casos de uso de negócios globais

Impactos da GRA:

- Como o código é fornecido

   - Criado em repositórios de código específicos à finalidade, que fornecem experiências diferentes.

- Como os sistemas empresariais são integrados

   - Consolida conexões com sistemas de negócios por marca e/ou região.

- Como a personalização é desenvolvida e mantida

   - Garante que as personalizações sejam centralizadas e específicas por domínio, para que todo o esforço de personalização seja feito de um ponto de vista holístico para os negócios.

- Como novos mercados são ativados

   - Simplifica o lançamento de vários canais e mercados que, de outra forma, custariam consideravelmente mais tempo e dinheiro.

