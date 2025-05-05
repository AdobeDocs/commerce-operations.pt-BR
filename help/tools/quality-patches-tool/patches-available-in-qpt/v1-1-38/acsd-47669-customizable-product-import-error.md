---
title: "ACSD-47669: erro interno do servidor ao importar produtos com opções personalizáveis"
description: Aplique o patch ACSD-47669 para corrigir o problema do Adobe Commerce em que há um erro interno do servidor durante a importação de produtos com opções personalizáveis.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47669: erro interno do servidor ao importar produtos com opções personalizáveis

O patch ACSD-47669 corrige o problema em que há um erro interno do servidor durante importações de produtos com opções personalizáveis. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.38 está instalado. A ID do patch é ACSD-47669. Observe que o problema já foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Há um erro interno do servidor ao importar produtos com opções personalizáveis.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma exibição de loja adicional. Verifique se você tem duas visualizações de loja, por exemplo, en, UK.
1. Crie dois produtos simples, por exemplo, prod1 e prod2.
1. Prepare um arquivo csv que adicione opções personalizadas para ambos os produtos em cada exibição de loja e para o escopo **Todas as Exibições de Loja**. Importe este arquivo csv.
1. Prepare outro arquivo csv que inclua dois registros. O primeiro registro deve atualizar as opções personalizadas de &quot;prod1&quot; especificamente para o escopo de exibição de loja do Reino Unido e o segundo registro deve atualizar as opções personalizadas de &quot;prod2&quot; para o escopo **Todas as Exibições de Loja**. Importe este segundo arquivo csv.

<u>Resultados esperados</u>:

Você deve ser capaz de personalizar as opções sem erros.

<u>Resultados reais</u>:

Ocorre um erro de violação de restrição de integridade.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
