---
title: 'MDVA-39181: Regras de produtos relacionados mostram produtos da categoria indefinida na regra'
description: O patch MDVA-39181 resolve o problema em que as regras de produto relacionadas mostram produtos de uma categoria não definida na regra. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-39181. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181: Regras de produtos relacionados mostram produtos da categoria indefinida na regra

O patch MDVA-39181 resolve o problema em que as regras de produto relacionadas mostram produtos de uma categoria não definida na regra. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-39181. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As regras de produtos relacionados mostram produtos de categorias não definidas na regra.

<u>Pré-requisitos</u>:

Instalar dados de amostra.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma marca de atributo e adicione-a ao **Conjunto de atributos principais**.
1. Escolha **Josie**, **Augusta** e **Ingrid** jaquetas para adicionar ao Brand Kitty de **Women** > **Tops** > **Jackets category**.
1. Escolha as **jaquetas Beaumont**, **Hyperion** e **Kenobi** para adicionar ao Brand Kitty em **Men** > **Tops** > **Categoria Jacket**.
1. Criar um produto relacionado com:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Produtos correspondentes:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Produtos a exibir:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Abra o SKU WJ04 no front-end e verifique os produtos relacionados.
1. Atualize a ID de categoria de **Mulheres** > **Tops** > **Jaquetas** caso seja diferente disso.

<u>Resultados esperados</u>:

Somente os produtos da mesma marca e da mesma categoria secundária são mostrados em produtos relacionados.

<u>Resultados reais</u>:

Os produtos relacionados são mostrados da mesma marca, mas a partir de uma categoria principal aleatória.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
