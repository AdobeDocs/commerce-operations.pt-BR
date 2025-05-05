---
title: 'ACSD-61969: é necessário digitar o código do cupom conforme configurado em maiúsculas ou minúsculas'
description: Aplique o patch ACSD-61969 para corrigir o problema do Adobe Commerce em que um usuário precisa digitar o código do cupom exatamente como está configurado em maiúsculas ou minúsculas.
feature: Price Rules
role: Admin, Developer
source-git-commit: b2660e3ca0dedbe4c9d8fa441f2e49b2e096474b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: é necessário digitar o código do cupom conforme configurado em maiúsculas ou minúsculas

O patch ACSD-61969 corrige o problema em que um usuário precisa digitar o código do cupom exatamente como está configurado em maiúsculas ou minúsculas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 está instalado. A ID do patch é ACSD-61969. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

É necessário digitar o código do cupom exatamente como configurado em maiúsculas ou minúsculas ao aplicá-los do back-end. Eles fazem distinção entre maiúsculas e minúsculas na criação do pedido do administrador, mas não entre maiúsculas e minúsculas na loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie um *[!UICONTROL Cart Price Rule]* com um cupom específico *TEST*. Verifique se o código do cupom está em maiúsculas.
1. Crie um pedido no Administrador.
1. Adicione *test* ao campo *[!UICONTROL Apply Coupon Code]* e clique na seta próximo ao campo para aplicar o cupom.
1. Observe o resultado.

<u>Resultados esperados</u>:

O cupom foi aplicado com êxito. O campo de cupom não diferencia maiúsculas de minúsculas.

<u>Resultados reais</u>:

O cupom não é aplicado. O seguinte erro é exibido:

*O código do cupom &quot;teste&quot; não é válido. Verifique o código e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
