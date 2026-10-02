---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.83'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.83.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 6fedf98a6936fe842230003e0c2d52598bcf999d
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.83

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.83.

O QPT v1.1.83 inclui os seguintes patches:

1. **AC-17975**: corrige vários problemas de compatibilidade do PHP 8.5 que afetam workflows de administração, autenticação de checkout, processamento de CAPTCHA, gerenciamento de categorias, páginas de configuração e operações de linha de comando em determinados ambientes PHP.
1. **AC-18128**: corrige o problema em que as datas de pedidos e os carimbos de data/hora de comentários de pedidos retornados pelo GraphQL exibem datas de calendário incorretas em configurações de localidade fora do inglês.
1. **AC-18096**: corrige o problema em que os campos de data do Sales GraphQL retornam datas em um formato diferente das versões anteriores revertendo o formato de data de separado por barra (`/`) para separado por traço (`-`).
1. **ACP2E-4639**: corrige o problema em que o tipo de itens da lista de requisições foi digitado incorretamente no esquema do GraphQL, enquanto o campo de itens mais antigos e o tipo `RequistionListItems` permanecem disponíveis, mas são descontinuados.
1. **ACP2E-4838**: corrige o problema em que um usuário administrador com permissões restritas não pode excluir clientes da grade Clientes.
1. **ACP2E-4877**: corrige o problema em que os pedidos feitos usando o **[!UICONTROL Payment on Account]** não podiam ser editados no Administrador enquanto estavam no status *Pendente*.
1. **ACP2E-4908**: corrige o problema em que catálogos grandes causam o uso excessivo de memória no Redis ou Valkey porque foram criadas entradas de cache de layout separadas para cada produto em cada exibição de loja.
1. **AC-12854**: corrige o problema em que reordenar um pedido no Administrador cria um novo número de pedido com um sufixo *-1* em vez de atribuir o próximo número de pedido sequencial.
1. **ACP2E-4977**: corrige o problema em que os totais gerais de faturas e memorandos de crédito para produtos configuráveis não incluem **[!UICONTROL Fixed Product Tax]** (FPT), resultando em totais inferiores ao total do pedido.
1. **AC-16530**: corrige o problema em que o carrinho de compras não refletia consistentemente as atualizações agendadas das regras de preço do catálogo.
1. **AC-11389**: corrige o problema em que descontos, impostos e totais de pedidos são calculados incorretamente em alguns cenários de arredondamento.
1. **ACP2E-4998**: corrige o problema em que a solicitação da API REST `POST /V1/products/tier-prices` falhava para toda a solicitação quando uma SKU na carga não existia, impedindo que SKUs válidas fossem atualizadas.
1. **ACP2E-5015**: corrige o problema em que salvar um catálogo compartilhado no Administrador pode remover involuntariamente os produtos atribuídos e os preços quando os dados de catálogo necessários não estiverem disponíveis.
1. **AC-14940**: corrige o problema em que clicar em **[!UICONTROL Reset Password]** para uma conta de cliente no Administrador não enviava o email de redefinição de senha em alguns casos relacionados a lojas.
1. **ACP2E-5101**: corrige o problema em que a instalação do módulo B2B falhava quando indexadores eram definidos como **[!UICONTROL Update on Schedule]**.
1. **ACP2E-5205**: corrige o problema quando o carregamento de categoria leva um tempo considerável ou causa um tempo limite quando um grande número de categorias e produtos está envolvido. Além disso, a contagem de produtos agora é exibida corretamente para cada folha de categoria.
1. **ACP2E-3211**: corrige o problema em que adicionar o mesmo produto ao carrinho ao mesmo tempo na loja cria itens separados no carrinho para a mesma SKU, em vez de combiná-los em um único item.
1. **ACP2E-5223**: corrige o problema em que o índice de Permissões de Catálogo inclui sites que são excluídos de um grupo de clientes.

Use o menu à esquerda para navegar até uma página de patch específica.
