---
title: '"[!DNL Upgrade Compatibility Tool] exigências"'
description: 'Verifique se o sistema atende aos requisitos necessários para executar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando para seu projeto do Adobe Commerce. '
source-git-commit: 7ec999f9122eb0707ac6c37b7b49f9c423945318
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Chaves de acesso do Adobe Commerce

{{commerce-only}}

Você deve ter [Chaves de acesso do Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) para baixar e usar o [!DNL Upgrade Compatibility Tool]. Adicione as chaves de acesso do Adobe Commerce à `auth.json` arquivo , localizado em `~/.composer` por padrão.

>[!NOTE]
>
>Verifique sua **COMPOSER_HOME** variável de ambiente para ver onde a variável `auth.json` está localizado.

O **chave pública** corresponde a _username_ Considerando que **chave privada** é _senha_:

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
> Se você não configurar corretamente **Chaves de acesso do Adobe Commerce**, não é possível baixar o [!DNL Upgrade Compatibility Tool] e `composer create-project` falhará.

Executar `composer install` no terminal para instalar dependências.

## Requisitos do sistema

Os requisitos mínimos para utilizar a variável [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando são:

| **Requisitos** | **Restrições** |
|----------------|-----------------|
| versão PHP | >= 7.3 |
| Composer | nenhum requisito conhecido. |
| Node.js | Versões do Node.js `^12.22.0`, `^14.17.0`ou `>=16.0.0` (consulte [Instalar o Node.js](https://nodejs.dev/learn/how-to-install-nodejs)) |
| Limitações de memória | Pelo menos 2 GB de RAM. |

O Adobe Commerce só é compatível com sistemas operacionais Linux. Você pode executar o [!DNL Upgrade Compatibility Tool] em um sistema operacional Linux. Você não precisa executar a variável [!DNL Upgrade Compatibility Tool] onde a instância do Adobe Commerce está localizada.

É necessário [!DNL Upgrade Compatibility Tool] para ter acesso ao código-fonte da instância do Adobe Commerce. Por exemplo, você pode instalá-lo em um servidor e apontá-lo na instalação do Adobe Commerce em outro servidor.

Se você estiver executando o [!DNL Upgrade Compatibility Tool] em relação a uma instância do Adobe Commerce com módulos e arquivos grandes, a ferramenta pode exigir uma quantidade alta de RAM (pelo menos 2 GB).
