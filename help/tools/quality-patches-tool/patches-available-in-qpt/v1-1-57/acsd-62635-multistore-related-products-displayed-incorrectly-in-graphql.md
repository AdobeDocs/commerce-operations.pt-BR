---
title: 'ACSD-62635: produtos relacionados a várias lojas exibidos incorretamente em [!DNL GraphQL]'
description: Aplique o patch ACSD-62635 para corrigir o problema do Adobe Commerce em que os produtos relacionados a várias lojas não são exibidos corretamente na consulta de produto do [!DNL GraphQL].
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '417'
ht-degree: 0%
---
# ACSD-62635: produtos relacionados a várias lojas exibidos incorretamente em [!DNL GraphQL]

O patch ACSD-62635 corrige o problema em que produtos relacionados a várias lojas não são exibidos corretamente na consulta de produto do [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) 1.1.57 está instalado. A ID do patch é ACSD-62635. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando B2B está habilitado, a solicitação [!DNL GraphQL] retorna todos os produtos relacionados de todos os sites, mesmo se um escopo de exibição de loja for usado na solicitação.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites, lojas e visualizações de loja.
1. Crie os seguintes produtos simples:
   * Um principal com SKU *product1* atribuído a todos os sites
   * Um atribuído somente ao *Site 1*
   * Um atribuído somente ao *Site 2*
   * Um atribuído ao *Site 1* e ao *Site 2*
1. Adicione todos os produtos relacionados ao *produto1*.
1. Habilitar [!UICONTROL B2B] e [!UICONTROL Shared Catalog].
1. Adicione todos os produtos ao catálogo compartilhado padrão.
1. Envie a solicitação [!DNL GraphQL] para recuperar o *produto1* e seus produtos relacionados com o código de armazenamento do *Site 1* no cabeçalho.

<u>Resultados esperados</u>:

A resposta contém produtos relacionados somente dos sites que correspondem ao código da loja enviado no cabeçalho da solicitação.

<u>Resultados reais</u>:

A resposta contém todos os produtos relacionados de todos os sites, independentemente do código da loja especificado na solicitação.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
