---
title: 'ACSD-62971: a importação de origens de estoque com valores de quantidade não numéricos resulta na definição da quantidade como 0'
description: Aplique o patch ACSD-62971 para corrigir o problema do Adobe Commerce em que a importação de origens de estoque com valores não numéricos na coluna "quantidade" resulta na definição da quantidade como 0.
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-62971: a importação de origens de estoque com valores de quantidade não numéricos resulta na definição da quantidade como 0

O patch ACSD-62971 corrige o problema em que a importação de origens de estoque com valores não numéricos na coluna &quot;quantidade&quot; resulta na definição da quantidade como 0. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-62971. Observe que o problema foi agendado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que a importação de origens de estoque com valores não numéricos na coluna **[!UICONTROL Quantity]** resulta na definição da quantidade como 0.

<u>Etapas a serem reproduzidas</u>:

1. Criar **[!UICONTROL Simple Product]** com qty=100
1. Fazer uma importação de **[!UICONTROL Stock Sources]** usando o arquivo que tem uma quantidade incorreta (&quot;abc&quot;)

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. Verifique a quantidade após a importação.

<u>Resultados esperados</u>:
A validação dos dados de importação deve falhar.

<u>Resultados reais</u>:
A quantidade de produto simples tornou-se 0 e o produto foi atualizado como [!UICONTROL Out of Stock].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
