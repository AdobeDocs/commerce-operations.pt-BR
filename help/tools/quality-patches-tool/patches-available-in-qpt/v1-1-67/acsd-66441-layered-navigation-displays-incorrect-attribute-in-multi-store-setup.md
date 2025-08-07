---
title: 'ACSD-66441: a Navegação em camadas exibe opções de atributo incorretas na configuração de várias lojas'
description: Aplique o patch ACSD-66441 para corrigir o problema do Adobe Commerce, em que a Navegação em camadas exibe atributos de outros armazenamentos incorretamente em uma configuração de várias lojas.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5a8b30d1fac953ff5d921b7a7d3f12619b03bc81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# ACSD-66441: a Navegação em camadas exibe opções de atributo incorretas na configuração de várias lojas

O patch ACSD-66441 corrige o problema em que a Navegação em camadas exibe atributos de outros armazenamentos incorretamente em uma configuração de várias lojas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-66441. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A Navegação em camadas na loja inclui valores de atributo de outras lojas, mesmo quando esses produtos não estão disponíveis na visualização da loja atual.

<u>Etapas a serem reproduzidas</u>:

1. Crie um modo de exibição de site, loja e loja secundário.
1. Crie um produto configurável usando um atributo personalizado (por exemplo, tamanho).
1. Atribua o produto configurável ao site principal e a uma categoria.
1. Reindexar todos os dados.
1. Navegue até a categoria atribuída na loja. Todas as opções de tamanho são exibidas corretamente na Navegação em camadas.
1. Cancele a atribuição de dois produtos simples do site principal e atribua-os ao site secundário, ou remova-os do site principal.
1. Reindexar todos os dados.
1. Revise a página de categoria da loja e verifique a Navegação em camadas.

<u>Resultados esperados</u>:

A Navegação em camadas exibe somente as opções de atributo dos produtos atribuídos à loja ou ao site atual.

<u>Resultados reais</u>:

A Navegação em camadas exibe opções de atributo (tamanhos) de produtos atribuídos a outras lojas ou sites.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
