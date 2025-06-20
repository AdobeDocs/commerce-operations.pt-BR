---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.55'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.55.
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.55

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.55.

O QPT v1.1.55 inclui os seguintes patches:

1. **ACSD-58383**: corrige o problema em que a emissão de um reembolso via [!DNL REST API] com duas solicitações idênticas executadas simultaneamente cria avisos de crédito duplicados.
1. **ACSD-58471**: corrige o problema em que o conteúdo dinâmico não é carregado na página de detalhes do produto quando as regras de preço de catálogo associadas são agendadas.
1. **ACSD-58566**: corrige o problema em que [!DNL GraphQL] retorna um erro de servidor interno ao consultar o campo `created_at` na mutação `addPurchaseOrderComment`.
1. **ACSD-58685**: corrige o problema em que emails de vendas iniciados enquanto a comunicação por email está desabilitada ainda são enviados quando a comunicação por email é habilitada novamente.
1. **ACSD-58735**: corrige o problema em que um administrador restrito não consegue visualizar os carrinhos de compras abandonados na página da conta do cliente no [!UICONTROL Admin] para um site associado.
1. **ACSD-58828**: corrige o problema em que a mensagem de validação do lado do servidor *endereço é obrigatório* aparece se qualquer campo obrigatório estiver vazio, junto com a mensagem de validação do lado do cliente. A validação do lado do servidor não exibirá a mensagem para campos obrigatórios vazios, e a validação do lado do cliente lidará com a notificação de erro, informando: *Este campo é obrigatório.*
1. **ACSD-60344**: corrige o problema em que emails de confirmação de pedido duplicados são enviados ao usar um **[!UICONTROL Purchase Order]** com aprovação automática.
1. **ACSD-61348**: corrige o problema em que os itens da lista de desejos ficam visíveis via [!DNL GraphQL], mas não na loja em um ambiente com vários sites.
1. **ACSD-61534**: corrige o problema em que a configuração de design não pode ser definida usando o comando `bin/magento config:set`, e os valores bloqueados podem ser alterados por meio da manipulação de formulários. Agora, os valores bloqueados definidos de [!DNL CLI] com `--lock-env` ou `--lock-conf` não podem ser atualizados.
1. **ACSD-61785**: corrige o problema em que a atualização do atributo `reward_warning_notification` não é possível via mutação [!DNL GraphQL] e chamadas [!DNL REST API], alinhando seu comportamento com `reward_update_notification`.
1. **ACSD-62591**: corrige o problema em que o tema não é alternado corretamente quando os **[!UICONTROL User Agent Rules]** são configurados.
1. **ACSD-62793**: corrige o problema em que os atributos `datetime` nos dados exportados não incluem o componente de tempo. Além disso, se *[!UICONTROL Fields Enclosure]* estiver *habilitado*, os valores de atributo na coluna `additional_attributes` serão colocados entre aspas duplas.
1. **ACSD-62332**: corrige o problema em que a consulta da lista de produtos [!DNL GraphQL] é limitada a `total_count` de 10.000 produtos. Além disso, corrige o problema em que [!DNL Live Search] define a página atual como *1* em vez da página *2* nos critérios de pesquisa quando consultado via [!DNL GraphQL].

Use o menu à esquerda para navegar até uma página de patch específica.
