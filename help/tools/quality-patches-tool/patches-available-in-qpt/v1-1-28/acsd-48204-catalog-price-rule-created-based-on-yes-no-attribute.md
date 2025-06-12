---
title: 'ACSD-48204: a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado'
description: Aplique o patch ACSD-48204 para corrigir o problema do Adobe Commerce em que a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204: a regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado

O patch ACSD-48204 corrige o problema em que a regra de preço do catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 está instalado. A ID do patch é ACSD-48204. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de preço de catálogo criada com base no atributo *Sim/Não* não considera o escopo selecionado.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites (Padrão e W2).
1. Crie um atributo de produto do tipo *Sim/Não*.
   * Conjunto [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Crie um produto configurável com base em qualquer atributo com duas variações (V1 e V2).
   * Adicionar o atributo *Sim/Não* ao conjunto de atributos de variações configuráveis
   * Para uma das variações (V1), defina o valor como *[!UICONTROL Yes]* no site não padrão (W2)
1. Criar uma regra de catálogo:
   * Aplicado a ambos os sites
   * Condição: *Sim/Não* o valor do atributo é *[!UICONTROL Yes]*
   * Desconto = 50%
1. Abra o produto configurável no site fora do padrão (W2).
1. Verifique se a variação V1 tem o desconto de 50% aplicado.
1. Abra a variação V1 no Administrador do Adobe Commerce.
   * Alternar para o site padrão
   * Não fazer alterações e salvar o produto
1. Atualize a página inicial da loja de produtos configurável.

<u>Resultados esperados</u>:

A variação V1 ainda tem o desconto de 50% aplicado, pois nenhuma alteração foi feita.

<u>Resultados reais</u>:

O desconto desaparece.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
