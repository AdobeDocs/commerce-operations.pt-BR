---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.64'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.64.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f6013ec84c1b3c65e2fe2ca062616976326d2fef
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.64

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.64.

O QPT v1.1.64 inclui os seguintes patches:

1. **ACP2E-3838**: corrige o problema em que os erros do CORS [!DNL Page Builder] impedem que as alterações sejam salvas no painel de Administração no modo de produção.
1. **ACP2E-3841**: corrige o problema em que as regras de preço do carrinho para produtos de remessa múltipla não se aplicam corretamente quando as condições `subselect` são usadas e o **[!UICONTROL Free Shipping]** é habilitado.
1. **ACSD-63139**: corrige o problema em que a exportação de produtos falha quando os atributos do produto contêm milhares de valores de opção.
1. **ACSD-65100**: corrige o problema em que a remoção dos valores de **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]** na configuração **[!UICONTROL Media Gallery Image Optimization]** causa um erro durante o processo de otimização de imagem.
1. **ACSD-65127**: corrige o problema em que a habilitação da minificação do JavaScript no modo de produção faz com que o [!DNL TinyMCE] 6 gere erros no console do navegador, afetando a funcionalidade e a experiência do usuário.
1. **ACSD-65787**: corrige o problema em que a classe `SchemaBuilder` falha durante a criação ou atualizações de esquema devido a uma chave de matriz indefinida *coluna* ao processar dados da tabela.
1. **ACSD-65223**: corrige o problema em que os termos e contratos selecionados manualmente para [!DNL B2B] ordens de compra resultam em um erro.
1. **ACSD-65540**: corrige o problema em que ocorre um erro de sintaxe SQL devido à ausência da função `REGEXP_LIKE` ao atualizar a tabela `company_structure`.
1. **ACSD-65684**: corrige o problema de desempenho em que a atualização do módulo `Magento_Company` após a atualização para o [!DNL B2B] 1.5.2 demorava muito para processar um grande número de registros (~100.000+) na tabela `company_structure`.

Use o menu à esquerda para navegar até uma página de patch específica.
