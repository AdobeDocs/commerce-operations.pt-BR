---
title: Conclusão
description: Analise os conceitos do guia Fornecer experiências comerciais em escala.
source-git-commit: 1cff7359ddb4caeca6773ff74b92048c89676f12
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Conclusão

Esse conteúdo deve ser um guia de alto nível para fornecer algumas áreas a serem investigadas inicialmente, preparando o ambiente de comércio AEM/CIF/Adobe para carga pesada. Há muitas áreas do Adobe Commerce, CIF e Fastly que não são contempladas no guia acima, o que exigirá otimizações específicas para seu ambiente. Além disso, o código personalizado e os módulos de terceiros podem ter efeitos nos tempos de resposta que não podem ser abordados aqui.

Para reduzir o risco de introdução de alterações ou códigos que afetarão negativamente o tempo de resposta do usuário final do AEM/CIF/Adobe Commerce, deve garantir-se que seja implementada uma estratégia de teste de desempenho completa e repetível, incluindo a definição de KPIs que podem ser medidos ao longo do tempo. O teste de desempenho deve ser realizado não apenas antes de entrar em funcionamento, mas também após o lançamento, idealmente antes de cada versão principal ou alteração nos ambientes de produção, para medir os impactos no desempenho.
