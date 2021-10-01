---
title: Planejamento de Cache Efetivo
description: Consulte os benchmarks recomendados para armazenamento em cache para garantir o sucesso do site sob carregamento.
source-git-commit: 41c0ba17b3d731a82ad6ecd8b16fac151a597e75
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Planejamento de armazenamento em cache eficaz para o sucesso do comércio eletrônico sob carga

Fornecer uma experiência de compra sob carga requer uma estratégia de cache bem planejada. Embora, inicialmente, o pedido das partes interessadas possa ser sempre o de apresentar dados do produto em tempo real aos clientes, não se trata de uma utilização ótima dos recursos do sistema, e os impactos do desempenho do site do usuário final ultrapassariam consideravelmente os benefícios da apresentação consistente de informações em tempo real.

A primeira etapa da estratégia de armazenamento em cache deve, por conseguinte, consistir em definir com as partes interessadas uma matriz de tempos de armazenamento em cache aceitáveis para as diferentes áreas do sítio, por exemplo:

| Área de armazenamento em cache | Com que frequência você muda? | Impacto se o conteúdo obsoleto for distribuído do cache | TTL (Tempo de vida útil) do armazenamento em cache aceitável? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Páginas HTML de conteúdo do site, atualizadas por CMS | Infrequentemente | Baixo | 1 dia |
| Mídia/ativos do modelo de conteúdo do site - logotipo, design CSS, imagens | Infrequentemente | Baixo | 1 semana |
| Páginas de listagem de produtos (PLP) | Infrequentemente | Médio | 1 dia |
| Página de detalhes do produto (PDP) | Algumas vezes | Médio | 1 hora |
| Categorias de produtos | Infrequentemente | Médio | 1 dia |
| Preços | Frequentemente | Alto | Sem cache |
| Inventário/estoque | Frequentemente | Alto | Sem cache |
| Pesquisa no site | A maioria dos usuários é exclusiva | Médio | Resultados do cache das 100 frases de pesquisa principais para 1 dia |
| Check-out | Cada usuário único | Muito alta | Sem cache |
| Carrinho de compras | Cada usuário único | Muito alta | Sem cache |
| Páginas de pagamento | Cada usuário único | Muito alta | Sem cache |

Com esse planejamento inicial concluído, a configuração técnica pode começar a ser implementada para configurar caches com base nesses requisitos.

Mesmo que o conteúdo seja atualizado e precise ser ativado no TTL de armazenamento em cache, é possível, na maioria dos casos, limpar manualmente os caches do cache do AEM dispatcher e do Adobe Commerce de forma seletiva para esse conteúdo, o que significa que as alterações urgentes serão refletidas imediatamente. O processo de limpeza manual do cache também deve ser planejado e testado antecipadamente para que, se houver a necessidade de forçar uma atualização manual em algum conteúdo, ele seja documentado em um runbook de operações do site e saiba como e quem precisa estar envolvido para agir. Um exemplo de operação manual de limpeza de cache para AEM e Adobe Commerce é mostrado aqui.
