---
title: '"[!DNL Upgrade Compatibility Tool] Informações do desenvolvedor"'
description: Personalize o [!DNL Upgrade Compatibility Tool] usando a integração de índice da API.
source-git-commit: 97295df89fda393c8cf8675f8f4be92ac6f38a6a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] informações do desenvolvedor

Este tópico contém informações para desenvolvedores que trabalham em conjunto com o código Adobe Commerce e que desejam obter informações detalhadas sobre o [!DNL Upgrade Compatibility Tool]. Você pode usar esse conhecimento para personalizar os componentes da ferramenta.

## Integração de índice da API Adobe Commerce

A integração de índice da API do Adobe Commerce é uma solução de integração interna que abrange um conjunto de ferramentas para explorar extensões do Adobe Commerce desenvolvidas pelo Adobe, pelos parceiros da Adobe Commerce e por fornecedores terceirizados com base na análise de código estático.

A integração com o índice da API do Adobe Commerce é feita por meio de:

`sut\Domain\MRay\MRayInterface`

É implementado por meio do `config/services.yaml` arquivo. Seu valor decide onde a resposta dos métodos `api()` e `modules()` vem de.

Edite este arquivo para personalizar a resposta de acordo com sua instalação. Substitua o valor atribuído a `sut\Domain\MRay\MRayInterface`:

### Exemplo de um valor personalizado

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

No exemplo anterior, a variável [!DNL Upgrade Compatibility Tool] uses `@sut_mray_mock` como `MRayInterface` implementação. As respostas da `api()` e `modules()` Os métodos vêm dos seguintes arquivos:

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>Quando você altera a variável `services.yaml` , exclua o `var/cache/` para aplicar corretamente as alterações.

## Teste da unidade

Para executar os testes de unidade, execute um dos seguintes comandos:

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## Teste de integração

Para executar os testes de integração, execute um dos seguintes comandos:

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## Teste de aceitação

1. Antes de executar testes de aceitação, você deve definir o URL do Adobe Commerce no `phpunit` arquivo de configuração.
1. Copiar o padrão `tests/acceptance/phpunit.xml` (sem o sufixo .dist).
1. Altere o `TESTS_BASE_URL` para apontar para o URL do Adobe Commerce que você deseja testar.
1. Para executar os testes de aceitação, execute um dos seguintes comandos:

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## Teste de unidade GraphQL e análise de código ESLint

### Requisitos

>[!NOTE]
>
>Você deve ter o Node.js em seu sistema; consulte o [Documentação do Node.js](https://nodejs.dev/learn/how-to-install-nodejs).

As instruções a seguir são para sistemas MacOS:

1. Abra um terminal e navegue até o diretório raiz do projeto.
1. Instalar dependências do projeto:

   ```bash
   npm install
   ```

### Teste de unidade GraphQL

O [Jest](https://jestjs.io/docs/getting-started) A estrutura foi usada para criar estes testes de unidade JS:

Os testes estão dentro `dev/tests/Js`.

Os esquemas de string para testes estão dentro de `dev/tests/Acceptance/_files/graphql_schemas`.

Executar testes de unidade ou `jest` como se segue:

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### Análise de código do ESLint

[ESLint](https://eslint.org/docs/user-guide/getting-started) O é uma ferramenta de análise de código estático para identificar padrões problemáticos encontrados no código JavaScript, com o objetivo de tornar o código mais consistente e evitar erros.

Executar `eslint` análise de código da seguinte maneira:

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## Pontuação de complexidade

O **pontuação de complexidade** é uma figura que indica a dificuldade de uma atualização da versão atual para a nova. Números mais baixos indicam atualizações mais fáceis.

>[!NOTE]
>
>As pontuações de complexidade variam entre 0 e ∞.

Essa pontuação é baseada nos resultados extraídos da análise:

- Número de problemas identificados
- Gravidade dos problemas identificados

O [!DNL Upgrade Compatibility Tool] O calcula essa pontuação de acordo com a fórmula de pontuação de complexidade abaixo.

### Fórmula de pontuação de complexidade

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>Esses são valores absolutos.
