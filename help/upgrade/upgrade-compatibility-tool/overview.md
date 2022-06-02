---
title: '"Visão geral da [!DNL Upgrade Compatibility Tool]"'
description: Saiba mais sobre o [!DNL Upgrade Compatibility Tool] e como ele pode ajudá-lo com seu projeto do Adobe Commerce.
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Visão geral do guia

{{commerce-only}}

Este guia destina-se aos administradores e engenheiros de software da Adobe Commerce. Inclui informações detalhadas sobre a instalação do [!DNL Upgrade Compatibility Tool], bem como a sua configuração e gestão. Ele assume uma compreensão básica da configuração e funcionalidade principais do Commerce.

## Visão geral da [!DNL Upgrade Compatibility Tool]

O [!DNL Upgrade Compatibility Tool] é uma ferramenta que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos e códigos principais instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes de atualizar para uma versão mais recente do Adobe Commerce.

## Use o [!DNL Upgrade Compatibility Tool]

Você pode usar o [!DNL Upgrade Compatibility Tool] via:

- Como independente [interface de linha de comando](../upgrade-compatibility-tool/run.md) ferramenta.
- Integração do [!DNL Upgrade Compatibility Tool] com o [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Uma configuração de execução no [Plug-in Magento PHPStorm](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

### Fluxo de trabalho

O diagrama a seguir mostra os workflows possíveis ao executar o [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/uct-diagram-v5.png)

### Ajude a melhorar o [!DNL Upgrade Compatibility Tool]

Se você precisar de informações ou se tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

Para conectar-se ao [!DNL Upgrade Compatibility Tool] equipe, entre em contato conosco no canal de Slack de Engenharia [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos ouvir seus comentários, problemas e sugestões para nos ajudar a melhorar a ferramenta.

O [!DNL Upgrade Compatibility Tool] usa regras definidas em nossa [Padrões de codificação](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) para garantir que seu projeto esteja seguindo as práticas recomendadas da Adobe Commerce e para ajudá-lo a melhorar e estender o [!DNL Upgrade Compatibility Tool].

Consulte a [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html) tópico para obter mais informações sobre a contribuição dos padrões de codificação.

### Recursos

Consulte os seguintes recursos para ajudá-lo a entender as atualizações do Adobe Commerce:

- O [guia de atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) O fornece uma visão geral da jornada de atualização típica do Adobe Commerce ou Magento Open Source e das práticas recomendadas para acompanhar essa jornada.
- O [próximas versões](https://devdocs.magento.com/release/) fornece as datas para versões programadas e futuras.
- O [recursos da comunidade](https://developer.adobe.com/commerce/contributor/community/) é o local para iniciar discussões ou encontrar mais informações.
- Verifique a [ferramentas relacionadas](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html) para obter ferramentas úteis em sua jornada de atualização típica.
