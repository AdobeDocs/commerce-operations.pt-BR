---
title: 'ACSD-56246: O agendamento de atualizações de produto apaga valores de atributo de seleção múltipla'
description: Aplique o patch ACSD-56246 para corrigir o problema do Adobe Commerce em que a programação de atualizações de produtos apaga os valores de atributo de seleção múltipla.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
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
source-wordcount: '432'
ht-degree: 5%
---
# ACSD-56246: o agendamento de atualizações de produto apaga valores de atributos de multisseleção

O patch ACSD-56246 corrige o problema em que o agendamento de atualizações de produtos apaga valores de atributos de multisseleção. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. A ID do patch é ACSD-56246. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As atualizações de produto programadas apagam os valores de atributo de seleção múltipla.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e crie o seguinte atributo:

   * Rótulo padrão: Programa
   * Tipo de Entrada de Catálogo para Proprietário da Loja: Seleção Múltipla
   * Gerenciar opções (valores do seu atributo): Choice, Sunscape, Safetyshield
   * Código do atributo: customer_program
   * Escopo: Global
   * Adicionar às Opções de Coluna: Não
   * Usar nas Opções de Filtro: Não
   * Propriedades da vitrine
   * Posição: *333*
   * Permitir Tags do HTML na Loja: Não

1. Executar
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Executar
   `bin/magento setup:upgrade`.
1. Vá para **[!UICONTROL Admin]** > Escolha qualquer produto simples > Selecione todos os itens no atributo de programa > Clique em **[!UICONTROL Save the product]**.
1. Agende uma atualização para esse produto no próximo minuto e execute o comando abaixo para que o Armazenamento temporário de conteúdo funcione:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Resultados esperados</u>:

O atributo **[!UICONTROL program]** do produto não deve ser alterado.

<u>Resultados reais</u>:

O atributo **[!UICONTROL program]** do produto é limpo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
