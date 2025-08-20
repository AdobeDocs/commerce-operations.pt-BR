---
title: 'ACSD-66149: o manipulador IPN retorna *500* para tipos não suportados'
description: Aplique o patch ACSD-66149 para corrigir o problema do Adobe Commerce em que o manipulador IPN não ignora tipos IPN incompatíveis ou desconhecidos, fazendo com que o problema não seja registrado, interrompendo o processo e também retornando um erro 500.
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66149: o manipulador IPN retorna *500* para tipos sem suporte

O patch ACSD-66149 corrige o problema em que o manipulador IPN (Notificação de pagamento instantâneo) retorna um erro 500 para tipos IPN incompatíveis ou desconhecidos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-66149. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O problema é que o manipulador IPN retorna um erro *500* para tipos IPN sem suporte ou desconhecidos. Ocorre quando Paypal envia IPN com alguns campos ausentes.

<u>Etapas a serem reproduzidas</u>:

1. Crie um módulo personalizado que emula todos os tipos de tipos de IPN desconhecidos do PayPal.
1. Crie pelo menos um produto.
1. Configure o PayPal Express com suas próprias credenciais.
1. Faça um pedido com o Paypal Express.
1. Execute o emulador PayPal.

<u>Resultados esperados</u>:

O manipulador IPN do aplicativo ignora tipos IPN incorretos e não gera erros *500*:

```Order 000000001: Status processing — HTTP 500```

<u>Resultados reais</u>:

O aplicativo gera muitos erros *500* durante o processamento de IPNs incorretos e, esporadicamente, não processa alguns pedidos se os campos esperados estiverem ausentes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas
