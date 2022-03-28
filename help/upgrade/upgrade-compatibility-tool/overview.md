---
title: Visão geral da [!DNL Upgrade Compatibility Tool]
description: Saiba mais sobre o [!DNL Upgrade Compatibility Tool] e como ele pode ajudá-lo com seu projeto do Adobe Commerce.
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# Visão geral da [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

O [!DNL Upgrade Compatibility Tool] é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos e o código principal instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce. Ela também identifica possíveis problemas que devem ser corrigidos no código antes de tentar atualizar para uma versão mais recente do Adobe Commerce.

O [!DNL Upgrade Compatibility Tool] O permite identificar quando as alterações no código principal foram feitas nos recursos personalizados. Consulte a [Executar a ferramenta](../upgrade-compatibility-tool/run.md) para obter mais informações.

Ele é distribuído como um pacote Composer com cada versão de uma versão do Adobe Commerce. Consulte a [Desenvolvedor](../upgrade-compatibility-tool/developer.md) para obter mais informações.

Consulte a [Instalar](../upgrade-compatibility-tool/install.md) tópico para as primeiras etapas com o [!DNL Upgrade Compatibility Tool].

## Fluxo de trabalho

O diagrama a seguir mostra o fluxo de trabalho esperado ao executar o [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/mvp-diagram-v3.png)

## O [!DNL Upgrade Compatibility Tool] caso de uso

O caso de uso a seguir descreve o processo típico de um parceiro da Adobe Commerce para atualizar a instância de um cliente:

1. Baixe o [!DNL Upgrade Compatibility Tool] do repositório Adobe Commerce (`https://repo.magento.com/`). Consulte a [Baixe o [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) para obter mais informações.
1. Execute o [!DNL Upgrade Compatibility Tool] durante a [beta](https://devdocs.magento.com/release/beta-program.html) fase mais recente [Versão do Adobe Commerce](https://devdocs.magento.com/release/).
1. O comando principal é `upgrade:check`. Esse comando analisa sua instância e verifica se há erros, avisos e problemas críticos na instância. Para otimizar os resultados:

   - Opção Adicionar `--ignore-current-version-compatibility-issues` para ignorar todos os problemas críticos, erros e avisos conhecidos em relação à sua versão atual do Adobe Commerce. Mostra somente os resultados da versão desejada.
   - Opção de uso `--min-issue-level` para definir o nível mínimo de emissão. Ajuda a priorizar apenas os problemas mais importantes com a atualização. Se quiser analisar apenas um determinado fornecedor, módulo ou diretório par, também poderá especificar o caminho. Consulte a [Executar a ferramenta](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) para obter mais detalhes.

1. Gere uma instância baunilha para a versão específica do Adobe Commerce que está instalada no momento. Consulte a [Guia do colaborador](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obter mais informações sobre como usar o `instance` para gerar uma instalação baunilha.

   >[!NOTE]
   >
   >Uma instância baunilha é uma instalação limpa de uma tag ou ramificação de versão especificada para uma versão específica.

1. O [!DNL Upgrade Compatibility Tool] Identifica áreas quebradas personalizadas. O Engenheiro de Software é capaz de entender a complexidade e estimar o esforço da atualização. Esta informação é partilhada com as partes interessadas.
1. Um orçamento e uma linha do tempo serão definidos para a atualização.
1. Os engenheiros de software podem trabalhar nas modificações de código necessárias para corrigir os módulos quebrados.
1. O [!DNL Upgrade Compatibility Tool] pode ser executado para rastrear o progresso da atualização.
1. Todas as verificações e engenharia agora podem encaminhar o código para um ambiente de preparo, onde os testes de regressão confirmam que todos os testes estão verdes, o que permite que eles liberem a versão mais recente do Adobe Commerce para produção no mesmo dia em que o pré-lançamento do Adobe Commerce foi lançado.

   ![[!DNL Upgrade Compatibility Tool] público](../../assets/upgrade-guide/audience-uct-v3.png)

## Ajude a melhorar o [!DNL Upgrade Compatibility Tool]

Para conectar-se ao [!DNL Upgrade Compatibility Tool] equipe, entre em contato conosco no canal de Slack de Engenharia [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos ouvir seus comentários, problemas e sugestões para nos ajudar a melhorar a ferramenta.

O [!DNL Upgrade Compatibility Tool] usa regras definidas em nossa [Padrões de codificação](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) para garantir que seu projeto esteja seguindo as práticas recomendadas da Adobe Commerce e para ajudá-lo a melhorar e estender o [!DNL Upgrade Compatibility Tool].

Consulte a [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  para obter mais informações sobre como contribuir com esse projeto.

## Recursos

Desenvolvemos os seguintes recursos para ajudá-lo a entender as atualizações do Adobe Commerce:

- [Guia de atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Próximas versões](https://devdocs.magento.com/release/)
- [Recursos da comunidade](https://devdocs.magento.com/community/resources/resources.html) para obter mais informações.
