---
title: 'ACSD-46869: produtos configuráveis não são atualizados usando a API REST no check-out'
description: O patch ACSD-46869 corrige o problema em que os produtos configuráveis não são atualizados usando a API REST na finalização. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 está instalada. A ID do patch é ACSD-46869. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869: produtos configuráveis não são atualizados usando a API REST no check-out

O patch ACSD-46869 corrige o problema em que os produtos configuráveis não são atualizados usando a API REST na finalização. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 está instalado. A ID do patch é ACSD-46869. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL QPT] página de aterrissagem](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos configuráveis não são atualizados usando a API REST durante o check-out.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com atributos de cor e tamanho.
1. Selecione **[!UICONTROL Options]** e adicione o produto ao carrinho.
1. Vá para **[!UICONTROL Checkout]**, atualize o tamanho várias vezes exceto por qtd. e verifique a solicitação e a resposta.
1. Você recebe a seguinte resposta ao atualizar o tamanho.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Resultados esperados</u>:

O valor é atualizado de acordo com as alterações.

<u>Resultados reais</u>:

`option_value` não é atualizado, portanto, quando o pedido for feito, ele terá o valor do tamanho antigo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tools] > Uso](/help/tools/quality-patches-tool/usage.md) no guia Ferramenta de Patches de Qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
