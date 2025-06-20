---
title: 'ACSD-48694: erro solicitado de alteração de estado inválido impede que o cliente faça o pedido'
description: Aplique o patch ACSD-48694 para corrigir o problema do Adobe Commerce em que o erro *Alteração de estado inválida solicitada* impede que um cliente faça um pedido.
feature: Admin Workspace, Orders
role: Admin
exl-id: 6b9fa474-1d9d-411d-bbca-ce7463cfeb0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694: *Solicitação de alteração de estado inválida*. O erro impede que o cliente faça o pedido

O patch ACSD-48694 corrige o problema em que o erro *Alteração de estado inválida solicitada* impede que um cliente faça um pedido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 está instalado. A ID do patch é ACSD-48694. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O erro *Solicitação de alteração de estado inválida* impede que um cliente faça um pedido.

<u>Etapas a serem reproduzidas</u>:

1. Adicione um pequeno atraso durante a solicitação `/estimate-shipping-methods` ao incluir uma função `sleep()` em `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()`, para que a solicitação `/estimate-shipping-methods` seja concluída após `/shipping-information` ao ir da etapa de envio para a etapa de pagamento durante o check-out.
1. Configure a sessão para usar [!DNL Redis] com a configuração *disable_locking: 1*.
1. Abrir **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** e habilitar *[!UICONTROL Persistent Shopping Cart]*.
1. Faça logon como cliente e adicione um produto ao carrinho.
1. Deixe a sessão do cliente expirar. O cookie persistente e o carrinho ainda persistem.
1. Agora vá para o check-out, adicione o endereço de entrega e navegue até a seção de pagamento.
1. Volte para a home page ou para qualquer outra página e faça logon com a conta do cliente.
1. Deixe a sessão expirar novamente.
1. Agora vá diretamente para a página de check-out e navegue até a etapa de pagamento.
1. Tente fazer o pedido.

<u>Resultados esperados</u>:

* Não há erros.
* O pedido foi feito com êxito, e a página *Obrigado* é exibida.

<u>Resultados reais</u>:

O erro *Solicitação de alteração de estado inválida* é exibido, mas o pedido foi feito.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
