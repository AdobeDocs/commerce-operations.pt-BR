---
title: 'ACSD-57565: o painel de pedidos exibe informações de pedidos incorretas'
description: Aplique o patch ACSD-57565 para corrigir o problema do Adobe Commerce em que o painel de pedidos exibe informações incorretas sobre os pedidos até que o período seja atualizado.
feature: Roles/Permissions
role: Admin, Developer
exl-id: dc4ad263-725e-4605-9b85-fc4305ab9a29
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-57565: o painel de pedidos exibe informações de pedidos incorretas

O patch ACSD-57565 corrige o problema em que o painel de pedidos exibe informações incorretas do pedido até que o período de tempo seja atualizado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.48 está instalado. A ID do patch é ACSD-57565. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch

## Problema

O painel do pedido exibe informações incorretas do pedido.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL dashboard charts]**.
1. Criar um pedido e faturar.
1. Aguarde pelo menos 24 horas após o horário de criação do pedido.
1. Verifique os dados de **[!UICONTROL dashboard chart]**.
1. Anote a contagem completa de pedidos.
1. Altere a hora para o *mês atual* e altere-a novamente para *hoje*.

<u>Resultados esperados</u>:

O gráfico de painel deve mostrar as estatísticas corretas o tempo todo.

<u>Resultados reais</u>:

O gráfico de painel mostra estatísticas incorretas na primeira carga. As estatísticas precisas do gráfico são atualizadas após o período.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
