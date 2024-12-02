---
title: 'MDVA-39713: O usuário pode editar a hora de início da atualização agendada ativa'
description: O patch MDVA-39713 corrige o problema em que um usuário pode editar a hora de início de uma atualização agendada ativa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-39713. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713: O usuário pode editar a hora de início da atualização agendada ativa

O patch MDVA-39713 corrige o problema em que um usuário pode editar a hora de início de uma atualização agendada ativa. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-39713. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário pode editar a hora de início de uma atualização agendada ativa.

<u>Etapas a serem reproduzidas</u>:

1. Criar novas páginas do CMS.
1. Selecione **Agendar Nova Atualização** e defina a **Data de Início** como atual +1 minuto.
1. Ative a Atualização Agendada executando o comando `bin/magento cron:run --group=staging` no ambiente local. Aguarde alguns minutos e verifique se o agendamento está ativo.
1. Quando o agendamento estiver ativo, atualize a página.
1. Clique em **Exibir/Editar** na seção Alterações agendadas.
1. Edite o tempo adicionando +2 minutos e salve a alteração.
1. Salve a página do CMS.
1. Execute novamente o seguinte comando: `bin/magento cron:run --group=staging`.
1. Clique em **Exibir/Editar** da Atualização Agendada.

<u>Resultados esperados</u>:

O usuário não pode editar a hora de início de uma atualização agendada ativa.

<u>Resultados reais</u>:

O usuário recebe um erro como *Já existe um item (Magento\Cms\Model\Page) com a mesma ID &quot;11&quot;.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
