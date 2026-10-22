---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.84'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.84.
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
source-git-commit: ea739d12f02672cf585925b90860bca3b44de02a
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.84

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.84.

O QPT v1.1.84 inclui os seguintes patches:

1. **[ACP2E-5005](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5005.md)**: corrige o problema em que a quantidade de uma opção de produto agrupado em uma cotação negociável é revertida para seu valor anterior quando o produto agrupado é reconfigurado no Administrador e a quantidade é editada.
1. **[ACP2E-4913](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4913.md)**: corrige o problema em que a entrega da API REST e a criação da fatura falham permanentemente após um deadlock do banco de dados.
1. **ACP2E-5009**: corrige o problema em que a migração de dados do Magento Open Source para o Adobe Commerce não migra corretamente as alterações de design agendado da categoria e as atualizações agendadas do produto **[!UICONTROL Special Price]**, fazendo com que algumas atualizações agendadas sejam ignoradas ou ausentes durante a migração, e melhora o desempenho da migração.
1. **[ACP2E-5017](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5017.md)**: corrige o problema em que a consulta do cliente `role` por meio do GraphQL retorna o *erro interno do servidor* quando o cliente não está atribuído a uma empresa.
1. **ACP2E-5027**: corrige o problema em que indexadores permanecem presos em um loop e a reindexação não é concluída quando o bloqueio de arquivos está habilitado.
1. **ACP2E-5029**: corrige o problema em que as alterações nas regras de preço do catálogo não aparecem em **[!DNL Live Search]** até que uma ressincronização manual seja executada.
1. **ACP2E-5041**: corrige o problema em que salvar um produto durante uma atualização agendada faz com que a loja mostre o preço normal em vez de **[!UICONTROL Special Price]** depois que a atualização termina.
1. **[ACP2E-5059](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5059.md)**: corrige o problema em que os clientes recebem emails de confirmação de pedido duplicados para o mesmo pedido.
1. **[ACP2E-5122](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5122.md)**: corrige o problema em que erros manipulados de solicitações do GraphQL para o carrinho de compras são registrados incorretamente em logs de exceção como erros de aplicativo.
1. **[ACP2E-5143](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5143.md)**: corrige o problema em que a consulta do GraphQL `route` renderiza o conteúdo completo da página do CMS quando somente metadados de roteamento são solicitados, aumentando o número de consultas do banco de dados para páginas do CMS que contêm widgets do Page Builder.
1. **ACP2E-5183**: Corrige o problema em que a implantação de conteúdo estático falha no PHP 8.5 durante a compilação de um arquivo `LESS` que usa a diretiva `@magento_import`.
1. **ACP2E-5242**: corrige o problema em que a verificação da disponibilidade do produto ao adicionar itens ao carrinho exibe um erro indicando que o site não pode ser encontrado.
1. **ACP2E-5263**: corrige o problema em que a exportação de produtos para um arquivo CSV pode ser interrompida antes da inclusão de todos os produtos, resultando em um arquivo incompleto.
1. **ACP2E-5034**: corrige o problema em que o gerenciamento de cotações negociáveis redefine incorretamente os totais como *zero* ao recalcular uma cotação após selecionar um método de envio, descarta atualizações de quantidades de opções de produtos agrupados feitas por meio da ação **[!UICONTROL Configure]** no Administrador e não reflete corretamente os descontos no nível do item aplicados aos produtos de pacotes de preços dinâmicos nos subtotais da cotação.
1. **[ACP2E-4741](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4741.md)**: corrige o problema em que um produto desaparece da Loja depois que um produto vinculado a ele como um Produto Relacionado, Venda Suplementar ou Venda Cruzada é salvo enquanto um estoque e uma origem não padrão estão em uso.
1. **[ACP2E-5127](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5127.md)**: Corrige o problema no qual a edição de uma conta de empresa no Administrador com uma localidade não padrão redefine sua **[!UICONTROL Credit Limit]** como `0`.
1. **[ACP2E-5079](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5079.md)**: corrige o problema em que um segmento de cliente atribuído a vários sites retorna clientes correspondentes somente do primeiro site quando as contas de cliente são compartilhadas globalmente.
1. **AC-15494**: corrige o problema em que a consulta de produtos retorna nomes de produtos com caracteres especiais com escape de HTML em vez de seus caracteres originais.

Use o menu à esquerda para navegar até uma página de patch específica.
