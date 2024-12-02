---
title: 'ACSD-57003: O status do pedido muda para *Concluído* em vez de mudar para *Processamento*'
description: Aplique o patch ACSD-57003 para corrigir o problema do Adobe Commerce em que o status do pedido muda para *Concluído* em vez de mudar para *Processamento*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-57003: O status do pedido muda para *Concluído* em vez de mudar para *Processamento*

O patch ACSD-57003 corrige o problema em que o status do pedido muda para *Concluído* em vez de mudar para *Processamento*. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.46 está instalado. A ID do patch é ACSD-57003. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do pedido muda para *Concluído* em vez de mudar para *Processando* quando um pedido é parcialmente reembolsado e parcialmente remetido.

<u>Etapas a serem reproduzidas</u>:

1. Criar um pedido com dois produtos configuráveis.
1. Faturar todos os itens.
1. Entregar somente o primeiro item.
1. Reembolsar/criar um aviso de crédito somente para o item remetido (*primeiro item*).
1. Verifique o status do pedido.

<u>Resultados esperados</u>:

O status do pedido deve estar no estado _Processando_.

<u>Resultados reais</u>:

O status da ordem é alterado para *Concluído* após a criação de um aviso de crédito para o item parcialmente remetido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
