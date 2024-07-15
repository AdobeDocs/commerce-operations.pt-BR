---
title: Conclusão
description: Revise os conceitos do guia Fornecer experiências do Commerce em escala.
exl-id: a5d5c398-451f-4283-b787-d16c7486e824
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Conclusão

Esse conteúdo deve ser um guia de alto nível para fornecer algumas áreas a serem investigadas inicialmente, ao preparar seu ambiente AEM/CIF/Adobe Commerce para carga pesada. Há muitas áreas do Adobe Commerce, CIF e Fastly que não são abordadas pelo guia acima e exigirão otimizações específicas para seu ambiente. Além disso, o código personalizado e os módulos de terceiros podem ter efeitos nos tempos de resposta que não podem ser abordados aqui.

Para reduzir o risco de introdução de alterações ou códigos que afetem negativamente os tempos de resposta do usuário final do AEM/CIF/Adobe Commerce, deve garantir-se a implementação de uma estratégia de teste de desempenho completa e repetível, incluindo a definição de KPIs que possam ser medidos ao longo do tempo. Os testes de desempenho devem ser realizados não apenas antes da ativação, mas também após a ativação, de preferência antes de cada versão principal ou alteração nos ambientes de produção para medir os impactos no desempenho.
