---
title: 'MDVA-42520: Alíquota de imposto aplicada duas vezes quando "Habilitar Comércio Transfronteiriço" é usado'
description: O patch MDVA-42520 corrige o problema em que a alíquota do imposto é aplicada duas vezes quando a opção **Ativar comércio transfronteiriço** é usada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 está instalada. A ID do patch é MDVA-42520. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# MDVA-42520: Alíquota de imposto aplicada duas vezes quando &quot;Habilitar Comércio Transfronteiriço&quot; é usado

O patch MDVA-42520 corrige o problema em que a alíquota de imposto é aplicada duas vezes quando a **Habilitar comércio entre fronteiras** é usada. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 está instalada. A ID do patch é MDVA-42520. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A alíquota é aplicada duas vezes quando a **Habilitar Comércio Transfronteiriço** é usada.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **Empresa**, **Catálogo Compartilhado** e **Cotação**
1. Configure os impostos de acordo com a captura de tela. Habilite o **Comércio entre Fronteiras**.

   ![configurações de imposto](/help/assets/tools/tax_settings_1.png){width="700"}

1. Criar uma taxa de imposto para a Alemanha (10%).
1. Crie uma regra de imposto para aplicar a alíquota do imposto.
1. Crie uma empresa e um catálogo compartilhado personalizado.
1. Crie um produto com um preço de 100 e inclua-o no catálogo compartilhado personalizado com um desconto de preço de 20%.
1. Crie um cliente com um endereço alemão e atribua-o à empresa
1. Adicione 10 produtos ao cartão como cliente.
1. Vá para o carrinho de compras e solicite uma cotação.
1. Abra esta cotação no back-end e tente adicionar um desconto adicional de 10%.

<u>Resultados esperados</u>:

Subtotal da Cotação (Incluindo Imposto) e Total Geral da Cotação (Incluindo Imposto) = US$ 720

<u>Resultados reais</u>:

Subtotal da Cotação (Incluindo Imposto) e Total Geral da Cotação (Incluindo Imposto) = US$ 649,50.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
