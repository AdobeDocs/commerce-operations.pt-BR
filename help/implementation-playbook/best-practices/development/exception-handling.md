---
title: Práticas recomendadas de tratamento de exceções
description: Saiba mais sobre os métodos recomendados para registrar exceções ao desenvolver projetos no Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# Práticas recomendadas de tratamento de exceções

Se uma exceção não for gravada na variável `exception.log` arquivo com o modelo de exceção como contexto, ele não é reconhecido e analisado corretamente no New Relic ou em outro armazenamento de log compatível com monólogo PSR-3. Registrar somente uma parte da exceção (ou registrá-la no arquivo errado) gera bugs na produção quando as exceções são ignoradas.

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

Essa abordagem salva automaticamente as `$e->getMessage` à mensagem de log e à `$e` para o contexto, seguindo o [Padrão de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context). Isso é feito em `\Magento\Framework\Logger\Monolog::addRecord`.

### ![correto](../../../assets/yes.svg) Silenciar sinais

Silencie sinais ao não registrar exceções que fazem parte do fluxo de operações pretendido. Nenhuma ação de acompanhamento é necessária quando a exceção é encontrada, portanto, ela não precisa ser registrada e analisada quando ocorrer. Adicione um comentário indicando o motivo para silenciar sinais e que é intencional. Combinar com `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![correto](../../../assets/yes.svg) Fazer downgrade das exceções

Faça downgrade das exceções seguindo o [Padrão de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![correto](../../../assets/yes.svg) O registro sempre vem primeiro

Como prática recomendada, o registro em log sempre vem primeiro no código para evitar casos em que outra exceção ou erro fatal é lançado antes da gravação no log.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![correto](../../../assets/yes.svg) Registrar mensagens e todo o rastreamento de exceção

Registrar mensagens e todo o rastreamento de exceção seguindo o [Padrão de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Tratamento de exceção incorreto

Os exemplos a seguir demonstram o tratamento incorreto de exceções.

### ![incorreto](../../../assets/no.svg) Lógica antes do registro

A lógica antes do registro em log pode levar a outra exceção ou erro fatal, que impede que a exceção seja registrada e deve ser substituída por [exemplo correto](#correct-logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![incorreto](../../../assets/no.svg) Empty `catch`

Empty `catch` ser um sinal de mutação não intencional e deve ser substituída pela [exemplo correto](#correct-mute-signals).

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

### ![incorreto](../../../assets/no.svg) Registrar mensagens e rastrear arquivos de log diferentes

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

Corrija esse problema substituindo o código seguindo os exemplos corretos mostrados em [Gravar no log de exceções](#correct-write-to-the-exception-log) ou [Fazer downgrade das exceções](#correct-downgrade-exceptions).

### ![incorreto](../../../assets/no.svg) Fazer downgrade de exceções sem contexto

A exceção é rebaixada para um erro, que não permite que um objeto seja transmitido, mas apenas uma string, portanto a variável `getMessage()`. Isso faz com que o rastreamento seja perdido e deve ser substituído pelos exemplos corretos mostrados em [Gravar no log de exceções](#correct-write-to-the-exception-log) ou [Fazer downgrade das exceções](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![incorreto](../../../assets/no.svg) Registrar somente a mensagem no log de exceções

Em vez de passar o objeto `$e`, somente `$e->getMessage()` é transmitido. Isso causa a perda do rastreamento e deve ser substituído pelos exemplos corretos mostrados [Gravar no log de exceções](#correct-write-to-the-exception-log) ou [Fazer downgrade das exceções](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![incorreto](../../../assets/no.svg) Ausente `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Omitir o `phpcs:ignore` dispara um aviso no PHPCS e não deve passar seu CI. Isso deve ser substituído pelo exemplo correto mostrado em [Silenciar sinais](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
