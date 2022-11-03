---
title: Práticas recomendadas de implantação de conteúdo estático
description: Saiba como evitar problemas com conteúdo estático que não aparecem na loja da Adobe Commerce ou do Magento Open Source.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# Práticas recomendadas de implantação de conteúdo estático

Este artigo fala sobre as práticas recomendadas de implantação de conteúdo estático (SCD) no Adobe Commerce para ajudar a evitar problemas em que o conteúdo estático não estaria disponível em seu site.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

* Adobe Commerce na infraestrutura de nuvem
* Adobe Commerce no local
* Magento Open Source

## Práticas recomendadas

Para evitar um problema com o conteúdo estático que não está disponível em seu site, siga as práticas recomendadas a seguir para garantir que seu conteúdo estático seja configurado e implantado corretamente:

1. Siga as diretrizes de implantação:
   * Para o Adobe Commerce no local e o Magento Open Source (todas as versões), consulte [Visão geral da implantação](../../../configuration/deployment/overview.md) na documentação do desenvolvedor.
   * Para obter informações sobre a infraestrutura em nuvem do Adobe Commerce (todas as versões), consulte [Processo de implantação na nuvem](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) e [Estratégias estáticas de implantação de conteúdo](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) na documentação do desenvolvedor.

1. Para o Adobe Commerce na infraestrutura de nuvem (todas as versões), verifique se as ferramentas de gráficos estão na versão mais recente. Consulte: [Atualizar a versão das ferramentas gráficas](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) na documentação do desenvolvedor.
1. Para o Adobe Commerce na infraestrutura em nuvem (todas as versões), verifique se o conteúdo estático é implantado durante a fase de criação, em vez da fase de implantação. Consulte: [Gerenciamento de configurações para configurações de armazenamento - Desempenho estático da implantação de conteúdo](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) na documentação do desenvolvedor.
1. Certifique-se de que você não tenha trabalhos cron de longa duração e elimine qualquer processo cron de longa duração. Trabalhos cron de longa duração podem consumir recursos da CPU e, potencialmente, aumentar bastante o tempo de implantação.
1. Para o Adobe Commerce no local e o Magento Open Source (todas as versões), verifique se a variável `php` processo na CLI tem acesso ao `pub/static` diretório. Caso contrário, você poderá enfrentar um problema em que uma implantação de conteúdo estático não poderá gravar arquivos nesse diretório. Para obter mais informações: [Permissões de acesso aos sistemas de arquivos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) na documentação do desenvolvedor.
1. Verifique se a `generated` diretório não é um diretório compartilhado em builds; caso contrário, as builds poderiam falhar aleatoriamente. Para obter mais informações:
   * Adobe Commerce no local e Magento Open Source (todas as versões): [Detalhes técnicos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) na documentação do desenvolvedor.
   * Adobe Commerce na infraestrutura de nuvem (todas as versões): [Processo de implantação - Fase 2: build](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) na documentação do desenvolvedor.

1. Verifique sua estratégia de SCD. O *rápida* estratégia é o padrão. Para obter mais informações:
   * Adobe Commerce no local e Magento Open Source (todas as versões): [Estratégias de implantação de arquivos estáticos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) na documentação do desenvolvedor.
   * Adobe Commerce na infraestrutura de nuvem (todas as versões): [Implantar variáveis - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) na documentação do desenvolvedor.

## Informações adicionais

Em nossa documentação do desenvolvedor:

* [Contêiner de conteúdo estático](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Assinatura de conteúdo estático](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Implantar variáveis - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Fluxo de implantação](../../../performance/deployment-flow.md)
* [Implantação de tempo de inatividade zero](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Otimizar a implantação da nuvem](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

