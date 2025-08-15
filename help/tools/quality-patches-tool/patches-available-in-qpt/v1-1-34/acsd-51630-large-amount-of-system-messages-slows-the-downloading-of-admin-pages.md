---
title: 'ACSD-51630: Várias mensagens do sistema atrasam o download das páginas de administração'
description: Aplique o patch ACSD-51630 para corrigir o problema de desempenho do Adobe Commerce em que uma grande quantidade de mensagens do sistema atrasa o download de Páginas de Administração.
feature: Admin Workspace, System
role: Admin
exl-id: 8f39afea-551a-4306-994a-cb8ce5bd5b4a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-51630: Várias mensagens do sistema atrasam o download das páginas de administração

O patch ACSD-51630 corrige o problema de desempenho em que uma grande quantidade de mensagens do sistema atrasa o download de Páginas de administrador. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.34 está instalado. A ID do patch é ACSD-51630. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Várias mensagens do sistema atrasam o download das páginas de administração

<u>Etapas a serem reproduzidas</u>:

1. Faça um grande número de solicitações (~50k) ao DELETE `/rest/async/v1/products/ {sku}`.
1. Acesse qualquer **Página de Administrador**.

<u>Resultados esperados</u>:

A página é carregada em um horário adequado. Somente as mensagens exibidas devem ser carregadas.

<u>Resultados reais</u>:

A página leva muito tempo para carregar. Todas as mensagens existentes são carregadas do banco de dados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
