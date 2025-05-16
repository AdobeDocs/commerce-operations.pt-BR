---
title: 'ACSD-64732: controladores de terceiros não armazenados em cache corretamente com segmentos do cliente'
description: Aplique o patch ACSD-64732 para corrigir o problema do Adobe Commerce em que controladoras de terceiros não são armazenadas em cache corretamente com segmentos do cliente.
feature: Cache
role: Admin, Developer
source-git-commit: 047de42098f711036f1f5252d2cbc4a329ebbfb2
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# ACSD-64732: controladores de terceiros não armazenados em cache corretamente com segmentos do cliente

O patch ACSD-64732 corrige o problema em que as controladoras de terceiros não são armazenadas em cache corretamente com segmentos do cliente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 está instalado. A ID do patch é ACSD-64732. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Controladores de terceiros não são armazenados em cache corretamente com segmentos do cliente.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a controladora personalizada (/catalog/category/vary).
1. Vá para a guia **[!UICONTROL Network]** e verifique o valor de **[!DNL X-Magento-Vary]**.

<u>Resultados esperados</u>:

O valor **[!UICONTROL X-Magento-Vary]** deve ser o mesmo no controlador personalizado.

<u>Resultados reais</u>:

O valor de **[!UICONTROL X-Magento-Vary]** é diferente, o que causa erros de cache. Isso significa que o cache gerado anteriormente não pode ser usado ao visitar o controlador personalizado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
