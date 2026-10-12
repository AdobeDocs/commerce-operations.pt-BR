---
title: 'ACSD-64684: erro de validação ao salvar um cartão-presente com um valor superior a 999 devido à vírgula em mil (1.000)'
description: Aplique o patch ACSD-64684 para corrigir o problema do Adobe Commerce em que ocorre um erro de validação ao salvar um cartão-presente com um valor superior a 999 devido à vírgula em "mil" (1.000).
feature: Catalog Management
role: Admin, Developer
exl-id: 327c5d28-b52c-4da9-a905-8a3deb755241
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
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
source-wordcount: '378'
ht-degree: 0%
---
# ACSD-64684: erro de validação ao salvar um cartão-presente com um valor superior a 999 devido à vírgula em mil (1.000)

O patch ACSD-64684 corrige o problema em que um erro de validação ocorre ao salvar um cartão-presente com um valor superior a 999 devido à vírgula em &quot;mil&quot; (1.000). Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-64684. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro de validação ao editar e salvar um cartão-presente com um valor maior que 999 devido à vírgula (separador de milhar) no número, como &quot;mil&quot; (1.000).

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto de cartão-presente.
   1. Digite 1.000 como [!UICONTROL Amount].
   1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

* O novo vale-presente com uma quantia de 1.000 é salvo.

<u>Resultados reais</u>:

* Ocorre um erro de validação quando o valor do cartão-presente é maior que 999.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
