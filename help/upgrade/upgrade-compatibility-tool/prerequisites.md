---
title: '[!DNL Upgrade Compatibility Tool] requisitos'
description: Verifique se o sistema atende aos requisitos necessários para executar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando para o seu projeto do Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Chaves de acesso do Adobe Commerce

{{commerce-only}}

Você deve ter [chaves de acesso do Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) para baixar e usar o [!DNL Upgrade Compatibility Tool]. Adicione suas chaves de acesso do Adobe Commerce ao arquivo `auth.json`, localizado em `~/.composer` por padrão.

>[!NOTE]
>
>Verifique a variável de ambiente **COMPOSER_HOME** para ver onde o arquivo `auth.json` está localizado.

A **chave pública** corresponde ao _nome de usuário_, enquanto a **chave privada** é a _senha_:

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
> Se você não configurar corretamente as **chaves de acesso do Adobe Commerce**, não poderá baixar o [!DNL Upgrade Compatibility Tool] e o comando `composer create-project` falhará.

Execute `composer install` no terminal para instalar dependências.

## Requisitos do sistema

Os requisitos mínimos para usar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando são:

| **Requisitos** | **Restrições** |
|----------------|-----------------|
| versão do PHP | >= 7,3 |
| Compositor | nenhum requisito conhecido. |
| Node.js | Versões `^12.22.0`, `^14.17.0` ou `>=16.0.0` da Node.js (consulte [Instalar Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Limitações de memória | Pelo menos 2 GB de RAM. |

[!DNL Upgrade Compatibility Tool] requer [PCNTL](https://www.php.net/manual/en/book.pcntl.php) e outras extensões PHP para execução. Verifique as extensões necessárias do PHP usando o comando `composer check-platform-reqs`:

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

O Adobe Commerce só é compatível com sistemas operacionais Linux. Você pode executar o [!DNL Upgrade Compatibility Tool] em um sistema operacional Linux. Não é necessário executar o [!DNL Upgrade Compatibility Tool] onde a instância do Adobe Commerce está localizada.

É necessário que [!DNL Upgrade Compatibility Tool] tenha acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalá-lo em um servidor e apontá-lo para a instalação do Adobe Commerce em outro servidor.

Se você estiver executando o [!DNL Upgrade Compatibility Tool] em uma instância do Adobe Commerce com módulos e arquivos grandes, a ferramenta poderá exigir uma grande quantidade de RAM (pelo menos 2 GB).

Execute o [!DNL Upgrade Compatibility Tool] a partir do [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=pt-BR) para projetos do [Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=pt-BR){target=_blank}.
