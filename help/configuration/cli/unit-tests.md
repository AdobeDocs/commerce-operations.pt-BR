---
title: Executar testes de unidade
description: Execute testes de unidade definidos na base de código Adobe Commerce.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Executar testes de unidade

{{file-system-owner}}

Esse comando executa um conjunto de testes definidos na base de código do Commerce 2. Você pode executar todos os testes ou testes selecionados. Sempre que um tipo não suportado é especificado, o programa é encerrado e lista todos os tipos disponíveis. Após a execução, um relatório detalhado é exibido mostrando a execução do teste e os resultados.

## Pré-requisitos

Antes de executar este comando, faça o seguinte _deve_ ser verdadeiro:

- A variável `Magento_Developer` o módulo deve ser habilitado. Você pode ativá-la da seguinte maneira:

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   Use o `--force` opção apenas se for necessário.

- Seu sistema deve estar configurado para executar os testes desejados.

Por exemplo, para executar testes de integração, você deve copiar `dev/tests/integration/etc/install-config-mysql.php.dist` para `dev/tests/integration/etc/install-config-mysql.php` e modificá-lo para se adequar ao seu ambiente.

## Execução de testes

Uso do comando:

```bash
bin/magento dev:tests:run <test>
```

Para listar os tipos de teste disponíveis:

```bash
bin/magento dev:tests:run --help
```

Retorno de amostra:

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Por exemplo, para executar testes de integração:

```bash
bin/magento dev:tests:run integration
```
