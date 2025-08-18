---
title: 'ACSD-66404: o trabalho Cron falha ao limpar as tabelas de log de alterações devido aos limites de tamanho da transação  [!DNL Galera Cluster] '
description: Aplique o patch ACSD-66404 para corrigir o problema do Adobe Commerce em que o trabalho cron não limpa as tabelas de log de alterações e causa  [!DNL Galera Cluster]  problemas no caso de uma grande quantidade de dados nessas tabelas.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404: o trabalho Cron falha ao limpar as tabelas de log de alterações devido aos limites de tamanho da transação [!DNL Galera Cluster]

O patch ACSD-66404 corrige o problema em que o trabalho cron falha ao limpar as tabelas de changelog, causando [!DNL Galera Cluster] problemas ao manipular grandes quantidades de dados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-66404. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p6, 2.4.7-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O trabalho do Cron não limpa as tabelas de log de alterações e causa [!DNL Galera Cluster] problemas em caso de grande quantidade de dados nessas tabelas.

<u>Etapas a serem reproduzidas</u>:

1. Gere muitos produtos usando perfis de desempenho.
1. Execute uma atualização em massa para todos os produtos no sistema para que haja muitas entradas na tabela de banco de dados `inventory_cl`.
1. Execute o trabalho cron `indexer_clean_all_changelogs`.

<u>Resultados esperados</u>:

O trabalho do cron `indexer_clean_all_changelogs` pode realizar a limpeza do log de alterações em um log de alterações grande (10+ GB) em várias consultas de exclusão, sem causar [!DNL Galera Cluster] problemas.

<u>Resultados reais</u>:

O trabalho do cron `indexer_clean_all_changelogs` executa a limpeza do log de alterações em um log de alterações grande (10+ GB) em uma única consulta de exclusão, causando [!DNL Galera Cluster] problemas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas
