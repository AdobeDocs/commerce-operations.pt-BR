---
title: "MDVA-43718: o erro 'o consumidor não está autorizado a acessar recursos' aparece ao acessar o catálogo compartilhado"
description: O patch MDVA-43718 resolve o problema em que o erro *consumidor não está autorizado a acessar %resources.* é exibido ao acessar um catálogo compartilhado de uma integração personalizada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 está instalada. A ID do patch é MDVA-43718. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Catalog Management
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-43718: o erro &quot;o consumidor não está autorizado a acessar recursos&quot; aparece ao acessar o catálogo compartilhado

O patch MDVA-43718 resolve o problema em que o consumidor *do erro não está autorizado a acessar %resources.* aparece ao acessar um catálogo compartilhado de uma integração personalizada. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 está instalada. A ID do patch é MDVA-43718. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O seguinte erro é exibido ao acessar um catálogo compartilhado de uma integração personalizada: *O consumidor não está autorizado a acessar %resources*.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova integração por meio do Administrador > **Sistema** > **Integração** > **Adicionar Integração**.
1. Adicione acesso aos seguintes recursos e ative a integração:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::manage
   * Magento_Catalog::catálogo

1. Usando o acesso de integração: `rest/default/V1/sharedCatalog/1`

<u>Resultados esperados</u>:

Os detalhes do catálogo compartilhado são retornados.

<u>Resultados reais</u>:

O seguinte erro é retornado:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
