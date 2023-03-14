---
title: Visão geral do processo de atualização
description: Saiba como atualizar seu projeto do Adobe Commerce ajuda a manter sua loja segura e operando com eficiência.
source-git-commit: 015997bf9aab32c443dd2cc198f2ed41018d7a49
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---


# Visão geral do processo de atualização

Atualizar seu projeto Adobe Commerce é fundamental para garantir que sua loja permaneça segura, compatível com PCI e operando no máximo de eficiência. Este guia aborda as principais considerações ao se preparar para uma atualização.

O guia fornece uma visão geral da jornada de atualização típica do Adobe Commerce e as práticas recomendadas para seguir ao longo dessa jornada. Ele também descreve detalhes técnicos do processo de atualização com um exemplo oportuno e instruções passo a passo para atualizar para a versão mais recente do Adobe Commerce. É importante analisar a Adobe Commerce [programação de lançamento](../release/schedule.md) e comece a se preparar para atualizações antecipadamente. O Adobe publica o cronograma de lançamento anualmente para facilitar o processo de planejamento dos comerciantes e recomenda atualizar cada ciclo de lançamento de patch. Para permanecer em conformidade com o PCI, os comerciantes devem estar usando o patch ou patch de segurança mais recente.

## Para quem este guia se destina?

O público-alvo deste guia inclui:

- **Gerentes de comércio eletrônico e diretores técnicos**— entenda a jornada de upgrade, a importância de fazer upgrade regularmente e como planejar e se preparar melhor para um upgrade.
- **Equipes de operações e desenvolvimento**—Saiba mais sobre as etapas técnicas necessárias para atualizar para a versão mais recente do Adobe Commerce e as ferramentas disponíveis que tornam o processo mais fácil, rápido e acessível.

## Explicação do processo de atualização

Um dos motivos pelos quais você escolheu o Adobe Commerce provavelmente inclui:

- Amplo conjunto de recursos prontos para uso
- Recursos SaaS oferecidos separados do código principal
- Oferta robusta de extensões do Marketplace
- Capacidade exclusiva de permitir flexibilidade infinita para que você possa personalizar seu site para melhor atender às necessidades de seus negócios e clientes

O benefício de ser um produto altamente extensível e personalizável, no entanto, pode estimular possíveis problemas de atualização quando as personalizações não são codificadas de acordo com as práticas recomendadas, resultando em custos de atualização maiores do que o esperado.

_Então... por que atualizar em tudo?_

A atualização capacita sua empresa a permanecer ágil no veloz e em constante mudança setor de comércio eletrônico e permite que sua plataforma seja compatível com os recursos mais recentes do Adobe Commerce que ajudam a maximizar as vendas e conversões. Incluir upgrades em seus planos de manutenção regular é essencial para garantir que sua loja permaneça segura, em conformidade com o PCI e operando no máximo de eficiência.

### Segurança

A segurança é um dos principais motivos para fazer upgrade, pois 83% dos incidentes de segurança ocorrem em software desatualizado. De acordo [IBM](https://www.ibm.com/reports/data-breach)No entanto, o custo médio de uma violação de dados é de US$ 3,86 milhões — muito superior ao custo de mitigar esse risco com o upgrade. O Adobe oferece duas maneiras de manter sua loja segura durante todo o ano:

- **Versões de correção**— Inclui correções de erros de segurança, desempenho, qualidade e alta prioridade.
- **Versões de patch de segurança**—Inclua correções e aprimoramentos para manter seu site seguro e sejam mais fáceis de implementar.

### Desempenho

O desempenho é outro motivo importante para a atualização. De acordo [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), os primeiros cinco segundos de tempo de carregamento têm um efeito significativo nas taxas de conversão e cada segundo de latência depois disso tem um impacto de -4,4%. Isso, juntamente com o fato de que a velocidade da página é um fator de classificação de SEO líder, demonstra por que o desempenho do site é um elemento crítico do seu site para manter e melhorar regularmente. Cada versão de patch inclui melhorias de desempenho, de modo que aproveitar as novas versões dá suporte aos seus planos de crescimento e mantém a sua empresa competitiva.

### Custo do atraso

O caso para atrasar ou adiar upgrades de plataformas geralmente tem um custo imediato. No entanto, o custo real de executar uma versão desatualizada de qualquer software é muito maior e pode ter um impacto duradouro em uma empresa.

Pode parecer contraintuitivo, mas a execução de atualizações regulares da plataforma requer menos esforço geral do que a execução de atualizações pouco frequentes devido à quantidade de dívida técnica acumulada resultante do atraso. Adobe recentemente trabalhou com um parceiro que tem um comerciante de varejo que costumava realizar atualizações com pouca frequência e inconsistência (anualmente ou por mais tempo). Ao transformar a maneira como eles abordam atualizações e seguir um caminho de atualização regular recomendado pela Adobe ao longo de 12 meses, o parceiro conseguiu economizar o cliente em quatro semanas de tempo de desenvolvimento cumulativo, esforço e custos associados. Esses custos poderiam então ser redirecionados para iniciativas que impulsionassem o crescimento dos negócios.

Quando as atualizações são executadas regularmente, as alterações são incrementais e o esforço de atualização correspondente reflete isso. Quando as atualizações da plataforma são adiadas por um período estendido, elas podem se tornar um processo muito mais envolvido. Além disso, as extensões usadas na [Adobe Commerce Marketplace](https://marketplace.magento.com/) e outras integrações de terceiros também podem ser afetadas. Por fim, o tempo necessário para investigar, planejar e executar um upgrade atrasado é estendido, o que adiciona esforço e custos evitáveis.

Alguns dos fatores gerais que afetam o nível de esforço para atualizar seu projeto incluem, mas não estão limitados a:

| Complexidade técnica | Planejamento e estratégia |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Extensão das personalizações | Clareza dos requisitos, decisões flutuantes e deformação do escopo |
| Número de extensões | Sua frequência de atualização |
| Número de integrações com terceiros (OMS, ERP) | Sua estratégia de teste |
| Codificação para práticas recomendadas |  |

O crescimento contínuo no espaço de comércio digital tem exercido uma maior pressão sobre as empresas para que evoluam mais rápido, com mais frequência e de maneiras imprevisíveis. A incapacidade de acompanhar e antecipar o comportamento de compra do cliente nivelou o campo de jogo até mesmo para as maiores marcas mais estabelecidas. Você deve ser capaz de fornecer experiências robustas e personalizadas em todos os pontos de contato, sem interrupções no desempenho e no tempo de atividade. Você deve ser capaz de inovar mais rápido, sem limites, para ficar à frente dos concorrentes globais. Ao atualizar, você está preparando seus negócios para o futuro e se preparando para atender melhor às necessidades dinâmicas dos clientes.
