---
title: 'ACSD-64467: editor do WYSIWYG vazio após salvar a descrição da categoria no nível de exibição da loja'
description: Aplique o patch ACSD-64467 para corrigir o problema do Adobe Commerce em que o editor do WYSIWYG aparece vazio após salvar uma descrição de categoria no nível de exibição da loja.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
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
source-wordcount: '339'
ht-degree: 0%
---
# ACSD-64467: editor do WYSIWYG vazio após salvar a descrição da categoria no nível de exibição da loja

O patch ACSD-64467 corrige o problema em que o editor do WYSIWYG aparece vazio após salvar uma descrição de categoria no nível de exibição da loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-64467. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O editor do WYSIWYG aparece vazio após salvar uma descrição de categoria no nível de exibição de loja.

<u>Etapas a serem reproduzidas</u>:

1. Edite uma categoria no Administrador do Commerce no nível de visualização da loja.
1. Desmarque a caixa de seleção *[!UICONTROL Use default value]* ao lado da descrição da categoria.
1. Insira uma descrição no editor do WYSIWYG.
1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

A descrição é salva e exibida corretamente.

<u>Resultados reais</u>:

A descrição fica vazia após o recarregamento da página.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
