---
title: Visão geral do [!DNL Upgrade Compatibility Tool]
description: Saiba mais sobre o [!DNL Upgrade Compatibility Tool] e como ele pode ajudá-lo com seu projeto do Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Visão geral do guia

{{commerce-only}}

Este guia destina-se aos administradores e engenheiros de software da Adobe Commerce. Inclui informações detalhadas sobre a instalação do [!DNL Upgrade Compatibility Tool], bem como sua configuração e gerenciamento. Ele pressupõe uma compreensão básica da configuração e funcionalidade principais do Commerce.

## Visão geral do [!DNL Upgrade Compatibility Tool]

A variável [!DNL Upgrade Compatibility Tool] O é uma ferramenta que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos e o código principal instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes de atualizar para uma versão mais recente do Adobe Commerce.

## Use o [!DNL Upgrade Compatibility Tool]

Você pode usar o [!DNL Upgrade Compatibility Tool] via:

- Como um usuário independente [interface de linha de comando](../upgrade-compatibility-tool/run.md) ferramenta.
- Integrando o [!DNL Upgrade Compatibility Tool] com o [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Uma configuração de execução dentro do [Plug- in PHPStorm para o MagentoName](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Fluxo de trabalho

O diagrama a seguir mostra os workflows possíveis ao executar o [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demonstração

Assista a este vídeo para saber mais [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Ajude a melhorar o [!DNL Upgrade Compatibility Tool]

Se você precisar de informações ou tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

Para se conectar com o [!DNL Upgrade Compatibility Tool] equipe, entre em contato conosco no canal de Slack de engenharia [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos ouvir seus comentários, problemas e sugestões para nos ajudar a melhorar a ferramenta.

A variável [!DNL Upgrade Compatibility Tool] O usa regras definidas em nosso [Padrões de codificação](https://developer.adobe.com/commerce/php/coding-standards/) para garantir que seu projeto esteja seguindo as práticas recomendadas da Adobe Commerce e para ajudar você a melhorar e estender o [!DNL Upgrade Compatibility Tool].

Consulte a [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) para obter mais informações sobre como contribuir com padrões de codificação.

## Recursos

Consulte os seguintes recursos para ajudá-lo a entender as atualizações do Adobe Commerce:

- A variável [guia de atualização](../overview.md) fornece uma visão geral da jornada de atualização típica de Adobe Commerce ou Magento Open Source e as práticas recomendadas para seguir ao longo dessa jornada.
- A variável [versões futuras](https://devdocs.magento.com/release/) fornece as datas das versões programadas e futuras.
- A variável [recursos da comunidade](https://developer.adobe.com/commerce/contributor/community/) é o local para iniciar discussões ou encontrar mais informações.
- Verifique a [ferramentas relacionadas](../upgrade-compatibility-tool/related-tools.md) página para obter ferramentas úteis na sua jornada de atualização típica.
