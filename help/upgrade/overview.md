---
title: Visão geral do processo de atualização
description: Saiba mais sobre como atualizar seu projeto do Adobe Commerce e do Magento Open Source ajuda a manter sua loja segura e funcionando com eficiência.
source-git-commit: 5841f30f3b3539de425f0597ef05cab4e3316263
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Visão geral do processo de atualização

A atualização de seu projeto Adobe Commerce ou Magento Open Source é essencial para garantir que sua loja permaneça segura, em conformidade com o PCI e operando com eficiência máxima. Desenvolvemos este guia para orientá-lo pelas principais considerações ao preparar-se para uma atualização.

O guia fornece uma visão geral da jornada de atualização típica do Adobe Commerce/Magento Open Source e das práticas recomendadas para seguir ao longo dessa jornada. Ela também descreve detalhes técnicos do processo de atualização com um exemplo em tempo hábil e instruções passo a passo para atualizar para o Adobe Commerce/Magento Open Source versão 2.4.4. A versão de patch 2.4.4 estará disponível em 8 de março de 2022, portanto, é importante começar a se preparar para essa atualização antecipadamente, pois a [Fim da vida útil (EOL)](https://devdocs.magento.com/release/lifecycle-policy.html) as datas estão se aproximando tanto para a linha 2.3 quanto para as versões 2.4.0 a 2.4.3 em 2022. Por fim, fornecemos recursos de planejamento e ferramentas de atualização que tornam seu processo de atualização mais eficiente.

## Para quem é este guia?

O público-alvo deste guia inclui:

### Gerentes de comércio eletrônico e diretores técnicos

Este guia ajuda os clientes nessas funções a entender a jornada de atualização, a importância de atualizar regularmente e como planejar e se preparar para uma atualização da melhor maneira.

### Equipes de operações e desenvolvimento

Este guia ajuda essas equipes a aprenderem as etapas técnicas necessárias para atualizar para a versão 2.4.4 (ou qualquer versão do Adobe Commerce/Magento Open Source) e as ferramentas que podem usar para tornar o processo mais fácil, rápido e acessível.

## Explicação do processo de atualização

Um dos motivos pelos quais você escolheu Adobe Commerce/Magento Open Source provavelmente inclui:

- Amplo conjunto de recursos pronto para uso
- Recursos de SaaS oferecidos separados do código principal
- Oferta robusta de extensões do Marketplace
- Capacidade exclusiva de permitir flexibilidade infinita para personalizar seu site para atender melhor às necessidades de sua empresa e de seus clientes.

A vantagem de ser um produto altamente extensível e personalizável, no entanto, pode impulsionar possíveis problemas de atualização quando as personalizações não estão codificadas para as práticas recomendadas, resultando em custos de atualização mais altos do que o esperado.

_Então... por que atualizar?_

A atualização capacita sua empresa a permanecer incapaz no setor de comércio eletrônico em ritmo veloz e em constante mudança e permite que sua plataforma seja sempre compatível com os recursos mais recentes que ajudam a maximizar as vendas e as conversões. Incluir atualizações em seus planos de manutenção regulares também é essencial para garantir que sua loja permaneça segura, em conformidade com o PCI e operando com eficiência máxima.

### Segurança

A segurança é uma das principais razões para atualizar, pois 83% dos incidentes de segurança ocorrem em softwares desatualizados. De acordo com [IBM](https://www.ibm.com/security/data-breach), o custo médio de uma violação de dados é de US$ 3,86 milhões — muito maior do que o custo para reduzir esse risco por meio da atualização. O Adobe oferece duas maneiras de manter sua loja segura durante todo o ano:

- **Versões de patch**—Inclui correções de erros de alta prioridade, desempenho, qualidade e segurança.
- **Versões de patch de segurança**—Inclua correções e aprimoramentos para manter o site protegido e é mais fácil de implementar.

### Desempenho

O desempenho é outro dos principais motivos para a atualização. De acordo com [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), os primeiros cinco segundos de tempo de carga têm um efeito significativo nas taxas de conversão e a cada segundo de latência depois tem um impacto de -4,4%. Isso, aliado ao fato de que a velocidade da página é um fator importante de classificação de SEO, demonstra por que o desempenho do site é um elemento essencial do site para manter e melhorar regularmente. Cada versão de patch inclui melhorias de desempenho, portanto, aproveitar as novas versões suporta seus planos de crescimento e mantém seus negócios competitivos.

### Custo do atraso

O caso de atraso ou adiamento de atualizações de plataforma geralmente se resume ao custo imediato. No entanto, o custo real de executar uma versão desatualizada de qualquer software é muito maior e pode ter um impacto duradouro nos negócios.

Pode parecer contraintuitivo, mas executar atualizações regulares da plataforma requer menos esforço geral do que executar atualizações raras devido à quantidade de dívida técnica acumulada resultante do atraso. Trabalhamos recentemente com um parceiro que tem um comerciante de varejo que costumava realizar atualizações de maneira infrequente e inconsistente (anual ou mais). Ao transformar a maneira como eles abordam as atualizações e seguindo um caminho de atualização regular recomendado pelo Adobe ao longo de 12 meses, o parceiro foi capaz de economizar tempo de desenvolvimento cumulativo, esforço e custos associados de quatro semanas para o cliente, tudo isso foi redirecionado para iniciativas que impulsionam o crescimento dos negócios.

Quando as atualizações são executadas regularmente, as alterações são incrementais e o esforço de atualização correspondente reflete isso. Quando as atualizações da plataforma são adiadas por um período estendido, elas podem se tornar um processo muito mais envolvido. Além disso, as extensões usadas do [Marketplace](https://marketplace.magento.com/) e quaisquer outras integrações de terceiros também podem ser afetadas. Por fim, o tempo necessário para investigar, planejar e executar uma atualização atrasada é estendido, o que aumenta os esforços e custos evitáveis.

Alguns dos fatores gerais que afetam o nível de esforço para atualizar seu projeto incluem, entre outros, os seguintes:

| Complexidade técnica | Planejamento e estratégia |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Extensão das personalizações | Clareza dos requisitos, decisões de hesitação e alcance |
| Número de extensões | Sua frequência de atualização |
| Número de integrações com terceiros (OMS, ERP) | Sua estratégia de teste |
| Codificação para práticas recomendadas |  |

O contínuo crescimento no espaço de comércio digital tem aplicado maior pressão sobre as empresas para que evoluam mais rápido, com mais frequência e de maneiras imprevisíveis. A falta de manutenção e antecipação do comportamento de compra do cliente nivelou as condições de concorrência até mesmo para as maiores marcas mais estabelecidas. Você deve ser capaz de fornecer experiências robustas e personalizadas em todos os pontos de contato, sem lapsos de desempenho e tempo de atividade. Você deve ser capaz de inovar mais rápido, sem limites, para ficar à frente dos concorrentes globais. Ao atualizar, você verá sua empresa no futuro e se configurará para atender melhor às necessidades dinâmicas do cliente.

## Programação de versão de 2022

O Adobe publica um [cronograma de lançamento](https://devdocs.magento.com/release/) anualmente para facilitar o processo de planejamento dos comerciantes e recomenda atualizar cada ciclo de lançamento de patch. Para manter-se em conformidade com o PCI, os comerciantes devem estar usando o patch ou patch de segurança mais recente. A linha do tempo a seguir mostra a versão principal e os eventos EOL em 2022.

![](../assets/upgrade-guide/2022-release-timeline.png)

Os eventos importantes a serem observados incluem:

- A linha 2.3.x atinge o fim do suporte (EOS) em setembro de 2022
- 2.4.0 a 2.4.3 (baseado no PHP 7.4) chega ao EOS em novembro de 2022, quando o PHP 7.4 chega ao fim da vida útil (EOL)
- Com base nestes dois eventos de EOS, **é importante atualizar para a versão 2.4.4 ou superior até novembro de 2022**
- Em conformidade com a Adobe Commerce [política de ciclo de vida](https://devdocs.magento.com/release/lifecycle-policy.html), as versões 2.4.4 e 2.4.5 receberão suporte de qualidade e patches de segurança até novembro de 2024
