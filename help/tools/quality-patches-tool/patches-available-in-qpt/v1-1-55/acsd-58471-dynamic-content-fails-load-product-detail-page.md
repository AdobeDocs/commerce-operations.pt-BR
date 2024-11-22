---
title: "ACSD-58471: o conteúdo dinâmico não é carregado na página de detalhes do produto quando as regras de preço de catálogo associadas são agendadas"
description: Aplique o patch ACSD-58471 para corrigir o problema do Adobe Commerce em que o conteúdo dinâmico falha ao carregar na página de detalhes do produto, quando as regras de preço de catálogo associadas foram agendadas.
feature: Catalog Management
role: Admin, Developer
source-git-commit: a3afb779006de95ac70dff39a737360112220af8
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---


# ACSD-58471: falha no carregamento do conteúdo dinâmico na página de detalhes do produto, quando as regras de preço de catálogo associadas foram agendadas

O patch ACSD-58471 resolve o problema em que o conteúdo dinâmico não é carregado na página de detalhes do produto quando as regras de preço de catálogo associadas são agendadas. O sistema agora exibe corretamente o conteúdo dinâmico associado às regras de preço do catálogo agendado na página de detalhes do produto. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-58471. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.5-p4

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Criar um Bloco Dinâmico no Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**.
1. Criar um Bloco Estático em [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**. Use widgets para adicionar conteúdo.
1. Crie um produto e adicione o bloco CMS à descrição.
1. Crie uma regra de catálogo com uma atualização agendada e atribua o produto e o bloco dinâmico criado em **[!UICONTROL Marketing]** > Promoções > **[!UICONTROL Catalog Products Rules]**.
1. Execute o cron e verifique se a página de detalhes do produto mostra o conteúdo dinâmico após a hora de início agendada.
1. Crie uma regra de catálogo sem uma atualização agendada e atribua o produto e o bloco dinâmico criado em **[!UICONTROL Marketing]** > Promoções > **[!UICONTROL Catalog Products Rules]**.
1. Execute o cron e verifique se a página detalhada do produto exibe o conteúdo dinâmico após o horário agendado.


<u>Resultados esperados</u>:

O conteúdo dinâmico é carregado após a hora de início agendada.

<u>Resultados reais</u>:

O conteúdo dinâmico não carrega.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
