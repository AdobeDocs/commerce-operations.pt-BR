---
title: 'ACSD-62671: [!DNL GraphQL] não retorna o endereço atualizado na primeira tentativa'
description: Aplique o patch ACSD-62671 para corrigir o problema do Adobe Commerce em que uma solicitação  [!DNL GraphQL]  não retorna informações de endereço atualizadas na primeira tentativa.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL] não retorna o endereço atualizado na primeira tentativa

O patch ACSD-62671 corrige o problema em que uma solicitação do [!DNL GraphQL] não retorna informações de endereço atualizadas na primeira tentativa. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) 1.1.57 está instalado. A ID do patch é ACSD-62671. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao usar o [!DNL GraphQL Application Server], a solicitação de endereço do cliente não retorna os dados mais recentes.

<u>Etapas a serem reproduzidas</u>:

1. Instalar e iniciar [!DNL GraphQL Application Server].
1. Verifique se o tipo de cache `graphQL_query_resolver_result` está habilitado.
1. Use [!DNL GraphQL] para:

   * Crie um cliente.
   * Gerar um token.
   * Use o token para criar vários endereços para o cliente acima.

1. Envie a solicitação [!DNL GraphQL] para obter os endereços do cliente.
1. Adicione um novo endereço ao cliente.
1. Repita a solicitação da Etapa #4 várias vezes enquanto monitora a contagem de endereços retornados na resposta.

<u>Resultados esperados</u>:

A resposta [!DNL GraphQL] contém o número correto de endereços de clientes.

<u>Resultados reais</u>:

Ocasionalmente, um número incorreto de endereços é retornado na resposta [!DNL GraphQL].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
