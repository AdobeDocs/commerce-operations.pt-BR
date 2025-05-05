---
title: "ACSD-53845: problema de tempo limite de conexão MySQL quando consumidor max_messages = 0"
description: Aplique o patch ACSD-53845 para corrigir o problema do Adobe Commerce em que a conexão MySQL atinge o tempo limite quando o consumidor "max_messages = 0".
feature: REST, Configuration
role: Admin, Developer
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-53845: problema de tempo limite de conexão MySQL quando o consumidor `max_messages = 0`

O patch ACSD-53845 corrige o problema em que a conexão MySQL atinge o tempo limite quando o consumidor `max_messages = 0`. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.42 está instalado. A ID do patch é ACSD-53845. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A conexão MySQL expira quando o consumidor `max_messages = 0`.

No entanto, a conexão com o banco de dados será restaurada ao iniciar uma transação.

<u>Etapas a serem reproduzidas</u>:

1. Envie uma solicitação para atualizar produtos em massa usando o ponto de extremidade da API REST `async/bulk/V1/products`.
1. Verifique o status na tabela `magento_operation`.

<u>Resultados esperados</u>:

Os produtos são atualizados.

<u>Resultados reais</u>:

1. Um erro é registrado:

   ```
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. O *status* desta operação permanece *4* na tabela `magento_operation`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
