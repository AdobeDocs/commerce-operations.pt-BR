---
title: '[!DNL Upgrade Compatibility Tool] requisitos'
description: Verifique se o seu sistema atende aos requisitos necessários para executar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando para o seu projeto do Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Chaves de acesso do Adobe Commerce

{{commerce-only}}

Você deve ter [Chaves de acesso do Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) para baixar e usar o [!DNL Upgrade Compatibility Tool]. Adicione as chaves de acesso do Adobe Commerce ao `auth.json` arquivo, localizado em `~/.composer` por padrão.

>[!NOTE]
>
>Verifique o seu **COMPOSER_HOME** variável de ambiente para ver onde a variável `auth.json` arquivo estiver localizado.

A variável **chave pública** corresponde ao _nome de usuário_ Considerando que a **chave privada** é o _senha_:

## Exemplo de chaves de acesso do Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Se você não configurar corretamente suas **Chaves de acesso do Adobe Commerce**, não é possível baixar o [!DNL Upgrade Compatibility Tool] e a variável `composer create-project` falhará.

Executar `composer install` no terminal para instalar dependências.

## Requisitos do sistema

Os requisitos mínimos para utilizar a [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando:

| **Requisitos** | **Restrições** |
|----------------|-----------------|
| versão do PHP | >= 7.3 |
| Compositor | nenhum requisito conhecido. |
| Node.js | Versões da Node.js `^12.22.0`, `^14.17.0`ou `>=16.0.0` (consulte [Instalar Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| Limitações de memória | Pelo menos 2 GB de RAM. |

[!DNL Upgrade Compatibility Tool] exige [PCNTL](https://www.php.net/manual/en/book.pcntl.php) e outras extensões PHP para execução. Verifique as extensões necessárias do PHP usando `composer check-platform-reqs` comando:

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

O Adobe Commerce só é compatível com sistemas operacionais Linux. Você pode executar o [!DNL Upgrade Compatibility Tool] em um sistema operacional Linux. Não é necessário executar o [!DNL Upgrade Compatibility Tool] onde sua instância do Adobe Commerce está localizada.

É necessário que a [!DNL Upgrade Compatibility Tool] para ter acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalá-lo em um servidor e apontá-lo para a instalação do Adobe Commerce em outro servidor.

Se você estiver executando o [!DNL Upgrade Compatibility Tool] em uma instância do Adobe Commerce com módulos e arquivos grandes, a ferramenta pode exigir uma grande quantidade de RAM (pelo menos 2 GB).

Execute o [!DNL Upgrade Compatibility Tool] do [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) para [Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} projetos.
