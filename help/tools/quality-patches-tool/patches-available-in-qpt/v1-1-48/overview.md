---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
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
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.48

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.48.

O QPT v1.1.48 inclui os seguintes patches:

1. **ACSD-55566**: corrige o problema em que o *[!UICONTROL mergeCart mutation]* falha com um *Erro Interno do Servidor* na resposta do GraphQL ao mesclar carrinhos de origem e de destino que têm os mesmos itens agrupados.
1. **ACSD-56546**: corrige o problema em que os produtos configuráveis e agrupados são exibidos como *[!UICONTROL Out of Stock]* na loja quando a configuração *[!UICONTROL Display Out of Stock Product]* está desabilitada.
1. **ACSD-56635**: corrige o problema em que o cliente importado é duplicado com o mesmo endereço de email quando a importação é usada com [!UICONTROL Account Sharing] definido como *[!UICONTROL Global]*.
1. **ACSD-56741**: corrige a mensagem de erro *Tentando acessar o deslocamento da matriz no valor do tipo nulo* que é exibida durante `setup:upgrade` quando o banco de dados contém um gatilho MySQL personalizado não relacionado ao mecanismo de indexação e [!DNL MView].
1. **ACSD-57315**: corrige o problema em que uma nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão **[!UICONTROL Fetch]** é clicado na tela exibir transação no [!UICONTROL Admin].
1. **ACSD-57337**: corrige o problema em que um usuário administrador com restrições de acesso a sites específicos pode ver empresas de todos os sites na grade *[!UICONTROL Companies]*.
1. **ACSD-57394**: corrige a classificação de produto incorreta por campos de classificação múltipla no GraphQL.
1. **ACSD-57565**: corrige o problema em que o painel *[!UICONTROL Order]* exibe informações de pedido incorretas até que o período seja atualizado. O painel agora exibe estatísticas de ordem corretas na primeira carga.
1. **ACSD-57854**: corrige o problema em que as solicitações de GraphQL de produto retornam categorias desabilitadas nas agregações de categoria.
1. **ACSD-58008**: corrige o problema em que a atualização programada remove a versão anterior do item preparado se nenhuma data final for especificada.

Use o menu à esquerda para navegar até uma página de patch específica.
