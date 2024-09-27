---
title: "ACSD-46618: o widget lista de produtos mostra preços em cache incorretos para o cliente conectado"
description: Aplique uma correção para corrigir o problema do Adobe Commerce em que o widget lista de produtos mostra preços em cache incorretos para um cliente conectado.
feature: Cache, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-46618: o widget Lista de produtos mostra preços em cache incorretos para um cliente conectado

O patch ACSD-46618 resolve o problema em que o widget lista de produtos mostra preços em cache incorretos para um cliente conectado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21 está instalado. A ID do patch é ACSD-46618. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O patch ACSD-46618 resolve o problema em que o widget lista de produtos mostra preços em cache incorretos para um cliente conectado.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, selecione **[!UICONTROL Stores]**, depois **[!UICONTROL Configuration]**, expanda **[!UICONTROL Sales]** e selecione **[!UICONTROL Tax]**. Atualize as configurações de imposto para mostrar preços incluindo e excluindo impostos.
1. Defina **[!UICONTROL Enable Cross Border Trade]** = _Sim_.
1. Crie uma regra de imposto que se aplique somente aos EUA.
1. Adicione um widget à página inicial, incluindo mais de um produto.
1. Crie dois clientes com um endereço dos EUA e um endereço fora dos EUA.
1. Faça logon usando o cliente dos EUA na loja. Verifique se a página está armazenada em cache.
1. Observe o preço exibido no widget página inicial.
1. Faça logout e login usando um cliente que não seja dos EUA.

<u>Resultados esperados</u>:

O preço exibido no widget da página inicial corresponde ao endereço do cliente.

<u>Resultados reais</u>:

O widget da página inicial mostra os preços usando o imposto para clientes fora dos EUA.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
