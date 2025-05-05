---
title: '"ACSD-46938: problemas de desempenho com acionadores de DB durante "setup:upgrade""'
description: Aplique o patch ACSD-46938 para corrigir o problema do Adobe Commerce em que o comando "setup:upgrade" altera o modo do indexador de agendamento para salvar, causando lentidão significativa no desempenho.
feature: Upgrade
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-46938: problemas de desempenho com acionadores de BD durante `setup:upgrade`

O patch ACSD-46938 corrige o problema em que o comando `setup:upgrade` altera o modo do indexador de agendamento para salvar, causando lentidão significativa no desempenho. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 está instalado. A ID do patch é ACSD-46938. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Degradação de desempenho durante recriação do gatilho do banco de dados em `setup:upgrade`.

<u>Etapas a serem reproduzidas</u>:

1. Crie um catálogo grande com muitos produtos e categorias.
1. Faça logon no [!UICONTROL Admin].
1. Defina todos os indexadores para o modo [!UICONTROL Update By Schedule].
1. Abra qualquer produto.
1. Atualize-o. Por exemplo, atribua uma nova categoria a ela.
1. Clique em [!UICONTROL Save].
1. Execute comandos `bin/magento setup:upgrade` e `bin/magento cron:run` em paralelo.

<u>Resultados esperados</u>:

O tempo de execução do comando `bin/magento setup:upgrade` aumenta significativamente quando o comando `bin/magento cron:run` é executado simultaneamente.

<u>Resultados reais</u>:

O tempo de execução do comando não aumenta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
