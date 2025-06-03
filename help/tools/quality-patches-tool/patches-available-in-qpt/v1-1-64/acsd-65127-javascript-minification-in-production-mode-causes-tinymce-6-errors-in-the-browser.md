---
title: 'ACSD-65127: a minificação do JavaScript no modo de produção causa erros [!DNL TinyMCE] 6 no navegador'
description: Aplique o patch ACSD-65127 para corrigir o problema do Adobe Commerce em que a habilitação da minificação do JavaScript no modo de produção fazia com que  [!DNL TinyMCE] 6 gerasse erros no console do navegador, afetando a funcionalidade e a experiência do usuário.
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: c5b27b79dd2dc7f9b39e629756d3d5d01e019710
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# ACSD-65127: a minificação do JavaScript no modo de produção causa [!DNL TinyMCE] 6 erros no navegador

O patch ACSD-65127 corrige o problema em que a ativação da minificação do JavaScript no modo de produção fazia com que o [!DNL TinyMCE] 6 gerasse erros no console do navegador, afetando a funcionalidade e a experiência do usuário. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACSD-65127. Observe que esse problema foi corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na página [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Habilitar a minificação do JavaScript no modo de produção fez com que o [!DNL TinyMCE] 6 gerasse erros no console do navegador, afetando a funcionalidade e a experiência do usuário.

<u>Etapas a serem reproduzidas</u>:

1. Defina a configuração executando os comandos abaixo:

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. Ativar modo de produção.

```
bin/magento deploy:mode:set production
```

1. Na barra lateral Admin, vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Clique em **[!UICONTROL Edit]** em qualquer produto listado, role até **[!UICONTROL Content]** e selecione **[!UICONTROL Show Editor]**.

<u>Resultados esperados</u>:

Nenhum erro de JS no console do navegador.

<u>Resultados reais</u>:

*404* erros no console do navegador para o js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
