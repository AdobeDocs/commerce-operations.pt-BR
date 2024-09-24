---
title: "MDVA-38728: alterar a visibilidade do produto cria regravação de URL para o site principal"
description: O patch MDVA-38728 resolve o problema em que a alteração da visibilidade do produto do segundo site cria uma reescrita de URL para o site principal. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-38728. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-38728: Alterar a visibilidade do produto cria regravação de URL para o site principal

O patch MDVA-38728 resolve o problema em que a alteração da visibilidade do produto do segundo site cria uma reescrita de URL para o site principal. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-38728. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Alterar a visibilidade do produto do segundo site cria uma reescrita de URL para o site principal.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site, uma loja e uma loja adicionais.
1. Crie um produto simples.
1. Defina a visibilidade como **Não visível individualmente**.
1. Atribuir o produto somente ao segundo site.
1. Preencha todos os outros campos obrigatórios.
1. Salve o produto.
1. Iniciar filas MySQL:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Vá para a Lista de produtos.
1. Selecione o produto criado e atualize o atributo de visibilidade usando a atualização em massa para Catálogo e Pesquisa.
1. Verifique a regravação do URL.

<u>Resultados esperados</u>:

A regravação é criada para o segundo site ao qual o produto é atribuído.

<u>Resultados reais</u>:

A regravação é criada para o site principal.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
