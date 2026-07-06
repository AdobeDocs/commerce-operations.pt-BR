---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.80'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.80.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6e8a9f1bf5ac0495cbaf9178b9a422fd76721789
workflow-type: tm+mt
source-wordcount: 413
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.80

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.80.

O QPT v1.1.80 inclui os seguintes patches:

1. **[ACP2E-4493](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4493.md)**: corrige o problema em que a grade do Arquivo Morto de Ordens de Venda exibe um status de pedido incorreto quando a indexação assíncrona está habilitada.
1. **[ACP2E-4239](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4239.md)**: corrige o problema em que os filtros de grade de administração que usam atributos de data não retornam resultados devido à incompatibilidade de fuso horário entre a data selecionada, os valores [!DNL UTC] armazenados e o fuso horário de repositório configurado.
1. **[ACP2E-4481](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4481.md)**: corrige o problema em que a capacidade de venda do produto do pacote é recalculada incorretamente após o cancelamento do pedido.
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)**: Corrige o problema em que um registro de cotação nula é criado na tabela de banco de dados `quote` durante o fluxo **[!UICONTROL Login as Customer]**.
1. **[ACP2E-4488](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4488.md)**: corrige o problema em que salvar ou editar produtos no Administrador é lento para produtos com conjuntos de atributos grandes.
1. **[ACP2E-4610](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4610.md)**: corrige o problema em que o trabalho cron `sales_clean_quotes` tem problemas de desempenho.
1. **[ACP2E-4552](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4552.md)**: corrige o problema em que o status da empresa não é retornado na resposta do GraphQL.
1. **[ACP2E-4496](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4496.md)**: corrige o problema em que o trabalho cron do analytics causa degradação do desempenho durante a execução, resultando no aprimoramento do desempenho geral do sistema.
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**: corrige o problema em que imagens de espaço reservado não são carregadas na loja quando um código de armazenamento é incluído na URL.
1. **[ACP2E-4615](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4615.md)**: corrige o problema em que os reembolsos de pedidos online falham com um erro do PayPal informando *O gateway do PayPal rejeita a solicitação. Erro Interno.*.
1. **[ACP2E-4626](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4626.md)**: corrige o problema em que alguns arquivos JavaScript do Storefront eram solicitados e executados duas vezes, causando cargas duplicadas intermitentes e comportamento instável.
1. **[ACP2E-4813](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4813.md)**: corrige o problema em que os métodos de envio do USPS não estão disponíveis no check-out e as estimativas de envio estão incorretas para determinados produtos, incluindo pedidos divididos em vários pacotes.
1. **[ACP2E-4653](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653.md)**: corrige o problema em que o escopo do atributo de condição do preço do carrinho para **[!UICONTROL Category (Parent Only)]** e **[!UICONTROL Category (Children Only)]** não é exposto ao recuperar ou atualizar regras por meio da API [!DNL REST].
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**: corrige o problema em que o atributo Weight na página de produto da loja exibe apenas um valor numérico bruto na seção **[!UICONTROL Additional Information]** ou **[!UICONTROL More Information]** sem a unidade de medida configurada (lb ou kg).
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**: corrige o problema em que a validação do endereço de remessa na API [!DNL REST] não adere à configuração de atributo definida no Administrador.
1. **[ACSD-53502](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acsd-53502.md)**: corrige o problema em que **[!UICONTROL Add to Cart]** falha intermitentemente na loja do iOS [!DNL Safari] devido a chamadas recursivas para o script de monitoramento do New Relic, causando recarregamentos de página.

Use o menu à esquerda para navegar até uma página de patch específica.
