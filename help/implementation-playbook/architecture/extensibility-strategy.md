---
title: Estratégia de extensibilidade do Adobe Commerce
description: Saiba como o modelo de extensibilidade do Adobe Commerce permite personalizar sua implementação.
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Estratégia de extensibilidade

A plataforma de extensibilidade da Adobe Commerce permite que as marcas personalizem processos, integrem sistemas e implantem novos recursos com eficiência, mantendo a capacidade de atualização.

## Visão geral das estratégias de extensão do Commerce

A extensão dos recursos da plataforma Commerce inclui as seguintes abordagens de alto nível:

* Extensão dos recursos nativos da plataforma Commerce. Por exemplo, os comerciantes podem instalar aplicativos do Marketplace (geralmente criados por terceiros) que estendem e refinam os recursos nativos da plataforma — por exemplo, uma extensão que pode validar endereços de envio durante o check-out e facilitar a integração rápida com APIs de endereço de operadora UPS.

* Integração de aplicativos/extensões de terceiros à plataforma do Commerce. Os desenvolvedores podem usar as APIs atuais e abrangentes do REST e do GraphQL do Commerce para integrar diretamente o Commerce a soluções de terceiros.

No entanto, a arquitetura da plataforma determina as melhores estratégias para estender uma plataforma. O Commerce oferece uma cobertura avançada de API GQL e REST para implantação headless. A base de código principal do Commerce continua evoluindo para uma arquitetura mais modular e uma única camada de integração, o que fornece ferramentas de personalização novas e aprimoradas:

* [Construtor de aplicativos para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) O é uma estrutura de desenvolvimento e um conjunto de ferramentas construído na infraestrutura Adobe. Os desenvolvedores podem usá-lo para criar extensões do Commerce que variam de personalizações de experiência do usuário/vitrine a extensões de middleware e lógica de negócios.

* [Malha de API para o Construtor de aplicativos Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/) O permite aos desenvolvedores combinar várias fontes de dados em um único endpoint de API. Isso permite a orquestração ou integração de APIs privadas e de terceiros e outras interfaces de software com APIs Adobe Commerce e outros produtos de Adobe usando o Adobe I/O.

* [Eventos Adobe I/O para Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/) disponibiliza dados transacionais para aplicativos desenvolvidos com o App Builder e ganchos da Web de terceiros, oferecendo suporte à criação de aplicativos orientados por eventos.

Essas ferramentas fornecem acesso ao Console do Adobe Developer e às ferramentas do desenvolvedor do Adobe para criar APIs e integrar plug-ins e integrações personalizados.

O diagrama a seguir destaca os principais componentes da estratégia de exentisibilidade do Commerce.

![Diagrama de estratégia de extensibilidade do Adobe Commerce](../../assets/playbooks/extensibility-strategy-overview.png)
