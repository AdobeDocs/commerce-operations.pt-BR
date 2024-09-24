---
title: "MDVA-38393: As regras do catálogo param de funcionar para o produto configurável se seu produto simples for renomeado"
description: O patch MDVA-38393 corrige o problema em que as regras de catálogo param de funcionar para um produto configurável se seu produto simples for renomeado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 está instalada. A ID do patch é MDVA-38393. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393: As regras do catálogo param de funcionar para o produto configurável se seu produto simples for renomeado

O patch MDVA-38393 corrige o problema em que as regras de catálogo param de funcionar para um produto configurável se seu produto simples for renomeado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 está instalada. A ID do patch é MDVA-38393. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As regras do catálogo param de funcionar para um produto configurável se seu produto simples for renomeado.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com um produto simples associado.
1. Crie uma categoria.
1. Atribua somente o produto configurável à nova categoria.
1. Criar novas regras de catálogo:
   * Condição = A categoria contém \&lt;nova id de categoria>
   * Ação = 50% de desconto
   * Ativo = Sim
1. Executar reindexação.
1. Verifique o produto configurável no front-end (o desconto deve ser aplicado).
1. Verifique a tabela `catalogrule_product` (o produto simples deve ter um desconto).
1. Acesse o Administrador e altere o nome do produto simples. Isso adicionaria um registro à tabela `catalogrule_product_cl`.
1. Execute o cron ou o comando `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`.
1. Verifique a tabela `catalogrule_product`.

<u>Resultados esperados</u>:

O produto configurável tem um desconto.

<u>Resultados reais</u>:

* Os registros de desconto criados para os produtos simples estão ausentes na tabela `catalogrule_product`.
* O produto configurável no front-end tem o preço original completo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
