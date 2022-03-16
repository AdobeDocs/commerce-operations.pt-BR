---
title: Ambientes da infraestrutura em nuvem
description: Use os ambientes certos para os casos de uso corretos.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Ambientes

A arquitetura Adobe Commerce on cloud Infrastructure Pro suporta ambientes que você pode usar para desenvolver, testar e iniciar sua loja. Cada ambiente contém um banco de dados e um servidor da Web. Os quatro ambientes aproveitados pelo Adobe Commerce são:

- **Integração**—Fornece uma única ramificação de ambiente e você pode criar até quatro ramificações de ambiente adicionais. Isso permite no máximo cinco ramificações ativas implantadas em contêineres de Plataforma como Serviço (PaaS).

- **Estágios**—Fornece uma única ramificação de ambiente implantada em contêineres dedicados de infraestrutura como serviço (IaaS).

- **Produção**—Fornece uma única ramificação de ambiente implantada em contêineres dedicados de infraestrutura como serviço (IaaS).

- **Global Principal**—Fornece uma ramificação principal implantada em contêineres de Plataforma como Serviço (PaaS).

![Diagrama que mostra a relação entre os ambientes de nuvem do Adobe Commerce](../../../assets/playbooks/environment-diagram.svg)

## Ramificações Git

O Ambiente de integração fornece uma única ramificação de integração básica que contém seu código Adobe Commerce implantado em contêineres de Plataforma como Serviço (PaaS).

Os ambientes de infraestrutura em nuvem do Adobe Commerce oferecem suporte a um processo de integração flexível e contínuo. Comece clonando a ramificação de integração para a pasta do projeto local. Crie uma nova ramificação ou várias ramificações para desenvolver novos recursos, configurar alterações e adicionar extensões. Com uma ramificação de código desenvolvida e os arquivos de configuração correspondentes, suas alterações de código estão prontas para se mesclar à ramificação de integração para testes mais abrangentes.

![Diagrama que mostra a estratégia de ramificação baseada em git para ambientes de nuvem do Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
