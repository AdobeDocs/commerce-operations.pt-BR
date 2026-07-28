---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.82'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.82.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: bd989d82-1e15-4534-88db-f1f51dd77ffaid: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: e52becee703b046f5ffb00b01ca780311d711ec8
workflow-type: tm+mt
source-wordcount: 485
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.82

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.82.

O QPT v1.1.82 inclui os seguintes patches:

1. **ACP2E-4815**: corrige vários problemas do GraphQL que causavam exceções de PHP em logs, a associação correta de pedidos com contas de clientes criadas pós-pedido via GraphQL e o alinhamento de respostas com o GraphQL sobre especificações HTTP.
1. **ACP2E-4194**: corrige o problema em que as respostas do GraphQL retornam códigos de status HTTP incorretos para solicitações inválidas, não autorizadas ou malformadas.
1. **ACP2E-4547**: corrige o problema em que um usuário administrador não pode usar **[!UICONTROL Add Products by SKU]** no Administrador para adicionar produtos do catálogo padrão a uma cotação negociável para uma empresa atribuída a um grupo de clientes que não está vinculada a um catálogo compartilhado.
1. **ACP2E-4593**: corrige o problema em que a página do CMS exibida para restrições de site está incorreta em sites secundários em implantações de vários sites.
1. **ACP2E-4682**: corrige o problema em que visitar uma página da Loja que verifica o status da cotação `isActive` cria registros de cotação vazios toda vez que a página é carregada.
1. **ACP2E-4695**: Corrige o problema em que o indexador de regras de catálogo consome memória excessiva e não é concluído, causando instabilidade e erros de memória insuficiente.
1. **ACP2E-4698**: corrige o problema em que editar uma imagem novamente no conteúdo de texto do Page Builder salva uma URL de mídia absoluta em vez de preservar uma diretiva de mídia portátil.
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**: corrige o problema em que a expiração dos pontos de premiação é executada lentamente em lojas com um histórico de pontos de premiação grande, causando atrasos na expiração dos pontos de premiação.
1. **ACP2E-4797**: corrige o problema em que inserir caracteres Unicode de 4 bytes no editor do WYSIWYG ou conteúdo do Page Builder no Administrador é bloqueado incorretamente mesmo quando o banco de dados está configurado para oferecer suporte a `utf8mb4`.
1. **ACP2E-4799**: corrige o problema em que a consulta do GraphQL `requisition_lists` retorna um valor `total_count` que reflete somente o número de itens na página atual em vez do número total de listas de requisições que correspondem aos critérios da consulta.
1. **[ACP2E-4805](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805.md)**: corrige o problema em que as solicitações de API de check-out se tornam significativamente mais lentas para produtos configuráveis com muitos produtos derivados quando o primeiro produto derivado comercializável aparece atrasado na lista.
1. **ACP2E-4840**: corrige o problema em que o valor de quantidade solicitado na consulta do GraphQL `products` retorna *null*.
1. **ACP2E-4870**: corrige o problema em que as notificações por email do **[!UICONTROL Product Alerts]** ignoram as configurações de email de exibição do repositório.
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**: corrige o problema em que a exibição de contas de clientes com catálogos de endereços grandes no Administrador faz logoff inesperado de usuários Administradores.
1. **ACP2E-4894**: corrige o problema em que novos pedidos atrasam a exibição nas grades de gerenciamento de pedidos de Administrador quando **[!UICONTROL Asynchronous Indexing]** está habilitado em armazenamentos de alto volume.
1. **ACP2E-4981**: corrige o problema em que os carrosséis de produtos do Page Builder exibem produtos em uma ordem que não reflete a posição definida no Administrador e inclui produtos configuráveis quando os produtos secundários correspondentes estão visíveis individualmente.

Use o menu à esquerda para navegar até uma página de patch específica.
