---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.84'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.84.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: f0b3307638e56d5930753a4123a98ddea6714faa
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.84

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.84.

O QPT v1.1.84 inclui os seguintes patches:

1. **ACP2E-4913**: corrige o problema em que as operações de remessa e faturamento falham devido a um deadlock.
1. **ACP2E-5005**: corrige o problema em que a quantidade de uma opção de produto agrupado em uma cotação negociável é revertida para seu valor anterior quando o produto agrupado é reconfigurado no Administrador e a quantidade é editada.
1. **ACP2E-5009**: corrige o problema em que a migração de dados do Magento Open Source para o Adobe Commerce não migra corretamente as alterações de design agendado da categoria e as atualizações agendadas do produto **[!UICONTROL Special Price]**, fazendo com que algumas atualizações agendadas sejam ignoradas ou ausentes durante a migração, e melhora o desempenho da migração.
1. **ACP2E-5017**: corrige o problema em que a consulta da função do cliente por meio do GraphQL retorna um *Erro interno de servidor* quando o cliente não está atribuído a uma empresa.
1. **ACP2E-5027**: corrige o problema em que indexadores permanecem presos em um loop e a reindexação não é concluída quando o bloqueio de arquivos está habilitado.
1. **ACP2E-5029**: corrige o problema em que as alterações nas regras de preço do catálogo não aparecem em **[!DNL Live Search]** até que uma ressincronização manual seja executada.
1. **ACP2E-5041**: corrige o problema em que salvar um produto durante uma atualização agendada faz com que a loja mostre o preço normal em vez de **[!UICONTROL Special Price]** depois que a atualização termina.
1. **ACP2E-5059**: corrige o problema em que os clientes recebem emails de confirmação de pedido duplicados para o mesmo pedido.
1. **ACP2E-5122**: corrige o problema em que erros manipulados de solicitações do GraphQL para o carrinho de compras são registrados incorretamente em logs de exceção como erros de aplicativo.
1. **ACP2E-5143**: corrige o problema em que a consulta de rota do GraphQL renderiza o conteúdo completo da página do CMS quando somente os metadados de roteamento são solicitados, aumentando as consultas do banco de dados para páginas do CMS que contêm widgets do Page Builder.
1. **ACP2E-5183**: Corrige o problema em que a implantação de conteúdo estático falha no PHP 8.5 durante a compilação de um arquivo `LESS` que usa a diretiva `@magento_import`.
1. **ACP2E-5242**: corrige o problema em que a verificação da disponibilidade do produto ao adicionar itens ao carrinho exibe um erro indicando que o site não pode ser encontrado.
1. **ACP2E-5263**: corrige o problema em que a exportação de produtos para um arquivo CSV pode ser interrompida antes da inclusão de todos os produtos, resultando em um arquivo incompleto.
1. **ACP2E-5034**: corrige o problema em que o gerenciamento de cotações negociáveis redefine incorretamente os totais como *zero* ao recalcular uma cotação após selecionar um método de envio, descarta atualizações de quantidades de opções de produtos agrupados feitas por meio da ação **[!UICONTROL Configure]** no Administrador e não reflete corretamente os descontos no nível do item aplicados aos produtos de pacotes de preços dinâmicos nos subtotais da cotação.
1. **ACP2E-4741**: corrige o problema em que um produto desaparece da loja depois que um produto vinculado a ele como [!UICONTROL Related Product], [!UICONTROL Up-Sell] ou Venda Cruzada é salvo enquanto um estoque e uma origem não padrão estão em uso.
1. **ACP2E-5079**: corrige o problema em que a avaliação de um segmento de cliente atribuído a vários sites retorna clientes correspondentes somente do primeiro site quando as contas de cliente são compartilhadas globalmente.
1. **ACP2E-5127**: Corrige o problema no qual a edição de uma conta de empresa no painel Admin com uma localidade não padrão redefine seu **[!UICONTROL Credit Limit]** como *zero*.
1. **AC-15494**: corrige o problema em que a consulta de produtos retorna nomes de produtos com caracteres especiais com escape de HTML em vez de seus caracteres originais.

Use o menu à esquerda para navegar até uma página de patch específica.
