---
title: 'ACSD-62708: o tamanho da fonte do editor  [!DNL TinyMCE] 7 no painel do administrador mostra PT'
description: Aplique o patch ACSD-62708 para corrigir o problema do Adobe Commerce em que o tamanho da fonte do editor do  [!DNL TinyMCE] 7 no administrador mostra PT e não PX. Agora, você também pode definir o tamanho da fonte em PX em vez de PT.
feature: Admin Workspace
role: Admin, Developer
exl-id: 037a5831-dbc7-4834-ab8e-9b1f765b92b2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-62708: tamanho da fonte do editor do [!DNL TinyMCE] 7 no painel de administração mostra PT

O patch ACSD-62708 resolve o problema em que o tamanho da fonte do editor do [!DNL TinyMCE] 7 no painel de administração é exibido em PT em vez de PX. Este patch permite que você defina o tamanho da fonte em PX. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-62708. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O editor do [!DNL TinyMCE] 7 no painel de administração exibe o tamanho da fonte em PT em vez de PX.

<u>Etapas a serem reproduzidas</u>:

1. Abra a página de edição do produto no painel de administração.
1. Expanda a seção [!UICONTROL Content].
1. Verifique os controles de fonte no editor [!DNL TinyMCE].

<u>Resultados esperados</u>:

O tamanho da fonte deve estar em PX.

<u>Resultados reais</u>:

O tamanho da fonte está em PT.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
