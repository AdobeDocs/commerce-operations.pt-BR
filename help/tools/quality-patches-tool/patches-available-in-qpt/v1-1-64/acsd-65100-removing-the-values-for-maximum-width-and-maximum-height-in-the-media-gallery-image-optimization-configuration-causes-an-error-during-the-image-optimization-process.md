---
title: 'ACSD-65100: a remoção dos valores [!UICONTROL Maximum Width] e [!UICONTROL Maximum Height] na configuração [!UICONTROL Media Gallery Image Optimization] causa um erro'
description: Aplique o patch ACSD-65100 para corrigir o problema do Adobe Commerce em que a remoção dos valores [!UICONTROL Maximum Width] e [!UICONTROL Maximum Height] na configuração [!UICONTROL Media Gallery Image Optimization] causa um erro durante o processo de otimização de imagem.
feature: Media
role: Admin, Developer
source-git-commit: 97ffcd84b760962e1ad7290343f81860ca6568c7
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACSD-65100: a remoção dos valores [!UICONTROL Maximum Width] e [!UICONTROL Maximum Height] na configuração [!UICONTROL Media Gallery Image Optimization] causa um erro

O patch ACSD-65100 corrige o problema em que a remoção dos valores **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]** na configuração **[!UICONTROL Media Gallery Image Optimization]** causa um erro durante o processo de otimização de imagem. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACSD-65100. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro durante o processo de otimização de imagem quando os valores de **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]** são removidos na configuração **[!UICONTROL Media Gallery Image Optimization]**.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**.
1. Remova os valores de **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]**.
1. Limpe o cache de configuração.
1. Navegue até **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Abra qualquer página para edição.
1. Na área de conteúdo:
   1. Selecione **[!UICONTROL Add Layout]** > **[!UICONTROL Row]**.
   1. Selecione **[!UICONTROL Add Elements]** > **[!UICONTROL Text]**.
   1. No editor do WYSIWYG, clique em **[!UICONTROL Add Image]**.
   1. Carregue uma imagem e selecione **[!UICONTROL Add Selected]**.
1. Verifique o arquivo `var/log/exception.log`.

<u>Resultados esperados</u>:

Nenhum erro.

<u>Resultados reais</u>:

Um erro semelhante ao seguinte é registrado:

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
