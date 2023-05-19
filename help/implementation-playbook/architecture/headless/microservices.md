---
title: Microsserviços da Adobe Commerce
description: Ser capaz de diferenciar entre headless e microsserviços, pois se refere ao Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Headless e microsserviços

É importante não confundir headless com microsserviços. Na maior parte do tempo, ouvimos conversas sobre microsserviços na mesma frase que headless. São coisas completamente diferentes. Eles podem ser usados juntos, mas são conceitos completamente diferentes.

Arquitetura de microsserviços é um termo usado para descrever a prática de dividir um aplicativo em uma coleção de serviços menores e dispersos. Os microsserviços permitem que os serviços de back-end individuais sejam:

- **Isolados um do outro**— Por exemplo, o serviço de preços não depende do serviço de catálogo.

- **Implantado à la carte**— os clientes implantam somente as partes do aplicativo de que precisam.

- **Dimensionar independentemente**— Os recursos podem ser atribuídos a serviços de alta demanda, como pesquisa de inventário.

- **Desenvolvido de forma autônoma**— podem ser desenvolvidas e implantadas independentemente umas das outras.

Os microsserviços não têm nada a ver com cortar a cabeça da pilha de comércio ou das APIs. Quando pensamos sobre os serviços comerciais no código principal que estão no back office do Adobe Commerce, trata-se de isolar esses serviços uns dos outros. Assim, uma arquitetura de microsserviços está quebrando todos esses serviços, como os serviços de preços, serviço de catálogo e serviço de inventário, e tornando cada um isolado do outro.

Os microsserviços podem ser escalonados de forma independente e desenvolvidos de forma autônoma. Os microsserviços são semelhantes a um processo de desenvolvimento SaaS de vários locatários. Muitos produtos SaaS modernos com vários locatários são desenvolvidos usando uma abordagem de vários serviços. Até mesmo os produtos SaaS da Adobe, como o Order Management, a nova ferramenta Product Recommendations orientada por IA e outros componentes SaaS da Adobe Commerce estão sendo desenvolvidos usando uma abordagem de microsserviços. Para ser bem claro, o Adobe Commerce 2.4.x não é uma arquitetura de microsserviços, mas sim uma arquitetura headless.
