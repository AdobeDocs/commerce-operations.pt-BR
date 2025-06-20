---
title: 'ACSD-62758: resolução do problema de renderização de vídeo nas páginas de produto configuráveis'
description: Aplique o patch ACSD-62758 para corrigir o problema do Adobe Commerce, em que os vídeos de produtos nas páginas de detalhes do produto configuráveis não são renderizados corretamente quando os URLs contêm opções de amostra pré-selecionadas.
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758: resolução do problema de renderização de vídeo nas páginas de produto configuráveis

O patch ACSD-62758 corrige o problema em que vídeos de produtos nas páginas de detalhes do produto configuráveis não são renderizados corretamente quando URLs contêm opções de amostra pré-selecionadas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-62758. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os vídeos de produtos não são renderizados corretamente nas páginas de detalhes do produto configuráveis quando o URL inclui opções de amostra pré-selecionadas, resultando na exibição de uma imagem estática em vez do vídeo.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product].
1. Selecione o atributo **[!UICONTROL Color]** e edite-o.
1. Atualize as seguintes configurações:
   1. Defina [!UICONTROL Catalog Input Type for Store Owner] como [!UICONTROL Visual Swatch].
   1. Defina **[!UICONTROL Update Product Preview Image]** como **[!UICONTROL Yes]**.
1. Crie algumas opções para este atributo.
1. Crie uma nova categoria e adicione um novo produto configurável a ela, usando o atributo **[!UICONTROL Color]**.
1. Adicione uma única imagem aleatória ao produto principal.
1. Edite os produtos secundários configuráveis recém-criados e adicione um vídeo à galeria de mídia:
   1. Clique em **[!UICONTROL Add Video]** e use o URL do vídeo de teste: https://vimeo.com/12860646.
1. Salve o produto, limpe o cache e reindexe a loja.
1. Abra o produto recém-criado na loja, selecione uma das opções de amostra e confirme se o vídeo é carregado corretamente com o botão player exibido.
1. O vídeo deve ser carregado conforme esperado, e o botão do reprodutor deve ser exibido.
1. Agora, clique com o botão direito do mouse em uma das opções de amostra, selecione **[!UICONTROL Inspect]**, e localize o id do atributo e o id da opção. Copie a URL do produto e anexe o seguinte ao final dela: `www.product-url.com/producit-test#attribute_id=option_id`. Isso pré-selecionará a opção de amostra. Abra o URL atualizado em uma nova janela.

<u>Resultados esperados</u>:

O vídeo deve ser carregado corretamente, de modo semelhante a quando uma opção de amostra é selecionada manualmente.

<u>Resultados reais</u>:

Uma imagem estática é exibida em vez do vídeo. Os erros do console são registrados, indicando uma falha na inicialização do vídeo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.

