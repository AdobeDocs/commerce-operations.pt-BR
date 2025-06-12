---
title: 'ACSD-56790: a opção **[!UICONTROL move out of stock to bottom]** não funciona ao classificar produtos no  [!DNL Visual Merchandiser]'
description: Aplique o patch ACSD-56790 para corrigir o problema do Adobe Commerce em que a opção de mover do estoque para o final não funciona ao classificar produtos no Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-56790: a opção **[!UICONTROL move out of stock to bottom]** não funciona ao classificar produtos no [!DNL Visual Merchandiser]

O patch ACSD-56790 corrige o problema em que a opção de mover do estoque para o final não funciona ao classificar produtos no [!DNL Visual Merchandiser]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 está instalado. A ID do patch é ACSD-56790. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A opção **[!UICONTROL move out of stock to bottom]** não funciona ao classificar produtos no [!DNL Visual Merchandiser]

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e crie os seguintes atributos.
1. Crie um novo site: **Não principal**.
1. Crie uma **Loja Não Principal** neste novo site.
1. Criar dois armazenamentos:

   * Primeiro no **Repositório de sites principais**.
   * Segundo no **armazenamento não principal**.

1. Criar duas fontes:
   * Cartas.
   * Números.

1. Criar dois estoques:
   * Primeiro Principal - canais de vendas: Site Principal - fontes atribuídas: Cartas.
   * Segundo não principal - canais de vendas: Não principal - fontes atribuídas: Números.

1. Crie três produtos simples em ambos os sites, todos na categoria Padrão, todos atribuídos a ambas as fontes:

   * ProductA - Qtd. *10* em Cartas, Qtd. *0* em Números.
   * Product1 - Qtd. *0* em Cartas, Qtd. *10* em Números.
   * ProductA1 - Qtd. *10* em Cartas, Qtd. *10* em Números.

1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e selecione **[!UICONTROL Default category]**.
1. Alterar o escopo para **Primeiro**.
1. Expanda os Produtos na seção Categoria.
1. Escolha a ordem de classificação como: **[!UICONTROL move out of stock to bottom]**

<u>Resultados esperados</u>:

A lista de produtos com os **produtos indisponíveis** é movida para a parte inferior.

<u>Resultados reais</u>:

Falha ao carregar os produtos. Uma página redireciona para o painel de administração com a mensagem de erro: `Invalid security or form key. Please refresh the page`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
