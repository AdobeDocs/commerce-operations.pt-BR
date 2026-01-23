---
title: '[!DNL Data Migration Tool] pré-requisitos'
description: Saiba o que é necessário fazer antes de começar a usar o [!DNL Data Migration Tool] para transferir dados entre o Magento 1 e o Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool] pré-requisitos

Antes de iniciar a migração, verifique se os seguintes requisitos foram atendidos.

## sistema Magento 2

* Configure seu sistema Magento 2 para que ele atenda aos [requisitos de sistema](../../installation/system-requirements.md).

  Use uma topologia e um design que correspondam pelo menos ao seu sistema Magento 1 existente.

* [Instalar o Magento 2](../../installation/overview.md).

## Cron

Não inicie trabalhos cron do Magento 2.

## Banco de dados

* Após a instalação, faça backup ou [despeje](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) seu banco de dados Magento 2 o mais rápido possível. Isso permite restaurar o estado inicial do banco de dados se a migração não for bem-sucedida.

* Verifique se o [!DNL Data Migration Tool] tem acesso de rede para conectar os bancos de dados Magento 1 e Magento 2.

  Abra portas no firewall para que a Ferramenta de Migração possa se comunicar com os bancos de dados.

* Verifique se suas contas do MySQL têm todos os privilégios necessários para acessar os bancos de dados do Magento.

Se o Log Binário estiver habilitado para seu banco de dados Magento 1, defina a variável de sistema global [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL como `1` ou conceda o [privilégio SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) à sua conta.

* Não recomendamos criar novas entidades (produtos, categorias e atributos) no armazenamento do Magento 2 antes da migração, pois o [!DNL Data Migration Tool] substitui essas novas entidades pelas entidades antigas do Magento 1.

## Extensões

Migrar o código de extensão do Magento 1 para o Magento 2.

Para encontrar as versões mais recentes das extensões, visite [!DNL [Commerce Marketplace]](https://commercemarketplace.adobe.com//) ou contate seu provedor de extensões.

Você também pode usar o [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
