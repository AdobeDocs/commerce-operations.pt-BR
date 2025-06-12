---
title: 'ACSD-60788: scripts personalizados para  [!DNL Google Tag Manager]  não executados devido a erros de CSP'
description: Aplique o patch ACSD-60788 para corrigir o problema do Adobe Commerce em que os scripts personalizados para  [!DNL Google Tag Manager]  não são executados devido a erros de Política de Segurança de Conteúdo (CSP).
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788: scripts personalizados para [!DNL Google Tag Manager] não são executados devido a erros de Política de Segurança de Conteúdo

O patch ACSD-60788 corrige o problema em que scripts personalizados para [!DNL Google Tag Manager] não são executados devido a erros de Política de segurança de conteúdo. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 está instalado. A ID do patch é ACSD-60788. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os scripts personalizados para [!DNL Google Tag Manager] não são executados devido a erros da Política de Segurança de Conteúdo (CSP).

<u>Etapas a serem reproduzidas</u>:

1. Configure a variável *[!DNL Google Tag Manager]*.
1. Configure a Marca HTML Personalizada *[!DNL Google Tag Manager]*.
1. Coloque o seguinte código JavaScript na primeira tag:

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Limpar caches após configurar o *GTM*.
1. Abra o console do desenvolvedor no navegador.
1. Abra a Página inicial.

<u>Resultados esperados</u>:

O console de desenvolvimento do navegador exibe *Nonce de JS simples (caracteres aleatórios)*.

<u>Resultados reais</u>:

O console de desenvolvimento do navegador exibe *Nonce de JS simples indefinido*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
