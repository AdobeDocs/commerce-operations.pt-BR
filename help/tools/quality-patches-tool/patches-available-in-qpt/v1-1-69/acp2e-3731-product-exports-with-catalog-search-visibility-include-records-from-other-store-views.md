---
title: 'ACP2E-3731: Exportações de produtos com visibilidade [!UICONTROL Catalog, Search] incluem registros de outras exibições de loja'
description: Aplique o patch ACP2E-3731 para corrigir o Adobe Commerce em que as exportações de produtos com o filtro de visibilidade definido como [!UICONTROL Catalog, Search] incluem linhas incorretas em configurações de várias lojas devido a variações de atributo no escopo do armazenamento.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731: Exportações de produtos com visibilidade [!UICONTROL Catalog, Search] incluem registros de outras exibições de loja

O patch ACP2E-3731 corrige o problema em que exportações de produtos com visibilidade *[!UICONTROL Catalog, Search]* incluem incorretamente registros de outras exibições de loja em ambientes de várias lojas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACP2E-3731. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p9

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Exportações de produtos incluem linhas incorretas quando o filtro de visibilidade está definido como *[!UICONTROL Catalog, Search]* em configurações de várias lojas devido a variações de atributo no escopo do armazenamento.

<u>Etapas a serem reproduzidas</u>:

1. No painel Admin, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** para criar um site, loja e exibição de loja adicionais.
1. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**. Clique em **[!UICONTROL Add Attribute Set]** para criar um atributo. Definir **[!UICONTROL Based On]** como *Padrão*.
1. Crie um produto e atribua-o ao site principal e ao site secundário.
1. Defina um valor de texto para o atributo recém-criado com **[!UICONTROL Scope]** definido como *Todas as Exibições de Repositório*.
1. Altere o escopo para a exibição de armazenamento secundário e atualize o atributo com um valor diferente.
1. Altere o escopo para o modo de exibição de armazenamento padrão e o modo de exibição de armazenamento secundário, e defina a visibilidade do produto como *Não Visível Individualmente*.
1. Vá para **[!UICONTROL System]** > **[!UICONTROL Export]** e selecione *Produtos* no menu suspenso.
1. Defina um filtro em que **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]* e clique em **[!UICONTROL Continue]**.
1. Execute o seguinte comando para processar a exportação:

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. Verifique o arquivo exportado.

<u>Resultados esperados</u>:

Somente os registros filtrados são exportados.

<u>Resultados reais</u>:

O arquivo exportado inclui uma linha para a exibição de armazenamento secundário, que não corresponde aos critérios de filtro definidos durante a exportação.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
