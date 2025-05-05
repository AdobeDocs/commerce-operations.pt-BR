---
title: 'ACSD-62591: o tema não muda quando **[!UICONTROL User Agent Rules]** é configurado'
description: Aplique o patch ACSD-62591 para corrigir o problema do Adobe Commerce em que o tema não muda corretamente quando o **[!UICONTROL User Agent Rules]** é configurado.
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# ACSD-62591: O tema não muda corretamente quando [!UICONTROL User Agent Rules] é configurado

O patch ACSD-62591 corrige o problema em que o tema não muda corretamente quando o **[!UICONTROL User Agent Rules]** é configurado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-62591. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O tema não muda corretamente quando os **[!UICONTROL User Agent Rules]** são configurados.

<u>Etapas a serem reproduzidas</u>:

1. Abra o Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Editar um tema de exibição da loja.
1. Defina `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` em **[!UICONTROL User Agent Rules]** e escolha um tema diferente.
1. Salve as alterações e limpe os caches.
1. Abra uma página da Loja em um dispositivo móvel.
1. Abra a mesma página em um navegador do desktop.

<u>Resultados esperados</u>:

O navegador da área de trabalho e o dispositivo móvel exibem páginas usando seus respectivos temas.

<u>Resultados reais</u>:

O navegador do desktop exibe a página em cache com o tema móvel.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.

