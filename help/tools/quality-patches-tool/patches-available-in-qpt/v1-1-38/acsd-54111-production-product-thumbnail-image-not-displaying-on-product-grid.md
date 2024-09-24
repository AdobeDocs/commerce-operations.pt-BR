---
title: "ACSD-54111: a imagem em miniatura do produto não é exibida"
description: Aplique o patch ACSD-54111 para corrigir o problema do Adobe Commerce em que todas as imagens são substituídas pela imagem de espaço reservado do produto padrão.
feature: Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54111: a imagem em miniatura do produto não é exibida

O patch ACSD-54111 corrige o problema em que todas as imagens são substituídas pela imagem de espaço reservado do produto padrão. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38 está instalado. A ID do patch é ACSD-54111. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A imagem em miniatura do produto não é exibida.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Carregue a imagem com uma miniatura e defina a posição da imagem como *[!UICONTROL Center]*.
1. Clique em **[!UICONTROL Save Configuration]**.
1. Limpar cache.
1. Acesse a loja como convidado/cliente.
1. Adicione um produto ao carrinho.
1. Execute `bin/magento catalog:image:resize` no console.
1. Abra o minicarrinho no front-end ou na grade de produtos no back-end para ver se as miniaturas de imagem estão visíveis.

<u>Resultados esperados</u>:

As imagens do produto não são substituídas pela imagem do espaço reservado.

<u>Resultados reais</u>:

As imagens do produto são substituídas pela imagem padrão do espaço reservado do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
