---
title: 'ACP2E-3918: Falha de check-out para clientes da empresa que usam a retirada na loja'
description: Aplique o patch ACP2E-3918 para corrigir o problema do Adobe Commerce em que o check-out falha para clientes da empresa conectados que usam a coleta na loja sem um endereço de cobrança padrão.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACP2E-3918: Falha de check-out para clientes da empresa que usam a retirada na loja

O patch ACP2E-3918 corrige o problema em que o check-out falha para clientes da empresa conectados que usam a retirada na loja sem um endereço de cobrança padrão. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACP2E-3918. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A finalização falha quando um cliente da empresa conectado sem um endereço padrão tenta colocar uma ordem de compra usando a retirada na loja.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL Purchase Orders]**.
1. Crie um **[!UICONTROL Company]** e habilite **[!UICONTROL Purchase Orders]** para ele.
1. Criar um **[!UICONTROL Company User]** sem endereços salvos.
1. Habilite o método de envio **[!UICONTROL In-Store Delivery]**.
1. Adicione uma origem de inventário.
1. Adicionar um estoque de estoque.
1. Atribuir estoque a um produto.
1. No front-end, faça logon como o usuário da empresa.
1. Adicionar produtos a **[!UICONTROL Cart]**.
1. Prossiga para o check-out.
1. Selecione **[!UICONTROL In-Store Pick Up]** na etapa de envio.
1. Prosseguir com o pagamento.

<u>Resultados esperados</u>:

A etapa de pagamento deve ser carregada com êxito durante o check-out e nenhum erro deve aparecer no console do navegador.

<u>Resultados reais</u>:

A etapa de pagamento não é carregada e o console do navegador exibe o seguinte erro do JavaScript:

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
