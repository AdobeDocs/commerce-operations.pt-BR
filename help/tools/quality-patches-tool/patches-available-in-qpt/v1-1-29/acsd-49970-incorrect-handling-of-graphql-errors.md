---
title: 'ACSD-49970: Tratamento incorreto de erros do GraphQL'
description: Aplique o patch ACSD-49970 para corrigir o problema do Adobe Commerce em que há tratamento incorreto de erros de GraphQL quando [!UICONTROL New Relic Reporting] está ativado.
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970: Tratamento incorreto de erros do GraphQL

O patch ACSD-49970 corrige o problema em que há tratamento incorreto de erros de GraphQL quando *[!UICONTROL New Relic Reporting]* está ativado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49970. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A chave `GraphQLOperationNames` não é tratada corretamente caso `logDataHelper` contenha ou não essa chave.

<u>Etapas a serem reproduzidas</u>:

1. Executar `bin/magento deploy:mode:set developer`.
1. Faça logon no Administrador.
1. Habilitar **[!UICONTROL New Relic Integration]** de **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Observação: mesmo que um erro seja exibido informando que a extensão [!DNL New Relic] não está disponível, a configuração será salva).
1. Execute esta mutação do *GraphQL* para `http://yourMagentoDomain/graphql` do cliente *[!DNL Altair]* ou qualquer outro cliente ou via cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Observação: Defina o **[!UICONTROL Header]** como [!UICONTROL Content-Currency:CA] antes de executá-lo).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Resultados esperados</u>:

Não há *500 exceção* nos logs. A chave `GraphQLOperationNames` está sendo tratada corretamente.

<u>Resultados reais</u>:

Há uma *500 exceção* nos logs. A chave `GraphQLOperationNames` não está sendo tratada corretamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
