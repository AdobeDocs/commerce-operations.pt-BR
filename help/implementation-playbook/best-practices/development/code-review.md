---
title: Práticas recomendadas de revisão do código
description: Saiba mais sobre as práticas recomendadas de revisão de código para a fase de desenvolvimento de projetos do Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Práticas recomendadas de revisão do código do Adobe Commerce

O principal objetivo da revisão do código é validar se a funcionalidade implementada atende aos requisitos de maneira ideal das perspectivas de desempenho, arquitetura e segurança.

Além disso, a análise de código tem como objetivo garantir que o código atenda às práticas recomendadas de desenvolvimento da Adobe Commerce, seja fácil de entender e manter e siga os padrões de codificação. A maioria dos padrões de codificação deve ser verificada automaticamente por ferramentas apropriadas.

## Processo recomendado de revisão do código

Em um nível superior, o processo de revisão do código deve consistir nas seguintes etapas:

1. Fazer check-out da ramificação de recursos no ambiente de desenvolvimento local.
1. Se tiver passado algum tempo desde que o código foi enviado para revisão, mescle as alterações mais recentes da ramificação de destino (geralmente ramificação de controle de qualidade) e envie atualizações para a ramificação de recurso remoto (se houver).
1. Faça uma revisão de alto nível para validar se o código implementa todos os requisitos. Se houver grandes discrepâncias, entre em contato com o desenvolvedor para obter esclarecimentos.
1. A execução do código é opcional, mas se você tiver dúvidas de que o código funciona conforme esperado ou se ele facilitar a eficiência do processo, teste se a funcionalidade implementada funciona conforme esperado para os principais cenários de uso. Se houver problemas graves, interrompa o processo de revisão e reabra o ticket com os comentários apropriados.
1. Faça uma revisão completa para validar se o código implementa todos os requisitos. Se houver problemas, adicione os comentários apropriados à solicitação de pull e reabra o ticket.
1. Se tudo estiver bem, mescle a solicitação de pull (ou passe-a para o próximo nível de revisão de código, se um tiver sido estabelecido).

Além disso, considere os seguintes pontos ao implementar processos de revisão do código:

- A revisão do código é uma ferramenta básica para comunicação e transferência de conhecimento em uma equipe. Mesmo que uma solicitação de pull não contenha problemas graves e implemente a lógica de negócios necessária, você pode usá-la como uma oportunidade para sugerir mais melhorias após a mesclagem.

- Em média, a revisão do código não deve demorar mais de 10% a 20% do esforço de desenvolvimento. Isso pressupondo que a equipe de desenvolvimento seja formada por engenheiros seniores que trabalham bem em conjunto. Se a revisão do código demorar mais, ela pode afetar o orçamento e o cronograma do projeto.

- Resolva problemas com esforço excessivo necessário para revisões de código identificando a causa raiz. Geralmente, isso ocorre porque os requisitos não são traduzidos adequadamente em tíquetes de desenvolvimento (devido a problemas de comunicação, histórias de usuários ruins) ou porque é um problema de treinamento. No primeiro caso, a mitigação recomendada é garantir que os tíquetes tenham informações suficientes para que os membros da equipe atendam aos requisitos com eficiência. No segundo caso, talvez seja necessário ajustar a estrutura da equipe para incluir engenheiros mais experientes ou obter aprovação fora do mentoreamento e do treinamento.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## O que procurar na revisão do código

### Estilo

O estilo pode ser testado automaticamente executando a inspeção PhpStorm (veja abaixo).

Certifique-se de configurar [PHPMD e PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) e para executar o [Padrão de codificação](https://github.com/magento/magento-coding-standard) da CLI (também abaixo). Há algumas sobreposições, mas ambas também têm testes únicos.

### Convenção e estrutura

As revisões de convenção e estrutura são feitas manualmente.

- A funcionalidade da classe está limitada a uma única responsabilidade?
- A estrutura de diretórios faz sentido?
- É a funcionalidade executada no nível correto (servidor, cliente, CSS, JS, banco de dados, estrutura, infraestrutura).
- O controle de versão está correto?
- O código não parece convencional ou está tentando contornar um problema da maneira errada?
- A convenção de nomenclatura para o nome do módulo, nome do pacote e nome do repositório foi aplicada corretamente?
- Verifique se os estilos CSS globais foram aplicados cuidadosamente e se não estão sendo usados em excesso.

### Integralidade

As análises de integridade são feitas manualmente.

- O código pode ser ativado ou desativado pela configuração e todo o código necessário se comporta conforme esperado?
- Há alguma configuração presente que seja mencionada no tíquete? Verifique o escopo, o tipo de dados, a validação, a conversão e os valores padrão.
- A configuração é sempre recuperada no nível mais baixo possível (nível de exibição de armazenamento, nível de site ou nível global)? A recuperação da configuração deve corresponder à definição do escopo no `system.xml` arquivo.
- São abrangidos todos os percursos do fluxograma da especificação técnica? Todas as outras especificações técnicas são abrangidas?
- As ACLs estão definidas para a nova funcionalidade?
- O PhpDocs está limpo? As mensagens de confirmação estão limpas?
- Algum código foi comentado ou você está vendo código de depuração?

### Desempenho

As análises de desempenho são feitas manualmente, o que pode ser auxiliado pela execução do código em caso de dúvida.

- As consultas são executadas em um loop? Este loop pode estar fora dos arquivos editados.
- Você consegue detectar algum `cachable="false"` atributos? Eles são aplicados corretamente?

### Segurança

As análises de segurança são feitas manualmente, o que pode ser auxiliado pela pesquisa de texto. Parte da verificação de segurança é tratada por testes automatizados.

- As exceções são registradas quando necessário? Os tipos corretos de exceções são usados?
- Pode `around` plug-ins sejam evitados?
- Os plug-ins do retornam os tipos corretos de dados?
- Você pode encontrar consultas SQL brutas que devem ser criadas usando a camada de abstração do banco de dados?
- Algum novo tipo de dados é exposto a qualquer tipo de usuário, administrador ou front-end? Essa exposição é um risco de segurança?
- Os dados gerados pelo usuário são validados? Tudo o que vem do navegador é considerado gerado pelo usuário, incluindo valores de cookies e cabeçalhos do servidor.

### Privacidade e o RGPD

Revisões sobre privacidade e [GDPR](../../../security-and-compliance/privacy/gdpr.md) são feitas manualmente.

- O código lida com dados ou emails do cliente? Preste atenção especial.
- Se esse código puder ser executado em um loop, ele poderá vazar dados do cliente de um ciclo de loop para outro?
- Os indicadores de risco são importações, trabalhos cron, emails transacionais e manipuladores de fila de lotes.
- Garanta o isolamento dos dados do usuário em loops. Adobe aconselha usar fábricas ou repositórios para criar modelos no ciclo de loop, que não são acessíveis fora do loop.

### Mentoria

As análises para orientação são feitas manualmente.

- Procure locais para compartilhar conhecimento com o objetivo de educar a equipe.
- Se o seu comentário for meramente educacional, mas não fundamental para atender aos padrões, indique que não é obrigatório que o autor o resolva.
- Se você vir algo bom, diga ao desenvolvedor, especialmente quando eles abordaram um de seus comentários de uma maneira excelente. As revisões de código muitas vezes se concentram em erros, mas também devem oferecer incentivo e apreço pelas boas práticas. Às vezes, é ainda mais valioso, em termos de orientação, dizer a um desenvolvedor o que ele fez certo, do que contar a ele o que ele fez errado.

## Automação

Os desenvolvedores podem usar a automação para revisar a compilação de ID, o esquema do banco de dados, a validação do compositor e a conformidade com os padrões de codificação:

- Compilação de ID—Execute os seguintes comandos da CLI para ver se o código pode ser compilado sem problemas.

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- Esquema de banco de dados `whitelist.json`—Execute o seguinte comando da CLI e verifique se `db_schema_whitelist.json` arquivo não é adicionado ou alterado.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Validação do compositor — Validação da `composer.json` arquivo executando o seguinte comando da CLI no diretório que contém a `composer.json` arquivo.

  ```bash
  composer validate
  ```

- Padrão de codificação — Instale e execute a ferramenta Padrão de codificação e execute-a no módulo. O arquivo a seguir mostra como habilitá-lo para execução em qualquer lugar digitando `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- Inspeção de PhpStorm

- Detector de copiar/colar do PHP no PhpStorm
