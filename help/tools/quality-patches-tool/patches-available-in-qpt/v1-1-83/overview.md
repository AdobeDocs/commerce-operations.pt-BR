---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.83'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.83.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: e7d4ea592892d77cea7891773645a8381870f80a
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.83

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.83.

O QPT v1.1.83 inclui os seguintes patches:

1. **AC-17975**: corrige vários problemas de compatibilidade do PHP 8.5 que afetam workflows de administração, autenticação de checkout, processamento de CAPTCHA, gerenciamento de categorias, páginas de configuração e operações de linha de comando em determinados ambientes PHP.
1. **[AC-18128](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-18128.md)**: corrige o problema em que datas de pedidos e carimbos de data/hora de comentários de pedidos retornados pelo GraphQL podem exibir datas de calendário incorretas em configurações de localidade em outros idiomas.
1. **AC-18096**: corrige o problema em que os campos de data do Sales GraphQL retornam datas em um formato diferente das versões anteriores revertendo o formato de data de separado por barra (`/`) para separado por traço (`-`).
1. **[ACP2E-4838](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4838.md)**: corrige o problema em que um usuário administrador com permissões restritas não pode excluir clientes da grade Clientes.
1. **[ACP2E-4639](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4639.md)**: corrige o problema em que o tipo de itens da lista de requisições é digitado incorretamente no esquema do GraphQL. O campo `items` mais antigo e o tipo `RequistionListItems` permanecem disponíveis, mas estão obsoletos.
1. **ACP2E-4877**: corrige o problema em que os pedidos feitos usando o **[!UICONTROL Payment on Account]** não podiam ser editados no Administrador enquanto estavam no status *Pendente*.
1. **ACP2E-4908**: corrige o problema em que catálogos grandes causam o uso excessivo de memória no Redis ou Valkey porque foram criadas entradas de cache de layout separadas para cada produto em cada exibição de loja.
1. **[AC-12854](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-12854.md)**: corrige o problema em que reordenar um pedido no Administrador cria um novo número de pedido com um sufixo `-1` em vez de atribuir o próximo número de pedido sequencial.
1. **ACP2E-4977**: corrige o problema em que os totais gerais de faturas e memorandos de crédito para produtos configuráveis não incluem **[!UICONTROL Fixed Product Tax]** (FPT), resultando em totais inferiores ao total do pedido.
1. **AC-16530**: corrige o problema em que o carrinho de compras não refletia consistentemente as atualizações agendadas das regras de preço do catálogo.
1. **AC-11389**: corrige o problema em que descontos, impostos e totais de pedidos são calculados incorretamente em alguns cenários de arredondamento.
1. **[ACP2E-4998](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4998.md)**: corrige o problema em que a solicitação da API REST `POST /V1/products/tier-prices` falhava totalmente quando uma SKU na carga não existia, impedindo que SKUs válidas fossem atualizadas.
1. **ACP2E-5015**: corrige o problema em que salvar um catálogo compartilhado no Administrador pode remover involuntariamente os produtos atribuídos e os preços quando os dados de catálogo necessários não estiverem disponíveis.
1. **AC-14940**: corrige o problema em que clicar em **[!UICONTROL Reset Password]** para uma conta de cliente no Administrador não enviava o email de redefinição de senha em alguns casos relacionados a lojas.
1. **[ACP2E-5101](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5101.md)**: corrige o problema em que a instalação do módulo B2B falhava quando indexadores eram definidos como **[!UICONTROL Update by Schedule]**.
1. **ACP2E-5205**: corrige o problema quando o carregamento de categoria leva um tempo considerável ou causa um tempo limite quando um grande número de categorias e produtos está envolvido. Além disso, a contagem de produtos agora é exibida corretamente para cada folha de categoria.
1. **ACP2E-3211**: corrige o problema em que adicionar o mesmo produto ao carrinho ao mesmo tempo na loja cria itens separados no carrinho para a mesma SKU, em vez de combiná-los em um único item.
1. **[ACP2E-5223](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5223.md)**: corrige o problema em que o índice **[!UICONTROL Catalog Permissions]** inclui sites que são excluídos de um grupo de clientes.

Use o menu à esquerda para navegar até uma página de patch específica.
