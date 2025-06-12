---
title: 'ACSD-55241: os atributos **Used** e **Times Used** exibem valores incorretos para cupons gerados'
description: Aplique o patch ACSD-55241 para corrigir o problema do Adobe Commerce em que os atributos **Usado** e **Horas usadas** exibem valores incorretos para cupons gerados
feature: Price Rules
role: Admin, Developer
exl-id: a156f03c-c939-4ea7-bd34-03c2234edbff
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-55241: **Used** e **Times Used** exibem valores incorretos para cupons gerados

O patch ACSD-55241 corrige o problema em que os atributos **Used** e **Times Used** exibem valores incorretos para cupons gerados. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.47 está instalado. A ID do patch é ACSD-55241. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os atributos **Used** e **Times Used** exibem valores incorretos para cupons gerados.

<u>Etapas a serem reproduzidas</u>:

1. Crie **[!UICONTROL Cart Price Rules]** de **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** e adicione qualquer condição que corresponda ao fazer um pedido (Exemplo: subtotal maior que *5$*)

   * Aplicar qualquer desconto.
   * Selecione **[!UICONTROL Auto Coupon]**.
   * Ele gerará alguns Códigos de Cupom de **Gerenciar Códigos de Cupom**.
   * Reindexe e limpe o cache.

1. Crie um **[!UICONTROL customer account]** e faça logon no front-end.
1. Adicione um produto com mais de *2* quantidades no carrinho e aplique um cupom.
1. Clique em **[!UICONTROL Check Out with Multiple Addresses]**.
1. Selecione um endereço separado para cada quantidade, faça o pedido e conclua o processo de finalização.
1. Observe o total do pedido do administrador e veja o desconto aplicado.
1. Faça outro pedido com outro cupom.
1. Execute o comando `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` para atualizar o uso do código do cupom.

<u>Resultados esperados</u>:

A contagem correta deve ser exibida nas colunas **Tempo usado** e **Usado** com o valor **Sim** para **[!UICONTROL manage coupon]** no **[!UICONTROL cart price rule]** no administrador.

<u>Resultados reais</u>:

A contagem de código de cupom usada não é atualizada na coluna **Tempo de Uso** da grade de cupons, e a coluna **Usado** mostrará o valor *Não* se você fizer um pedido com vários endereços de envio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
