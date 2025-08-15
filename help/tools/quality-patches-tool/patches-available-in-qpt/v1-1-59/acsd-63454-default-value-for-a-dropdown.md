---
title: 'ACSD-63454: O valor padrão de um atributo Suspenso e Múltipla seleção não é salvo corretamente no banco de dados'
description: Aplique o patch ACSD-63454 para corrigir o problema do Adobe Commerce em que o valor padrão de um atributo Suspenso e de Seleção Múltipla não é salvo corretamente no banco de dados.
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454: O valor padrão para os atributos [!UICONTROL Dropdown] e [!UICONTROL Multiple Select] não é salvo corretamente no banco de dados

O patch ACSD-63454 corrige o problema em que o valor padrão de um atributo [!UICONTROL Dropdown] e [!UICONTROL Multiple Select] não é salvo corretamente no banco de dados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-63454. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor padrão dos atributos [!UICONTROL Dropdown] e [!UICONTROL Multiple Select] não está salvo corretamente no banco de dados; em vez de atualizar o valor padrão, o novo valor é anexado ao antigo, separado por vírgula.

<u>Etapas a serem reproduzidas</u>:

1. Faça login no back-end, vá para **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**.
1. Clique em **[!UICONTROL Add New Attribute]**.
1. Na guia **[!UICONTROL Properties]**, defina o seguinte:
   * **[!UICONTROL Default Label]**: *teste*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**: Adicione duas opções sem selecionar **[!UICONTROL Is Default]**.
1. Clique em **[!UICONTROL Save Attribute]**.
1. Verifique no banco de dados se a coluna `default_value` está vazia.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. Retorne e defina uma das duas opções como **[!UICONTROL Is Default]**.
1. Verifique o banco de dados novamente para garantir que `default_value` agora contenha a ID da opção selecionada.
1. Retorne e altere a opção padrão selecionando a outra opção.

<u>Resultados esperados</u>:

O novo valor padrão deve substituir o valor antigo no banco de dados.

<u>Resultados reais</u>:

Em vez de substituir o valor padrão pelo novo, ele anexa o novo valor ao valor antigo, separado por vírgula.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
