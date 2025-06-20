---
title: 'ACSD-62755: [!DNL TinyMCE] 7 precisa do tamanho e da fonte da fonte adicionados às configurações de inicialização do editor'
description: Aplique o patch ACSD-62755 para corrigir o problema do Adobe Commerce, em que [!DNL TinyMCE] 7 requer que o *tamanho da fonte* e a *família da fonte* sejam adicionados especificamente nas configurações de inicialização do editor.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755: [!DNL TinyMCE] 7 precisa do tamanho e da fonte da fonte adicionados às configurações de inicialização do editor

O patch ACSD-62755 corrige o problema em que o [!DNL TinyMCE] 7 requer que os seletores *tamanho da fonte* e *família da fonte* sejam adicionados especificamente nas configurações de inicialização do editor. Este patch está disponível com o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 instalado. A ID do patch é ACSD-62755. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p10

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL TinyMCE] 7 requer que os seletores *tamanho da fonte* e *família da fonte* sejam adicionados especificamente nas configurações de inicialização do editor.

<u>Etapas a serem reproduzidas</u>:

Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** e selecione *[!UICONTROL Show Editor]*.

<u>Resultados esperados</u>:

Os seletores *Tamanho da fonte* e *família da fonte* estão visíveis no editor do WYSIWYG.

<u>Resultados reais</u>:

O seletor *Tamanho da fonte* está ausente do editor do WYSIWYG.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
