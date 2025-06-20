---
title: 'ACSD-54472: os clientes de uma empresa rejeitada ainda podem autenticar'
description: Aplique o patch ACSD-54472 para corrigir o problema do Adobe Commerce em que os clientes de uma empresa rejeitada ainda podem se autenticar e os clientes de uma empresa bloqueada e rejeitada ainda podem fazer pedidos.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472: os clientes de uma empresa rejeitada ainda podem autenticar

O patch ACSD-54472 corrige o problema em que os clientes de uma empresa rejeitada ainda podem se autenticar e os clientes de uma empresa bloqueada e rejeitada ainda podem fazer pedidos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 está instalado. A ID do patch é ACSD-54472. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes de uma empresa rejeitada ainda podem se autenticar e os clientes de uma empresa bloqueada e rejeitada ainda podem fazer pedidos.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma empresa.
1. Adicionar produtos ao carrinho via [!DNL GraphQL].
1. Alterar o status da empresa para *Bloqueado*.
1. Envie uma solicitação [!DNL GraphQL] para fazer o pedido e criar uma cotação negociável.
1. Alterar o status da empresa para *Rejeitada*.
1. Envie uma solicitação [!DNL GraphQL] para obter o token de autorização do usuário da empresa.
1. Defina o status do cliente como *Inativo*.
1. Envie uma solicitação [!DNL GraphQL] para obter o token de autorização do usuário da empresa.

<u>Resultados esperados</u>:

* A ordem e a cotação negociável não foram feitas pelo usuário da empresa *Bloqueada*.
* O token de autorização não foi obtido para o usuário da empresa *Rejected*.
* O token de autorização não foi obtido para o cliente *Inativo*.

<u>Resultados reais</u>:

* A ordem e a cotação negociável foram feitas pelo usuário da empresa *Bloqueada*.
* O token de autorização é obtido para o usuário da empresa *Rejected*.
* O token de autorização é obtido para o cliente *Inativo*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
