---
title: Práticas recomendadas de implantação de conteúdo estático
description: Saiba como evitar problemas com o conteúdo estático que não aparece em sua loja do Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Práticas recomendadas de implantação de conteúdo estático

Este artigo fala sobre as práticas recomendadas de implantação de conteúdo estático (SCD) no Adobe Commerce para ajudar a evitar problemas em que o conteúdo estático não estaria disponível em seu site.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

* Adobe Commerce na infraestrutura em nuvem
* Adobe Commerce no local

## Práticas recomendadas

Para evitar um problema com o conteúdo estático não disponível em seu site, siga estas práticas recomendadas para garantir que seu conteúdo estático esteja configurado e implantado corretamente:

1. Siga as diretrizes de implantação:
   * Para o Adobe Commerce no local (todas as versões), consulte [Visão geral da implantação](../../../configuration/deployment/overview.md) em nossa documentação para desenvolvedores.
   * Para obter informações sobre a infraestrutura do Adobe Commerce na nuvem (todas as versões), consulte [Processo de implantação da nuvem](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) e [Estratégias de implantação de conteúdo estático](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) na documentação do desenvolvedor.

1. Para o Adobe Commerce na infraestrutura em nuvem (todas as versões), verifique se ece-tools está na versão mais recente. Consulte: [Atualizar versão de ferramentas ece](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) na documentação do desenvolvedor.
1. Para o Adobe Commerce na infraestrutura em nuvem (todas as versões), verifique se o conteúdo estático está implantado durante a fase de criação em vez da fase de implantação. Consulte: [Gerenciamento de configurações para configurações de armazenamento - Desempenho de implantação de conteúdo estático](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) na documentação do desenvolvedor.
1. Certifique-se de que você não tenha trabalhos cron de longa duração e elimine quaisquer processos cron de longa duração. Trabalhos cron de longa duração podem consumir recursos da CPU e potencialmente aumentar muito o tempo de implantação.
1. Para Adobe Commerce local (todas as versões), verifique se o processo `php` na CLI tem acesso ao diretório `pub/static`. Caso contrário, você poderá enfrentar um problema em que uma implantação de conteúdo estático não conseguirá gravar arquivos nesse diretório. Para obter mais informações: [Permissões de acesso a sistemas de arquivos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) em nossa documentação para desenvolvedores.
1. Verifique se o diretório `generated` não é um diretório compartilhado nas compilações; caso contrário, as compilações poderão falhar aleatoriamente. Para obter mais informações:
   * Adobe Commerce no local (todas as versões): [Detalhes técnicos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) em nossa documentação do desenvolvedor.
   * Adobe Commerce na infraestrutura em nuvem (todas as versões): [Processo de implantação - Fase 2: compilação](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) em nossa documentação do desenvolvedor.

1. Verifique sua estratégia de SCD. A estratégia *quick* é padrão. Para obter mais informações:
   * Adobe Commerce local (todas as versões): [Estratégias de implantação de arquivos estáticos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) em nossa documentação de desenvolvedor.
   * Adobe Commerce na infraestrutura em nuvem (todas as versões): [Implantar variáveis - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) na documentação do desenvolvedor.

## Informações adicionais

Em nossa documentação do desenvolvedor:

* [Contêiner de conteúdo estático](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Assinatura de Conteúdo Estático](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Implantar variáveis - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Fluxo de implantação](../../../performance/deployment-flow.md)
* [Nenhuma implantação de tempo de inatividade](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Otimizar implantação na nuvem](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
