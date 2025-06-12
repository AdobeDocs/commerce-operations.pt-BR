---
title: 'ACSD-50849: a adição de novo produto após a limpeza do cache resulta em incompatibilidade'
description: Aplique o patch ACSD-50849 para corrigir o problema do Adobe Commerce em que adicionar um novo produto à categoria após limpar o cache resulta em uma incompatibilidade de posições e seleções dos produtos existentes.
feature: Cache, Categories, Products
role: Admin
exl-id: e7fd0614-eaa3-48ad-95ff-87f7ad3d76c1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-50849: a adição de novo produto após a limpeza do cache resulta em incompatibilidade

O patch ACSD-50849 corrige o problema em que a adição de um novo produto à categoria após a limpeza do cache resulta em uma incompatibilidade de posições e seleções dos produtos existentes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) QPT 1.1.32 está instalado. A ID do patch é ACSD-50849. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Adicionar um novo produto à categoria depois de limpar o cache resulta em uma incompatibilidade de posições e seleções dos produtos existentes.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos.
1. Atribuir um produto a uma categoria.
1. Abra a categoria do administrador.
1. Limpar o cache `bin/magento cache:flush`.
1. Adicione o segundo produto à categoria.

<u>Resultados esperados</u>:

Os produtos existentes atribuídos na categoria não são removidos automaticamente.

<u>Resultados reais</u>:

O primeiro produto (existente) é removido automaticamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
