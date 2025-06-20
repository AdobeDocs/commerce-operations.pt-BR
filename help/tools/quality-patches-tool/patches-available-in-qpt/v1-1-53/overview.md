---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.53.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.53

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.53.

O QPT v1.1.53 inclui os seguintes patches:

1. **ACSD-48318**: corrige o problema em que o aninhamento de emulação de ambiente não é permitido. Agora, a emulação é iniciada durante a chamada `send()` assim que a emulação é interrompida durante a chamada `getInfoBlockHtml()`.
1. **ACSD-59930**: melhora o desempenho dos fluxos *[!UICONTROL Create]*, *[!UICONTROL Save]* e *[!UICONTROL Delete]* da empresa.
1. **ACSD-60584**: corrige o problema em que um token de acesso criado para o usuário em um site tem permissão para acessar ou alterar informações do cliente em outros sites.
1. **ACSD-60804**: corrige o problema em que editar um cliente vinculado a uma empresa excluída causa o erro *Chamada para uma função membro `getSuperUserId()` em nulo*.
1. **ACSD-61133**: corrige o problema em que o cron `sales_clean_quotes` exclui cotações de ordens de compra não aprovadas.
1. **ACSD-61528**: corrige o problema em que a recuperação de funções de [!UICONTROL Admin] usando GraphQL não retorna resultados.
1. **ACSD-61553**: corrige o problema em que os descontos de *[!UICONTROL Cart Price Rule]* são calculados incorretamente quando vários descontos com prioridades diferentes e *[!UICONTROL Maximum Qty Discount is Applied To]* são aplicados ao produto.
1. **ACSD-61667**: melhora o desempenho do inventário ao criar remessa no caso de muitas fontes com *Seleção na Loja*.
1. **ACSD-61969**: corrige o problema em que o usuário precisa digitar um código de cupom que diferencie maiúsculas e minúsculas que corresponda exatamente ao código de cupom configurado.

Use o menu à esquerda para navegar até uma página de patch específica.
