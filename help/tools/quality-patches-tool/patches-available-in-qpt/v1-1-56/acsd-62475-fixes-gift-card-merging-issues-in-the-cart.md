---
title: 'ACSD-62475: corrige problemas de mesclagem de cartão-presente no carrinho'
description: Aplique o patch ACSD-62475 para corrigir o problema do Adobe Commerce em que produtos de cartão-presente com detalhes diferentes são mesclados incorretamente em um único item de linha no carrinho.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475: corrige problemas de mesclagem de cartão-presente no carrinho

O patch ACSD-62475 corrige o problema em que produtos de cartão-presente com detalhes diferentes são mesclados incorretamente em um único item de linha no carrinho. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-62475. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos de cartão-presente adicionados ao carrinho com detalhes exclusivos do remetente ou do destinatário são mesclados incorretamente em um único item de linha, resultando em inconsistências de dados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto [!UICONTROL Gift Card] com as seguintes configurações:
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. Na loja, crie um novo usuário e faça logon.

1. Adicione o produto Cartão-presente ao carrinho com os seguintes detalhes:
   * **[!UICONTROL Sender Name]**: Remetente 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]: destinatário 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. Fazer logoff

1. Adicione o mesmo produto Cartão-presente ao carrinho com os seguintes detalhes:
   * **[!UICONTROL Sender Name]**: Remetente 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]: destinatário 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. Faça logon novamente e verifique o carrinho.

<u>Resultados esperados</u>:

Ambos os Cartões-presente devem aparecer como dois itens de linha separados com seus respectivos detalhes.

<u>Resultados reais</u>:

Os Cartões-presente são mesclados em um item de linha com uma quantidade de 2, mantendo os detalhes do primeiro Cartão-presente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
