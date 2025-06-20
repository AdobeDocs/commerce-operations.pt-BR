---
title: 'ACSD-63572: as tabelas temporárias do indexador "catalogrule" não serão limpas se o processo do indexador for encerrado'
description: Aplique o patch ACSD-63572 para corrigir o problema do Adobe Commerce em que as tabelas de indexador não são limpas quando o processo é encerrado devido a uma atualização ou interrupção do sistema em [!UICONTROL CLI].
feature: System
Role: Admin, Developers
exl-id: 1cab7058-ca20-4d43-bfca-9b0e3ad35f42
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-63572: `catalogrule` as tabelas temporárias do indexador não são limpas se o processo do indexador for finalizado

O patch ACSD-63572 corrige o problema em que as tabelas temporárias do indexador não são limpas quando o processo é encerrado devido a uma atualização/sistema ou interrupção em [!UICONTROL CLI]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63572. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As tabelas temporárias do indexador não são limpas quando o processo foi encerrado devido a uma atualização ou interrupção do sistema em [!UICONTROL CLI].

<u>Etapas a serem reproduzidas</u>:

1. Abrir [!UICONTROL CLI].
1. Executar comando: `bin/magento indexer:reindex catalogrule_rule`.
1. Cancele o processo antes que ele termine de usar: `^C`.
1. Reinicializa indexadores usando: `bin/magento indexer:reset catalogrule_rule catalogrule_product`.
1. Repita as etapas anteriores várias vezes.
1. Verifique as seguintes tabelas temporárias que foram criadas no banco de dados:

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>Resultados esperados</u>:

As tabelas temporárias antigas são excluídas quando não são necessárias.

<u>Resultados reais</u>:

As tabelas temporárias antigas não são removidas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
