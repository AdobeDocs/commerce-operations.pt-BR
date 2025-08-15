---
title: 'ACSD-61366: o comando &grave;bin/magento setup:static-content:deploy —jobs 4&grave; encontra várias falhas de trabalho com um erro'
description: Aplique o patch ACSD-61366 para corrigir o problema do Adobe Commerce em que o comando &grave;bin/magento setup:static-content:deploy —jobs 4&grave; encontra várias falhas de trabalho com o erro *Port must be configured within the host parameter*, apesar de especificar a porta para a conexão de banco de dados.
feature: SCD
role: Admin, Developer
exl-id: d71a4833-a236-429b-a4e5-7d7d51c2caeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366: o comando `bin/magento setup:static-content:deploy --jobs 4` encontra várias falhas de trabalho com um erro

O patch ACSD-61366 corrige o problema em que o comando `bin/magento setup:static-content:deploy --jobs 4` encontra várias falhas de trabalho com o erro *Port deve ser configurado dentro do parâmetro de host*, apesar de especificar a porta para a conexão de banco de dados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 está instalado. A ID do patch é ACSD-61366. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O comando `bin/magento setup:static-content:deploy --jobs 4` encontra várias falhas de trabalho com o erro *A porta deve ser configurada dentro do parâmetro de host*, apesar de especificar a porta para a conexão de banco de dados.

<u>Etapas a serem reproduzidas</u>:

1. Especifique uma porta na conexão de banco de dados em `app/etc/env.php`.
1. Execute o comando `bin/magento setup:static-content:deploy --jobs 4`.

<u>Resultados esperados</u>:

A implantação de conteúdo estático é concluída com sucesso.

<u>Resultados reais</u>:

O comando falha com o erro *Port deve ser configurado dentro do parâmetro de host*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
