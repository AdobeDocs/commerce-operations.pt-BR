---
title: Instale o [!DNL Upgrade Compatibility Tool]
description: Siga estas etapas para instalar o [!DNL Upgrade Compatibility Tool] para seu projeto do Adobe Commerce.
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Instale o [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

O [!DNL Upgrade Compatibility Tool] é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos instalados nela. Retorna uma lista de erros e avisos que devem ser endereçados antes de atualizar para a versão mais recente do Adobe Commerce.

## Baixe o [!DNL Upgrade Compatibility Tool]

Para baixar o [!DNL Upgrade Compatibility Tool], execute o seguinte comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Instalar

Para instalar o [!DNL Upgrade Compatibility Tool], instale os pré-requisitos necessários:

* Chaves de acesso do Adobe Commerce
* Composer
* Node.js

## Pré-requisitos

Consulte [pré-requisitos](../upgrade-compatibility-tool/prerequisites.md) para obter mais informações.

### Chaves de acesso do Adobe Commerce

Você deve ter [Chaves de acesso do Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) para baixar e usar o [!DNL Upgrade Compatibility Tool]. Adicione as chaves de acesso do Adobe Commerce à `auth.json` arquivo , localizado em `~/.composer` por padrão.

>[!WARNING]
>
>Verifique sua **COMPOSER_HOME** variável de ambiente para ver onde a variável `auth.json` está localizado.

O **chave pública** corresponde a _username_ Considerando que **chave privada** é _senha_:

### Exemplo de chaves de acesso do Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Composer

Clonar o [!DNL Upgrade Compatibility Tool] repositório e execução `composer install` no terminal para instalar dependências.

>[!WARNING]
>
>Se a variável **Chaves de acesso do Adobe Commerce** não estão configuradas corretamente, a variável [!DNL Upgrade Compatibility Tool] não será instalado e ocorrerão erros ao executar o `composer install` comando.

### Node.js

Para instalar o Node.js, consulte Node.js [documentação](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensões de terceiros

O Adobe recomenda que você entre em contato com o fornecedor da extensão para determinar se a extensão é totalmente compatível com a versão mais recente do Adobe Commerce.

Consulte [Executar a ferramenta](../upgrade-compatibility-tool/run.md) para obter informações sobre como executar o [!DNL Upgrade Compatibility Tool].
