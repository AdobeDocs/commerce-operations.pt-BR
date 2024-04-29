---
title: Dicas e truques do compositor
description: Saiba mais sobre as tarefas de desenvolvimento comuns do Composer e orientações para resolver problemas rapidamente.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Dicas e truques do compositor

Você pode encontrar problemas ao desenvolver módulos do Adobe Commerce com o Composer. Essas práticas recomendadas descrevem algumas tarefas comuns para facilitar o desenvolvimento e ajudar você a resolver problemas rapidamente.

>[!NOTE]
>
>As presentes orientações aplicam-se [arquitetura de referência global (GRA)](../overview.md) projetos.

## Speed-up Composer

Instalar [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) para acelerar o Composer com downloads de pacotes assíncronos.

```bash
composer global require hirak/prestissimo
```

Se você encontrar problemas, desinstale `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## Resolver problemas vagos de controle de versão

O compositor às vezes fica bloqueado com as versões do pacote. Você pode ver mensagens sobre versões incompatíveis, mesmo que não sejam. Antes de depurar problemas de compatibilidade, tente redefinir o Composer:

1. Limpe o cache do Composer.

   ```bash
   composer clearcache
   ```

1. Remova o `composer.lock` arquivo para todos os pacotes.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Reinstale os pacotes do Composer.

   ```bash
   composer install
   ```

>[!TIP]
>
>Essas etapas atualizam todos os pacotes para a versão mais recente disponível. Reverter o `composer.lock` arquivo do Git para desfazer essas atualizações.

## Verificar possíveis atualizações em pacotes de clientes

1. Descubra quais pacotes podem estar desatualizados.

   ```bash
   composer outdated
   ```

1. Filtre usando curingas e/ou `--minor-only` opção para ignorar atualizações incompatíveis com versões anteriores:

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## Descubra se um módulo está instalado

Exibir detalhes sobre todos os pacotes instalados em uma ramificação Git.

```bash
composer info
```

Executar `composer install` depois de trocar ramificações Git e antes de executar `composer info`. Caso contrário, o Composer mostrará detalhes sobre a ramificação anterior que você fez check-out.

>[!TIP]
>
>Para filtrar ou pesquisar, use um dos comandos a seguir.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## Descobrir por que um pacote do (versão específica de um) está instalado

Às vezes, o Composer instala a versão mais recente disponível de um pacote devido a uma dependência estrita em outro pacote.

Descubra se há uma dependência estrita em outro pacote.

```bash
composer why client/module-example
```

Se os resultados mostrarem uma lista de metapackages ou outro pacote que não seja explicitamente necessário, execute o comando nesse pacote:

```bash
composer why example/metapackage
```

## Descobrir por que um pacote não está instalado

Às vezes, o Composer não instala um pacote porque ele está em conflito com outro pacote, outro pacote o substitui ou você não o definiu como uma dependência.

Descubra por que um pacote não está instalado.

```bash
composer why-not client/module-example
```

## Hospede um repositório privado do Composer

Se você precisar de um repositório privado do Composer, use [Packagist Particular](https://packagist.com/) ou [JFrog Artifatory](https://jfrog.com/integration/php-composer-repository/). Não usar [Satis](https://github.com/composer/satis).

- **Packagist Particular** O é seguro, custa cerca de US$ 600 por ano com três usuários administradores e é hospedado.

- **JFrog Artifatory** A partir de US$ 1.176 por ano. Ele não é tão comumente usado como o Packagist, mas suporta mais linguagens do que o PHP.

- **Satis** O não tem segurança integrada, nenhuma automação e requer hospedagem adicional. Só é gratuito se o seu tempo também é gratuito.

## Controle de versão de pacotes

Uso [Versão semântica 2.0.0](https://semver.org/spec/v2.0.0.html) conforme descrito na seção Adobe Commerce [esquema de controle de versão](https://developer.adobe.com/commerce/php/development/versioning/). Não reinvente a roda.

Para dependências do módulo Adobe Commerce, siga as instruções [dependências de versão do módulo](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) documentação.

Não use a definição de versão dentro do `composer.json` arquivo. Em vez disso, use as tags Git para versões. Consulte [Versões e restrições do Composer](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Onde colocar os módulos que vêm em um arquivo e não através do Composer

Crie um repositório Git para módulos em um arquivo e hospede-os você mesmo. Cada módulo do Adobe Commerce tem um `composer.json` arquivo. Depois de hospedá-lo no Git e sincronizá-lo com o Private Packagist, você pode instalá-lo com o Composer.

Ao receber uma nova versão do pacote, faça upload do código no Git, marque-o e instale a nova versão com o Composer.
