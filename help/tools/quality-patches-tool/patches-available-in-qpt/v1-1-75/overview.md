---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: cb39f5a778ee8af49823f45704d0bb68a13fbf08
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.75

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.75.

O QPT v1.1.75 inclui os seguintes patches:
1. **ACSD-68289**: corrige um problema em que a pesquisa de texto completo agora retorna produtos correspondentes se a condição de correspondência mínima for atendida em todos os campos pesquisáveis coletivamente, em vez de exigir que a condição seja atendida por um único campo.
1. **ACSD-68359**: corrige um problema em que selecionar um armazenamento durante o check-out usando o **[!UICONTROL Pick in Store]** não falha mais devido a URLs longas quando muitos produtos estão no carrinho. Anteriormente, isso acionava um erro 414 causado por URLs excessivamente longos gerados durante uma venda de loja.
1. **ACSD-68451**: corrige um problema para vários sites em que um administrador de empresa faz logon em um site, cria uma empresa não relacionada em outro site, mas é erroneamente vinculada a essa empresa não relacionada.
1. **ACSD-68490**: corrige o problema em que o botão **[!UICONTROL Add New Attribute]** fica visível para um usuário administrador restrito durante a criação do produto configurável.
1. **ACSD-68517**: corrige um erro de reenvio de formulário nas páginas Pesquisa no catálogo e no catálogo.
1. **ACSD-68573**: corrige o problema em que as permissões de categoria não eram aplicadas corretamente aos itens da lista de desejos do cliente. Após a correção, os itens da lista de desejos são exibidos e paginados corretamente na Web e no GraphQL.
1. **ACSD-68615**: corrige o problema em que a CLI de compensação de reserva de estoque mostrava uma exceção se a combinação processada tivesse uma ID de pedido ausente.
1. **ACSD-68793**: corrige um problema em que produtos válidos eram rejeitados incorretamente ao atribuí-los a um catálogo compartilhado.
1. **ACSD-68925**: corrige um problema em que as respostas das solicitações do GraphQL agora estão alinhadas com as especificações do GraphQL sobre HTTP. Um código de resposta 4XX é retornado quando a solicitação não pode ser analisada, não está autorizada ou encontra um problema geral se a solicitação for analisada.

Use o menu à esquerda para navegar até uma página de patch específica.
