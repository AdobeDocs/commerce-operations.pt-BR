---
title: "MDVA-41061: O status do estoque é redefinido para vendável quando o produto é salvo do Administrador"
description: O patch MDVA-41061 corrige o problema em que o status do estoque é redefinido para vendable quando o produto é salvo do Admin. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 está instalada. A ID do patch é MDVA-41061. A versão de patch mais recente está disponível no QPT 1.1.15 com ID de patch MDVA-41061-V3. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061: O status do estoque é redefinido para vendável quando o produto é salvo do Administrador

O patch MDVA-41061 corrige o problema em que o status do estoque é redefinido para vendable quando o produto é salvo do Admin. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 está instalada. A ID do patch é MDVA-41061. A versão de patch mais recente está disponível no QPT 1.1.15 com ID de patch MDVA-41061-V3. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do estoque é redefinido para vendável quando o produto é salvo do Administrador.

<u>Pré-requisitos</u>:

Os módulos de inventário estão instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com Qtd. = 1.
1. Faça um pedido usando o produto criado na etapa 1.
1. Executar cron - verifique se a fila `inventory.reservations.updateSalabilityStatus` foi executada e se o status do estoque do produto foi alterado para zero na tabela `cataloginventory_stock_status`.
1. Verifique o produto no front-end. Deve ser marcado como **Sem Estoque**.
1. Salve o produto no Administrador sem nenhuma alteração.

<u>Resultados esperados</u>:

* O status do estoque não deve ser atualizado.
* O produto deve estar **sem estoque** no front-end.

<u>Resultados reais</u>:

* O produto simples está marcado como **Em Estoque** no front-end.
* Os usuários obtêm a mensagem *A quantidade solicitada não está disponível* ao tentar adicioná-la ao carrinho.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
