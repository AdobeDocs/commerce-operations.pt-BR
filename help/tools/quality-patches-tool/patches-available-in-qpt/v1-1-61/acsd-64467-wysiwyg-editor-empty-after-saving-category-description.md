---
title: 'ACSD-64467: WYSIWYG editor vazio após salvar categoria descrição em armazenamento nível de visualização'
description: Aplicar o ACSD-64467 correção para corrigir o problema Comércio Adobe Systems em que o editor WYSIWYG aparece vazio depois de salvar uma descrição categoria no nível armazenamento visualização.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
source-git-commit: b71447d5dac3208e537b29204dc8d47e8838f584
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: WYSIWYG editor vazio após salvar categoria descrição em armazenamento nível de visualização

O patch ACSD-64467 corrige o problema em que o editor do WYSIWYG aparece vazio após salvar uma descrição de categoria no nível de exibição da loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-64467. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o correção é compatível com a sua Adobe Systems versão Comércio, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade em [[!DNL Quality Patches Tool]: Search para patches página](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID da correção como palavra-chave de pesquisa para localizar a correção.

## Questão

O editor do WYSIWYG aparece vazio após salvar uma descrição de categoria no nível de exibição de loja.

<u>Etapas a serem reproduzidas</u>:

1. Edite uma categoria no Administrador do Commerce no nível de visualização da loja.
1. Desmarque a caixa de seleção *[!UICONTROL Use default value]* ao lado da descrição da categoria.
1. Insira uma descrição no editor do WYSIWYG.
1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

A descrição é salva e exibida corretamente.

<u>Resultados reais</u>:

A descrição fica vazia após o recarregamento do página.

## Aplicar o correção

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
