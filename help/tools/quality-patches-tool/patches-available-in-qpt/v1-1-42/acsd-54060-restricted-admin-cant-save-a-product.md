---
title: 'ACSD-54060: O administrador restrito não pode salvar o produto se ele for filho de outro produto'
description: Aplique o patch ACSD-54060 para corrigir o problema do Adobe Commerce em que um administrador restrito não pode salvar um produto se ele for filho de outro produto atribuído a um escopo diferente.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 2af24cbf-65a1-4bd6-aad3-19b613bee7f2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-54060: O administrador restrito não pode salvar o produto se ele for filho de outro produto

O patch ACSD-54060 corrige o problema em que um administrador restrito não pode salvar um produto se ele for filho de outro produto atribuído a um escopo diferente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 está instalado. A ID do patch é ACSD-54060. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um administrador restrito não poderá salvar um produto se ele for filho de outro produto atribuído a um escopo diferente.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site adicional.
1. Crie um produto simples e atribua-o a ambos os sites.
1. Crie um produto configurável com o produto simples como a única variação e atribua o produto configurável somente ao site padrão.
1. Crie um usuário administrador restrito com acesso somente ao segundo site.
1. Faça logon como o usuário administrador restrito.
1. Tente alterar o nome do produto simples no escopo do segundo site.

<u>Resultados esperados</u>:

O administrador restrito pode alterar o nome do produto.

<u>Resultados reais</u>:

Erro: *São necessárias mais permissões para exibir este item*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
