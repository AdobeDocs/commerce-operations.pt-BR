---
title: 'MDVA-42855: O novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra '
description: O patch MDVA-42855 corrige o problema em que o novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-42855. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
exl-id: 924b8f57-1fec-4e62-bf0e-1f9cafa75cab
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855: O novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra

O patch MDVA-42855 corrige o problema em que o novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-42855. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O novo endereço do cliente não é salvo no catálogo de endereços durante a finalização da compra.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente e atualize o endereço padrão de entrega e cobrança.
1. Adicione um produto ao carrinho e navegue até a página de check-out.
1. Ao enviar, clique em **+ Novo Endereço**.
1. Digite seu novo endereço e mantenha marcada a caixa de seleção **Salvar no Catálogo de Endereços**.
1. No Pagamento, marque a caixa de seleção **Meus endereços de cobrança e de entrega são iguais**.
1. Coloque o pedido.
1. Verifique o catálogo de endereços.

<u>Resultados esperados</u>:

O novo endereço de entrega é salvo no catálogo de endereços.

<u>Resultados reais</u>:

O novo endereço de entrega não é salvo no catálogo de endereços.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
