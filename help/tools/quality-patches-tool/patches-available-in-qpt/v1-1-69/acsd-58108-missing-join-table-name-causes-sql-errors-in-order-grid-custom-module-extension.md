---
title: 'ACSD-58108: Erros SQL ocorrem na extensão de módulo personalizado da grade de ordem devido à falta de nome de tabela de junção'
description: Aplique o patch ACSD-58108 para corrigir o problema do Adobe Commerce em que um nome de tabela de junção ausente na extensão de módulo personalizado da grade de ordem causa erros de SQL ao filtrar determinadas colunas.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 26009fee51fb81e2517ad09319bac1190d127564
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-58108: Erros SQL ocorrem na extensão de módulo personalizado da grade de ordem devido à falta de nome de tabela de junção

O patch ACSD-58108 corrige o problema em que um nome de tabela de junção ausente na extensão de módulo personalizado da grade de ordem causa erros de SQL ao filtrar determinadas colunas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-58108. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O nome ausente da tabela de junção na tabela de busca original causa erros SQL na grade da ordem ao usar uma extensão de módulo personalizada. Esse problema ocorre porque a função `addFilterToMap` não funciona para determinadas colunas após unir a tabela **[!UICONTROL sales_order_item]**, resultando em erros ao filtrar.

<u>Etapas a serem reproduzidas</u>:

&#x200B;01. Instale uma instância 2.4-develop.
&#x200B;02. Criar um novo pedido.
&#x200B;03. Instale um módulo personalizado com uma extensão SQL.
&#x200B;04. Navegue até **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
&#x200B;05. Aplique o filtro **[!UICONTROL Purchase Date]** e aguarde o resultado.
&#x200B;06. Aplicar filtro **[!UICONTROL Product SKU]**.

<u>Resultados esperados</u>:

A filtragem de pedidos na grade de pedidos funciona sem erros.

<u>Resultados reais</u>:

Ocorre um erro ao aplicar filtros na grade da ordem.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
