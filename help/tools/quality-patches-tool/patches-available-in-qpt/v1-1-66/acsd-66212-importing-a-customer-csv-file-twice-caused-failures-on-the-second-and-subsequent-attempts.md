---
title: 'ACSD-66212: a importação do arquivo CSV do cliente causou falhas na segunda tentativa e nas subsequentes'
description: Aplique o patch ACSD-66212 para corrigir o problema do Adobe Commerce em que a importação de um arquivo CSV do cliente causou falhas na segunda e nas tentativas subsequentes.
feature: Data Import/Export, Customers
role: Admin, Developer
source-git-commit: 97a5979a189e43b737c44cfe7a65025effae711c
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# ACSD-66212: a importação do arquivo CSV do cliente causou falhas na segunda tentativa e nas subsequentes

O patch ACSD-66212 corrige o problema em que a importação de um arquivo CSV do cliente causou falhas na segunda e nas tentativas subsequentes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACSD-66212. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A importação de um arquivo CSV do cliente duas vezes causou falhas na segunda tentativa e nas subsequentes.

<u>Etapas a serem reproduzidas</u>:

Importe um CSV que contenha dados do cliente, incluindo o status do cliente.

<u>Resultados esperados</u>:

O status é importado e exportado corretamente.

<u>Resultados reais</u>:

Ocorre um erro durante a importação:

```
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
