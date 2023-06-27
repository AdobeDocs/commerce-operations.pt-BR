---
title: Planejamento Efetivo do Cache
description: Consulte os benchmarks recomendados para armazenamento em cache para garantir o sucesso do site sob carga.
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
feature: Integration, Cache
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Planejamento do armazenamento em cache eficaz para o sucesso do comércio eletrônico sob carga

A entrega de uma experiência de compra em carga exigirá uma estratégia de armazenamento em cache bem planejada. Embora inicialmente a solicitação das partes interessadas seja sempre apresentar os dados do produto em tempo real aos clientes, esse não é um uso ideal dos recursos do sistema, e os impactos do desempenho do site do usuário final seriam muito maiores do que os benefícios de mostrar consistentemente as informações em tempo real.

A etapa inicial da estratégia de armazenamento em cache deve, por conseguinte, consistir em definir, com as partes interessadas pertinentes, uma matriz de prazos de armazenamento em cache aceitáveis para as diferentes áreas do site, por exemplo:

| Área de armazenamento em cache | Com que frequência o muda? | Impacto se o conteúdo obsoleto veiculado a partir do cache | Tempo de vida (TTL) aceitável para armazenamento em cache? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Páginas de HTML de conteúdo do site, atualizadas via CMS | Raramente | Baixa | 1 dia |
| Mídia/ativos do modelo de conteúdo do site - logotipo, design de CSS, imagens | Raramente | Baixa | 1 semana |
| Páginas de listagem de produtos (PLP) | Raramente | Medium | 1 dia |
| Página de detalhes do produto (PDP) | Às vezes | Medium | 1 hora |
| Categorias de produto | Raramente | Medium | 1 dia |
| Preços | Frequentemente | Alta | Sem cache |
| Estoque/estoque | Frequentemente | Alta | Sem cache |
| Pesquisa no site | A maioria dos usuários é única | Medium | Armazenar em cache os resultados das 100 principais frases de pesquisa por 1 dia |
| Check-out | Cada usuário único | Muito alto | Sem cache |
| Carrinho de compras | Cada usuário único | Muito alto | Sem cache |
| Páginas de pagamento | Cada usuário único | Muito alto | Sem cache |

Com esse planejamento inicial concluído, a configuração técnica pode começar a ser implementada para configurar caches com base nesses requisitos.

Mesmo que o conteúdo seja atualizado e precise ser colocado em funcionamento dentro do TTL de cache, na maioria dos casos, é possível limpar manualmente os caches para o [Dispatcher AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) e [Adobe Commerce](../configuration//cli/manage-cache.md#clean-and-flush-cache-types) armazenar em cache de forma seletiva esse conteúdo, o que significa que as alterações urgentes serão refletidas imediatamente. O processo de limpeza manual do cache também deve ser planejado e testado antecipadamente para que, se houver necessidade de forçar manualmente uma atualização em algum conteúdo, ele seja documentado em um runbook de operações do site e limpe como e quem precisa ser envolvido para agir isso.
