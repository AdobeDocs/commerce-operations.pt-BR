---
title: "ACSD-51819: Fazer vários pedidos com uma ID de cotação única"
description: Aplique o patch ACSD-51819 para corrigir o problema do Adobe Commerce em que vários pedidos podem ser feitos por meio da mesma ID de cotação.
feature: Orders, Checkout
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819: Fazer vários pedidos com uma ID de cotação única

O patch ACSD-51819 corrige o problema em que vários pedidos podem ser feitos por meio da mesma ID de cotação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 está instalado. A ID do patch é ACSD-51819. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Vários pedidos podem ser feitos com a mesma ID de cotação.

<u>Etapas a serem reproduzidas</u>:

1. Efetue logon como usuário.
1. Adicione itens ao carrinho e prossiga para o check-out.
1. Escolha qualquer método de pagamento, mas não clique no botão **[!UICONTROL Place Order]**.
1. Faça logon na mesma conta em outro navegador.
1. Continue com o check-out dos mesmos itens sem clicar no botão **[!UICONTROL Place Order]**.
1. Clique no botão **[!UICONTROL Place Order]** em ambos os sistemas ao mesmo tempo.
1. Validar os pedidos feitos em ambos os navegadores.

<u>Resultados esperados</u>:

Somente o primeiro pedido feito de um navegador é processado com êxito.

<u>Resultados reais</u>:

Foram feitos pedidos em ambos os navegadores.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
