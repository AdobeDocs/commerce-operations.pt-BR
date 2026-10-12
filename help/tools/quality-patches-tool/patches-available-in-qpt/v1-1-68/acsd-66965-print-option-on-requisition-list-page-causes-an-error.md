---
title: 'ACSD-66965: a opção [!UICONTROL Print] na página [!UICONTROL Requisition List] causa um erro'
description: Aplique o patch ACSD-66965 para corrigir um problema no Adobe Commerce em que a opção [!UICONTROL Print] na página [!UICONTROL Requisition List] causa um erro.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: ccd0920a-074c-4851-a45a-09c43b04fe64
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '338'
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

```text
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
