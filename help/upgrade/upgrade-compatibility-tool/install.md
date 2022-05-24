---
title: Baixe o [!DNL Upgrade Compatibility Tool]
description: Siga estas etapas para baixar a variável [!DNL Upgrade Compatibility Tool] para seu projeto do Adobe Commerce.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# Instale o [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

O [!DNL Upgrade Compatibility Tool] é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos instalados nela. Retorna uma lista de erros e avisos que devem ser endereçados antes de atualizar para a versão mais recente do Adobe Commerce.

## Pré-requisitos

Para instalar o [!DNL Upgrade Compatibility Tool], instale os pré-requisitos necessários.

Consulte [pré-requisitos](../upgrade-compatibility-tool/prerequisites.md) para obter mais informações.

## Baixe o [!DNL Upgrade Compatibility Tool]

Para baixar o [!DNL Upgrade Compatibility Tool], execute o seguinte comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

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

Baixe o [!DNL Upgrade Compatibility Tool] repositório e execução `composer install` no terminal para instalar dependências.

>[!WARNING]
>
>Se a variável **Chaves de acesso do Adobe Commerce** não estiverem configuradas corretamente, não será possível baixar a variável [!DNL Upgrade Compatibility Tool] e ao executar o `composer create-project` comando falhará.

### Node.js

Para instalar o Node.js, consulte Node.js [documentação](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensões de terceiros

O Adobe recomenda que você entre em contato com o fornecedor da extensão para determinar se a extensão é totalmente compatível com a versão mais recente do Adobe Commerce.

Consulte [Executar a ferramenta](../upgrade-compatibility-tool/run.md) para obter informações sobre como executar o [!DNL Upgrade Compatibility Tool].
