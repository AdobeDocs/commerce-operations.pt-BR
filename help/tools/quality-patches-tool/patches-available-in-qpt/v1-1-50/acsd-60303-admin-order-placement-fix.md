---
title: 'ACSD-60303: problema de posicionamento de pedido do administrador resolvido com a minificação do HTML ativada'
description: Aplique o patch ACSD-60303 para corrigir o problema do Adobe Commerce em que um pedido do administrador não pode ser feito se a minificação do HTML estiver ativada.
feature: Orders
role: Admin, Developer
exl-id: 85b987e7-9d65-4d15-8099-985dc227b66c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-60303: problema de posicionamento de pedido do administrador resolvido com a minificação do HTML ativada

O patch ACSD-60303 corrige o problema em que um pedido do Administrador não pode ser feito se a minificação do HTML estiver ativada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 está instalado. A ID do patch é ACSD-60303. Observe que o problema está programado para ser corrigido na versão 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p9 - 2.4.4-p10, 2.4.5-p8 - 2.4.5-p9, 2.4.6-p6 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os pedidos não podem ser feitos pelo painel Admin quando a minificação do HTML está ativada.

<u>Etapas a serem reproduzidas</u>:

1. Ative a minificação do HTML.
1. Defina o **[!UICONTROL Application Mode]** como *[!UICONTROL Production]*.
1. Crie um pedido no painel Admin.

<u>Resultados esperados</u>:

O pedido foi feito com sucesso.

<u>Resultados reais</u>:

A ordem não é criada e o seguinte erro é registrado:

`report.CRITICAL: ParseError: syntax error, unexpected token "<<" in var/view_preprocessed/pub/static/vendor/magento/module-gift-wrapping/view/adminhtml/templates/order/create/info.phtml:1`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
