---
title: 'ACSD-63182: Ocorre um erro ao salvar um produto após a duplicação do produto empacotado'
description: Aplique o patch ACSD-63182 para corrigir o problema do Adobe Commerce em que ocorre um erro ao salvar um produto depois que um pacote de produto é duplicado com o MSI ativado.
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182: Ocorre um erro ao salvar um produto após a duplicação do produto empacotado

O patch ACSD-63182 corrige o problema em que um produto simples usado como uma opção de pacote não podia ser salvo após a duplicação do produto de pacote. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63182. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro ao salvar um produto simples usado como uma opção de pacote após duplicar o produto de pacote.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma nova fonte e estoque de MSI.
1. Crie dois produtos simples: **p1** e **p2**.
1. Crie um produto agrupado **b1** com **p1** e **p2** como opções agrupadas.
1. Edite o **produto incorporado b1** e clique em ***[!UICONTROL Save and Duplicate]**.
1. Edite o **produto simples p1** e clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

O produto é salvo sem erros.

<u>Resultados reais</u>:

O seguinte erro é exibido:
*Exceção: já existe um item (Magento\Catalog\Model\Product\Interceptor) com a mesma ID &#39;XXX&#39;.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
