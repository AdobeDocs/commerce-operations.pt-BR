---
title: Visão geral do  [!DNL Upgrade Compatibility Tool]
description: Saiba mais sobre o  [!DNL Upgrade Compatibility Tool] e como ele pode ajudar você com seu projeto do Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Visão geral do guia

{{commerce-only}}

Este guia destina-se aos administradores e engenheiros de software da Adobe Commerce. Inclui informações detalhadas sobre a instalação do [!DNL Upgrade Compatibility Tool], bem como sobre sua configuração e gerenciamento. Ele pressupõe uma compreensão básica da configuração e funcionalidade principais do Commerce.

## Visão geral do [!DNL Upgrade Compatibility Tool]

O [!DNL Upgrade Compatibility Tool] é uma ferramenta que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos e o código principal instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes de atualizar para uma versão mais recente do Adobe Commerce.

## Usar o [!DNL Upgrade Compatibility Tool]

Você pode usar o [!DNL Upgrade Compatibility Tool] via:

- Como uma ferramenta [de interface de linha de comando](../upgrade-compatibility-tool/run.md) autônoma. Para obter a lista completa de comandos disponíveis, consulte a [`bin/uct` referência](../../tools/reference/uct.md).
- Integrando o [!DNL Upgrade Compatibility Tool] ao [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Uma configuração de execução no [plug-in PHPStorm do Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Fluxo de trabalho (WRK)

O diagrama a seguir mostra os fluxos de trabalho possíveis ao executar o [!DNL Upgrade Compatibility Tool]:

Diagrama ![[!DNL Upgrade Compatibility Tool]](../../assets/upgrade-guide/uct-diagram-v5.png)

## Demonstração do [!DNL Upgrade Compatibility Tool]

Assista a este vídeo para saber mais sobre o [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Ajude a melhorar o [!DNL Upgrade Compatibility Tool]

Se você precisar de informações ou tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

Para se conectar com a equipe [!DNL Upgrade Compatibility Tool], entre em contato conosco no canal de Slack de Engenharia [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos ouvir seus comentários, problemas e sugestões para nos ajudar a melhorar a ferramenta.

O [!DNL Upgrade Compatibility Tool] usa regras definidas em nossos [Padrões de Codificação](https://developer.adobe.com/commerce/php/coding-standards/) para garantir que seu projeto esteja seguindo as práticas recomendadas da Adobe Commerce e para ajudá-lo a melhorar e estender o [!DNL Upgrade Compatibility Tool].

Consulte o tópico [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) para obter mais informações sobre como contribuir com padrões de codificação.

## Recursos

Consulte os seguintes recursos para ajudá-lo a entender as atualizações do Adobe Commerce:

- O [guia de atualização](../overview.md) fornece uma visão geral da jornada de atualização típica do Adobe Commerce e as práticas recomendadas para seguir ao longo dessa jornada.
- A página [versões futuras](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/planning/schedule) fornece as datas das versões programadas e futuras.
- A página [recursos da comunidade](https://developer.adobe.com/commerce/contributor/community/) é o local ideal para iniciar discussões ou encontrar mais informações.
- Verifique a página [ferramentas relacionadas](../upgrade-compatibility-tool/related-tools.md) para obter ferramentas úteis na jornada de atualização típica.
