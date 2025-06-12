---
title: 'ACSD-55566: falha na mutação [!UICONTROL mergeCart] com erro interno do servidor na resposta  [!DNL GraphQL] '
description: Aplique o patch ACSD-55566 para corrigir o problema do Adobe Commerce em que a mutação "mergeCart" falha com um erro interno do servidor na resposta  [!DNL GraphQL]  ao mesclar os carrinhos de origem e de destino que têm os mesmos itens de pacote.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566: falha na mutação `mergeCart` com erro interno do servidor na resposta [!DNL GraphQL]

O patch ACSD-55566 corrige o problema em que a mutação `mergeCart` falha com um erro interno do servidor na resposta [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 está instalado. A ID do patch é ACSD-55566. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mutação `mergeCart` falha com um erro de servidor interno na resposta [!DNL GraphQL] ao mesclar os carrinhos de origem e destino que têm os mesmos itens de pacote.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma fonte personalizada e um estoque personalizado.
1. Atribua o estoque criado ao site principal.
1. Crie um produto simples e atribua a ele a origem criada (qtd.=2).
1. Crie um produto combinado com uma opção e um produto secundário (produto criado na etapa 3).
1. Crie um carrinho de convidados via [!DNL GraphQL].
1. Adicione um produto do pacote com ambas as opções selecionadas.
1. Salve a *cartID*.
1. Crie um cliente e gere um token de cliente.
1. Crie um carrinho do cliente.
1. Adicione o mesmo produto do pacote com a mesma configuração ao carrinho.
1. Tente mesclar o carrinho de convidado com o carrinho do cliente.

<u>Resultados esperados</u>:

O carrinho do cliente contém produtos de ambos os carrinhos.

<u>Resultados reais</u>:

Você recebe um erro interno.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
