---
title: 'ACSD-62629: a lista de produtos em widgets mostra categorias incorretas'
description: Aplique o patch ACSD-62629 para corrigir o problema do Adobe Commerce em que uma lista de produtos usada em widgets não respeita a condição de categoria.
feature: Page Content
role: Admin, Developer
exl-id: a7d6bd43-4b8b-48c4-ae9a-4093ac3a4110
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-62629: a lista de produtos em widgets mostra categorias incorretas

O patch ACSD-62629 corrige o problema em que a lista de produtos usada em widgets não respeita a condição de categoria. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-62629. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A lista de produtos usada em widgets não respeita a condição da categoria.

<u>Etapas a serem reproduzidas</u>:

1. Crie um [!UICONTROL simple product] chamado TEST e adicione-o à Categoria 1.
1. Crie uma atualização de preparo sem uma data de término para o produto TEST. Aguarde até que a atualização se torne ativa.
1. Crie um [!UICONTROL configurable product] chamado TESTE 2 com dois produtos derivados e adicione-o à Categoria 2.
1. Crie outro [!UICONTROL simple product] chamado TESTE 5 e adicione-o à Categoria 1.
1. Executar uma reindexação completa.
1. Navegue até **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** e edite a home page.
1. Adicione um widget [!UICONTROL Products] com *[!UICONTROL Appearance]* definido como *[!UICONTROL Product Carousel]* e *[!UICONTROL Category]* definido como Categoria 2. Salve a página.
1. Vá para o front-end e abra a home page.

<u>Resultados esperados</u>:

Somente o produto TEST 2 (configurável) deve estar presente na página.

<u>Resultados reais</u>:

Ambos os produtos TEST 5 (simples) e TEST 2 (configurável) estão presentes na página.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
