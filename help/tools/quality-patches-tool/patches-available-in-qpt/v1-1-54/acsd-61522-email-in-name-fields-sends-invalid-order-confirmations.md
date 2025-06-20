---
title: 'ACSD-61522: endereços de email nos campos *Nome e Sobrenome* enviam confirmações de pedido inválidas'
description: Aplique o patch ACSD-61522 para corrigir o problema do Adobe Commerce em que é possível inserir endereços de email nos campos *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* de um cliente convidado, resultando no envio de emails de confirmação de pedido inválidos.
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522: Endereços de email nos campos *Nome e Sobrenome* enviam confirmações de ordem inválidas

O patch ACSD-61522 corrige o problema em que é possível inserir endereços de email nos campos *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* de um cliente convidado, resultando no envio de emails de confirmação de pedido inválidos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-61522. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p9

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O sistema permite que endereços de email sejam inseridos nos campos *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* de um cliente convidado, resultando no envio de emails de confirmação de pedido inválidos.

<u>Etapas a serem reproduzidas</u>:

1. Adicione qualquer produto ao carrinho como cliente convidado.
1. Ir para **[!UICONTROL Checkout]**.
1. Preencha o campo *[!UICONTROL Email Address]* com *test1@example.com*.
1. Preencha o campo *[!UICONTROL First Name]* com *<test2@example.com>*.
1. Preencha *[!UICONTROL Last Name]* com *<test3@example.com>*.
1. Preencha outros campos obrigatórios.
1. Coloque o pedido.

<u>Resultados esperados</u>:

Não é possível usar endereços de email nos campos *[!UICONTROL First Name]* e *[!UICONTROL Last Name]*.

<u>Resultados reais</u>:

1. O pedido é feito.
1. *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* campos são salvos como inseridos.
1. Os emails de confirmação de pedido são enviados para os três emails.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
