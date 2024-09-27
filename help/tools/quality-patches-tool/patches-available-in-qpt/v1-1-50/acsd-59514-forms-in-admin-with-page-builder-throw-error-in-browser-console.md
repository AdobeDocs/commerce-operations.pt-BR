---
title: "ACSD-59514: Forms no Admin com  [!DNL Page Builder] lançamento de erro no console do navegador"
description: Aplique o patch ACSD-59514 para corrigir o problema do Adobe Commerce em que os formulários em Admin com  [!DNL Page Builder] lançam o erro "[!DNL Page Builder] foi renderizado por 5 segundos sem liberar bloqueios." no console do navegador após o envio do formulário, e as alterações não podem ser salvas.
feature: Page Builder
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---


# ACSD-59514: Forms no Admin com [!DNL Page Builder] gera erro no console do navegador

O patch ACSD-59514 corrige o problema em que os formulários em Admin com [!DNL Page Builder] geravam o erro *[!DNL Page Builder]por 5 segundos sem liberar bloqueios.* no console do navegador após o envio do formulário, e as alterações não podem ser salvas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 está instalado. A ID do patch é ACSD-59514. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Forms no Admin com [!DNL Page Builder] gerou o erro *[!DNL Page Builder]foi renderizado por 5 segundos sem liberar bloqueios.* no console do navegador após o envio do formulário, e as alterações não podem ser salvas.

<u>Pré-requisitos</u>:

Os módulos do Adobe Commerce [!DNL Page Builder] estão instalados e habilitados.

<u>Etapas a serem reproduzidas</u>:

1. Abra o painel de administração e clique no botão [!UICONTROL Content].
1. Selecione o bloco e edite-o.
1. Altere o conteúdo e clique em [!UICONTROL Save].
1. Abra o console e veja a mensagem de erro.

<u>Resultados esperados</u>:

O bloco foi salvo com sucesso.

<u>Resultados reais</u>:

O carregador não para de girar e o bloco não é salvo. O seguinte erro é exibido no console do navegador:
*[!DNL Page Builder]foi renderizado por 5 segundos sem liberar bloqueios.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
