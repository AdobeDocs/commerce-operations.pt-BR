---
title: Executar testes de unidade
description: Execute testes de unidade definidos na base de código Adobe Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Executar testes de unidade

{{file-system-owner}}

Este comando executa um conjunto de testes definidos na base de código do Commerce 2. Você pode executar todos os testes ou testes selecionados. Sempre que um tipo não suportado é especificado, o programa encerra e lista todos os tipos disponíveis. Após a execução, um relatório detalhado é exibido mostrando a execução do teste e os resultados.

## Pré-requisitos

Antes de executar esse comando, execute o seguinte _must_ ser verdadeiro:

- O `Magento_Developer` deve estar habilitado. Você pode habilitá-lo da seguinte maneira:

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   Use o `--force` somente se necessário.

- Seu sistema deve ser configurado para executar os testes desejados.

Por exemplo, para executar testes de integração, você deve copiar `dev/tests/integration/etc/install-config-mysql.php.dist` para `dev/tests/integration/etc/install-config-mysql.php` e modificá-la de acordo com seu ambiente.

## Execução de testes

Uso do comando:

```bash
bin/magento dev:tests:run <test>
```

Para listar os tipos de teste disponíveis:

```bash
bin/magento dev:tests:run --help
```

Retorno de exemplo:

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Por exemplo, para executar testes de integração:

```bash
bin/magento dev:tests:run integration
```
