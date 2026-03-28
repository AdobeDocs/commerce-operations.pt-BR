---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.77'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.77.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 98ccb5c357ebcb3bc2a7bb48e61b8557a65049f9
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.77

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.77.

O QPT v1.1.77 inclui os seguintes patches:

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)**: corrige um problema em que preços incorretos são exibidos porque não é possível limpar o cache do [!DNL Redis].
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)**: corrige um problema em que o cookie `X-Magento-Vary` é definido várias vezes durante o carregamento de PDP, quando vários segmentos de clientes são criados no armazenamento.
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)**: corrige um problema em que o desempenho do check-out é degradado à medida que o número de segmentos de clientes aumenta.
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)**: corrige um problema em que a visualização da atualização agendada é interrompida ao tentar visualizar o conteúdo de armazenamentos com domínios personalizados.
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)**: corrige um problema em que a criação de uma conta de cliente falha ao usar a localidade árabe e o atributo Data de Nascimento (DOB) está definido para exibição na loja.
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)**: corrige um problema em que as páginas armazenáveis em cache não são armazenadas ou fornecidas corretamente do cache do [!DNL Fastly], resultando em comportamento de cache inconsistente e desempenho reduzido.
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)**: corrige um problema em que o preço especial não entra em vigor para sites criados em fusos horários diferentes.
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)**: corrige um problema em que um produto configurável é incluído automaticamente nas listagens do carrossel de produtos [!DNL Page Builder] se qualquer um dos seus produtos derivados atender às condições de filtragem.
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)**: corrige um problema em que o número de entradas que podem ser processadas e inseridas por meio dos trabalhos do cron `sales_*_async_insert` é limitado a *100* por execução.
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)**: corrige um problema com o cálculo de imposto incorreto em avisos de crédito ao criar um reembolso parcial a partir de uma fatura, se um aviso de crédito anterior tiver sido criado a partir da página de exibição de pedido.
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)**: corrige um problema em que os saldos dos cartões-presente e as datas de vencimento não são exibidos de acordo com o escopo do site atribuído.
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)**: corrige um problema nas operações assíncronas de reembolso em que as solicitações de reembolso com o parâmetro `is_online` não são processadas corretamente.

Use o menu à esquerda para navegar até uma página de patch específica.
