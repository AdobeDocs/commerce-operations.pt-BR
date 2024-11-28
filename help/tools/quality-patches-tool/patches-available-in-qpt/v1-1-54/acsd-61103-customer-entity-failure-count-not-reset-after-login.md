---
title: "ACSD-61103: contagem de falhas não redefinida para zero após o logon bem-sucedido do cliente por meio da API"
description: Aplique o patch ACSD-61103 para corrigir o problema do Adobe Commerce em que a contagem de falhas na tabela "customer_entity" não é redefinida para zero depois que um cliente faz logon por meio de endpoints da API.
feature: GraphQL, REST, Customers
role: Admin, Developer
source-git-commit: d53b747c3b2021e842647de5371a5f0f2a760f09
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-61103: Contagem de falhas não redefinida para zero após o logon bem-sucedido do cliente por meio da API

O patch ACSD-61103 resolve o problema em que a contagem de falhas na tabela `customer_entity` não é redefinida para zero depois que um cliente faz logon por meio de pontos de extremidade de API. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-61103. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A contagem de falhas na tabela `customer_entity` não é redefinida para zero mesmo depois que um cliente faz logon com êxito por meio de pontos de extremidade de API.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente.
1. Gerar um token do cliente por meio da API, usando detalhes incorretos.
1. Verifique a coluna `failures_num` na tabela do banco de dados `customer_entity` para o cliente acima.
1. Gere um token do cliente por meio da API, usando os detalhes corretos.
1. Verifique a coluna `failures_num` na tabela do banco de dados `customer_entity` para o cliente acima.

<u>Resultados esperados</u>:

A coluna `failures_num` deve ser redefinida como 0 depois de usar as credenciais corretas para gerar um token de cliente por meio da API.

<u>Resultados reais</u>:

A coluna `failures_num` não é redefinida como 0 depois de usar as credenciais corretas para gerar um token de cliente por meio da API.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.

