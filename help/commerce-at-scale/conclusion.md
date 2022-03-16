---
title: Conclusão
description: Analise os conceitos do guia Fornecer experiências comerciais em escala.
exl-id: a5d5c398-451f-4283-b787-d16c7486e824
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Conclusão

Esse conteúdo deve ser um guia de alto nível para fornecer algumas áreas para investigação inicial enquanto preparava o ambiente AEM/CIF/Adobe Commerce para carga pesada. Há muitas áreas do Adobe Commerce, da CIF e do Fastly não abrangidas pelo guia acima, o que exigirá otimizações específicas para seu ambiente. Além disso, o código personalizado e os módulos de terceiros podem ter efeitos nos tempos de resposta que não podem ser abordados aqui.

Para reduzir o risco de introdução de alterações ou códigos que afetarão negativamente o tempo de resposta do usuário final da AEM/CIF/Adobe Commerce, deve-se garantir a implementação de uma estratégia completa e repetível de teste de desempenho, incluindo a definição de KPIs que podem ser medidos ao longo do tempo. O teste de desempenho deve ser realizado não apenas antes de entrar em funcionamento, mas também após o lançamento, idealmente antes de cada versão principal ou alteração nos ambientes de produção, para medir os impactos no desempenho.
