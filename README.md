---
source-git-commit: 21a4ec57b49f896cffefbec8db4ce97c161315a0
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 3%

---
# Documentação técnica operacional do Adobe Commerce

Agradecemos as contribuições da comunidade e de funcionários da Adobe de fora das equipes de documentação.

## Ganchos de pré-confirmação para otimização de imagem

Esse repositório inclui ganchos de pré-confirmação automatizados que otimizam imagens antes da confirmação. **Todos os colaboradores devem habilitar esses ganchos** para garantir uma otimização de imagem consistente e um tamanho de repositório reduzido.

### Configuração rápida

Após clonar o repositório, execute:

```bash
.githooks/setup-hooks.sh
```

### O que os ganchos fazem

- Detectar automaticamente arquivos de imagem preparados (PNG, JPG, JPEG, GIF, SVG)
- Executar `image_optim` para compactar e otimizar imagens
- Transferir imagens otimizadas automaticamente
- Garantir que todas as imagens confirmadas estejam corretamente otimizadas

### Benefícios

- Tamanho reduzido do repositório
- Carregamentos de página mais rápidos para a documentação
- Qualidade de imagem consistente em todos os colaboradores
- Não é necessária otimização manual

Para obter instruções detalhadas de instalação, solução de problemas e configuração, consulte [`.githooks/README.md`](.githooks/README.md).

## Código de conduta do Adobe Open Source

Este projeto adotou o [Código de conduta de código aberto da Adobe](code-of-conduct.md) ou o [Código de conduta do .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Para obter mais informações, consulte o artigo [Contribuição](contributing.md).

## Sobre suas contribuições para o conteúdo do Adobe

Consulte o [Guia do colaborador do Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

A forma como você contribui depende de quem você é e do tipo de alterações com as quais deseja contribuir:

### Pequenas alterações

Se você estiver contribuindo com pequenas atualizações, visite o artigo e clique na área de feedback que aparece na parte inferior do artigo, clique em **Opções de feedback detalhadas** e em **Sugerir uma edição** para ir para o arquivo de origem do Markdown no GitHub. Use a interface do GitHub para fazer suas atualizações. Consulte o [guia geral do colaborador do Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) para obter mais informações.

Pequenas correções ou esclarecimentos que você envia para documentação e exemplos de código neste repositório são cobertos pelos termos de uso da Adobe.

### Grandes alterações ou novos artigos de membros da comunidade

Se você fizer parte da comunidade da Adobe e quiser criar um novo artigo ou enviar grandes alterações, use a guia Problemas no repositório Git para enviar um problema e iniciar uma conversa com a equipe de documentação. Depois de concordar com um plano, você precisará trabalhar com um funcionário para ajudá-lo a inserir o novo conteúdo por meio de uma combinação de trabalho nos repositórios públicos e privados.

### Grandes mudanças de funcionários da Adobe

Se você for um autor técnico, gerente de programa ou desenvolvedor da equipe de produtos de uma solução da Adobe Experience Cloud e seu trabalho for contribuir com ou criar artigos técnicos, deverá usar o repositório privado em `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Ferramentas e configuração

Os colaboradores da comunidade podem usar a interface do usuário do GitHub para a edição básica ou bifurcar o repositório para fazer grandes contribuições.

Consulte o [Guia do colaborador do Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) para obter mais detalhes.

## Como usar marcação para formatar seu tópico

Todos os artigos neste repositório usam GitHub flavored markdown. Se não estiver familiarizado com a marcação, consulte:

- [Noções básicas do Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [Cheatsheet de markdown para impressão](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Modelos

Para alguns tópicos, usamos arquivos de dados e modelos para gerar conteúdo publicado. Os casos de uso para essa abordagem incluem:

- Publicação de grandes conjuntos de conteúdo gerado de forma programática
- Fornecer uma única fonte da verdade para clientes em vários sistemas que exigem formatos de arquivo legíveis por máquina, como YAML, para integração (por exemplo, ferramenta de análise que abrange todo o site)

Os exemplos de conteúdo de modelo incluem, entre outros, os seguintes:

- [Referência de ferramentas da CLI](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [Tabelas de disponibilidade de produtos](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [Tabelas de requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Gerar conteúdo em modelo

Em geral, a maioria dos autores só precisa adicionar uma versão de lançamento às tabelas de disponibilidade de produtos e requisitos do sistema. A manutenção de todos os outros conteúdos em modelos é automatizada ou gerenciada por um membro dedicado da equipe. Estas instruções são destinadas para a maioria dos escritores.

>**OBSERVAÇÃO:**
>
>- A geração de conteúdo de modelo requer o trabalho na linha de comando em um terminal.
>- É necessário ter o Ruby instalado para executar o script de renderização. Consulte [_jekyll/.ruby-version](_jekyll/.ruby-version) para obter a versão necessária.

Consulte o seguinte para obter uma descrição da estrutura do arquivo para conteúdo de modelos:

- `_jekyll` — Contém tópicos de modelo e ativos necessários
- `_jekyll/_data` — Contém os formatos de arquivo legíveis por máquina usados para renderizar modelos
- `_jekyll/templated` — Contém arquivos de modelo baseados em HTML que usam a linguagem de modelo Liquid
- `help/_includes/templated` — Contém a saída gerada para conteúdo de modelo no formato de arquivo `.md` para que possa ser publicada nos tópicos do Experience League; o script de renderização grava automaticamente a saída gerada nesse diretório para você

Para atualizar o conteúdo do modelo:

1. No editor de texto, abra um arquivo de dados no diretório `/jekyll/_data`. Por exemplo:

   - [Tabelas de disponibilidade de produtos](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   - [Tabelas de requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Use a estrutura YAML existente para criar entradas.

   Por exemplo, para adicionar uma versão do Adobe Commerce às tabelas de disponibilidade de produtos, adicione o seguinte a cada entrada nas seções `extensions` e `services` do arquivo `/jekyll/_data/product-availability.yml` (modifique os números de versão conforme necessário):

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navegue até o diretório `_jekyll`.

   ```bash
   cd _jekyll
   ```

1. Gere conteúdo de modelo e grave a saída no diretório `help/_includes/templated`.

   ```bash
   bundle exec rake render
   ```

   >**OBSERVAÇÃO:** você deve executar o script a partir do diretório `_jekyll`. Se esta for a primeira vez que você executa o script, instale primeiro as dependências de Ruby com o comando `bundle install`. As tarefas do rake são fornecidas pela gem `adobe-comdox-exl-rake-tasks` para melhor manutenção nos repositórios de documentação da Adobe Commerce.

1. Volte para o diretório `root`.

   ```bash
   cd ..
   ```

1. Verifique se os `help/_includes/templated` arquivos esperados foram modificados.

   ```bash
   git status
   ```

   Você deve ver uma saída semelhante à seguinte:

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Envie suas alterações.

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

Consulte a documentação do Jekyll para obter mais detalhes sobre [Arquivos de dados](https://jekyllrb.com/docs/datafiles), [Filtros líquidos](https://jekyllrb.com/docs/liquid/filters/) e outros recursos.

## Tarefas do rake disponíveis

Este repositório usa tarefas do rake fornecidas pela gem `adobe-comdox-exl-rake-tasks`. Para ver todas as tarefas disponíveis, execute:

```bash
cd _jekyll
bundle exec rake --tasks
```
