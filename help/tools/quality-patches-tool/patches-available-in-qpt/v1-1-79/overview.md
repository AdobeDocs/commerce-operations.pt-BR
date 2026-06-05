---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.79'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.79.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9de5006ef5231f1009e3b6b44a365e151d56e998
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.79

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.79.

O QPT v1.1.79 inclui os seguintes patches:
1. **ACP2E-4402**: corrige o problema em que os produtos criados como desabilitados não eram adicionados novamente aos resultados da Regra de Destino relacionados após serem habilitados.
1. **ACP2E-4505**: corrige o problema em que era possível salvar uma categoria com dados obsoletos de uma guia do navegador duplicada, criando uma dependência circular.
1. **ACP2E-4531**: corrige o problema em que a alteração da chave de URL de uma página do CMS não atualizava a URL hierárquica da página.
1. **ACP2E-4601**: Corrige o problema em que o processamento de transações de pagamento poderia ter um comportamento ineficiente sob determinadas condições.
1. **ACP2E-4603**: corrige o problema em que a execução da reindexação do produto [!UICONTROL Catalog Permissions] deixava as linhas de índice de permissão existentes inalteradas, fazendo com que as concessões de permissão de categoria atualizadas não fossem refletidas de forma confiável nos produtos.
1. **ACP2E-4706**: corrige o problema em que os produtos não habilitados no escopo [!UICONTROL Admin] foram ignorados pelo indexador [!UICONTROL Target Rule].
1. **[ACP2E-4720](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4720.md)**: corrige o problema em que o frete grátis não foi corretamente aplicado nem removido de produtos de pacote com regras de desconto de carrinho.
1. **ACP2E-4411**: corrige o problema em que o preço incorreto é mostrado para um produto de pacote na página do carrinho e no minicarrinho para lojas de várias moedas.
1. **[ACP2E-4475](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4475.md)**: corrige o problema em que a página de listagem de produtos filtra e classifica incorretamente os produtos de pacote esgotados por preço quando a opção [!UICONTROL Display Out of Stock Products] está habilitada.
1. **ACP2E-4110**: corrige o problema em que produtos de pacote com um preço especial exibiam valores incorretos em PDP e PLP em uma moeda não padrão.
1. **[AC-10698](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10698.md)**: corrige o problema em que o sistema enviava a moeda no nível de todos os pedidos em vez de associá-la a pedidos individuais.
1. **AC-10737**: corrige um problema em que o comando `bin/magento setup:db:status` não reconhece o tipo de dados JSON.
1. **[ACP2E-4411](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4411.md)**: corrige o problema em que o preço incorreto é mostrado para um produto de pacote na página do carrinho e no minicarrinho para lojas de várias moedas.
1. **ACP2E-4475**: corrige o problema em que a página de listagem de produtos filtra e classifica incorretamente os produtos de pacote esgotados por preço quando a opção **[!UICONTROL Display Out of Stock Products]** está habilitada.
1. **[ACP2E-4110](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4110.md)**: corrige o problema em que os produtos de pacote com um **[!UICONTROL Special Price]** exibem valores incorretos no PDP e no PLP em uma moeda não padrão.
1. **AC-10698**: corrige o problema em que o sistema enviava a moeda no nível de todos os pedidos em vez de associá-la a pedidos individuais. Os preços e os totais da transação agora são enviados por pedido para [!DNL Google Tag], melhorando a precisão do rastreamento de dados de comércio eletrônico.
1. **[AC-10737](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10737.md)**: corrige um problema em que o comando `bin/magento setup:db:status` não reconhece o tipo de dados JSON.

Use o menu à esquerda para navegar até uma página de patch específica.
