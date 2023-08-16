---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 5%

---
# Documentação técnica do Adobe Commerce

Agradecemos as contribuições de nossa comunidade, bem como de funcionários da Adobe de fora das equipes de documentação.

## Código de conduta de código aberto do Adobe

Este projeto adotou o [Código de conduta de código aberto da Adobe](code-of-conduct.md) ou o [Código de conduta do .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Para obter mais informações, consulte o artigo [Contribuição](contributing.md).

## Sobre suas contribuições para o conteúdo do Adobe

Consulte a [Guia do colaborador do Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

A forma como você contribui depende de quem você é e do tipo de alterações com as quais deseja contribuir:

### Pequenas alterações

Se você estiver contribuindo com pequenas atualizações, visite o artigo e clique no link **Editar** no artigo que vai para a origem GitHub do artigo. Em seguida, use a interface do usuário do GitHub para fazer suas atualizações. Consulte as [Guia do colaborador do Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) para obter mais informações.

As pequenas correções ou esclarecimentos que você envia para documentação e exemplos de código neste repositório são cobertos pelos termos de uso do Adobe.

### Grandes alterações ou novos artigos de membros da comunidade

Se você fizer parte da comunidade Adobe e quiser criar um novo artigo ou enviar grandes alterações, use a guia Problemas no repositório Git para enviar um problema e iniciar uma conversa com a equipe de documentação. Depois de concordar com um plano, você precisará trabalhar com um funcionário para ajudá-lo a inserir o novo conteúdo por meio de uma combinação de trabalho nos repositórios públicos e privados.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Grandes mudanças dos funcionários do Adobe

Se você for um autor técnico, gerente de programa ou desenvolvedor da equipe de produtos de uma solução da Adobe Experience Cloud e seu trabalho for contribuir com ou criar artigos técnicos, deverá usar o repositório privado em `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Ferramentas e configuração

Os colaboradores da comunidade podem usar a interface do usuário do GitHub para a edição básica ou bifurcar o repositório para fazer grandes contribuições.

Consulte a [Guia do colaborador do Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) para obter detalhes.

## Como usar marcação para formatar seu tópico

Todos os artigos neste repositório usam GitHub flavored markdown. Se não estiver familiarizado com a marcação, consulte:

* [Noções básicas do Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Cheatsheet de markdown para impressão](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Modelos

A variável `_jekyll` O diretório contém tópicos de modelo e ativos necessários.
Os templates que usam o idioma de modelo Liquid residem no `_jekyll/templated` como arquivos HTML.
A variável `_jekyll/_data` O diretório contém arquivos com os dados usados para renderizar os modelos.

Para renderizar todos os modelos:

1. Navegue até a `_jekyll` diretório.

   cd_jekyll

1. Execute o script de renderização.

```
_scripts/render
```

> **NOTA:** Você deve executar o script a partir do `_jekyll` diretório.
> **NOTA:** É necessário ter o Ruby instalado para executar este script.

O script executa a renderização e grava modelos renderizados na `help/_includes/templated` diretório.

Consulte a documentação do Jekyll para obter mais detalhes sobre [Arquivos de dados](https://jekyllrb.com/docs/datafiles), [Filtros líquidos](https://jekyllrb.com/docs/liquid/filters/)e outros recursos.
