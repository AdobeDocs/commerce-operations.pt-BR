---
title: "ACSD-54983: UID do usuário da empresa com GraphQL não disponível com usuário inativo"
description: Aplique o patch ACSD-54983 para corrigir o problema do Adobe Commerce em que não é possível obter o usuário da empresa UID com a solicitação do GraphQL quando o status do usuário está definido como inativo.
feature: GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983: UID do usuário da empresa com GraphQL não disponível com usuário inativo

O patch ACSD-54983 corrige o problema em que não é possível obter o usuário da empresa UID com a solicitação do GraphQL quando o status do usuário está definido como inativo. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 está instalado. A ID do patch é ACSD-54983. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Não é possível obter a solicitação do usuário da empresa UID com GraphQL quando o status do usuário está definido como inativo.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma empresa com um usuário administrador. Por exemplo, company@test.com.
1. Crie um novo cliente.
1. Atribua o novo cliente a uma empresa.
1. Obter um **[!UICONTROL company admin token]**.
1. Usando o **[!UICONTROL company admin token]**, busque a estrutura da empresa. Consulte [Retornar a estrutura da empresa](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) na documentação do desenvolvedor.
1. A resposta contém apenas *CLIENTES ATIVOS* com suas IDs.
1. Atualize o usuário da empresa para *INATIVO*.
1. Procure a estrutura da empresa novamente.

<u>Resultados esperados</u>:

É possível obter o UID do usuário da empresa quando o status está definido como inativo.

<u>Resultados reais</u>:

Os clientes inativos não estão na lista. Não é possível obter o UID do usuário da empresa quando o status está definido como inativo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
