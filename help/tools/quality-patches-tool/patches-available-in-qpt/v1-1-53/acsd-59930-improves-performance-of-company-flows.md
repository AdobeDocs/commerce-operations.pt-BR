---
title: 'ACSD-59930: melhora o desempenho dos fluxos da empresa'
description: Aplique o patch ACSD-59930 para resolver o problema do Adobe Commerce em que um erro de *Tempo limite* é exibido no painel de administração ao criar, salvar ou excluir uma empresa com um administrador que tenha *1000+* endereços no catálogo de endereços.
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930: melhora o desempenho dos fluxos da empresa

O patch ACSD-59930 corrige o problema em que um erro de *Tempo limite* é exibido no painel de administração ao criar, salvar ou excluir uma empresa com um administrador que tenha *1000+* endereços no catálogo de endereços. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 está instalado. A ID do patch é ACSD-59930. Observe que esse problema está programado para ser corrigido no Adobe Commerce B2B-1.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Melhora o desempenho dos fluxos criar, salvar e excluir da empresa.

<u>Pré-requisitos:</u>:

Instale e ative os módulos B2B do Adobe Commerce.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cliente com *1000+* endereços no *[!UICONTROL Address Book]*.
1. Crie uma empresa e use o cliente acima como administrador.
1. Salve a empresa.

<u>Resultados esperados</u>:

A empresa foi criada com êxito sem mostrar erros de tempo limite.

<u>Resultados reais</u>:

Um erro de tempo limite é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
