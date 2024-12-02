---
title: 'MDVA-39993: As alterações de inventário feitas por meio da API não são refletidas na loja'
description: O patch MDVA-39993 resolve o problema em que as alterações de inventário feitas por meio da API não são refletidas na loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-39993. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993: As alterações de inventário feitas por meio da API não são refletidas na loja

O patch MDVA-39993 resolve o problema em que as alterações de inventário feitas por meio da API não são refletidas na loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-39993. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.3.7-p2 e 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As alterações de inventário feitas por meio da API não são refletidas na página do produto da loja.

<u>Pré-requisitos</u>:

Módulos de inventário instalados.

<u>Etapas a serem reproduzidas</u>:

1. Verifique se a fila está definida para execução com o cron e se o cron está instalado e em execução.
1. Crie um produto configurável (COC001), com duas cores (preto e vermelho) e dois tamanhos (M e L).
1. Faça uma opção em estoque (COC001-Red-M).
1. Carregue a página do produto configurável na vitrine e tente clicar em cada cor. Ao clicar em **Vermelho**, o tamanho **M** deve ser riscado porque está esgotado.
1. Faça o COC001-Red-M em estoque usando o seguinte endpoint de API e a carga:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Verifique esse produto simples no back-end e verifique se ele foi atualizado para Em estoque.
1. Carregue o produto configurável do front-end e clique em cada cor. Observe o tamanho **M** ao clicar em **Vermelho**.

<u>Resultados esperados</u>:

A opção COC001-Red-M não é riscada porque foi atualizada para Em estoque pela API.

<u>Resultados reais</u>:

A opção COC001-Red-M ainda está riscada, mesmo que esteja em estoque.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
