---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.85

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.85.

O QPT v1.1.85 inclui os seguintes patches:

1. **ACP2E-4929**: Corrige o problema em que os rótulos de atributo na página **[!UICONTROL Compare Products]** exibem traduções de uma exibição de repositório diferente em vez da exibição de repositório atual.
1. **ACP2E-5075**: corrige o problema em que uma regra de preço de carrinho de valor fixo com uma condição de categoria aplicava incorretamente um desconto a todos os filhos de um produto de pacote de preço dinâmico quando a regra correspondia somente ao produto pai do pacote.
1. **ACP2E-5077**: corrige o problema em que `customerCart` consultas simultâneas do GraphQL ou `POST /V1/carts/mine` solicitações REST criam carrinhos ativos duplicados para clientes que ainda não têm um carrinho ativo.
1. **ACP2E-5088**: corrige o problema em que o carrinho de compras persistente de um cliente é limpo quando a sessão expira.
1. **ACP2E-3991**: corrige o problema em que o endereço IP do cliente não é determinado corretamente.
1. **ACP2E-5092**: corrige o problema em que a página **[!UICONTROL Company Profile]** e a página Editar Cliente Admin exibem um erro quando um endereço de empresa salvo sem uma região posteriormente tem uma região adicionada ao seu país.
1. **ACP2E-5124**: Corrige o problema em que o botão **[!UICONTROL Import]** permanece disponível nos resultados da validação após a falha da validação quando o **[!UICONTROL Validation Strategy]** está definido como **[!UICONTROL Stop on Error]**.
1. **AC-17456**: corrige o problema em que a edição do escopo **[!UICONTROL Global]** na página **[!UICONTROL Design Configuration]** do Painel de Administração retorna um erro *HTTP 500* no PHP 8.4 e 8.5.
1. **ACP2E-5212**: corrige o problema em que **[!UICONTROL Quick Order]** aceita arquivos não CSV renomeados com uma extensão `.csv`.
1. **ACP2E-5300**: Corrige o problema em que pesquisas por palavras-chave para vários números de ordem separados por espaços ou vírgulas na grade do Painel de Administração **[!UICONTROL Orders]** não retornam ordens correspondentes.
1. **ACP2E-5354**: corrige o problema em que atualizar um cliente por meio da API REST faz com que um cliente associado a uma conta da empresa apareça várias vezes na grade Admin **[!UICONTROL Customers]**.
1. **ACP2E-5208**: corrige o problema em que a seção **[!UICONTROL Requisition List]** é recarregada em cada navegação de página da Storefront, mesmo quando nenhuma alteração é feita.

Use o menu à esquerda para navegar até uma página de patch específica.
