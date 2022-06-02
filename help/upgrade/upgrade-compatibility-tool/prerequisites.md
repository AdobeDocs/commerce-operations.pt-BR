---
title: '"[!DNL Upgrade Compatibility Tool] exigências"'
description: 'Verifique se o sistema atende aos requisitos necessários para executar o [!DNL Upgrade Compatibility Tool] para seu projeto do Adobe Commerce. '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Requisitos do sistema

{{commerce-only}}

Os requisitos mínimos para utilizar a variável [!DNL Upgrade Compatibility Tool] são:

| **Requisitos** | **Restrições** |
|----------------|-----------------|
| versão PHP | >= 7.3 |
| Composer | nenhum requisito conhecido |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Limitações de memória | Pelo menos 2 GB de RAM |

Você pode executar o [!DNL Upgrade Compatibility Tool] em vários sistemas operacionais (o Windows não é compatível). Você não precisa executar a variável [!DNL Upgrade Compatibility Tool] onde a instância do Adobe Commerce está localizada.

É necessário [!DNL Upgrade Compatibility Tool] para ter acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalá-lo em um servidor e apontá-lo na instalação do Adobe Commerce em outro servidor.

Se você estiver executando o [!DNL Upgrade Compatibility Tool] em relação a uma instância do Adobe Commerce com módulos e arquivos grandes, a ferramenta pode exigir uma quantidade alta de RAM (pelo menos 2 GB).

## Chaves de acesso do Adobe Commerce

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

## Composer

Baixe o [!DNL Upgrade Compatibility Tool] repositório e execução `composer install` no terminal para instalar dependências.

>[!NOTE]
>
> Se você não configurar corretamente **Chaves de acesso do Adobe Commerce**, não é possível baixar o [!DNL Upgrade Compatibility Tool]. Executar o `composer create-project` falhará.

## Node.js

Para instalar o Node.js, consulte Node.js [documentação](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensões de terceiros

O Adobe recomenda que você entre em contato com o fornecedor da extensão para determinar se a extensão é totalmente compatível com a versão mais recente do Adobe Commerce.
