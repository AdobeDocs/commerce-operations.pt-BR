---
title: 'MDVA-38929: Fatura com FPT mostra total incorreto'
description: O patch MDVA-38929 resolve o problema em que a fatura com FPT mostra um total geral incorreto quando o pedido é pago com crédito de loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-38929. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Invoices, Orders
role: Admin
exl-id: fd0ca2f3-c6bf-4f09-a0fa-c931df94158b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-38929: Fatura com FPT mostra total incorreto

O patch MDVA-38929 resolve o problema em que a fatura com FPT mostra um total geral incorreto quando o pedido é pago com crédito de loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-38929. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A fatura com FPT mostra um total geral incorreto quando o pedido é pago com crédito de loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cliente e verifique se ele tem crédito de armazenamento suficiente para cobrir o pedido.
1. Habilite o FPT e adicione o FPT a um produto.
1. No front-end, faça logon como o cliente acabou de criar.
1. Adicione o produto com FTP ao carrinho.
1. Finalizar compra e pagar com crédito de loja. Deve ser uma ordem de pagamento zero.
1. Ir para Pedidos e faturar manualmente o pedido.
1. Verifique o total geral da fatura.

<u>Resultados esperados</u>:

* O total geral da fatura é zero.
* O valor pago total do pedido é zero.

<u>Resultados reais</u>:

* O total geral da fatura ainda mostra o valor FPT.
* O total pago ainda mostra o valor do FPT.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
