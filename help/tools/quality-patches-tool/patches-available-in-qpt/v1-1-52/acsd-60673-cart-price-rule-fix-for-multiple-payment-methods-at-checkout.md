---
title: "ACSD-60673: [!UICONTROL Cart Price Rule] problema corrigido para vários métodos de pagamento no check-out"
description: Aplique o patch ACSD-60673 para corrigir o problema do Adobe Commerce em que os descontos de um [!UICONTROL Cart Price Rule] que usa uma condição de método de pagamento nem sempre são listados nos totais.
feature: Price Rules
role: Admin, Developer
source-git-commit: 9334b0bb7aa32cd14622c6dcef799dffe7e35fdc
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: [!UICONTROL Cart Price Rule] problema corrigido para vários métodos de pagamento no check-out

O patch ACSD-60673 corrige o problema em que os descontos de um [!UICONTROL Cart Price Rule] que usa uma condição de método de pagamento nem sempre são listados nos totais. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 está instalado. A ID do patch é ACSD-60673. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O [!UICONTROL Cart Price Rule] para vários métodos de pagamento no check-out não se aplica corretamente ao método de pagamento específico.

<u>Pré-requisitos</u>

Verifique se em **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** e **[!UICONTROL Bank Transfer]** está habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL Multiple Payment Methods]**.
1. Criar um *[!UICONTROL Cart Price Rule]*.
   * Definir **[!UICONTROL Conditions]** : Método de Pagamento como **[!UICONTROL Money Order]** (ou Transferência Bancária)
   * Selecione **[!UICONTROL Actions]** = *25%* desconto em todos os produtos
1. Crie um produto virtual.
1. Para copiar uma cotação nova e um cliente convidado *[!UICONTROL Status]*, vá para a loja e limpe os cookies.
1. Adicione o produto virtual ao carrinho.
1. Vá para *check-out*.
1. Clique no método de pagamento definido em *[!UICONTROL Cart Price Rule]*.
1. Atualize seu *[!UICONTROL Billing Address]*.
1. Certifique-se de que o desconto esteja visível no valor total.
1. Clique na caixa de seleção para alterar o método de pagamento.
1. Verifique se o desconto está visível.

<u>Resultados esperados</u>:

O desconto está visível em *Totais* depois de clicar na caixa de seleção para alternar para um método de pagamento aplicável.

<u>Resultados reais</u>:

O desconto não está visível nos *Totais*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
