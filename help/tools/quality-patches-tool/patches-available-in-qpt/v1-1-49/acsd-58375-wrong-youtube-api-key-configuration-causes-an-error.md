---
title: 'ACSD-58375: a chave de API do YouTube configurada incorretamente causa erro ao adicionar vídeo no nível de exibição da loja'
description: Aplique o patch ACSD-58375 para corrigir o problema do Adobe Commerce em que uma configuração incorreta da chave de API do YouTube causa um erro ao adicionar um vídeo do YouTube no nível de exibição da loja.
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-58735: a chave de API do YouTube configurada incorretamente causa erro ao adicionar vídeo no nível de exibição da loja

O patch ACSD-58735 corrige o problema em que uma configuração incorreta da chave de API do YouTube causa um erro ao adicionar um vídeo do YouTube no nível de exibição da loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 está instalado. A ID do patch é ACSD-58735. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma configuração incorreta da chave de API do YouTube causa um erro ao adicionar um vídeo do YouTube no nível de visualização da loja.

<u>Etapas a serem reproduzidas</u>:

1. Vá para Admin > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Alterar o *Escopo* para o nível *[!UICONTROL Main Website]*.
1. Adicione a chave da API do YouTube.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Selecione qualquer produto e navegue até *[!UICONTROL Images and Video]*. Clique em **[!UICONTROL Add Video]**.
1. Copie um link de vídeo do YouTube e cole-o no campo de link do vídeo. Saia do campo.

<u>Resultados esperados</u>:

A chave de API do YouTube tem um escopo global e está oculta no nível do site.

<u>Resultados reais</u>:

O seguinte erro é lançado: *O vídeo não é mostrado devido ao seguinte motivo: a chave de API não é válida. Passe uma chave de API válida*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
