---
title: 'ACSD-63974: correções lentas [!UICONTROL Requisition List] no tempo de carregamento com paginação'
description: Aplique o patch ACSD-63974 para corrigir o problema em que a página [!UICONTROL Requisition List] leva muito tempo para carregar quando há muitos itens.
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974: correções lentas [!UICONTROL Requisition List] no tempo de carregamento com paginação

O patch ACSD-63974 corrige o problema em que a página **[!UICONTROL Requisition List]** leva muito tempo para carregar quando há muitos itens. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-63974. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A página **[!UICONTROL Requisition List]** leva muito tempo para carregar quando há muitos itens (mais de 2000). Isso se deve à ausência de paginação, fazendo com que todos os itens sejam carregados de uma só vez.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Defina **[!UICONTROL Enable Requisition List]** como *Sim*.
1. Gere mais de 2000 produtos editando o nó `simple_products` em `setup/performance-toolkit/profiles/ce/small.xml`.
1. Execute o comando:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Crie um cliente e faça logon.
1. Adicione todos os produtos ao **[!UICONTROL Requisition List]**.
1. Exiba **[!UICONTROL Requisition List]** na Loja.


<u>Resultados esperados</u>:

A página deve ser carregada dentro de um tempo razoável.


<u>Resultados reais</u>:

O tempo de carregamento da página aumenta com o número de itens, pois todos os itens são carregados de uma só vez devido à ausência de paginação.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
