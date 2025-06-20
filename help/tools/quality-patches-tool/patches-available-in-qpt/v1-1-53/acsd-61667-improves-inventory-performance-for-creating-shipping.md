---
title: 'ACSD-61667: melhora o desempenho do inventário para criar entregas'
description: Aplique o patch ACSD-60584 para melhorar o desempenho do inventário para criar remessa no caso de muitas fontes com retirada na loja.
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: melhora o desempenho do inventário para criar entregas

O patch ACSD-61667 corrige o problema em que o comerciante não consegue enviar o pedido quando o armazenamento de retirada do [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/inventory/introduction) (antigo MSI) está habilitado com várias fontes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 está instalado. A ID do patch é ACSD-61667. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Você não poderá enviar o pedido quando o armazenamento de retirada MSI estiver ativado, com várias origens. Este patch melhora o desempenho do inventário para criar remessa no caso de muitas fontes com retirada na loja.

<u>Pré-requisitos:</u>:

Os módulos do Adobe Commerce Inventory estão instalados e ativados.

<u>Etapas a serem reproduzidas</u>:

1. Crie mais de *10* fontes e habilite seus locais de retirada.
1. O Armazenamento de retirada está habilitado em **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Crie um grande volume de ordens de retirada.
1. Vá para **[!UICONTROL Admin login]** e selecione **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**.
1. Filtrar e verificar pedidos pendentes.
1. Clique em **[!UICONTROL Ship]**.

<u>Resultados esperados</u>:

A página de remessa é carregada conforme esperado.

<u>Resultados reais</u>:

Você recebe um erro de *503 Tempo máximo de execução*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
