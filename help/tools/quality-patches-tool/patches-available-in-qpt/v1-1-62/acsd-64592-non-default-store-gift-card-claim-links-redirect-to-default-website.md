---
title: 'ACSD-64592: links de reclamação de cartão-presente de loja não padrão redirecionam para o site padrão'
description: Aplique o patch ACSD-64592 para corrigir o problema em que, em uma configuração de vários sites, quando um Cartão Presente Virtual é comprado do site secundário (não padrão), o link Código do Cartão Presente no email tem o URL padrão do site.
feature: Gift, Products
role: Admin, Developer
exl-id: 1cc026c0-7487-48e8-a092-3e72085ca38a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-64592: links de reclamação de cartão-presente de loja não padrão redirecionam para o site padrão

O patch ACSD-64592 corrige um problema em que, em um ambiente de vários sites, se um Cartão Presente Virtual for comprado de um site secundário (não primário), o email contendo o link Código do Cartão Presente direcionará os usuários para o URL do site padrão. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Em uma configuração de vários sites, quando um Cartão-presente virtual é comprado de um site secundário (não padrão), o email contendo o link Código do cartão-presente direciona os usuários para o URL do site padrão.

<u>Etapas a serem reproduzidas</u>:

1. Crie um modo de exibição de site, loja e loja secundário.
1. Configure URLs de base diferentes para o site básico e secundário.
1. Crie um Cartão Presente Virtual com algumas opções de valor.
1. Gerar um novo pool de códigos em **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**.
1. Faça um pedido com o produto Cartão Presente no site secundário.
1. Faturar o pedido no administrador do Commerce.
1. Verifique a URL no link Código do Cartão Presente do *Você recebeu um presente de email Two*.

<u>Resultados esperados</u>:

O link Código do cartão-presente deve ter o link para o segundo site.

<u>Resultados reais</u>:

O link Código do cartão-presente tem o URL do site padrão, mesmo que o pedido seja feito no segundo site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:
* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
