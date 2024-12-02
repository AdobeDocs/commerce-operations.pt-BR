---
title: 'ACSD-61534: a configuração de design não pode ser definida usando bin/magento config:set, e os valores bloqueados podem ser alterados por meio da manipulação de formulários'
description: Aplique o patch ACSD-61534 para corrigir o problema do Adobe Commerce, em que a configuração de design não pode ser definida usando o comando "bin/magento config:set", e os valores bloqueados podem ser alterados por meio da manipulação de formulários.
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
source-git-commit: bbf7df7fdca4c11f6f268344db00e2c8643b5dce
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: A configuração de design não pode ser definida usando `bin/magento config:set`, e os valores bloqueados podem ser alterados por meio da manipulação de formulário

O patch ACSD-61534 corrige o problema em que a configuração de design não pode ser definida usando o comando `bin/magento config:set` e os valores bloqueados podem ser alterados por meio da manipulação de formulários. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-61534. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A configuração de design não pode ser definida usando o comando `bin/magento config:set`, e os valores bloqueados podem ser alterados por meio de manipulação de formulário. Com este patch, os valores bloqueados definidos pela CLI (Ferramenta de Linha de Comando) com `--lock-env` ou `--lock-conf` não podem ser atualizados.

<u>Etapas a serem reproduzidas</u>:

1. Bloquear um valor de configuração usando uma variável de ambiente de nuvem, como `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Vá para o painel *[!UICONTROL Admin]*.
1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Clique em **[!UICONTROL Edit]** próximo a **[!UICONTROL Global/Main website]** na segunda linha.
1. Editar tema para uma exibição de loja.
1. Abra o cabeçote do HTML.
1. Habilitar o campo **[!UICONTROL Scripts and Style Sheets]** desabilitado usando ferramentas de desenvolvedor.
1. Altere o valor e salve-o.

<u>Resultados esperados</u>:

Um valor bloqueado não pode ser salvo.

<u>Resultados reais</u>:

A tabela `core_config_data` contém um valor atualizado para `design/head/includes`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
