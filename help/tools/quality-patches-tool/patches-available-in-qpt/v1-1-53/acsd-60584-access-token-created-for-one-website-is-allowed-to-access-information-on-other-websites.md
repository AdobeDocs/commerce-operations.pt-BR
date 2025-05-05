---
title: "ACSD-60584: o token de acesso criado para um site tem permissão para acessar informações em outros sites"
description: Aplique o patch ACSD-60584 para corrigir o problema em que o token de acesso criado para o usuário em um site tem permissão para acessar ou alterar informações do cliente em outros sites.
feature: Customers, GraphQL
role: Admin, Developer
source-git-commit: eba4a8fd7bbf52fbc4295feab0d5bb79e7383b66
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584: o token de acesso criado para um site tem permissão para acessar informações em outros sites

O patch ACSD-60584 corrige o problema em que o token de acesso criado para o usuário em um site tem permissão para acessar ou alterar informações do cliente em outros sites. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) 1.1.53 está instalado. A ID do patch é ACSD-60584. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O token de API criado para o usuário em um site permite acessar informações do cliente, criar um carrinho e adicionar produtos ao carrinho em outras visualizações do site.

<u>Etapas a serem reproduzidas</u>:

1. Verifique se **[!DNL Share Customer Accounts configuration]** está definido como **[!UICONTROL Per Website]**.
1. Crie um *site*, *repositório* e *storeview* adicionais.
1. Crie dois clientes com o mesmo email no *site* principal e no *site* da etapa anterior.
1. Gere um token de cliente via [!DNL GraphQL] no site principal.
1. Usando o token gerado, envie uma consulta de cliente **[!DNL GraphQL]** com o segundo site no cabeçalho para recuperar informações do cliente.
1. Observe o resultado retornado.

<u>Resultados esperados</u>:

As informações do cliente do *site* principal são retornadas porque o token do *site* principal é usado na consulta [!DNL GraphQL].

<u>Resultados reais</u>:

As informações do cliente do segundo site são retornadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
