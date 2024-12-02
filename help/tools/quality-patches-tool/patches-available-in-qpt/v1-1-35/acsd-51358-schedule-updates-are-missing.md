---
title: 'ACSD-51358: atualizações de programação ausentes'
description: Aplique o patch ACSD-51358 para corrigir o problema do Adobe Commerce em que as alterações na atualização agendada sem uma data final levam à remoção de outras atualizações agendadas na mesma entidade.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358: atualizações de programação ausentes

O patch ACSD-51358 corrige o problema em que as alterações na atualização agendada sem uma data final levam à remoção de outras atualizações agendadas na mesma entidade. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 está instalado. A ID do patch é ACSD-51358. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As alterações na atualização agendada sem uma data de término levam à remoção de outras atualizações agendadas na mesma entidade.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **[!UICONTROL scheduled update]** sem a data final (*atualização 1*).
1. Crie um novo **[!UICONTROL scheduled update]** com a mesma data de início da primeira atualização, mas adicione o dia seguinte e a data de término (*atualização 2*).
1. Edite **[!UICONTROL scheduled update]** criado na etapa 1 (*atualização 1*) e salve as alterações.

<u>Resultados esperados</u>

A (*atualização 2*) deve permanecer na lista **[!UICONTROL schedule update]** quando a (*atualização 1*) for editada.

<u>Resultados reais</u>

A (*atualização 2*) foi removida da lista **[!UICONTROL schedule update]** quando a (*atualização 1*) foi editada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](</help/tools/quality-patches-tool/usage.md>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no guia [!DNL Quality Patches Tool].
