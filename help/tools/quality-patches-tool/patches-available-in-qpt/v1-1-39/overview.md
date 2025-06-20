---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.39

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.39.

O QPT v1.1.39 inclui os seguintes patches:

1. **ACSD-53704**: corrige o problema em que o histórico de saldo de pontos de recompensa é calculado incorretamente após a expiração dos pontos de recompensa.
1. **ACSD-53583**: melhora o desempenho da reindexação parcial para *Produtos de Categoria* e *Categorias de Produto* indexadores.
1. **ACSD-54026**: corrige uma mensagem de erro incorreta para uma solicitação do GraphQL `updateCompanyRole` para um usuário não autorizado.
1. **ACSD-54106**: corrige o problema em que a classificação de produto de categoria por nome para caracteres com acento turco está incorreta.
1. **ACSD-52219**: corrige o problema em que os filtros salvos das grades de administração não funcionam como esperado ao alternar frequentemente entre exibições de marcadores.
1. **ACSD-54342**: corrige uma mensagem de erro incorreta *Erro na estrutura de dados: os valores são misturados* ao importar um arquivo CSV sem dados válidos.
1. **ACSD-54660**: um novo atributo de entrada *sort* foi adicionado para classificar pedidos de clientes no GraphQL por `sort_field` e `sort_direction`.
1. **ACSD-54776**: corrige o problema em que os valores de campo de produto desmarcados *[!UICONTROL Use Default Value]* e não padrão não são salvos no segundo modo de exibição de site, loja e loja.
1. **ACSD-53998**: corrige o problema em que um **[!UICONTROL Dynamic Block]** baseado em um **[!UICONTROL Customer Segment]** não funciona corretamente depois de sair de uma conta de cliente.
1. **ACSD-53204**: correções *Não é possível salvar o produto.* erro ao fazer solicitações simultâneas para adicionar imagens à galeria de produtos usando o ponto de extremidade `rest/V1/products/<sku>/media`.
1. **ACSD-47657**: adição de um mecanismo de cache para credenciais do AWS. Um provedor de credenciais agora usa o cache do Magento para armazenar em cache credenciais recuperadas do AWS para configuração EC2.

Use o menu à esquerda para navegar até uma página de patch específica.
