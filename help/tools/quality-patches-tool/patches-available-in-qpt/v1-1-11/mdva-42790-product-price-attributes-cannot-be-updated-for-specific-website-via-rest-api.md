---
title: 'MDVA-42790: os atributos de preço do produto não podem ser atualizados para um site específico por meio da API REST'
description: O patch MDVA-42790 corrige o problema em que os usuários não conseguem atualizar atributos de preço do produto para sites específicos por meio da API REST. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 está instalada. A ID do patch é MDVA-42790. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: REST, Attributes, Orders, Products
role: Admin
exl-id: bb8dc764-d2d5-4e00-884a-2b4c1a567f58
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42790: os atributos de preço do produto não podem ser atualizados para um site específico por meio da API REST

O patch MDVA-42790 corrige o problema em que os usuários não conseguem atualizar atributos de preço do produto para sites específicos por meio da API REST. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 está instalada. A ID do patch é MDVA-42790. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não podem atualizar os atributos de preço do produto para sites específicos por meio da API REST.

<u>Etapas a serem reproduzidas</u>:

1. No Admin, vá para **Lojas** > **Configuração** > **Catálogo** > **Preço** > e defina o **Escopo do Preço do Catálogo** para o Site.
1. Atualizar preço especial de um produto empacotado usando a API REST, `POST rest/V1/products/`.

   ```JSON
   {
     "product": {
       "id": 46,
       "sku": "24-WG080",
       "name": "Sprite Yoga Companion Kit",
       "attribute_set_id": 4,
       "price": 10,
       "status": 1,
       "visibility": 1,
       "type_id": "bundle",
       "weight": 0,
       "custom_attributes": [
         {
           "attribute_code": "special_price",
           "value": "2"
         }
       ]
     }
   }
   ```

<u>Resultados esperados</u>:

O preço especial é atualizado para o produto em pacote quando o **Escopo do Preço de Catálogo** está definido como Site.

<u>Resultados reais</u>:

O preço especial não é atualizado para o produto em pacote quando o **Escopo do Preço de Catálogo** está definido como Site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
