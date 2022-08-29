---
title: '"[!DNL Data Migration Tool] pré-requisitos"'
description: '"Saiba o que precisa fazer antes de começar a usar o [!DNL Data Migration Tool] para transferir dados entre o Magento 1 e o Magento 2."'
source-git-commit: 87298a6dfd783fed264f275495a3ad72374eb9f6
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# [!DNL Data Migration Tool] pré-requisitos

Antes de iniciar a migração, verifique se os seguintes requisitos foram atendidos.

## sistema Magento 2

* Configure seu sistema Magento 2 para que ele atenda à [requisitos do sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html).

   Use uma topologia e um design que pelo menos correspondam ao seu sistema Magento 1 existente.

* [Instalar o Magento 2](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html).

## Cron

Não inicie os trabalhos do Magento 2 cron.

## Banco de dados

* Após a instalação, faça o backup ou [lixeira](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) seu banco de dados do Magento 2 assim que possível. Isso permite restaurar o estado inicial do banco de dados se a migração não for bem-sucedida.

* Verifique se a variável [!DNL Data Migration Tool] O tem acesso à rede para conectar os bancos de dados Magento 1 e Magento 2.

   Abra portas no firewall para que a Ferramenta de migração possa se comunicar com os bancos de dados.

* Certifique-se de que suas contas MySQL tenham todos os privilégios necessários para acessar bancos de dados do Magento.

Se o Registro Binário estiver ativado para o banco de dados do Magento 1, defina a variável global [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) Variável do sistema MySQL para `1`ou conceda a [Privilégio SUPERIOR](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) para sua conta.

* Não é recomendável criar novas entidades (produtos, categorias e atributos) na sua loja do Magento 2 antes da migração, pois a variável [!DNL Data Migration Tool] substitui essas novas entidades pelas antigas do Magento 1.

## Extensões

Migre o código de extensão do Magento 1 para o Magento 2.

Para encontrar as versões mais recentes das extensões, visite [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) ou entre em contato com seu provedor de extensão.

Também é possível usar a variável [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
