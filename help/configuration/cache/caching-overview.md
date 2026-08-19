---
title: Visão geral do armazenamento em cache e opções de configuração
description: Saiba mais sobre armazenamento em cache no Adobe Commerce, incluindo armazenamento de back-end, configuração de front-end e armazenamento em cache de página inteira com cache L2, Vernish, Redis e Valkey.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# Visão geral do armazenamento em cache e opções de configuração

O Adobe Commerce usa várias camadas de cache para reduzir o processamento repetido, diminuir a carga do banco de dados e melhorar os tempos de resposta. Essas camadas operam em diferentes pontos na solicitação e na entrega de ativos:

- O **cache de aplicativo** armazena dados gerados ou processados usando tipos de cache do Commerce.
- O **cache de página inteira do HTTP** armazena respostas HTTP completas antes de chegar ao aplicativo do Commerce.
- O **cache L2** pode adicionar um cache local em cada nó da Web em frente ao armazenamento de cache remoto compartilhado.
- **O armazenamento em cache de conteúdo estático** permite que os navegadores reutilizem CSS, JavaScript, imagens e outros recursos estáticos.

Esta página fornece uma visão geral conceitual dessas camadas e links para sua orientação de configuração. Para opções de back-end, detalhes de implementação e configurações específicas da versão, consulte [Opções de back-end de cache e referência de armazenamento](cache-options.md).

## Armazenamento em cache de camadas

### Armazenamento em cache do aplicativo

O armazenamento em cache de aplicativos do Commerce é organizado como:

>[!BEGINSHADEBOX]

tipo de cache → front-end do cache → back-end do cache

>[!ENDSHADEBOX]

Um **tipo de cache** identifica o tipo de dados que está sendo armazenado em cache, como configuração, layout, HTML de bloco ou conteúdo de página inteira. Um **front-end do cache** conecta um ou mais tipos de cache ao armazenamento. Um **back-end de cache** fornece a implementação de armazenamento.

Você pode atribuir diferentes tipos de cache a diferentes front-ends quando configurações de cache ou armazenamento separados forem necessários. Para obter detalhes sobre a configuração, consulte [Configurar front-ends e tipos de cache](cache-types.md).

### Cache HTTP de página inteira

O cache de página inteira HTTP armazena respostas completas na camada HTTP ou CDN. Para implantações de produção:

- **Adobe Commerce no local**—A Adobe recomenda [Verniz](config-varnish.md) para armazenamento em cache de página inteira. O verniz opera como um proxy reverso na frente do servidor Web.
- A **infraestrutura do Adobe Commerce na nuvem** usa o [Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"} para a camada de armazenamento em cache de borda e página inteira. A infraestrutura em nuvem não usa um serviço verniz gerenciado separadamente.

>[!NOTE]
>
>Alterar o back-end do cache de aplicativos do Commerce não configura o Varnish ou o Fastly. O cache HTTP de página inteira é configurado e gerenciado separadamente do cache de aplicativos de baixo nível.

### Cache L2

O cache L2, ou de dois níveis, adiciona um cache local em cada nó da Web do Commerce, além de reter o armazenamento em cache remoto compartilhado. Os dados acessados com frequência podem ser fornecidos localmente, reduzindo a comunicação com o cache remoto em implantações de vários nós.

A configuração L2 e as implementações compatíveis variam de acordo com a versão e o tipo de implantação do Commerce. Para obter detalhes, consulte [configuração do cache L2](level-two-cache.md).

### Armazenamento em cache de conteúdo estático

O Commerce pode melhorar o cache do navegador para recursos estáticos, como CSS, JavaScript e imagens, adicionando uma versão de implantação a seus URLs. Quando o conteúdo é alterado, o URL muda, fazendo com que o navegador solicite o novo recurso em vez de usar uma cópia em cache mais antiga.

## Configuração específica para implantação

As tarefas de configuração a seguir variam de acordo com o tipo de implantação.

| Tarefa | No local | Infraestrutura em nuvem |
| --- | --- | --- |
| Infraestruturas do cache de aplicativos | [Opções de back-end do cache e referência de armazenamento](cache-options.md) | [Práticas recomendadas para a configuração do serviço Valkey e Redis](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| Cache de página inteira HTTP | [Configurar verniz](config-varnish.md) | [Visão geral dos serviços do Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) |

As seguintes tarefas se aplicam a todos os tipos de implantação:

- **Configurar tipos de cache e front-ends** [Configurar front-ends e tipos de cache](cache-types.md) para associar tipos de cache com front-ends de cache.
- **Configurar cache L2**—[Configuração de cache L2](level-two-cache.md).
- **Configurar a invalidação do cache do navegador para conteúdo estático**—[Assinatura de conteúdo estático e invalidação do cache do navegador](static-content-signing.md).
