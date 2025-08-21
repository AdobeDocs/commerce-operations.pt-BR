---
title: 'ACSD-66965: a opção [!UICONTROL Print] na página [!UICONTROL Requisition List] causa um erro'
description: Aplique o patch ACSD-66965 para corrigir um problema no Adobe Commerce em que a opção [!UICONTROL Print] na página [!UICONTROL Requisition List] causa um erro.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965: a opção **[!UICONTROL Print]** na página **[!UICONTROL Requisition List]** causa um erro

O patch ACSD-66965 corrige o problema em que a opção **[!UICONTROL Print]** na página **[!UICONTROL Requisition List]** causa um erro. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66965. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A opção **[!UICONTROL Print]** na página **[!UICONTROL Requisition List]** causa um erro devido a uma referência de objeto nulo em `Grid.php`.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Defina **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** e **[!UICONTROL Enable Requisition List]** como `Yes`.
1. Crie dois produtos simples.
1. Faça logon na loja e abra a página **[!UICONTROL My Account]**.
1. Criar uma lista de requisições.
1. Atribuir ambos os produtos à lista de requisições.
1. Acesse a lista de requisições e liste os produtos.
1. Clique em **[!UICONTROL Print]**.

<u>Resultados esperados</u>:

A opção **[!UICONTROL Print]** na página **[!UICONTROL Requisition List]** exibe a visualização de impressão sem erros.

<u>Resultados reais</u>:

A seguinte mensagem de erro é exibida: *Ocorreu um erro durante a execução do aplicativo. Consulte o log de exceções para obter detalhes.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
