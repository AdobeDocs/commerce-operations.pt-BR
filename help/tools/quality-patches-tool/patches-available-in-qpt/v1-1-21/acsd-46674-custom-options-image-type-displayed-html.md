---
title: 'ACSD-46674: opções personalizadas do tipo de imagem exibidas como HTML nos emails do cliente'
description: Aplique o patch ACSD-46674 para corrigir o problema do Adobe Commerce, em que as opções personalizadas do tipo de imagem são exibidas como HTML nos emails do cliente.
feature: Communications, Personalization
role: Developer
exl-id: 123ca7b5-02da-4573-897f-ff8adb184389
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-46674: opções personalizadas do tipo de imagem exibidas como HTML nos emails do cliente

O patch ACSD-46674 corrige o problema em que as opções personalizadas de um tipo de imagem são exibidas como HTML nos emails do cliente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 está instalado. A ID do patch é ACSD-46674. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As opções personalizadas de um tipo de imagem são exibidas como HTML nos emails do cliente.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com uma opção personalizada.
   * Tipo de opção: *Arquivo*
   * Extensões de arquivo compatíveis: *png, jpg, gif*
   * Obrigatório: *Sim*
1. Faça um pedido deste produto usando uma imagem carregada como opção personalizada.
1. Crie uma fatura para o pedido criado na etapa dois.
1. Crie um memorando de crédito.
1. Verifique todos os emails de confirmação.

<u>Resultados esperados</u>:

Os emails de confirmação exibem a imagem carregada.

<u>Resultados reais</u>:

Os emails de confirmação contêm código HTML simples em vez da imagem da opção personalizada do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tools] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis em [!DNL QPT], consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
