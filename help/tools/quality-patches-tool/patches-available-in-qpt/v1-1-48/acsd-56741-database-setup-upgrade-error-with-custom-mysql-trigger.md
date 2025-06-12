---
title: 'ACSD-56741: Resolução de erros de configuração de banco de dados com acionadores MySQL personalizados'
description: Aplique o patch ACSD-56741 para corrigir o problema do Adobe Commerce em que uma mensagem de erro *Tentando acessar o deslocamento da matriz no valor do tipo null* aparece durante &grave;setup:upgrade&grave; devido a um gatilho MySQL personalizado no banco de dados não relacionado à indexação e  [!DNL MView].
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741: Resolução de erros de configuração de banco de dados com acionadores MySQL personalizados

O patch ACSD-56741 corrige o problema em que uma mensagem de erro *Tentando acessar o deslocamento da matriz no valor do tipo nulo* aparece durante `setup:upgrade` devido a um gatilho MySQL personalizado no banco de dados não relacionado à indexação e [!DNL MView]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 está instalado. A ID do patch é ACSD-56741. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma mensagem de erro *Tentando acessar o deslocamento da matriz no valor do tipo nulo* aparece durante `setup:upgrade` devido a um gatilho MySQL personalizado no banco de dados não relacionado à indexação e [!DNL MView].

<u>Etapas a serem reproduzidas</u>:

1. Executar `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Executar `php bin/magento c:f`.
1. Executar `php bin/magento setup:upgrade`.

<u>Resultados esperados</u>:

A atualização da instalação é concluída sem erros.

<u>Resultados reais</u>:

A atualização da instalação é encerrada com uma mensagem de erro:

*Aviso: tentando acessar o deslocamento da matriz no valor do tipo nulo*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
