---
title: 'ACSD-58828: a mensagem *address is required* do lado do servidor é exibida para qualquer campo obrigatório vazio, junto com a validação do lado do cliente'
description: Aplique o patch ACSD-58828 para corrigir o problema do Adobe Commerce em que a mensagem de validação do lado do servidor *address is required* é exibida se qualquer campo obrigatório estiver vazio, junto com a mensagem de validação do lado do cliente.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '387'
ht-degree: 0%
---
# ACSD-58828: O endereço *do lado do servidor é obrigatório*. A mensagem é exibida para qualquer campo obrigatório vazio, junto com a validação do lado do cliente

O patch ACSD-58828 corrige o problema em que a mensagem de validação do lado do servidor *address is required* é exibida se qualquer campo obrigatório estiver vazio, junto com a mensagem de validação do lado do cliente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-58828. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mensagem de validação do lado do servidor *endereço é obrigatório* será exibida se qualquer campo obrigatório estiver vazio, junto com a mensagem de validação do lado do cliente.

Etapas a serem reproduzidas:

1. Faça logon como cliente.
1. Adicione um produto ao carrinho.
1. Prossiga para o check-out.
1. Deixe o endereço de entrega como está.
1. Selecione o **[!UICONTROL Flat rate]** e selecione **[!UICONTROL Next]**.
1. Desmarcar **[!UICONTROL My billing and shipping address are the same]**.
1. Adicione um novo endereço na lista suspensa.
1. Deixe qualquer campo obrigatório vazio e selecione **[!UICONTROL Update]**.

Resultados esperados:

A mensagem de erro descreve informações ausentes ou incorretas necessárias para o check-out.

Resultados reais:

O endereço de erro *é obrigatório. Insira e tente novamente.* é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
