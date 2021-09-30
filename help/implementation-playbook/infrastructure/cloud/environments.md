---
title: Ambientes da infraestrutura em nuvem
description: Use os ambientes certos para os casos de uso corretos.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Ambientes

O Adobe Commerce on cloud Infrastructure Pro oferece suporte a ambientes que você pode usar para desenvolver, testar e iniciar sua loja. Cada ambiente contém um banco de dados e um servidor da Web. Os quatro ambientes aproveitados pelo Adobe Commerce são:

- **Integração** — Fornece uma única ramificação de ambiente e você pode criar até quatro ramificações de ambiente adicionais. Isso permite no máximo cinco ramificações ativas implantadas em contêineres de Plataforma como Serviço (PaaS).

- **Armazenamento temporário** — Fornece uma única ramificação de ambiente implantada em contêineres dedicados de infraestrutura como serviço (IaaS).

- **Produção** — Fornece uma única ramificação de ambiente implantada em contêineres dedicados de infraestrutura como serviço (IaaS).

- **Global Principal** — Fornece uma ramificação principal implantada em contêineres de Plataforma como Serviço (PaaS).

![Diagrama que mostra a relação entre os ambientes de nuvem do Adobe Commerce](../../../assets/playbooks/environment-diagram.svg)

## Ramificações Git

O Ambiente de integração fornece uma única ramificação de integração básica que contém seu código de comércio do Adobe implantado em contêineres de Plataforma como um Serviço (PaaS).

O Adobe Commerce em ambientes de infraestrutura em nuvem oferece suporte a um processo de integração flexível e contínuo. Comece clonando a ramificação de integração para a pasta do projeto local. Crie uma nova ramificação ou várias ramificações para desenvolver novos recursos, configurar alterações e adicionar extensões. Com uma ramificação de código desenvolvida e os arquivos de configuração correspondentes, suas alterações de código estão prontas para se mesclar à ramificação de integração para testes mais abrangentes.

![Diagrama que mostra a estratégia de ramificação baseada em git para ambientes de nuvem do Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
