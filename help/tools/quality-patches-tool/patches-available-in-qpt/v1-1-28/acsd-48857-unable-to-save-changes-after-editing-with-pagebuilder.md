---
title: 'ACSD-48857: Não é possível salvar as alterações após a edição com [!DNL Page Builder]'
description: Aplique o patch ACSD-48857 para corrigir o problema do Adobe Commerce em que o usuário não pode salvar alterações após editar com o  [!DNL Page Builder].
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-48857: Não é possível salvar as alterações após a edição com [!DNL Page Builder]

O patch ACSD-48857 corrige o problema em que o usuário não consegue salvar alterações após editar com [!DNL Page Builder]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 está instalado. A ID do patch é ACSD-48857. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário não pode salvar as alterações após a edição com [!DNL Page Builder].

<u>Etapas a serem reproduzidas</u>

1. Faça logon no site de administração.
1. Navegue até **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** para criar uma página vazia do CMS.
1. Execute este script SQL para definir o seguinte valor de campo **[!UICONTROL Content]**:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Retorne a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** no Administrador.
1. Edite sua página.
1. Vá para a guia **[!UICONTROL Content]**.
1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>

A limpeza de conteúdo do HTML está implementada. Isso remove os atributos HTML reservados [!DNL Page Builder] do conteúdo gerado pelo editor de texto.

<u>Resultados reais</u>

A página permanece não salva e o carregador continua girando. No console, o seguinte erro é gerado:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
