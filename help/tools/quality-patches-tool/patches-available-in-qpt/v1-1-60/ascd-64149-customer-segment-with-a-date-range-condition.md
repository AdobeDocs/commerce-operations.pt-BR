---
title: 'ACSD-64149: Um segmento de cliente com uma condição [!UICONTROL Date range] pode ser salvo quando apenas uma data é editada'
description: Aplique o patch ACSD-64149 para corrigir o problema do Adobe Commerce em que o segmento de cliente com uma condição **[!UICONTROL Date range]** pode ser salvo quando apenas uma das datas é editada.
feature: Customers, Admin Workspace
role: Admin, Developer
source-git-commit: c1c5256aee44ce65e9339cf3985e53f710fc7c8a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64149: Um segmento de cliente com uma condição [!UICONTROL Date range] pode ser salvo quando apenas uma data é editada

O patch ACSD-64149 corrige o problema em que um segmento de cliente com uma condição de intervalo de datas pode ser salvo quando apenas uma das datas é editada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 está instalado. A ID do patch é ACSD-64149. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao editar um segmento de cliente existente com uma condição em produtos dentro do carrinho de compras especificado por um intervalo de datas, o consumidor `matchCustomerSegmentProcessor` falha com um erro SQL.

<u>Etapas a serem reproduzidas</u>:

1. Verifique se o consumidor `matchCustomerSegmentProcessor` está em execução:

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Vá para o **[!UICONTROL Magento backend]**.
1. Vá para **[!UICONTROL Customers]** > **[!UICONTROL Segments]**.
1. Clique em **[!UICONTROL Add Segment]**.
1. Insira um **[!UICONTROL Segment Name]**, selecione um site em **[!UICONTROL Assigned to Website]** e verifique se **[!UICONTROL Status]** está definido como *Ativo*.
1. Clique em **[!UICONTROL Save and Continue Edit]**.
1. Vá para a guia **[!UICONTROL Conditions]** e adicione uma nova Condição: *Produtos{} > {}Lista de Produtos*{*}*.
1. Adicione uma subcondição para **[!UICONTROL Date range]** e defina um **[!UICONTROL Date range]** válido.
1. Clique no botão verde de confirmação ao lado de **[!UICONTROL Date range]**.
1. Clique no **[!UICONTROL Date range]** novamente, selecione o seletor de datas, edite um dos valores de data e confirme clicando no botão verde.

<u>Resultados esperados</u>:

O seletor **[!UICONTROL Date range]** não deve adicionar hora à data ao editar.

<u>Resultados reais</u>:

* O seletor **[!UICONTROL Date range]** adiciona hora à data:
   * Uma data tem apenas a data, enquanto a outra tem a data e a hora especificadas.
* O seguinte erro é exibido nos logs:

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
