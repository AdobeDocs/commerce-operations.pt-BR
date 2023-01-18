---
title: Prática recomendada para configurar a conexão escrava do MySQL
description: Saiba como configurar a conexão escrava MySQL para sites Adobe Commerce implantados na infraestrutura de nuvem.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: a5a6e25e3fd303e07a07110b85aa1d460f53cd54
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# Prática recomendada para configurar a conexão escrava do MySQL

>[!NOTE]
>
>Sabemos que este artigo ainda contém termos de software padrão do setor que alguns podem achar racistas, sexistas ou opressivos e que podem fazer o leitor se sentir machucado, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.

Para sites Adobe Commerce implantados na arquitetura cloud Infrastructure Pro, o Adobe recomenda habilitar a conexão escrava MYSQL para o banco de dados por padrão.

O Adobe Commerce pode ler vários bancos de dados de forma assíncrona.  Ao habilitar a conexão escrava MYSQL, o Adobe Commerce usa uma conexão somente leitura com o banco de dados para receber tráfego somente leitura em um nó não principal. Isso melhora o desempenho através do balanceamento de carga, pois apenas um nó precisa lidar com o tráfego de leitura e gravação.

## Versões afetadas

Adobe Commerce na infraestrutura em nuvem, arquitetura Pro

## Configurar conexão escrava MySQL

A configuração da conexão escrava MYSQL é definida pela variável [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) implantar variável no arquivo de configuração do ambiente da infraestrutura em nuvem do Adobe Commerce, `.magento.env.yaml`. Defina essa variável como `true` para habilitar a conexão.

Para habilitar a conexão escrava MySQL:

1. Edite as `.magento.env.yaml` e verifique se `MYSQL_USE_SLAVE_CONNECTION` estiver ativado.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirme todas as alterações e envie-as para a ramificação de ambiente para implantar a atualização.

   Depois que a implantação é concluída com êxito, a conexão escrava MySQL é habilitada em sua infraestrutura de nuvem.

## Informações adicionais

- [Variáveis de ambiente](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [Gargalo de alta carga do MySQL no Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Práticas recomendadas do banco de dados para o Adobe Commerce na infraestrutura em nuvem](database-on-cloud.md)
