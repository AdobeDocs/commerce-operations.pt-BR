---
title: 'ACSD-60632: Endereço salvo com cada tentativa de pedido'
description: Aplique o patch ACSD-60632 para corrigir o problema do Adobe Commerce em que um novo endereço é salvo a cada tentativa de inserção de pedido, independentemente de o pedido ser criado com sucesso ou não.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: Endereço salvo com cada tentativa de pedido

O patch ACSD-60632 corrige o problema em que um novo endereço é salvo a cada tentativa de inserção de pedido, independentemente de o pedido ser criado com sucesso ou não. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 está instalado. A ID do patch é ACSD-60632. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Cada vez que um pedido é tentado, uma nova entrada de endereço é salva no sistema, independentemente do pedido ser criado com sucesso.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar método de pagamento **[!DNL PayPal Payflow Link]**:
   * Em um computador local, o sistema não pode receber chamadas de API de [!DNL PayPal Payflow Link] sem um IP real.
1. Crie um produto simples.
1. Crie um cliente registrado sem endereço.
1. Adicionar o produto ao carrinho.
1. Prossiga para o Check-out.
1. Preencha o endereço. Certifique-se de que o primeiro endereço seja criado nesta etapa.
1. Na página *[!UICONTROL Review and Payments]*, selecione o botão de opção **[!UICONTROL Credit Card (Payflow Link)]**.
1. Clique em **[!UICONTROL Continue]**:
   * A página de check-out retorna à etapa *[!UICONTROL Review and Payments]* com o endereço pré-preenchido e a mensagem de erro esperada.
1. Selecione o botão de opção *[!UICONTROL Credit Card (Payflow Link)]* novamente.
1. Clique em **[!UICONTROL Continue]**.

<u>Resultados esperados</u>:

Um novo endereço não é criado na segunda tentativa de colocação de pedido.

<u>Resultados reais</u>:

Um novo endereço é criado após cada tentativa de posicionamento de pedido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
