---
title: 'ACSD-50895: [!DNL Google Analytics] 3 marcas GTM não são acionadas se o GTM [!DNL Google Analytics] 4 não estiver configurado'
description: Aplique o patch ACSD-50895 para corrigir o problema do Adobe Commerce em que as tags GTM  [!DNL Google Analytics] 3 não são acionadas se o GTM [!DNL Google Analytics] 4 não estiver configurado.
role: Admin
exl-id: 871e2ca1-dc10-435c-9325-62f5b9b673ad
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 marcas GTM não são acionadas se [!DNL Google Analytics] 4 GTM não estiver configurado

O patch ACSD-50895 corrige o problema em que [!DNL Google Analytics] 3 marcas GTM não são acionadas se [!DNL Google Analytics] 4 GTM não estiver configurado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 está instalado. A ID do patch é ACSD-50895. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL Google Analytics] 3 marcas GTM não serão acionadas se [!DNL Google Analytics] 4 GTM não estiver configurado.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como um usuário administrador.
1. Habilitar **[!DNL Google Analytics 3]** e **[!DNL Google Tag Manager]** em **Admin** > **Store** > **Configuração** > **Vendas** > **API Google** > **Google Analytics**.
1. Não habilite o **[!DNL Google Analytics 4]** e o **[!DNL Google Tag Manager]**.
1. Abra a página do produto na Loja.

<u>Resultados esperados</u>:

As marcas GTM são acionadas quando apenas **[!DNL Google Analytics]** 3 GTM está habilitado.

<u>Resultados reais</u>:

As marcas GTM não são acionadas quando o **[!DNL Google Analytics]** 4 GTM está desabilitado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
