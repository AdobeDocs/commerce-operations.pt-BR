---
title: 'ACSD-47937: notificações de queda de preço não enviadas devido ao armazenamento em cache no nível do aplicativo'
description: Aplique o patch ACSD-47937 para corrigir o problema do Adobe Commerce em que as notificações de queda de preço nem sempre são enviadas devido ao armazenamento em cache no nível do aplicativo.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937: notificações de queda de preço não enviadas devido ao armazenamento em cache no nível do aplicativo

O patch ACSD-47937 corrige o problema em que as notificações de queda de preço nem sempre são enviadas devido ao armazenamento em cache no nível do aplicativo. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 está instalado. A ID do patch é ACSD-47937. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 e 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4, 2.4.5 e 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes não estão recebendo email de queda de preço de produto para alterações subsequentes de preço de produto.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL Product Alert]** para *[!UICONTROL Price Changes]* e *[!UICONTROL Back in Stock]* em **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Habilitar **[!UICONTROL Display Out of Stock Products]**.
1. Crie um produto simples (ABC) com quantidade = 0.
1. Crie um cliente na loja e assine o produto acima para receber alertas de produtos em caso de queda de preços.
1. Iniciar o alerta de produto para clientes.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Baixe o preço do produto ABC.
1. Acione o cron de alerta do produto.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Baixe o preço do produto ABC novamente.
1. Acione o cron de alerta do produto.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Se você não estiver familiarizado com a ferramenta [!DNL n98], poderá executar `bin/magento cron:run command` como de costume e monitorar a tabela `cron_schedule` para verificar se o trabalho `catalog_product_alert` obterá status de sucesso.

<u>Resultados esperados</u>:

O segundo e-mail de queda de preço é enviado.

<u>Resultados reais</u>:

O e-mail da segunda redução de preço não é enviado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
