---
title: Fase de desenvolvimento da implementação
description: Saiba mais sobre as práticas recomendadas de implementação para a fase de desenvolvimento de projetos do Adobe Commerce.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
source-git-commit: ce386611834c4199e34b5d95ce76254957821f46
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---


# Fase de desenvolvimento

A fase de desenvolvimento inclui as seguintes atividades:

- Configuração de ambiente local e de preparo
- Planejamento Sprint
- Execução de tíquete
- Solução de problemas
- Revisão de código, mesclagem e teste
- Revisão de Sprint
- Aprovação do cliente

>[!TIP]
>
>Consulte [práticas recomendadas gerais](general.md) para obter recomendações de alto nível sobre a gestão geral do processo de desenvolvimento.

As seções a seguir incluem informações de práticas recomendadas para a fase de desenvolvimento.

## Gerenciamento de código

| Prática recomendada | Descrição |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Revisão do código](code-review.md) | Processo de validação recomendado para garantir que a funcionalidade implementada atenda aos requisitos |
| [Composer vs Git](code-management.md) | Determine como distribuir o código personalizado considerando o gerenciamento de versões, a complexidade do código e o gerenciamento de dependências |
| [Estratégia de ramificação](git-branching.md) | Gerenciar código-fonte em repositórios Git |
| [Exemplos de GRA](../../architecture/global-reference/examples.md) | Entender métodos comuns de organização de uma [arquitetura de referência global](../../architecture/global-reference/overview.md) base de código |

## Banco de dados

| Prática recomendada | Descrição |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Modificação de tabela](modifying-core-and-third-party-tables.md) | Determine como e quando modificar tabelas de banco de dados do Adobe Commerce e de terceiros |

## Otimização de arquivos

| Prática recomendada | Descrição |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Redimensionamento da imagem do catálogo](catalog-image-resizing.md) | Fornece orientação sobre o redimensionamento de imagens antes que um armazenamento entre em produção para garantir o desempenho ideal |
| [CSS e JS](optimize-css-js-files.md) | Mesclar e minificar arquivos de folha de estilos em cascata (CSS) e JavaScript (JS) do Administrador ou da linha de comando |
| [Imagens](image-optimization.md) | Otimizar imagens e usar o Fastly para otimizar o tempo de resposta |

## Desenvolvimento de front-end

| Prática recomendada | Descrição |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Desenvolvimento de tema](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Descreve padrões de desenvolvimento para ajudar a garantir a compatibilidade entre o tema, versões futuras do Adobe Commerce e extensões personalizadas |

## Desenvolvimento em PHP

| Prática recomendada | Descrição |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Tratamento de exceções](exception-handling.md) | Descreve os métodos recomendados para registrar exceções |
| [Extensões](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Descreve padrões de desenvolvimento para ajudar a garantir a compatibilidade entre sua extensão, versões futuras do Adobe Commerce e outras extensões personalizadas |
| [Blocos de conteúdo privado](private-content-block-configuration.md) | Configurar blocos de conteúdo privado para otimizar o desempenho da loja |
| [Modificar código PHP principal e de terceiros](modifying-core-and-third-party-code.md) | Modifique a funcionalidade, o resultado ou a entrada de qualquer código que você não criou ou não controla diretamente |

## Plataforma e serviços

| Prática recomendada | Descrição |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Criações e implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html){target="_blank"} | Descreve as práticas recomendadas para os estágios de criação e implantação do Adobe Commerce em projetos de infraestrutura em nuvem |
| Depuração | Depurar a estrutura do Adobe Commerce de forma sistemática e eficaz |
| [Implantação de conteúdo estático](static-content-deployment.md) | Evite problemas com o conteúdo estático que não aparece em sua loja |
| [Solução de problemas](troubleshooting.md) | Solução de problemas comuns de implementação do Adobe Commerce |
