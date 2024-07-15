---
title: Práticas recomendadas de tratamento de exceções
description: Saiba mais sobre os métodos recomendados para registrar exceções ao desenvolver projetos no Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Práticas recomendadas de tratamento de exceções

Se uma exceção não for gravada no arquivo `exception.log` com o modelo de exceção como contexto, ela não será reconhecida e analisada corretamente no New Relic ou em outro armazenamento de log compatível com monólogo PSR-3. Registrar somente uma parte da exceção (ou registrá-la no arquivo errado) gera bugs na produção quando as exceções são ignoradas.

## Manuseio de exceção correto

A lista de verificação a seguir fornece exemplos para demonstrar o manuseio correto de exceções.

### ![correto](../../../assets/yes.svg) Gravar no log de exceções

Grave no log de exceções usando o seguinte padrão, independentemente de outras ações, a menos que haja um motivo convincente para não fazê-lo.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Esta abordagem salva automaticamente o `$e->getMessage` na mensagem de log e o objeto `$e` no contexto, seguindo o [padrão de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context). Isso é feito em `\Magento\Framework\Logger\Monolog::addRecord`.

### ![corrigir](../../../assets/yes.svg) Sinais mudos

Silencie sinais ao não registrar exceções que fazem parte do fluxo de operações pretendido. Nenhuma ação de acompanhamento é necessária quando a exceção é encontrada, portanto, ela não precisa ser registrada e analisada quando ocorrer. Adicione um comentário indicando o motivo para silenciar sinais e que é intencional. Combinar com `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![corrigir](../../../assets/yes.svg) exceções de downgrade

Faça downgrade das exceções seguindo o [padrão de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### O registro ![correto](../../../assets/yes.svg) sempre vem primeiro

Como prática recomendada, o registro em log sempre vem primeiro no código para evitar casos em que outra exceção ou erro fatal é lançado antes da gravação no log.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![corrigir](../../../assets/yes.svg) Mensagens de log e todo o rastreamento de exceção

Registre mensagens e todo o rastreamento de exceção seguindo o [padrão de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Tratamento de exceção incorreto

Os exemplos a seguir demonstram o tratamento incorreto de exceções.

### Lógica ![incorreta](../../../assets/no.svg) antes de fazer logon

A lógica antes do registro em log pode levar a outra exceção ou erro fatal, que impede que a exceção seja registrada e deve ser substituída por [exemplo correto](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![incorreto](../../../assets/no.svg) Vazio `catch`

Blocos `catch` vazios podem ser sinal de silenciamento não intencional e devem ser substituídos pelo [exemplo correto](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![incorreto](../../../assets/no.svg) Localização dupla

Se a exceção localizada capturada ainda não for traduzida, resolva o problema no local em que a exceção é gerada pela primeira vez.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![incorreto](../../../assets/no.svg) Registra mensagens e rastreia para diferentes arquivos de registro

O código a seguir registra incorretamente o rastreamento de pilha de uma exceção como uma string em um arquivo de log.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Essa abordagem introduz quebras de linha na mensagem, que não é compatível com o PSR-3. A exceção, incluindo o rastreamento de pilha, deve fazer parte do contexto da mensagem para garantir que ela seja salva corretamente com a mensagem no New Relic ou em outro armazenamento de log compatível com monólogo PSR-3.

Corrija esse problema substituindo o código seguindo os exemplos corretos mostrados em [Gravar no log de exceções](#write-to-the-exception-log) ou [Baixar exceções](#downgrade-exceptions).

### ![incorreto](../../../assets/no.svg). Rebaixar exceções sem contexto

A exceção foi rebaixada para um erro, que não permite que um objeto seja passado, mas apenas uma cadeia de caracteres, portanto o `getMessage()`. Isso faz com que o rastreamento seja perdido e deve ser substituído pelos exemplos corretos mostrados em [Gravar no log de exceções](#write-to-the-exception-log) ou [Baixar exceções](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![incorreto](../../../assets/no.svg) registra somente a mensagem no log de exceção

Em vez de passar o objeto `$e`, apenas `$e->getMessage()` é passado. Isso faz com que o rastreamento seja perdido e deve ser substituído pelos exemplos corretos mostrados [Gravar no log de exceções](#write-to-the-exception-log) ou [Baixar exceções](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![incorreto](../../../assets/no.svg) `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch` ausente(s)

A omissão da linha `phpcs:ignore` aciona um aviso no PHPCS e não deve passar seu CI. Este deve ser substituído pelo exemplo correto mostrado em [Sinais mudos](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
