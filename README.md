---
source-git-commit: 2727ddb18995ac2163276a0aa8573161add48971
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 3%

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

Para alguns tópicos, usamos arquivos de dados e modelos para gerar conteúdo publicado. Os casos de uso para essa abordagem incluem:

* Publicação de grandes conjuntos de conteúdo gerado de forma programática
* Fornecer uma única fonte da verdade para clientes em vários sistemas que exigem formatos de arquivo legíveis por máquina, como YAML, para integração (por exemplo, ferramenta de análise que abrange todo o site)

Os exemplos de conteúdo de modelo incluem, entre outros, os seguintes:

* [Referência de ferramentas da CLI](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [Tabelas de disponibilidade de produtos](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [Tabelas de requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Gerar conteúdo em modelo

Em geral, a maioria dos autores só precisa adicionar uma versão de lançamento às tabelas de disponibilidade de produtos e requisitos do sistema. A manutenção de todos os outros conteúdos em modelos é automatizada ou gerenciada por um membro dedicado da equipe. Estas instruções destinam-se à &quot;maioria&quot; dos autores.

>**NOTA:**
>
>* A geração de conteúdo de modelo requer o trabalho na linha de comando em um terminal.
>* É necessário ter o Ruby instalado para executar o script de renderização. Consulte [_jekyll/.ruby-version](_jekyll/.ruby-version) para a versão necessária.

Consulte o seguinte para obter uma descrição da estrutura do arquivo para conteúdo de modelos:

* `_jekyll`—Contém tópicos com modelo e ativos necessários
* `_jekyll/_data`—Contém os formatos de arquivo legíveis por máquina usados para renderizar modelos
* `_jekyll/templated`—Contém arquivos de modelo baseados em HTML que usam a linguagem de modelo Liquid
* `help/_includes/templated`—Contém a saída gerada para conteúdo de modelo em `.md` formato de arquivo para que possa ser publicado em tópicos de Experience League; o script de renderização grava automaticamente a saída gerada nesse diretório para você

Para atualizar o conteúdo do modelo:

1. No editor de texto, abra um arquivo de dados no `/jekyll/_data` diretório. Por exemplo:

   * [Tabelas de disponibilidade de produtos](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [Tabelas de requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Use a estrutura YAML existente para criar entradas.

   Por exemplo, para adicionar uma versão do Adobe Commerce às tabelas de disponibilidade de produtos, adicione o seguinte a cada entrada na `extensions` e `services` seções do `/jekyll/_data/product-availability.yml` arquivo (modifique os números de versão conforme necessário):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navegue até a `_jekyll` diretório.

   ```
   cd _jekyll
   ```

1. Gere conteúdo de modelo e grave a saída na `help/_includes/templated` diretório.

   ```
   rake render
   ```

   >**NOTA:** Você deve executar o script a partir do `_jekyll` diretório. Se esta for a primeira vez que você executa o script, deve instalar as dependências do Ruby primeiro com o `bundle install` comando.

1. Verifique se o valor esperado `help/_includes/templated` arquivos foram modificados.

   ```
   git status
   ```

   Você deve ver uma saída semelhante à seguinte:

   ```
   modified:   _data/product-availability.yml
   modified:   ../help/_includes/templated/product-availability-extensions.md
   ```

Consulte a documentação do Jekyll para obter mais detalhes sobre [Arquivos de dados](https://jekyllrb.com/docs/datafiles), [Filtros líquidos](https://jekyllrb.com/docs/liquid/filters/)e outros recursos.
