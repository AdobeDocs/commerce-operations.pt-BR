---
title: 'ACSD-48293: produtos compostos sem estoque quando vendidos produtos secundários reabastecidos'
description: Aplique o patch ACSD-48293 para corrigir o problema do Adobe Commerce em que os produtos compostos ficam sem estoque quando os produtos secundários esgotados são devolvidos ao estoque.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293: produtos compostos sem estoque quando vendidos produtos secundários reabastecidos

O patch ACSD-48293 corrige o problema em que os produtos compostos saem do estoque quando os produtos secundários esgotados são devolvidos ao estoque. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 está instalado. A ID do patch é ACSD-48293. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos compostos ficam sem estoque quando os produtos secundários que foram vendidos são devolvidos ao estoque.

<u>Etapas a serem reproduzidas</u>:

1. Crie um modo de exibição de site, loja e loja secundário.
1. Crie duas fontes e estoques e atribua-os a cada site.
1. Habilite a opção mostrar produtos indisponíveis em **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Crie um produto configurável com um produto associado usando a fonte de estoque do site primário (defina qtd = 1).
1. Faça um pedido do produto configurável.
1. Execute o cron.
1. Abra o produto configurável na loja e confirme se ele está indisponível.
1. Abra o produto configurável do [!UICONTROL Admin] e defina o **[!UICONTROL Manage Stock Option]** como *[!UICONTROL No]*.
1. Execute o cron.
1. Envie o pedido e adicione a quantidade ao produto simples que está em estoque.
1. Execute o cron.
1. Verifique a disponibilidade do produto na loja.

<u>Resultados esperados</u>:

O produto configurável está no estoque.

<u>Resultados reais</u>:

O produto configurável está esgotado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
