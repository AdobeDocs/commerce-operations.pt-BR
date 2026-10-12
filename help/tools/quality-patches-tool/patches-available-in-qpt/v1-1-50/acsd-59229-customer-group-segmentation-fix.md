---
title: 'ACSD-59229: Alocação incorreta de dados de grupo do cliente devido a um valor X-Magento-Vary desatualizado'
description: Aplique o patch ACSD-59229 para corrigir o problema do Adobe Commerce em que as informações relacionadas ao grupo de clientes são salvas no segmento errado devido a um valor X-Magento-Vary desatualizado na solicitação.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%
---
# ACSD-59229: Alocação incorreta de dados de grupo do cliente devido a um valor X-Magento-Vary desatualizado

O patch ACSD-59229 corrige o problema em que as informações relacionadas ao grupo de clientes são salvas no segmento errado devido a um valor X-Magento-Vary desatualizado na solicitação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-59229. Observe que o problema foi corrigido na versão 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As informações relacionadas ao grupo do cliente são salvas no segmento errado devido a um valor X-Magento-Vary desatualizado na solicitação.

<u>Pré-requisitos</u>:

Verifique se o Adobe Commerce B2B com dados de exemplo está instalado e se [!DNL Varnish] está configurado.

<u>Etapas a serem reproduzidas</u>:

1. Configurar preços avançados para o [!DNL SKU 24-MB01]:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Atacado* = *$200*
      * *Retailer* = *$30*

1. Crie duas contas de cliente.
1. Atribua ambos os clientes ao grupo **Atacado**.
1. Abra duas sessões diferentes do navegador e faça logon com cada cliente.
1. Navegue até a página do produto **[!UICONTROL 24-MB01]** para cada cliente e verifique se o preço exibido é *$200*.
1. Altere o grupo de clientes de um dos clientes para **Varejo**.
1. Limpe o cache usando o comando: `bin/magento cache:flush full_page`.
1. Atualize a página do produto de cada cliente.

<u>Resultados esperados</u>:

1. O cliente de varejo pode ver o preço correto de *$30* para o produto.
1. O cliente no atacado pode ver o preço correto do produto em *$200*.

<u>Resultados reais</u>:

1. O cliente de varejo pode ver o preço correto de *$30* para o produto.
1. O cliente grossista vê um preço incorreto de *$30* (preço de varejo) para o produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
