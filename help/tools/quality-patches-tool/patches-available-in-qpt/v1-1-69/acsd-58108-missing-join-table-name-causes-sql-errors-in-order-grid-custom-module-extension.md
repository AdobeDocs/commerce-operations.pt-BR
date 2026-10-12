---
title: 'ACSD-58108: Erros SQL ocorrem na extensão de módulo personalizado da grade de ordem devido à falta de nome de tabela de junção'
description: Aplique o patch ACSD-58108 para corrigir o problema do Adobe Commerce em que um nome de tabela de junção ausente na extensão de módulo personalizado da grade de ordem causa erros de SQL ao filtrar determinadas colunas.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
exl-id: 1195e1c3-575c-48d6-8a10-c300f9bbb84a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
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
source-wordcount: '388'
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

01. Instale uma instância 2.4-develop.
02. Criar um novo pedido.
03. Instale um módulo personalizado com uma extensão SQL.
04. Navegue até **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
05. Aplique o filtro **[!UICONTROL Purchase Date]** e aguarde o resultado.
06. Aplicar filtro **[!UICONTROL Product SKU]**.

<u>Resultados esperados</u>:

A filtragem de pedidos na grade de pedidos funciona sem erros.

<u>Resultados reais</u>:

Ocorre um erro ao aplicar filtros na grade da ordem.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
