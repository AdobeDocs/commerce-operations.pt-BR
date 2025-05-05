---
title: 'ACSD-52657: Minicart não atualizado na segunda loja que usa o subdomínio'
description: Aplique o patch ACSD-52657 para corrigir o problema do Adobe Commerce em que o minicart não é atualizado na segunda loja que usa um subdomínio.
feature: Shopping Cart
role: Admin, Developer
exl-id: feec9dde-5532-481b-9410-7f6be9df4be7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52657: Minicart não atualizado na segunda loja que usa o subdomínio

O patch ACSD-52657 corrige o problema em que o minicart não é atualizado na segunda loja que usa um subdomínio. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 está instalado. A ID do patch é ACSD-52657. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Minicart não é atualizado na loja secundária que usa um subdomínio.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma segunda loja e configure um subdomínio para o URL de base.
1. Atualize o domínio do cookie para ter o domínio comum.
1. Na loja principal, adicione um produto ao carrinho.
1. Atualize a segunda loja e acesse a página do carrinho de compras.

<u>Resultados esperados</u>:

O carrinho de compras e o minicart são atualizados no subdomínio.

<u>Resultados reais</u>:

O Minicart não é atualizado quando o armazenamento secundário é atualizado, mas a página do carrinho mostra o produto adicionado e você pode fazer um pedido nessa sessão (o cookie `PHPSESSID` é compartilhado).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
