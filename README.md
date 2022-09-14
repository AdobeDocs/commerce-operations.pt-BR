---
source-git-commit: 5a950079e8b445ef363217c085da92f0991a3a7f
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 5%

---
# Documentação do usuário do Adobe Commerce

Agradecemos as contribuições de nossa comunidade, bem como de Adobe funcionários de fora das equipes de documentação.

## Código de conduta de fonte aberta do Adobe

Este projeto adotou o [Código de conduta de código aberto da Adobe](code-of-conduct.md) ou o [Código de conduta do .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Para obter mais informações, consulte o artigo [Contribuição](contributing.md).

## Sobre suas contribuições para o conteúdo do Adobe

Consulte a [Guia do colaborador Adobe Docs](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html).

A forma como você contribui depende de quem você é e do tipo de mudanças com as quais você gostaria de contribuir:

### Pequenas alterações

Se você estiver contribuindo com pequenas atualizações, visite o artigo e clique no link **Editar** link no artigo que vai para a fonte GitHub do artigo. Em seguida, use a interface do usuário do GitHub para fazer as atualizações. Veja o [Guia do colaborador Adobe Docs](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html) para obter mais informações.

Pequenas correções ou esclarecimentos enviados para documentação e exemplos de código neste acordo de recompra são cobertos pelos termos de uso do Adobe.

### Alterações importantes ou novos artigos de membros da comunidade

Se fizer parte da comunidade Adobe e quiser criar um novo artigo ou enviar alterações importantes, use a guia Problemas no repositório Git para enviar um problema e iniciar uma conversa com a equipe de documentação. Depois de concordar com um plano, você precisará trabalhar com um funcionário para ajudá-lo a inserir o novo conteúdo por meio de uma combinação de trabalho nos repositórios públicos e privados.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Grandes mudanças dos funcionários do Adobe

Se você for um autor técnico, gerente de programa ou desenvolvedor da equipe de produtos de uma solução da Adobe Experience Cloud e seu trabalho for criar ou contribuir com a criação de artigos técnicos, deverá usar o repositório privado em `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Ferramentas e configuração

Os colaboradores da comunidade podem usar a interface do usuário do GitHub para a edição básica ou bifurcar o repositório para fazer grandes contribuições.

Consulte a [Guia do colaborador Adobe Docs](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html) para obter detalhes.

## Como usar marcação para formatar seu tópico

Todos os artigos neste repositório usam a marcação com sabor do GitHub. Se não estiver familiarizado com a marcação, consulte:

* [Noções básicas do Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Página de consulta do Markdown para impressão](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Rótulos

No repositório público, os rótulos automatizados são atribuídos para extrair solicitações para nos ajudar a gerenciar o fluxo de trabalho da solicitação de pull e para ajudar você a saber o que está acontecendo com sua solicitação de pull:

* **Alteração enviada ao autor**: O autor foi notificado da solicitação de pull pendente.
* **ready-to-merge (pronto para mesclar)**: Pronto para ser revisado pela equipe de revisão da solicitação de pull.

## Modelos

O `_jekyll` O diretório contém tópicos modelos e ativos necessários.
Os modelos que usam a linguagem de modelo Líquido residem no `_jekyll` como arquivos HTML.
O `_jekyll/_data` contém arquivos com os dados usados para renderizar os modelos.

Para renderizar todos os modelos:

1. Navegue até o `_jekyll` diretório.

   cd_jekyll

1. Execute o script de renderização.

```
_scripts/render
```

> **OBSERVAÇÃO:** Você deve executar o script a partir da variável `_jekyll` diretório.
> **OBSERVAÇÃO:** É necessário ter o Ruby instalado para executar esse script.

O script executa a renderização, grava arquivos renderizados no `_jekyll/_rendered` como arquivos HTML e os copia para o `help/_includes` diretório como `.md` arquivos.


Consulte a documentação de Jekyll para obter mais detalhes sobre [Arquivos de dados](https://jekyllrb.com/docs/datafiles) [Filtros líquidos](https://jekyllrb.com/docs/liquid/filters/)e outros recursos.
