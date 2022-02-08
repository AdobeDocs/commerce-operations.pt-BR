---
title: Microsserviços Adobe Commerce
description: Seja capaz de diferenciar entre headless e microsserviços, pois diz respeito ao Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Sem cabeçalho e microsserviços

É importante não confundir o headless com microsserviços. Muitas vezes, ouvimos conversas sobre microsserviços na mesma frase que sem cabeça. São coisas completamente diferentes. Eles podem ser usados juntos, mas são conceitos completamente diferentes.

Uma arquitetura de microsserviços é um termo usado para descrever a prática de quebrar um aplicativo em uma coleção de serviços menores e vagamente acoplados. Os microsserviços permitem que os serviços de back-end individuais sejam:

- **Isolados um do outro**—Por exemplo, o serviço de precificação não tem dependência no serviço de catálogo.

- **Implantação de um carrinho de la**—Os clientes implantam somente as partes do aplicativo de que precisam.

- **Dimensionar independentemente**—Os recursos podem ser atribuídos a serviços de alta demanda, como pesquisa de inventário.

- **Desenvolvimento autônomo**—Podem ser desenvolvidas e utilizadas de forma independente.

Os microsserviços não têm nada a ver com cortar o cabeçalho da pilha de comércio ou das APIs. Quando pensamos sobre esses serviços de comércio no código principal que estão no back-office da Adobe Commerce, é sobre isolar esses serviços uns dos outros. Assim, uma arquitetura de microsserviços está analisando vagamente todos esses serviços, como os serviços de preços, o serviço de catálogo e o serviço de inventário, e tornando cada um isolado do outro.

Os microsserviços podem ser dimensionados independentemente e desenvolvidos de forma autônoma. Os microsserviços são semelhantes a um processo de desenvolvimento de SaaS de vários locatários. Muitos dos produtos SaaS modernos de vários locatários são desenvolvidos usando uma abordagem de vários serviços. Até os próprios produtos SaaS da Adobe, como o Order Management, a nova ferramenta de Recommendations de produto orientada por IA e outros componentes SaaS da Adobe Commerce estão sendo desenvolvidos usando uma abordagem de microsserviços. Para ser muito claro, o Adobe Commerce 2.4.x não é uma arquitetura de microsserviços, mas sim uma arquitetura sem periféricos.
