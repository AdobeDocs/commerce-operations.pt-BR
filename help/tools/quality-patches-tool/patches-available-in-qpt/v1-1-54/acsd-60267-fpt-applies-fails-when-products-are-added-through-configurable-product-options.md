---
title: 'ACSD-60267: o FPT se aplica incorretamente quando os produtos são adicionados por meio de opções de produto configuráveis'
description: Aplique o patch ACSD-60267 para corrigir o problema do Adobe Commerce em que o imposto fixo do produto (FPT) se aplica corretamente ao adicionar produtos simples diretamente ao carrinho, mas falha ao selecionar os mesmos produtos por meio de opções de produto configuráveis.
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: o FPT se aplica incorretamente quando os produtos são adicionados por meio de opções de produto configuráveis

O patch ACSD-60267 corrige o problema em que o imposto fixo do produto (FPT) se aplica corretamente ao adicionar produtos simples diretamente ao carrinho, mas falha ao selecionar os mesmos produtos por meio de opções de produto configuráveis. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) 1.1.54 está instalado. A ID do patch é ACSD-60267. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Imposto Fixo sobre Produtos (FPT) funciona corretamente quando produtos simples com FPT são adicionados ao carrinho, mas o FPT não é adicionado quando os produtos são adicionados por meio da seleção de produto configurável.

<u>Etapas a serem reproduzidas</u>:

1. Defina *[!UICONTROL Enable FPT]* como *Sim* navegando até *Administrador* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**.
1. Crie um atributo FPT e atribua-o a um *[!UICONTROL Attribute Set]*.
1. Abrir **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Para *[!UICONTROL Default Label]*, insira um rótulo que identifique o atributo.
1. Defina *[!UICONTROL Catalog Input for Store Owner]* como *[!UICONTROL Fixed Product Tax]*.
1. Crie um novo imposto e zona e atribua-os a um novo *[!UICONTROL Tax Rule]*.
1. Crie um produto configurável com dois produtos simples.
1. Agora atribua dois valores de FPT diferentes a esses produtos simples.
1. Reindexe e verifique os preços na loja.
1. Adicione os produtos ao carrinho e verifique os subtotais.

<u>Resultados esperados</u>:

* A página *[!UICONTROL Catalog]* mostra preços incluindo FPT.
* Os subtotais no carrinho incluem FPT.

<u>Resultados reais</u>:

* A página *[!UICONTROL Catalog]* não mostra os preços incluindo o valor FPT.
* Os subtotais e o resumo são inválidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
