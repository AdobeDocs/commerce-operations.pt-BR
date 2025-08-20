---
title: 'ACP2E-3977: O campo [!UICONTROL Cap Reward Points Balance At] não pode ficar vazio'
description: Aplique o patch ACP2E-3977 para corrigir o problema do Adobe Commerce em que o campo **[!UICONTROL Cap Reward Points Balance At]** não podia ficar vazio quando o campo **[!UICONTROL Rewards Points Balance Redemption Threshold]** era definido, causando um erro de validação.
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
source-git-commit: 83ce590c5078d70f0414276e2f03a71bdcdad321
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACP2E-3977: O campo **[!UICONTROL Cap Reward Points Balance At]** não pode ficar vazio

O patch ACP2E-3977 corrige o problema em que o campo **[!UICONTROL Cap Reward Points Balance At]** não pode ser deixado em branco, mesmo quando deveria ser permitido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACP2E-3977. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p10

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Deixar **[!UICONTROL Cap Reward Points Balance At]** vazio aciona um erro de validação, mesmo que deva desabilitar o limite quando deixado em branco.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**.
1. Conjunto **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*.
1. Deixe **[!UICONTROL Cap Reward Points Balance At]** em branco.
1. Salve.

<u>Resultados esperados</u>:

Um valor vazio para **[!UICONTROL Cap Reward Points Balance At]** é permitido e desabilita a limitação.

<u>Resultados reais</u>:

*O Saldo de Pontos de Recompensa de Limite é inválido. O saldo precisa ser um número positivo ou ficar vazio. Verifique e tente novamente.* erro exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
