---
title: 'ACSD-64111: corrige o erro *InvalidArgumentException: a classe não existe* ao definir condições aninhadas para um componente Produto em  [!DNL Page Builder]'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111: corrige o erro *InvalidArgumentException: a classe não existe* ao definir condições aninhadas para um componente Produto em [!DNL Page Builder]

O patch ACSD-64111 corrige o problema em que *InvalidArgumentException: classe não existe* erro ocorre em `vendor/magento/module-rule/Model/ConditionFactory.php:50` ao definir condições aninhadas para um componente Produto em [!DNL Page Builder]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 está instalado. A ID do patch é ACSD-64111. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação)  2.4.6-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro *InvalidArgumentException: a classe não existe em /app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php* é lançada ao adicionar uma *[!UICONTROL Conditions Combination]* em [!DNL Page Builder] condição do widget Produtos.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no administrador do Adobe Commerce.
1. Vá para **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Adicionar uma nova página (ou editar uma página existente).
1. Expanda a seção **[!UICONTROL Content]** e clique em **[!UICONTROL Edit with Page Builder]**.
1. Adicione uma nova linha e depois o widget **[!UICONTROL Products]**.
1. Configurar o widget **[!UICONTROL Products]**.
1. Selecione o **[!UICONTROL Condition]** em **[!UICONTROL Select Products By]**.
1. Adicione uma nova condição e selecione **[!UICONTROL Conditions Combination]** na lista suspensa.

<u>Resultados esperados</u>:

Nenhum erro nos logs.

<u>Resultados reais</u>:

A exceção abaixo é registrada nos logs:

*report.CRITICAL: InvalidArgumentException: a classe não existe em vendor/magento/module-rule/Model/ConditionFactory.php:50*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
