---
title: 'ACSD-47875: Não é possível adicionar o produto ao carrinho para o escopo de exibição da loja com o gerenciamento de estoque'
description: Aplique o patch ACSD-47875 para corrigir o problema do Adobe Commerce em que um produto não pode ser adicionado ao carrinho do cliente do Administrador para um escopo de exibição de loja específico com gerenciamento de estoque.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-47875: Não é possível adicionar o produto ao carrinho para o escopo de exibição da loja com o gerenciamento de estoque

O patch ACSD-47875 corrige o problema em que um produto não pode ser adicionado a um carrinho do cliente do Administrador para um escopo de exibição de loja específico com gerenciamento de estoque. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. A ID do patch é ACSD-47875. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários administradores não podem adicionar um produto ao carrinho do cliente usando o recurso **[!UICONTROL Manage Shopping Cart]** no Administrador para um escopo de exibição de loja específico com o MSI instalado.

<u>Pré-requisitos</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] módulos estão instalados e habilitados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site, uma loja e uma visualização de loja.
1. Criar uma fonte adicional diferente de *Padrão*.
1. Crie um novo estoque e atribua-o ao novo site e à nova fonte.
1. Crie um novo cliente para o novo site.
1. Atribuir um produto somente ao novo site; cancelar atribuição do site padrão.

   * Atribua a nova origem e defina a Qtd. *acima de* para a nova origem e *0* para a origem padrão.

1. Vá para a página **[!UICONTROL Customer Edit]** no Administrador. Clique em **[!UICONTROL Manage Shopping Cart]**.
1. Altere o escopo de exibição de loja para a nova exibição de loja.
1. Acesse a seção **[!UICONTROL Products]** e pesquise o produto.
1. Selecione o produto e clique em **[!UICONTROL Add selections to my cart]**.

<u>Resultados esperados</u>:

O produto é adicionado ao carrinho.

<u>Resultados reais</u>:

* O seguinte erro é lançado: *O produto que você está tentando adicionar não está disponível.*
* O produto não é adicionado ao carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
