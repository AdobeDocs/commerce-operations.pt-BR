---
title: "ACSD-50478: Problema de JS para ação de reversão na grade de backups e no comando de reversão do banco de dados"
description: Aplique o patch ACSD-50478 para corrigir o problema de JS para a ação de reversão na grade de backups e o comando de reversão do banco de dados para um caso em que o despejo do banco de dados contém acionadores e um comando SQL *delimitador*.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-50478: Problema de JS para ação de reversão na grade de backups e comando de reversão do banco de dados

O patch ACSD-50478 corrige o problema de JS para a ação de reversão na grade de backups e o comando de reversão do banco de dados para um caso em que o despejo do banco de dados contém acionadores e um comando SQL *delimitador*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 está instalado. A ID do patch é ACSD-50478. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problema de JS para a ação de reversão na grade Backups e no comando de reversão do banco de dados para um caso em que o despejo do banco de dados contém acionadores e um comando SQL *delimitador*.

<u>Etapas a serem reproduzidas</u>:

1. Defina indexadores para o modo [!UICONTROL Update on Schedule] para que os acionadores sejam criados no banco de dados.
1. Habilite a funcionalidade de backup na linha de comando:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Vá para **Sistema** > **Ferramentas** > **Backups** e gere um backup de BD.
1. Abra o console do navegador; você verá o seguinte erro:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Tente importar o BD da linha de comando:

   `bin/magento setup:rollback --db-file="<filename>"`

1. O seguinte erro é exibido:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Resultados esperados</u>:

A restauração do banco de dados é bem-sucedida a partir do Admin e da linha de comando.

<u>Resultados reais</u>:

Você observou os erros mencionados nas etapas 4 e 6.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
